---
title: "Grub problems after deleting partitions"
date: 2012-01-16
forum: Installation &amp; Upgrades
---

### Post by justgrant2009 on 2012-01-16
Hey guys, I have a laptop that was multi-booting about 6 partitions.  

I had multiple operating systems on it (Vista/XP/Ubuntu/BackTrak/etc) and I decided I would wipe the partitions down to one, and just leave Vista on it for my wife to use (she already has a lot of pictures and music on that partition that she wants to keep) and I didn't have anything of any importance on any of the other partitions.  

In Vista I used the disk manager, and just deleted the other partitions.  Upon reboot, grub cannot find my HDD, so I don't even get the menu to pick what to boot.  Also, (I don't have a vista disk, but I do have the xp one) I tried putting the XP disk in to see if I could at least reinstall xp to unallocated space I had cleared, and it tells me that windows can't find the hard drive either.  

If you need me to give you guys any more information from the computer, just ask, I'll gladly do so.  

I just really want the computer up and running again (hopefully, without having lost the data that was in the vista partition).

---

### Post by drs305 on 2012-01-16
I am not a Windows guy but will offer a few points.

When Windows installs newer versions, it often places some of it's boot files in the previous version's partition. Removing an older Windows partition may delete files required to boot and may require repair via Windows software.

However, it's also possible all you have to do is point the MBR back to the Vista partition (if that is where *all* the Windows boot files reside.

If this is the case, you can try to restore the Windows bootloader via an Ubuntu LiveCD. This should work if the boot flag is on your Vista partition.

Boot the CD, open a terminal, and run the following commands. The system will say that lilo is not fully installed and suggest you run additional commands. This is NOT desired or necessary.

If Vista is not on the 'sda' drive, change the command to the proper drive.

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

---

### Post by justgrant2009 on 2012-01-16
DRS,

Thanks, I'll give that a shot.  Unfortunately, I'm at work right now and don't have the computer with me.  But thank you for such a quick response.  Vista was the first operating system on the machine, followed by Ubuntu 9.04, upon which I set up GRUB and edited my MBR as needed upon each new OS "moving in" to the machine.  

Does anybody else have any ideas?  I know I can't try anything until I get home today, but it would be great if I had a few different options to try, just in case the first doesn't work. (although I'll be crossing my fingers it does)

edit: Also, it's been quite a while since I've used the forums here and my profile is out of date, I tried to edit it, but it's telling me I don't have permission to.  Is this because of my inactivity? (I know that's completely unrelated, and not really important)

---

### Post by ajgreeny on 2012-01-16
Another option is to download and burn the [Supergrub]("http://www.supergrubdisk.org/") live CD, then boot from that and use it to reset the vista MBR, but as I assume you already have a live ubuntu CD, the lilo method will be quicker and easier.

---

### Post by justgrant2009 on 2012-01-16
> **ajgreeny said:**
> Another option is to download and burn the [Supergrub]("http://www.supergrubdisk.org/") live CD, then boot from that and use it to reset the vista MBR, but as I assume you already have a live ubuntu CD, the lilo method will be quicker and easier.
Actually, I do have a Supergrub cd somewhere in the house.  I didn't know it had an easier method for just resetting the MBR.  Is it pretty straight forward?

---

### Post by Mark Phelps on 2012-01-16
You said you erased all but the Vista partition, right?

OK, then you erased the partition containing the GRUB code -- so of course, GRUB no longer worked.

And, since you (apparently) had XP before Vista, when you installed Vista, without telling you (why would it do that??), Vista installed its boot loader files to the XP partition.  So when you removed that, you removed the Vista boot loader files.

What MIGHT work, is Boot-Repair:

[http://ubuntuforums.org/showthread.php?t=1769482]("http://ubuntuforums.org/showthread.php?t=1769482")

---

### Post by sonicsackboyver.25.04 on 2012-01-16
I had this problem once and here is what i did.
Go to the supergrubdisk website and download rescatux. Burn it to a cd/dvd then boot into rescatux. This video will show you the rest:
[http://www.youtube.com/watch?v=SPpPgnfTdE0](http://www.youtube.com/watch?v=SPpPgnfTdE0)
once done restart and it should boot into windows :)

---

### Post by justgrant2009 on 2012-01-16
This is all great, thank you guys! I'll be trying this all tonight.  

Mark, Vista came on the machine, not xp.  I put xp on way later in the machine's life.  But considering, I set up the dual boot with the first Ubuntu partition on it, and that is one of the partitions I deleted, I think you're right that the boot loader got deleted.  

I'll try all this stuff out tonight and let everyone know what worked.

Thank you for all the advice!

---

### Post by ottosykora on 2012-01-16
I can also recomend for that the Boot-repair CD/usb .

Recently I was in need to repair MBR, in seconds the Boot-repair did find and replace the MBR with the right version for the task. No need to think too much, it does all by itself almost.
It has generic MBR Versions on board and will place it to the right position, windows boots as new then.

---

### Post by drs305 on 2012-01-16
> **ottosykora said:**
> I can also recomend for that the Boot-repair CD/usb .

Recently I was in need to repair MBR, in seconds the Boot-repair did find and replace the MBR with the right version for the task. No need to think too much, it does all by itself almost.
It has generic MBR Versions on board and will place it to the right position, windows boots as new then.

I haven't used Boot Repair with Windows but have read where it works. There is a link on using BR in my signature line in Post #2. Even if you don't use it this time, it's nice to have around...

---

### Post by justgrant2009 on 2012-01-16
> **drs305 said:**
> I haven't used Boot Repair with Windows but have read where it works. There is a link on using BR in my signature line in Post #2. Even if you don't use it this time, it's nice to have around...
That's a very good idea actually.  Like I said, I know I have a SuperGrub Disk at home somewhere, so I'll find it or make a new one as well as a disk for all these other ideas, and keep them all in one place.  Just so I know I'll always have the tools necessary and can save time in the future.

---

### Post by justgrant2009 on 2012-01-16
> **sonicsackboyver.25.04 said:**
> I had this problem once and here is what i did.
Go to the supergrubdisk website and download rescatux. Burn it to a cd/dvd then boot into rescatux. This video will show you the rest:
[http://www.youtube.com/watch?v=SPpPgnfTdE0](http://www.youtube.com/watch?v=SPpPgnfTdE0)
once done restart and it should boot into windows :)
After watching the linked video, this looks most like what I need.  I'll try this first, and let you all know what happens.

---

### Post by darkod on 2012-01-16
Even though a one-click solutions sound tempting, I would boot with the ubuntu cd (you still have one?) into live mode, open the vista partition and take a look at the files. If you don't have the three boot files/folders, I don't think supergrub or boot-repair can help. They just install windows bootloader if I'm not mistaken, more or less.
Vista boot files are:
bootmgr
boot/BCD
system32/winload.exe

That should be in the root of the vista partition.

If you do have them, and you have the boot flag set on the partition (can be checked with sudo fdisk -l), you only need a windows bootloader on the MBR or equivalent.
The lilo commands posted earlier will do the job from live mode.
All of that without letting SG or BR running around your HDD and possibly ending with a result you didn't expect (I've seen it here).

---

### Post by justgrant2009 on 2012-01-17
Well I tried Rescatux, and it hasn't worked.  There were three partitions sda1-3, It told me it Cannot mount the partition for all 3 of them.  Also, now when I boot, instead of getting a grub error, I get "MBR" [line return] "MBR 123:   " and then nothing happens, I can't type anything, it just locks there.

---

### Post by justgrant2009 on 2012-01-17
I just plugged my Gparted live cd in to take a look at the partitions, and sda2 is where vista is and that's what I want to keep safe.  Both sda1 and 2 have warning symbols next to them, and when I view information on the drives, they both have the same warning: "Unable to detect file system! Possible reasons are: - the file system is damaged, -the file system is unknown to Gparted, -there is no file system available (unformatted)"

sda2 is also flagged as boot.

Please tell me we havn't lost our photos?

---

### Post by Mark Phelps on 2012-01-17
> **justgrant2009 said:**
> Please tell me we havn't lost our photos?

Well, at this point, it looks like you have ...

The question is whether or not you can get them back.

The link below shows how to use TestDisk to get stuff back:

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step")

Since sda2 was Vista, and that used NTFS, if testdisk doesn't work for you, then you can explore using an MS Windows PC to try to recover the files, but you will need to remove the drive from this PC and connect it to a Windows PC.  IF you can do that, then go to Runtime Software and download their trial versions of either RecoverMyFiles or GetDataBack for NTFS.  You can use either to see if it finds your files -- but you have to go online and purchase the retail version to do the actual recovery.

---

### Post by justgrant2009 on 2012-01-17
This is seriously bad.  I don't know why this is so bad, and how it happened.  This is really distressing to have lost the data.  I didn't adjust the vista partition and I didn't do anything to affect the data located there, so there must be a way to retrieve it all.  Can anyone help further, are there any other options to recover it.  

One main question is why is it unable to mount? What changed?  And for future reference, what did I do that was so irreparable as to cause this?

---

### Post by darkod on 2012-01-17
Hit the brakes, don't panic. And don't start trying all sorts of things, just confirmed ones. There is hope yet I think.

You can use testdisk to try recover deleted partitions.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

At this moment it's better if you can bring the disk to the same partition layout as before if that gets your data back. You can delete partitions you don't want later.

You experienced are you with partitions? You understand your disk layout?

---

### Post by justgrant2009 on 2012-01-18
I have dealt with partitioning drives before, yes. I'm experienced in setting up dual boots and why partitions need swaps, yes.  But do I remember exactly what my partition layout was on this machine before I threw it off, no :( . But I'll try TestDisk and see if that helps.

---

### Post by justgrant2009 on 2012-01-18
Something I'm trying to understand, do I need to use the TestDisk Live CD or download it inside an Ubuntu Live CD environment?

---

### Post by darkod on 2012-01-18
It will work from ubuntu live mode. Download it inside live mode and run it with sudo.

When it lists the partitions found, there is one thing it took me time to figure out. The start and end of partitions are stated in groups of three numbers, CHS which I guess is Cylinder Head Sector.

So the first might start at
0 1 1

and end for example at the end of cylinder 111 like:
111 255 63

The second and third number 255 63 are the end of cylinders, depending if your partitions end on cylinder boundaries.

The deeper scan might detect two partitions number 1 for example, or even three, so you need to take a very good look at the CHS numbers and make sure partitions don't overlap. EDIT: Select to recover the partitions that look correct. You can use the P option to display files on any partition discovered by testdisk. The deep search is really good, so it can detect sometimes partitions you have deleted on purpose earlier. That's why you need to take a good look deciding which partition you want to recover.

If you know what the layout was, make sure it matches before you write the partition table. That is crucial with testdisk, their manual also says it: UNTIL ALL PARTITIONS ARE FOUND AND THE CHS DATA LOOKS CORRECT, NEVER WRITE THE PARTITION TABLE!!!

Their step by step manual for recovering partitions, it's good:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by justgrant2009 on 2012-01-18
If I attempt to do this TestDisk, and let's say I'm off a little bit on when the partitions look all correct  (like I said, i don't remember exactly how large each partition was, how many there were or what order they were in.  I know how large my vista partition was approximately 280gb) if I write with TestDisk, does that ruin my chances of taking it somewhere professional to have the data recovered?

Because honestly, when you started talking cylinder heads, that went over my head, I'm not that experienced then.

---

### Post by darkod on 2012-01-19
I just mentioned it so you won't be confused by the fact that the Start and End are marked with a group of three numbers, not a single number.

If you use the P option to browse files, it can help figure out which partition is the correct one, on top of the size of the partition.

You can do the testdisk deep search, if it doesn't look good to you you never write the partition table and testdisk doesn't change anything in this case.

---

### Post by justgrant2009 on 2012-01-19
Ok, when you say it "looks good to me" I'm not sure I'll know 100% when that is.  Like I said, I had a lot of partitions on it, and I know the size of the Vista one, and that's about it.  

So what happens if, say, I know I got about 90% of them right, I got the Vista partition right, I got several of the others (hopefully the logical partition that Vista needs to boot properly), but I missed 2 partitions at the end of the HDD.  Would it still be able to boot the Vista partition long enough for me to get all my files backed up then just reformat the whole drive?

---

### Post by darkod on 2012-01-19
Yeah, as long as the partition you need is correct, it should be fine.

---

### Post by justgrant2009 on 2012-01-19
Ok, then, I think I'll give it a shot then.  

Thanks for all your help so far, it's been very informative.  I'll post the verdict once I finish it.

---

### Post by justgrant2009 on 2012-01-24
Ok, so last night, I was finally able to sit down with the machine for a bit.  I used TestDisk and upon the Deeper Scan, it did find my partition with Vista and all my files.  I've brought it to work with me today, and I'm using TestDisk to copy folder by folder the files I want backed up to an external HDD.  That being said, at least I'll have my files.  

Next order of business is what do I do about the partition recovery inside TestDisk, I already read just about everything on the wiki, and follow it decently alright, but am still curious.  I have a lot of partions on it after the deeper scan and only 3 say they are NTFS (which I assume is good) I have the one vista is on, one that is a windows recovery, and one other.  Then I have a TON of [Linux] partitions it says, and a couple labeled FAT32.  It has a D for delete next to all of them except the NTFS paritions.  One of the NTFS has the * next to it, the partition with Vista and my file system is labeled with L, and the windows recovery NTFS is labeled L.  

Any suggestions on what to do?  Keep in mind, if I can recover it, I would much prefer that, and I don't care if any of the linux partitions are lost, I was deleting them anyways.

---

### Post by darkod on 2012-01-24
> **justgrant2009 said:**
> Ok, so last night, I was finally able to sit down with the machine for a bit.  I used TestDisk and upon the Deeper Scan, it did find my partition with Vista and all my files.  I've brought it to work with me today, and I'm using TestDisk to copy folder by folder the files I want backed up to an external HDD.  That being said, at least I'll have my files.  

Next order of business is what do I do about the partition recovery inside TestDisk, I already read just about everything on the wiki, and follow it decently alright, but am still curious.  I have a lot of partions on it after the deeper scan and only 3 say they are NTFS (which I assume is good) I have the one vista is on, one that is a windows recovery, and one other.  Then I have a TON of [Linux] partitions it says, and a couple labeled FAT32.  It has a D for delete next to all of them except the NTFS paritions.  One of the NTFS has the * next to it, the partition with Vista and my file system is labeled with L, and the windows recovery NTFS is labeled L.  

Any suggestions on what to do?  Keep in mind, if I can recover it, I would much prefer that, and I don't care if any of the linux partitions are lost, I was deleting them anyways.

If you can somehow copy the list the deeper scan returned, or even better take a pic and attach it here, I can give you my opinion.

Without seeing it, I really wouldn't like to say anything.

For example, you say the vista partition has L for logical, but in fact most of the time the windows partition should have the *, which means primary bootable. Often testdisk can return L instead of P or *, but it's good that at least it can find the partitions. It's up to you (us) to change the L to P or * where needed. And then you write the part table.

That's why I asked you about partitions and your disk layout at the beginning, it would help if you know what it was. We need it for the decisions where to put *, P or L and what to leave as D.

Post a pic if possible, and lets see.

---

### Post by justgrant2009 on 2012-01-24
I'll get you a screenshot here in a second, I've just set it up and need it to run analysis again.  So, provided it looks correct when show you, (that the chs's are correct), at least for the NTFS partitions, and we decide to set the Vista partition with my filesystem as the boot "*", things should go fairly smoothly right?

It's about 45% through the first quick scan analysis.  Once it finishes the deeper scan, I'll upload a screen capture.

---

### Post by darkod on 2012-01-24
Yeah, it should be smooth. Even if we make a mistake with the boot flag, it's the smallest problem. As long as the partition is correct and readable, you will be able to access it with ubuntu cd in live mode, etc. You can also use Gparted later to move the boot flag if we see that we put it wrongly.

The boot flag is only for windows to boot, it has no relation to the data on the partitions. For this reason, it is usually set on the system partition, C:. Lately in win7 MS started creating separate small boot partition and the flag is there, but in vista it didn't exist.

---

### Post by justgrant2009 on 2012-01-24
Ok, I have 3 pictures here.  The first is what Test disk first tells me when it finished the deeper search:

[IMG]http://i.imgur.com/soWUw.png[/IMG]

The second Image is what I have when I continue and look at my partitions that TestDisk found without making any changes.  The [SQ004732V03] partition has my vista filesystem on it.  

[IMG]http://i.imgur.com/KAutd.png[/IMG]

The last image is what I have attempted to do to tell it which partition I want to boot from, and put "P" on the other partitions that at least have names (I could be very wrong with this move, so please help correct me if need be)

[IMG]http://i.imgur.com/KbXa3.png[/IMG]

---

### Post by justgrant2009 on 2012-01-24
Does this look correct to you Darko?

---

### Post by darkod on 2012-01-24
I looks good. But I don't understand one thing. I thought you had all these linux partitions until recently. How come the vista partition seems almost as big as the whole disk, with the exception of the two other small partitions (Toshiba system and HDD Recovery).

If you write your part table with only these three partitions does it sound OK to you according to what you had?

Another important thing. If you select the vista partition with the up/down arrows and hit P does it list the files you expect? Are they readable?

If they are, it's an excellent sign. And I guess you can set the partition as your last screenshot, hit Enter to continue and you should see a list with only those three partitions next. At the bottom there will be the Write command.

---

### Post by justgrant2009 on 2012-01-24
Yes, that is correct, the vista partition was by far the largest on the computer.  My wife used it mostly, and I just used the linux partitions experimentally.  They were on it up until I tried using vista to delete the partitions and that's when all this started going wrong.  So no I don't mind deleting them, but is it alright that they get deleted this way, or do I have to make sure that the partition layout goes back exactly the same?

Yes when I press P it lets me access the file system and it all looks fine.  I even copied a some photos over to my external HDD and plugged it in to another computer as was able to view the images correctly.

I'm going to go ahead and accept the layout I displayed in the third image and choose write.

Wish me luck. I'll let you know what happens.

---

### Post by justgrant2009 on 2012-01-25
EDIT: Wow Sorry for the size of the photo, it was taken with my phone and somehow thinks it needs to be huge...

Ok, so far I think it's good.  I've got this after doing that:

[IMG]http://i.imgur.com/BTLEY.jpg[/IMG]

Is this what you mentioned about the boot flag needing to be switched?  I think we used to boot from grub by choosing windows recovery menu option (I don't know why, but the label was windows recovery and when we would choose that, it would load Vista no problem).  So should we try moving the boot flag to that partition labeled recovery?  

Could you direct me to a thread on moving the boot flag with grub? Or could you explain how I do that?

Thanks! Almost there!

---

### Post by darkod on 2012-01-25
The picture doesn't display, at least not to me right now. Maybe because it's too big.

I wouldn't usually recommend booting the restore partition because that may begin a restore process. But in case the vista boot process was "added" to that partition, then it might work out fine.

In any case, I would do this:
1. Boot with the ubuntu cd and try to open the vista partition now after the testdisk procedure. Look if all your files are there. Plug in an external hdd and copy everything. I know you said you copied some files, but copy everything now.
2. Then unplug the external hdd, open Gparted and on the vista partition do a right-clink, Manage Flags. Deselect the boot flag. On the recovery partition do the same but this time select the boot flag. That will turn it on.

Restart and see if it boots.

But it also depends if you have windows bootloader or grub on the MBR of the disk because grub won't work now. As I said the picture is not showing and I can't see.

If you get a grub message do the lilo procedure we talked about earlier in this thread. That will sort out grub.

---

### Post by justgrant2009 on 2012-01-25
I just shrank the photo in PS, let's see if this one works better.

[IMG]http://i.imgur.com/2ZmpL.jpg[/IMG]

I don't think it's GRUB, it looks like a windows problem.  Unfortunately, it's asking for the windows disk, which I don't have.  It came with Vista on it OEM from Toshiba, and they didn't send a disk with it.  I do have a 64-bit windows XP disk that I'm currently not using, and I'm getting a windows 7 ultimate upgrade disk later this week or next (that I planned to use in junction with the XP disk).

---

### Post by darkod on 2012-01-25
Yes, it's windows bootloder. You see the file it reports as missing? That's one of the vista/7 bootfiles.
Open the vista partition and check if you have the folder windows there, then system32 and the file winload.exe inside.

Also check if you have the file/folder:
/bootmgr
/boot/BCD

Those are the other two vista boot files/folders. Although these two can be on another partition sometimes, it depends. But as far as I know, the winload.exe needs to be on the system partition because it's in the /windows/system32 folder.

---

### Post by justgrant2009 on 2012-01-25
So if those files aren't present on the partition with my file system, but are present on the backup HDD partition, would it be fine to just copy them over to the appropriate folders?

---

### Post by Quackers on 2012-01-25
As darkod seems to be offline I would suggest that you now run the automatic repair option from the Windows cd. It may need to be run up to 3 times.
If your Windows system has been successfully recovered the winload.exe file should be present. The current problem would seem to be that the bootloader (or lack of one) can't find the Windows partition because there is no pointer to it in the MBR of the drive.

---

### Post by darkod on 2012-01-25
> **justgrant2009 said:**
> So if those files aren't present on the partition with my file system, but are present on the backup HDD partition, would it be fine to just copy them over to the appropriate folders?

Yes, it should be fine. If you have an earlier backup or somehow you managed to copy them and you have them, just copy them back and it should be fine. It depends a little what was the original setup, just a standard or something more specific, but in general just copying files back should work.

In XP I have done it with general boot files that weren't even from the same computer, and it worked.

---

### Post by Quackers on 2012-01-25
Aha! darkod is back :-)

---

### Post by justgrant2009 on 2012-01-25
Darko, 

So it doesn't matter that it may have originally been on a different partition (I know you just said it worked going from a completely different computer, so I don't know how specific that file needs to be).  If I change the boot flag in grub and try setting it to the other partition would that do anything or just be ignored since it's using windows to boot now?  (I'm just getting all my information before I attempt anything).

And Quackers,  I really appreciate you jumping in to help when I didn't get an immediate response from Darko, thank you!

---

### Post by darkod on 2012-01-25
Changing the boot flag is still an option, it might be as simple as that. I preferred you copy all the data first in case the recovery partition kick in if we set the boot flag on it.

Also, after all this effort, I think it might be a good idea to run the boot info script. It will show details what it can see, and what not. Follow the link in my signature, it has all the instructions to run it (you can do it from live mode) and how to post the results.

---

### Post by Quackers on 2012-01-25
Definitely :-)
The boot script output will tell what's where........and what isn't!

---

### Post by justgrant2009 on 2012-01-28
Ok, I just checked, and it does have all three file/folders on the main vista partition.  So since it has those, I'm assuming, they might be corrupt? 
I'll run the boot script here and paste the contents for you.

---

### Post by justgrant2009 on 2012-01-28
here's what the boot info script gave me

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Testdisk is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

hda: ___________________________________________________________________________

    File system:       iso9660
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048     3,074,047     3,072,000   7 NTFS / exFAT / HPFS
/dev/sda2    *      3,074,048   608,464,895   605,390,848   7 NTFS / exFAT / HPFS
/dev/sda3         608,464,896   625,141,759    16,676,864   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5c74ae42

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   781,417,664   781,417,602   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/hda                                                iso9660    Ubuntu 8.04.2 i386
/dev/loop0                                              squashfs   
/dev/sda1        DA1C4F001C4ED763                       ntfs       TOSHIBA SYSTEM VOLUME
/dev/sda2        BA4C7E6B4C7E21F5                       ntfs       SQ004732V03
/dev/sda3        4484A48084A475D8                       ntfs       HDDRECOVERY
/dev/sdb1        EE4D-4942                              vfat       My Passport

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /media/SQ004732V03       fuseblk    (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sdb1        /media/My Passport       vfat       (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb1

00000000  eb 5a 90 4d 53 57 49 4e  34 2e 31 00 02 40 20 00  |.Z.MSWIN4.1..@ .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  82 7c 93 2e 91 74 01 00  00 00 00 00 02 00 00 00  |.|...t..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 42 49 4d ee 4d  79 20 50 61 73 73 70 6f  |..)BIM.My Passpo|
00000050  72 74 46 41 54 33 32 20  20 20 f1 7d fa 33 c9 8e  |rtFAT32   .}.3..|
00000060  d1 bc f8 7b 8e c1 bd 78  00 c5 76 00 1e 56 16 55  |...{...x..v..V.U|
00000070  bf 22 05 89 7e 00 89 4e  02 b1 0b fc f3 a4 8e d9  |."..~..N........|
00000080  bd 00 7c c6 45 fe 0f 8b  46 18 88 45 f9 fb 38 66  |..|.E...F..E..8f|
00000090  40 7c 04 cd 13 72 4e bf  02 00 83 7e 16 00 75 71  |@|...rN....~..uq|
000000a0  66 83 7e 24 00 74 6a 8b  46 1c 8b 56 1e b9 03 00  |f.~$.tj.F..V....|
000000b0  49 40 75 01 42 bb 00 7e  e8 90 00 73 2a b0 f8 4f  |I@u.B..~...s*..O|
000000c0  74 21 8b 46 32 33 d2 b9  03 00 3b c8 77 43 8b 76  |t!.F23....;.wC.v|
000000d0  0e 3b ce 73 3c 2b f1 3b  c6 77 36 03 46 1c 13 56  |.;.s<+.;.w6.F..V|
000000e0  1e eb cd 73 2c eb 49 66  81 be 00 02 52 52 61 41  |...s,.If....RRaA|
000000f0  75 cc 66 81 be fc 03 00  00 55 aa 75 c1 66 81 be  |u.f......U.u.f..|
00000100  fc 05 00 00 55 aa 75 b6  83 7e 2a 00 77 03 e9 ef  |....U.u..~*.w...|
00000110  02 be 80 7d fb ac 98 03  f0 ac 84 c0 74 17 3c ff  |...}........t.<.|
00000120  74 09 b4 0e bb 07 00 cd  10 eb ee be 83 7d eb e4  |t............}..|
00000130  be 81 7d eb df 33 c0 cd  16 5e 1f 8f 04 8f 44 02  |..}..3...^....D.|
00000140  cd 19 00 00 00 00 00 00  00 00 00 50 52 51 91 92  |...........PRQ..|
00000150  33 d2 f7 76 18 91 f7 76  18 42 87 ca f7 76 1a 8a  |3..v...v.B...v..|
00000160  f2 8a 56 40 8a e8 d0 cc  d0 cc 0a cc b8 01 02 cd  |..V@............|
00000170  13 59 5a 58 72 09 40 75  01 42 03 5e 0b e2 cc c3  |.YZXr.@u.B.^....|
00000180  03 18 01 27 0d 0a 49 6e  76 61 6c 69 64 20 73 79  |...'..Invalid sy|
00000190  73 74 65 6d 20 64 69 73  6b ff 0d 0a 44 69 73 6b  |stem disk...Disk|
000001a0  20 49 2f 4f 20 65 72 72  6f 72 ff 0d 0a 52 65 70  | I/O error...Rep|
000001b0  6c 61 63 65 20 74 68 65  20 64 69 73 6b 2c 20 61  |lace the disk, a|
000001c0  6e 64 20 74 68 65 6e 20  70 72 65 73 73 20 61 6e  |nd then press an|
000001d0  79 20 6b 65 79 0d 0a 00  49 4f 20 20 20 20 20 20  |y key...IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 80 01  |SYSMSDOS   SYS..|
000001f0  00 57 49 4e 42 4f 4f 54  20 53 59 53 00 00 55 aa  |.WINBOOT SYS..U.|
00000200




```


Keep in mind, I did have my external HDD plugged in when I ran the script (it's labeled "My Passport") I hope that doesn't throw off some of the information for you.  If I need to, let me know and I can run the script again with the drive unplugged.

---

### Post by darkod on 2012-01-28
It looks fine except it seems there is no bootloader on the MBR of sda:
Testdisk is installed in the MBR of /dev/sda.

You can use either the vista install dvd if you have one, to repair the boot process (not to install vista one more time). Or you can write generic mbr with lilo if you have no vista dvd.

From ubuntu live mode do:
sudo apt-get install lilo (the computer needs to be connected to internet)
sudo lilo -M /dev/sda mbr

It will show a warning about lilo config files, it's normal. Just continue and it will work fine.

The boot flag is correct on /dev/sda2 and after you install the generic mbr just restart without the ubuntu cd and vista should load.

---

### Post by justgrant2009 on 2012-01-28
I don't have a vista boot disk, so I ran LILO like you suggested. I typed exactly what you put. But I didnt get a warning like you said I would, instead it just told me the mbr was updated (this was displayed almost immediately) so I then reboot the machine, but got the exact same windows boot manager error about winload.exe.

---

### Post by darkod on 2012-01-28
Well, unfortunately in that case it seems the file is not missing but is corrupt.

I am not sure if any winload.exe from another vista would work if you copy it, or not. I have never tried it.

PS. At least your data should be readable to copy it and make a backup. Then you could use the recovery partition to do a factory restore. But that usually means overwriting all your data and programs, so you will need to install the programs again too.

---

### Post by justgrant2009 on 2012-01-28
Haha, well, since I have all our files backed up, allow me to be your guinnea pig. I'll let you know the outcome.

---

### Post by Quackers on 2012-01-28
If you re-run the bootscript and post the new results it will tell us if the lilo install went properly.
Also which drive is set to boot first in bios?

---

### Post by justgrant2009 on 2012-01-28
I'll try the boot info script again for you.  Also, I don't know how to check which drive is set to boot first in the BIOS, if you tell me, I'll check.  And I tried to copy a winload.exe from another machine (albeit a windows 7 machine, but I made a backup of my original, just in cas) and the same error occured.

Also, I went to try and just install windows xp over the entire hdd, since I'm about to give up on recovering vista (again, I don't have a vista disk, but I do have an old XP that's not in use).  But when I try to install XP it tells me that windows did not detect a hard disk drive (at all). And only lets me reboot the machine from there.

---

### Post by Quackers on 2012-01-28
duplicate post

---

### Post by Quackers on 2012-01-28
To see which hard drive you are booting from you should enter your pc's bios. It's normally done by pressing a specific key just as the boot process starts.
The key can be the del key, or sometimes F2. There are many keys. Your manual will tell you. Alternatively you could google it for your hardware.

EDIT I thought you had recovered Vista once already? You say you have no recovery discs?

---

### Post by justgrant2009 on 2012-01-28
Nope, no recovery disks, and no I never recovered Vista before. The laptop came with it on it, and it's always been on it.

Here's what boot info script gives me now.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Lilo is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

hda: ___________________________________________________________________________

    File system:       iso9660
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x45606843

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048     3,074,047     3,072,000   7 NTFS / exFAT / HPFS
/dev/sda2    *      3,074,048   608,464,895   605,390,848   7 NTFS / exFAT / HPFS
/dev/sda3         608,464,896   625,141,759    16,676,864   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/hda                                                iso9660    Ubuntu 8.04.2 i386
/dev/loop0                                              squashfs   
/dev/sda1        DA1C4F001C4ED763                       ntfs       TOSHIBA SYSTEM VOLUME
/dev/sda2        BA4C7E6B4C7E21F5                       ntfs       SQ004732V03
/dev/sda3        4484A48084A475D8                       ntfs       HDDRECOVERY

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /media/SQ004732V03       fuseblk    (rw,nosuid,nodev,noatime,allow_other,blksize=4096)



```

I'm going to check the BIOS now for you.  What specifically am I looking for?  I think I know, but I'm just double checking as always.  Man, you guys are working so hard to help me, I wish I could fly ya'll to Texas and buy you each a steak and some beers... Thanks!

---

### Post by Quackers on 2012-01-28
Did you unplug your second drive?
Lilo is installed in the MBR of sda so I see no reason why it shouldn't now be booting.
There is a recovery partition on your hard drive (/dev/sda3). This can normally be accessed by pressing a key at boot. It can be F10 or F11 or something else.
Check with your pc's maker for the correct key to press. On pressing that key the recovery console will appear. That console may or may not have an automatic repair function. If it does you could try that.
If it doesn't you should still be able to recover your Windows system, but that will bring it back to the state it was in on the day you bought it. ie everything will be lost (all data and updates etc etc).

---

### Post by justgrant2009 on 2012-01-28
For 1, when I checked the Bios, I'm booting from 
HDD1: TOSHIBA MK3252GSX-(S1)

HDD2 is blank (no name). Then my next option is the optical drive.

As far as recovery, I'm fine with that, but upon boot, it does show the Toshiba booting screen and at the bottom, my only two options are F2 for BIOS or F12 for multi-boot options.  When I enter multiboot options, I only get to boot from HDD1, Optical, or LAN.  I don't see anything about picking another boot partition.

---

### Post by darkod on 2012-01-28
> **justgrant2009 said:**
> 
Also, I went to try and just install windows xp over the entire hdd, since I'm about to give up on recovering vista (again, I don't have a vista disk, but I do have an old XP that's not in use).  But when I try to install XP it tells me that windows did not detect a hard disk drive (at all). And only lets me reboot the machine from there.

XP doesn't have sata drivers by default and it will not be able to "see" any sata HDDs. You can either use a floppy with the drivers during the install, or change the sata port mode in BIOS to IDE. XP should be able to see the disk in IDE mode. Note that this will mean the disk will work little slower, the sata AHCI mode is generally faster than IDE.

---

### Post by Quackers on 2012-01-28
There will be a key to press to access the recovery partition. It won't be the same as the bios or boot options one.
What is your exact hardware please?

---

### Post by Quackers on 2012-01-28
Doing some googling it appears that on some Toshibas at least there is a "hotkey". On those systems you turn off the machine and remove all peripherals/discs etc. Then after a few seconds you press and hold the 0 (zero) key and press the power button. The recovery console should then start up.

see here
[http://aps2.toshiba-tro.de/kb0/HTD7C02140000R01.htm](http://aps2.toshiba-tro.de/kb0/HTD7C02140000R01.htm)

---

### Post by justgrant2009 on 2012-01-28
Ok, So I checked online about booting into HDD recovery mode.  It's a Toshiba Satellite.  I hold the 0 (zero) key during boot up.  It takes me to a screen offering to restore Windows Vista, but when I select to do so, it takes me back to the same windows boot manager error screen where it tells me winload.exe is corrupt or missing.

Darko, if I change the hard drive mode in the bios to IDE, can I switch it back to SATA after a windows 7 upgrade from XP?

---

### Post by Quackers on 2012-01-28
It seems then that something is wrong with your recovery partition as well. And you never made a set of recovery dvd's it seems. It's the first thing I do when I get a new system. It can save a lot of heartache, not to mention expense.

Incidentally I have heard of people using a replacement winload.exe file and getting their system back. Obviously it should be from a system the same as yours. What happened to your winload.exe I can't imagine.

---

### Post by darkod on 2012-01-28
> **justgrant2009 said:**
> Ok, So I checked online about booting into HDD recovery mode.  It's a Toshiba Satellite.  I hold the 0 (zero) key during boot up.  It takes me to a screen offering to restore Windows Vista, but when I select to do so, it takes me back to the same windows boot manager error screen where it tells me winload.exe is corrupt or missing.

Darko, if I change the hard drive mode in the bios to IDE, can I switch it back to SATA after a windows 7 upgrade from XP?

You can change back anytime you want, but windows doesn't play nice with that change. In other words, I don't think so.

Because you are talking about upgrade from XP to 7 I don't know how it will react, but I know this (tried on my own PC):
If you install Win7 in IDE mode, and you go into bios and change to AHCI, it doesn't boot.
On the other hand, my ubuntu was also installed in IDE mode, after the change to AHCI it works fine.

So right now I am waiting for a good opportunity to reinstall win7 from scratch, and will change it to AHCI before the install.

---

### Post by justgrant2009 on 2012-01-28
> **Quackers said:**
> It seems then that something is wrong with your recovery partition as well. And you never made a set of recovery dvd's it seems. It's the first thing I do when I get a new system. It can save a lot of heartache, not to mention expense.

Incidentally I have heard of people using a replacement winload.exe file and getting their system back. Obviously it should be from a system the same as yours. What happened to your winload.exe I can't imagine.
I dunno, but I did try another winload.exe but it was from a Toshiba Satellite running windows 7.  

If I change the BIOS to read my HDD as IDE so that I can just install windows XP, will I be able to change it back to SATA later when I upgrade to 7?

EDIT: Nevermind, Darko replied before I submitted to post.  So at this point, really my only option is to just set to IDE and install XP and live with it that way.  When I upgrade to 7, do you think it'd be safe to try switching it back, and if it doesn't work, switch back to IDE and just deal with it.  And how do I switch it, since that sounds like my only option right now...

---

### Post by justgrant2009 on 2012-01-28
Ok, nevermind again. I've set it to Compatability and XP recognized it. I'm installing xp now, and will try switching things up after using the windows 7 upgrade. 

Thank you both for all your support and really great help. This community is the best when it comes to friendly and helpful members. Although we weren't able to fully recover my machine, we were at least able to recover all my files, and for that I am incredibly thankful. 

Thank you Darko, and Thank you Quackers.
I look forward to further communications with you. I'll continue to keep you both informed about any progress I have at least with switching from AHCI back to SATA. Take care, friends.

---

