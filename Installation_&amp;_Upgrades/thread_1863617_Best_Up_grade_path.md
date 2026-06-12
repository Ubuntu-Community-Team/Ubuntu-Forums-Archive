---
title: "Best Up grade path"
date: 2011-10-18
forum: Installation &amp; Upgrades
---

### Post by SteveTyrer on 2011-10-18
About one year ago i installed Ubuntu on my Dell Vostro 1500 laptop, as duel boot with Windows XP just to see what Ubuntu is like, I am pleased to say that over the 12 months i no longer use Windows XP and am  exclusively a Ubuntu user :)

The question is I need more space for Ubuntu do I

1/ Change the partition size and reduce Windows space on the HD
2/ Do a complete new installation of Ubuntu 11.10 and remove Windows completely

Any help will be much appreciated

---

### Post by mue.de on 2011-10-18
Hello,

my first enthusiasm was about the same, but i wouldn't throw windows away!
You can reduce the needed amount of space for windows by repartitioning -beware of your data!-
First you should defragment the win-Partition, then you can use GParted to change the partition-size.
For that you should alwas boot with an ubuntu-live-cd so that the system on harddisk isn't used

---

### Post by Mark Phelps on 2011-10-18
First of all, seeing the large number of posts on the forum related to 11.10 install and upgrade problems, I would NOT remove Windows and HOPE that an install of 11.10 would be OK.

If you really want to upgrade, then burn a CD, boot from that, and see how well that works -- before you remove anything.

Just in case you might want to have XP back, for that, I suggest you download and install the FREE version of Macrium Reflect, image the Windows XP install off to an external drive, and create the Linux Boot CD for MR.  This will allow you to restore it later -- if needed.

If you just remove the XP partition, that's liable to hose up GRUB; so instead, just reformat it and use it as a data partition.

---

### Post by SteveTyrer on 2011-10-18
Thanks Mue and Mark for the help you have both given me something to think about :p

Taking what you both have advised I think I will take the safe option and keep XP for now
and reconsider my options when the next long term support version of Ubuntu is out.

Thanks again Steve

---

