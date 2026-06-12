---
title: "Any plans for a right click format option for flash drives etc?"
date: 2009-07-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by snargfish on 2009-07-25
It's one little thing that has always annoyed me with Ubuntu. Would it be hard to implement such an option?

---

### Post by kingborel on 2009-07-26
+1

I'm ok with dropping to the terminal to mkfs.ntfs -f or whatever, but less technically minded people would have no clue. This has been severely lacking for a long time.

---

### Post by philcamlin on 2009-07-26
i wish they would put this in :popcorn:

ah well i dont mind using gparted :D

---

### Post by Nburnes on 2009-07-26
This would be pretty nice..........:D

But Gparted really isn't bad either.

---

### Post by snargfish on 2009-07-26
> **Nburnes said:**
> This would be pretty nice..........:D

But Gparted really isn't bad either.

Yeah but even Windows XP has right click formatting.

---

### Post by Ravernomina on 2009-07-26
well we could beat the crap out of windows if he had had the option then give a list of all the formats like on Gparted Super formating or what :)

---

### Post by JohnJackson on 2009-07-26
I think [gnome-format]("http://www.phoronix.com/scan.php?page=article&item=gnome_format") has been suggested for this, it is in universe. It was discussed in the [Jaunty forum]("http://ubuntuforums.org/showthread.php?t=1034510").

---

### Post by amano on 2009-07-26
Nope. Gnome-format is already deprecated as Felix Kaser stated. The new gnome-disk-utility (g-d-u) is the new way to go. It should come with the new devicekit-disks by David Zeuthen. Isn't it installed by default already??

---

### Post by 23meg on 2009-07-26
> **amano said:**
>  Isn't it installed by default already??

No, it's in Universe.

---

### Post by Gina on 2009-07-26
I agree, it would be very useful. 

It would also be nice to have formatting (or at least deleting all files, if format is already OK) in the USB Startup Disk Creator.

---

### Post by pelle.k on 2009-07-26
I disagree that the option to *format* should be in the right click menu. It's too specific. A more general term like "Manage this drive", or what have you, would be better IMHO. Even more so when it's about an action that is not likely to be used on a daily basis.
Gparted would be perfect for this.
Of course, that wouldn't be as newbie friendly. Personally i don't want ubuntu to be more newbie friendly. Just more elegant.

---

### Post by Gina on 2009-07-26
Why not make Ubuntu newbie friendly??  Surely the idea is to make Ubuntu as user friendly as possible?  If you don't like "newbie friendly" or "user friendly" there are other distros that are less user friendly!

I think there should be something other than GParted for formatting USB sticks.  GParted should be left separate for doing risky things with hard disks.  The ability to do the same with any sort of USB drive is fine but I think there should be a USB stick formatter separate from GParted and NOT able to destroy your OS.

---

### Post by vishalrao on 2009-07-26
I'm not sure if you can DIY with GNOME like I did with KDE for a similar thingy: [http://forum.kde.org/viewtopic.php?f=83&t=40090](http://forum.kde.org/viewtopic.php?f=83&t=40090) :D

Any links/tutorials for how to add a right-click menu item in Nautilus which runs your own command?

---

### Post by 23meg on 2009-07-26
> **Gina said:**
> Why not make Ubuntu newbie friendly??  Surely the idea is to make Ubuntu as user friendly as possible?  If you don't like "newbie friendly" or "user friendly" there are other distros that are less user friendly!

For the sake of argument, and not exactly pertaining to gnome-disk-utility: giving people more and/or easier ways to do things is not the necessary definition of being "newbie friendly". Explicitly choosing not to give people semi-automatic weapons (such as formatting tools) with which they can shoot themselves in the foot by default, or choosing not to make them easily accessible, can be an equally "newbie friendly" attitude, since you wouldn't want users losing data due to accidental uninformed use of such tools.

---

### Post by wayne_cat on 2009-07-26
> **vishalrao said:**
> I'm not sure if you can DIY with GNOME like I did with KDE for a similar thingy: [http://forum.kde.org/viewtopic.php?f=83&t=40090](http://forum.kde.org/viewtopic.php?f=83&t=40090) :D

Any links/tutorials for how to add a right-click menu item in Nautilus which runs your own command?

maybe with a nautilus-script:

[http://g-scripts.sourceforge.net/faq.php](http://g-scripts.sourceforge.net/faq.php)

edit: or nautilus-actions

---

### Post by aamukahvi on 2009-07-26
[install nautilus-actions]("apt://nautilus-actions") 

Add an action named "Manage hard drives", icon gtk-harddisk.
Click Edit, then edit the profile "Main".

**Action**
Path: gksudo /usr/sbin/gparted
or gnome-disk-utility or whatever

**Conditions**
filename: *.drive

**Advanced Conditions**
add scheme "computer"

Note1: this will just start gparted, not preselect the hard drive. Maybe there is a way to pass the drive id to gparted?
Note2: only works for items in "Computer"
Note3: This entry will also appear for the CD drive.

---

### Post by pelle.k on 2009-07-26
> **Gina said:**
> Why not make Ubuntu newbie friendly??
Maybe i should elaborate some more on what i meant. I guess the term "newbie friendly" is too general, and misleading anyway.
The "easiest" option is not so often the most elegant, nor dynamic one. You have to weigh in the practicality of the mechanism in question. In this case a more general option such as "manage this drive" is quite descriptive, while not being overly simplistic. It probably caters better to most scenarios, since it covers a larger range of options, that may not be used very often, vs *one* option that may not be used very often.
I'm not saying "dont make ubuntu newbie friendly", i'm trying to say don't simplify things too much.

> **Gina said:**
> Surely the idea is to make Ubuntu as user friendly as possible?  If you don't like "newbie friendly" or "user friendly" there are other distros that are less user friendly!
I'm not very elitist, even if i may at times sound as such. I'm simply trying to point out the impracticality of "dumbing thing down" to the point that they are indeed, *very* easy too use, while not being very practical in the large scale of things.
There are other "advanced" distros out there, i know that. I do think ubuntu strikes a good balance, in that regard, for the most part though.

> **Gina said:**
> I think there should be something other than GParted for formatting USB sticks.  GParted should be left separate for doing risky things with hard disks.  The ability to do the same with any sort of USB drive is fine but I think there should be a USB stick formatter separate from GParted and NOT able to destroy your OS.
Fair enough! This is a good point actually. +1
If we could have gparted isolate the actual drive in question (starting gparted with the actual drive as an argument isn't good enough, since you can change that in gparted anyway) would be optimal, **IMHO of course**. ;)

---

### Post by dirtylobster on 2009-07-27
I've always missed this feature.

---

### Post by hugmenot on 2009-07-27
Guys, rejoice! This comes to you via Nautilus gdu extension. It has been there for quite a while.

EDIT: I just realized you have to install gnome-disk-utility for this. Why is this not depended on by ubuntu-desktop?

---

### Post by inportb on 2009-07-27
> **Gina said:**
> I think there should be something other than GParted for formatting USB sticks.  GParted should be left separate for doing risky things with hard disks.  The ability to do the same with any sort of USB drive is fine but I think there should be a USB stick formatter separate from GParted and NOT able to destroy your OS.

Data seem to be of primary importance to most people, above the OS and other executables. One could easily repair or reinstall software, but lost data are lost data. Removable disks tend to carry some of the most critical information, so it would be particularly risky to have an easy format button for drives on such disks.

On the other hand, a destroyed OS could be restored.

---

### Post by kaitwospirit on 2009-07-27
I'd say that we do need something other than gparted, which can nuke your drive, there for formatting USB sticks and things like that. However, I don't think I want to just right-click and go straight to format. 

An accidental click would be the far more common occurance for me, and I imagine quite a few users, than actually wanting to reformat USB media (a task I think I have done one time in the past five years). Assuming that an accidental click does not lead to immediate data loss, it would still be annoying because an accidental click would lead to a lot of loading, which could render slower systems unusable for awhile.

---

### Post by Reiger on 2009-07-27
Ehrm, am I Captain Obvious Ignorance here or does any tool that has the potential to rewrite the meta information on a harddisk (which is essentially what re-formatting is) the tool to nuke the logical structure of the device, thereby making it inoperable?

In other words, is a right-click-to-nuke-this-device option on a flash drive not equally "dangerous" as firing up GParted and clicking "option-to-nuke-this-device" after selecting the flash drive...

---

### Post by hugmenot on 2009-07-27
Hey guys, please look at my last post. Your theorizing is obsolete now.

---

### Post by hugmenot on 2009-07-27
> **Reiger said:**
> Ehrm, am I Captain Obvious Ignorance here or does any tool that has the potential to rewrite the meta information on a harddisk (which is essentially what re-formatting is) the tool to nuke the logical structure of the device, thereby making it inoperable?

In other words, is a right-click-to-nuke-this-device option on a flash drive not equally "dangerous" as firing up GParted and clicking "option-to-nuke-this-device" after selecting the flash drive...

Well, you can always have bugs, you know. But all the tool would get, when it is a simple formatter, is a device handle to the partition. And it can mess it up as much as it wants, the partition table is not part of it. So no way to "brick" a partition

---

### Post by wayne_cat on 2009-07-27
> **hugmenot said:**
> Hey guys, please look at my last post. Your theorizing is obsolete now.

Thank you for this tip!

gnome-disk-utility should definitely be a part of the standard installation.

---

### Post by amano on 2009-07-27
Hmm. Shall we file a bug for that?

---

### Post by wayne_cat on 2009-07-27
> **amano said:**
> Hmm. Shall we file a bug for that?

is it a bug? ... hmmm .. I think it is something for the "feature requests"

edit:

[http://brainstorm.ubuntu.com](http://brainstorm.ubuntu.com)

---

### Post by Regenweald on 2009-07-27
As i saw this thread I thought, Is Palimpsest aka Gnome-disk-utility not what they are asking for ? It's been in fedora by default with their last release and is in karmic for testing. It will probably be in Karmic final. Test away. 

Also, with the nature of our filesystems, a right click options to format a flash may not be the best idea. Ext3/4 file removal is final.Don' be too eager to frak your portable drives.

---

### Post by BCurtisWX on 2009-07-27
> **amano said:**
> Hmm. Shall we file a bug for that?

Go ahead, and PM me.. I will take care of moving it to wishlist and getting the higher up people to notice it.

---

### Post by 23meg on 2009-07-27
Suggestions for changing defaults are best posted to the ubuntu-devel-discuss mailing list, [not as bug reports]("https://help.ubuntu.com/community/ReportingBugs#When%20not%20to%20file%20a%20bug").

---

### Post by Levitation on 2009-08-02
Deleted - wrong forum

---

### Post by phenest on 2009-08-02
> **Regenweald said:**
> Also, with the nature of our filesystems, a right click options to format a flash may not be the best idea. Ext3/4 file removal is final.Don' be too eager to frak your portable drives.

But I'm guessing it'll ask for a password first? Not something you could do accidentally if so.

---

### Post by GeorgeVita on 2009-09-29
... as 9.10 beta comes, 'right click FORMAT' tool: **gdu-format-tool**

- does NOT ask for a password
- by default formats to: compatible for all systems (FAT) meaning FAT32
- and mixes (?) FAT32 with FAT16 on a preformated FAT16 USB memory

My test:
- attach a FAT16 formated USB memory (I used a 2GB kingston DTmini)
- run Disk Utility to check that it is FAT16 (attachment fat16usb)
- close Disk Utility
- right click on USB memory icon, and 'Format'
- format it with the default 'FAT' selection
- (!) [TWO file browsers will appear]("https://bugs.launchpad.net/bugs/427006"), close them
- run again Disk Utility to see the FAT16/FAT32 mode (attachment FATedUSB)

As I know FAT32 and FAT16 are similar but different file systems.
Is above OK and I am just missing a technical point?

Thanks for any idea,
George

---

### Post by hugmenot on 2009-09-30
> **GeorgeVita said:**
> 
As I know FAT32 and FAT16 are similar but different file systems.
Is above OK and I am just missing a technical point?

Thanks for any idea,
George

There is no reason to use FAT16. Does FAT16 even support filenames longer than 8.3?

---

### Post by GeorgeVita on 2009-10-01
> **hugmenot said:**
> There is no reason to use FAT16. Does FAT16 even support filenames longer than 8.3?

I agree but now I am testing, and this program seems to format in a mixed/messed mode. If FAT16 is no longer supported must be removed or 'forced' to FAT32 after a descriptive message.

Using gdu-format-tool and disk utility we can notice a lot of 'new definitions' some times more accurate some other 'loosy':

gdu-format-tool: compatible for all systems (FAT)
disk utility has many FAT16s and FAT32s

G

---

### Post by hugmenot on 2009-10-01
Well, probably the guy writing the simple, user-friendly formatting tool saw no reason to include all options available in the advanced, experts&#8217; tool, which might be confusing and lead to problems. Like, for example, offering file systems that only support partitions smaller than 2GB. Right?

What is the problem? And, what are you saying is lossy?

---

### Post by GeorgeVita on 2009-10-01
> **hugmenot said:**
> What is the problem? And, what are you saying is lossy?

I am using small USB memory sticks for creation of Ubuntu LiveUSBs, which sometimes are FAT16 formated (by default). Running gdu-format-tool (right click on mem icon) you can use the 'compatible for all systems (FAT)' and the result is as shown at my [2nd attachment]("http://ubuntuforums.org/attachment.php?attachmentid=130204&d=1254260371")

Disk Utility shows on left window: 2.0 GB FAT (32-bit version)
at right: FAT (32-bit versio) File System
Partition 1 (FAT16 (0x06)) /dev/sdb1 mounted at...
as shown into Type field: FAT16 (0x06)

My 'confusion': Is the memory stick formated to FAT32 or FAT16?

>>> EDIT: reported as [https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/440500](https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/440500)

Thanks,
George

---

