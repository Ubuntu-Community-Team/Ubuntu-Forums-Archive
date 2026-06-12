---
title: "Live CD hangs on Toshiba laptop"
date: 2008-03-23
forum: Installation &amp; Upgrades
---

### Post by mattpatey on 2008-03-23
Hi,

I want to try Ubuntu 7.10 on a Toshiba Satellite Pro A210 laptop (ATI Radeon XPress 200M Series graphics card), but I cannot make the CD work.

When I boot from the CD everything seems to go fine until some lines of text start appearing. 4 lines starting "var/lib/acpi-support/" have "no such file or directory" against them. Then it says it is starting the gnome environment or something similar and then the screen goes blank and the system freezes.

I have tried the reduced graphics driver option, but this does exactly the same thing. I am completely new to Linux, please could you give me some pointers on how to work out what's going on/how to fix it?

Thanks

---

### Post by Pumalite on 2008-03-23
Memory? You should install with the Alternate CD anyway, but you might need a lighter Desktop depending on your memory.

---

### Post by mattpatey on 2008-03-23
I've got 704 MB of memory. Is that a possible cause? I had assumed it was something to do with the graphics card.

---

### Post by Pumalite on 2008-03-23
Your memory is fine. Due to your video card I'd install with the Alternate CD.
Did you try 'Safe Graphics Mode'?

---

### Post by mattpatey on 2008-03-23
Yes, I tried with the reduced graphics option, but it didn't work. I'll try the alternative cd and see how that goes.

Thanks for your help.

---

### Post by Pumalite on 2008-03-23
You are welcome. Good luck.

---

### Post by mattpatey on 2008-03-23
Hi,

I have now tried installing using the alternate cd (selecting the option from the boot menu to install with an additional driver CD). 

When it gets to the stage where it says it is starting the Gnome desktop, the screen al ternates between being black and displaying the following 2 lines:

Checking battery state...       [OK]
Running local bcot scripts (/ekc/rc.local)   [OK]

After it does that a few times a different screen appears. It says something like:

"The display server has been shut down about 6 times in the last 90 secs. It is likely something bad is going on. Waiting 2 mins before trying again on display :0"

When I hit enter it waits 2 mins before doing the same alternating thing again.

What should I do next?

---

### Post by Pumalite on 2008-03-23
Try your luck with some boot parameters:
Boot parameters
[http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1](http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1)
[http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html](http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html)
[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
[http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html](http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html)
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)
[http://www.knoppix.net/wiki/Kernel-parameters-2.6.11](http://www.knoppix.net/wiki/Kernel-parameters-2.6.11)
noapic nolapic acpi=off pci=noacpi pnpbios=off vga=0x317 vga=791

---

