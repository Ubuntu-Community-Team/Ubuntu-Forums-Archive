---
title: "ntfs partition raw error bc ubuntu"
date: 2009-12-09
forum: Installation &amp; Upgrades
---

### Post by bashirby on 2009-12-09
Dear all,
I have Win recovery on dev/sda1, Win7 64x on dev/sda2, had Ubuntu 9.10 on sda5 and swap was sda6. I was using this ubuntu program with the name of NTFS configuration or something in the lines of that and it forced my win7 partition sda2 to mount on startup. I couldn't get around that so I went ahead and did a wipe of ubuntu to reinstall it.
Using grub fixer, I wanted to get into win7 but apparently my windows 7 is now a raw partition (I DID NOT wipe it, I can assure you.)
I have ubuntu live and this is the error I get, [ATTACH]139232[/ATTACH] 
When I run the recovery console on windows using sda1 I get the following error messages
[ATTACH]139233[/ATTACH], chkdsk can't run bc it's raw, can't system restore, can't do anything.

I need to get data off of my sda2, otherwise I would do a clean reinstall. [SIZE=4]
Any help would be greatly appreciated. [/SIZE]
If need more info, let me know and I'll do my best.

---

### Post by lemming465 on 2009-12-12
I'd try running *testdisk* to see if could repair sda2 enough that you could run chkdsk on it from sda1.

---

