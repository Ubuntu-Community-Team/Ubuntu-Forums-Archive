---
title: "Ubuntu 10.4 LTS Boot Error"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by Cibomatto2002 on 2010-04-30
When I burn a iso of Ubuntu 10.4 LTS it will not boot all I get on the screen is a Box = stick man that's the only way I can explain it if I had a camera I would take a picture of it. Now I can install Ubuntu 10.4 LTS in Windows 7 with Wubi also checksum checks out correct.

E machine: ET1831-07

Specifications:

# Intel Pentium Dual-Core Processor E5400 (2.7GHz, 2MB L2 Cache, 800MHz  FSB)
# Windows 7 Home Premium 64-Bit
# NVIDIA GeForce 7050 Chipset
#  4GB DDR2 Dual Channel Memory
# 750GB SATA Hard Drive
# 16x DVD  +/- RW SuperMulti Drive
# High Definition Audio with 7.1 Channel  Support
# Multi in 1 Digital Media Card Reader
# 10/100 Fast  Ethernet LAN
# 6 USB Ports (2 Front)
# PS/2 Keyboard & PS/2  Optical Mouse

---

### Post by plucky on 2010-04-30
> all I get on the screen is a Box = stick man 

Hit the space bar or enter key when that screen comes up and it will take you the choose language screen.After that it will go to the menu screen.

Run the check CD from there.

Good Luck

---

### Post by Cibomatto2002 on 2010-04-30
Thanks [plucky]("http://ubuntuforums.org/member.php?u=317619") pressing enter took me to the Ubuntu screen but the computer froze up when I got there i'm going to download the ubuntu-10.04-alternate-i386.iso thanks for your help.


I got a picture of what I was talking about


[[IMG]http://img408.imageshack.us/img408/8149/dcp0488.jpg[/IMG]]("http://img408.imageshack.us/i/dcp0488.jpg/")

Uploaded with [ImageShack.us]("http://imageshack.us")

---

### Post by giruzz on 2010-04-30
> **Cibomatto2002 said:**
> Thanks [plucky]("http://ubuntuforums.org/member.php?u=317619") pressing enter took me to the Ubuntu screen but the computer froze up when I got there i'm going to download the ubuntu-10.04-alternate-i386.iso thanks for your help.


I got a picture of what I was talking about


[[IMG]http://img408.imageshack.us/img408/8149/dcp0488.jpg[/IMG]]("http://img408.imageshack.us/i/dcp0488.jpg/")

Uploaded with [ImageShack.us]("http://imageshack.us")

Same issue here. I think that the issue lies with the latest kernel.

I have installed the RC and I have played a bit...

Kernel 2.6.32-21 works fine.
Kernel 2.6.32-31 (or whatever is the latest version) doesn't boot. 

Same with the CD...it doesn't want to install..it get stuck after a with an ugly black screen.

Any suggestions?

giruzz

---

### Post by Gyanos422 on 2010-04-30
i think i have the same problem. Haven't tried the RC but i couldn't boot correctly off the cd either.  I burned 2 copies and no luck. I installed 9.10 and upgraded from there.  took longer but i had to other choice

---

### Post by Cibomatto2002 on 2010-05-01
The ubuntu-10.04-alternate iso fixed my problem.

---

### Post by Rackstar on 2010-05-01
This sounds like this bug:
[https://bugs.launchpad.net/ubuntu/+bug/572868](https://bugs.launchpad.net/ubuntu/+bug/572868)

---

### Post by bquietndrive on 2010-06-08
i got a problem with the ubuntu boot cd i restart the pc, run from cd then a bit after appears a error message "Installation Failed" " The installer encountered an unrecoverable error. a desktop session will now be run so that you may investigate the problem or try installing again." i burned over 5 cd's at various speeds an always appears this message i try to install by entering the live cd but it doesn't install. can anyone help please.

Thanks.

---

