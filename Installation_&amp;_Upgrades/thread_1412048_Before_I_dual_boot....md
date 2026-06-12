---
title: "Before I dual boot..."
date: 2010-02-20
forum: Installation &amp; Upgrades
---

### Post by wbest on 2010-02-20
I'm planning on dual booting my netbook with Windows 7 and UNR.
However, given that I don't have a DVD drive to back up my system I was wondering if the "Backup Partition" on my harddrive (which as far as I know, was pre-installed) is the same as these disks.
Now another problem lies in what happens if all goes south.  Do I lose all three partitions? (Ubuntu, Windows, Backup).

I suppose that wouldn't be end of the world.  I still have another (main) computer running Vista.  Still...

Anyway.  Is this safe enough?  I've dual booted my Vista before and while the main job went withou major incident...I do have a bad history of screwing up one or both partitions.

Also, will GRUB still work okay with Windows 7?  I'd hate to install UNR and then have the boot loader not let me into one (or both OSes).

Sorry this is so long...just a little nervous I guess.  Without the recovery disks I don't really have a safety net.  I do have an external, but it already has stuff on it (my Mac HDD finally gave out, and the ext is a mirror of the HDD as death, which is stuff I do not want to lose).  So as a last question (in case you know the answer) will backing up NetBook's HDD using the Windows Backup create a new folder of backup in the external, or use the entire external?

---

### Post by crlang13 on 2010-02-20
The point of the backup is to backup the files off your computer.  It's not likely, but it's possible for something to go wrong and have you lose everything.  You could just backup onto a USB, or, if your backup is less than 2 GB you can store it online for free on ubuntu one.

---

### Post by wbest on 2010-02-20
Well, I'm not as concerned about the files as I am the Windows OS.  Not sure how I'd get that back if the partition got corrupted.

---

### Post by darkod on 2010-02-20
Win7 Backup&Restore tool should be able to save the image file on your ext hdd. It doesn't need to wipe your hdd.
First you should check how many partitions you have right now, not just visible ones in Computer. Open Disk Management and check. Lately lot of laptops seem to come already with 4 partitions and you can't have a 5th one which makes you choose which one to delete.
If you're not suffering from that sindrome, and after doing the backup, use Disk Management to shrink the win7 system partition for as much as you want. Leave the space as unallocated. DEFINITELY DO NOT create ntfs partition out of it. Reboot win7 few times to figure out the shrink and do the disk check.
After win7 is happy again, boot with UNR usb stick and in step 4 tell the installer to Use Largest Available free space (the one you left unallocated). Job done. :)

I'm dual booting Win7 Ult 32bit and Karmic Desktop (not UNR) 32bit on Samsung NC10 and no issues at all with grub2 and win7. Also dual booting Win7 Ult 64bit and Karmic Desktop 64bit on my desktop.

One final note, if you keep your restore partition don't be surprised if you see something like
Windows 7
Windows Vista

in your grub menu. The restore partition also has boot files which can be detected by grub2 and vista and 7 have almost identical boot files, so it's not rare a win7 restore partition to be mistaken for vista. I don't advise to start that entry in grub menu (unless you need to) because I'm not sure if you can reverse the process of those restore partitions and what will it do before it gives you chance to reverse it. For example, deleting grub off the MBR.

---

### Post by Mark Phelps on 2010-02-21
> **wbest said:**
> I'm planning on dual booting my netbook with Windows 7 and UNR.
However, given that I don't have a DVD drive to back up my system I was wondering if the "Backup Partition" on my harddrive (which as far as I know, was pre-installed) is the same as these disks.

To answer this specific question -- NO.  The backup partition most probably contains a custom OEM image of Win7 -- which can be used to restore your machine to factory conditions.  It will most probably wipe everything on your drive in the process.  So, it's not a backup utility; it's a restore utility.

---

### Post by wbest on 2010-02-21
Yeah, I got a chance to look at my partitions, and it looks like a I have 4 right now.
SYSTEM ~200MB
C: ~137GB
RECOVERY ~12GB
HPTOOLS ~100MB

So I'm guessing SYSTEM and C: I can't lose.  But what of RECOVERY and HPTOOLS?
I may want recovery to save my system.  But I don't know what HPTOOLS is.  
I've read that it relates to recover.  Looking at in MyComputer it seems to have only one folder 'SystemDiags'

I pretty much need Ubuntu on this netbook.  so I need to now how much in danger I'll be putting my Windows Partition.  Again, I can back up all the data and so forth with little problem.  But getting the OS back is going to be difficult without the right recovery stuff.

If I can't have 5 partitions, I need to delete one, and it needs to be the least important.

---

### Post by darkod on 2010-02-21
> **wbest said:**
> Yeah, I got a chance to look at my partitions, and it looks like a I have 4 right now.
SYSTEM ~200MB
C: ~137GB
RECOVERY ~12GB
HPTOOLS ~100MB

So I'm guessing SYSTEM and C: I can't lose.  But what of RECOVERY and HPTOOLS?
I may want recovery to save my system.  But I don't know what HPTOOLS is.  
I've read that it relates to recover.  Looking at in MyComputer it seems to have only one folder 'SystemDiags'

I pretty much need Ubuntu on this netbook.  so I need to now how much in danger I'll be putting my Windows Partition.  Again, I can back up all the data and so forth with little problem.  But getting the OS back is going to be difficult without the right recovery stuff.

If I can't have 5 partitions, I need to delete one, and it needs to be the least important.

My personal opinion, you don't need both HP Tools and Recovery. Also, as mentioned in threads here, HP Support is usually very helpful if you explain the situation and they might advise you what to do. After all, you paid for their product.
I remember a case where the person spoke to them and it was actually them who advised him to create a set of recovery DVDs from that partition (there must be a procedure in the manual) and delete it. He also deleted the HP Tools and was happy after that.
On the other hand, some people are simply afraid to do that.

Another reason I don't like those recovery partition is as Mark said, it will probably wipe everything including your windows system partition and any ntfs data partition that you might have, not only ubuntu. IMHO that's not a recovery of any kind, in fact that's destroying data.
Imagine you have only few corrupt files and you have to wipe your whole hdd to get vista back working. But that's what MS makes you do with not giving you install media.

So, I would consider using Backup&Restore and create image of C:, which you can restore again probably to any partition you need. That process does not wipe your hdd like the restore partition. Even the restore DVDs set would wipe the hdd most likely. So just make an image of C: if you like it as it is, and you can restore it to the same state if you ever need to.

Another option is spending little money on some software, for example Acronis True Image Home I think sells for $59, which can also image your partition to a file (on ext hdd for example), offers to create bootable cd that you can boot your computer with and restore the image just to a selected partition, while not touching any other partition in the process. It offers compression too so I recently imaged 29GB system partition into 9GB image file, and that was High not Maximum compression.

Those are just a few ideas. Think it over and the choice is yours. The bottom line is to create a way to get vista back, and you can get rid of the restore partition after that.

---

### Post by wbest on 2010-02-21
One other question about this.  It only allows 4 PRIMARY partitions, right?  Because doesn't Ubuntu setup a swap space partition?  Should I be worried about that one?  Or will that work out fine?

---

### Post by wbest on 2010-02-22
Dual boot went fine.
Got rid of th HP_TOOLS partition (but backed it up on my external just in case).

Both UNR and Windows 7 boot without incident.  There was a tense moment for a minute there, but after booting into Ubuntu recovery and running the package fixer and stuff, it turned out okay.

Thanks for all your help guys.  I really appreciate it.

---

