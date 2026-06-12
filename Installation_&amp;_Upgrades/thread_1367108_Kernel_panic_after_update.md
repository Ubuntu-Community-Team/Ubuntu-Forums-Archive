---
title: "Kernel panic after update"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by jhl.foreign on 2009-12-29
Hi,
I am totaly new to linux. Last night while reading email I updated my system using update manager. Oops. This morning When booting I got the following error:
[1.5..]RAMDISK: gzip image found at block 0
[1.7..]uncompressed error
[1.7..]List of all partitions:
[1.7..]0800             78150744 sda driver: sd
[1.7..]   0801             56878101  sda1
[1.7..]   0802                         1  sda2
[1.7..]   0803               6128797  sda3
[1.7..]   0805              15141231 sda5
[1.7..]0b00               1048575 sr0 driver: sr
[1.7..]No filesystem coul mount root, ext3 ext2 ext4 fuseblk
[1.7..]Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,5)
[1.7..]Pid: 1, com: swapper Not tainted 2.6.31-14-generic #48-Ubuntu
etc.
 
I am dual booting my Ubuntu system with Windows XP on GRUB. How can I fix this error? The only thing strange is the 0b00 part. 
 
I used the following to boot:
insmod ntfs
set root=(hd0,5)
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /boot/vmlinuz-2.6.31.14-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro
initrd /boot/initrd.img-2.6.31-14-generic
boot
 
Thank you very much for your elp :P

---

