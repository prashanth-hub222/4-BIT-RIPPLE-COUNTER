# 4-BIT-RIPPLE-COUNTER

**AIM:**

To implement  4 Bit Ripple Counter using verilog and validating their functionality using their functional tables

**SOFTWARE REQUIRED:**

Quartus prime

**THEORY**

**4 Bit Ripple Counter**

A binary ripple counter consists of a series connection of complementing flip-flops (T or JK type), with the output of each flip-flop connected to the Clock Pulse input of the next higher-order flip-flop. The flip-flop holding the least significant bit receives the incoming count pulses. The diagram of a 4-bit binary ripple counter is shown in Fig. below.

![image](https://github.com/naavaneetha/4-BIT-RIPPLE-COUNTER/assets/154305477/cb4b74d4-31ab-4359-95d0-d22e67daba13)

In timing diagram Q0 is changing as soon as the negative edge of clock pulse is encountered, Q1 is changing when negative edge of Q0 is encountered(because Q0 is like clock pulse for second flip flop) and so on.

![image](https://github.com/naavaneetha/4-BIT-RIPPLE-COUNTER/assets/154305477/a573a7d6-014e-4e54-93e6-e2ac9530960b)

![image](https://github.com/naavaneetha/4-BIT-RIPPLE-COUNTER/assets/154305477/85e1958a-2fc1-49bb-9a9f-d58ccbf3663c)

**Procedure**
```
Step 1: Start the program and declare the inputs, outputs, clock, and reset signals for the 4-bit ripple counter.

Step 2: Write the Verilog code using flip-flops connected in cascade to perform ripple counting operation.

Step 3: Apply clock pulses and observe the binary count sequence at the output.

Step 4: Simulate the design in Quartus/ModelSim and verify the counter outputs using the functional table and waveform.
```
**PROGRAM**
```
module Exp12(q, clk, reset); 
output [3:0] q;
input clk, reset;
T_FF tffo(q[0], clk, reset); 
T_FF tff1(q[1], q[0], reset); 
T_FF tff2(q[2], q[1], reset); 
T_FF tff3(q[3], q[2], reset); 
endmodule

module D_FF(q, d, clk, reset); 
output q;
input d, clk, reset;
reg q;
always @(posedge reset or negedge clk)
if (reset)
q = 1'b0;
else
q = d;
endmodule

module T_FF(q, clk, reset);
output q;
input clk, reset;
wire d;
D_FF dff0(q, d, clk, reset);
not n1(d, q); 
endmodule
```
```
 Developed by:Prashanth Raaj S
 RegisterNumber:212225100035
```

**RTL LOGIC FOR 4 Bit Ripple Counter**
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/091015b1-5007-40e3-9722-e29a12853e2f" />

**TIMING DIGRAMS FOR 4 Bit Ripple Counter**
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/c6e24746-f1e9-46a9-92a4-07ac9858de21" />


**RESULTS**
This Verilog code implements a 4-bit asynchronous (ripple) binary counter using T flip-flops.
