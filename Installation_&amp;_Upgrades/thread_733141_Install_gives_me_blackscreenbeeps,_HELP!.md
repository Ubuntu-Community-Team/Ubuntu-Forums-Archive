---
title: "Install gives me blackscreen/beeps, HELP!"
date: 2008-03-23
forum: Installation &amp; Upgrades
---

### Post by jkalex05 on 2008-03-23
I made a 50gb partition for Ubuntu. Restarted and started with the install procedure.

It started loading and then right after it seemed it loaded. I started hearing beeps and the screen went black (standby).

Here are my computer specs:

Intel Q6600 Quad-Core 2.4ghz
3gb DDR2 6300
Nvidia 8800GT OC
x86 based system

Any info would be appreciated.

---

### Post by buntu_Geek on 2008-03-23
Did these happened after finishing the installation step or what???

And give the exact scenario when this black out happened...???( the sequence of events...) 

It would be helpful for diagonsing your problem....

---

### Post by Pumalite on 2008-03-23
Are you dual booting with Vista? If so, did you partition from WITHIN Vista before attempting installation of Ubuntu?

---

### Post by jkalex05 on 2008-03-23
I did the partition within vista.

This happened after the selection of install. I selected normal install.

Then Ubuntu loading screen came up. After it loaded it started beeping and screen went black.

edit: should I try with low graphics install?

---

### Post by buntu_Geek on 2008-03-23
yes.... since you have NVDIA graphics card... you have to install in a low graphics mode...
I have seen many posts that talk about some extra to install ubuntu when such problem arises...coz of the graphics card....

---

### Post by Pumalite on 2008-03-23
Once IN the system, install the appropriate driver (169.12)

---

### Post by jkalex05 on 2008-03-23
Tried Starting ubuntu in low graphics mode and still got the beeping and black screen....

---

### Post by Pumalite on 2008-03-23
Time to try some boot parameters:
[http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1](http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1)
[http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html](http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html)
[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)
Here is the guide:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
[http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html](http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html)
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)
[http://www.knoppix.net/wiki/Kernel-parameters-2.6.11](http://www.knoppix.net/wiki/Kernel-parameters-2.6.11)

Start with the most common ones:
noapic nolapic acpi=off pci=noacpi pnpbios=off vga=0x317 vga=791

---

### Post by jkalex05 on 2008-03-23
Im going to use the alternate cd method and see if that works.

---

### Post by buntu_Geek on 2008-03-23
I also suggest you to try a 32 bit distro for installation.. as i have personally many problems when it comes to an intel motherboard....( which actually doesnt truely a 64 bit processor... internally in its architechtural design as an AMD...)

Secondly i suggest you to view this thread before proceeding,....

[http://ubuntuforums.org/showthread.php?p=3645072](http://ubuntuforums.org/showthread.php?p=3645072)

---

### Post by Pumalite on 2008-03-23
Good idea too. You might need the boot parameters anyway.

---

### Post by jkalex05 on 2008-03-23
Let me say, I am a LINUX NOOB!

I booted off the alternate cd. Right away I got a PCI: Unable to allocate Memory and some other numbers error. However the install process started.

I got to Installing and Software and got 6% through where it got stuck.

I checked disk integrity no problem.

I installed grub and tried to boot ubuntu. I got a black and white text loading screen it got to my internet mask and asked for a password and wouldn't get anywhere passed that. So I don't think I got a GUI or anything.

Any idea what I should do?

---

### Post by halln on 2008-03-24
have you try to change your monitor yet. I solved mine with the same problem by changing my monitor. You can try by barrowing one to isolate your problem. I hope this helps.

---

