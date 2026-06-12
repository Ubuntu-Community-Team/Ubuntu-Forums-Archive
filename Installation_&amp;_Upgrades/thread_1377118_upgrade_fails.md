---
title: "upgrade fails"
date: 2010-01-09
forum: Installation &amp; Upgrades
---

### Post by ralphtdog on 2010-01-09
Hi folks,
I ran into a wierd problem during an upgrade to ubuntu studio. This is 9.10 64 bit
 
here is the issue:
I intall Wubi from windows 7. IT installs the amd64 bit version and that works great. I do all upgrades and reboot. all is well.
 
I do the install of the ubuntu studio from the upgrade instructions at [https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu](https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu) and i get a sh:grub prompt
 
I try this several times and the exact thing happens again (does that mean I am insane?)
 
I look for the error and find this: [http://ubuntuforums.org/showthread.php?t=1339203](http://ubuntuforums.org/showthread.php?t=1339203)
 
I try the instructions and I get a screen that has this: [ 9.7.46801] sd 6:0:0:2: [sdf} Attached SCSI removable disk and just sits there.
 
I try this serveral times and I decide to install the studio upgrades one at a time. I reboot after each install. I find that the error occurs after I run the following command: sudo aptitude update && sudo aptitude install ubuntustudio-audio.\ after the reboot.
 
I can hit enter the initramfs prompt appears. 
 
Not sure what to do next....
 
Hardware: Dell xps 630 core dual running win 7 64 bit Nvidia 2 gig ram

---

### Post by ralphtdog on 2010-01-10
I burned both the basic Ubuntu-64 bit and Ubuntu studio64 bit disks and tried to install with those. both disks failed as soon as I started the install. (Black screen and a flashing cursor). I have to internal dvd drives and external dvd drive. All failed.
 
I had Ubuntu 64 working with the wubi install before I tried to do the upgrade. SO it is not a 64 bit/vs 32 bit issue.
 
I decided to try a 32 bit version of the studio disk and I was able to start the dvd install. This failed during the install of the select and Install software portion. This is booting from the install CD and installing to a  empty drive.
 
 
I have a cd-rom intergrity check, and it came back fine. 
 
It seems that the ttf-mscorefonts seem to be a problem. One other thing I can think of as causing the problem:
I purchased a SATA to IDE  converter because the computer didn't have enough SATA slots. Both of my internal DVD drives are plugged into the converter. I have also tried a extenal USB dvd drive to install.  MY next step is to try to remove the converter and install the dvd drive back to the SATA port.
 
 
Any ideas?

---

### Post by phillw on 2010-01-10
Hi,

when you say cdrom integrity check - is that the one in the install CD menu, or a different method ?

Also, are you trying to install with Wubi, or do a true dual boot install ?

Try running the ubuntu LiveCD in "don't alter my computer" mode. 
Assuming that boots okay, can you go to Terminal (Applications --> Accessories --> Terminal) and post back the output of
```
 sudo fdisk -l
``` (That's a little 'L' at the end)

Thanks,

Phill.

---

### Post by ralphtdog on 2010-01-10
I have tried to install both Wubi and dual boot. Both fail.
 
I have tried to run an install from mulitple cds/dvds all fail. I have booted from an external usb drive as well. 
 
when booting the Live cd, it starts and lets me choose the Try Ubuntu without any change, I get a flashing _ in the upper corner.
 
When booting from a usb stick using the pennlive loader I get the 
 
Loading /casper/vmlinuz.........................................
loading /casper/initrd.gz..........................................ready and it hangs.
 
I have checked the hardware and win7 64bit runs with out a problem.
 
the only time I had ubuntu working was when I did a wubi install of the 9.10 64 bit and that worked up till I tried the manual install of the studio packages.
 
The computer is a Dell xps 630 with three hds and two dvd drives/one burner. it is dual headed and has a nVIDIA GeForce gts240. IT has 2 gig of ram and a card reader.
 
It also has a dual port sata to Ide connector board to run the dvd drives. 
 
I don't think it is a hardware issue, I ran all the diags and nothing reported as bad.
 
I pulled the card reader and the sata/ide board and no change.
 
 
I did have one Wubi install work. I am going to try that again to see if there is something else wrong.

---

### Post by ralphtdog on 2010-01-10
I reinstalled the wubi verion but will not install the studio piece until I get an idea on the original issue.

Here it is :

[FONT=Fixedsys]rick@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x78000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  de  Dell Utility
/dev/sda2               9        1967    15728640    7  HPFS/NTFS
/dev/sda3   *        1967        1979      102400    7  HPFS/NTFS
/dev/sda4            1979       60802   472489984    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x269aedd0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4178    33554432    7  HPFS/NTFS

Disk /dev/sdc: 400.1 GB, 400088457216 bytes
16 heads, 63 sectors/track, 775221 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xc35b279d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      775221   390711352+  42  SFS

Disk /dev/sdf: 1977 MB, 1977614336 bytes
64 heads, 63 sectors/track, 957 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1         957     1929244+   6  FAT16
[/FONT]

---

### Post by ralphtdog on 2010-01-11
To be clear. ther are two seperate issues: 
I cannot install ubuntu from a dvd. I can only install from WUBI.

and  I can't upgrade or install the ubuntu or ubuntu studio from dvd or via the cammands on the ubuntu studio page. Nor can I install from a USB drive.

I am going to burn new disks after I download everything again from work.

thanks.

.

---

