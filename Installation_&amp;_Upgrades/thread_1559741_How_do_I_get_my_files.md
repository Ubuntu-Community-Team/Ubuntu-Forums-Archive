---
title: "How do I get my files?"
date: 2010-08-23
forum: Installation &amp; Upgrades
---

### Post by james.euless on 2010-08-23
I installed Ubuntu on a secondary HD.  I ran sudo fdisk -l and got:


Disk /dev/sda: 40.0 GB, 40020664320 bytes
240 heads, 63 sectors/track, 5169 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xc06e7af3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2690    20336368+   7  HPFS/NTFS
/dev/sda2            2691        5169    18741240    f  W95 Ext'd (LBA)
/dev/sda5            2691        5169    18741208+   7  HPFS/NTFS

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcae973e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19929   160079661    7  HPFS/NTFS

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc39ef0f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdb is where Ubuntu was installed under Windows.  How do I reach the files that are on that disk?  Should I have put Ubuntu on its own partition?

---

### Post by sgosnell on 2010-08-24
Did you install with wubi?  It appears you must have, since all the disks are NTFS.  Wubi is a Windows program, so you need to boot Windows, then run wubi as you would any other Windows program, which launches Ubuntu.

---

### Post by uRock on 2010-08-24
+1 It looks like Wubi is installed. There aren't any EXT partitions.

---

### Post by bcbc on 2010-08-24
Wubi installs Ubuntu on a virtual disk x:\ubuntu\disks\root.disk

So you can either mount it from a live CD and copy the data, or install a tool to view it from windows (see [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)).

To mount it after booting a live CD (assuming it's on /dev/sdb1):
```
sudo mkdir /media/win
sudo mount /dev/sdb1 /media/win
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
nautilus /mnt
```

---

### Post by jocko on 2010-08-24
> **sgosnell said:**
>   Wubi is a Windows program, so you need to boot Windows, then run wubi as you would any other Windows program, which launches Ubuntu.
Not quite. 
What makes a wubi install different from a normal install is that ubuntu is installed from within windows to a file on a windows file system instead of to a real partition. Ubuntu's boot loader (grub) is also installed in this file instead of on the mbr of the hard drive and have to be loaded from the windows boot loader. This results in a ubuntu system that can be uninstalled like if it was a windows program.
But even with a wubi install, you boot ubuntu directly on the real hardware (except the virtual hard drive file instead of a real hard drive) without loading any part of windows.

I think what the op really meant to ask was how can you access the files that are saved within the ubuntu system from windows. I don't know enough about the format of the wubi virtual hard drive file to know if this is possible, but I think it is at least theoretically possible to mount it in some virtual disk manager and access the files from there. But I also guess that since the file system in that virtual disk is a linux file system (probably ext3 or 4), you would need to install some ext file system driver in windows.

---

### Post by james.euless on 2010-08-24
I installed Ubuntu through Wubi on a HD (call it D:\) So D:\Ubuntu.  When I open Windows, I can go to the HD and get to all the files, for example: D:\pictures.  When I boot into Ubuntu, I do not know how to get to those Windows created folders.

---

### Post by bcbc on 2010-08-24
> **james.euless said:**
> I installed Ubuntu through Wubi on a HD (call it D:\) So D:\Ubuntu.  When I open Windows, I can go to the HD and get to all the files, for example: D:\pictures.  When I boot into Ubuntu, I do not know how to get to those Windows created folders.

The easiest way is to go to click on Places and select each partition. A browser window (nautilus if you're using ubuntu) will let you browse the partition and find the one with /ubuntu/disks/root.disk. Then find the path the partition is automounted on by hitting CTRL+L. It should show you something like /media/XXXXXXX

Then just use that:
```
sudo mount -o loop /media/XXXXXXX/ubuntu/disks/root.disk /mnt
nautilus /mnt
```

If your drives have labels, typing XXXXXXX will be easier. If it's a UUID just type in the first two letters and hit [TAB] to autocomplete.

---

### Post by james.euless on 2010-08-26
I can see the root dir, but it is "X" and says I do not have permission.  How do I open and view it?  I'm using Ubuntu 9.10 is that makes a diff.

---

### Post by uRock on 2010-08-26
In a terminal, run ```
gksu nautilus
``` to open a file browser with root permissions. **_WARNING: Moving deleting, or altering these files can easily kill your system!_**

---

### Post by james.euless on 2010-08-27
No luck.  I ran gksu nautilus and got this in the terminal:


** (nautilus:2657): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:2657): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Looking at root, I don't see anything like you describe.  Ctr + L shows only "Location: \Root"

Any ideas?  Did I miss a step?

---

### Post by bcbc on 2010-08-27
Rereading this thread... I now think you want to access the windows files that are on the same partition that you installed ubuntu on?

They're in the /host directory.

Find it under: Places, Computer, File System, host

---

### Post by james.euless on 2010-08-30
"host"  That's it.  I thought I had looked in each folder, but apparently I'm blind.  Thank you.

---

