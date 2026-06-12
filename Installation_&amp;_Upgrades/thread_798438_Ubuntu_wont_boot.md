---
title: "Ubuntu wont boot"
date: 2008-05-18
forum: Installation &amp; Upgrades
---

### Post by DaleNewton on 2008-05-18
Hi,

I am new to Linux, and have been reading thought the wikis when I get stuck, but any help with this really appreciated.

I have recently edited my hard driver partitions using 'parted', and now Ubuntu wont boot anymore.

At first I got a Grub 'error 14'. Then I installed xp in the partition I created for it, and it formatted that partition.  Then, tp try and get Ubuntu back, I used the live cd and parted, and flagged the original sda1 for boot. But Im getting a boot error message in SPanish (the xp version was in SPanish), and no boot.  Xp still boots up fine.

This was the parted, print output before editing partitions and starting xp installation:


Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  9097MB  9097MB  primary  ext3         boot 
 2      9097MB  160GB   151GB   extended           
 6      9097MB  148Gb   139GB   logical  ex3
 7      148GB   154GB   5922MB  logical  linux swap
 5      154GB   160GB   6161MB  logical  linux-swap
    
Ubuntu Hardy is on number one (sda1).  THe swap space for it was 5.  I made another installation of Ubuntu which (I think) was on 6.

This is now:

Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  9097MB  9097MB  primary  ext3         boot 
 2      9097MB  154GB   145GB   primary  ntfs              
 3      154GB   160GB   6161MB  primary  linux-swap    

Thanks,
Dale.

---

### Post by cdtech on 2008-05-18
I would stop grub, hilite the Ubuntu kernel, press "e" to edit and look at your boot drive. It should look something like (hd0,0) for the first partition. If it's not, change it and boot from there. You can edit the /boot/grub/menu.lst once you get into Ubuntu to make it permanent. Window's is using (hd0,1).

---

### Post by DaleNewton on 2008-05-19
Hi cdtech,

Thanks.

I cant stop grub though. If I flag partition /dev/sda2/ for windows it boots windows OK. But if i flag partition /dev/sda1, which is the two ubuntu kernels I had installed when I got the laptop, it just prints ' error cargar el systemo operativo'.  I cant manage to stop grub becasue it doesnt visibly start.

I can get into BIOS ok, and I can get into the boot drive options menu, but I cant get the kernel bot list from grub that I could before. Is there a special key to stop grub?

I used to get 'grub loading ...1...2...3....4....5.

After installing xp I got 1....5... then error 14.

Now I just get ' error cargar el systemo operativo'.  The fact that that mesage is in spanish makes me think that its something to do with the xp, because its in Spanish.

I can access the boot menu.lst anytime using the live cd, and all my files and the other data on the partition seems to be there.

---

### Post by confused57 on 2008-05-19
You might try reinstalling grub to the mbr, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

You're probably going to get a UUID error when you try to boot into Ubuntu, since you repartitioned your hard drive...what you might want to do is mount your Ubuntu partition from the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_a_reiserfs_filesystem](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_a_reiserfs_filesystem)
See the link, but it would be something like:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda1 /media/ubuntu
gksudo gedit /media/ubuntu/etc/fstab
```

Check the UUID's in your fstab with the output of:
```
blkid
```

---

### Post by DaleNewton on 2008-05-21
Thanks!

Looked at that guide and it did the trick.

Doesnt give otion of booting windows in grub though. I guess Ill have to inert windows details in the boot.lst file.  Not sure of the code for that yet , but I think the grub help files should show how to do it.

Dale.

---

### Post by confused57 on 2008-05-21
> **DaleNewton said:**
> Thanks!

Looked at that guide and it did the trick.

Doesnt give otion of booting windows in grub though. I guess Ill have to inert windows details in the boot.lst file.  Not sure of the code for that yet , but I think the grub help files should show how to do it.

Dale.
Your Windows is on (hd0,1), as mentioned by cdtech...to edit your menu.lst:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

Try adding this entry to the very end of your menu.lst:
```
title Windows XP
root (hd0,1)
makeactive
chainloader +1
```
you can put anything you'd like for the title.

---

### Post by DaleNewton on 2008-05-22
Thanks,

Got dual boot running with GRUB.

Found this selection of comprehensive guides to installing GRUB and dual booting all kinds of OS's.

[http://apcmag.com/howto_category.htm?cid=198](http://apcmag.com/howto_category.htm?cid=198)

Dale.

---

