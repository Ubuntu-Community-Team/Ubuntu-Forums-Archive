---
title: "Clean Reinstall on Dual Boot System"
date: 2008-09-16
forum: Installation &amp; Upgrades
---

### Post by trotskythehero on 2008-09-16
I have a dual boot system with Win XP on the master hard drive 8.04 on the slave. I want to do a clean reinstall of 8.04 on the system. If I remove the ubuntu partitions and reinstall from the CD what happens to the old grub file that in on the master hard disk? Do I have to delete it? If so how? Or, will the new grub file over write it? Any help would be appreciated by a gnu linux newbie since I like to have some idea what is needed or what is going to happen before a I mess with things.

---

### Post by manishtech on 2008-09-16
> **trotskythehero said:**
> I have a dual boot system with Win XP on the master hard drive 8.04 on the slave. I want to do a clean reinstall of 8.04 on the system. If I remove the ubuntu partitions and reinstall from the CD what happens to the old grub file that in on the master hard disk? Do I have to delete it? If so how? Or, will the new grub file over write it? Any help would be appreciated by a gnu linux newbie since I like to have some idea what is needed or what is going to happen before a I mess with things.
Did you make a /boot partition. If not, then your MBR would be pointing got GRUB installed in the ubuntu partition of slave hard disk. In this case just reinstall ubuntu on the slave.
I never knew that the GRUB files are stored on master hard disk. If am wrong, can anyone correct me?

---

