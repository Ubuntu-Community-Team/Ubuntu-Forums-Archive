---
title: "Dell Precision 450 Ubuntu 7.10 Dual Boot XP SP2"
date: 2007-11-26
forum: Installation &amp; Upgrades
---

### Post by fatbuttlarry on 2007-11-26
**FIXED**

Bazaar to say the least.  I called a fellow associate and he showed me how to "turn on" the new drive in the bios.  The drive listed as "OFF" in bios, so made it unbootable.  He turned it to auto.  Stupid mistake on my part. I attempted this upon installation, but I couldn't figure out how to change it.  He was more familiar with the navigation of the Dell BIOS.

Worth noting, I still couldn't get the boot.ini method to work.  I had to revert to the original GRUB method. Cheers.

Here's my grub.conf:
```

# Added by Tres Finocchiaro to boot XP
title 		Microsoft Windows XP Professional
map (hd0) (hd1)
map (hd1) (hd0)
root 		(hd1,1)
makeactive
chainloader +1
```

Linux drive is master, windows is slave.  Not sure why we root hd1 if we mapped it to hd0, but it works, and now I have both OSs independent of each other.

-Tres
[COLOR="Gray"]
------------------------------------------------------------------------------------------------

I cannot dual boot two separate hard drives in my Dell Precision 450.

I have a Dell Precision 450 with two 80 GB Western Digital drives.  Both drives have OSs installed.  Both function independent of each other.

The BIOS will not let me change the boot order of specific hard drives, and the second drive (in Cable Select Mode, or in Master/Slave Mode) does not list properly in BIOS, although functional from the OS level.

**FIRST EFFORTS: (using grub)**

I followed the GRUB tutorial for getting XP to boot from the linux boot loader.

```

sudo fdisk -lu
root (hdx,x)
#rootnoverify(hdx,x)
makeactive
chainloader +1

```

Note, in my case hdx, x was 1, 1.  Second drive, second partition.  I **did** try all other possibilities with no luck.

**SECOND EFFORTS: (using boot.ini)**

Following [this tutorial](http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/), I used the command:
```

dd if=/dev/hda2 of=/home/tfino/Desktop/ubuntu.bin bs=512 count=1
cp ~/Desktop/ubuntu.bin /mnt/(windows drive)
vi /mnt/(windows drive)/boot.ini
# append: c:\ubuntu.bin "Ubuntu Linux 7.10"

```

With multiple variations of course.  Luckilly, Ubuntu 7.10 can now write to NTFS, so the steps were minimal.

No success, so I downloaded bootpart.exe for Windows (neat app!), and used it's command line interface to build a ubuntu.bin or ubuntu.lnx boot image for the exact same purpose.  This utility appends the boot.ini entry for you.  No luck.

So after reading [this post](http://forum.winimage.com/viewtopic.php?t=1997), I created a boot image for each partition, with no luck.

**THIRD EFFORT:**
My guess is that DELL has the first drive listing as the only drive by design, to tie in with the XP recovery utilities.  This isn't to say a new BIOS won't remedy this, but the release notes for the 450 bios update don't state anything about drive issues.

> 
**From [dell.com]("http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R108007&SystemID=WRK_PNT_P4_450&servicetag=&os=WW1&osl=en&deviceid=258&devlib=0&typecnt=0&vercnt=4&catid=-1&impid=-1&formatcnt=3&libid=1&fileid=140577")**
* Add test for a bad CPU cache during normal boots.
* Fixed possible issue with the auto-power-on WEEKDAYS function of SETUP.
* Fix failure of some security and PCMCIA adapter cards to properly install
and run under Windows.
* Improve hotkey handling in setup.
* Fix misreporting of multiple bit errors when only a single bit error occurred.
* Bring microcode updates for all supported processors up to current versions.
* Improve the internal error-handling of the flash program.


I'm fairly confident that reinstalling Ubuntu with the Windows drive as primary will work.  Unfortunately, this is undesired, because it will cause the Windows drive to rely on GRUB, and the Linux drive to be unbootable if the Windows drive fails.

My third and final effort (aside from upgrading my system bios) is using the [Ultimate Boot CD]("http://www.ultimatebootcd.com/") to choose the correct drive during boot.  I'll post my success.

*Note:  No luck with ultimateboot cd!!!

-Tres[/COLOR]

---

