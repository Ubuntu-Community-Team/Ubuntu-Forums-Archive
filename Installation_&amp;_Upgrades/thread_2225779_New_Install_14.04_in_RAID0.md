---
title: "New Install 14.04 in RAID0"
date: 2014-05-23
forum: Installation &amp; Upgrades
---

### Post by nuns-m on 2014-05-23
Hello everyone,

i would like make a new install with ubuntu 14.04 in RAID0, but I can't find how do it.
the last time i made an install with the CD ubuntu 12.2 Alternative there an option for parted the disque in Raid.

but I d'ont found the version in alternative 14.04.


I'm very sorry for my bad English.

Could you help me please.

thank you so much 
Best regards

---

### Post by nuns-m on 2014-05-23
Someone can help me? how can I install 14.04 in Raid0 software.

---

### Post by oldfred on 2014-05-23
Please only bump once per 24 hrs. Not everyone is on line at any given time that may know about your question.
I do not use RAID.

       Do not use gparted on RAID.
[http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid](http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid)
Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

They did away with the alternative installer that users used for LVM, encrypted LVM and RAID in 12.04. There was discussion of adding that to the desktop installer and now LVM is included. But not RAID.
You may need to use server installer then add the desktop of your choice. Underlying software/kernal is the same.

      
 Elimination of Alternative installer for 12.10 and no RAID support directly for Desktop.
[http://ubuntuforums.org/showthread.php?t=2049021](http://ubuntuforums.org/showthread.php?t=2049021)

---

