---
title: "Installation - prepare recovery/back-up disk"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by pol50 on 2009-11-22
Linux 2-6-31-14 Ubuntu 9.10 recently installed on Sony vaio notebook, double op.sys installed in two partitions, launched by grub.
A problem still remaining, help needed from the community experts:
1- Does it exist a programme to prepare a bootable disk (cd/dvd) to automatically restore my ubuntu installation "as it is", including the installed programmes and the current set-up (modems, ip, preferences and grub included)? I means, in case of need, I would insert my bootable (linux o.s. rel. ubuntu 9.10) cd/dvd, that also contains the currently installed programmes and the actual set-up and preferences, and automatically restore this stored status. Does it exist a restore/back-up programme/application that allow to prepare such a recovery disk? 
Or, where can I found a procedure by terminal commands (tar, etc..) to do the above? 
It should be a well tested and safe step-by step procedure (for dummy user), un-ambiguos and clear. The problem is that, if something does not work or is not applicable to my configuration, I will discover it if I have a fatal fail and when it is needed to restore a previously working scheme/installation (too late!).
Some community expert can please help me for point 1, 2 or 3? Tnk a lot.  Pol50

---

### Post by darkod on 2009-11-22
[www.clonezilla.org](www.clonezilla.org)

They have bootable CloneZilla CD image that you can boot with and image your whole drive to an external drive for example. It supports ext4, ext3 and ntfs partitions and only images the data used part, not the whole partition saving you space and time.

---

### Post by pol50 on 2009-12-02
Thanks a lot Darkod, I'm going to inform on CloneZilla and I'll try to prepare a restore/backup disk in this way. 
The fact that it supprts ext3, ext2, and nfts should mean that is applicable to my double op-sys with grub, may you confirm it?
The fact that it work only on wrote sector should mean that it also provide back-up of the partitions (not just a disk-bootable op-system), so I could be able to restore the same status as below, including programmes and archive data and the related set-up; may you please confirm the above?
Enjiy your life and your IT sys
        pol50 from Italy

---

### Post by darkod on 2009-12-02
Yes, it is applicable to both windows ntfs paritions and linux partitions. It can backup all partitions that you want to back up. Basically you get what is called image of the partition(s), of your whole system.

---

### Post by pol50 on 2009-12-03
Hello Darko,
thanks a lot, following your confirmation, I'm now proceeding
Also if not finished, all the info are now available and the post received answer, it is considered closed,:D  tnk again
      pol50

---

