---
title: "Unable to mount DVD-RAM disc"
date: 2007-02-04
forum: Installation &amp; Upgrades
---

### Post by lepus on 2007-02-04
I have just replaced a CD-ROM drive with a Samsung SH-S182D DVD rewriter. I can read and write CD's. I can read DVD's, I havn't tried writting one as I currently don't have any blank DVD's. My problem is that I can't mount a DVD-RAM disc. The one I'm trying to mount will mount OK on another PC with Ubuntu on it. When I do a mount I get the error message 
"mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so"

Doing a dmesg | tail gave me 
"cdrom: hdc: mrw address space DMA selected
cdrom open: mrw_status 'not mrw'
Unable to identify CD-ROM format."

/etc/fstab has the line "/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0" in it.

Is there something else I have to do to get Ubuntu to use DVD-RAM, or is there a problem with the drive itself?

---

### Post by dcstar on 2007-02-04
> **lepus said:**
> I have just replaced a CD-ROM drive with a Samsung SH-S182D DVD rewriter. I can read and write CD's. I can read DVD's, I havn't tried writting one as I currently don't have any blank DVD's. My problem is that I can't mount a DVD-RAM disc. The one I'm trying to mount will mount OK on another PC with Ubuntu on it. When I do a mount I get the error message 
"mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so"

Doing a dmesg | tail gave me 
"cdrom: hdc: mrw address space DMA selected
cdrom open: mrw_status 'not mrw'
Unable to identify CD-ROM format."

/etc/fstab has the line "/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0" in it.

Is there something else I have to do to get Ubuntu to use DVD-RAM, or is there a problem with the drive itself?

You may want to experiment with hdparm to turn DMA off and on for that drive, and see if things change.

You may also want to check your BIOS for the settings for that IDE channel, as well as the jumpers on the back of the actual drive to make sure they match your hardware.

---

### Post by lepus on 2007-02-06
I tried disabling and enabling DMA (hparm -d0 /dev/hdc and  hparm -d1 /dev/hdc) but it made no difference. The jumper on the drive is set to MASTER as recommended in the install instructions for a single drive on a cable, and I can't see any reference to any other switch/setting. What should I be looking for in the BIOS channel settings? 

However, I have had a partial breakthrough. There's a german guy who had a simular problem and he got around it by doing a mount -t udf /dev/hdc /media/cdrom0 -o rw, this gives the error mesage "mount -t udf /dev/hdc /media/cdrom0 -o rw", but if you then do a 
mount -t udf /dev/hdc /media/cdrom0 -o remount command, it works. I can now write to the disc.

Does this give you any more clues? It works but I have to su to root to do anything, which I would rather avoid. Is there any way of "cleaning this up"?

Thanks for your help.

---

### Post by lepus on 2007-02-06
Futher info. I have tried the SH-S182D on my other Ubuntu system, with the same result. So both PCs work happily with an older LG DVD rewriter, but not the Samsung. Both BIOSes are about 1999 vintage. 

I have also discovered that I can sudo mount (using the 2 mount commands mentioned earlier) and unmount from my adminstration logon and then write to the RAM disc as the adminstration logon. So it's not quite as bad as I thought. However, I would still like it to work as normal if possible. ie, automatically mount and be able to do an eject from the RAM disc's icons menu.

---

