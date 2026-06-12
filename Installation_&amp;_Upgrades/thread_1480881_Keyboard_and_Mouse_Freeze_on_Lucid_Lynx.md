---
title: "Keyboard and Mouse Freeze on Lucid Lynx"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by iNaitvad on 2010-05-12
Hi, first of all, sorry for my bad english and thank you for your future help.

Ok, so i boot Ubuntu Live CD x86-64 on my Pentium D processor (with EMT64) all seems to boot fine, just that my keyboard and mouse are freezed. I search on some forums and a guy said to try with NOAPIC function, so i did that. It worked fine on the installation, but i didnt see any compiz effect (i suposse it was because i choose Install Ubuntu instead of TRY). 

Everything good until I restarded my PC (btw i have a ATI X200, on Karmic I used the built in driver, not ATI's, with compiz and everything else), my mouse was working before gnome launched the panels once the panels where there my keyboard and mouse stoped working. 
I suppose i must start ubuntu with noapic function on, but how to? And if that isnt the problem, what can i do? Help me please =D I use Ubuntu since Dapper Drake and I never have this problem.

---

### Post by oldfred on 2010-05-12
I do not know if it is a similar problem or not.

A year or so ago I put in a new motherboard. When I booted the mouse & keyboard did not work in grub but did in Ubuntu. I then found it worked with the ps/2 connection in grub so I was switching adapters to choose menu items in grub. It turned out to be a BIOS setting on USB mouse & keyboard vs ps/2 settings.

---

### Post by iNaitvad on 2010-05-12
Thanks, yeah i had the exactly same problem, but only some times, so i didnt mind... I had a Asus P5W DH DELUXE, it is a great mobo, i belive the issue was that my usb extension wasnt the best... 

Speaking about my current problem, it wasnt on grub (the new one that comes since 9.10), it was with Ubuntu 10.04. I found on the net howto put de noapic function. CTRL-E selecting the kernel i want to boot, but this will make me always type noapic... I didnt have enough time to found a better workaround, there is one for menu.lst (i think so) but its for grub legacy (the old one). Maybe i will try at night. Thanks anyway, i dont know if i should mark this as solved, haha... Maybe it is, maybe it isnt the best way, but it is solved, not perfectly, I just need to make it permanent, I will mark it as solved when i found the perfect solution, then i will post it right here.. =D

---

### Post by oldfred on 2010-05-12
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Search for this section:
# GRUB_CMDLINE_LINUX
If it exists, this line imports any entries to the end of the 'linux' command line (Grub Legacy's "kernel" line) for both normal and recovery modes. This is similar to the "altoptions" line in menu.lst
# GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
This line imports any entries to the end of the 'linux' line (Grub Legacy's "kernel" line). The entries are appended to the end of the normal mode only. This is similar to the "defoptions" line in menu.lst. For a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash". This line is where other instructions, such as "acpi=off" are placed.

---

### Post by iNaitvad on 2010-05-14
Thank you, i finally installed BURG and modify its configuration file, hahaha... but thanks anyway i will mark this thread as solved...

---

