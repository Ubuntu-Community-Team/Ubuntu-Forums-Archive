---
title: "Mounting a partition for /home"
date: 2006-06-12
forum: Installation &amp; Upgrades
---

### Post by StandardDeviant on 2006-06-12
Hello all, I managed to get a dual boot install of XP and Ubuntu working perfectly, and I've been trying to fix it up a bit to make life easier.  I've got the following partitions:

/dev/sda1 (Windows)
/dev/sda2 (Ubuntu root)
/dev/sda3 (Extended partition)
   /dev/sda5 (Linux swap)
   /dev/sda6 (fat32 for documents to share between the 2 OS's)

When I had Breezy, I would just edit fstab and mount /dev/sda5 to /home/mdrogers/documents (after creating the /documents folder), and through some kind of magical poking-around managed to edit the permissions so I could write to it.  However, I was thinking it might be easier to just mount /dev/sda5 to /home, thereby creating a file structure that Ubuntu sees as /home/mdrogers and that Windows would see as D:\mdrogers\.

Unfortunately, the theory does not extend into the real world... Is it possible to have it set up this way, or is it not possible to mount a fat32 partition to /home?

I didn't have much data on the computer and it's all backed up anyway, so if there's a better way to arrange the partitions then I can just start from scratch, so don't hold back any suggestions ;)

---

### Post by taurus on 2006-06-12
First of, /dev/sda5 is your swap partition so you cannot mount it anywhere except as a swap partition!!!  Then, it is NOT a good idea to create /home as fat32 because of the permissions stuff.  If you want to share files between ubuntu and windows, create a partition with fat32 filesystem and mount it somewhere like /share.  In other words, /home needs to be at least ext3 (or ext2 or other Linux native filesystem).

---

### Post by StandardDeviant on 2006-06-12
Gah, I meant /dev/sda6 between the 2 OS's.  And okay, the not being able to mount a fat32 as /home is what I thought, thank you!

---

### Post by taurus on 2006-06-12
If I were you, I would make my partition table to look something like

/dev/sda1 (Windows)
/dev/sda2 (Ubuntu root--ext3)
/dev/sda3 (Extended partition)
/dev/sda5 (Linux swap)
/dev/sda6 (/home--ext3)
/dev/sda7 (/share--vfat)

---

