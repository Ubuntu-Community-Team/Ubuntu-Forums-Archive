---
title: "Boot loader failed to install"
date: 2011-08-30
forum: Installation &amp; Upgrades
---

### Post by pchokola on 2011-08-30
I got all the way to the very last step of the 10.04.3 Server LTS installation, where I attempted to install the bootloader into the /dev/sdc3 partition as noted below, but it came up with a failure message that it could not install the boot loader. I was forced to select "Continue without bootloader".
 
So,
 
1) Why did this happen so I do not go through this on the next install?
2) How do I fix it without reinstalling everything (I dread setting up all those logical volumes again).
3) Is it OK to use GRUB2, and is it possible to chainload from Centos6 into Ubuntu 10.04.3 or other  similar method (I like the option to have a menu of kernels to pick from), and if so is there a special syntax?.
 
CONFIGURATION
My intent is to dual boot from Centos 6 into Ubuntu 10.04.3. Is my setup correct? One thing I did not do is set the bootable flag on the /dev/sdc3 /boot partition, but not sure that makes a difference or not.
 
My configuration:
 
Centos 6
/dev/sdc1 = /boot (ext4)
/dev/sdc2 = LVM (/, /home and swap logical volumes)
 
Ubuntu 10.04.3 LTS Server
/dev/sdc3 = /boot (ext2)
/dev/sdc5 = LVM (/, /home and swap logical volumes)
 
I need a beer.

---

### Post by YesWeCan on 2011-08-30
Hi. I am not familiar with CENTOS and what boot loader it uses. Does it boot from its boot partition? So do you have a normal MBR at the moment?

Grub is not designed to work from a partition. It is designed to replace the normal MBR boot code and basically take over your disk. It will work if its boot code is put in a partition boot record (PBR) but not reliably because of the way it locates other files it needs. To install to the PBR you would need to boot a live CD/USB and run (check the drive name is still sdc first):
[COLOR=Navy]sudo mount /dev/sc3 /mnt
sudo grub-install --force --boot-directory=/mnt /dev/sdc3[/COLOR]
and if you are using a normal MBR then set the boot flag to sdc3.

Whether if you installed Grub to the MBR (as it is designed to work) it would be able to boot CENTOS I am not sure. To install to the MBR use:
[COLOR=Navy]sudo mount /dev/sc3 /mnt
sudo grub-install --force --boot-directory=/mnt /dev/sdc[/COLOR]

For more help please download and run [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) and post RESULTS.txt here.

[edit] A quick Google suggests CENTOS already uses Grub. So you should be able to boot CENTOS and add your Ubuntu OS to the CENTOS boot menu (no need to install another Grub). If you are using Grub2 you just do [COLOR=Navy]sudo update-grub[/COLOR].
Post your Grub version from CENTOS: [COLOR=Navy]grub-install -v[/COLOR]

---

### Post by pchokola on 2011-08-31
Thanks for replying. I have included the answers to your questions. Bear in mind that this is my first time using Ubuntu or Debian, as well as GRUB2, so this is all new to me. My past experience has strictly been with Red Hat and its clones (Centos, Scientific Linux) as well as its development branch (Fedora).
 
 
1) I am not familiar with CENTOS and what boot loader it uses.
CentOS, like Scientific Linux and several others are free clone versions of the associated Red Hat Enterprise software. They use legacy GRUB, which can be placed in either the MBR or the first sector of a boot partition.
 
 
2) Does it boot from its boot partition? So do you have a normal MBR at the moment?
Yes, Centos6 was installed on a clean disk, with the bootloader installed in the MBR.
 
 
3) Post your Grub version from CENTOS: [COLOR=#000080]grub-install -v[/COLOR]
Legacy GRUB is installed via Centos6. GNU GRUB 0.97
 
4) Grub is not designed to work from a partition.
With Centos/Fedora/Red Hat, this is the way I have always done it, whether it is really the correct way or not, well I can not say for sure. As far as pointing one operating system to another, I see so many different ways of doing this (directly to the kernel, to menu.lst, chainloading, etc.). Once again, I am not sure of the preferred way. There is an option during the install to put GRUB in the first sector of the boot partition rather than the MBR. That is how I did it on a different hard drive as follows:
 
 
Centos 5.6
/dev/sda1 /boot ext3
/dev/sda2 /, swap LVM
 
 
Scientific Linux 6.1
/dev/sda3 /boot ext4
/dev/sda7 /, /home, swap LVM
 
 
In the grub.conf of Centos 5.6 I have the following in order to load Scientific Linux. In this way I get a menu for each operating system, which allows me to select the kernel and options that I need:
 
 
title Scientific Linux on partition (hd0,2)
root (hd0,2)
chainloader +1
 
5) For more help please download and run [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) and post RESULTS.txt here.
 
This was a big help. I see from the results of this that it looks like GRUB2 did indeed get installed after all. I actually tried 3 times during the install to get it to install, and on the third attempt it no longer gave a failed message, although it still claimed that it was not installed, so magically it was installed.
 
This is a pretty big file, so I have posted it to the following:
 
[http://sharetext.org/BBGG](http://sharetext.org/BBGG)
 
 
So I tried to chainload into Ubuntu and the menu comes up and Ubuntu loads !  There were a couple of errors immediately after the menu, but I will look into that later.  My experience so far is that Red Hat / Fedora have a much more intuitive and polished installation program.

---

### Post by YesWeCan on 2011-08-31
> **pchokola said:**
> So I tried to chainload into Ubuntu and the menu comes up and Ubuntu loads !  There were a couple of errors immediately after the menu, but I will look into that later.  My experience so far is that Red Hat / Fedora have a much more intuitive and polished installation program.
Bootinfoscript is really useful. The Ubuntu installer has some, erm, shortcomings. Don't get me started. ;)

> So,
 
1) Why did this happen so I do not go through this on the next install?
Grub-2 will not work reliably when installed to a partition. This is because it uses absolute sector addressing to find one of its files that's in the /boot/grub directory and this file can change location as the result of normal file system housekeeping. Unlike Windows file systems, the ext system does not appear to make adequate provision for a fixed position boot program. Which sucks.

I know quite a bit about Grub-2. I am a lot less familiar with how Grub-1 works. I know that it does not complain if you install it to a partition and that people do this. But I do not understand how it gets around, if in fact it actually does, the absolute addressing issue. I would like to know but documentation is spartan and it is a pest trying to unravel the source code.

> 2) How do I fix it without reinstalling everything (I dread setting up all those logical volumes again).
Well, what you have got is not going to be reliable. You are chainloading Grub-2 in sdc3 from Grub-1 in the MBR.

The only "easy" way I know to make Grub-2 reliable is to install it to the MBR. You should be able to use Grub-2 in place of Grub-1 on sdc. You can do everything Grub-1 does with Grub-2 but it is a little more complicated in some ways. At least Grub-2/Ubuntu has an OS-prober tool that will automatically populate the Grub menu by scanning all your drives for OSs.

You could add instructions to boot Ubuntu directly in menu.lst rather than chain-load Grub-2.

You could remove Grub-2 from Ubuntu and install Grub-1.

> 3) Is it OK to use GRUB2, and is it possible to chainload from Centos6  into Ubuntu 10.04.3 or other  similar method (I like the option to have a  menu of kernels to pick from), and if so is there a special syntax?.
 
CONFIGURATION
My intent is to dual boot from Centos 6 into Ubuntu 10.04.3. Is my setup  correct? One thing I did not do is set the bootable flag on the  /dev/sdc3 /boot partition, but not sure that makes a difference or not.
Not sure. When you say chainload from Centos?
The boot flags are ignored by Grubs. They are only used by the original multi-boot system MBR code, which Grub wipes out.

---

### Post by oldfred on 2011-08-31
Prior to 9.10, I used to chain load my various installs of Ubuntu and a few others. But grub2 changed all that & at first I was not happy. But I find grub2 is better for new users as its os-prober finds other installs and for those who want to do thing other ways it can chain load to old grub PBRs or directly boot in many cases.

The issue may be if Centos grub  legacy has been updated to work with ext4 partitions which Ubuntu now defaults to. Ubuntu modified its version of grub 0.97 with 9.04 to work with ext4 but other distributions at that time had not. Grub legacy has not been maintained and each distribution has recently tweaked it to work for the time being. Redora is changing to grub2 with the alpha just released.

These may work from grub to boot Ubuntu if your grub works with ext4. I have not used them. Note that grub legacy counts partitions from 0 so sda1 is hd0,0, but grub2 counts from 1 so sda1 is hd0,1. Also if you have a separate /boot the root line is to the boot partition but the kernel line is to the root partition.

examples adjust to your drive - X and partitions - Y:
Grub to grub2:
title  Ubuntu on sda5
root (hd0,4)
kernel /boot/grub/core.img
boot

title    Most Current Ubuntu on sdc5
root    (hd2,4)
linux   /vmlinuz root=/dev/sdc5 ro quiet splash
initrd  /initrd.img

---

### Post by pchokola on 2011-08-31
I was reading the GRUB2 documentation today, and yes, there are a lot of changes.  
So, at least for the time being, the following is working when I add it to the Centos6 grub.conf file like I always do.  But it sounds like I better try some of the other methods mentioned here if they are indeed more reliable.
 
 
title Ubuntu Server LTS 10.04.3
     root (hd0,2)
     chainloader +1

---

### Post by YesWeCan on 2011-08-31
[http://www.pixelbeat.org/docs/disk/](http://www.pixelbeat.org/docs/disk/)
[http://www.gnu.org/software/grub/manual/legacy/Bootstrap-tricks.html#Bootstrap-tricks](http://www.gnu.org/software/grub/manual/legacy/Bootstrap-tricks.html#Bootstrap-tricks)

I've been looking for details of how Grub-1 boots. It looks like it works very similarly to Grub-2 and that installing Grub-1 in a partition should have exactly the same reliability problems. The Grub-1 PBR code has to load the stage2 file using a fixed address and Grub-2 PBR code has to load the core.img file using a fixed address.

But get this, when Grub-1 is installed to a partition of a ReiserFS or FFS (Flash file system?) it does install the stage1.5 which is used to search for stage2, thus making the boot process reliable. It appears the ReiserFS leaves a 64k gap between partition start and superblock start - excellent! Whereas ext4 leaves only 1kB - which sucks.

I don't know what grub-2 does if you try to install it to a Reiser of Flash file system partition. Perhaps it embeds core.img. I'll have to test this. If it does that would be brilliant.

---

### Post by YesWeCan on 2011-08-31
FFS!
and I don't mean Flash File System. ;)

I used Disk utility to create a 1GB Reiser partition. Had to install reiserfsprogs first. The partition is sdb11:
```
~$ sudo grub-install -v
grub-install (GRUB) 1.99~rc1-13ubuntu3
~$ sudo grub-install /dev/sdb11
/usr/sbin/grub-setup: error: /dev/sdb appears to contain a reiserfs filesystem which isn't
known to reserve space for DOS-style boot.  Installing GRUB there could result in FILESYSTEM
DESTRUCTION if valuable data is overwritten by grub-setup (--skip-fs-probe disables this check,
use at your own risk).

```
--skip-fs-probe is not recognized as a valid option #-o
--force results in the same error message :?

sdb11 has 64kiB of space before the superblock.

Grub is such a pain in the ... sometimes. ](*,)
Could be I'm doing it wrong. Could be a bug. Could be a design oversight.



Anyhow, according to the Grub-1 GNU documentation, it looks like it may be possible to set up a reliable, MBR compliant boot system if a Reiser fs is used for /boot. I won't get my hopes up until I've tested it.

---

### Post by YesWeCan on 2011-08-31
Yes yes yes :D
Come back Grub legacy, all is forgiven. It installs stages 1 and 1.5 to the PBR area of a Reiser fs as promised. Marvellous.

---

