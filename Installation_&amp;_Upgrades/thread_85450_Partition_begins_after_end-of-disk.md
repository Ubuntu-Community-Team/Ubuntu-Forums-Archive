---
title: "Partition begins after end-of-disk"
date: 2005-11-02
forum: Installation &amp; Upgrades
---

### Post by aaichert on 2005-11-02
I have had Ubuntu installed on a 4GB Partition in order to test it. Its the best Linux I have ever seen, so I decided to make a fresh install of the new version to a 9GB Partition. I also have WinXP SPII installed and I used it in order to copy the files from a 5GB partition in order to delete both the 4 and 5 GB Partitions to use the free space for a new ubuntu installation.:smile: 

I rebooted and used the Ubuntu CD to begin the setup. My Computer crashed at some point when setting up the new partitioning. Funny thing is that the bootloader and Ubuntu still work fine and stupid WinXP just won't find any partitions on my hd. I don't know if the installation failed because of the problem or if it caused it. But please somebody help.

I have valuable information on one of the drives that I cannot so easily back up

heres some information about my System:
Laptop P4 3.1GHz
hda1: 60GB drive

here's what happens when I run sfdisk:

22:13:53 ::aaichert:: ~$ sudo sfdisk -d /dev/hda
Password:

sfdisk: read error on /dev/hda - cannot read sector 117210240
# partition table of /dev/hda
unit: sectors

/dev/hda1 : start=       63, size= 51102702, Id= 7, bootable
/dev/hda2 : start= 51102765, size=  7116795, Id=83
/dev/hda3 : start=117210240, size=4281569086, Id= f
/dev/hda4 : start= 58605183, size= 45206847, Id= c

this is my partition table as it used to be.
when I run cfdisk it will say

FATAL ERROR: Bad primary partition 2: Partition begins after end-of-disk

I did not dare to try Microsoft chkdsk yet.:mad: 


Anybody any Idea?

---

### Post by paddyg on 2005-11-03
i've got a couple of questions----if you haven't sorted your problem out in the meantime

1. how have you organised your disk?
2. can you boot anything (win, ubuntu)?

---

### Post by az on 2005-11-03
Did you partition with a windows partitioning tool?

They do not work as well as GNUparted.  Even installing windows on top of an Ubuntu install confuses the heck out of it.  You need to wipe the partition table for the windows installer to make heads or tail....

---

