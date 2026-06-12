---
title: "No Disk Space?"
date: 2007-10-05
forum: Installation &amp; Upgrades
---

### Post by dare dukes on 2007-10-05
Hi.  I just installed Feisty yesterday on my brand new work laptop.  Tried to install Open Office 2.3 and it said I don't have sufficient disk space.  What's up?

Also, when folks install ubuntu, do they generally uninstall the old windows files?

Thanks for your help.

Dare

---

### Post by becominglumberg on 2007-10-05
How much did you let Ubuntu allocate to your linux file table, and how much did you leave windows? Also, did you separate out your home partition?

---

### Post by dare dukes on 2007-10-05
all excellent questions.  and I haven't the slightest idea.  I indicated that the partition should be 75%, if that means anything to you.  I'm very new to all this.  I basically just did what the install program told me to do.  I wasn't worried about losing anything, since I backed up what very little was on there.

Is there a way to find out how i partitioned the disk?

---

### Post by ajgreeny on 2007-10-05
From ubuntu enter sudo fdisk -l in a terminal and you will get an output showing your various partitions on the disk.  Windows will have one, two or three partitions usually, depending on the setup of the laptop, and all will normally be ntfs, though they may be fat32 or vfat.  Ubuntu will have just two partitions if you used the default as you say, though one of them will be the swap partition and is usually enclosed in an extended partition.

Copy the output of that command and we should be able to help further if you can't understand what it all means.  And welcome to ubuntu; enjoy!

---

### Post by dare dukes on 2007-10-05
thanks.  that's all greek to me.  but i'm willing to learn.  Here's the output from that command:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       13995   112414806   83  Linux
/dev/sda2           13996       14252     2064352+   5  Extended
/dev/sda3   *       14253       14593     2739082+  83  Linux
/dev/sda5           13996       14228     1871541   82  Linux swap / Solaris
/dev/sda6           14229       14252      192748+  82  Linux swap / Solaris

---

### Post by becominglumberg on 2007-10-05
That doesn't seem like the output of a machine that was previously running windows, unless you let the installer delete windows from your system.

---

### Post by dare dukes on 2007-10-05
Well, let me back up.  What I described earlier was what happened the second time I ran the install.  The first time I told it to allocate 100% of the disk for the install (that was an option).  I figured wiping windows off the hard drive was no big deal, since I have the disks and the computer's pretty much brand new.

so where do I go from here?  Do most people keep windows (or OSX) on their hard drives as some kind of back up?

---

### Post by ajgreeny on 2007-10-06
Whether people keep their old win or mac files and filesystems is totally up to them, most probably start dual booting so they still have a system they know and can use straight away without too much trouble.  It looks as if you only have linux on your system with two distros, though that may be as a result of two installs of ubuntu.  Does grub menu show just one or more OSs to boot?  If you don't see a grub menu hit esc when you see the words "starting grub" and a menu should appear.

In a terminal enter:- ```
df -h
``` and post the output again. This will show us which partition is your current ubuntu and the exact sizes of the partitions related to that in MB terms, so much more understandable than block etc as shown in fdisk -l.  Similarly the command ```
mount
``` will tell you which partitions (actual and virtual) are mounted and the top one will be the current OS partition.

---

