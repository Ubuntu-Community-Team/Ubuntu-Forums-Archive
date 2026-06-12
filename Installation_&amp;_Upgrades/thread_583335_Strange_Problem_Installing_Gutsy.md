---
title: "Strange Problem Installing Gutsy"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by BlackRazor22 on 2007-10-20
Hi everybody, I have some problems installing Gutsy and I'd really appreciate some assistance.

First of all system specs: the laptop is an Acer Aspire 1650, Intel Pentium M Processor 1.73GHz, 1Gb RAM DDR2 (dual channel), ATI Mobility Radeon X300 PCI-Express 128Mb, 100Gb HDD, DVD/CD burner.
What I am trying to accomplish is a dual boot with Windows XP SP2 Home Edition. Originally the hard disk was partitioned like this: 1 primary partition containing Windows and programs (FAT32) + 1 extended partition containing a logical FAT32 partition (for data). I used partition Magic to resize the extended and logical partition leaving 10Gb unallocated.
Then I downloaded the Ubuntu iso (for the 386 architecture), checked its md5, burned it, rebooted the pc and used the check cd to make sure the disk was correctly burned. Both the md5 and cd checks showed no errors.

I then started the LiveCD and started the installation procedure. The first weird thing happened immediately after the keyboard layout choice: a small pop-up window should have appeared saying something like "analysing partitions" but it took 10 minutes for it to appear; then the window remained at 0% for some other minutes (about 5) before filling up and allowing the installation to proceed. During this periods of time the cd was not accessed but the hard disk light remained on.

Next I had to choose how to partition the HDD so I chose manual and used the 10 Gb unallocated space to create an 8Gb ext3 partition (mount point: /) and a 2Gb swap partition. Creating these 2 partitions was a long process too since the aforementioned "analysing partitions" pop-up window appeared after almost every operation and took some minutes to complete whatever it was doing; the only actions that were swift to do were ticking the ext3 partition format checkbox and choosing the mount points.

I then proceeded to the final passages of the installation procedure and finally the installer started transferring files to the HDD. However before the transfer was finished the installer simply window simply vanished and the transfer was aborted without even showing an error. Of course the installation was incomplete (it did not even install grub).
So I tried with Kubuntu (Gutsy) and Ubuntu (Feisty Fawn) and had the same problems; I even tried with the alternate installation cd (Gutsy) but again in the middle of the transfer the installation aborted saying that a file could not be transferred.

I suspected a HDD failure so I used fsck to check all HDD partitions but no problems were found. I also tried to reboot in Windows, restore the original partitions with Partition Magic and check them with chkdsk but again no problems were found. Since the HDD seemed to be working flawlessly I used the Ubuntu cd to check the RAM but again the test was passed with no errors.
I suspect something is wrong with the partitions given the long time it took for the installer to recognize and modify them and because I also noticed that manually starting the partition editor from the LiveCD took a long time but then again Partition Magic can access them with no problem and starts up in a very short time. I am really confused by this situation and being a Linux newbie does not help so if anybody has some suggestions I could really use them.

---

### Post by teejay17 on 2007-10-20
I suggest going back to 7.04. 
Gutsy is really buggy and is causing major headaches all over.

---

### Post by WernerBrandt on 2007-10-20
> **BlackRazor22 said:**
> HI everybody, I have some problems installing Gutsy and I'd really appreciate some assistance. First of all system specs: the laptop is an Acer Aspire 1650, Intel Pentium M Processor 1.73GHz, 1Gb RAM DDR2 (dual channel), ATI Mobility Radeon X300 PCI-Express 128Mb, 100Gb HDD, DVD/CD burner. What I am trying to accomplish is a dual boot with Windows XP SP2 Home Edition. Originally the hard disk was partitioned like this: 1 primary partition containing Windows and programs (FAT32) + 1 extended partition containing a logical FAT32 partition (for data). I used partition Magic to resize the extended and logical partition leaving 10Gb unallocated. Then I downloaded the Ubuntu iso (for the 386 architecture), checked its md5, burned it, rebooted the pc and used the check cd to make sure the disk was correctly burned. Both the md5 and cd checks showed no errors. I then started the LiveCD and started the installation procedure. The first weird thing happened immediately after the keyboard layout choice: a small pop-up window should have appeared saying something like "analysing partitions" but it took 10 minutes for it to appear; then the window remained at 0% for some other minutes (about 5) before filling up and allowing the installation to proceed. During this periods of time the cd was not accessed but the hard disk light remained on. Next I had to choose how to partition the HDD so I chose manual and used the 10 Gb unallocated space to create an 8Gb ext3 partition (mount point: /) and a 2Gb swap partition. Creating these 2 partitions was a long process too since the aforementioned "analysing partitions" pop-up window appeared after almost every operation and took some minutes to complete whatever it was doing; the only actions that were swift to do were ticking the ext3 partition format checkbox and choosing the mount points. I then proceeded to the following passages of the installation procedure and finally the installer started transferring files to the HDD. However before the transfer was finished the installer simply window simply vanished and the transfer was aborted without even showing an error. Of course the installation was incomplete (it did not even install grub). So I tried with Kubuntu (Gutsy) and Ubuntu (Feisty Fawn) and had the same problems; I even tried with the alternate installation cd (Gutsy) but again in the middle of the transfer the installation aborted saying that a file could not be transferred. I suspected a HDD failure so I used fsck to check all HDD partitions but no problems were found. I also tried to reboot in Windows, restore the original partitions with Partition Magic and check them with chkdsk but again no problems were found. Since the HDD seemed to be working flawlessly I used the Ubuntu cd to check the RAM but again the test was passed with no errors. I suspect something is wrong with the partitions given the long time it took for the installer to recognize and modify them and because I also noticed that manually starting the partition editor from the LiveCD took a long time but then again Partition Magic can access them with no problem and starts up in a very short time. I am really confused by this situation and being a Linux newbie does not help so if anybody has some suggestions I could really use them.

Unreadable, I suggest you use some enters once in a while when u want people to respond, noone is going to read this
:confused:

---

### Post by BlackRazor22 on 2007-10-20
> **WernerBrandt said:**
> Unreadable, I suggest you use some enters once in a while when u want people to respond, noone is going to read this
:confused:

Ops, you're right, should be a little more readable now.

---

