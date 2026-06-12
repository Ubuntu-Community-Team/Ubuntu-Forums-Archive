---
title: "Creating ext4 file system for/in partition #8..... stuck?"
date: 2011-04-03
forum: Installation &amp; Upgrades
---

### Post by Cattails on 2011-04-03
I've previously used Ubuntu. Older version, now I'm installing Ubuntu 10.10 on my other laptop. after a serious amounts of troubles, finally got there. its been 1-2 hours and it seems to be stuck at Creating ext4 file system for/in partitian #8 of SCSI1 (0,0,0) (sdb)... Now, I've looked at other posts, a few explained it might be the CD was created badly. I'm installing from a USB, but the same problem could be. 

I haven't tried Restarting, b/c at other posts I have read I should wait... Since it's worth the waiting which is true, but how long should I wait? Should I restart my laptop and re-try Installing Ubuntu? OH, and if it was indeed a corrupt or wrongly created file or something, wouldn't it show me an Error message by now? That's what it did with the previous USB. 

PS, I'm a technotard, so if you have a solution please try simplifying it to the maximum.

---

### Post by Dutch70 on 2011-04-03
IMHO, it shouldn't take that long to format, I also doubt that sdb8 would be a really huge partition.

Were you able to select "Try Ubuntu" to run test it on your system?
If not, did you check the md5sum of the downloaded .iso? 
[[COLOR="Red"]HowToMD5SUM[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM")
To check the integrity of the cd/usb?
[[COLOR="Red"]CDIntegrityCheck[/COLOR]]("https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck")

I strongly recommend unplugging your other hdd's before installing. It not only prevents some mistakes & simplifies the install, it also simplifies solving any problems you may have after you install.

---

### Post by SeijiSensei on 2011-04-03
> **Cattails said:**
> it seems to be stuck at Creating ext4 file system for/in partitian #8 of SCSI1 (0,0,0) (sdb)...

How many disk drives does this computer have?  sdb refers to the second ("b") drive on a computer with multiple drives.  Do you actually have a second drive?  Did you try installing with a USB drive connected?  If so, disconnect them all before installing as Dutch70 says.

---

