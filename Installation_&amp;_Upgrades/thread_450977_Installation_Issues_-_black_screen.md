---
title: "Installation Issues - black screen"
date: 2007-05-21
forum: Installation &amp; Upgrades
---

### Post by RaiSuli on 2007-05-21
Hi,

just built a new computer and tried to install a Kubuntu/Vista dual boot system. Kubuntu 64bit Feisty wouldn't get past the welcome screen - it was followed by a black screen -  the same with Ubunty 64 Feisty. Kubuntu 32bit Feisty installed fine, but when the system rebooted it told me the hd hadn't been checked in 43000 days. It checked, rebooted which was followed again by a black screen, nothing else.

I tried the following: 
- burning the cds with a different cd-rom
- downloading cds again
- installing Kubuntu in safe graphics mode

My system specs are:
Intel Dual Core E6600 processor
Asus P5N-E SLI mainboard
Nvidia GF8800 GTS
400GB WD hd

I would love to run Kubuntu again, especially the 64bit version, now that my system can take it, but I've no idea where to go from here. Any help would be greatly appreciated!

---

### Post by RaiSuli on 2007-05-22
/bump

Can anyone help?

---

### Post by siteguru on 2007-05-22
I had a similar issue with Ubuntu 64 dual boot with XP pro. I could boot OK from the grub menu in Recovery Mode but in normal mode I would only get a black screen.

What I did was amend the menu.lst file (/boot/grub/menu.lst ?? ) to remove the word **splash** from the kernel line for the normal boot and all seems OK now (apart from getting a verbose boot, but I get through to the login screen properly so who cares? 8) )  Not saying this will help you though).

---

### Post by RaiSuli on 2007-05-22
Thanks. Didn't work for me, but I got around the issue by installing Kubuntu 32bit from a flashdrive. 64bit still didn't work, but at least I can post this from Linux now. ;)

---

