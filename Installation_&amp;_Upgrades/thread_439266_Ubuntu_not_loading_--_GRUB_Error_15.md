---
title: "Ubuntu not loading -- GRUB Error 15"
date: 2007-05-10
forum: Installation &amp; Upgrades
---

### Post by Sh00nya on 2007-05-10
I am having a problem with loading Ubuntu Linux in my dual-boot machine, wherein Windows Server gets loaded without a problem. 

To sum up the issue: my machine has 3 HDDs with Windows on the first and Ubuntu on the second drive...the third drive being used under Ubuntu ....last week I was trying to configure partition on the this drive n somehow messed up the primary Ubuntu drive ie the second one....consequently 
next time the Grub failed to load...I took it to one of my instructors who after being unable to help in this matter suggested to install Fedora on third drive ....the Grub menu came back n I could boot both into Fedora as well as Windows but still not into Ubuntu...everytime I chose Ubuntu it would stop at file not found error (15)..meaning that the Grub couldn't find the  kernel for Ubuntu at the location listed in menu.lst file under boot folder in grub directory in the boot partition of the 3rd drive (where Fedora was installed)...so after considerable efforts with no result I decided to install Ubuntu over Fedora thinking that with Ubuntu again on the system grub might be able to load the original Ubuntu (in 2nd drive)....but still the problem persists...I looked up online n did whatever I think matched my situation like modifying grub...updating menu.lst file...

I in fact used Knoppix as well as UBuntu Live CD for mounting partitions....since I installed UBuntu over Fedora on the third drive (hd2,0)...thats what shows up when I search the menu.lst file in Grub shell...after I mount that drive....more over I don't have a grub.conf file  although all the rest of the files like device.map are present in the grub directory....as I mentioned Windows gets loaded perfectly its the Ubuntu thats the problem...when thats chosen in the Grub menu...it shows the following msg:
----
Booting 'Ubuntu, kernel 2.6.20-15-386

root (hd2,0)
Filesystem type is ext2fs, partition type 0x83
kernel /vmlinuz-2.6.20-15-386 root=/dev/mapper/Ubuntu-root ro quiet splash

Error 15:File not found...
Press any key to continue
----

...n this is what fdisk -l shows:
---
Disk /dev/hda 20.5 GB.... (This is the Windows drive)

Device      Boot    Start    End    Blocks    Id    System
/dev/hda1  *    1    26    208813  6    FAT16
/dev/hda2 .......

Disk /dev/hdb: 6448 MB (This is in fact my original UBuntu)
Device      Boot    Start    End    Blocks    Id    System
/dev/hdb1  *    1    26    208813  83    Linux

Disk /dev/sda: 9104 MB (This UBuntu I installed over Fedora)
Device      Boot    Start    End    Blocks    Id    System
/dev/sda1  *    1    608    ...     83    Linux
/dev/sda2       609    1106    ...     5    Extended
/dev/sda5       1054    ...    ...     82    Linux swap/Solaris
/dev/sda6       1    608    ...     83    Linux
------

Also, as mentioned above...when I mount this last drive -- sda and enter the grub shell...run the find/boot/grub/menu.lst command it gives

(hd2,0)

as the output.

One thing I noticed was there was no gub.conf file any where...am I missing something...? To my understanding...grub is not able to locate the kernel in
the location mentioned in menu.lst file..

Here's a partial shot of what 's there in the menu.lst file:

---

title    Ubuntu
root    (hd2,0)
kernel     /vmlinuz-2.6.20-15-386    root=/dev/mapper/Ubuntu-root ro quiet
splash
initrd    /initrd.img-2.6.20-15-386
savedefault
..
.
title    Windows NT/2000/XP
root    (hd0,)
savedefault
makeactive
chainloader    +1
----

BTW, I remember copying the grub file from my original Ubuntu drive (hdb1) over in the new location...is that whats causing the problem...that kernel location didn't get updated...

TKA for any insight into this problem!

---

### Post by ajgreeny on 2007-05-10
Show us the output fron **sudo fdisk -l** and we may be able to help you.  It sounds as if your partitions have got renamed in some way, as you suggested.

---

### Post by Sh00nya on 2007-05-10
The output from sudo fdisk -l is this:


Disk /dev/hda 20.5 GB.... (This is the Windows drive)

Device Boot Start End Blocks Id System
/dev/hda1 * 1 26 208813 6 FAT16
/dev/hda2 .......

Disk /dev/hdb: 6448 MB (This is in fact my original UBuntu)
Device Boot Start End Blocks Id System
/dev/hdb1 * 1 26 208813 83 Linux

Disk /dev/sda: 9104 MB (This UBuntu I installed over Fedora)
Device Boot Start End Blocks Id System
/dev/sda1 * 1 608 ... 83 Linux
/dev/sda2 609 1106 ... 5 Extended
/dev/sda5 1054 ... ... 82 Linux swap/Solaris
/dev/sda6 1 608 ... 83 Linux

----

---

### Post by ceverett on 2007-05-14
I'm having the same problem.  going into grub and doing "find /boot/grub/stage1" gives a file not found error.

here is my "fdisk -l" nd "cat /etc/fstab":
```

root@william:/home/ceverett# sudo grub
Probing devices to guess BIOS drives. This may take a long time.
root@william:/home/ceverett# sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          31      248976   83  Linux
/dev/sda2              32       25334   203246347+   5  Extended
/dev/sda5              32         280     2000061   82  Linux swap / Solaris
/dev/sda6             281         529     2000061   83  Linux
/dev/sda7             530        1027     4000153+  83  Linux
/dev/sda8            1028        1525     4000153+  83  Linux
/dev/sda9            1526        2147     4996183+  83  Linux
/dev/sda10           2148        5882    30001356   83  Linux
/dev/sda11           5883       25334   156248158+  83  Linux
root@william:/home/ceverett# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=5fcdd7a0-1697-47c3-8160-3595b4ce6e79 /               reiserfs defaults        0       1
# /dev/sda1
UUID=760d3a10-8515-4b14-aaf1-8a08d68abea0 /boot           reiserfs notail          0       2
# /dev/sda11
UUID=dc53d499-635b-4a24-9035-afabfb0b97de /home           reiserfs defaults        0       2
# /dev/sda9
UUID=6029d3da-28a1-4a23-8173-2d1a552430a4 /tmp            reiserfs defaults        0       2
# /dev/sda7
UUID=b285947f-5697-430a-8cd0-457250764cf2 /usr            reiserfs defaults        0       2
# /dev/sda8
UUID=0defdc7b-24d8-4811-bc56-9dbfa4c20ff6 /var            reiserfs defaults        0       2
# /dev/sda10
UUID=513d8079-9ba4-43cb-80a5-919a9ff16a09 /var/lib/mysql  reiserfs defaults        0       2
# /dev/sda5
UUID=c1ea0ac5-c6d1-49d1-86a8-31309ec19d58 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0


```

---

### Post by psusi on 2007-05-14
Looks like your Ubuntu entry is missing the /boot before the /vmlinuz part.  Change it to /boot/vmlinuz...

---

### Post by matthinckley on 2007-05-19
i have the same error and I press e to edit.. deleted the savedefault line and it boots just fine.. don't know why this is happening though

---

