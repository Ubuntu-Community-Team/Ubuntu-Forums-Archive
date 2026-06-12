---
title: "Moving ubuntu partition to the front of the hdd"
date: 2007-11-25
forum: Installation &amp; Upgrades
---

### Post by boast on 2007-11-25
The first half of my hard drive is a NTFS partition, and linux is the second half of the hard drive. I need a boot disk that can delete the NTFS partition and move the second partition to the front of the drive so I can expand the size.

anybody know of such utility? thanks

---

### Post by irw on 2007-11-25
The ubuntu live CD will do this - fire up the partition editor under /System/Administration, delete the NTFS partion, then move /resize the second partiotion.

one comment that cannot be repeated often enough - back up your data first!

---

### Post by ajgreeny on 2007-11-25
Gparted liveCD is the best answer to this.  Remember,however, that you may have grub installed on the MBR of windows on the ntfs partition, so you will need to reinstall grub after removing the ntfs partition and moving the Ubuntu partition backwards on the disk to the start.  The move can take a long time so be patient when you do it, and don't stop it half way through or you could be in trouble, bigtime.  Make sure you have backups of all your important personal data first, just in case.

If you need to reinstall grub have a look at the attached txt file.

---

### Post by meierfra on 2007-11-25
> grub installed on the MBR of windows on the ntfs partition,

Grub is never installed on the MBR of  the ntfs partition. 

But ajgreeny is right with his conclusion: If  you delete the ntfs partition and merge it with ubuntu partition you will have to reinstall grub and edit menu.lst.

Instead of resizing the ubuntu partition, I recommend to create to separate /home partition.

---

### Post by lobner on 2007-11-25
> Grub is never installed on the MBR of the ntfs partition. 

Grub in in the /boot-folder of the main linux partition... right? Never in the MBR of any disc.
The MBR is a table which holds partition information... ect. -> [http://en.wikipedia.org/wiki/MBR]("http://en.wikipedia.org/wiki/Master_boot_record")

---

### Post by meierfra on 2007-11-25
Grub  comes in two parts:

One part is in /boot/grub in the ubuntu partition.

The second part is usually on the MBR of the hard drive. The MBR is the first sector of the harddrive and comes before any of the partitions.   (Edit:    actually grub uses a little more than just the MBR, but stays inside the first 63 sectors, which still  come before any of the partiions) Sometimes the second part is installed to the first sector of the ubuntu partition, but then you need a different boot loader installed on the MBR of the hard drive

Edit: The last few lines of the MBR  form  the partition table. But grub will not touch the partition table. (Well, it might set a boot-flag, if you use "makeactive" in menu.lst)

---

### Post by ajgreeny on 2007-11-26
Thanks folks, I stand corrected about grub and ntfs partitions etc, but the problem will still exist if the windows partition is removed, won't it?

---

### Post by meierfra on 2007-11-26
> but the problem will still exist if the windows partition is removed, won't it?

Yes, and I said so, didn't I ?:)

> But ajgreeny is right with his conclusion: If you delete the ntfs partition and merge it with ubuntu partition you will have to reinstall grub and edit menu.lst.

---

### Post by ajgreeny on 2007-11-27
That was a retorical question!

---

