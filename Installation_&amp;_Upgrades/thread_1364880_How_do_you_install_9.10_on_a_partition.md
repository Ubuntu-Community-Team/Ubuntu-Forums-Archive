---
title: "How do you install 9.10 on a partition?"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by Secret Neo on 2009-12-26
So anyway, I got a laptop with Windows 7 on a 220GB partition (my primary OS) Windows XP on a 65GB partition, and an extra one with 13GB, used to be a recovery for Vista back in the day. Anyway I wanna wipe out my XP partition and install Ubuntu over it, but I'm really confused, how do I format it with the advanced partition thing during the installation? What do I format it to? I used to run Ubuntu off Wubi but I only allocated it to 6.5 GB and I'm deciding to go bigger and better. btw I'm installing this with a burnt CD of the newest Ubuntu 9.10 x64.

---

### Post by taurus on 2009-12-26
Boot from the CD.  Follow the instructions on screen.  When you get to the partition part, pick Manual (instead of using the whole harddrive) and tell the installer whichever partition you want to install Ubuntu to.

---

### Post by Secret Neo on 2009-12-26
> **taurus said:**
> Boot from the CD.  Follow the instructions on screen.  When you get to the partition part, pick Manual (instead of using the whole harddrive) and tell the installer whichever partition you want to install Ubuntu to.

So I won't need to format the partitioon before moving on? cuz right now its formatted NTFS with Windows XP on it, if I click forward, it will just be ok?

---

### Post by fancypiper on 2009-12-26
> **Secret Neo said:**
> So anyway, I got a laptop with Windows 7 on a 220GB partition (my primary OS) Windows XP on a 65GB partition, and an extra one with 13GB, used to be a recovery for Vista back in the day. Anyway I wanna wipe out my XP partition and install Ubuntu over it, but I'm really confused, how do I format it with the advanced partition thing during the installation? What do I format it to? I used to run Ubuntu off Wubi but I only allocated it to 6.5 GB and I'm deciding to go bigger and better. btw I'm installing this with a burnt CD of the newest Ubuntu 9.10 x64.You probably need to furnish a little more info. Personally, I am not familiar with Windows beyond XP, so I don't know what partitions Windows 7 uses.

Ubuntu uses the ext4 file system by default.

If you choose to boot to the live CD, you can find out your current disk partitioning scheme with the command

sudo fdisk -l

These will probably help:

[Linux Partition HOWTO](http://lissot.net/partition/Partition.html)

[Dual Boot Ubuntu and Windows](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by taurus on 2009-12-26
Ubuntu installer will format it for you so you do not have to do anything before hand.  It will probably create two more partitions, one for / (root filesystem) and one for swap, from that partition.

---

### Post by phillw on 2009-12-26
> **Secret Neo said:**
> So I won't need to format the partitioon before moving on? cuz right now its formatted NTFS with Windows XP on it, if I click forward, it will just be ok?

The install will tell you it is going to 'nuke' that partition - As that's what you want - say yes.

Phill.

---

### Post by Secret Neo on 2009-12-26
> **phillw said:**
> The install will tell you it is going to 'nuke' that partition - As that's what you want - say yes.

Phill.

thx, but theres a message that pops up saying "no root defined" doesn that mean I have to format it first?

---

### Post by taurus on 2009-12-26
You need to tell the installer which partition to install it to with / (root filesystem).  Again, you do not to format anything first since the installer will do that for you.  However, you need to specify which partition to mount as root--/.

---

### Post by Secret Neo on 2009-12-26
> **taurus said:**
> You need to tell the installer which partition to install it to with / (root filesystem).  Again, you do not to format anything first since the installer will do that for you.  However, you need to specify which partition to mount as root--/.

ok, so now i get that message when I click forward

"You have not selected any partitions for use as swap space. Enabling swap space is recommended so that the system can make better use of the available physical memory, and so that it behaves better when physical memory is scarce. You may experience installation problems if you do not have enough physical memory."

btw i clicked the XP partition and made it ext4 with mount as /.

---

### Post by fancypiper on 2009-12-26
> **Secret Neo said:**
> ok, so now i get that message when I click forward

"You have not selected any partitions for use as swap space. Enabling swap space is recommended so that the system can make better use of the available physical memory, and so that it behaves better when physical memory is scarce. You may experience installation problems if you do not have enough physical memory."
You can either create a swap file or a swap partition if you need it.

[Swap FAQ](https://help.ubuntu.com/community/SwapFaq)

I have 2 GB RAM and a 2 GB swap partition and I am using 97 MB of it running firefox, thunderbird, gedit, transmission, log viewer, 2 terminals, miro and vlc.

---

### Post by darkod on 2009-12-26
If you want to install ubuntu in the place of existing ntfs partition the best practice is:
Boot with ubuntu cd, Try ubuntu option. Open Gparted and delete the partition you want gone. Leave the space as unallocated. DO NOT create ext4 partition for ubuntu (you already figured out you need swap partition as minimum too).
Then boot with the cd again, Install Ubuntu option, and in step 4 tell it to use Largest Available Free space (in other words the unallocated space you just created).
Until you get more familiar with partitioning practices,this is the best approach IMHO.

---

