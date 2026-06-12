---
title: "Ubuntu Install on Windows 7 &amp; WinServer 2008"
date: 2010-05-23
forum: Installation &amp; Upgrades
---

### Post by nana336 on 2010-05-23
Hi Experts

I'm in a strange situation. I Installed Ubuntu 9.10 on perfectly working dual boot computer (I have Win7, WinServer 2008 & Mac OSX). After Installation, GRUB consolidated Win7 & WinSer 2008 and just put WinServer2008. Windows 7 totally disappeard. I'm sure it did't go any where, but GRUB did some consolidation and put just WS 2008.

**Before Ubuntu 9.1.0 Install my Dual Boot OS are**
Win7
WinServer 2008 &
Mac OS X

**After Ubuntu 9.1.0 Install my Dual Boot OS are**
Ubuntu 9.1.0
Windows Vista Loader - This is WinServer 2008 &
Mac OS X

UR Expert help is appreciated and may help other community members.

Thanks
Naren

---

### Post by darkod on 2010-05-23
What happens when you select winserver in the menu? It should show you another menu with win7 and winserver.

---

### Post by nana336 on 2010-05-23
Actually to be more specific

**After I install Ubuntu, the multi boot shows**
Ubuntu (there are 6 diff Ubuntu stuff)
Windows Vista Loader (This is WinServer 2008)
Mac OS X

When I select Windows Vista Loader, its starting WinS2008 directly. Win7 not at all there any where in GRUB, just wondering where it hide or which GRUB stuff made it hide totally in boot...

THX
Nana

---

### Post by darkod on 2010-05-24
It seems the win7 boot files are missing, and grub2 relies on detecting the boot files.

If you run the boot info script as instructed here:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

it will show us more. Post the content of the results file if you have any questions.

---

### Post by nana336 on 2010-05-24
Here are Results after running the script & and also my grub file. I try to tweek waht ever, its not holding Win7. Even in my grub, u can see it messed up my OS X.

Your help will be greatly appreciated. I want my old
Ubuntu
Win 7 (This is only missing)
WinServer 2008 &
Mac OS X

Thanks
Nana

---

