---
title: "Ubuntu looking for deleted partition? Mystery?"
date: 2006-05-09
forum: Installation &amp; Upgrades
---

### Post by nomadic on 2006-05-09
I'm using Ubuntu 5.10, fully up to date.

Using Gparted I deleted a partition (sda9) - this was a Debian partition and was not part of Ubuntu.
I also formatted an unused windows partition sda3 (under windows) to ntfs - was raw. This speeds up image copy. It was not being used by Ubuntu.

Now when loading up Ubuntu, I get two errors

error 1
- e2fsck.ext3: bad magic number in super-block while trying to open /dev/sda3. The superblock could not be read and does not describe a correct ext2 filesystem.

The install carries on and this error seems to have no effect.

error 2
- e2fsck.ext3: No such file or directory while trying to open /dev/sda9. The superblock could not be read and does not describe a correct ext2 filesystem.

By pressing control / D the install carries on and this error seems to have no effect.

Ubuntu (and everything else on my machine) seems to be working fine.

Can anyone explain please why Ubuntu
 i) seems not to recognise sda3 as ntfs (it has no problem with sda2, which is the XP partition. It had no problem with sda3 when raw).
 ii) is looking for sda9, which is deleted.

nomadic

---

### Post by louis_nichols on 2006-05-09
You have to reflect these changes in fstab too. Erase the reference to the deleted partition and, for the re-formatted one, change fstype to ntfs.

EDIT: typo

---

### Post by nomadic on 2006-05-09
Louis nichols
Many thanks - that fixed the problem. Item closed.
Question: Does that mean that every time I make a change to a non-Ubuntu partition I have to update Ubuntu's /fstab?
Nomadic

---

### Post by Irony on 2006-05-09
Any time you make a change to any partition (Ubuntu or otherwise) you need to change the fstab file.

---

### Post by Shay Stephens on 2006-05-09
Thank you for the information.  I just wound up with the same problem.  And this info helped me to fix it.

It does seem that the partition program should handle this or at least give a warning that fstab needs changing.

---

### Post by louis_nichols on 2006-05-09
[QUOTE=Shay Stephens]Thank you for the information.  I just wound up with the same problem.  And this info helped me to fix it.

It does seem that the partition program should handle this or at least give a warning that fstab needs changing.[/QUOTE]


I think this is a matter of Linux philosophy. The fstab is  not updated because the user might not want it to be, for various reasons. It might be related to security, to what users have access to it, or driver availability...

For example, ntfs read support is very good at this point, but writing is still experimental. So, a piece of software can't update the fstab because it doesn't know wether the user wants it read-only or wants to experiment writing to it.

I'm not sure these are the reasons, but it never bothered me very much. I mean, one doesn't change the partition table of a hdd very often, so manually editing the fstab after such a change is no big deal.

---

### Post by nomadic on 2006-05-09
Thanks again for the info. I can see the rationale for it. And it is no big deal to update it.

nomadic

---

### Post by louis_nichols on 2006-05-10
Oh, just remembered!!! (should anyone still be interested)

Ubuntu has this tool under System>Administration called disks. It does pretty much the same thing that editing the fstab does, it's just that it's a GUI. I guess, after you get used to one method, it's hard to get used to others... Anyways, some of you might be interested in it. I haven't really tried it, as I said, so i don't exactly know all its features and capabilities, or if it has shortcomings.

---

