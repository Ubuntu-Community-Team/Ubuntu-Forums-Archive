---
title: "[Solved] After installation problem"
date: 2013-03-16
forum: Installation &amp; Upgrades
---

### Post by speedon on 2013-03-16
Hi, I'm a new linux user. 

I have installed linux 12.10 (first the 32bit one and after the 64).

I write because since i have installed ubuntu + grab ,a problem arose:

Frequently, when I start windows (seven 64bit), the OS start without recognising touchpad neither keybord, and with a resolution completely out of phase (640 x480 pixels or something like that) forcing me to force shutdown the PC.
The only thing I noticed is that if I put the external mouse is sometimes recognized and allows me to restart the pc without forcing shutdown.

Can you help me ???

---

### Post by tgalati4 on 2013-03-16
Did you have dual boot working correctly with the 32-bit installation?  Did Windows7 boot OK and work correctly as well as Ubuntu boot and work correctly?  Then you installed 64-bit Ubuntu and did it work correctly?  Seems like you are either in "Safe Mode" in Windows7 or you have some corruption that needs fixing.  Typically when installing on a dual-boot machine, you need to run CHKDSK on the Windows partition to fix it after shrinking the partition or Windows will have a fit.  Hold down the F8 key while booting Windows and select "Safe Mode--Command Prompt".  Once booted into a command line, run CHKDSK /F.

What model is the machine?

---

### Post by speedon on 2013-03-16
Firs of all, thank you very much for your reply.

I installed (by mistake) first the version at 32 bit, and the day after I put the 64 bit version. 
But in this little period of time the problem occurred (if i remember, at first boot of windows).

It not seems that it starts the with the "safe mode" (the desktop is ok, there are also available the widget,  and in "safe mode" the keyboard should have to work correct, I suppose).

I will try with the chkdsk, and i'll let you know the result.

My machine is an Intel® Core&#8482;2 Duo CPU T5550 @ 1.83GHz × 2     with a 3 gb of RAM.

---

### Post by speedon on 2013-03-16
I have performed the chkdsk, and the problem shows up again. 

But I have noticed a new detail. 

[B][SIZE=3]The problem shows-up at the first win boot, after a linux boot.
[/SIZE][/B]

---

### Post by speedon on 2013-03-17
After many tests, I have finally solved the problem, and I report the solution for who is interested in:

[B]
[SIZE=3]==>  THE PROBLEM WAS IN THE BIOS, I HAVE UPDATED IT AND ALL WORK GOOD

[/SIZE][/B][SIZE=3][SIZE=1][SIZE=2]
I hope that the solution can help someone[/SIZE][/SIZE][/SIZE][SIZE=3][SIZE=1][SIZE=2].

**==> WARNING: after the bios update (at least in my case), windows don't wont to start (Blue Screen Of Death) ==> The update of the bios changed some optron of the bios itself , I had to change only the setting "ATA ... something ..." in "COMPATIBILITY" and all worked good.**[/SIZE][/SIZE][/SIZE]

---

