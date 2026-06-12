---
title: "I give up, my install is dead...now what..."
date: 2007-11-04
forum: Installation &amp; Upgrades
---

### Post by Hagar55 on 2007-11-04
I started with 7.04 and upgrade to 7.10.
Everything was OK, then I altered my usplash.conf to try and fix long boot up and everything went down the toilet...see this topic I started :ubuntuforums.org/showthread.php?p=3698618

Now I got into recovery mode and used MC to alter the mentioned file....diden't help.

By now I'm giving up and would try a fresh install.
Only problem is when I boot using my fresh and new 7.10 Live CD all is not well.
When it boots it shuts down the screen, most of the time I just wiggle the mouse or tap a key and everything appears again (looks like the screen goes into hibernation when with the splash screen and stays there).
But sometimes I only have the keyboard and the mouse doens't want to work (logitech MX610 USB wireless).

Now I have to say the Kubuntu CD works flawlessly....the Ubuntu one seems to be a bit buggy.

How do I install Ubuntu again and force it to use the partitions I used for the original install.
That is a thirs harddrive on SATA (two others on IDE wich contain WinXp ...WICH MUST SURVIVE AT ALL COSTS !!!).

I already saved everything in the Home partition so there isn't anything that I cannot stand losing.

Help is deeply needed.

---

### Post by gpilkay on 2007-11-04
I do the double-drive trick too, to avoid any XP problem, but frequently, IDE drives seem to the install area of choice for Ubuntu.  What you could try is disconnect the Windows drives during the install, then manually add them to Grub later.  In my own system, two IDE hard drives each boot XP or Ubuntu, with Linux as master and XP as Slave.  However, my computer's also rather old.  I do recommend using a wired muse and keyboard during install, it will greatly simplify your troubles.

I'm afraid I don't now enough about partitioning to help with that, though.  partedmagic.com has a great Live-CD that can make them, though.

---

### Post by Vn Tutor on 2007-11-04
The Ubuntu Installer allows you to customize existing partitions on your hard disks. So, when you are asked to partition your disk, like this

1. Guided - resize the partion and use the freed space
2. Guided - use entire disk
3. Manual

I think you can select the third option to customize what you want.

---

### Post by Hagar55 on 2007-11-05
I was planning on using the manual option, this is the point where I get lost.
I want to use the partitions already used by my broken install to put the new one on.

Only problem is I don't know how to tell the installer to do so (I don't understand how to put the correct mount points in.
/dev/hda1 ntfs  /media/hda1 is the windows partion wich contains Xp
/dev/sda2 ext3 /media/sda2 was the root partition
/dev/sda3 ext3 /media/sda4 was the home partition
/dev/sda5 swap was the swap partition

This is the information I get when I choose the manual install (there are a buch of other ntfs and Fat32 partitions but they don't kneed to change.

The installer tells me to :You need to specify a partition for the root file system (mount point "/") with a minimum size of 2 GB, and a swap partition of at least 256 MB. You may also set up other partitions if you wish.
What do I change from there on to install Gutsy sucessfully on these partitions.

Will it change the Grub installer on itself or should I do anything about that as well ?

---

### Post by bulldog on 2007-11-05
> **Hagar55 said:**
> I was planning on using the manual option, this is the point where I get lost.
I want to use the partitions already used by my broken install to put the new one on.

Only problem is I don't know how to tell the installer to do so (I don't understand how to put the correct mount points in.
/dev/hda1 ntfs  /media/hda1 is the windows partion wich contains Xp
/dev/sda2 ext3 /media/sda2 was the root partition
/dev/sda3 ext3 /media/sda4 was the home partition
/dev/sda5 swap was the swap partition

This is the information I get when I choose the manual install (there are a buch of other ntfs and Fat32 partitions but they don't kneed to change.

The installer tells me to :You need to specify a partition for the root file system (mount point "/") with a minimum size of 2 GB, and a swap partition of at least 256 MB. You may also set up other partitions if you wish.
What do I change from there on to install Gutsy sucessfully on these partitions.

Will it change the Grub installer on itself or should I do anything about that as well ?

Not so hard to do actually :)
Choose manual partition and when you see your partitions,mouse klik the one you want to use for the root partition.
A new screen appears,look trough the options,take as mount point / set the bootflag [just klik] and set it to format.
Do the same with the home partition,BUT mount it as /home,if there is valuable info on the partition DON"T format and don't set the boot flag.
Swap should be set for itself but to be sure you can mount it as swap no bootflag and set it to format.
Your windows partitions should be left alone,they should be automounted by ubuntu in the /media folder,make sure you didn't set them to format by accident!!
If done and all is as you wish,write it to the hdd and ubuntu will apply your changes.

More info you can find here:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

---

### Post by Hagar55 on 2007-11-05
First problem is I don't see a bootflag anywyere.
I can choose mountpoint "/" or "/boot"
When I change this one and the one from the home partition in "/home" and then try to go to the next screen I get an error message saying (roughly translated from Dutch):
No base file system defined, please correct this from the disk menu.

---

### Post by bulldog on 2007-11-05
I'm Dutch too so I should understand :)
Well if memory is not too old to remember the details........
When you come to partition your hdd,you should see all your existing partitions.
You should select the one you want to use for the / [root] file system and choose next.
You get a new page with some options,there should be a drop down menu at the end of the mount point line,here you can choose where to mount it [/ is recommended]
One of the other options should be 'set bootflag yes / no' ,just click on this one and it should be changed from no to yes.
Then look for the format line,default is no,click it and it should be yes.

Don't be afraid,there's nothing happening in this stage,ONLY WHEN YOU CLICK APPLY CHANGES TO DISK,it will be carried out,if you don't do this,you can click around to explore.

---

### Post by Hagar55 on 2007-11-05
I'm afraid it only is getting more weird from here on...
I tried altering the partitions with the partitioning tool in the Live CD.
Unfortunately it kept crashing when it was done with a task (like deleting a partition).

So I booted with a separate disk containing Gparted.
I deleted both the old root and Home partition and made new ones. Both  formatted as ext3, and the one which I want to become the root set the "boot" flag.
No errors this time so I booted using the live Cd with Ubuntu 7.10 again.
Choose install, went to the manual option and noted the mounting point for the root partition as "/" and "/home" for the other one.
When I choose next I get two errors:
First one :The information sector has the wrong signature (0). Select cancel for now, and send in a bug report. If you're desperate, it's probably safe to ignore.

When  I choose ignore I get the next one :File system is reporting the free space as 0 clusters, not 1322378 clusters.

Now those two got me a little nervous because I don't understand them.
So for now I haven't gone any further and would like some more help....that is if there is anyone who can make something of this.

---

