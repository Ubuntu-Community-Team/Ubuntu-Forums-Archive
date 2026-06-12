---
title: "Stange boot sequence with two HDD"
date: 2006-08-30
forum: Installation &amp; Upgrades
---

### Post by ricardo06 on 2006-08-30
I have two HDD, hda (primary master) and hdb (slave).
I installed ubuntu on hda and fedora on hdb. 
fedora was installed after ubuntu. 
Although i declared the primary disk as my boot disk in the bios, obviously, when ubuntu boots, it boots from the fedora installation, i can recognize the  grub menu of this installation. 
As my hdb disk is in the process of ending its life I want to restore boot from my primary disk.
Any one has an idea ?

thanks

Richard

additional info: 
 - i have two bootable partitions (hdb1 and hda12)

---

### Post by amo-ej1 on 2006-08-30
Fedora has overwritten your grub installation and placed itself in the bootsector of your first disk /dev/hda.

This can be easily restored, simly boot ubuntu, and run as groot "grub" 
now you enter *root (hd0,x)* this selects the partition grub should read, this is the partition the grub config file is on (it can be either the partition used to contain / or you could have chosen a different partition to be mounted at /boot, if unsure check the output of the 'mount' command).
Now suppose /boot is on /dev/hda you would type 
```

grub> root (hd0,0)
 Filesystem type is reiserfs, partition type 0x83
grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/reiserfs_stage1_5" exists... yes
 Running "embed /boot/grub/reiserfs_stage1_5 (hd0)"...  18 sectors are embedded
.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+18 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.
grub>

```

The second commands overwrites the MBR of the hd0 drive by the one found on the device you specified as a root device. Next you can type quit and  when you reboot you will be using the ubuntu config again.

---

### Post by ricardo06 on 2006-08-30
I did .
grub> root (hd0,11)

....
because my boot partition is on hda12. well now i cannot boot anymore. it says  it cannot find a valid disk. 

i am now working from a boot CD... not very convenient...
any more help would be much appreciated.

richard

richard

---

### Post by confused57 on 2006-08-30
Maybe this thread can help:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

---

### Post by randell6564 on 2006-08-30
You need to boot into Ubuntu and reinstall grub to the MBR.  Thats it!

Try this.,
[B]sudo grub

find /boot/grub/stage1[/B]

I am set up just like you, except I have Xubuntu on hdb1.  So your results of 'find /boot/grub/stage1' should look like this:

[B]grub> find /boot/grub/stage1
 (hd0,0)
 (hd1,0)
[/B]

So now you would do.,

[B]root (hd0,0)

setup (hd0)

quit[/B]

That will reinstall grub to your MBR.

---

