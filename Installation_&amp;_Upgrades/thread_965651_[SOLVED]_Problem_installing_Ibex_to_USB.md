---
title: "[SOLVED] Problem installing Ibex to USB"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by kwatson512 on 2008-10-31
I really like 8.10, especially the updated networking capabilities.  I'm trying to create a bootable USB (I have a Corsair Flash Voyager GT 16GB).  I've made 3 attempts:

1) Followed the instructions in the Live version, creating an 8GB persistence file.  I think that was too big, because after I made a few changes I got several notices that there was no more room on the drive.

2) Wiped that out and reformatted, then tried installing a full version on the stick (yes, including Grub).  That worked well, except that it performed excruciatingly slow.

3) Wiped that out and reformatted again, going back to the Live instructions with persistence, this time going for a 4GB persistence file.  I got a Grub error 17 on boot, so tried it again and just got the word "GRUB" on a black screen on boot.  I think something residual is still there from my attempt #2, but can't figure out how to get back to a fresh start.

Any ideas?

---

### Post by darkhammer8108 on 2008-10-31
are you trying to make a live usb drive?
if you are try this

#mkdosfs -vF 32 /dev/<your device partition>
<install unetbootin>
#unetbootin
then select the 8.10 Live CD and image it.

when you boot you may need to type 
/isolinux/vesamenu.c32
in order to get the system to start up.

---

### Post by GregMcn on 2008-10-31
Ok.Well i successfully installed 8.10 to a 8gb usb thumb drive and it was pretty simple.

Basically I put in the live CD and booted to install.

Go through all the screens until you get to the install section and select your thumb drive.(Make sure you dont select hda etc.It should show as SBA or similiar.)

Hit next and before installing click advanced to ensure you select install boot loader.

And away it goes.

When finished i rebooted with the usb stick and ensured that the bios was set to boot usb first and away it went.Using it now and works a treat.

P.S. No responsibility if you stuff it up so make double sure you set the correct partition when u install. Good luck.

---

### Post by caljohnsmith on 2008-10-31
If I were you, I would first reinstall Grub to the MBR of your USB drive to make sure Grub points correctly to the USB install for its boot files:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd1,0). If you get more than one answer, use the one where X = 1 or greater, and then do:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
That should at least make your USB drive bootable so you can get the Grub menu on start up. It might be that you won't be able to boot Ubuntu from the menu though, and you'll have to fix the menu.lst. But see if you can at least get as far as a grub menu, and we can work from here; otherwise let me know if you run into problems. :)

---

### Post by kwatson512 on 2008-10-31
caljohnsmith,

Thanks for the attempt, but evidently the "create a USB startup disk" script didn't install grub this time.  

I navigated to the USB drive (/media/CORSAIR).  The grub "find" command only found the instances of grub I have on my HDD (I am triple-booting WinXP, Mint 5, and OpenSUSE on this machine).

Here's the result:
```
grub> find /boot/grub/stage1
 (hd0,4)
 (hd0,7)
```

I know that the partition I want will be enumerated (hd1,0), but when I use the "root" and "setup" commands I get:
```

grub> root (hd1,0)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found
```

Is there a script in the Live CD to just install or repair grub?  Why wouldn't the "Create a USB startup disk" finish the task this time?

Thanks...

---

### Post by caljohnsmith on 2008-10-31
> **kwatson512 said:**
> 
Is there a script in the Live CD to just install or repair grub?  Why wouldn't the "Create a USB startup disk" finish the task this time?

Thanks...
So are you basically trying to install the Live CD to your USB at this point? Not a full install, is that true? If so, have you checked out:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

The "UNetBootin" program can do it all automatically, or there is also a bash script available on that page that will do the same thing. The steps I gave are only applicable to a full install, because installing a Live CD to the USB stick uses the syslinux boot loader instead of Grub.

---

### Post by kwatson512 on 2008-10-31
Intrepid Ibex comes with an option in the Administration menu to install a "USB startup disk," basically a live version with persistence.  And you're right, it does use syslinux as a bootloader instead of grub.  I was distracted by your earlier post on grub and forgot that salient fact.

So why do I get a "GRUB" message when I try to boot the live USB?  It should use ldlinux.sys, which is the syslinux boot executable.

Here are the folders and files on the USB:

Folders:
.disk
casper
dists
install
pics
pool
preseed
syslinux

Files:
autorun.inf
casper-rw (this is the persistence file created upon install)
ldlinux.sys
md5sum.txt
README.diskdefines
syslinux.cfg
umenu.exe
wubi.exe

---

### Post by caljohnsmith on 2008-10-31
How about first posting the following to help clarify your setup:
```
sudo fdisk -lu
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```

---

### Post by kwatson512 on 2008-10-31
Here are the results:

```
kwatson@kwatson-mint ~ $ sudo fdisk -lu
[sudo] password for kwatson: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xed1f86f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    98767619    49383778+   7  HPFS/NTFS
/dev/sda2        98767620   110205899     5719140   12  Compaq diagnostics
/dev/sda3       110205900   312576704   101185402+   5  Extended
/dev/sda5       110205963   134897804    12345921   83  Linux
/dev/sda6       134897868   139026509     2064321   82  Linux swap / Solaris
/dev/sda7       139026573   211399334    36186381   83  Linux
/dev/sda8       211399398   240219944    14410273+  83  Linux
/dev/sda9       240220008   312576704    36178348+  83  Linux

Disk /dev/sdb: 16.2 GB, 16240345088 bytes
255 heads, 63 sectors/track, 1974 cylinders, total 31719424 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00034125

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1    31719423    15859711+   c  W95 FAT32 (LBA)
```
```

kwatson@kwatson-mint ~ $ sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
GRUB
GRUB 
kwatson@kwatson-mint ~ $ sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
GRUB 
kwatson@kwatson-mint ~ $ 
```

I don't believe this should have returned GRUB for sdb, since I have syslinux there.  Is there a way to remove GRUB so it boots with syslinux?

Thanks for all this troubleshooting help.

---

### Post by caljohnsmith on 2008-11-01
Yes, that's interesting that sdb looks like it has Grub in the MBR instead of syslinux. If syslinux wasn't installed to the MBR of sdb, that might be an indication there are other issues too, but you could manually install syslinux to the MBR of sdb with:
```
sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sdb
```
Reboot, make sure sdb is first in the boot order, and let me know what happens. :)

---

### Post by kwatson512 on 2008-11-01
Haha!  I fixed it!

Manually installing syslinux didn't overwrite whatever remained of Grub in the MBR.  So I used dd to copy the MBR of another USB drive onto this one.  That made this one unbootable (great!).  So then it was just a matter of reformatting the USB partition and reinstalling Ubuntu.  Works like a champ now!  I'm writing this from my USB install.

:)

---

### Post by XProgrammer on 2008-11-02
I had similar problem with 2GB pendrive. I installed super-grub for some recovery purpose. Today i tried installing ubuntu 8.10 using "Create USB live" given by ubuntu 8.10rc (i'm running release candidate). After that, i did reboot, i got only GRUB and hang.  

Solution:

sudo apt-get install install-mbr

sudo install-mbr /dev/sdx 

x - your USB drive letter. (my case its 'b')


Thought of sharing this.. :)

---

### Post by Brian Smith on 2008-11-02
> **XProgrammer said:**
> 
Solution:

sudo apt-get install install-mbr

sudo install-mbr /dev/sdx 

x - your USB drive letter. (my case its 'b')


Thought of sharing this.. :)

This solution also worked for me, though with the final i386 release version, I did not have to install "install-mbr."  It was already a recognized command when I tried "sudo install-mbr /dev/sd(in my case "c")
Thanks for sharing that, and I wonder why theis did not work out of the box in using the create bootable usb key command from the administration menu...

---

### Post by C.S.Cameron on 2008-11-02
If your only problem with a Full install is that it is excruciatingly slow, 
try formatting in reiserfs, and not ext3, when you get to partitioning.
Seems to make a big difference in speed to me, 
when running off flash drive.

---

### Post by kwatson512 on 2008-12-23
Bottom line is that the Live USB Creator in Intrepid works like a champ.  I really like my fully portable "OS on a stick."  Very impressive to family and friends!  My problem was that I had experimented with several distros on that stick before figuring out how to clean up the MBR.

---

