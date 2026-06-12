---
title: "Trouble Dual Booting"
date: 2008-10-13
forum: Installation &amp; Upgrades
---

### Post by jvaverka24.86 on 2008-10-13
Hi everyone,

First of all, I'd just like to start by thanking anyone who can help me with my issue.  It is much appreciated!  Now, onto the problem at hand...

I have 2 hard drives which I am trying to use for my dual boot system.  On the first hard drive I have Vista installed.  It is using the whole drive.  The second drive I have has several partitions.  The first 2 are used for data, and then I have installed Ubuntu on the third partition.  

In the past, after installing Ubuntu (I have installed it before and had to remove it) a reboot has brought up the GRUB menu and everything has worked correctly.  However, after my most recent installation, I am not presented with any menu.  Instead, Vista starts loading with out any options.  It's as if Ubuntu/Grub was never installed.  After I removed Ubuntu the first time, I did run commands to fix the mbr and return it to the Vista mbr so I was not presented with a menu and had the original functionality of a single boot to Vista.  I'm not sure if this has confused GRUB/Ubuntu in some way or what.  I had presumed when I reinstalled Ubuntu that GRUB would be reinstalled and everything would work correctly, but that did not happen.  

In an attempt to try to be able to use my Ubuntu installation, I added an entry using EasyBCD 1.7.2.  This is also something I had used in the past successfully.  I added a Linux entry and gave it the type GRUB and selected the installation partition.  Under the settings for the Ubuntu Installation, EasyBCD shows this information:

[INDENT]Entry #2

Name:  Ubuntu
BCD ID:  {95d31e04-980a-11dd-b162-cb4a07815291}
Drive:  C:\
Bootloader Path:  \NST\nst_grub.mbr[/INDENT]

This path is something within Vista and not the Ubuntu installation drive, so I am unsure if this is the way it should look or not.  Anyway, the result I get with this setup is the Windows boot manager is shown, and Ubuntu is listed as an option.  However, if I select to try to boot to Ubuntu, I am presented with this:

[INDENT]BootPart 2.60 Bootsector (c) 1993-2005 Gilles Vollant [http://www.winimage.com/bo](http://www.winimage.com/bo)
otpart.htm
Loading new partition
Bootsector from C.H. Hochstätter[/INDENT]

At this screen nothing happens and I can't do anything.

So this is the problem I'm having with not being able to boot into my Ubuntu installation...  Sorry this is so long, but I wanted to provide as much information as possible, as I know that makes things easier for you guys to diagnose what's going on.  Again, **_[SIZE="5"]THANK YOU[/SIZE]_** very much to anyone who is able to help me out!

Thanks,
J

---

### Post by caljohnsmith on 2008-10-13
If you want to use the Vista boot loader to boot Ubuntu like you have tried with EasyBCD, here is a tutorial that might help:

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

Personally I would just use Grub to boot either Ubuntu or Vista. If you would like help with that, then open up a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "operating system"
```
So replace "sda" above with each of your drives. And finally, for each command above that returns "GRUB", please post:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] bs=1 skip=1049 count=2 2>/dev/null | hexdump
```
And replace sda with the drives that previously returned "GRUB". And lastly, from the fdisk output above, note which is your Ubuntu partition (it should be type "linux" under "system"), and post the output of the following:
```
sudo mount /dev/sdX /mnt
cat /mnt/boot/grub/menu.lst
```
Where "sdX" is your Ubuntu partition, for example /dev/sdb2. That will greatly clarify exactly what your setup is right now.

---

### Post by jvaverka24.86 on 2008-10-13
caljohnsmith,

Thanks for your reply.  I will give this a try when I get off of work.  I'll have to run those commands using the LiveCD...but that shouldn't cause any problems or list the drives differently should it?  I also prefer to use the GRUB boot loader, but I was trying EasyBCD as a alternate option since GRUB was not working.  Thanks again and I will get the results from those commands posted a little later.

J

---

### Post by jvaverka24.86 on 2008-10-13
Ok, I have run the suggested commands in the terminal using the LiveCD and here are the results I get.
```

sudo fdisk -lu
``` 
returns:
```
Disk /dev/sda: 500.1 GB, 500106780160 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976771055 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5f9729c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   209848319   104923136    7  HPFS/NTFS
/dev/sda2       209848320   419694591   104923136    7  HPFS/NTFS
/dev/sda3       972767880   976768064     2000092+  82  Linux swap / Solaris
/dev/sda4       876763440   972767879    48002220   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80025280000 bytes
240 heads, 63 sectors/track, 10337 cylinders, total 156299375 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x21e521e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   156296035    78147986+   7  HPFS/NTFS
```



```
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "operating system"
```
using sda returns GRUB and using sdb (which has Vista installed) returns:
```
Error loading operating system
Missing operating system
```


Next, for sda which returned GRUB,
```

sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump
```
returns:
```
0000000 ff03                                   
0000002
```


and finally,
```
cat /boot/grub/menu.lst
```
returns:
```
cat: /boot/grub/menu.lst: No such file or directory
```


I think that should be what you were looking for.  Let me know if I didn't do something right.

THANKS!
J

---

### Post by caljohnsmith on 2008-10-13
Jvaverka24.86, those commands tell me that you have Grub installed to the MBR (Master Boot Record) of drive sda, and it is correctly pointing to your Ubuntu partition sda4 for its system files (menu.lst, etc). Also, sdb has a Windows MBR like it should, since drive sdb is your Vista drive, correct? 

So bottom line, if when you boot up you are getting Vista, your BIOS must be set to boot your sdb Vista drive first, not the Ubuntu drive. I think all you need to do is change your BIOS boot order so that the Ubuntu drive boots first. That should at least get you to the Grub menu on start up, but you might have to modify the OS menu entries to get Ubuntu and Vista booting properly. But first see if you can get the Grub menu on start up, and we'll go from there. :)

---

### Post by jvaverka24.86 on 2008-10-14
caljohnsmith,

Thank you very much for your help!!

After switching the sda hard drive to boot first everything worked great...except I still have to remove the Ubuntu record from the Vista installation, but that I know how to do.  I can't believe I missed such an easy fix.  After you mentioned it I had to do that previously when I had installed Ubuntu, but it never even crossed my mind this time.  Thanks so much!

J

---

### Post by caljohnsmith on 2008-10-14
I'm glad that it was such an easy fix too; sometimes sorting out booting issues with two or more HDDs can take a lot more time. Glad I could help out; cheers and have fun. :)

---

