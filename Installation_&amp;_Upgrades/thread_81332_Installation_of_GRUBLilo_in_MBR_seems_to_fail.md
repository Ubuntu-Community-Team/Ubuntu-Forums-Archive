---
title: "Installation of GRUB/Lilo in MBR seems to fail"
date: 2005-10-24
forum: Installation &amp; Upgrades
---

### Post by Coldie on 2005-10-24
Hi there,
recently I tried to install Ubuntu on my external USB HDD. The installation itself is pretty straight forward... but just up to the point, where I need to install a boot manager. I've already read some threads about installing linux on an external USB device. So I always add USB support to the bootimage. Afterwards I install GRUB in the MBR of my USB-HDD, but after rebooting the PC never finds a MBR on the HDD ("**Searching for Boot Record from USB HDD..Not Found**"). In my opinion it's not an hardware issue (booting from USB stick works and my USB HDD is - according to the manufacturer - "bootable").

BTW. I also tried to install GRUB manually (which seems to work, since I get no error message), BUT using LILO fails always for some reason, I don't know. Lilo simply hangs after calling it.

Can someone give me a proper lilo.conf??
My USB HDD is /dev/sdc and my /boot can be found on /dev/sdc1 (sda & sdb are used for a win Software-RAID, so I don't want to touch them)

Thanks in advance and sorry for that long posting ;) 

Daniel

---

### Post by DaBruGo on 2005-10-25
Coldie,

I don't know if this will help you, but here are a few posts from me on the external USB setup

[http://www.ubuntuforums.org/showthread.php?t=80811](http://www.ubuntuforums.org/showthread.php?t=80811)

DAVE

---

