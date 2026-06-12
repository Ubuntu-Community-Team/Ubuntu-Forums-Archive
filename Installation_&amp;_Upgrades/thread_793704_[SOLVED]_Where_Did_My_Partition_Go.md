---
title: "[SOLVED] Where Did My Partition Go?"
date: 2008-05-14
forum: Installation &amp; Upgrades
---

### Post by twoseids on 2008-05-14
So I just installed Hardy, and instead of continuing to dual-boot with XP, I decided to wipe the XP partition clean and install XP within VirtualBox (or if that fails, VMWare Server).

When partitioning during installation, I told it to format that partition as ext3, but I did not label it as anything. I thought maybe it would create an extra directory (like an extra drive on Windows). But now it looks like Ubuntu is using that partition for something else (see screenshot).

How can I reclaim that partition for disk space? Can I merge it with /home?

Thanks!

---

### Post by forestpixie on 2008-05-14
There isn't a partition there to reclaimm I'm not too sure what the hidden gvs folder is but I have one as well  - check partitions on disks

sudo fdisk -l

---

### Post by twoseids on 2008-05-14
> **forestpixie said:**
> There isn't a partition there to reclaimm I'm not too sure what the hidden gvs folder is but I have one as well  - check partitions on disks

```
sudo fdisk -l
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   83  Linux
/dev/sda3   *        1311        2585    10241437+  83  Linux
/dev/sda4            2586       12161    76919220   83  Linux
```

The partition in question is /dev/sda2. Hmm...where'd it go?

---

### Post by forestpixie on 2008-05-14
You can install gparted - which will appear in system >admin menu - it could be empty unallocated space

```
sudo apt-get install gparted
gksudo gparted
```

You won't be able to work on mounted drives there - but you should be bale to see if there is the space there and format it

---

### Post by twoseids on 2008-05-14
Okay, done. Here's what GParted is telling me (see pic).

So what can I do to that partition to make it usable disk space? Can I merge it with /home without screwing up /home?

P.S. Thanks for the quick replies!

---

### Post by forestpixie on 2008-05-14
There are 2 ways to go with this
1 - format the unallocated space within ubuntu to ext3 and then mount it - it will be an extra partition

2 - add it to /home if you like, this can take a _long_ time and it is possible to lose information (although that is just a warning)

First option is easiest and if you want you use the space for a virtual machine file probably will be sufficient.

If you want to do that - right click the unallocated space and make a ext3 partition, apply - let it do it's thing and close

Then you need to make it mount at boot - to do that add it to fstab.

---

### Post by twoseids on 2008-05-14
> **forestpixie said:**
> There are 2 ways to go with this
1 - format the unallocated space within ubuntu to ext3 and then mount it - it will be an extra partition

2 - add it to /home if you like, this can take a _long_ time and it is possible to lose information (although that is just a warning)

First option is easiest and if you want you use the space for a virtual machine file probably will be sufficient.

If you want to do that - right click the unallocated space and make a ext3 partition, apply - let it do it's thing and close

Then you need to make it mount at boot - to do that add it to fstab.
Okay, I've got the partition done. I need a little help with fstab, as I'm still a newbie with it. Here's how it looks now:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=bc787d41-2502-487b-ad12-4999295f064a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=400f898e-09b5-40ce-92e0-5c32e7e092a3 /home           ext3    relatime        0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

How shall I add the new line? Thanks!

---

### Post by sunstriker on 2008-05-14
just for your information: if you don't like the extra partition you can always merge it with your ubuntupartition with the live cd

---

### Post by forestpixie on 2008-05-14
Had it more or less ready - guessed you'd go for option 1

Make a directory for the partition to mount in -

```
sudo mkdir /media/[COLOR="#ff0000"]data[/COLOR]
```

change name 'data' to whatever you want, if you do change in fstab as well

You will need to know how partition is referenced - use the fdisk command I gave you earlier
it will be the new one - not sda1,3 or 4

Now backup and edit fstab

```
sudo cp /etc/fstab /etc/fstab.1405
gksudo gedit /etc/fstab
```

File is now open for editing - go to end and add new line, replace sda* with number you get form fdisk 

```
/dev/[COLOR="#ff0000"]sda*[/COLOR] /media/[COLOR="Red"]data[/COLOR]    ext3    defaults 
```

To mount it 

```
sudo mount -a
```

check the new partition has mounted with 

```
mount
```

It should mount on reboot.

---

### Post by twoseids on 2008-05-14
Awesome! It worked. The only thing I had to change was to tweak the permissions so I could add/delete/etc without having to sudo.

One last question: How can I hide my /dev/sda1 partition from the Places menu (and Nautilus, too, if that's possible)? It's just my boot partition, so I don't need to always see this 41.1MB partition.

---

### Post by forestpixie on 2008-05-14
I don't know that you can pick and choose - I hope that you don't get problems with such a small /boot partition - others have had some. You start getting kernel upgrades and you could soon run out of room.

---

### Post by twoseids on 2008-05-14
> **forestpixie said:**
> I don't know that you can pick and choose - I hope that you don't get problems with such a small /boot partition - others have had some. You start getting kernel upgrades and you could soon run out of room.
Hmm, well I haven't modified my /dev/sda1 as long as I can remember, and I've been running Ubuntu since Hoary. So I guess/hope I'm okay!

Thanks again for all your help today.

---

### Post by forestpixie on 2008-05-14
You're welcome - only reason I said that was the threads I've seen that have had problems. If you've been around longer than me you've probably seen more of them.

My /boot is at 37Mb at the moment - another kernel upgrade would tip it over your 41Mb

---

