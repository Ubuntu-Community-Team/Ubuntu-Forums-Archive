---
title: "Grub on a second drive - to MBR or not to MBR"
date: 2008-01-05
forum: Installation &amp; Upgrades
---

### Post by klichev on 2008-01-05
OK! Just now I tried dual-booting XP and Ubuntu 7.10. I have two hard drives and Windows XP is installed on the first. I then installed Ubuntu on the second with Grub placed in the MBR of the second drive (hd1). I then chain-loaded the NT loader. But every time I selected Ubuntu, I got:
```
GRUB GRUB GRUB Hard Disk Error
```
Well, back to Live CD, the find -> root -> setup procedure (again for the MBR of the second drive). New dd image. Now I just got GRUB as error message. I then swapped the loading BIOS sequence to load from the second hard drive first. The Grub menu showed, but whenever I tried to run anything I got
**Unable to mount drive** (or something like that)

OK, what's going on?

Should I try install Grub at:
(hd1,0) *(that's my /)*

---

### Post by Pumalite on 2008-01-05
Boot your Live CD and post:
sudo fdisk -lu

---

### Post by klichev on 2008-01-06
I got it, guys. I read the post of **paisley**, who explains that Grub hard codes the sequence for the given drive, and so the NT chain-load file should be taken from the MBR of the first Windows drive. Here's the post:

[http://www.oreillynet.com/cs/user/view/cs_msg/66218]("http://www.oreillynet.com/cs/user/view/cs_msg/66218")

In short:
1. Install Ubuntu on the second drive
2. Put the Grub loader in the MBR of the first (Windows) drive
3. Create file to chain NTLDR via **dd**
4. Fix the MBR of the first drive via Windows XP CD
5. Place the chain-load file and fix the **boot.ini**

---

### Post by modelmark on 2008-01-06
How do you move the mbr from the 2nd to the first (windows) drive ? I tried during install from the live cd with the advanced options to change (hd0) to (sda0), the grub failed to install and and my windows boot failed (later recovered)
Is there a way to first get everything running on the linux drive and then move the mbr and grub to the windows drive ?

---

