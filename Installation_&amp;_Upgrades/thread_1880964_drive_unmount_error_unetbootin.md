---
title: "drive unmount error unetbootin"
date: 2011-11-14
forum: Installation &amp; Upgrades
---

### Post by CHAUDHRY07 on 2011-11-14
i had 11.04 working well on my pc dual boot with xp and then i upgraded to 11.10 and suddenly i couldnt see any video on any player just audio provided i had installed codecs or extras.some one asked me to reinstall ubuntu.
so i fix up the mbr and then formated the partition of 11.10.now i installed unetbootin and chose to use hard disk as bootloader.every thing went fine i made new partitions and when i click install now it just ran into a error.
cannot unmount /cdrom unmount and try again.and after this it is stuck nothing i can do.
i love ubuntu but its getting complex help me.

---

### Post by CHAUDHRY07 on 2011-11-16
failed to unmount partitions 

the installer needs to commit changes to partition tables,
but cannot do so because partitions on the following could
not be unmounted.

/cdrom

please close any applications using these mount points.

would you like the installer to try to unmount these partitions again

go back continue
this is the exact error message  
any body help please

---

### Post by WasMeHere on 2011-11-16
Hi CHAUDHRY07,

Please describe your present system in more detail, in order to make it easier to help you!

What computer do you have? Is there a CD/DVD drive? What can be booted now from the hard drive? What is installed but not working? What partitions do you have and what do they contain. Please post the output of
```
sudo fdisk -lu
``` and ```
df
```
How did you install your present system with Unetbootin: did you make a boot USB drive, and installed from it to the hard drive, or did you install a Unetbootin system to your hard drive? It is a silly question, but I can't figure it out from your description.


Have fun finding out :-)
Olle

---

### Post by CHAUDHRY07 on 2011-11-16
olle thanks for kind reply.
currently i have only 1 OS running on my system which is win xp.i have 5 partitions on my harddisk 3 of them are NTFS(on 1 win xp is installed and other two just contain data) and the 4th partition is formated as ext3 for linux.and 5th one is formated as linux swap.i partitioned using unetbootin-partitionmanagerrev146 software.
i am trying to install ubuntu 11.10 on 4th partition using unetbootin frugal install(mounting harddisk for disk iso).after installing unetbootin i rebooted and went in unetbootin option from bootloader and selected the partition for installation and click intall now.but it wouldnt proceed further and gives the error pasted in my above post.
and sorry if i am not clear.
some how i managed to install 11.04 natty on my system long ago using same process.but now i cant...........
i am missing ubuntu very much :(
regards

---

### Post by WasMeHere on 2011-11-16
I would say that *frugal install* suits a static system, where you might add some application and some personal data. But if you want a full-featured linux system with updates for security and improvement of the software, I recommend that you install it.

Ubuntu is made for testing as a live system and then, if it looks promising, installation in the conventional way. So test Ubuntu 11.10 live from a boot CD or USB drive, and then if you wish, install it to your partition with ext3!

---

### Post by CHAUDHRY07 on 2011-11-16
no by frugal install means installing it on dual boot using just harddisk no external disk required and not by wubi.

---

### Post by CHAUDHRY07 on 2011-11-16
[http://www.damnsmalllinux.org/wiki/index.php/Frugal_Install](http://www.damnsmalllinux.org/wiki/index.php/Frugal_Install)
[http://wiki.wolvix.org/FrugalInstall](http://wiki.wolvix.org/FrugalInstall)

have look at these links.probably i couldnt communicate well enough and am sorry for that.
regards

---

### Post by WasMeHere on 2011-11-17
I know that there are issues for many users with graphics when installing 11.10. These might be easier to solve in an ordinary installation. But your problem now is to clean your system and reinstall it, right?

First you should backup your personal files, documents, photos etc.

Can you run a live system from a live CD or USB drive? In that case, you can reformat the partition with Ubuntu using gparted on the live Ubuntu system. It is important that you run the system from another drive, not the one that you will edit with gparted.

Then you should be able to reinstall Ubuntu the way you want. If you do all the steps it should work for a normal install as well as for your unetbootin install to the hard drive.

Good luck :-)
Olle

---

### Post by CHAUDHRY07 on 2011-11-17
i am running it from other partition and right now i am in live ubuntu but its again giving the same error.....any tests to check what is the source of error

---

### Post by CHAUDHRY07 on 2011-11-17
Disk /dev/sda: 40.8 GB, 40822161408 bytes
255 heads, 63 sectors/track, 4963 cylinders, total 79730784 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf4fbf4fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    20482874    10241406    7  HPFS/NTFS/exFAT
/dev/sda2        20482936    79728639    29622852    f  W95 Ext'd (LBA)
/dev/sda5        20482938    35837951     7677507    b  W95 FAT32
/dev/sda6        35840000    48801791     6480896    b  W95 FAT32
/dev/sda7        48805533    78236549    14715508+  83  Linux
/dev/sda8        78236613    79714529      738958+  82  Linux swap / Solaris

---

### Post by WasMeHere on 2011-11-17
> **CHAUDHRY07 said:**
> am running it from other partition and right now i am in live ubuntu but its again giving the same error.....any tests to check what is the source of error

Disk /dev/sda: 40.8 GB, 40822161408 bytes
255 heads, 63 sectors/track, 4963 cylinders, total 79730784 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf4fbf4fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    20482874    10241406    7  HPFS/NTFS/exFAT
/dev/sda2        20482936    79728639    29622852    f  W95 Ext'd (LBA)
/dev/sda5        20482938    35837951     7677507    b  W95 FAT32
/dev/sda6        35840000    48801791     6480896    b  W95 FAT32
/dev/sda7        48805533    78236549    14715508+  83  Linux
/dev/sda8        78236613    79714529      738958+  82  Linux swap / Solaris
Any tests...
Please describe your computer: cpu, ram, ***graphics*** ...
The unity desktop environment needs more computer power than gnome2 of the old Ubuntu. You may also try Xubuntu and Lubuntu, with smaller footprints, so that more computing power is left for the applications.

Your problems with video ... With Ubuntu you need to download the proprietary drivers and codecs yourself due to licensing limitations. With Linux Mint (based on Ubuntu) those are included on the live disk. Maybe it would work better for you with the unetbootin frugal install, to run Linux Mint. I suggest that you start trying Linux Mint 11 (of course live at first).

---

### Post by CHAUDHRY07 on 2011-11-17
i have p4 2.4Ghz,512 mb of ram and built in 64mb video gpu.

---

### Post by WasMeHere on 2011-11-17
> **CHAUDHRY07 said:**
> i have p4 2.4Ghz,512 mb of ram and built in 64mb video gpu.
This computer is not powerful enough to run Unity desktop environment. But with XFCE or LXDE the computer will be fine again :-)

This can be done with Xubuntu or Lubuntu or with the corresponding Linux Mint versions. Also Linux Mint 11 standard with gnome 2 will work but not as fast as the other two small desktop environments. LXDE is the smallest one. The desktop environments can be installed directly into an existing system (with Synaptic or [FONT="Courier New"]sudo apt-get install ...[/FONT]), but I recommend to make a fresh install from a downloaded iso file.

---

### Post by CHAUDHRY07 on 2011-11-17
i think i ll opt for xubuntu....thanks for help

---

### Post by CHAUDHRY07 on 2011-11-18
i have a question.....can i install ubuntu and then completely convert to xubuntu?
regards

---

### Post by WasMeHere on 2011-11-18
If you install (vanilla) Ubuntu you will have not only its visible desktop but also the infrastructure behind it. If you install the Xubuntu desktop on top of that, in principle you should be able to get rid of all the 'vanilla'-specific software, but it is difficult, and you may damage your system. So in that case you should accept having some disk space occupied but on the other hand, you can also use that software for example Nautilus within XFCE.
```
sudo apt-get install xubuntu-desktop
```

---

### Post by CHAUDHRY07 on 2011-11-19
atlast i have found a work around for the problem i faced.
before starting installer just run command "sudo umount -l -r -f /cdrom" and now the most important type the next command "sudo mount /dev/sda1 /cdrom" but dont press enter.when you have selected partition just click install now and enter this command.if it is not fast then ubiquity will crash.it will surely work if you are booting from harddrive using unetbootin and facing cdrom unmount error.

thanks for your kind help.and yeah i have reinstalled ubuntu now i will migrate to xubuntu found a workaround for that on pshycho cat website.i was directed their by xubuntu official site.

regards

---

### Post by WasMeHere on 2011-11-19
Thanks for sharing your solution!
When you feel satisfied, please mark the thread SOLVED

Having fun finding out
Olle

---

### Post by CHAUDHRY07 on 2011-11-20
yup thanks for your help man.

regards

---

