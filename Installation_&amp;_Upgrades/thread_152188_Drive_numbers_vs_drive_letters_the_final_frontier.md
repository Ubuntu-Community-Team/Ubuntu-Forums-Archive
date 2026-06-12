---
title: "Drive numbers vs drive letters: the final frontier"
date: 2006-03-29
forum: Installation &amp; Upgrades
---

### Post by joeuser1 on 2006-03-29
Help me folks!

I'm trying to install Breezy on a Celeron machine with an install CD. But I'm not making any progress because I don't know which of the hda-s is my F: drive that I've emptied and defragged for Ubuntu. The 'partition disk' part lists the drives as hda1, etc. (My guess is that it's hda7)

I've installed the old Mandrake, RH 8, and Fedora Core 4. But this one is tough and seems risky! How do I go about this? Please help!

This is urgent 'cos I've been looking forward to this for too long :)

Joe

---

### Post by taurus on 2006-03-29
The first HD is known as /dev/hda, /dev/hdb for second, /dev/hdc for the third and so on, assuming you have an EIDE harddrives...

---

### Post by ispmarin on 2006-03-29
Do you know the size of the partitions? If you know, you can do a 
df -h
and sees the sizes of the partitons, and figure out the numbers. If you are in windows, the things become more complicated: on the installation process, sees when the partitioner runs the sizes and try to figure out who is who. If you don't know the sizes, try using on linux the gparted or in windows something like paragon partition manager or even the disk manager from windows (don't remember where it is, it's been a long time...)

---

### Post by ispmarin on 2006-03-29
Yes, just like taurus said, if they are different disks, the tip from taurus is a good one. But if the partitions are on the same disk, try to do what I said. hope it helps!

---

### Post by randomity on 2006-03-29
(I'm assuming some version of windows xp and that you have only one hard disk)

Windows assigns drive letters fairly randomly, and they rarely have any relation to the actual location of the drive (which hard disk, which partition, etc). To figure it out, go to Start->Run and type compmgmt.msc and go to Disk Management. Find the disk entry corresponding to your hard disk. It will have a number of rectangles indicating partitions, one of which should be C: and one of which should be F:. Count from the left, starting at 1, to find which disk you're looking for. Some PC's have a small recovery/diagnostics partition at the start of the disc which won't have a drive letter. It should also be counted to figure out which disc is which. Your drive F: should then be hda<number from left>. Write down the size of this disk and check that its right when the installer shows you the list of partitions.

Incidentally, defragging F: was a waste of time. Defragging cleans up the windows filesystem into a more efficient state. To install Ubuntu, the installer will have to wipe the windows filesystem on F: and install a linux filesystem.

---

### Post by joeuser1 on 2006-03-30
How typically nice of you! Anyway I couldn't find out the number of the F drive with the left-to-right technique. I should have given you more details. However, I downloaded the Live CD version and found out that hda7 was indeed the F drive. I'll be installing Breezy tomorrow.

The Live CD version didn't automatically show /mnt/windows in Nautilus. I'd like to know if I have to edit the fstab file after installing it. May be the Live CD has this limitation of not mounting the other partitions?

Thanks a lot for your help!

Diwakar
India

---

