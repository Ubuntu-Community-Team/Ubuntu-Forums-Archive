---
title: "Best format for the /boot partition"
date: 2008-10-29
forum: Installation &amp; Upgrades
---

### Post by zuheyr on 2008-10-29
Hello,

I will certainly want to add other versions of Ubuntu in the future.
Therefore, I understand it is a good idea also to create a separate boot partition.

I will use dual booting with Ubuntu and Vista.

In all the documentation I could search, I could not see what is the best format for the /boot partition? I saw ext3, also jfs?

In another document the recommended size of the /boot is at most 15GB and I will follow the advice.

Many thanks for reading (and for your patience).

Regards, Zuheyr

---

### Post by tompickles on 2008-10-29
/boot I have personanly heard is ext2 about 100mb........ think i read that with gentoo.

---

### Post by zuheyr on 2008-10-29
My apologies thank you!!

It is the / that is 3-15 GB. The recommended /boot is 100-250MB.

The ref is: [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

Unfortunately (s)he does not mention what format for the beginners...
 
Many thanks and excuses.
Zuheyr

---

### Post by dabl on 2008-10-29
100MB is plenty of space, format ext2.

This is a few years old, but still accurate:

[http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html](http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html)


One challenge you will face is the limitation to 4 primary partitions on a hard drive.  I believe Vista requires two, and with a separate /boot partition (which needs to be a primary), Linux is going to need three partitions.  :(

Best bet, I think, would be to let "/" and swap be on logical partitions within an extended partition.  :)

---

### Post by zuheyr on 2008-10-29
Dear Dabl,

Thank you very much. 

May I please ask how to do that, putting the swap and the "/" to be on the same logical partition within an extended partition? Partitioning sort of scares me as there is no room for error here and my understanding of the subject is limited at best. 

Many thanks, regards, Zuheyr

---

### Post by mikeweston on 2009-05-20
> **dabl said:**
> 100MB is plenty of space, format ext2.

I wish that was true for me. I am trying to upgrade from 6.06 LTS to 8.04 LTS (yes, the end-of-life clock on 6.06 is starting to tick loudly), but the upgrade aborts saying that it needs at least 105MB of free space on /boot, which is currently 100MB total. So even if I could delete everything there, it woudn't be quite big enough.

It doesn't seem immediately obvious how to expand /boot since the swap partition comes right after it.

Any suggestions?

This is x86 64-bit, in case it matters.

---

### Post by logos34 on 2009-05-20
> **mikeweston said:**
> 
It doesn't seem immediately obvious how to expand /boot since the swap partition comes right after it.

Any suggestions?

This is x86 64-bit, in case it matters.

Delete swap and make a new one at the end of the disk/after root partition.  Then expand /boot into the empty space.  (use Gparted on the ubuntu live cd or GParted live cd). Remember to edit /etc/fstab, as well as reinstall grub [edit]

The only other way would maybe be to move /boot back on / partition. (just reverse the process [here]("http://tekguru.wordpress.com/2007/09/04/howto-moving-boot-to-its-own-partition/"))

---

### Post by mikeweston on 2009-05-20
Since swap was relatively big compared with the additional space needed for /boot, I actually shrank swap a little so I could expand /boot. And that worked. I had a few glitches during the upgrade, but it seems to be fine at the moment.

Thanks for the help. If I decide to change things more radically later, I'll have a better idea where to look.

---

### Post by logos34 on 2009-05-20
> **rstu132 said:**
> Do not be so Lazy! Just add as much as you can at here![http://www.nikeshoxr4.net](http://www.nikeshoxr4.net)[Puma shoes](http://www.nikeshoxr4.net/puma-shoes.html)[Nike Air Max TN](http://www.nikeshoxr4.net/nike-air-max-tn.html)[Nike Shox R3](http://www.nikeshoxr4.net/nike-shox-r3.html)[Nike Air max 95](http://www.nikeshoxr4.net/nike-air-max-95.html)

Why didn't we think of that?

---

