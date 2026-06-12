---
title: "Won't boot without CD"
date: 2006-11-13
forum: Installation &amp; Upgrades
---

### Post by helpdeskdan on 2006-11-13
On boot, I get the following message.  (Would post exact message, but it's not in dmesg & don't know another place to look)

sd 0:0:6:0 Attached SCSI disk sdb
  Attached SCSI disk sdb
  No volume groups found
Done.

Right before "No volume groups found" the CD starts spinning.  If there is a disk in the drive, it will boot up.  If there is NOT a disk in the drive, it will hang and never get to "No volume groups found."  I'm not a linux guru - have no idea where to start.  ](*,)  

Any help would be much appreciated!

Thanks, 
-Dan

---

### Post by helpdeskdan on 2006-11-15
Perhaps I should post this as a bug?  Any suggestions?

---

### Post by helpdeskdan on 2006-11-15
sdb is the drive Linux is on - why does it want to access the CDROM at this point?  Exactly what is a volume group?  Any help much appreciated, thanks!

---

