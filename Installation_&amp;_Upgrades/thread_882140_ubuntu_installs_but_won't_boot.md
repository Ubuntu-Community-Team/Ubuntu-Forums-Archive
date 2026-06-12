---
title: "ubuntu installs but won't boot"
date: 2008-08-06
forum: Installation &amp; Upgrades
---

### Post by pripper on 2008-08-06
Hi, I've got a problem...but you already know that :)

I've tried installing the 32 bit and 64 bit versions of ubuntu on my system and they copy all the files partition i set i'm fairly new to linux but have setup a drbl server in the past month or so with out problems.

trying to set this machine as a dual boot with vista but heres what
the grub file says when i look at it.
but when i reboot its done two things

1st just shows "GRUB_"

2nd it comes up with the grub menu but the when you select anything it says invalid partition except for vista. 

kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

(hd0)	/dev/sda
(hd1)	/dev/sdb
ubuntu@ubuntu:/media/disk/boot/grub$ 

 

my system specs are 

nforce 780i xfx board

4gb ocz platinum xt ram
cpu = q6600
2x gforce 8800gtx
2x sata hdd's 1x320gb 1 x250gb
1 x sata lightscribe drive

I've tried installing it with 1 stick less of ram but didn't change anything  (needed to with vista install)

I've also tried using other boot loaders such as lilo and the one built into vista but none of its worked :S

any idea's any help would be much apreciated.

Thanks

---

