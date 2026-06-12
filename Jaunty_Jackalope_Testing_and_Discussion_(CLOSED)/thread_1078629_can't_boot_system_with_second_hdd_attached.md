---
title: "can't boot system with second hdd attached"
date: 2009-02-23
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by LadFromWales85 on 2009-02-23
Hey all,

My system has developed an issue starting up when my storage hdd is attached.  The drive is LVM2'ed with a single filesystem across the whole drive.

After the system detects my USB card reader, there is a long delay before the screen is spammed with references to the drive (sdb).  I cannot find these logged anywhere in /var/log

```

[   20.172463] sd 6:0:0:0: [sdb] Attached SCSI removable disk                                                 
[   20.173394] sd 6:0:0:0: Attached scsi generic sg3 type 0                                                   
[   20.177331] sd 6:0:0:1: [sdc] Attached SCSI removable disk                                                 
[   20.177385] sd 6:0:0:1: Attached scsi generic sg4 type 0                                                   
[   20.181427] sd 6:0:0:2: [sdd] Attached SCSI removable disk                                                 
[   20.181488] sd 6:0:0:2: Attached scsi generic sg5 type 0                                                   
[   20.233594] sd 6:0:0:3: [sde] Attached SCSI removable disk                                                 
[   20.233655] sd 6:0:0:3: Attached scsi generic sg6 type 0                                                   
[   20.966585] type=1505 audit(1235417529.736:2): 
!!ERRORS OCCUR HERE!!
operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2745                                                                                            
[   20.966705] type=1505 audit(1235417529.736:3): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2745                                                                  
.....................

```

I was able to boot using an older 2.6.27 kernel, but since installing bootchart in an attempt to see what process was taking a lot of time, it is now also spamming messages about sdb.
Is there somewhere I am not looking for any errors being output?
As bootchart doesn't appear to create a record until it's finished, I still don't know whats causing the problem :(

As it stands I cannot get as far as the login screen with the second drive attached.

Any help much appreciated :)

---

