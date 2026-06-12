---
title: "Triple Boot; XP, Edgy, and Dapper server?"
date: 2006-10-25
forum: Installation &amp; Upgrades
---

### Post by RRS on 2006-10-25
Windows was a mess, so I reinstalled. Hey, it came with the machine and I've got room so may as  well have it available.

So anyway I partitioned the rest of the drive to install Edgy with seperate root and home partitions.

I've been meaning to try using a server install and then add X to experiment with building a minimilist type using Ice, flux, or something along those lines. I also created a partition to use for this.

So, my questions are;
1> Should I install the full (w/gnome) Edgy or Dapper Server first?
2>Can I share Home between the two or will that create more problems then its worth?
3>What do I have to do to configure Grub properly?

I've been doing some searching and have only come across seperate bits and pieces of info, usually directed towards another final goal.

Any guidance and suggestions would be appreciated.

Also, there's no data at risk, only my sanity.
 
Thanks :-?

---

### Post by RRS on 2006-10-27
Burning Edgy to a cd now. Any advice or warnings before I install tomorrow night would be appreciated.

Thanks.

---

### Post by God Of Atheism on 2006-10-27
Warning: The text below contains mostly guesses, educated guesses, but nonetheless, follow this advice at your own risk.

1. I don't think it matters what you install first. I think grub in both versions can recognize the other version of the OS.

2. You can share home, but it might cause problems. The best bet is probably to share home, but use different usernames initially and check whether things go awry if you create the same user for the other system (with the same administrator permissions). There is always a chance it won't work properly, since the some of the settings stored in home for one system can be incompatible with the other. In this way you can try to see if things work, and, if not, still have two working systems. For different usernames it should not cause any trouble.

3. I don't think you need to do a lot to configure grub. Grub should recognize the presence of the other OS and automatically (with confirmation by you) configure itself properly during installation.

Another thing to take into account is the partitioning. I assume you intend to have five primary partitions:

1. Dapper root
2. Edgy root
3. Home
4. Swap
5. Virus XP

(or in any other order)

Now if you have only one harddisk you run into trouble, since you can only have four primary partitions. However, unless you have very little memory, you might not need the swap partition. If you have two or more harddisks then you're fine, and I suggest adding another, fat32, partition to exchange data between windoze and the ubuntus, unless you feel you don't need to exchange data. Ubuntu can read from ntfs, but writing, while possible with some added packages, is still risky. Windoze can not use ext3, although there does exist some freeware package to enable dealing with ext2/3 from windoze (however, I advice against using this for writing, since it does not support the journaling abilities of ext3). Of course you can try other file systems for ubuntu, in which case your chances of being able to read it from windoze decrease even further (unless you use fat32, which I advice against because of speed or lack thereof)

Good luck

---

### Post by RRS on 2006-10-27
Thanks.

I've created an extended partition for the 3rd OS, an ext3 to share data, and swap.

I've used [EXT2 IFS]("http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm") for sharing data between windows and an ext3 partition on other machines.

Glad to hear I shouldn't have any problems with Grub.

You're likely right about sharing /home, probably won't try.

---

