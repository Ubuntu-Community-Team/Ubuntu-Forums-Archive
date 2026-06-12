---
title: "Grrrrrrub"
date: 2005-04-30
forum: Installation &amp; Upgrades
---

### Post by trash on 2005-04-30
sorry yet another grub issue...
I had win98 and Warty running very nicely together... 
hda1-win98 and
hdd1-warty

then i smoothly dist-upgraded to hoary, rebooted a few times(everything was fine), upped the clock from 266 to 291mhz. Booted into windows and everything was sweet, booted into hoary, got all kinds of boot errors happening and now grub is nothing but errors.

I've tried most of the fixes i can figure out from the forum here but nothing is helping. I decided to reinstall but now all i am getting from the hoary installer is
'attempt to mount a file system type ext3 in IDE1 slave, partition #1 (hdb1) at / failed.

i have taken the drive off of IDE2 because of the bug reports but still no diff.

Dunno why but my win98 boot floppy doesn't wanna boot so i have absolutely no way of getting into win or hoary. Though the live cd does run nicely.

Anyhow, what can i do???

---

### Post by trash on 2005-04-30
ok, the problem seems to be disks with 4092 cylinders.... dunno why it works fine the first install but i tried 4 disks all 4092, they all failed.... installing fine on a newer disk now.

booting Hoary live and using fdisk told me of the problems booting from 4092 cyl disks.

---

