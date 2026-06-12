---
title: "[SOLVED] no swap after expanding it in gparted"
date: 2008-07-20
forum: Installation &amp; Upgrades
---

### Post by cwacker on 2008-07-20
I expanded my swap from 950 mb to 1200 mb in gparted live, after that i coulndt use it. I changed the uuid of /dev/sda5 (swap) and put it into fstab with:

mkswap and then just edited fstab and put the uuid in it.

fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=3bba1285-733a-43ff-bb58-f1ceaf4e3a68 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=115431ca-ba73-467f-a869-abb75ec64d16 /boot           ext3    relatime        0       2
# /dev/sda3
UUID=0ebeadaa-d2f1-4668-a0b4-77986af8d0b9 /home           ext3    relatime        0       2
# /dev/sda5
UUID=539e6f8a-7d74-40b3-82ef-60438fb869b0            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


blkid:
/dev/sda1: UUID="115431ca-ba73-467f-a869-abb75ec64d16" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sda2: UUID="3bba1285-733a-43ff-bb58-f1ceaf4e3a68" TYPE="ext3" 
/dev/sda3: UUID="0ebeadaa-d2f1-4668-a0b4-77986af8d0b9" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sda5: TYPE="swap" UUID="539e6f8a-7d74-40b3-82ef-60438fb869b0" 
/dev/sdb1: UUID="167CB7057CB6DF25" LABEL="STORAGE" TYPE="ntfs" 


as you can see the uuid 539e6f8a-7d74-40b3-82ef-60438fb869b0 are identical.. Ive also run swapon -va with no sucess.

Thanks before hand


edit: on boot i recieve "mount point SWAP does not exist" and then a red [FAIL]. since the mounpoint in fstab is swap, maybe i should change it to SWAP (capitals)?
edit 2. did not help..

---

### Post by ajgreeny on 2008-07-20
After the UUID number locating the partition add the word **none** which is how my fstab is showing, ie there is no mount point in fstab for swap partitions, simply mounting as swap is enough.  Like this:-
```
# /dev/sda5
UUID=1bfd912d-b6b6-4a68-9aaf-4139513772ec none            swap    sw              0       0
```

---

### Post by cwacker on 2008-07-20
Oh my! :D
It works! Thanks alot! Maybe next time i'll make a backup before i mess with system critical files...8-[

---

### Post by coffeecat on 2008-07-20
**cwacker**, if I've understood your first post you resized your swap partition and that changed its UUID. I hope you keep in contact with this thread because you have now lost your pretty usplash screen (if you're using Hardy). How do I know? Bitter experience. :(

[All is explained]("http://ubuntuforums.org/showthread.php?t=864936"). In fact, you'll probably need to go to the thread(s) I've linked in my post there.

---

### Post by cwacker on 2008-07-20
Actually, I had already removed the splash in GRUB, so I didn't even know it was missing :P it seems that that problem should be related to hibernation, why is that?

Just to let me double check: in fstab the thing next to the UUID is always the presumed mountpoint? And i hade removed "none" which made swap stand next to the uuid and thats was why my swap did't mount?

---

### Post by coffeecat on 2008-07-20
> **cwacker said:**
> it seems that that problem should be related to hibernation, why is that?

Because this is Linux? :?

:lol:

> **cwacker said:**
> Just to let me double check: in fstab the thing next to the UUID is always the presumed mountpoint? And i hade removed "none" which made swap stand next to the uuid and thats was why my swap did't mount?

Yes. First field/column is device. Second mountpoint. Third filesystem type. Fourth mount options. And 5 & 6 are to do with unmounting, but I can't remember the terms. I'm using my Mac atm so I can't check in man fstab.

---

### Post by ajgreeny on 2008-07-20
> Just to let me double check: in fstab the thing next to the UUID is always the presumed mountpoint? And i hade removed "none" which made swap stand next to the uuid and thats was why my swap did't mount?Yes, that's about it!  You were trying to mount the swap partition at "swap" which didn't exist.

Incidentally, it is possible to still use the /dev/sda5 instead of the UUID in fstab if you want or need to, though that can also cause problems occasionally when partition numbering changes for some reason or other.  The only reason you had a problem was that the UUID changed, as it always (usually?) does when you do anything to it with gparted etc.

---

### Post by cwacker on 2008-07-20
on the other hand, my hibernation don't seem to work.. or.. well.. id does hibernate but it doesn't "remember" anything about the earlier state of the system...

---

