---
title: "Cannot install Fiesty on External HDD"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by x3ros on 2007-05-05
Just wondering if anyone could offer any insight or advice on the problem i seem to be having...

i have just gotten myself an external hdd, and established three partitions on it..

sda1 = /
sda2 = swap
sda3 = ntfs

ive unpliugged my internal hard-drives and installed ubuntu 7.04 to my external hard drive, and done a grub-install /dev/sda, which installed without issue

my m/b supports booting from USB devices, yet when i select the USB drive as my prefered booting method, it simply ignores it and jumps to cdrom, no errors, nothing..it simply ignores it

ive been pulling my hair out for about three days now, and every forum or bit of information i have come across so far has lead to false hopes and more disapointment

my last attempt was to try and boot from my internal hard drive, and once i got to grub, change the boot parameters to point to the external hard drive.... as far as grub was concerned i only have two hard drives installed (both internal ones) it couldnt even see the external one

i have checked my configuration for menu.lst, devices.map and anything else i could percieve as being relevant.

very rare is it that i get on forums requesting help, but i have reached my limits, i have exhausted my knowledge and creativity, and spent hours on this and other linux related forums to no avail.

can anyone point me in the right direction ?

Thankyou in Advance.

---

### Post by gjm777 on 2007-05-06
I have this issue as well. I can install to an external usb hard drive just fine.
Once I reboot and try to boot off the external drive it goes right to a grub prompt.
It can't even find /boot/grub/stage1 or stage2 for that matter.

It's almost like grub cant see the drive at all.

x3ros,

In your BIOS is there a legacy USB setting by chance?
You might have to enable that.

---

