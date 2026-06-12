---
title: "Install 12.04 alongside 9.10 - inncorrect location?"
date: 2013-11-07
forum: Installation &amp; Upgrades
---

### Post by joebrady on 2013-11-07
I've been running an HTPC with 9.10 and XBMC for quite some time.  Zotac dual core Atom, 3, 1Tb HDs.  I've not wanted to mess with it since getting everything right, but it's finally time to update...

I wanted to install 12.04 along side 9.10, so i had the option of dual booting until the time I had everything set up in 12.04 just as I wanted it for daily use.  

9.10 is installed on a partition of sda (the first hd), with also a swap partition and then a third for storage.  The other two hard drive are storage and backup.

When I get to the option to install along side 9.10, the installer only give me one option for one location in which to install (sdc, the third drive).  This is not the drive I want to add partitions to or lose any data on.  

How to I get the installer to show sda as an option?  (just as a test, i went to the full install option, and there I can see all three disks in the drop down list as options..)

Any help is appreciated and if I need to provide more info, let me know, thanks!

---

### Post by fantab on 2013-11-07
Post the output of:

```
sudo fdisk -l
sudo parted -l
```

---

### Post by Bucky Ball on 2013-11-07
Make some free space next to 9.10 or somewhere on sda (shrink a partition). That will then give you an option to install there. You can do that when choosing 'Something Else' during install or by using Gparted when running the desktop from a LiveCD. 

You can't install on sda if there is no free space there to install.

---

### Post by joebrady on 2013-11-07
That was my first thought actually, and I tried this to no avail.  Of course, may have done it incorrectly.  I created an empty 20G partition on the drive I wanted to use, as EXT4, and marked it at "bootable", but it still did not show up.  I think I have all the data I need off that drive now, so maybe I'll just bite the bullet and format and start from scratch....

---

### Post by fantab on 2013-11-07
No, don't mark it as bootable. Post the output of commands I requested earlier.

---

### Post by joebrady on 2013-11-07
Ah, as a last ditch effort before that I went into the "something else" option.  There I was able to add the mount point of / to that new partition, so fingers crossed it works.

fantab - if this doesn't work I'll post those, thanks for the reply.

---

### Post by joebrady on 2013-11-07
Well, it did let me install in on that partition of the first disk where I wanted it, but I got no dual boot option upon restart, so...

output of fdisk -l below, output of gparted just gave me a "no such device" message...

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes  

 255 heads, 63 sectors/track, 121601 cylinders  
 Units = cylinders of 16065 * 512 = 8225280 bytes  
 Disk identifier: 0x000dadee  
 

    Device Boot      Start         End      Blocks   Id  System  
 /dev/sda1               1        2527    20298096   83  Linux  
 /dev/sda2            2528      121601   956461905    5  Extended  
 /dev/sda5            2528        2910     3076416   82  Linux swap / Solaris  
 /dev/sda6            2911      118990   932412568+   c  W95 FAT32 (LBA)  
 /dev/sda7   *      118991      121601    20972826   83  Linux  
 

 WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.  
 

 

 Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes  
 255 heads, 63 sectors/track, 121601 cylinders  
 Units = cylinders of 16065 * 512 = 8225280 bytes  
 Disk identifier: 0x00000000  
 

    Device Boot      Start         End      Blocks   Id  System  
 /dev/sdb1               1      121602   976762583+  ee  GPT  
 

 Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes  
 255 heads, 63 sectors/track, 121601 cylinders  
 Units = cylinders of 16065 * 512 = 8225280 bytes  
 Disk identifier: 0x05de22ff  
 

    Device Boot      Start         End      Blocks   Id  System  
 /dev/sdc1               1      108167   868846007    7  HPFS/NTFS  
 /dev/sdc2          108168      121601   107908605    7  HPFS/NTFS

---

### Post by fantab on 2013-11-07
My bad. also edited the earlier post.
```
sudo parted -l
```

Don't use 'boot' flag on /dev/sda7, instead put it on /dev/sda1

---

### Post by Bucky Ball on 2013-11-07
Okay, just hold down the shift key when you boot. That should give you a list with installed OS and you're good to go.

If Windows is not there, boot to Ubuntu, open a terminal and run:

sudo update-grub

Reboot and hold down shift. Is it there now? If that worked we can make the list appear at boot without holding down shift if you like.

> **fantab said:**
> My bad. also edited the earlier post.
```
sudo parted -l
```

Don't use 'boot' flag on /dev/sda7, instead put it on /dev/sda1

Don't know if any of this matters now as you have Ubuntu installed and booting, just not getting a selection at boot. That's a different matter. (Unless you've accidentally wiped Windows.) You are sure it is still on the drive (you can check with Gparted)? ;)

---

