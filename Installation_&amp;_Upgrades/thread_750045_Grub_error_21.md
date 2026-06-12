---
title: "Grub error 21"
date: 2008-04-09
forum: Installation &amp; Upgrades
---

### Post by suss427 on 2008-04-09
Here is what I am trying to do:

I have 4 hard drives in my computer
The first 2 are in raid 0 and vista is installed on it
HDD 3 is for storage
HDD 4 is for ubuntu

I want to go into my bios and change which hard drive to boot too, and then have it boot! My motherboard allows this!

I dont like boot managers and do not want to use them. 
I had xp/ vista set up this way before and it worked great,


Here is the problem:
After I install ubuntu (AND grub) onto this 4th hard drive, and when I change in the bios to boot to this drive, I get a Grub error 21.

I have tried this with ubuntu 8.04 x86, 8.04 x64, and 7.10 x86 all with no luck.

I have searched everywhere and could not find anyone with the same problem.

Please help me :confused:)

FYI: my linux experience is limited, so please do not talk too far over my head ;)

---

### Post by suss427 on 2008-04-09
one more failed attempt:

Installed 8.04 x86 without boot loader and now get a grub error 15 when it tries to boot to that hard drive.

help?

---

### Post by Partyboi2 on 2008-04-09
[Here]("http://users.bigpond.net.au/hermanzone/p15.htm#Grub_Errors") is a page with a list of grub error messages, you might find something of use.

---

### Post by suss427 on 2008-04-09
Thanks for the link. Unfortunately it did not help me too much. Anyone have any ideas?

Thanks

---

### Post by suss427 on 2008-04-09
Thanks for the link. Unfortunately it did not help me too much. Anyone have any ideas?

Thanks

---

### Post by confused57 on 2008-04-09
If your Ubuntu drive is IDE, you might want to check in bios if the controller is set to "Auto" (or possibly Enabled).  You might have a problem booting to the drive, if it's connected to a PCI IDE adapter.

---

### Post by suss427 on 2008-04-09
All hard drives are sata 300 on an intel ICHR9.

---

### Post by confused57 on 2008-04-09
Do you get a grub boot menu when you boot first to the Ubuntu drive?

You could boot the Ubuntu live cd, open a terminal(Applications---Accessories---Terminal), post the output of:
```
sudo fdisk -l
```
-l is a lowercase "L"

---

### Post by suss427 on 2008-04-09
Here is what I get:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2f3854d8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60802   488389632    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x79c66e4c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60802   488384512    7  HPFS/NTFS

Disk /dev/sdd: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x362b362b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        8666    69609613+  83  Linux
/dev/sdd2            8667        9039     2996122+   5  Extended
/dev/sdd5            8667        9039     2996091   82  Linux swap / Solaris

```

---

### Post by confused57 on 2008-04-09
If you're getting a grub boot menu when you boot first to your Ubuntu drive, select the first Ubuntu entry, press "e", select the line with root, press "e" again, change root from (hdx,0) to (hd0,0), press "enter", then "b" to boot.

If you're not getting a grub boot menu, you can try reinstalling grub to the Ubuntu drive's mbr, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
read the tutorial, but it would be something like:
```
sudo grub
find /boot/grub/stage1
```
from the output of the last command:
```
root (hdx,0)
setup (hdx)
quit
```

If this gives you a grub boot menu, then try the "e" method above.

If you want to see how grub is configured, you can mount your root partition from the live cd:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sdd1 /media/ubuntu
gedit /media/ubuntu/boot/grub/menu.lst
gedit /media/ubuntu/boot/grub/device.map
```

---

### Post by suss427 on 2008-04-09
Ok, I am going to reinstall first, and then try messing with grub.

In Advanced Options of step 7 of 7 in the install process, it asks if to install a boot loader, and where to do it.

"Device for boot loader installation:"

The options are:
/dev/sda
/dev/sdb
/dev/sdc
/dev/sdc1
/dev/sdd
/dev/sdd1

I am assuming it is either
/dev/sdd
/dev/sdd1

Any thoughts?

---

### Post by confused57 on 2008-04-09
Yes, /dev/sdd would install grub to the Ubuntu drive's mbr, which is where you want to install grub.../dev/sdd1 would install to the root partition.

---

### Post by suss427 on 2008-04-09
GOT IT!

After reinstalling I got the error 21 again.
I edited the first line.

> change root from (hdx,0) to (hd0,0), press "enter", then "b" to boot.
 

Worked perfectly!
Thanks a bunch!

=D>

---

### Post by suss427 on 2008-04-09
any changes i make in grub are gone as soon as I boot, and I do not have permission to change the /boot/grub/menu.lst file. How do I make these changes permanent?

---

### Post by confused57 on 2008-04-09
> **suss427 said:**
> any changes i make in grub are gone as soon as I boot, and I do not have permission to change the /boot/grub/menu.lst file. How do I make these changes permanent?
You can make it permanent by:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```
Change all the lines with root to (hd0,0)...also, change the line with #groot to (hd0,0)...leave the # in front of groot.

quit & save.

Glad it worked for you.

---

