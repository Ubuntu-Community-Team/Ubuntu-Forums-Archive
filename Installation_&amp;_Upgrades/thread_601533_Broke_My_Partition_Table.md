---
title: "Broke My Partition Table"
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by aaaantoine on 2007-11-03
I decided I was going to mess around with my partitions to make more room for Ubuntu and take space away from Windows.

My partition table looked something like this:

```

|    |    /win/c              |  /win/d |[| /        | /home     | |]
  ^ factory settings partition                                    ^ swap
[] = extended partition   

```

For reasons I can only attribute to lack of sleep, I decided to use Windows XP's disk manager to remove /win/d.  Restarted.  Grub error 15.

I loaded the Live CD, which shows the contents of the drive (/dev/sda) as 111.79 GiB of unallocated space.  This scared the crap out of me.

I popped in a Windows XP install CD to see if I could repair the Windows installation.  It did find XP on the drive, so I opted to Repair in the hopes that it would change the boot sector.  Nope.

I loaded the Live CD again since I had a glimmer of hope now.  I ran fdisk -l /dev/sda and it showed me the remaining partitions of the drive.  According to fdisk, removing /win/d also wiped out /.  Okay, so I'll just try to reinstall Ubuntu...  The only problem is, I'm not comfortable with using fdisk at all.  Agitated by all this, I shut down and went to sleep.

This morning, I woke up and loaded the LiveCD again.  Now fdisk -l /dev/sda tells me "Cannot open /dev/sda".  Crap.  BUT!  If I go to Places -> Computer, all the unaffected partitions show up there, fully accessible (except for /win/d and /, as indicated above).

So my question is, how can I reinstall Ubuntu using the unallocated space and fix the partition table without wiping the drive?  All help on this matter is greatly appreciated.

Due to the urgency of this issue, I plan to hang out in #ubuntu all day.  If a solution is reached there, I will update this thread.

---

### Post by leonidas666 on 2007-11-03
I understand that you don't like fdisk, i also don't like it... Anyway, did you try fixing things with gparted? gparted has a nice gui, and it should be no problem creating a new partition at the place where your /-partition was before. 
And to fix the grub-Error: Did you try reinstalling Grub? Unfortunately there's no gui for this, but there are some instructions here in the forum. 
By the way: If you can still access some partitions after booting from the liveCD, i think it is a good time to make some backups...:)

---

### Post by Pumalite on 2007-11-03
And Super Grub to see if you can boot something, or repair MBR, etc, etc:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
(or reinstall Grub)

---

### Post by aaaantoine on 2007-11-03
> **leonidas666 said:**
> 
By the way: If you can still access some partitions after booting from the liveCD, i think it is a good time to make some backups...:)

Yeah.  I'm doing this now, actually.

I've decided that I"m just gonna forget dual boot (since A: I have Windows loaded into VirtualBox, and B: I can't really game on the laptop), backup all my documents from both Windows and Ubuntu, and just install Ubuntu across the drive.  This is what I was inching towards, anyway. :)

I'll let you know how it goes.

---

### Post by Pumalite on 2007-11-03
Good move.

---

### Post by aaaantoine on 2007-11-04
I find it strange that neither fdisk nor gparted recognized the partition layout, but the LiveCD still managed to load the various partitions.  It strikes me as a bug... in something...

Anyway, all went well.  I just had trouble copying up my VirtualBox VDI because it was over 4GB in size.  The solution was to zip it and *then* copy it to the backup drive.

---

