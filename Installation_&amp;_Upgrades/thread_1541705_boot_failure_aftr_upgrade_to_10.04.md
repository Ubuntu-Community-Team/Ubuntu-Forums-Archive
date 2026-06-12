---
title: "boot failure aftr upgrade to 10.04"
date: 2010-07-29
forum: Installation &amp; Upgrades
---

### Post by wclarowe on 2010-07-29
I have 3 separate hard drives, I IDE and 2 SATA.  The IDE has side by side installation of Windows XP and Ubuntu.  The 2 sata drives each have Ubuntu only.  I upgraded the 2 separate drives to 10.04. with no problems  I then upgraded the dual boot Ubuntu to 10.04 and it would no longer boot  I formatted the partition and did a clean install of 10.04  Thereafter the Ubuntu on the dual boot drive will boot but windows will not nor will either of the 2 separate drives.  Results text from boot info search is attached.  Any help will be appreciated.  I can access the 2 Ubuntu drives through the funcitonal Ubuntu on the dual boot drive, but cannot boot them.

---

### Post by dino99 on 2010-07-29
boot on lucid and into a console:

first remove menu.lst (from grub1) if it exist

then:

sudo grub-mkconfig
sudo update-grub

you might set bios on ahci mode for better performance and select the hdd to boot on first position

*** only grub-pc and grub-common have to be installed on /dev/sdx ( x= the hdd mbr where you boot)

---

