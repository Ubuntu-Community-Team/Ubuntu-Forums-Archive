---
title: "Grub message biosdisk read error"
date: 2010-01-19
forum: Installation &amp; Upgrades
---

### Post by aovermy on 2010-01-19
Hardware:
2400 XP AMD CPU
Phoenix Bios around 2003
6 SATA drives, 1 PATA drive

SATA drives identified as /dev/sda - /dev/sdf
PATA drive identified as /dev/sdg
the motherboard bios will not allow boot off of SATA drive.

OK, so I installed mythbuntu 9.10 from CD, and chose to install it to the PATA drive at /dev/sdg, I chose manual partition and have:

part # 1: 6 G /boot
part # 2: 6 G swap space
part #3: 383G /

Install went fine until reboot. On reboot nothing happened (no system disk was found). Did a little research and found out about /boot/grub/device.map.

I used the livecd with chroot etc. to change device.map such that hd0 refers to /dev/sdg, hd1 /dev/sda, hd2 /dev/sdb ... Did update-grub and now I get:

grub-rescue> (progress I suppose).

at grub-rescue, I can ls (hd0,1)/ and it sees the boot partition. Running set shows that prefix and root are both set properly, so I can also do ls / and see boot partition. 

I am able to grub-rescue>insmod (hd0,1)/grub/help.mod and a few other mods. But if I try:
insmod (hd0,1)/grub/normal.mod or insmod(hd0,1)/grub/linux.mod I get biosdisk read error, even though those files are there when I do ls (hd0,1)/grub. 

Any ideas?

---

### Post by aovermy on 2010-01-20
Well, I gave up on this as it was just not working despite all my efforts. I finally used the ubuntu alternate installer and chose lilo and... it boots right up now. I'm in the process of installing the mythbuntu-desktop.

So going forward is this going to cause me massive troubles? That I have lilo instead of grub? Obviously when I install new kernels, I'll need to rerun lilo, and upgrades will probably involve using alternate installer or other means.

---

