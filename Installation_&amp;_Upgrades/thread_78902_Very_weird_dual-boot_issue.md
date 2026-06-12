---
title: "Very weird dual-boot issue"
date: 2005-10-19
forum: Installation &amp; Upgrades
---

### Post by chipmonk on 2005-10-19
Hello everyone,

I am trying to make dual-booting computer with XP and Breezy. My computer already had XP installed on SATA disk (/dev/sda1), and I had one IDE-drive for files. I got new IDE disk, which I installed as a master of Primary IDE, and I installed Ubuntu on it. Installation went fine, and install program recognized my existing Windows XP and installed GRUB to /dev/hda. I changed boot order from BIOS to boot primarily from /dev/hda (or Ubuntu disk which contained GRUB in its MBR) and then try to boot from /dev/sda (XP). First time I tried to boot, it gave me error message along these lines:

Loading GRUB Stage 1.5Read Error

I rebootted, and my machine just ignored boot order and my (apparently) broken GRUB and directly booted to XP. I fiddled around with boot order, but I just wouldn't even try to boot from my Ubuntu disk. Using very good examples from this forum I tried to re-install GRUB to Ubuntu disk (this didn't change anything, there wasn't even errors, just XP) and then I tried to install GRUB to XP disk (this time GRUB loaded... or flooded screen full of GRUB GRUB GRUB). I tinkered with my menu.lst, but as far as I could determine, it was correct. I tried to re-install Ubuntu (twice), no change to behaviour. I tried to unplug my SATA drive to test GRUB, but I got "No system disk" at boot time.

So, now I am quite baffled as what to do next. I planned to unplug my Windows disk and try to install Ubuntu once more and test is my hard disk even capable of booting. Or I could probably try to install GRUB to my XP's MBR directly at installation time, and hope that installer does it better than I did :) As far as I know, hard disk should be working (it's brand new, installation on it went fine and I can mount it's partitions from Live-CD).

Any ideas are appreciated, thank you :)

---

