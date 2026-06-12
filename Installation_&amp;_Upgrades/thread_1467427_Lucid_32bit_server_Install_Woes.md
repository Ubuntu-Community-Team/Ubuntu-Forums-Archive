---
title: "Lucid 32bit server Install Woes"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by unicorn13 on 2010-04-30
High all,

Has anyone had this problem, during install approx 90%, the installer says that there is a media change and to insert the server cd named _LUCID_LYNX_ (2010427) into /CDROM/

ONLY 1 server disk for 32bit exists and it in the drive, would say it's not very lucid but down right confused.

Any fixes for this, BTW it won't install from 2gb cruizer flash either

TIA
Andy

---

### Post by djchandler on 2010-04-30
> **unicorn13 said:**
> High all,

Has anyone had this problem, during install approx 90%, the installer says that there is a media change and to insert the server cd named _LUCID_LYNX_ (2010427) into /CDROM/

ONLY 1 server disk for 32bit exists and it in the drive, would say it's not very lucid but down right confused.

Any fixes for this, BTW it won't install from 2gb cruizer flash either

TIA
Andy

The installer is most likely looking for a resource that isn't on the CDROM. Did you run a checksum on the iso file before burning, and then check the disk before installing?

Do you have a working internet connection for the install? I know you  said you got as far as 90%, but something isn't meshing properly.

You may want to check the [Server Platforms forum]("http://ubuntuforums.org/forumdisplay.php?f=339") to post you server specific support requests there.

---

### Post by unicorn13 on 2010-05-01
Hi djchandler,

Ran an integrity check on the disc and the checker confirmed dis is ok and valid.

Also downloaded iso's from torrent and U.S. mirror, burnt and checked both, and both stalled at same point, so if it is looking for something that is missing, then I have no clue as the screen don't list what it is wanting.

Have been reading the server sub-set but not found anything similar as yet

Thanks for reply.

A.

---

### Post by djchandler on 2010-05-01
> **unicorn13 said:**
> Hi djchandler,

Ran an integrity check on the disc and the checker confirmed dis is ok and valid.

Also downloaded iso's from torrent and U.S. mirror, burnt and checked both, and both stalled at same point, so if it is looking for something that is missing, then I have no clue as the screen don't list what it is wanting.

Have been reading the server sub-set but not found anything similar as yet

Thanks for reply.

A.
Are you trying to set up RAID? What happens if you tell it to continue? Could it be the CD-ROM drive, i.e., you're actually getting a device unavailable or not ready error? Did you try ejecting, and then placing the same CD back? If that works, there's a time-out issue with your hardware.

---

### Post by unicorn13 on 2010-05-02
> **djchandler said:**
> Are you trying to set up RAID? What happens if you tell it to continue? Could it be the CD-ROM drive, i.e., you're actually getting a device unavailable or not ready error? Did you try ejecting, and then placing the same CD back? If that works, there's a time-out issue with your hardware.

Hi,

No RAID just regular install, clicking continue, just loops the process, and ejecting/re inserting disc results in the same looping back to 'media change insert...' message.

Hardware is ok, as 8.04 LTS, Desktop versions 9.04 and 9.10 install no problems.

I'm quite :confused:

Regards
Andy

---

### Post by djchandler on 2010-05-02
> **unicorn13 said:**
> Hi,

No RAID just regular install, clicking continue, just loops the process, and ejecting/re inserting disc results in the same looping back to 'media change insert...' message.

Hardware is ok, as 8.04 LTS, Desktop versions 9.04 and 9.10 install no problems.

I'm quite :confused:

Regards
Andy

I'm confused and dismayed as well.

I just found out last night that the ISO images are being rebuilt due to at least one (maybe more) defects. I have no idea when those will be ready and damage control protocols seem to be in place. The best thing to do is check the date of the ISO image on the mirror you use for your download.

[http://www.phoronix.com/scan.php?page=news_item&px=ODE5Ng](http://www.phoronix.com/scan.php?page=news_item&px=ODE5Ng)

Sorry. I just checked the ISOs at the [fastest US mirror]("http://mirror.mcs.anl.gov/pub/ubuntu-iso/CDs-Ubuntu/10.04/"). The ISOs are still dated two days before the release date.

Can you do a version upgrade from a 8.04 or 9.10 (preferably 9.10) installation?

---

### Post by unicorn13 on 2010-05-02
> **djchandler said:**
> I'm confused and dismayed as well.

Sorry. I just checked the ISOs at the [fastest US mirror]("http://mirror.mcs.anl.gov/pub/ubuntu-iso/CDs-Ubuntu/10.04/"). The ISOs are still dated two days before the release date.

Can you do a version upgrade from a 8.04 or 9.10 (preferably 9.10) installation?

The date for Lucid on UK Mirror Service is 27-Apr-2010 so it would seem no respin yet here.

Just downloading svr 9.10, will install and try an upgrade.

First time using upgrade, I'll assume, this:-> #

Install update-manager-core if it is not already installed:   

sudo apt-get install update-manager-core 

#

edit /etc/update-manager/release-upgrades and set Prompt=normal  
#

Launch the upgrade tool:   

sudo do-release-upgrade

# Follow the on-screen instructions.  

Should that 'set prompt' be 'lts' for server?

regards
Andy

---

### Post by djchandler on 2010-05-02
It's good that someone else is looking at these CD labels/titles. Unfortunately I have no idea how to find the CD title without downloading the ISO. Here's another workaround that may work for you:

[http://ubuntuforums.org/showthread.php?t=1466406](http://ubuntuforums.org/showthread.php?t=1466406)

In answer to your question, "no" on whether that should be LTS or normal, as you are upgrading from the previous "normal" or regular release (9.10), not the LTS (8.04) release.

I hope you don't experience even more problems. This situation is evolving as fixes are being submitted for the re-spin of the ISO and others here are posting workarounds in Ubuntu Forums. A local friend of mine called me on the telephone a couple of hours ago and told me he couldn't access the upgrade repositories, that access was failing for him.

---

### Post by unicorn13 on 2010-05-02
> **djchandler said:**
> 
I hope you don't experience even more problems.

:D Thats what I thought, I must be jinxed. I had a stable install using 9.04, I'm begining to wish I had left well alone.

Got rid of 10.04 deleted partitions reset MBR, and tried server 9.10, lo and behold same problem as with 10 'media change' at the exact same point???

One thinks, reboots tidies up HDD and made good, put the 9.04 server disk the one I used when had stable install.

Fails again this time, just after the configuration messages for apt, 'red screen o death' on software selection.

Just out of curiosity, install XP, it install no probs, so the H/W seems ok.

I'm gonna take a break, and come back with a fresh head.

Andy.

---

### Post by unicorn13 on 2010-05-03
@djchandler

Hi,

Still no joy with the install disc, did some searching and found a work around for installing from flash device.

Use unetbootin windows app to make bootable flash using karmic iso, once done edit the syslinux.cfg in the root of the flash drive and changed this:

```
label ubuntuserver
menu label ^Install
kernel /install/netboot/ubuntu-installer/i386/linux
append initrd=/install/netboot/ubuntu-installer/i386/initrd.gz vga=normal -- quiet
```

To this

```
label ubuntuserver
menu label ^Install
kernel /install/vmlinuz
append initrd=/install/initrd.gz ramdisk_size=10000 cdrom-detect/try-usb=true root=/dev/rd/0 devfs=mount,dall rw
```

A modification of [this chaps posted this solution so many thanks to him]("http://bendingmcp.blogspot.com/2009/12/installing-ubuntu-910-as-home-server.html")


Thanks for all your help djchandler, greatly appreciated

Andy.

---

