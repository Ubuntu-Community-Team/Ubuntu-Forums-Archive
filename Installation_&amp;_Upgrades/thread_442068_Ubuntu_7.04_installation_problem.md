---
title: "Ubuntu 7.04 installation problem"
date: 2007-05-13
forum: Installation &amp; Upgrades
---

### Post by AlexDudko on 2007-05-13
I downloaded Ubuntu 7.04 and tried to install it. On my laptop everything's gone just fine, but on my  another desktop, while trying to boot first as LiveCD, the screen changed to terminal with the following message
/bin/sh: can't access tty; job control turned off.

Ubuntu 6.10 CE installed on that desktop perfectly.
Any Ideas what to do?

---

### Post by starcraft.man on 2007-05-13
> **AlexDudko said:**
> I downloaded Ubuntu 7.04 and tried to install it. On my laptop everything's gone just fine, but on my  another desktop, while trying to boot first as LiveCD, the screen changed to terminal with the following message
/bin/sh: can't access tty; job control turned off.

Ubuntu 6.10 CE installed on that desktop perfectly.
Any Ideas what to do?

[Here]("http://ubuntuforums.org/showthread.php?t=415009&highlight=can%27t+access+tty") is the main thread with this. The problem almost always stems from multiple hardware that the kernel has trouble reading. The easiest solution is to unplug everything except 1 HDD and 1 CD/DVD drive, that usually gets ya to boot. If not, you can post in the thread to get a work around :)

---

### Post by jakelute on 2007-05-13
Hi! I'm completely new to Ubuntu. In fact, I  haven't even tried it yet! Except on the Live CD. I'm very excited about getting rid of Windows and using Ubuntu instead. I have long been fed up with Windows, and I applaud the whole principle of free and open source software.

But I too have been finding that everything freezes in the middle of installing Ubuntu on my PC. I don't get any error messages. It just stops and goes quiet and nothing happens so I press the reset button and start attempting the installation all over again. It usually freezes during step 4 or 5 of the 7-step process, though I once even got as far as 73% of the way through installing the system (copying files) before it froze.
I have two internal HDs; one is SATA and the other is connected the old-fashioned way (can't remember what it's called). I also have three disk drives: a floppy, a CDRW, and a DVDRW. Maybe the installer is getting confused about all this hardware?
Sorry to be ignorant.
I'd rather not open the case and disconnect a drive. That idea makes me nervous. But if it's the only way to get up and running......
Thanks very much in advance for any suggestions.
J.

---

### Post by jakelute on 2007-05-13
Can I add a quick update to my previous posting?
I've now managed to complete the installation process, and was told by the on-screen instructions to restart and remove the disk. I've done this. But when I restart, I get the message "error loading operating system", and Ubuntu doesn't load.
:(

---

### Post by AlexDudko on 2007-05-13
Thank you very much for the help! I tried everything mentioned in the thread but it didn't help. I upgraded the bios and it booted just fine! Still don't know what the problem was. Thanks once more!

---

### Post by AlexDudko on 2007-05-13
> **jakelute said:**
> Can I add a quick update to my previous posting?
I've now managed to complete the installation process, and was told by the on-screen instructions to restart and remove the disk. I've done this. But when I restart, I get the message "error loading operating system", and Ubuntu doesn't load.
:(

You've mentioned you have two HDD's. Have you installed your /boot or / partition on the primary one?

---

### Post by jakelute on 2007-05-13
Yes....

---

### Post by bulldog on 2007-05-13
Change in the BIOS boot from cd first into boot from hdd first,maybe it helps.

---

### Post by jakelute on 2007-05-13
Thank you very much, I'll try it.

---

### Post by carbonrcks on 2007-05-22
jake:  get anywhere with that problem.  I'm encountering the same error (error loading operating system) after good, clean installation and subsequent reboot.  Is it a SATA HDD issue?  

My components:

ASUS M2N-SLI Deluxe Socket AM2 NVIDIA nForce 570 SLI MCP ATX AMD 
AMD Athlon 64 X2 5200+ Windsor 2.6 GHz 2 x 1MB L2 Cache Socket AM2 Processor
Patriot eXtreme Performance 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Dual Channel Kit
Western Digital Caviar SE16 WD3200AAKS 320GB 7200 RPM 16MB Cache SATA 3.0Gb/s
Sony NEC Optiarc Black AD-7170S-0B 18X SATA
EVGA 512-P2-N548-TX GeForce 7600GS 512MB 128-bit GDDR2 PCI Express x16 Video Card
Creative Sound Blaster X-Fi XtremeGamer 7.1 Channels 24-bit 96 KHz PCI interface

Thanks in advance for anyone with advice.  I'm around and can answer question pretty quickly.

errors after successful install, reboot error,

---

