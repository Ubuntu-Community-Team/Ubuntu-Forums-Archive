---
title: "installation freezes, 64-bit processor"
date: 2006-08-28
forum: Installation &amp; Upgrades
---

### Post by user687 on 2006-08-28
Hi there!
I'm trying to install ubuntu 6.06, desktop 64-bit version, from livecd on my fujitsu-siemens scaleo p. Unfortunately, the installation crashes every time, even though I reformatted / with ext3 (30GB) and the swap partition (2GB). The Live-Cd works fine.

Details:
A64X2 3800+
Chipset NVIDIA nForce4 CK8-04
2x 250 GB hdd
2x 1024 MB ram

Can somebody help me?

Thanx in advance,
Peter

---

### Post by kshymkiw on 2006-08-28
Are you doing manual partition setup or erasing the entire hard disk?

---

### Post by user687 on 2006-08-28
I'm doing manual partition setup, because I have several partitions on sdb (sda is used for windows):
sdb1: fat32, used for sharing files with windows
sdb2: primary
[INDENT]sdb3: reiserfs, suse 10.1[/INDENT]
[INDENT]sdb4: swap, 2GB[/INDENT]
[INDENT]sdb4: reiserfs, /home, 50 GB[/INDENT]
[INDENT]sdb5: ext3, mountpount: / for ubuntu[/INDENT]

is there anything wrong?

---

### Post by user687 on 2006-08-29
i checked all the "normal" errors:

I ran Memtest - no errors
I checked my iso + cd - everything ok.
The installation always freezes at "copying files.. " at different percentages.

Is it problem that my hd is a sata device?

I read through many threads, but i couln't find a solution.

Peter

---

