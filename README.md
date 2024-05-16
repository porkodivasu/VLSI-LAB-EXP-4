# VLSI-LAB-EXP-4
SIMULATION AND IMPLEMENTATION OF SEQUENTIAL LOGIC CIRCUITS

AIM: 
 To simulate and synthesis SR, JK, T, D - FLIPFLOP, COUNTER DESIGN using Xilinx ISE.

APPARATUS REQUIRED:

Xilinx 14.7
Spartan6 FPGA

**LOGIC DIAGRAM**

SR FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/77fb7f38-5649-4778-a987-8468df9ea3c3)


JK FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/1510e030-4ddc-42b1-88ce-d00f6f0dc7e6)

T FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/7a020379-efb1-4104-85ee-439d660baa08)


D FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/dda843c5-f0a0-4b51-93a2-eaa4b7fa8aa0)


COUNTER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/a1fc5f68-aafb-49a1-93d2-779529f525fa)


  
PROCEDURE:
STEP:1  Start  the Xilinx navigator, Select and Name the New project.
STEP:2  Select the device family, device, package and speed.       
STEP:3  Select new source in the New Project and select Verilog Module as the Source type.                       
STEP:4  Type the File Name and Click Next and then finish button. Type the code and save it.
STEP:5  Select the Behavioral Simulation in the Source Window and click the check syntax.                       
STEP:6  Click the simulation to simulate the program and  give the inputs and verify the outputs as per the truth table.               
STEP:7  Select the Implementation in the Sources Window and select the required file in the Processes Window.
STEP:8  Select Check Syntax from the Synthesize  XST Process. Double Click in the  FloorplanArea/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained. 
STEP:9  In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu.
STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here.
STEP:11  On the board, by giving required input, the LEDs starts to glow light, indicating the output.

VERILOG CODE

   SR FLIPFLOP:
```
   module srff(clk,rst,s,r,q);
input clk,rst,s,r;
output reg q;
always@(posedge clk)
begin
if(rst==1)
q=0;
else
begin
case({s,r})
2'b00:q=q;
2'b01:q=0;
2'b10:q=1;
2'b11:q=1'bx;
endcase
end
end
endmodule
```

JK FLIPFLOP:

```
module jkff(j,k,q,clk,reset);
input j,k,clk,reset;
output reg q;
always @(posedge clk)
begin
if(reset==1)
q=0;
else
begin
case({j,k})
2'b00:q=q;
2'b01:q=0;
2'b10:q=1;
2'b11:q=~q;
endcase
end
end
endmodule

T FLIPFLOP:
```
module tff(clk,rst,t,q);
input clk,rst,t;
output reg q;
always @(posedge clk)
begin
if (rst==1)
q=1'b0;
else if (t==0)
q=q;
else
q=~q;
end
endmodule
```

D FLIPFLOP:

```
module dff(clk,reset,d,q);
input clk,d,reset;
output reg q;
always@(posedge clk)
begin
if(reset)
q<=1'b0;
else
q<=d;
end
endmodule
```

UPDOWN COUNTER:
```
module updowncount(clk,rst,updown,out);
input clk,rst,updown;
output reg [3:0] out;
always@ (posedge clk)
begin
if(rst==1)
out=4'b0000;
else if(updown==1)
out=out+1;
else
out=out-1;
end
endmodule
```

MOD 10 COUNTER:
```
module modcount(clk,rst,out);
input clk,rst;
output reg[3:0] out;
always @(posedge clk)
begin
if(rst==1 | out==4'b1001)
out=4'b0000;
else
out=out+1;
end
endmodule
```

RIPPLE COUNTER:

```
module ripple_carry_counter(q, clk, reset);
output [3:0] q;
input clk, reset;
T_FF tff0(q[0], clk, reset);
T_FF tff1(q[1], q[0], reset);
T_FF tff2(q[2], q[1], reset);
T_FF tff3(q[3], q[2], reset);
endmodule
module T_FF(q, clk, reset);
output q;
input clk, reset;
wire d;
D_FF dff0(q, d, clk, reset);
not n1(d, q); 
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
```


OUTPUT WAVEFORM

SR FLIPFLOP:

![Screenshot (47)](https://github.com/porkodivasu/VLSI-LAB-EXP-4/assets/160757120/37c79671-6b8f-4249-89ac-6cc3e38e0985)

JK FLIPFLOP:

![Screenshot (47)](https://github.com/porkodivasu/VLSI-LAB-EXP-4/assets/160757120/4724593c-a4d4-49b8-bc42-ffaf979c3ccb)

T FLIPFLOP:

![Screenshot (49)](https://github.com/porkodivasu/VLSI-LAB-EXP-4/assets/160757120/041c290b-64ea-4960-b836-40595f5de001)

D FLIPFLOP:

![Screenshot (51)](https://github.com/porkodivasu/VLSI-LAB-EXP-4/assets/160757120/50030b8d-0a62-4059-9185-4b1c3c6f506b)

UPDOWN COUNTER:

![Screenshot (57)](https://github.com/porkodivasu/VLSI-LAB-EXP-4/assets/160757120/a570165c-c43f-48e7-9daa-79b273845e37)

MOD 10 COUNTER:

![Screenshot (59)](https://github.com/porkodivasu/VLSI-LAB-EXP-4/assets/160757120/f4a40463-f65b-4af3-a48a-87c0a3f541c2)

RIPPLE COUNTER:

![Screenshot (60)](https://github.com/porkodivasu/VLSI-LAB-EXP-4/assets/160757120/e3617c52-7003-429c-bccd-4467b1b1abb0)


RESULT:

Thus,the simulation and synthesis of SR,JK,T,D flipflops,counters by using vivado has been successfully excecuted and
verified.


