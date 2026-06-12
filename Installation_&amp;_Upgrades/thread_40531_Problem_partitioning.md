---
title: "Problem partitioning"
date: 2005-06-09
forum: Installation &amp; Upgrades
---

### Post by Fozer on 2005-06-09
Well, I finally got around to installing Ubuntu. From what I know, the install cd comes with a partitioner thingie, and it'll automatically partition your hard drive if you have enough free space on it.

I went through the installer until I got to the partitioning part. I tried the guided partitioning, and it said there wasn't enough free space. I checked the size of the partitions and stuff using the manual partitioner, and sure enough there wasn't. I then made the assumption that if I resized an existing partition to make it smaller that the "extra" space would become free space. Only when I tried to resize my main partition, nothing happened. I typed in the new size that I wanted it to be, it went to the blue background screen for a while, then the manual partitioner popped up again, with nothing changed.

I did notice a symbol beside the partition I wanted to resize that the others didn't have, so maybe that has something to do with it.

---

### Post by mingus on 2005-06-09
Ummm . . . please give us more information to work with.  Apparently you have other partition(s) on the disk.  If you have a Windows installation already, use Disk Manager to find all the partitions and their sizes, total size of disk, etc.

---

### Post by Fozer on 2005-06-09
I have the main partition, with everything on it, and the backup partition that came with the computer.
The main one is 143GB total, and the backup is 6.96GB total, though I'm not sure how that would help.

Oh, and the disk is 160 gigs.

As for not giving much information, I don't have much information. I know what happened and I know what I was expecting to happen. Period.

---

### Post by mingus on 2005-06-09
[QUOTE=Fozer]As for not giving much information, I don't have much information. I know what happened and I know what I was expecting to happen. Period.[/QUOTE]

Patience, please.  Installing any OS - incl W$ - requires having this data.  Especially if there there are existing partitions or an existing installation, and double the case if helping someone remotely . . . assumptions or incomplete info can result in ugly surprises.

What does "with everything on it" mean?  Is there anything here you want to keep, like an existing Windows installation (dual-boot) or user files you want accessible to Ubuntu now?  If either, how much space does this occupy on the partition, and what filesystem is it using?  If there is nothing, then Ubuntu can takeover the entire drive (if so, why did you want to size it down rather than just deleting it and doing a clean install?)?

---

### Post by Fozer on 2005-06-09
Yeah, it's the one with the windows install and the user files, etc. on it. I do want to make it dual boot. The files take up roughly 16 gigs, and it uses NTFS.

---

### Post by mingus on 2005-06-09
OK, this is a start.  I'm assuming you are new to this.  If you're already familiar with this, apologies in advance.

One reason why the Ubuntu partitioner may not have attempted to resize the partition is because it detected a potentially unsafe condition - most often this is due to breaks in filesystem linkages, bad sectors, or fragmentation on this disk.  This is a fact of life with Windows systems (unlike Linux) and must be remedied before partitioning.

The tools MS provides to clean this up are chkdsk and the Disk Defragmenter.  Chkdsk is run from the command window with one or more parameters (-r, -f, etc.).  The program does not actually run until you reboot; it locks the drive and must not be interrupted.  Depending on the number of files (not size) on the partition, and speed of system, this can take quite a while.  Help & Support and the following article should be read first.

[http://support.microsoft.com/default.aspx?scid=kb;en-us;314835](http://support.microsoft.com/default.aspx?scid=kb;en-us;314835)

After chkdsk has finished, run the Disk Defragmenter.  If the disk is heavily fragmented, it may require 2 or even 3 passes.

You can then try the Ubuntu "guided" install again.  It is advisable to review the partitioning section of the Manual to understand the "guided" alternatives, or if you need/want manual control, those considerations.

[http://archive.ubuntulinux.org/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/ch06s03.html#di-partition](http://archive.ubuntulinux.org/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/ch06s03.html#di-partition)
[http://archive.ubuntulinux.org/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/apbs03.html](http://archive.ubuntulinux.org/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/apbs03.html)

Finally, before you begin it is very wise to have on hand Windows install media or recovery media from which you can boot into Windows and/or perform recovery commands from (e.g., the XP CD).

---

### Post by Fozer on 2005-06-10
Eh? XP has chkdsk? I thought they took it out for some inane reason. That could help.

---

### Post by mingus on 2005-06-10
It's still there.  If memory serves, used to be scandisk and a menu item.  After NTFS, chkdsk isn't needed as much as it was with FAT32, because NTFS is a journaled filesystem.

A detail I didn't mention:  when the disk is defragged, all the data will be moved to the front.  This is another requirement for resizing, otherwise the partitioner has to do the data moving.  PartitionMagic can do this, but it sure can take a long time.  Defrag works a lot better.  Not sure where the Ubuntu installer's threashold is with this, i.e., how much it is able/setup to move data.  Another reason to do in advance.

Finally, every source on the planet that does this kinda stuff will urge you to backup anything critical.  I've never seen a partition's data actually lost in a procedure like this, but I have seen glitches where getting things back right would've been a lot easier with a backup.

No reason to worry, just wise to be prudent.

---

### Post by Fozer on 2005-06-11
Thanks for the help, though it still doesn't seem to be working.
Also, one thing I forgot to mention earlier is that it's the 64-bit version I'm trying to install, if that makes any difference. I have heard that 64-bit Ubuntu is a bit mor buggy.

---

### Post by az on 2005-06-11
There are some things that do not compile in 64 bit.  there i nothing that affects the installer, though.

Read this:
[http://test.wiki.ubuntu.com/forum/installation/Partitioning](http://test.wiki.ubuntu.com/forum/installation/Partitioning)

When you shrink your ntfs partition, after it completes and you get the partition table again, there is no free space displayed?  What label is displayed next to the partition you just resized?

---

### Post by Fozer on 2005-06-11
The problem is, it doesn't shrink it. I get to the screen where you have to enter the new size you want, I enter a smaller size, and it goes directly to the manual partition screen with no changes made.

There is a zigzaggy arrow thing beside the partition I'm trying to shrink, though I don't know if that means anything or not.

Oh, and one more semi-related question: What is a good size for an Ubuntu partition?

---

### Post by az on 2005-06-11
I am not in front of an installer right now, but the zigzaggy thing may mean that there are changes to be done when you tell it do go.  Is there an "apply changes", or "continue" option displayed?  Perhaps you have to scroll down to see it, as I recall...

Size depends on what you need.  2.1G bare minimum, 3 or more for experimenting, 5 or six for a running desktop...

---

### Post by Fozer on 2005-06-11
Okay, I'll check for that option. Also, when I tried to resize my fat32 backup partition, just too see if it would work, it did.

One more question, is it possible to work in one partition (i.e. an Ubuntu partition) and save/edit/etcetera another, or do you need  extra space for programs, etc.?

EDIT:
I can't seem to find any of those options, though I do have an idea that may or may not be plausible. Since it seems to work with my fat32 backup partition, maybe I could somehow convert my main partition into fat32, resize it, then change it back to ntfs. If there's something blatantly stupid about that idea, please feel free to tell me so.

---

### Post by mingus on 2005-06-12
A FAT32 partition can be modfied from Linux, but NTFS is read only.

Not sure, but what azz may have been referring to - I'm working from memory here - is that the installer may queue up all the partitioning commands until you "apply" them.  This is how PartitionMagic and other partitioners work.  The idea is you can see what the final result will look like before you commit to the changes.  

What would you use to convert NTFS to FAT32 and back?

---

### Post by Fozer on 2005-06-12
[QUOTE=mingus]A FAT32 partition can be modfied from Linux, but NTFS is read only.

Not sure, but what azz may have been referring to - I'm working from memory here - is that the installer may queue up all the partitioning commands until you "apply" them.  This is how PartitionMagic and other partitioners work.  The idea is you can see what the final result will look like before you commit to the changes.  [/quote]
I've tried the "apply changes"(or whatever it's called) almost all of the times that I've tried the resizing. Doesn't seem to do anything

[QUOTE=mingus]What would you use to convert NTFS to FAT32 and back?[/QUOTE]
Dunno, don't know if it's even possible, just a passing thought.

[quote=fozer]One more question, is it possible to work in one partition (i.e. an Ubuntu partition) and save/edit/etcetera another, or do you need extra space for programs, etc.?[/quote]

---

### Post by mingus on 2005-06-12
Fozer -

If you are positive that the Ubuntu partitioner cannot resize, there is still an unidentified issue.

Re bi-directional conversion between NTFS & FAT32:  Yes, it can be done, but requires extreme care.  The first step of course is to back up the partition, *and* verify that the backup is good.

Using only what comes with Windows, there is a program (convert.exe) that can take a FAT32 to NTFS, but not the other way.  The only way in Windows to get NTFS to FAT32 is to delete the partition, reformat it, restore the files from the backup, and then restore the MBR.  (The backup/recovery must be a filesystem type, not a bit image; current imaging tools allow both methods.)

Another approach is to use PartitionMagic.  It can convert filesystems either direction.  I have used it for NTFS-->FAT32.  Of course, if you had PM, you probably would not need to consider this at all.  You would simply shrink the NTFS partition with it; if it could not, it may tell you why.    

Two other thoughts:

When you ran chkdsk, were you sure to use an option (like /r) that will fix everything?

Also, it occurs to me that you have a 160GB disk, more importantly, a 143GB partition.  Do you know if your system's controller and BIOS handles 48-bit LBA?  Additionally, are you using XP SP1, or W2K SP3 with the Registry bit enabled?  If all of the above is not true, then your system is only seeing 137GB, not the 143GB.  From Western-Digital:

"Certain operating system utilities such as scandisk and defrag may not function properly on drive partitions exceeding 137GB.  Creating multiple partitions less than 137GB will allow proper functionality."

In other words, even if the hardware and OS can handle the larger capacity, still some things may not work right over the 137GB barrier.  The drive manufacturers recommend PCI controller cards for drives this size (or as a last resort, a drive overlay - ugh!), but of course, you can't use that as your primary drive with Windows because it's system partition must be the first partition on the first IDE channel - that's hard coded.

You might compare what Windows Explorer, Disk Manager, fdisk, and msinfo32 tell the size of the drive is.  Don't be surprised if different capacities are reported.

---

### Post by Fozer on 2005-06-12
Ah, that's probably the problem then. So if I resize it to be less than 137 GB it should work?

Secondly, chkdsk doesn't seem to do anything with /R enabled. Just pops up for a second, then dissappears.

Thirdly, I still have the question about if it's possible to save on partitions you're not working on, or if extra space on the same partition is neede for that.

---

### Post by mingus on 2005-06-12
I trust you took a look at:

[http://support.microsoft.com/default.aspx?scid=kb;en-us;314835](http://support.microsoft.com/default.aspx?scid=kb;en-us;314835)

When you say chkdsk "Just pops up for a second, then dissappears" are you referring to when you open the command window and invoke chkdsk (>chkdsk /R), or after you have rebooted and chkdsk begins processing.

Chkdsk is going to check all the sectors on the disk.  If it finds one, it writes the data to a new cluster and marks that cluster as bad.  Encountering a bad sector can cause anything that moves data across the entire volume (like shrinking or defragging) to choke.  To read/write these sectors, the volume must be locked.  So when you invoke >chkdsk /R is instructs Windows to run the chkdsk process after reboot but before the OS loads (that is, before any files are opened).  If you are not seeing chkdsk run after reboot, something is wrong.  With 16GB, and chkdsk /R using 4 phases, you should definitely see something happening, even if nothing needs to be fixed.

So re *'sizing below 137GB and it should work?'* - first, if you have bad sectors and chkdsk doesn't run in /R mode, probably whatever you use to resize will probably fail.  If the bad sector is inside the first 16GB on the disk, it will definitely fail because it cannot write to that sector.  If the bad sector is elsewhere on the disk, if *may* fail, that is, sometime a sector can be read but not written to.  Bottom line, important to be satisfied that chkdsk has done its job, regardless.

Will it work once you've sized it down and you have the free space?  Probably.

Re:  *"I still have the question about if it's possible to save on partitions you're not working on, or if extra space on the same partition is neede for that."*

Not sure I'm understanding the question.  If you mean can you have a partition that both Windows and Ubuntu can write to, yes, if it is FAT32.  If this isn't what you mean, you'll need to clarify.

---

### Post by Fozer on 2005-06-13
Yeah, that's pretty much what I wanted to know. So if I somehow make my main partition into fat32, Ubuntu should still be able to write to it, even if it's installed on another partiton, right?

Also, upon reboot, chkdsk doesn't happen at all. Just the normal boot sequence thing.

---

### Post by mingus on 2005-06-13
[QUOTE=Fozer]So if I somehow make my main partition into fat32, Ubuntu should still be able to write to it, even if it's installed on another partiton, right?

Also, upon reboot, chkdsk doesn't happen at all. Just the normal boot sequence thing.[/QUOTE]

Definitely. 

Re chkdsk:  I'm sorry that the only suggestion I can offer is that you search the Microsoft support site or google for a clue - be sure to use Advanced Search and include TechNet and MSDN, not just the KB.  Here's how it's supposed to work, which may help in your search:

Chkdsk can run in several different modes.  If just an inquiry, it will run immediately and report the results.  I think there is 1 fix mode that also can run immediately.  But the /F and /R modes must lock the disk, which cannot be done while Windows is running.  So when you do >chkdsk /R, the program does not run; it sets a bit switch.  When Windows is just beginning to start, there is another program (I think it's autochk)  which checks this switch, and if it is set, Windows will stop loading and chkdsk will be called to do its /R thing.  You'll see a blue screen with white letters reporting disk results.  Also, unfortunately the query mode cannot check sectors, only the /R mode, so this process is all there is to verify the sectors are OK (aside from 3rd party products).

You may be able to successfully shrink the partition without chkdsk, just impossible to say.   :neutral:

---

### Post by Fozer on 2005-06-13
Nevermind that, I tried again and it worked. Odd.

---

