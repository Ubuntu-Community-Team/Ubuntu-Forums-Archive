---
title: "How to avoid XP crashing hal.dll/boot.ini with reinstall of Grub 2"
date: 2010-03-22
forum: Installation &amp; Upgrades
---

### Post by Trogdole on 2010-03-22
Okay, so I've had to reinstall Windows XP twice already, because apparently something is going wrong when I reinstall GRUB 2.

I want to know A) Is there a way I can boot Ubuntu from the windows boot.cfg?
B) Is there a certain order partitions have to be on a hard drive.
C) Is there any reason anyone can think of for this problem?

My XP never restarts after I the Grub 2 reinstall. I get different errors, like boot.ini, hal.dll, ntoskrnl.exe I think was the last one. I can't figure this out, I just want to dual boot. Technically I run Mint, not Ubuntu, does that matter? It's the latest release, Helena.

I can copy in some terminal code if I need to after work, just let me know what you guys need to help me with this.

I have sda1 as swap, sda2 as the main Mint, then sda3 is Windows then I have an extended partition (is that what it's called?) and inside that is the /home directory for Mint. Windows comes up as H:, I haven't livebooted yet so I got nothing more than that so far.

Please any help would be great, I'm worried about running out of my XP product key reuses. Is that possible?

---

### Post by efflandt on 2010-03-22
Usually when Windows says hal.dll is missing or corrupt, it really means that Windows is attempting to boot the wrong partition (possibly boot.ini issue or something in grub configuration changing something to different from reality).

I would put Windows on the first partition on the first drive (if you have more than one), and anything else after that.  Linux can boot from anywhere.

Some of my computers have an OEM recovery partition first, then Windows, then whatever I do with Linux.  I have not had any issues with grub or grub2, other than with splash if I change to a different DVI monitor with different native resolution (until I fix /etc/usplash.conf to native monitor resolution).

---

### Post by Trogdole on 2010-03-22
All right so I already installed everything. If I move it on GParted, is it going to be ****** up, since I'm changing it from H: to C: or whatever it will go to?

---

