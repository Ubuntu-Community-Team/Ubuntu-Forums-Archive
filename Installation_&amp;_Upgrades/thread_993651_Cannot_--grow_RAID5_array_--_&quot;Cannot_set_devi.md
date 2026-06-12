---
title: "Cannot --grow RAID5 array -- &quot;Cannot set device size/shape&quot;"
date: 2008-11-25
forum: Installation &amp; Upgrades
---

### Post by rgbtxus on 2008-11-25
I have a RAID5 array that currently is composed of 4 320GB partitions on 4 disks.  This array is one of several physical volumes in a LVM volume group. I just upgraded to Intrepid (two days ago).  And tonight installed the big update that was available today.  So this problem occurs with the latest and greatest.  I'm running out of space and so want to add a fifth disk.  I have done this on several occasions to other arrays and so did not anticipate problems -- always a mistake.

mdadm --add /dev/md21 /dev/sdi1 worked like a champ and the drive was added uneventfully as a spare to md21.  When I try mdadm --grow /dev/md21 --backup-file=/root/mdadmtmp -n 5 I get "mdadm: Cannot set device size/shape for /dev/md21: Device or resource busy" and dmesg shows "md: could not update array info. -16"

I've tried stopping nfs and samba (which share some of the files hosted on the PV), unmounting the logical volumes on the PV and setting the volume group inactive hoping that somehow LVM was the culprit.  No dice.  So I rebooted into rescue mode, drop to a root shell, unmounted and deactivated as above to no avail.

lsof /dev/md21 and /dev/sdi1 return no results.  So who might be responisble for the "busy?"  mdadm -D/-E of the relevant devices all look fine and consistent with this (sdi was removed before this, but was there)

/dev/md21:
        Version : 00.90
  Creation Time : Wed Nov 14 23:40:31 2007
     Raid Level : raid5
     Array Size : 937512768 (894.08 GiB 960.01 GB)
  Used Dev Size : 312504256 (298.03 GiB 320.00 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 21
    Persistence : Superblock is persistent

  Intent Bitmap : Internal

    Update Time : Tue Nov 25 23:20:38 2008
          State : active
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 5bf98f0f:38057634:dafc93a3:f3c76e1e
         Events : 0.9026

    Number   Major   Minor   RaidDevice State
       0       8      113        0      active sync   /dev/sdh1
       1       8       97        1      active sync   /dev/sdg1
       2       8       65        2      active sync   /dev/sde1
       3       8       81        3      active sync   /dev/sdf1

I'm getting really tight on space so could really use some help here (wiping, recreating and reload would be a major PITA since this PV is but one that support the LVs)

TIA
Dick

---

### Post by rgbtxus on 2008-11-29
bump - anyone have an idea of what is going on and how to reshape this array?

---

### Post by g.gavro on 2008-12-04
I was having the exact same problem as you. I haven't been able to find any useful insights on the net; but after fiddling around for AGES I found the solution.. I've just posted it on [>opensuse.org<]("http://forums.opensuse.org/pre-release-beta/400789-lvm-top-raid5-grow.html") as well, but seeing that you've hade the same problem I'd thought why not post it here as well.

Solution:
- remove the internal bitmap (e.g. mdadm --grow /dev/mdX -b none);
- grow the raid array (e.g. mdadm --grow /dev/mdX -n4);
- re-add the internal bitmap (e.g. mdadm --grow /dev/mdX -b internal).

---

### Post by rgbtxus on 2008-12-05
Thank you!  Like you I could not seem to find a solution.  My array is growing now thanks to your help.  I was 99+% full so this help came just in the nick of time <G>


> **g.gavro said:**
> I was having the exact same problem as you. I haven't been able to find any useful insights on the net; but after fiddling around for AGES I found the solution.. I've just posted it on [>opensuse.org<]("http://forums.opensuse.org/pre-release-beta/400789-lvm-top-raid5-grow.html") as well, but seeing that you've hade the same problem I'd thought why not post it here as well.

Solution:
- remove the internal bitmap (e.g. mdadm --grow /dev/mdX -b none);
- grow the raid array (e.g. mdadm --grow /dev/mdX -n4);
- re-add the internal bitmap (e.g. mdadm --grow /dev/mdX -b internal).

---

### Post by lucisandor on 2009-07-22
Hi all,
I am going through the of resizing a RAID5 and I was lucky to stumble on this thread, which fixed my problem for the time being.
I have one newbie question: what happens if, at the end of growing phase, one does not write the internal bitmap? Is this a required step, and is the internal bitmap a requirement?
Thanks.

---

### Post by lucisandor on 2009-08-26
Hi all,
I think I got the answers to my questions.
The bitmap is needed to ensure fast recovery after a crash. If you can live with hours of reconstructions upon boot after each system failure, you can think of the bitmap as optional.
As such, you can skip the step of re-adding the bitmap if you have a good reason for it; and you can add it later, if you forgot to add it in the first place.

---

### Post by samjbobb on 2010-04-05
Thanks for the tip. As usual, following some instructions, got an error, googled it, found the solution on ubuntu forums. Growing now, finish=800.1m. Guess it's time for bed.

---

### Post by Underpants on 2011-01-09
> **g.gavro said:**
> 
Solution:
- remove the internal bitmap (e.g. mdadm --grow /dev/mdX -b none);
- grow the raid array (e.g. mdadm --grow /dev/mdX -n4);
- re-add the internal bitmap (e.g. mdadm --grow /dev/mdX -b internal).

What exactly is going on here? I am testing out Ubuntu 10.10 and using the Disk Utility GUI and I am not able to grow a raid5 array. It gives the error the OP described. I can go CLI, enter this, and it seems to work, but I'd like to submit a ticket for the developers to get the GUI fixed..

---

