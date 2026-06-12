---
title: "Ubuntu installation in dual boot mode with previous Windows installation"
date: 2005-05-10
forum: Installation &amp; Upgrades
---

### Post by spanishwasabi on 2005-05-10
Cheers,

I've got a computer with Windows pre-installed. I am using it since a while already, and I've decided to try Ubuntu.

The thing is, I would hate to have to reinstall Windows after installing Ubuntu.
Does ubuntu have any "partition magic" equivalent tool in order to resize and create partitions? Or does it simply use any free space it finds? I would like to share a partition in FAT32 between Windows and Linux...

Thanks,

G

---

### Post by Zelut on 2005-05-10
I had the same problem when trying to share my partition with XP / ubuntu.  In the past I've manually edited the partitions using fdisk but that didn't seem to be an option in the ubuntu install.  I also noticed its either 'wipe the drive' or 'use extra space'.

Anyone have any suggestions on creating room for a ubuntu partition?

---

### Post by derrick1985 on 2005-05-10
[QUOTE=kuyaedz]I had the same problem when trying to share my partition with XP / ubuntu.  In the past I've manually edited the partitions using fdisk but that didn't seem to be an option in the ubuntu install.  I also noticed its either 'wipe the drive' or 'use extra space'.

Anyone have any suggestions on creating room for a ubuntu partition?[/QUOTE]

[http://www.sysresccd.org/](http://www.sysresccd.org/)

Use either Gparted or qtparted to edit your partitions linux style. Both are GUI based and resemble Partition Magic

---

### Post by spanishwasabi on 2005-05-10
Thanks for the answer.

I am afraid GNU parted does not work for resizing NTFS partitions. And as far as I know, Window XP is based on NTFS partitions... :-(

G

---

### Post by kosmic on 2005-05-10
[QUOTE=spanishwasabi]Thanks for the answer.

I am afraid GNU parted does not work for resizing NTFS partitions. And as far as I know, Window XP is based on NTFS partitions... :-(

G[/QUOTE]
 Windows XP can be instaled in FAT or NTFS, if your windows is instaled in NTFS the best way to resize or make new partition is to buy a comercial program like Partition Magic.

In this moment Writing to NTFS partitions from Linux is experimental and dangerous, but you can read NTFS partitions from linux with no problems

---

### Post by derrick1985 on 2005-05-10
[QUOTE=kosmic]Windows XP can be instaled in FAT or NTFS, if your windows is instaled in NTFS the best way to resize or make new partition is to buy a comercial program like Partition Magic.

In this moment Writing to NTFS partitions from Linux is experimental and dangerous, but you can read NTFS partitions from linux with no problems[/QUOTE]

I THINK qtparted can resize an NTFS partition, just make sure you do a Defrag before hand to make sure all your data ends up at the begining of the disk.

Don't quote me on this, it's been a long time since i messed with my NTFS partitions. Last time around, i just didn't use up my whole HD.

What about from Windows itself, through computer management?

---

### Post by Maestro23 on 2005-05-10
[QUOTE=spanishwasabi]Thanks for the answer.

I am afraid GNU parted does not work for resizing NTFS partitions. And as far as I know, Window XP is based on NTFS partitions... :-(

G[/QUOTE]

Quick keyword search on google (everyone should use), revealed this little bit of info:  [http://linux-ntfs.sourceforge.net/info/ntfsresize.html](http://linux-ntfs.sourceforge.net/info/ntfsresize.html)   Other results came up as well.  Will at least point you in the right direction.

Good luck man... :wink:

---

### Post by spanishwasabi on 2005-05-10
Thanks for the pointer.

I know the power of Google:
"Internet is my God and Google my Profet"
Should have used it :-)

Apparently, the answer of my initial question is in the link you gived me:

"""
Feb 24, 2005 	 Ubuntu 5.04, codenamed "Hoary Hedgehog", is the newest distribution that added support for non-destructive NTFS resizing during installation by the use Partman and ntfsresize. Here is how you can do it when the [Partitioning disks] screen appears:

   1. Choose the "Manually edit partition table" option.
   2. Choose the NTFS partition you want to resize.
   3. Choose the "Size:" line.
   4. Choose <Yes> if you are asked about "Write changes to disk and resize the partition?".
   5. Enter the new size.
   6. Please wait patiently until the resize process frees the needed space for Ubuntu installation. 
"""

With this and parted, I'll be able to reorganize my hard drive.

Thanks to everyone!

G

---

### Post by kriemer on 2005-05-12
Sorry but I'm going to ask for newbie clairification.

I gather from all this that Linux does not "see" the Windows NTFS partition on my HardDisk and that I need to partition while installing Ubuntu.

If the HD is not partitioned then Hoary Hedgehog will build a non-destructive partition?  So don't be afraid, just do it?

Sorry if I'm obtuse.

k

---

### Post by derrick1985 on 2005-05-12
[QUOTE=kriemer]Sorry but I'm going to ask for newbie clairification.

I gather from all this that Linux does not "see" the Windows NTFS partition on my HardDisk and that I need to partition while installing Ubuntu.

If the HD is not partitioned then Hoary Hedgehog will build a non-destructive partition?  So don't be afraid, just do it?

Sorry if I'm obtuse.

k[/QUOTE]

No, it can "see" and resize NTFS partitions.

In the past, it was tricky editing NTFS partitions, but now it's pretty care free. Ubuntu can resize your NTFS partition and you can make a root (/) and even a swap, if you need it.

GNUparted/qt parted, is just a GUI way of doing in, the ubuntu installation is all text install.

---

### Post by eeried on 2005-07-25
Partman is really great and full of options!

However as I didn't know the tool very well I used qtparted to resize the big C partition without destroying the hidden D part (hidden under windows but seen by ubuntu and qtparted). I used qtparted on Knoppix cd-live.

cheers,

---

### Post by kalle314 on 2005-07-26
Since I am a newbie, I am not sure i did understand everything written here.

If I understand correctly i will do like this: (please correct me)

Step 1: Defragmentation of the harddrive to be on the safe side.

Step 2: Partitioning, using "Ntfsresize" that Maestro23 mentioned above.
(or maybe partman).

I create three new partitions, called "swap", "home" and "root".  
What is the minimum size of these partitions?

Step 3 - Installation.
Will I get the following question now?

"List of partitions: 
partition#1: windows
partition#2: home
partition#3: root
partition#4: swap

Please choose your root partition."

or is it more complicated?

---

### Post by kalle314 on 2005-07-27
I found an answer to my question in another thread, where the user *not_yet* linked to this guide:
[http://www3.telus.net/linux4u/](http://www3.telus.net/linux4u/)
which was very helpful.

If you have free space on your harddrive, the installer can partition it for you. It creates a swap partition and an ext3 partition.

But what is the minimum free space before partition?

And will this take all remaining free space, so that nothing can be saved while in windows?

edit: I managed to find the answer to the first question in the forum, see the following threads: 
Disc space requirements
[http://ubuntuforums.org/showthread.php?t=42489](http://ubuntuforums.org/showthread.php?t=42489)
Space needed?
[http://ubuntuforums.org/showthread.php?t=29806](http://ubuntuforums.org/showthread.php?t=29806)
How much space?
[http://ubuntuforums.org/showthread.php?t=41417](http://ubuntuforums.org/showthread.php?t=41417)

edit 2: The second question was a misunderstanding - I thought that the installer would use all free memory in the windows partition, which was not the case.

---

### Post by thejaswip on 2007-10-19
How I have quick suggestion for the community of which i am a great fan of.
Even though the Ubuntu installer has been traditionally simple i need to point out that the installer formats the hard drive quite earlier and also writes the MBR at this time.
It would be great if we could rewrite the MBR (for grub or other boot loader ) at a later stage and simply format the hard disk so that incase the installation fails half way through and it is a dual boot system then it can still boot through.
Cheers
Tej

---

