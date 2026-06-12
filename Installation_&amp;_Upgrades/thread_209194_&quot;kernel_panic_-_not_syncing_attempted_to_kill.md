---
title: "&quot;kernel panic - not syncing: attempted to kill init&quot; on fresh server install"
date: 2006-07-04
forum: Installation &amp; Upgrades
---

### Post by lordelph on 2006-07-04
Following a fresh install of a LAMP server on booting I get these messages

Booting "Ubuntu, kernal 2.6.15-23-server"

root (hd0,0)
Filesystem type is ext2fs, partition type is 0x83
kernel /vmlinuz-2.6.15-23-server root=/dev/sda2 ro quiet splash
  [Linux-bzimage, setup=0x1c00, size=0x16b75f]
initrd  /initrd.img-2.6.15-23-server
  [Linux-initrd @ 0x1f950000, 0x69f4ea]
savedefault
boot
Uncompressing Linux... Ok, booting the kernel.
[42949300.130000] sda: asking for cache data failed
[42949300.130000] sda: assuming drive cache: write through
[42949300.130000] sda: asking for cache data failed
[42949300.130000] sda: assuming drive cache: write through
run-init: /sbin/init: error 80
[42949383.760000] Kernel panic - not syncing: Attempted to kill init!

Probably the only unusual thing about the system is that it has an Intel SRCS16 RAID card in it, but the installer worked OK with it.

Any pointers welcome!

---

### Post by lordelph on 2006-07-05
I tried a completely fresh install from a new CD, just in case. Still no joy.

Any pointers for diagnosing this gratefully received.

---

### Post by lordelph on 2006-07-06
Debian Sarge installed OK on this server, so it's sayonara Ubuntu sadly!

---

### Post by jinx099 on 2006-07-24
I'm having a very similar problem with Ubuntu 6.06 Server.  I am using a Promise Fasttrak S150 TX2 as a SATA controller only and using software RAID on 2 brand new Seagate Baracuda 320GB SATAII (new perpendicular recording ones).  

My setup also installs fine, however after doing an apt-get install xubuntu-desktop and rebooting, I get the same kernel panic.  I'm going to test this on my main system without the Promise card but same software RAID and see if I have any better results.

](*,)

---

### Post by wdm on 2007-02-04
i experienced this refuse to install too, i was trying to install on pc with 16MB RAM, probably this is not enouth, couse even with 32MB installation was with lot low memory errors.

---

