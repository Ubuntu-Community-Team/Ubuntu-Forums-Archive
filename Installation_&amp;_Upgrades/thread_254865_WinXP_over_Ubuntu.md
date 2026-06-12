---
title: "WinXP over Ubuntu"
date: 2006-09-10
forum: Installation &amp; Upgrades
---

### Post by davidsampson on 2006-09-10
I have Ubuntu 6.06 LTS 64-bit edition installed on my computer, and I would like to install WinXP in the unpartitioned space on my hard drive.  Currently, on the 160gb hard drive, 50 gb goes to /home, 10 gb to /, 2gb to swap, and the rest is free space.  How can I do this, with minimal impact to my ubuntu install?  All the tutorials I have read assume you have windows installed, or want to get rid of linux entirely.  Your help is appreciated.

---

### Post by jISh on 2006-09-10
Just select the unpartitioned space with the Windows installer. You shouldn't encounter any errors there.

You will, however, have problems booting your computer after. You'll have to re-install GRUB to your master boot record, which you should be able to do by loading your LiveCD, going to the terminal using grub-install.

Haven't done it before, but I believe it's
grub-install hd(0,0) #for your setup.

---

### Post by davidsampson on 2006-09-11
Well, this sucks.  XP says 3 is too many partitions, and it wont install.  I have only a /, /home, and swap, yet it absolutely refuses to install.  Is there any way to circumvent this?

---

### Post by davidsampson on 2006-09-11
EDIT: double post

---

### Post by orb9220 on 2006-09-11
I think it is because xp wants to first partition?

I installed xp first then my / /home swap and all are primary which 4 is the limit of.

You may be able to redo your swap as extended but don't know if this would solve your problem or not.

I always install xp first because it wipes out the mbr where grub resides.

---

