---
title: "Does this look right? (End Of Install)"
date: 2007-08-01
forum: Installation &amp; Upgrades
---

### Post by noneedforwindows on 2007-08-01
Last screen of the install. I already had a ext2 partition and a swap partition. I am very scared to finalize this! Couple years ago I lost all my files when trying another distro. My Wife will kill me if it messes up! I have 1 HD win XP on NTFS. Second Partition is FAT32. Then the Ext2 followed by Swap, then a little unallocated. I believe that the 4 of them are primary. I used a linux live cd partition tool (cant think of the name of it right now)

this is the text from the last screen

 Language: English
 Keyboard layout: U.S. English
 Name: 
 Login name: harrington
 Location: America/Toronto
 Migration Assistant:
 Windows XP Media Center Edition (/dev/sda1):


If you continue, the changes listed below will be written to the disks.
Otherwise, you will be able to make further changes manually.

WARNING: This will destroy all data on any partitions you have removed as
well as on the partitions that are going to be formatted.

The following partitions are going to be formatted:
 partition #3 of SCSI6 (0,0,0) (sda) as ext2
 partition #4 of SCSI6 (0,0,0) (sda) as swap

---

### Post by link2zelda on 2007-08-01
I've had data loss with ext2 when not shutting down properly each and every time.  But ext3 is great, no problems.  With ext3, although I shouldn't do it, I just hit reset quite a bit with no data loss at all.  Some help to convert if not re-installing [http://www.troubleshooters.com/linux/ext2toext3.htm](http://www.troubleshooters.com/linux/ext2toext3.htm)

To answer your question, I would make sure to choose the manual method for partitioning, as I always want to protect my NTFS drives as well. Make sure the NTFS and FAT32 partitions are mounted as /media/xyz  The ext2 partition should be mounted as / (formatting it is recommended)  When using the manual method just be sure that the NTFS and FAT32 partitions are NOT being formatted (NO CHECK) and you'll be fine.  But the warning is the step that will format the partitions.  I think you may even be able to install linux on the ext2 without formatting it (if you had some data on there that you wanted, but it should be backup up anyway) using the manual method by removing the check.

---

### Post by merlinus on 2007-08-01
>  The following partitions are going to be formatted:
 partition #3 of SCSI6 (0,0,0) (sda) as ext2
 partition #4 of SCSI6 (0,0,0) (sda) as swap


Looks good to me.  partition #1 is windows, #2 is fat.

I would agree with the previous poster, however, and format #3 as ext3.

But if something goes wrong, don't tell your wife it's my fault!

:biggrin:

-merlin

---

### Post by kdrumm on 2007-08-01
[COLOR="Navy"][SIZE="2"]I have nothing of value to add. It's hard to push that partition button. [COLOR="Red"][SIZE="3"]
JUST DO IT.[/SIZE][/COLOR]
Took me a while but i'm glad I did[/SIZE][/COLOR]

---

### Post by noneedforwindows on 2007-08-05
Everything went great, I love ubuntu, who needs windows besides playing a few games! Ext 3 worked great too. Thanks for the help!!!

---

