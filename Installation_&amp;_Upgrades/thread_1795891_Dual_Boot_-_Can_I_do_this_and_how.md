---
title: "Dual Boot - Can I do this and how?"
date: 2011-07-03
forum: Installation &amp; Upgrades
---

### Post by Julian1968 on 2011-07-03
Hello

My laptop currently runs Ubuntu 10 alone but I need to put Windows XP on and dual boot for occasional web design and graphics needed for the same.

Can I Install Windows alongside Ubuntu now or do I need to wipe clean and start again?

Also. Can I have both operating systems on my laptop but have my hard drive partitioned in a way that both Ubuntu and Windows can access it.. I want this to store Images, music and video which can then be accessed by my fave programs in Ubuntu or Windows?

If I can do this, how do i go about it please?

Thanks

---

### Post by Sef on 2011-07-03
1) > Can I Install Windows alongside Ubuntu now or do I need to wipe clean and start again?

a) Either, but Windows need to be on the first partition.

b) If only installing Windows, then you will need to reinstall GRUB after installing Windows.

2) > Also. Can I have both operating systems on my laptop but have my hard drive partitioned in a way that both Ubuntu and Windows can access it.. I want this to store Images, music and video which can then be accessed by my fave programs in Ubuntu or Windows?


a) Yes, set up a separate partition to save your data on.

b) Use NTFS as the file format for the data partition.

3) Back up your data before attempting anything.

---

### Post by Julian1968 on 2011-07-03
Thanks Sef

May sound silly but how do I reinstall Grub?

---

### Post by oldfred on 2011-07-03
I agree with all of Sef recommends, except windows does not have to be sda1. It likes to be first and does seem to work better on some systems if it is on sda not sdb when you have two drives.

Windows really just has to be on a primary NTFS partition - sda1 thru sda4 with the boot flag. The standard windows MBR boot only checks for active (boot flag) primary partition. Windows definition of primary is bootable.

So if you have a primary partition left, you can create a NTFS format and put the boot flag on it. Then the XP installer should see it and install. Your NTFS shared partition can be a logical partition in the extended partition as windows reads from logical, just does not boot from logical partitions.

---

