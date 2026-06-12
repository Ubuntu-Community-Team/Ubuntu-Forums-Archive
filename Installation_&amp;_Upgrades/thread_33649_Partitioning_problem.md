---
title: "Partitioning problem"
date: 2005-05-11
forum: Installation &amp; Upgrades
---

### Post by Slee on 2005-05-11
Hi,

So far, my system looks like this:
First HDD: Windows XP + Linux. Dual boot using Lilo (Mandrake 10.0).
Second HDD: 2 partitions of data

I want to install Ubuntu over the Mandrake I already have, using the already existing partitions I have on the first HDD. But the partitioning tool doesn't recognize any of my partitions on the first disk, althouth I have 3 linux partitions (1 for /, 1 for /home and 1 for swap)

Any idea?
Thanks for your help

---

### Post by alastair on 2005-05-11
On install, you can switch to a terminal using CTRL+ALT+F2 (I think it's F2) - and "hit enter" to activate.

Once you have a shell, you can use "fdisk" to list a disk's partitions e.g.

fdisk -l /dev/hda
fdisk -l /dev/hdb

(or whatever disks you have).

What does that report?

---

### Post by Slee on 2005-05-12
fdisk -l /dev/hda displays this (this is the disk I want to install on):

device                      id
/dev/hda1                 f
/dev/hda2      *          7
/dev/hda5                 83
/dev/hda6                 83
/dev/hda7                 b
/dev/hda8                 b
/dev/hda9                 82

I'd like to install on hda5 for the system, and keep my /home directory on hda6.
All this is not reported on the install screen. I only see HDA main disk.

Any clue?

---

### Post by pointym5 on 2005-05-12
The "83" you're seeing means that those are your Mandrake ext2 (or ext3) partitions.

Bring up the Ubuntu install manual partition tool.  Select hda5 and view it. Change the "Do not use this partition" to "Use this partition as ext2/3".  Tell it the mount point, and leave it at the "do not format" choice.

---

### Post by Slee on 2005-05-12
[QUOTE=pointym5]The "83" you're seeing means that those are your Mandrake ext2 (or ext3) partitions.

Bring up the Ubuntu install manual partition tool.  Select hda5 and view it. Change the "Do not use this partition" to "Use this partition as ext2/3".  Tell it the mount point, and leave it at the "do not format" choice.[/QUOTE]
 I don't see all this in the install screen.
I can only select HDA (not hda5 for instance) and install asks if I want to format it all

---

### Post by GTvulse on 2005-05-12
[quote=Slee]
 I don't see all this in the install screen.
I can only select HDA (not hda5 for instance) and install asks if I want to format it all
[/quote]

Scroll down the list. The option for manual partitioning is there.

---

### Post by Slee on 2005-05-12
Sorry for misunderstanding:
- I see the "Manual partitioning menu"
- BUT I can't choose the hda5 partition in the list. The install menu doesn't see all my partitions

/dev/hda is seen as a single partition under the install menu (whereas fdisk sees the partitions correctly)

---

### Post by pointym5 on 2005-05-12
Oh I see.  That's odd; I suspect it means that the installer's partitioning underpinnings don't understand the partition table, while fdisk does.

---

### Post by GTvulse on 2005-05-12
There is one thing you can try. You could, from within Windows XP, delete and recreate one of the partitions. 

E.g., if the Mandrake root partition doesn't contain valuable information, you could delete it and recreate it using WinXPs disk manager. This way you would repair any damage to the disk superblock and the extended partition superblock as well.

---

### Post by Slee on 2005-05-13
[QUOTE=dradul]There is one thing you can try. You could, from within Windows XP, delete and recreate one of the partitions. 

E.g., if the Mandrake root partition doesn't contain valuable information, you could delete it and recreate it using WinXPs disk manager. This way you would repair any damage to the disk superblock and the extended partition superblock as well.[/QUOTE]
 Just installed partition magic.
It says I have a problem with the HDA.
Strange though, because both WindowsXP and Linux start and run correctly.

I may have to move sensitive data on other disk, and reformat. But that's a pain, I don't want to reinstall the whole windows stuff.

---

### Post by GTvulse on 2005-05-13
*Sigh* I feel your pain. I had a similar incident less than a month ago. I had to buy a new HD in the process. Nothing to do with Ubuntu, but rather a bad jumper setting in the older HD that wouldn't let any Windows install and eventually borked the BIOS. I'm still wondering why the jumpers weren't set correctly... (I need this box to dual-boot even if I use the other OS only once every other full moon).

I notice that you are booting up from the second partition. What's in the first? I wonder if you could use the repair tools of the OS installed in the first partition to fix the MBR... That would be risky anyway you look at it. Back up first!

---

