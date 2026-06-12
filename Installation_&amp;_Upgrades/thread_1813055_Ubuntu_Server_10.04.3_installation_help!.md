---
title: "Ubuntu Server 10.04.3 installation help!"
date: 2011-07-27
forum: Installation &amp; Upgrades
---

### Post by bootzenkats on 2011-07-27
I'm attempting to install Ubuntu Server 10.04.3 from CD and I can't finish the installation. The installation will scan the CD-ROM, let me name it, configure the clock, partition the discs (LVM encrypted), set up a passcode, and install the base system. But, when this is finished, it asks, "Please insert the disc labeled: 'Ubuntu-Server 10.04.3 LTS _Lucid Lynx_ - Release amd64 (20110719.2)' in the drive '/cdrom/' and press enter." This disc is already in the drive and I am unable to continue the installation!! 

Has anyone had this problem or can think of a solution? I've tried going through the installation of Ubuntu Server 11.04 and gotten the same result.

---

### Post by bootzenkats on 2011-07-27
Preez? :3

---

### Post by varunendra on 2011-07-29
> **bootzenkats said:**
> I'm attempting to install Ubuntu Server 10.04.3 from CD and I can't finish the installation. The installation will scan the CD-ROM, let me name it, configure the clock, partition the discs (LVM encrypted), set up a passcode, and install the base system. But, when this is finished, it asks, "Please insert the disc labeled: **'Ubuntu-Server 10.04.3 LTS _Lucid Lynx_ - Release amd64 (20110719.2)'** in the drive '/cdrom/' and press enter." This disc is already in the drive and I am unable to continue the installation!! 

Has anyone had this problem or can think of a solution? I've tried going through the installation of Ubuntu Server 11.04 and gotten the same result.
Have you tried 32 bit? I have installed it in a VM months ago and it went without problems. I also tried 10.04.3 after reading your post (can't try 64-bit in a VM) and it went smooth too.

And BTW, the label it is asking for is invalid I think. The original label, as it appears after mounting, is- "**Ubuntu-Server 10.04.3 LTS amd64**". Maybe it is a bug/mistake while compiling the setup (on the developers' part). If so, maybe it would have been fixed in the latest release, or maybe the same CD could work if its label could be somehow changed to match the requested one. Which source did you download it from?
Mine was through torrent from [http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download)
Direct link to the torrent: [http://releases.ubuntu.com/10.04.3/ubuntu-10.04.3-server-amd64.iso.torrent](http://releases.ubuntu.com/10.04.3/ubuntu-10.04.3-server-amd64.iso.torrent)



[B]
_EDIT_:[/B]
Apparently, you can change the volume label using ISOMaster (it's in the repositories). But iso compatibility restrictions won't allow such a long name (Ubuntu-Server 10.04.3 LTS _Lucid Lynx_ - Release amd64 (20110719.2))as volume label.

But then again, I also think that the disk info (in Ubuntu/linux) is read from this file: **.disk/info** located in the root of the cd, which can be changed using ISOMaster. This file contains the same name (label) as asked, with the only difference being double-quotes (") replaced by underscore (_) in the requested label. So you may give it a try changing that text in the file as requested.

---

### Post by koles.pl on 2011-08-01
Hi,

Similar problem with x86 on my rig.
I am using 388104f6225ae676ceab0ba4bd7b5784 *ubuntu-10.04.3-server-i386.iso (704 217 088 bytes)

Athlon XP1700+
ASrock K7S41GX MoBo (SIS 741GX chipset)
768 MB RAM
Addon PCI SiI 3114 4xSATA controller
Attempting to install on an old PATA drive.
1 SATA 1.5 TB drive as storage

After partitioning, base system install proceeds until a message is shown:

*Please insert the disc labeled: 'Ubuntu-Server 10.04.3 LTS _Lucid Lynx_ - Release i386 (20110719.2)' in the drive '/cdrom/' and press enter.*

Are these ISOs OK? Maybe some driver is missing? Just a wild guess since it works for some people.

Cheers,
Michael

---

### Post by CharlesA on 2011-08-01
Try a different cdrom drive. I've see that happen where the cd drive doesn't want to read the disc correctly.

---

### Post by sam1948 on 2011-08-01
hi,
have you tried using usb?
```
sudo apt-get install usb-creator-common usb-creator-gtk usb-creator-kde
```

or take the disks to some other computer and check-sum-md5 them

---

### Post by koles.pl on 2011-08-01
Hi,

Thanks for prompt responses.

I already tried ISOMaster trick mentioned above - changed label in **.disk/info** file and the actual label to 'SERVER10' (<8 chars, all caps - as in good old times) but still got the installer asking for a disk labeled 'SERVER10'. Sigh.

The CD-Drive is the newest iin the rig actually, because it is only borrowed from my main PC for this server installation. It's an Optiarc (SONY/NEC) DVD RW with which I never had problems with booting any CD nor DVD (including RW media). I currently don't have a different drive to try.

I am now preparig an USB install to try. Will post an update if this works.

Cheers,
Michael

---

### Post by koles.pl on 2011-08-02
Hi,
I succeeded with USB install.
Cheers,
Michael

---

### Post by MAFoElffen on 2011-08-02
> **koles.pl said:**
> Hi,

Thanks for prompt responses.

I already tried ISOMaster trick mentioned above - changed label in **.disk/info** file and the actual label to 'SERVER10' (<8 chars, all caps - as in good old times) but still got the installer asking for a disk labeled 'SERVER10'. Sigh.

The CD-Drive is the newest iin the rig actually, because it is only borrowed from my main PC for this server installation. It's an Optiarc (SONY/NEC) DVD RW with which I never had problems with booting any CD nor DVD (including RW media). I currently don't have a different drive to try.

I am now preparig an USB install to try. Will post an update if this works.

Cheers,
MichaelWhy the USB would work... and why a lot of CD drive to CD drive disk failures occur... Is because of slight differences in drives.  USB install gets around this.  I do computer recycling and we test CD/DVD by burning from a new drive and trying to boot from the test drives.  You'ld be surprized how many fail from that!

Try to burn from the same drive you are installing to.  If not -or- even if another... Burn the ISO from the slowest speed possible.

---

### Post by neilneil2000 on 2011-08-07
Will there be a fix for this or is this just how it is? I've installed ubuntu countless times and never hit this problem until today. Note this is a freshly downloaded ISO.

It's very frustrating, even burning the iso on different machines.

I tried the USB install which worked but meant I had to leave the USB key in to boot the pc - not sure what I did wrong there! Any ideas on that one?

---

### Post by varunendra on 2011-08-07
> **neilneil2000 said:**
> Will there be a fix for this or is this just how it is? I've installed ubuntu countless times and never hit this problem until today. Note this is a freshly downloaded ISO.

It's very frustrating, even burning the iso on different machines.

I tried the USB install which worked but meant I had to leave the USB key in to boot the pc - not sure what I did wrong there! Any ideas on that one?
Grub must have been installed on the USB whereas it should have been installed on the internal hard drive. Not a big deal though, here's an easy fix -
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

I think you shouldn't need to use a live CD and the commands in the first method on the above linked page should work the same way from your installed version. Just be cautious with the selection of the drive/partition. Please post back in case you find problems.

---

### Post by MAFoElffen on 2011-08-07
> **neilneil2000 said:**
> Will there be a fix for this or is this just how it is? I've installed ubuntu countless times and never hit this problem until today. Note this is a freshly downloaded ISO.

It's very frustrating, even burning the iso on different machines.

I tried the USB install which worked but meant I had to leave the USB key in to boot the pc - not sure what I did wrong there! Any ideas on that one?
Acrually--
Where you all are looking for the disk name is not where I find it when I modifiy Install disks and LiveCD's.  If you open the ISO image with the Archive Manager and look in the root (/), you'll find a file called "README.diskdefines".  Look at it via highlight > right-click > open with > gedit... If you edit it, it would have to be via extract file > edit file > add/re[lace into archive... Doing this may change the checksum of the iso image.

Anyways, that is the file that contains the disk name or disk "image name" that the install script looks at.  It is in the first line of that file.  Example:
```

#define DISKNAME  [COLOR=Teal]Ubuntu-Server 10.10 "Maverick Meerkat" - Release amd64[/COLOR]
#define TYPE  binary
#define TYPEbinary  1
#define ARCH  amd64
#define ARCHamd64  1
#define DISKNUM  1
#define DISKNUM1  1
#define TOTALNUM  0
#define TOTALNUM0  1

```Is that a current image?  And why not a current version?  The Server Edition have a lot less idiocentricities than the Desktop Editions.   No Xserver or GUI to content with... well VGA graphics and the new aubergine theming...  But more forgiving about running on various hardware.

I've installed and set up 4 new server on 11.04 in the past 2 days with now troubles... and testing 2 server on 11.10 alpha3.  Really stable on all.  All versions 10.10 through 11.10 Server install ISO's that I downloaded last night where working for me.

---

### Post by SheaMan on 2011-11-15
I got this problem trying to install, so I decided to download a different version ( 10.04.3 desktop ) just to see what would happen and the system did not accept that in place of whatever it is asking for ..so.. I installed the desktop version instead.

---

