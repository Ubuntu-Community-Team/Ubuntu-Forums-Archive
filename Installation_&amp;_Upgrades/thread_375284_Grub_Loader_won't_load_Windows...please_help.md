---
title: "Grub Loader won't load Windows...please help"
date: 2007-03-03
forum: Installation &amp; Upgrades
---

### Post by cabber on 2007-03-03
Grub issue is this.  I am using Vista and decided to upgrade.  When I did, the GRUB loader was gone.

I went through this process to reinstall grub:
```


Code:
sudo grub 
This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands


Code:
find /boot/grub/stage1
This will return a location. If you have more than one, select the installation that you want to provide the grub files.

Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)


Code:
root (hd?,?)Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr


Code:
setup (hd0)Finally exit the grub shell

Code:
quitThat is it. Grub will be installed to the mbr.

```

I ran this with the Ubuntu Live CD and was able to reinstall the grub.  The problem now, is when I choose Windows Vista to load, it just loads the grub again.  I can boot into Ubuntu fine but choosing Windows brings the grub back up.  Can someone assist?

---

### Post by cabber on 2007-03-03
Here is my fdisk output:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29959   240640000    7  HPFS/NTFS
/dev/sda2           29960       60801   247738365    b  W95 FAT32

Disk /dev/sdb: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4314    34652173+  83  Linux
/dev/sdb2            4315        4500     1494045    5  Extended
/dev/sdb5            4315        4500     1494013+  82  Linux swap / Solaris
```

I have Windows Vista installed on sda1
I have Ubuntu 6.10 installed on sdb1
sda2 is a FAT32 Partition (on the same drive as Vista install) shared with the two OS's.

---

### Post by confused57 on 2007-03-03
Boot into Ubuntu and post the output of:
```
cat /boot/grub/menu.lst
```
menu.lst is short for menu.list(you probably know this, but won't hurt for me to mention it)

and please post the output of:
```
cat /etc/fstab
```

---

### Post by cabber on 2007-03-04
Thanks for the follow up.  I ended up installing the Grub via the same process noted above and it worked.  I must have fat fingered in my initial attempts, but all is well now.

---

