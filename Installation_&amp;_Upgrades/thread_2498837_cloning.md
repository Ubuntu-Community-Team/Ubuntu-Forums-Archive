---
title: "cloning"
date: 2024-06-30
forum: Installation &amp; Upgrades
---

### Post by zanetto on 2024-06-30
I need to clone a ssd to another ssd with dualboot system
    I need to divide the process of cloning because the ssd is big that is to say i need to pause and resume the process
    How can I do?
    Or I ask if it is possible to clone partitions one at a time
which program may I use?

    Thank You
    Roberto

---

### Post by TheFu on 2024-06-30
You can clone partitions 1 at a time using **any** program that doesn't molest the bytes along the way.  A few are:
**dd, ddresue, gddrescue, cp, less, more, cat,**  ... literally any program that knows how to move bytes from A ---> B.

There are some caveats, but you didn't ask about those.

I'd use ddresue.  In the old days, fsarchive was the tool, but I've read that it hasn't maintained support for all the likely file systems, so any special capabilities it had can easily be handled by ddrescue now.

For example, I use **cp** to create bootable installation USB flash drives. It is all in the selection of the source and target filenames.
```
$ sudo cp /some/path/to/ubuntu-22.04.iso   /dev/sdz
```
That's an example for putting an ISO onto a flash drive.  If you want copy partitions, then the source would be a partition device and the target would be a partition device that is the same size or LARGER than the source.  Even a few bytes matters.

You'll still need to manually fix any mount settings, probably need to change the UUIDs manually for the partitions and disks, and you'll need to handle any boot differences (single boot is different from dual, tri-, quad-booting).

Lots of other assumptions will likely come up and need fixing too.

OTOH, you could use this as an opportunity to test your backup restore process.  If that isn't working, you can use this opportunity to get it working.   Usually takes about 5 attempts to get a restore process working the first time. There are lots of chicken-egg issues that will become clear.  **For any computer with under 100G of stuff, if the restore process takes longer than 45 minutes, you are doing it wrong.**  

It is also possible to make a backup-restore process that doesn't care about duel boot or file systems or hardware stuff too much. That is how mine work. I can completely swap the storage layout on the new computer and still have "my system" back in less than 45 minutes.

---

### Post by zanetto on 2024-06-30
I ask for an adivse to use a program like clonezilla or something else not commands

---

### Post by oldfred on 2024-06-30
Are you planning on keeping both drives connected.
You cannot have duplicate UUIDs & GUIDs.
You cannot clone from MBR to gpt or vice-versa. 
And with gpt difficult to clone one partition as gpt has unique GUIDs in primary partition table, backup partition table & partition. Those must all be in sync and cloning a partition then gets them out of sync.

If planning on keeping drive, much better to do new install & restore from backup as TheFu suggests.

---

### Post by morovan on 2024-06-30
> **zanetto said:**
> I ask for an adivse to use a program like clonezilla or something else not commands

Sorry for nitpicking, but I do it with hope it will help you to get (quicker) answer you're looking for in the future:

dd, ddresue, gddrescue, cp, less, more and cat _are all programs_. We use commands to launch those programs and sometimes also pass arguments to those programs.

The word your looking for is **GUI** (graphical user interface) application/program

---

### Post by TheFu on 2024-06-30
I don't think clonezilla can do what you seek.  Plus, I find it 100x more complicated than typing 1 ddrescue command that will "just work".
But we are different people and our ideas of "simple" are different.

You could check out **gparted** for copying partitions, but that seems like overkill.  It is a GUI and very useful for most tasks related to partitioning disks. It isn't a 1-trick-pony.

Regardless, you'll still need to boot from alternate media like a USB Flash drive with an Ubuntu ISO on it to get a good clone of any partition.  Cloning partitions requires that the partitioned being cloned NOT be active, not used, not mounted.

---

### Post by 909mjolnir on 2024-07-01
I think clonezilla will work for just one partition at a time if you want it to.  I just used it a few days ago.  
Unfortunately, my session of clonezilla failed for reasons that I still don't understand.  
So I'm not sure if I should recommend that route to you.  

I tried to just clone my entire hard drive to a USB flash drive larger than my system drive.  
But it failed early on.  wierd.  

Good luck with yours, though.

---

