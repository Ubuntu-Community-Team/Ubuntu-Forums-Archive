---
title: "need help - GCC compiler installation on ubuntu 7.10"
date: 2008-01-20
forum: Installation &amp; Upgrades
---

### Post by tanu_10 on 2008-01-20
Hi all,

in ubuntu 7.10, OS, i tried to check the GCC compiler.
I wrote simple hello world program, compiled using GCC command in terminal, i got the following error:

s$ gcc test.c
test.c:1:19: error: stdio.h: No such file or directory
test.c: In function â€˜mainâ€™:
test.c:5: warning: incompatible implicit declaration of built-in function â€˜printfâ€™


How do i install GCC compiler on ubuntu 7.10, i dont have the internet
connection in ubuntu 7.10. so please help.
I also want to install GDB debugger, binutils toolchain.
Or how do i check if all these are installed in ubuntu.

any suggestions welcome.

thanks.

---

### Post by Sef on 2008-01-20
Build-Essential which has that compiler is on the install cd, so open the terminal (Applications > Accessories > Terminal), and type in this command:

```
sudo apt-get install build-essential
```,

you may be able to install it without being connected to the internet.   You will need to have the install cd that you used to install.

---

### Post by tanu_10 on 2008-01-20
Hey, thank you.

its working now. i am able to compile a simple C program.:)

> **Sef said:**
> Build-Essential which has that compiler is on the install cd, so open the terminal (Applications > Accessories > Terminal), and type in this command:

```
sudo apt-get install build-essential
```,

you may be able to install it without being connected to the internet.   You will need to have the install cd that you used to install.

---

