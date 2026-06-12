---
title: "Flex and bison installations"
date: 2008-05-22
forum: Installation &amp; Upgrades
---

### Post by srohit24 on 2008-05-22
Can somebody help me to install flex and bison in ubuntu 7.04??

I have tried installing, but there is error in lex.yy.c file when i compile my files.

the lex filename command works properly, but the next command of cc lex.yy.c has numerous weird errors. Accoring to me the program is correct, as its only a few lines.

Hlep will be appreciated

---

### Post by roelpeeters on 2008-05-22
Hi,

Could you also show us your lex file and the commands that you use?

---

### Post by sumankumardey on 2010-02-26
if lex command is working then it means that you have no problem with installation

let me give you the proceedure how to compile and run

1)     lex programname.l
2)     cc lex.yy.c -o filename -ll
3)    ./filename
note in the last step their is a dot

---

