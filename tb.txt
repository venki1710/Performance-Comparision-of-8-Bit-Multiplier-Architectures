`timescale 1ns/1ps

module tb_wallaceTreeMultiplier8Bit;
    // Inputs
    reg [7:0] a;
    reg [7:0] b;

    // Outputs
    wire [15:0] result;

    // Instantiate the Unit Under Test (UUT)
    wallaceTreeMultiplier8Bit uut (
        .result(result),
        .a(a),
        .b(b)
    );

    initial begin
        // Monitor the inputs and outputs
        $monitor("Time = %0d: a = %8b, b = %8b, result = %16b (decimal: %0d)", 
                 $time, a, b, result, result);

        // Test Case 1
        a = 8'b00000001; // 1
        b = 8'b00000001; // 1
        #10;

        // Test Case 2
        a = 8'b00000010; // 2
        b = 8'b00000011; // 3
        #10;

        // Test Case 3
        a = 8'b00001111; // 15
        b = 8'b00001111; // 15
        #10;

        // Test Case 4
        a = 8'b11111111; // 255
        b = 8'b00000001; // 1
        #10;

        // Test Case 5
        a = 8'b11111111; // 255
        b = 8'b11111111; // 255
        #10;

        // Test Case 6
        a = 8'b10101010; // 170
        b = 8'b01010101; // 85
        #10;

        // Test Case 7
        a = 8'b11001100; // 204
        b = 8'b00110011; // 51
        #10;

        // Test Case 8
        a = 8'b01111111; // 127
        b = 8'b01111111; // 127
        #10;

        // Test Case 9
        a = 8'b00000000; // 0
        b = 8'b11111111; // 255
        #10;

        // Test Case 10
        a = 8'b10000000; // 128
        b = 8'b10000000; // 128
        #10;

        // End of test
        $stop;
    end
endmodule
