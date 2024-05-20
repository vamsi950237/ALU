# ALU
![image](https://github.com/RESMIRNAIR/ALU/assets/154305926/33dff162-59b3-44e2-886a-1ddd6e60979f)
# ALU Arithmetic and Logic Operations
----------------------------------------------------------------------
|ALU_Sel|   ALU Operation
----------------------------------------------------------------------
| 0000  |   ALU_Out = A + B;
----------------------------------------------------------------------
| 0001  |   ALU_Out = A - B;
----------------------------------------------------------------------
| 0010  |   ALU_Out = A * B;
----------------------------------------------------------------------
| 0011  |   ALU_Out = A / B;
----------------------------------------------------------------------
| 0100  |   ALU_Out = A << 1;
----------------------------------------------------------------------
| 0101  |   ALU_Out = A >> 1;
----------------------------------------------------------------------
| 0110  |   ALU_Out = A rotated left by 1;
----------------------------------------------------------------------
| 0111  |   ALU_Out = A rotated right by 1;
----------------------------------------------------------------------
VERILOG CODE:
module alu(

           input [7:0] A,B,                
           
           input [3:0] ALU_Sel,
           
           output [7:0] ALU_Out, 
           
           output CarryOut 
    
    );
    
    reg [7:0] ALU_Result;
    
    wire [8:0] tmp;
    
    assign ALU_Out = ALU_Result; 
    
    assign tmp = {1'b0,A} + {1'b0,B};
    
    assign CarryOut = tmp[8];
    
    always @(*)
    
    begin
    
        case(ALU_Sel)
        
        4'b0000: // Addition
        
           ALU_Result = A + B ; 
        
        4'b0001: // Subtraction
          
           ALU_Result = A - B ;
        
        4'b0010: // Multiplication
        
           ALU_Result = A * B;
        
        4'b0011: // Division
        
           ALU_Result = A/B;
        
        4'b0100: // Logical shift left
        
           ALU_Result = A<<1;
         
         4'b0101: // Logical shift right
           
           ALU_Result = A>>1;
         
         4'b0110: // Rotate left
         
           ALU_Result = {A[6:0],A[7]};
         
         4'b0111: // Rotate right
         
           ALU_Result = {A[0],A[7:1]};
          
          4'b1000: //  Logical and 
          
           ALU_Result = A & B;
          
          4'b1001: //  Logical or
          
           ALU_Result = A | B;
          
          4'b1010: //  Logical xor 
          
           ALU_Result = A ^ B;
          
          4'b1011: //  Logical nor
          
           ALU_Result = ~(A | B);
          
          4'b1100: // Logical nand 
          
           ALU_Result = ~(A & B);
          
          4'b1101: // Logical xnor
          
           ALU_Result = ~(A ^ B);
          
          4'b1110: // Greater comparison
          
           ALU_Result = (A>B)?8'd1:8'd0 ;
          
          4'b1111: // Equal comparison   
          
            ALU_Result = (A==B)?8'd1:8'd0 ;
          
          default: ALU_Result = A + B ; 
        
        endcase
    
    end

endmodule
# OUTPUT:
![image](https://github.com/Bhavyaa369/ALU/assets/161431563/65467138-1698-41ee-a972-8af183ebbc58)

