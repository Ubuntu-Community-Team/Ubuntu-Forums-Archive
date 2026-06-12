---
title: "Auto-mount when Ubuntu starts"
date: 2008-06-10
forum: Installation &amp; Upgrades
---

### Post by JustAnotherVagueAnon on 2008-06-10
I have a second internal HDD installed, but it does not mount until I click the drive icon in Places. My mount options are (if that helps)
```

rw nosuid nodev relative uid=1000 fmask=0077 dmask=0077 codepage=cp437 iocharset=iso8859-1 shortname=mixed utf8

```
The drive works properly, but I would like it to automatically start when Ubuntu starts.

---

### Post by iaculallad on 2008-06-10
Mount your drive using etc/fstab.

NTFS Drive?

---

### Post by JustAnotherVagueAnon on 2008-06-10
fat32

---

### Post by iaculallad on 2008-06-10
> **JustAnotherVagueAnon said:**
> fat32

Post the output of:

```
sudo fdisk -l
```

So  we know what to add on fstab.

---

### Post by JustAnotherVagueAnon on 2008-06-10
```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000dfd9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38391   308375676    b  W95 FAT32
/dev/sda2           38392       38913     4192965   83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19190   154139719+   7  HPFS/NTFS
/dev/sdb2           19191       19197       56227+  83  Linux
/dev/sdb3           29263       30401     9149017+   7  HPFS/NTFS
/dev/sdb4           19198       29262    80847112+   5  Extended
/dev/sdb5           19198       19445     1992028+  82  Linux swap / Solaris
/dev/sdb6           19446       29262    78855021   83  Linux

Partition table entries are not in disk order

```

---

### Post by iaculallad on 2008-06-10
Make a directory of your Mount Point:

```
sudo mkdir /media/whatever_name_you_want_it_here
```

Open /etc/fstab for editing:

```
sudo gedit /etc/fstab
```

Insert the line of text below at the bottom of your /etc/fstab file:

> /dev/sda1 /media/whatever_name_you_want_it_here vfat umask=0000 0 0

Save and Close your /etc/fstab file.

Open up your terminal and issue the command below:

```
sudo mount -a
```

---

### Post by JustAnotherVagueAnon on 2008-06-10
My mount point is at /media/SHARED and I added the folowing line to my fstab

```

/dev/sda1 /media/SHARED vfat umask = 0000 0 0

```

I get the following error:
```

 sudo mount -a
[mntent]: line 13 in /etc/fstab is bad

```

---

### Post by iaculallad on 2008-06-10
> **JustAnotherVagueAnon said:**
> My mount point is at /media/SHARED and I added the folowing line to my fstab

```

/dev/sda1 /media/SHARED vfat umask = 0000 0 0

```

I get the following error:
```

 sudo mount -a
[mntent]: line 13 in /etc/fstab is bad

```

Post your fstab:

```
cat /etc/fstab
```

---

### Post by JustAnotherVagueAnon on 2008-06-10
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=a0369f42-e602-4e22-939f-85c97405ed65 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=83113965-0e0c-485a-985b-fb7360801fa8 /boot           ext3    relatime        0       2
# /dev/sda5
UUID=22be3a91-936b-45f8-a61f-b3e66b9126d6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/sda1
/dev/sda1 /media/SHARED vfat umask = 0000 0 0


```

---

### Post by Victormd on 2008-06-10
Check this [How to]("http://ubuntuforums.org/showthread.php?t=802699") that I put together.
Let me know if it helps...

---

### Post by iaculallad on 2008-06-10
Replace the last line of your /etc/fstab with this one:

> /dev/sda1 /media/SHARED vfat iocharset=utf8,umask=000 0 0

Save and Close it.

On your terminal:

```
sudo mount -a
```

---

### Post by JustAnotherVagueAnon on 2008-06-11
It turns out my /media/SHARED directory was only appearing once the drive had mounted, so I had to make the directory before mounting the drive... Heh, embarrassing. Thanks.

---

