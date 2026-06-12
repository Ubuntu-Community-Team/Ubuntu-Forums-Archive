---
title: "Xubuntu and Windows 98 SE dual boot"
date: 2008-07-07
forum: Installation &amp; Upgrades
---

### Post by racie on 2008-07-07
Hello.  I'm new to all things Linux and I wanted to install Linux on a Windows 98 SE as a dual-boot, so the files aren't lost.  I was told I needed partition whatever-you-call-it, so I downloaded Cute Partition Manager.  I burned the ISO to a disk, but when I try to boot it on Windows, nothing but a black screen comes up.  It doesn't let you type or anything.  I asked a question on Yahoo Answers and someone told me that usually Linux does the partitions for you.  Can someone please help?  Thanks.:biggrin:

***EDIT!* There's a new problem, the above one has been resolved.  Please scroll down to my fourth post to see the problem.**

---

### Post by avtolle on 2008-07-07
OK, first, you would boot the CD from the CD drive, after being sure your BIOS is set to boot from it. You do not boot it from Windows. 

Assuming no errors in the iso file and the burning was successful, the CD should boot (if your machine can boot from CD). Now, then, how much RAM is on your computer? I ask this because to run the Live (Desktop) CD, 384 mb RAM is required.

EDIT: Having reread your post, the problem is with the partitioner and not the Ubuntu Live CD? Is the partitioning program bootable?

EDIT2: OK, now that I reread again, I see that you are trying to go with Xubuntu. The RAM requirements to use the "Live" CD are lower than on Ubuntu (256 mb as I recall). This computer is likely an older one, so the Alternate CD is likely to be a better choice for you than the Live CD (you end up with a full installation, but as it is text based, fewer resources are needed for the installation).

---

### Post by racie on 2008-07-07
Oh, wait I didn't explain it clear enough.  I didn't install Xubuntu yet because I was told that I need the to do something with the paritions.  I downloaded Cute Partitioning Manager and burned THAT to an ISO file.  I wanted to know if Xubuntu will automatically set the partitions, or if I need to use Cute Partitioning Manager first.  Also, Cute Partitioning Manager didn't work when I turned on the computer.

---

### Post by avtolle on 2008-07-07
OK, I understand a bit better. So, is Cute Partition Manager bootable? And, can you boot from a CD on your particular computer? 

BTW, the Xubuntu CD will see the partitions. So, what I suggest is before doing anything else, defrag the HDD twice, maybe thrice, to clean it up. Then, if your computer can boot from CD, boot the Xubuntu CD; at step 4, IIRC, there will be a discussion of partitioning. What you want is to shrink the Windows partition, and then partition the space created. I think the Guided Partition (use largest available space) would be your best option. Be sure to NOT say "use entire disk". Good luck.

---

### Post by racie on 2008-07-07
K, thanks.  I'll report back later on how it went.

---

### Post by racie on 2008-07-07
Okay, I did everything... partitioned the hard drive, blah, blah, blah, installed Xubuntu, BUT I restarted the computer when it was done like it said to and Xubuntu won't run!!  Instead, Windows 98 starts up... I even pressed F1, went into the settings, and changed the current OS to "other," rather than "windows 98" and Xubuntu still doesn't start up.  What the heck is going on???

---

### Post by HotCupOfJava on 2008-07-07
I'll make a suggestion - try doing it again. Your Xubuntu live CD should have the GNU Partition Editor on it (gparted). Run the live CD, then click "Applications">"System">and you should then see a utility called "partition editor". This is the one you want. You can use it to resize or delete existing partitions to create free space to install Xubuntu on. (If you have already installed Xubuntu, you may wish to delete that partition and start over). Before doing such an operation, you might want to run the Windows Disk Defragmenter several times in a row (even if it says you don't need to). This will help reduce the risk of any data on the Windows filesystem being accidentally deleted by the partition editor. Once you have created your free space, reinstall Xubuntu and choose the option "guided - use largest contiguous free space". Once installation is complete and you restart, you should get an option for which OS you boot with. Note that the first time you boot in Windows after the partitioning, Windows may wish to "examine" the filesystem for errors. Let it do it.

---

### Post by racie on 2008-07-07
There's only one problem with that.  The computer runs so slowly that the partition editor that comes with Xubuntu freezes the computer when you try to use it.  I had to use a different partition editor called GParted.  It worked perfectly and everything.  The only problem is when the computer starts up.  Is there anything else I need to change in the settings when the computer starts?  (When you press the F1 button.)

---

### Post by HotCupOfJava on 2008-07-07
OK - try this: Load your installation CD again, and choose "Other Options" (you may have to press F6 to do this - it is the first screen where you see the Xubuntu logo). Xubuntu should then display the "boot options" line. Use the arrow keys to go to the end of the line. With the cursor positioned after the space following the two hyphens at the right end of the line, type "single" and press <ENTER>. Xubuntu should then boot in recovery mode w/out mounting any hard drives. You will see the "#" prompt. 

give the following command: "parted /dev/hda print". If that doesn't do anything try each of the following: "parted /dev/sda print", "parted /dev/hdb print", or "parted /dev/sdb print". One of these should display a list of partitions, one of which will have a boot flag. If the Filesystem marked "boot" is FAT32 or NTFS, that is the Windows partition. You may have to use GParted to make the Linux partition (usually ext2 or ext3 filesystem) a "boot" partition. Hopefully you won't have to manually mount the partition and edit grub.........

---

