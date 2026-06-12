---
title: "How much room for Ubuntu?"
date: 2005-11-29
forum: Installation &amp; Upgrades
---

### Post by shane2peru on 2005-11-29
Ok, I'm dual booting XP and Ubuntu.  I alreadh have it installed by have to re-install Ubuntu.  (I destroyed Gnome--User error ;) )  Ok, so I want XP and Ubuntu to **share** some of this harddrive.  I only have one drive.  I have 8Gig to divide for Ubuntu. **1.** How much will Ubuntu need for the program itself (i.e. filesystem), and how much for /usr.   **2.**Also will the /usr side be visible to XP (of course it has to be formated in FAT), if not, **3.**what else do I need to make this work?  I'm open for suggestions.  I really like Ubuntu, and would like to use it, but am required by my work to keep XP so this is my compromise.  Thanks!

Shane

---

### Post by Xian on 2005-11-29
[QUOTE=shane2peru]How much will Ubuntu need for the program itself (i.e. filesystem), and how much for /usr. [/QUOTE]
From the Install Guide: [Minimum Install Requirements](http://archive.ubuntulinux.org/ubuntu/dists/breezy/main/installer-i386/current/doc/manual/en/ch03s04.html).

---

### Post by shane2peru on 2005-11-29
Great ok, looking at about 2 gb for filesystem.  Any ideas on the /usr  can this be formatted as FAT32, and will XP see it?  Is this where all my files will be? or do I need a /storage  ?  or something.  I'm a little confused on this part.  Thanks.

Shane

---

### Post by akiro.yamamoto on 2005-11-29
Actually I thing you can mount it under /usr...
However the more typical place is under /media/
All you have to do is set the correct permissions for that (FAT32) partition .
XP will be able to access it as normal and Ubuntu will do so as well..
If you need Help Tyr the link in my sig..
:smile:

---

### Post by SickTwist on 2005-11-29
[QUOTE=shane2peru]Great ok, looking at about 2 gb for filesystem.  Any ideas on the /usr  can this be formatted as FAT32, and will XP see it?  Is this where all my files will be? or do I need a /storage  ?  or something.  I'm a little confused on this part.  Thanks.

Shane[/QUOTE]

You will need at least two partitions for Ubuntu: The root partition ( / ) and a swap partition. The root partition should **not** be formatted as FAT32 as that filesystem cannot store permissions and is inefficient. Use EXT3 (the default filesystem) or ReiserFS for the root partition. Neither of these is able to be read or written from Windows. The root partition is the one that needs to be at least 2 GB for a default Ubuntu install. You may need more space if you plan on installing more programs.

The swap partition will server as virtual memory. You will not need to pick a filesystem for this partition. Windows will not be able to read or write here either. Make this partition about twice the size of your RAM but no greater than 1 GB.

It's a good idea to create a third partition for /home. This is where all the user data will be stored including program settings, bookmarks, etc. If you ever need to upgrade/reinstall Linux, this partition does not need to be erased and you can retain all your user data. EXT3 or ReiserFS are good filesystems to use for this as well.

If your Windows partition is not currently FAT32, you may wish to create another partition explicitly for sharing data between Windows and Linux. You should use FAT32 to format this partition because it is the only stable solution for reading and writing from both Windows and Linux.

---

### Post by shane2peru on 2005-11-30
Great!  Thanks for the info.  Sounds like I should go with this`setup:

1   /               ext3            2.5GB
2   /swap        default         500MB
3.  /home        ext3            3GB
4.  /storage     FAT32          2GB


That may not be the right order, but that is the idea.  Thanks for all the input was very helpful!

Shane

---

### Post by shane2peru on 2005-11-30
Ok, I did as stated above and now I can't access hda1 in the media.  That is the one listed as FAT32 It is a read system only.  How can I fix this?  Thanks.

Shane

---

### Post by Xian on 2005-11-30
1. You can access it as admin with this command:
$ sudo nautilus

- or - 

2. Change the options line entry in /etc/fstab and remount. 
defaults,umask=0002

---

### Post by shane2peru on 2005-12-01
[QUOTE=Xian]
- or - 

2. Change the options line entry in /etc/fstab and remount. 
defaults,umask=0002[/QUOTE]
Xian,

I didn't attempt number 1.  But number 2 didn't work for me.  I even rebooted and nothing.  Someone else pointed me here:  [http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

This was a simple tutorial that fixed my problem, I wanted to share incase other's needed it. Thanks though!

Shane

---

