---
title: "Xp - Ubuntu"
date: 2007-03-13
forum: Installation &amp; Upgrades
---

### Post by needhelp101 on 2007-03-13
Hello,

After running Ubuntu (6.10) from a Live Cd this morning I have decided to upgrade to a dual booting XP.ubuntu. XP has to be installed first and I need to create a partition and then install Ubuntu onto this new partition (most of the hard disk space) and have the option to boot into XP or Ubuntu. As always help appreciated.

TIA.
needhelp101 (Adam)

---

### Post by louis_nichols on 2007-03-13
Well, you pretty much summed it up, there. :) There's nothing more that can be said about this. It's very simple: with Windows installed, just clean a partition for Ubuntu and install it there. The formatting of the partition, or lack thereof, doesn't matter, as the Ubuntu installer contains a tool to correctly format the space.

---

### Post by needhelp101 on 2007-03-13
But, how do I create a new partition in Windows? Or Ubuntu?

---

### Post by jameso on 2007-03-13
You will have to [resize your windows partition](http://www.ubuntuforums.org/showpost.php?p=2289906&postcount=2), so you have unallocated space at the end of your disk.

You can then run the ubuntu installer and create the linux partitions in this spare space.

---

### Post by needhelp101 on 2007-03-13
do i need to put a swap space in theredont i

---

### Post by louis_nichols on 2007-03-13
You don't need to set-up the swap space in advance. The installer will do this and also recommend the appropriate size for the swap partition in your case.

EDIT: typos

---

### Post by needhelp101 on 2007-03-13
I can't run the above program but can access the one that comes with ubuntu (Live CD) so can i make the changes there, if i can a guide would be useful.

---

### Post by needhelp101 on 2007-03-13
So can I make changes to my windows hdd GParted. Do i hit resize?? Will it work as ubuntu is running of of Cd??

---

### Post by enopepsoo on 2007-03-13
yes, gparted works from the livecd.  You should not multitask while resizing a partition though (I have found).

---

### Post by needhelp101 on 2007-03-13
SO all i do is hit resize. I have two showing at the min /dev/hda1 and unallocated grayed out. Do i resize the dev or unallocaed. The devis 55.8GB and un =7Mb. If I resize do I take it to about 25GB for Windows and leave the sare 30Gb slot or ubuntu. In the install how di I choose to put it onto that spare part of the HDD

---

### Post by needhelp101 on 2007-03-13
So simply hit the resize button?????????????:confused:

---

### Post by platinumpt on 2007-03-13
I did the exact process you're describing, setup windows xp on its own partition (25gb), ran the ubuntu installer, where I created another 25gb partition, and a 3gb swap partition.

Everything went ok, but on the first restart I was greeted with an "error 17", which seems that something went weird with the bootloader. I can restore windows by starting up off the CD and running /fixmbr. 

Just not sure what grub/ubuntu expects me to do next though? Sorry to steal your thread, but you may run into this as well!

---

