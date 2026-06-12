---
title: "Building Raid0 from two Raid1 Devices with mdadm"
date: 2008-02-09
forum: Installation &amp; Upgrades
---

### Post by martin1977 on 2008-02-09
I have two Raid 1 devices /dev/md2 and /dev/md3 formatted as Ext3 and I'm trying to set them up in a Raid0 Stripe, i.e.Raid 0+1

From the session below you will see that I'm not having much success.  I think I need to change the type of the Raid1 devices to Raid Autodetect, but I don't know how to do this.  fdisk /dev/md2 does not work.

md4 : active raid5 sda4[0] sdd4[3] sdc4[2] sdb4[1]
      732732480 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]
      
md3 : active raid1 sdc3[0] sdd3[1]
      195310144 blocks [2/2] [UU]
      
md1 : active raid1 sdc1[0] sdd1[1]
      43945664 blocks [2/2] [UU]
      
md2 : active raid1 sda3[0] sdb3[1]
      195310144 blocks [2/2] [UU]
      
md0 : active raid1 sda1[0] sdb1[1]
      43945664 blocks [2/2] [UU]

martin@TITAN:~$ sudo umount /dev/md3
martin@TITAN:~$ sudo umount /dev/md2
umount: /dev/md2: not mounted
martin@TITAN:~$ sudo mdadm --create --verbose /dev/md5 --level=0 --raid=devices=2 /dev/md2 /dev/md3
mdadm: invalid number of raid devices: devices=2
martin@TITAN:~$ sudo mdadm --stop /dev/md3
mdadm: stopped /dev/md3
martin@TITAN:~$ sudo mdadm --stop /dev/md2
mdadm: stopped /dev/md2
martin@TITAN:~$ sudo mdadm --create --verbose /dev/md5 --level=0 --raid=devices=2 /dev/md2 /dev/md3
mdadm: invalid number of raid devices: devices=2
martin@TITAN:~$ sudo fdisk /dev/md2
Unable to read /dev/md2
martin@TITAN:~$ sudo mdadm --assemble /dev/md3
mdadm: /dev/md3 has been started with 2 drives.
martin@TITAN:~$ sudo mdadm --assemble /dev/md2
mdadm: /dev/md2 has been started with 2 drives.
martin@TITAN:~$ sudo mdadm --create --verbose /dev/md5 --level=0 --raid=devices=2 /dev/md2 /dev/md3
mdadm: invalid number of raid devices: devices=2

Any pointers would be appreciated.

Regards, Martin

---

### Post by lha on 2008-02-09
> **martin1977 said:**
> 
martin@TITAN:~$ sudo mdadm --create --verbose /dev/md5 --level=0 --raid=devices=2 /dev/md2 /dev/md3
mdadm: invalid number of raid devices: devices=2

Any pointers would be appreciated.


Have you noticed that you are using "=" instead of "-" in "--raid-devices=2"?

---

### Post by martin1977 on 2008-02-10
Thanks - silly error - the simple change did solve the problem!

Regards, Martin

---

