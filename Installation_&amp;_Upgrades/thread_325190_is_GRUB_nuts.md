---
title: "is GRUB nuts???"
date: 2006-12-25
forum: Installation &amp; Upgrades
---

### Post by usien on 2006-12-25
i am totally new to linux nd ubuntu.i downloaded ubuntu 6.10 livecd and after evaluating i decided 2 install it.wen i installed it the GRUB didnt by default detect my previous windows xp installation.i tried to add the following to menu.lst but wen i run this entry it says 'invalid device requested' or 'non executable format' :

title                    Windows XP
root                    (hd0,1)
makeactive
chainloader          +1

i also tried changing (hd0,1) to all the partitions there r (e.g (hd0,2) (hd0,3) nd so on), but still the same error. can anyone help.i am using dell inspiron 6000 laptop.i tried installing windows xp nd ubuntu on top of each (abt 10 times :evil: ) other but to no use.eventually i had to remove ubuntu cause i need 2 use windows 4 a couple of softwares.i really like ubuntu but it doesnt want 2 work with me!

---

### Post by bulldog on 2006-12-25
Give us the output of ```
sudo fdisk -l (l as in like)
```
So we can see which partition is used by windows.

---

### Post by usien on 2006-12-25
isnt there ny other way cause i'll hav 2 install ubuntu again nd my windows will go then i will hav 2 install windows again!

---

### Post by bulldog on 2006-12-25
Well you can't run Ubuntu when it's not installed,can you?
If you want windows you won't need GRUB.

If you want a dual boot machine,you'll have to install Ubuntu again,and after that we can modify your GRUB to boot windows and Ubuntu.

---

### Post by richbarna on 2006-12-25
Checkout my post about GRUB

[http://www.ubuntuforums.org/showthread.php?p=1319395#post1319395](http://www.ubuntuforums.org/showthread.php?p=1319395#post1319395)

---

### Post by usien on 2006-12-25
bulldog>>
well i can run ubuntu without installing (livecd) but then there is no use since the fdisk output wont b appropriate without ubuntu installation  :D  . so i am going 2 install ubuntu again (abt 11th time) nd then post fdisk output.
btw: i do want a dual machine

richbarna>> i read ur thread nd will try if it works!

thanx all

---

### Post by bulldog on 2006-12-25
> **richbarna said:**
> Checkout my post about GRUB

[http://www.ubuntuforums.org/showthread.php?p=1319395#post1319395](http://www.ubuntuforums.org/showthread.php?p=1319395#post1319395)

Nice How to and very useful,thank you,have it bookmarked for further reference.

---

### Post by bulldog on 2006-12-25
> **usien said:**
> bulldog>>
well i can run ubuntu without installing (livecd) but then there is no use since the fdisk output wont b appropriate without ubuntu installation  :D  . so i am going 2 install ubuntu again (abt 11th time) nd then post fdisk output.
btw: i do want a dual machine

richbarna>> i read ur thread nd will try if it works!

thanx all

Well the output should be the same as when you installed ubuntu concerning windows that is.
So you can boot the live cd and give me the outcome of fdisk,but we can't modify your menu.lst because you haven't one.
So the best thing is to install again and we take it from there,just give me a PM or post back her,I'll find it.

---

### Post by usien on 2006-12-25
here is the output:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          12       96358+  de  Dell Utility
/dev/sda2              13        5413    43383532+   f  W95 Ext'd (LBA)
/dev/sda3            5414        7110    13631152+  83  Linux
/dev/sda4            7111        7296     1494045   82  Linux swap / Solaris
/dev/sda5              13        1970    15727603+   7  HPFS/NTFS
/dev/sda6            1971        3928    15727603+   7  HPFS/NTFS
/dev/sda7            3929        5413    11928231    7  HPFS/NTFS

---

### Post by bulldog on 2006-12-25
Why on earth you put your windows in an extended partition?
Why not leave windows where it belongs,on the first primary partition?
You have managed to make it hard for you to boot windows.
In most cases you can't boot windows from a logical disk.
Maybe you can alter the boot.ini to point it to the right partition.

Take a look here to find some answers for your problem,

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

