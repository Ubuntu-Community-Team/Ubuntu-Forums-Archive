---
title: "Ubuntu 18.04 freezes while installing"
date: 2019-08-02
forum: Installation &amp; Upgrades
---

### Post by ecolli on 2019-08-02
Hi everyone
I'm using [FONT=Arial]Win7 ultimate SP1 on my desktop PC and I want to have Ubuntu too.
Specs:
[/FONT][FONT=Arial]Processor: [/FONT][FONT=Arial]FX 6300 3.5Ghx, 4MB cache[/FONT][FONT=Arial]
[/FONT][FONT=Arial]RAM:8GB HyperX
[/FONT][FONT=Arial]Motherboard: N68 - GS4 FX
[/FONT][FONT=Arial]GPU: R7 240
[/FONT][FONT=Arial]Disk: 1TB
I prepaired a USB booteable (using Rufus with [/FONT][FONT=Arial]Ubuntu 18.04 .iso). I've put the USB and turned on my PC.  
At the begining desktop shows an error like "IRQ handler", and after that GUI Installion begins.
I've frozed always in different parts. I've never passed the 4 step. So I tried some stuff.
I've read that could be a GPU problem, so I tried using command line to boot with nomodeset option.
My steps are:
[/FONT][FONT=Arial]Ctrl+Alt+F2 in "Install" screen
login user ubuntu
[/FONT][FONT=Arial]sudo nano /etc/default/grub  
[/FONT]
[FONT=Arial]modify line to: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
[/FONT]
[FONT=Arial]ctrl+x[/FONT]
[FONT=Arial]sudo update-grub
And an error pops. failed to get canonical path of /cow.

I'm frustraded because I can't wait to much and I have to be very fast!
At the minute of using command line my PC freezes with a lot of messages "error IRQ handler" and I can't continue. I perform the previous steps REALLY fast.
So, any ideas? What can I do?
I don't get why changing that line /cow error appears, I can't see how they are related.

Regards [/FONT]

---

### Post by yancek on 2019-08-02
If you have windows 7, it is almost certainly a Legacy/CSM install as opposed to an EFI install.  If that is the case, you are only allowed 4 partitions and the amount of free space available is irrelevant.  So how many partitions do you have?

 Logging in as user ubuntu and attempting to modify the /etc/default/grub file will not work nor will updating grub.  It is a live DVD/USB which means it is read-only and any modifications made will be lost on reboot.  That is what the error "[FONT=Arial] failed to get canonical path of /cow" is telling you.

Have you tried both the install ubuntu and try ubuntu options?  Results the same or similar?

You might post some info on your hardware such as processor, RAM, etc.
[/FONT]

---

### Post by ecolli on 2019-08-02
I added my specs on top.
My disk have 990GB. Its distributed in
100MB reservated for System
660GB C:
330GB not assigned (here I want to install Ubuntu). I think its ok to install it.

I tried both options (Install and Try) and both ends with freeze screen.

---

