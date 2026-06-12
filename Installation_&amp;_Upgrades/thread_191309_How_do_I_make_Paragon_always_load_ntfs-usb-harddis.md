---
title: "How do I make Paragon always load ntfs-usb-harddisk?"
date: 2006-06-07
forum: Installation &amp; Upgrades
---

### Post by MikkelMJ on 2006-06-07
Hi, I've installed Paragon NTFS for Linux and it works perfectly. Ubuntu had already found and added my Windows partition to fstab, to make it writeable with Paragon I just changed the filesystem in fstab from ntfs to ufsd and added umask=0 (to allow complete write-acces) to the options. Ufsd is Paragons read/write-compatible filsystem for Windows. 

Well, so far so good. Now the thing is that I have an external harddisk with three NTFS partitions. When I plug it into my computer, Ubuntu locates it immediately, then mounts the three partitions and places shortcuts to the drives on my desktop. The thing is that I'm not sure how to make sure that they're mounted with Paragons ufsd, instead of the standard ntfs? 

The thing is that, unlike my internal Windows partition, the usb drives do not appear in my /etc/fstab. That way I can't make sure that they are loaded with ufsd and umask=0. When I type fdisk -l it tells me that all three usb harddisks are mounted with HPFS/NTFS. I'm not sure if that's usefull in anyway. How or where do I tell Ubuntu to allways mount partitions it finds as ntfs, with the ufsd filesystem and the umask=0 prefix?

Thanks,
  Mikkel

---

### Post by Soilman on 2006-06-20
I'd like to thow my hat in the ring and say that I also would like external USB disks to be mounted with Paragons driver.  If I find more information I'll post here. Now I'll go read the manual.
Soilman

---

### Post by Antman on 2006-06-22
Hey, good thread. I was going to buy it but wanted to see if there are any tweaks I needed to do in Ubuntu first for external USB drive support.

---

### Post by MikkelMJ on 2006-06-28
Okay, good news. I've come a little closer to the answer, but it still doesn't work completely. First I'll tell you what I've found concerning the ufsd-automounting, and then about how to apply the umask=0 option.

1) It turns out that there's a very easy way to see if your usb-drives (that are not mentioned in /etc/fstab) have actually been mounted with ufsd or if they still mount with ntfs. The command is:
```
cat /etc/mtab
```

That's the first step to succes.

Then I've found out that Linux reads which filesystems to use from /proc/filesystems, but this file shouldn't be edited. Instead Linux has the option to create the file /etc/filesystems and in there apply the filesystems to use. Then Linux will read /etc/filesystems first, from top to buttom, and apply the first working filesystem for the volume that needs to be mounted. Make your /etc/filesystems look something like this:

# /etc/filesystems
#
# This file defines the filesystems search order used by a
# 'mount -t auto' command.
#

reiserfs

# Uncomment the following line if your modular kernel has vfat
# support and you want mount to try vfat.
vfat
ufsd

# Uncomment the following line if your modular kernel has udf
# support and you want mount to try udf before iso9660.
udf
iso9660

# Keep the last '*' intact as it directs mount to use the
# filesystems list available at /proc/filesystems also.
# Don't remove it unless you REALLY know what you are doing!
*


The bad thing is that Ubuntu doesn't seem to read the /etc/filesystems file as it continues to load the drives as NTFS...


2)
cat /etc/mtab can also be utilized to check the umask=? option of a mounted volume. By default you will see something like this:
```
/dev/sda1 /media/A ntfs rw,nosuid,nodev,uid=1000,gid=1000,umask=077,iochar set=utf8 0 0
```

We need to change the umask=077 default option, to umask=0 to give full read/write permission. I've found the solution for how to do this for vfat volumes here [http://www.ubuntuforums.org/showthread.php?t=141295&page=2](http://www.ubuntuforums.org/showthread.php?t=141295&page=2). This link says:

[B][COLOR="Red"]WARNING: I'm not sure if this procedure is best-practice or if it might break something in the future[/COLOR]

edit /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi

search for and replace

```
<match key="volume.fstype" string="vfat"> <merge key="volume.policy.mount_option.iocharset=utf8" type="bool">true</merge> <merge key="volume.policy.mount_option.quiet" type="bool">true</merge> </match>
```

with

```
<match key="volume.fstype" string="vfat"> <merge key="volume.policy.mount_option.iocharset=utf8" type="bool">true</merge> <merge key="volume.policy.mount_option.quiet" type="bool">true</merge> <merge key="volume.policy.mount_option.umask" type="string">0000</merge> <!-- or whatever you desire --> </match>
```[/B]

This procedure, however, doesn't seem to be the same for NTFS...


So now we know that Linux should mount the drives with ufsd when it's written in /etc/filesystems, but it doesn't. And we know how to mount Fat32 drives with umask=0. So we are close. 

Is there are nice hacker out there that can use this info to put together the proper guide for getting this to work? :D

---

### Post by MikkelMJ on 2006-06-30
bump...

---

