---
title: "LiveCD on Disk"
date: 2007-02-14
forum: Installation &amp; Upgrades
---

### Post by hoyanf on 2007-02-14
How can i copy the livecd to a partition to boot from it... I would like to make the partition for rescue purpose instead of relying on the dvd all the time, its similar to this [howto...]("http://www.howtoforge.com/installing_linux_without_cd_or_dvd")
i'm stuck till the busybox command prompt as it's unable to load the gui..

the error :-
/bin/sh: can't access tty: job control turned off

my grub config :- 
kernel /casper/vmlinuz append file=/preseed/ubuntu.seed boot=casper xforcevesa initrd=/casper/initrd.gz ramdisk_size=1048576 root=/dev/ram looptype=squashfs loop=/casper/filesystem.squashfs cdroot=/dev/sda5 quiet splash cpus=2 --
initrd /casper/initrd.gz


thanx any help would do..

---

### Post by louieb on 2007-02-17
The Ubuntu live CD is only a so so rescue tool. Only because it doesn't have point and click access to the hard drive(s).  Haven't tried to copy it to a hard drive, I've only used the installer.
For a rescue Live CD  I have used Knoppix and Puppy.
Puppy is really nice as a rescue CD and its installer copies the CD to the Hard drive.
Puppy's big plus is its small and fast. That its small is also its biggest drawback. That why I keep the Knoppix Live CD around.

I guess I'm not much help with what you want to do.

---

### Post by hoyanf on 2007-02-18
the use of is especially when ur cdrom/cd died on u...

as for me i can hav a minimal size gentoo livecd on a <100mb partition in case of my system files are corrupted or i want to do a new install.. best is always having a tftpboot if u can afford one, but for me now.. cant afford it at the moment...

since this [dude ]("http://www.askapache.com/2006/security/install-multiple-os-without-cds.html")manage to get some other distro's on harddisk for installation i'd like to hav a live ubuntu on a partition in case of emergency... hope u get my picture... btw by seeing your hardware sum old pc's dun hav usb ports on them to boot...

---

