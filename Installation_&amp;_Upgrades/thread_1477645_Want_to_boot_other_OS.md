---
title: "Want to boot other OS"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by Randymanme on 2010-05-09
After installing Ubunut 10.04, my other os isn't listed on the grub menu.  How to get it back?

Help would be appreciated.

---

### Post by Sef on 2010-05-09
Applications > Accessories > TerminalThen copy and paste the code below in the terminal:

```
sudo fdisk -l
```

Then copy and paste the results here.

That code will show how your hard drive(s) is (are) partitioned.

---

### Post by Randymanme on 2010-05-09
randymanme@randymanme-desktop:~$ sudo fdisk -l
[sudo] password for randymanme: 

Disk /dev/sdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004ce78

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2277    18289971   83  Linux
/dev/sdb2            2278        3103     6634845   83  Linux
/dev/sdb3            4572        4866     2369587+  83  Linux
/dev/sdb4            3104        4571    11791710   83  Linux

Partition table entries are not in disk order

Disk /dev/sda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a825b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3494    28060672   83  Linux
/dev/sda2            3494        3650     1253377    5  Extended
/dev/sda5            3494        3650     1253376   82  Linux swap / Solaris
randymanme@randymanme-desktop:~$

---

### Post by vinod_home on 2010-05-09
you should be able to run update-grub and that should get all the OS's back to the grub menu.

sudo update-grub 

If you want to read up on the new grub2 features and how it works here is the link [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

HTH

---

### Post by Randymanme on 2010-05-09
randymanme@randymanme-desktop:~$ sudo update-grub 
[sudo] password for randymanme: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found openSUSE 11.2 (i586) on /dev/sdb4
done
randymanme@randymanme-desktop:~$ 


Thank you very much!:guitar:

---

### Post by kansasnoob on 2010-05-09
We'll need to see the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Randymanme on 2010-05-12
Well, okay, I've got it ([http://bootinfoscript.sourceforge.net/)]("http://bootinfoscript.sourceforge.net/")  downloaded;  what do I do with it now?  I need to choose an application to open it, and some helper application, too, (though none in specifically mentioned).

---

