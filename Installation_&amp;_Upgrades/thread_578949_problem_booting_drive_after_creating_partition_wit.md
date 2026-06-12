---
title: "problem booting drive after creating partition with dd"
date: 2007-10-17
forum: Installation &amp; Upgrades
---

### Post by vbdanl on 2007-10-17
Hi. I wanted to have a backup copy of ubuntu on a second drive, so I created it using the dd command.  appears to have created it fine, but since dd copies everything exactly as it is from one partition to the other, they both have the same UUID.  I have 2 entries in the menu.lst, so I can choose which one should boot, but I think it is actually booting the same one.
I would like to have them act as completely different distros, so if I choose to install the latest version of ubuntu on drive A, I can leave the old failsafe copy on drive B.  I thought about using crontab to keep both partitions/drives in sync, but if one gets messed up, both are messed up, and I would rather not risk that.
I am using a wireless modem on this pc, and went through all kinds of hoops to get it to work, so thats another reason why I like the idea of keeping a backup that I know works.  I have installed the upgrades and found after the new kernel boots, I lose connectivity to the internet.
so my question is what do i need to do to be able to boot ubuntu from either drive a or drive b, could be nearly the exact same release, or might be different ones ?
Here is the /dev/disk/by-uuid list (sdb6 has the same uuid as sda1 - I have seen both sda1 and sdb6 show up with the same uuid, but not at the same time.. it will give me a error during boot if I try to have them both in the fstab):
dan@Antec:/dev/disk$ l by-uuid
total 0
lrwxrwxrwx 1 root root 10 2007-10-17 18:52 133a8278-cc45-4220-99b3-23b3674d6595 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2007-10-17 18:52 303af08f-6580-4c68-9d50-e064098809b9 -> ../../sdb5
lrwxrwxrwx 1 root root 10 2007-10-17 18:52 4dbd19dc-df77-4595-a814-fc035e9f5cf7 -> ../../sdb3
lrwxrwxrwx 1 root root 10 2007-10-17 18:52 8d6a09e7-6983-4ddb-8264-0f82de2cbb11 -> ../../sda3
lrwxrwxrwx 1 root root 10 2007-10-17 18:52 93a64a90-5086-4790-8e5b-23e01ae06ad8 -> ../../sda5
lrwxrwxrwx 1 root root 10 2007-10-17 18:52 a5ae4915-7744-4c6e-91c9-27a080f5d477 -> ../../sdb7
lrwxrwxrwx 1 root root 10 2007-10-17 18:53 eeb7e59f-4c03-432f-aec3-a487e328d273 -> ../../sda1
dan@Antec:/dev/disk$

Here is the fstab.. I have played around with it, trying different ways of mounting sda1 and sdb6:
dan@Antec:/dev/disk$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=eeb7e59f-4c03-432f-aec3-a487e328d273 /               ext3    defaults,errors=remount-ro 0       1
/dev/sda3                                 /pclinuxos      ext3    defaults  0 2
/dev/sdb1                                 /grub-boot      ext3    defaults  0 2
/dev/sdb2                                 /mint           ext3    defaults  0 2
/dev/sdb3                                 /debian         ext3    defaults  0 2
/dev/sdb5                                 /data           ext3    defaults  0 2
/dev/sdb6                                 /ubuntu         ext3    defaults  0 2
# /dev/sda5
UUID=0aaf15f8-01c9-462c-b315-f7477ede3603 none            swap    sw        0 0
# /dev/sdb7
UUID=3760c383-6c96-484a-ac2d-f2b9bbb259d3 none            swap    sw        0 0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto      0       0

thanks for your help.

---

### Post by vbdanl on 2007-10-23
bump  not sure if this does any good, but seen it a few times, so thought i would give it a go..

---

