---
title: "Dual Boot Win 7 Grub failing"
date: 2010-03-25
forum: Installation &amp; Upgrades
---

### Post by The Hungry Lumberjack on 2010-03-25
So I followed the usual guides to fixing the nasty windows boot sector nonsense and I am still having problems.

I installed 7 on a separate hard drive (sdb) and it works mostly fine.

I used the live cd to load up a copy of Karmic (early version) and installed grub (sudo apt-get install grub).

Did the usual series of commands:

sudo grub

find /boot/grub/stage1

but I get "Error 15: File not found"

I know there is a script out there that spits out a ton of info about grub but I can't find it again.

The other OS on the first hard drive (sba) is Karmic and up to date. I have no idea why it can't find stage1 as there are a ton of other files in the /boot/grub so I would expect it to be no problem.

I tried the arrow in the dark and went
grub> root (hd0,0)
grub> setup (hd0)

but it gave me this:
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Any help? (also, I tried fdisk -l and it said: bash: /sbin/fdisk: Input/output error)

---

### Post by andrewthomas on 2010-03-25
I think the problem is that you are using legacy grub commands when you have grub2 installed.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Mark Phelps on 2010-03-25
When you install Karmic afresh, it automatically installs GRUB2 by default.  If you then went and forced an installation of legacy GRUB, that could be most of your problem.

Under GRUB2, all you would have to do is boot into Karmic and run "sudo update-grub" from a terminal -- and GRUB2 would automatically scan for, and find, your Win7 install, and create the correct GRUB menu entry for it.

Sorry, don't know how to clean up a system that has BOTH versions of GRUB installed.  It may be better to remove both and reinstall only GRUB2.

---

### Post by The Hungry Lumberjack on 2010-03-26
Wow I feel silly; refreshing grub2 worked perfect. Gah.

---

