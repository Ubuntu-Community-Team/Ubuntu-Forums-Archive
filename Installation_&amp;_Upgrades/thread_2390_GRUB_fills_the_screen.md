---
title: "GRUB fills the screen"
date: 2004-10-27
forum: Installation &amp; Upgrades
---

### Post by Satellite on 2004-10-27
Apologies if this has been asked before but I've just installed Ubuntu and after 2 attempts I have hit the same problem both times.

I am installing on a PC with XP pro installed with 2 hard disks, I first installed to some free space I had on the first hard disk (as a logical drive which I was dubious about having success with) then tried again with a primary partition (again on the first disk) ... both unfortunately give the same results.  On first boot after installation completes (after GRUB installation) the screen fills with the word GRUB and does nothing else!

I really need to get this working in order to get back into my XP installation.  I will be forced to do a fdisk /mbr to fix the master boot record and return to booting XP only if I can't find a fix.  Any ideas?

Thanks in advance

Satellite

---

### Post by Satellite on 2004-10-28
I have managed to get my XP install booting again with an fdisk /mbr and then re-setting the active partition in fdisk.

I still have Ubuntu installed therefore and wondered whether I could boot into it and perhaps load Grub into /boot rather than the MBR (I don't have a dedicated /boot partition though, just the standard / and swap that it auto created).  Can I do this?

Any success stories with XP dual booting that can point me in the right direction?

Just for reference my partitions are rather odd just to make things more complicated -

#1 primary 5.3GB ntfs
#5 logical 16.2GB ntfs
#6 logical 509.9MB swap
#3 primary 26.2GB ext3
#4 primary 31.5GB ntfs

Thanks in advance.

Adam

---

### Post by rthrbelsewhere on 2005-12-21
Belive it or not, i'm having that very same problem.  Loading on an Intellistation M Pro server with 6 18gb drives and 1 30gb ide drive.  I've installed twice, tried different configurations, nothing has worked....Except - having only the one ide drive installed, no scsis involved.

Back to Google....

;)

---

