---
title: "Did 6.06 on hda kill my 5.10 data on hdb?"
date: 2006-06-06
forum: Installation &amp; Upgrades
---

### Post by John Smith on 2006-06-06
Shame on me for being so trusting . . . 


What I had: 

i586
/dev/hda:  ide hd with Debian stable, with grub/mbr from Ubuntu 5.10 later standard install on /dev/hdb.
/dev/hdb:  ide hd with Ubuntu 5.10 system, standard install, apparently did LVM setup automatically. 
/dev/hdc: 2 stand alone vfat formatted partitions for miscellaneous storage.
/dev/hdd: ide cd/rw.

it was a dual boot debian and Ubuntu setup. grub installed by Ubuntu 5.10 automatically detected and set up grub to dual boot, and worked fine.  


What I did:

downlaoded downloaded Ubuntu 6.06 LTS, burned iso. Had already backed up all Debian (/dev/hda) data. Did not back up Ubuntu 5.10 data (/dev/hdc) . (Trusting, aren't we?) 

Installed Ubuntu 6.06 to /dev/hda, overwriting Debian as expected, using graphical installer and default automatic partioning.  Then the fun begins.  

Reboot.  Ubuntu Grub pops up, automatically booting directly into Ubuntu 6.06, without offering Ubuntu 5.10 as an option.  This was unexpected, as Ubuntu 5.10 had automatically detected Debian  and set that and itself up for dual boot.  Silly me for thinking 6.06 would be as advanced.  

The 2 partitions on /dev/hdc were readable, as was /dev/hda, the new Ubuntu 6.06 system.  /dev/hdb1, apparently the Ubuntu 5.10 root (or possibly boot) partition is readable, but /dev/hdb5 (possibly an LVM glob of the rest of the 5.10 system) is not readable, nor mountable.  cfdisk just scratches its head, saying there are NO partitions on /dev/hdb.  

The Ubuntu install disk main menu has an option to "boot from first hard disk."  So I re-cabled and jumpered /dev/hdb to be detected by the cmos as /dev/hda.  But the "boot from first hard disk" install disk option would not work, stalling after a  "ERR M" error message.  

Due to an undetermined hardware issue, I could not get the cmos to recognize all of the drives when trying to re-cable and jumper them into the original configuration. So I physically disconnected the drive at /dev/hdc, then re-connected the drive at /dev/hdb as /dev/hdc.  

What I have now:
i586
/dev/hda:  ide hd with Ubuntu 6.06 LTS occupying full disk, standard install.  
/dev/hdb:  no drives physically present. 
/dev/hdc:  was /dev/hdb, (hopefully) still has the Ubuntu 5.10 system, including my data.  Appaerntly 2 partions: /dev/hdc1, with the root (or boot) partition files.  Also /dev/hdc5, possibly an LVM clump of the rest of the Ubuntu 5.10 system, and hopefully where all of my data is.  
/dev/hdd:  ide cd/rw drive. 


What I (desperately) need:  
To retrieve my data from /dev/hdc, the Ubuntu 5.10 system, and move it to /dev/hda. the Ubuntu 6.06 system.   That's all I ever wanted!  

Just a side note: is there a way to install Ubuntu without LVM, so that you have real partitions that you can see/read/write/manipulate, like in the good old days?  

Any assistance would be appreciated, even if it's just to tell me the data is lost forever, so at least I can get on with the grieving process, and then try to get on with my life.  

Thanks!

---

