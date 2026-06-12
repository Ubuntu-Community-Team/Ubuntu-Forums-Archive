---
title: "no such partition grub rescue&gt;"
date: 2010-05-28
forum: Installation &amp; Upgrades
---

### Post by nana336 on 2010-05-28
I upgraded to 10.0.4 from 9.10. Rebooted couple of times and everyting is working fine. Then I did DiskScan utility and rebooted... Then I'm totally struck here. I'm getting the following error when I boot the machine. I read soo many forums, no right solution.

[B]GRUB- error: no such partition 
grub rescue>[/B]

As some of the members state, I try to boot from LIVECD iso file, but its giving an error stating Dos Commands can not run. Looks like this live Cd is not booting Ubuntu. I downloaded multiple times different versions - the lastest file name is ubuntu-10.04-Desktop-i386.iso.

**I'm really surprised there is no right solution for this. There are lot of people waiting for solution. **

Thanks
Nana

---

### Post by darkod on 2010-05-28
Are you creating a cd with the image file, or you are trying to boot from the ISO directly?

Being able to boot with the cd into live mode is the first step. And it has nothing to do with grub or the ubuntu on the hdd.

You need to boot into live mode so you can run some tests, for example run the boot info script as explained here and post the content of your results file:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by nana336 on 2010-05-30
Hi Darkod

U helped me earlier. But this is a bigger problem I'm facing. For 5/6 days, this problem is not solved.

Here along I'm attaching the resolts.txt file. It looks like tis trying to boot from 2 sources. But I'm not sure how to make just one boot.

Also I observe I see only 2 partetions where as when I run the same script when my system is working, I see lot of partetions. I'm not sure what happened to all of theose.

Your help will be real good for me and most of the community.

Thanks
Nana

---

### Post by nana336 on 2010-05-30
DARKOD

For your information, I'm giving you

ubuntu@ubuntu:/dev$ **sudo fdisk -l**

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1d7a3a8f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6544    52559872   af  HFS / HFS+

Disk /dev/sdb: 1051 MB, 1051721728 bytes
255 heads, 63 sectors/track, 127 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xaea0aea0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         128     1027008    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(126, 254, 63) logical=(127, 220, 29)

---

### Post by darkod on 2010-05-30
> **nana336 said:**
> 

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6544    52559872   af  HFS / HFS+



I'm not sure why or how, but it reports only one partition on your disk, and with HFS type. I'm not really familiar with that.

Not sure what's the deal with this HFS partition, and whether the other partitions are gone.

---

### Post by oldfred on 2010-05-30
Is disk scan a norton utility tool? I think it was one of these:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)
In Windows 7, I had to remove Windows 7 DataSafe.
HP ProtectTools, Dell Recovery, and a few others write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct issues with MBR
[http://ubuntuforums.org/showthread.php?t=923576](http://ubuntuforums.org/showthread.php?t=923576)

---

### Post by oldfred on 2010-05-30
Nevermind previous post. 

The HFS is a Apple format. If this is a Dell computer then you have a partition problem and testdisk may be able to recover partitions. I have not used it but many have and it works for some.

repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
download TestDisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by darkod on 2010-05-30
Irrelevant (deleted). :)

---

### Post by nana336 on 2010-06-01
**oldfred** thanks for you GOOD reply. 

After running TestDisk script It showes some 4 partetions
then after Deep Search it showed 8/9 partetions -- Which are all my original partetions (I can see even my Windows 7, which disappeared after Ubuntu installation).

Now of all the 8/9 partetions it displayed, all are havind D status. I can't change them to * or L. I moved left/right arrows, but nothging doing.

What is the solution to make them right partitions. How many *, P & L's I need to make. Do you think I can recover all the partitions and update my Grub so that I can get back all my lost partitions and I can start my Ubuntu/Windows operating systems ?

Ur help will be greatly appreciated.

Thanks
Nana

---

### Post by oldfred on 2010-06-01
I am afraid I cannot help as I have been fortunate enough not to have to actually use testdisk. I would review all the instructions on their site as they seem to be pretty good.

---

### Post by darkod on 2010-06-01
I haven't used testdisk too (luckily never needed to), but you have to be careful with the deep scan. If I understood correctly, as you said, it even found a windows partition that was overwritten with ubuntu.
If you deleted that partition on purpose, to install ubuntu in that space, you do not want that windows partition back. Ubuntu is now in its place.

When you see the list of found partitions after the deep scan, I suggest to grab a piece of paper and write down the ones you think are the current existing partitions (I mean current before this problem happened). On the paper note the start/end sectors testdisk is reporting for the partitions.

There SHOULD NOT be any overlapping. That could help you 'decide' which to restore. If I'm not mistaken, P is for primary, L for logical (inside extended), and * is for primary with boot flag. I'm not sure how much details about your partitions you knew, but you need to at least have a clue which partitions are primary and which logical. Then use P and L accordingly in the restore process.

Do the sectors math on paper first before writing a new partition table!

---

### Post by nana336 on 2010-06-01
**oldfred & darkod** - thanks for your replies.

The Windows 7 partition is not rewritten by Ubuntu. It disappeared after Ubuntu 9.1 install. I used to have 6 partitions (Win7, WinServer2008, MacOS X & 3 free partitions - I install 9.10 in 1 free partition). After 9.1 install my Win 7 & WinServer 2008 been consolidated by Grub and put name as Windows Vista in boot. So during boot I need to select Ubuntu/Windows Vista/Mac OS X/...etc. When I select Windows Vista, it will start WinServer 2008 and Win7 is gone. I did some tweeks in Grub & now instead of Vista its showing as Win Server 2008, where as Win7 is gone.

After DeepScan on TestDisk, I recovered that Win7. I see all the OS but not sure what to save as *, P & L. Also the entries are not changing the statuses (by moving left/right arrows); then i can save to partition table and reboot to see everything is working.

***Any Clue on this recovered partitions to change status to *,P&L from D. And finally saving to partition table.***

---

