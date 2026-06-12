---
title: "Ubuntu wont boot - Vista always is - plz help"
date: 2007-06-09
forum: Installation &amp; Upgrades
---

### Post by maher_79 on 2007-06-09
Hi all,

Very new to Ubuntu and Linux and just installed Ubuntu to dual boot with Vista Business.
used this link:[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

I CAN NOT get Ubuntu to boot though.  It is always vista that is booting.  Plz help - Below is the code output for sudo fdisk -l (did that by using the Live CD)

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30515   245111706   42  SFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7012    56320000    7  HPFS/NTFS
/dev/sdb2            7013       18945    95851822+  83  Linux
/dev/sdb3           18946       19457     4112640    5  Extended
/dev/sdb5           18946       19457     4112608+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

```

Please help would be greatly appreciated :(

---

### Post by logos34 on 2007-06-09
So you're not seeing the grub menu, even fleetingly before it goes into vista?

Try setting the bios to boot from the other hard disk...maybe grub went there.  If not, then grub either did not install at all or there's some other problem.  You can reinstall grub using the ubuntu live cd.  Fire it up, go to the desktop, open a terminal and type:

sudo grub
find /boot/grub/stage1
(Enter the output in the next command).
root (hdx,y)
setup (hdx)
quit  

That will write grub to the master boot record of /dev/sdb.  Boot from that drive

---

### Post by maher_79 on 2007-06-14
Ok, this is what the problem was and how did i resolved it :)

I had Vista installed on 160 GB SATA plus a 250GB IDE.  The IDE was setup as Primary Slave and SATA setup up as Primary.

The problem was that i installed Ubuntu while my IDE was still pluged in.  IF YOU WANT TO DUAL BOOT AND YOU HAVE AN EXTRA OR 2 HDS THEN MY ADVICE TO U IS TO UNPLUG THEM OR DISABLE THEM FROM THE BOIS.  DO THE INSTALL AND THEN PLUG THEM BACK IN OR ACTIVATE THEM (BOIS) AND YOU WILL HAVE NO PROBLEM DUAL BOOTING.

I hope this help :)   - Ubuntu ROCKS

---

