---
title: cs61c
date: 2024-06-09 12:02:25
categories: 
    - [课程相关,自学课程]
tags:
    - 自学
toc : true
---

还在学习中.....

<!-- more -->

# 课程内容
大概是计组？

## 笔记
还在学习中 只是暂时记录一下

### 寄存器


### RISC-V 常用指令集

详细请查询：

#### Some similar Instructions(with immediate)
|operation name|operand 1|operand 2| operand 3|meaning|
| :----: | :-----: | :-----: | :------: |:------|
|add(i)|s1|s2|s3(i)|s1 = s2 + s3|
|sub|s1|s2|s3|s1 = s2 - s3|
|sll(i)|s1|s2|s3(i)|shift left logical|
|srl(i)|s1|s2|s3(i)|shift right logical|
|sra(i)|s1|s2|s3(i)|shift right arithmetic|
|div|dst|s1|s2|s1 div s2|
|rem|dst|s1|s2|s1 mod s2|
|mul|dst|s1|s2|s1*s2 lower 32bits|
|mulh|dst|s1|s2|s1*s2 upper 32bits|

#### Data Transfer Instructions
一般格式： memop  reg, off(bAddr)
reg : register for operation source or destination
bAddr : address offset in bytes

|operation name|operand 1|operand 2|meaning|
| :----: | :-----: | :-----: |:------|
|lw|reg|off(bAddr)|load word|
|sw|reg|off(bAddr)|store word|
|lh|reg|off(bAddr)|load half word, upper 16bits with sign-extension|
|sh|reg|off(bAddr)|store half word, upper 16bits ignored|
|lhu|reg|off(bAddr)|load half word unsigned|
|lb|reg|off(bAddr)|load byte, upper 24bits with sign-extension|
|sb|reg|off(bAddr)|store byte, upper 24bits ignored|
|lbu|reg|off(bAddr)|load byte unsigned|
|and(i)|s1|s2|s3(i)|与|
|or(i)|s1|s2|s3(i)|或|
|xor(i)|s1|s2|s3(i)|Exclusive Or异或|

#### Branch on Conditions
|operation name|operand 1|operand 2| operand 3|meaning|
| :----: | :-----: | :-----: | :------: |:------|
|beq(Branch if equal)|reg1|reg2|label|If value in reg1 = reg2, go to label|
|bne(Branch if not equal)|reg1|reg2|label|If value in reg1 != reg2, go to label|
|blt|reg1|reg2|label|Branch less than|
|bge|reg1|reg2|label|Branch greater than or equal|

#### Transfer Instructions
· Jump(j)
    - j label === jal x0 label

· Jump Register(jr)
    - jr src
Used to return from a function(when src = ra).

· Jump and Link(jal)
    - jal (dst) label
    go to label,and store return address in ra(dst) register

· Jump and Link Register(jalr)
    - jalr dst src imm(offset)
    将当前指令的地址加上immediate的值，并将结果存储在dst寄存器中，同时跳转到src寄存器中的地址，并将下一条指令的地址存储在ra中
    - jalr rs, rd
    go to rs, and store return address in rd

ra = return address register, used to save where a function is called from.


#### Compare Instructions
|operation name|operand 1|operand 2| operand 3|meaning|
| :----: | :-----: | :-----: | :------: |:------|
|slt(i)|dst|reg1|reg2(i)|set less than(dst stores the value)|

#### Environment Call
·   ecall is a way to interact with the operating system
·   Functions depand on the value in register a0.
    —— Printing values
    —— Exiting th program
    —— Allocating more memory for the program

