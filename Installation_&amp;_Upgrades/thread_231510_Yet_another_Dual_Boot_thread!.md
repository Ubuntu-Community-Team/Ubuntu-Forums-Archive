---
title: "Yet another Dual Boot thread!"
date: 2006-08-07
forum: Installation &amp; Upgrades
---

### Post by dauber on 2006-08-07
Hi, all...to be honest, I did search the forums, and DID find a similar post, but darned if I had to leave the page and suddenly can't find it again, so I apologize in advance, but here's my situation...

I have a Dell Dimension 2400 with XP Pro on a 40-gig hard drive, which I BELIEVE is the primary slave.

I installed Dapper Drake onto, I believe, the fourth partition of a 160-gig hard drive, which I'm pretty sure is the primary master.

Here's the problem: grub is COMPLETELY skipped during the boot process. To get to it, I actually have to hit F12 during startup to get to the boot selector, then I have to select "Boot from utility partition" to get to Ubuntu.

I've tried changing default to 4 (3 Ubuntu options plus XP) in menu.lst; nothing. I cut'n'pasted this code into menu.lst, but to no avail:
```
title Windows XP
root (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

I've tried reinstalling grub into MBR with grub-install.

Nothing.

Any thoughts? Should I provide more details (and which ones)?

---

### Post by confused57 on 2006-08-07
You could boot into Ubuntu & see what the output of these commands are:

```
cat /etc/fstab
sudo fdisk -l
```
The -l is a small "L"

This should give an idea of your partition tables.

---

### Post by dauber on 2006-08-07
> **confused57 said:**
> You could boot into Ubuntu & see what the output of these commands are:

```
cat /etc/fstab
sudo fdisk -l
```
The -l is a small "L"

This should give an idea of your partition tables.

cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

sudo fdisk -l
Password:

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        3916    31455238+   7  HPFS/NTFS
/dev/hda2            3917        7832    31455270    7  HPFS/NTFS
/dev/hda3            7833       11748    31455270    7  HPFS/NTFS
/dev/hda4           11749       19457    61922542+   5  Extended
/dev/hda5   *       11749       19269    60412401   83  Linux
/dev/hda6           19270       19457     1510078+  82  Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4862    39053983+   7  HPFS/NTFS

---

### Post by confused57 on 2006-08-07
You could try reinstalling grub to hd0(hda) using the Live CD:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

Then you'd need to add the Windows entry to grub, if it's successful...can't guarantee it'll work, but it might be worth a shot.

---

### Post by dauber on 2006-08-07
Well, I must have done SOMETHING right...I just had a hunch that maybe...MAYBE...I should actually install grub on the right hard drive. :oops: 

So I tried installing on the other drive, rebooted, and THERE'S THE grub MENU!!!

And the "ntldr is missing" warning when I tried to boot XP. :shock: 

Just on a hunch I went into Ubuntu, changed "default 4" in menu.lst to "default 0," and suddenly I'm in business. =D> \\:D/

---

