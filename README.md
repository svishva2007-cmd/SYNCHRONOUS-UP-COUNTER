### SYNCHRONOUS-UP-COUNTER

**AIM:**

To implement 4 bit synchronous up counter and validate functionality.

**SOFTWARE REQUIRED:**

Quartus prime

**THEORY**

**4 bit synchronous UP Counter**

If we enable each J-K flip-flop to toggle based on whether or not all preceding flip-flop outputs (Q) are “high,” we can obtain the same counting sequence as the asynchronous circuit without the ripple effect, since each flip-flop in this circuit will be clocked at exactly the same time:

![image](https://github.com/naavaneetha/SYNCHRONOUS-UP-COUNTER/assets/154305477/d5db3fa0-e413-404c-b80e-b2f39d82e7e8)


![image](https://github.com/naavaneetha/SYNCHRONOUS-UP-COUNTER/assets/154305477/52cb61eb-d04b-442d-810c-31185a68410b)

Each flip-flop in this circuit will be clocked at exactly the same time.
The result is a four-bit synchronous “up” counter. Each of the higher-order flip-flops are made ready to toggle (both J and K inputs “high”) if the Q outputs of all previous flip-flops are “high.”
Otherwise, the J and K inputs for that flip-flop will both be “low,” placing it into the “latch” mode where it will maintain its present output state at the next clock pulse.
Since the first (LSB) flip-flop needs to toggle at every clock pulse, its J and K inputs are connected to Vcc or Vdd, where they will be “high” all the time.
The next flip-flop need only “recognize” that the first flip-flop’s Q output is high to be made ready to toggle, so no AND gate is needed.
However, the remaining flip-flops should be made ready to toggle only when all lower-order output bits are “high,” thus the need for AND gates.

**Procedure**

/* write all the steps invloved */

**PROGRAM**

// sync_up_counter.v
module synchronous #(
    parameter WIDTH = 8           // counter width, change as needed
)(
    input  wire                 clk,   // clock (rising-edge)
    input  wire                 rst,   // synchronous active-high reset
    input  wire                 en,    // enable counting when high
    output reg  [WIDTH-1:0]     count  // current count
);

    // Synchronous logic
    always @(posedge clk) begin
        if (rst) begin
            count <= {WIDTH{1'b0}}; // reset to 0 synchronously
        end else if (en) begin
            count <= count + 1'b1;  // increment on enable
        end
        // if !en, hold value
    end

endmodule


/* Program for flipflops and verify its truth table in quartus using Verilog programming. 

Developed by: RegisterNumber:
*/

**RTL LOGIC UP COUNTER**

<img width="1467" height="874" alt="image" src="https://github.com/user-attachments/assets/f7fb5de1-bc6f-4bab-88c4-6cbb4f7e2528" />


**TIMING DIAGRAM FOR IP COUNTER**

<img width="1320" height="823" alt="image" src="https://github.com/user-attachments/assets/611dd31c-d330-43fe-bb3f-23cfb41ca00c" />



**TRUTH TABLE**

**RESULTS**

Thus the Synchronous 3 bit Up counter is implemeted and verified.
