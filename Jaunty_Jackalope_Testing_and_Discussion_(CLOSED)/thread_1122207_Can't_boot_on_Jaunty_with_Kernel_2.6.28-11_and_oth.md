---
title: "Can't boot on Jaunty with Kernel 2.6.28-11 and other problems"
date: 2009-04-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Marlonsm on 2009-04-10
I've installed Jaunty beta today, but I'm having some problems.

One of them is that I can't boot on the 2.6.28-11 Kernel, I need to change to 2.6.27-11. Or else I get [this screen]("http://img125.imageshack.us/img125/3373/img1289.jpg"), and nothing happens after it.

I've had some bugs with compiz, like the desktop changing not actually moving the desktop, but only the windows over it, unless I disable it and enable again.

I tried running the new Computer Janitor, but all it has done was to uninstall Google Earth.

I've also noted that the computer is overall slower (including the boot time).


I'm aware it's a beta, so I shouldn't expect a bug-free system, but I didn't expect that problems.


My computer is:
-C2D E6420
-2gb Kingston RAM
-Geforce 8600Gt
-Asus P5VD2 mother board
-160Gb Samsung HD

And I have Ubuntu installed using Wubi(the most likely cause of that problems).

So if things doesn't get better until the release, I'll just download the .iso and install from scratch.

Did anybody have problems like these?

---

### Post by pomalin on 2009-04-10
may be your bug is the same as mine, can you boot the live cd ? 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/343268]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/343268")

---

### Post by Marlonsm on 2009-04-10
> **pomalin said:**
> may be your bug is the same as mine, can you boot the live cd ? 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/343268]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/343268")

I don't have the live CD, I updated the "update-manager -d" way.

---

### Post by pomalin on 2009-04-11
So, can you download an image of live cd and test it ?

---

### Post by Marlonsm on 2009-04-11
> **pomalin said:**
> So, can you download an image of live cd and test it ?

I have no CDs left right now, I'd have to go out and buy some, and as it's a holiday... also, I'm not using my computer right now, so I can't even start the 5-hour download of the ISO. Sorry. :(

---

### Post by pomalin on 2009-04-11
no prblems, it's just to see if you have the same bug so you can add a comment on the bug at launchpad.

---

### Post by Life On Mars on 2009-04-13
I have same problem I think with same motherboard as original poster. Added info to your bug report.

---

### Post by Tompalaz on 2009-04-15
Hi, I have a similar problem.
When I try to boot with the 2.6.28-* kernel I get a kernel panic.
It says something like:
> Kernel Panic Cannot sync - attempt to kill init!
and then everything freeze.   

I tried to boot the kernel withot the quiet and splash mode.
What i get out of it was:
Write protecting to read only 
Kernel Panic
dumping ftrace buffer
ftrace buffer empty.

I'm always getting this kernel panic. I've tried to boot with a CD, USB  and after a update-manager -d.

I tried the USB memory in school and it worked perfect. Can it be something with my hardware config?
It's strange that the panic comes directly after I choose 2.6.28-* from GRUB.
/T

---

