---
title: "install ubuntu on own partion with logical drive?"
date: 2013-03-10
forum: Installation &amp; Upgrades
---

### Post by userqq on 2013-03-10
Hello,
I would like to install ubuntu on the 9 gb partition shown in  blue as sda6 but as you can see I already have 3 partitions (yes I need  to keep the first 2 (green and orange).
Can I create a logical drive insde the blue unformatted 9 gb partition so I can install ubuntu completely on it's own partition?
If  so, then how? please keep in mind that Im a noob with ubuntu so I will  need step by step instructions and that I need to leave the windows  install (green and orange 3 and 27 gb respectively alone.
also:
What about bootlader (will my comp give me a choice the way it does when I install ubuntu within windows)
Thamk you!

---

### Post by oldfred on 2013-03-10
By definition sda5 & sda6 are logical partitions in an extended partition.
You may want to also create a swap partition. But 9GB is not a lot, but usable even if a bit smaller for a 1GB swap. How much RAM do you have? 
Auto install will just create / & swap, but then you have no control over how it proportions sizes.

If system is old you may need Lubuntu as full Ubuntu needs a lot of RAM and video to work well.
 [https://help.ubuntu.com/community/LubuntuLinks](https://help.ubuntu.com/community/LubuntuLinks)

Install options, Do not use erase entire drive unless that is really what you want.
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)
Install 12.04- side by side auto install with screen shots
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) 

Grub will be installed to MBR of hard drive and should give choice of which system to boot.

---

### Post by darkod on 2013-03-10
If you decide not to create a swap partition, when you reach the manual partitioning step (second image), simply select the sda6 partition and click the Change button below. Set the Use As to ext4, mount point to / and tick the format box. When you click OK it will bring you back to the partitions list.
For the bootloader destination leave it at /dev/sda as it is by default. That will show you the grub2 bootloader on boot.

If you decide to make swap, you will have to delete sda6 and create two new partitions. Don't make swap too big since you need almost all of the space for /. The / partition will have ext4 filesystem and mount point /, and the  swap partition will be used as swap area with no mount point. Swap doesn't use a mount point.

That's it.

---

### Post by userqq on 2013-03-12
Thanks for the answers. Oldfred the partition that I have to work with is sda6 unknown 9 gb and yes I would like to create a separate swap file. I have 2 gigs of ram and 1 g swap would be fine for me.

darkod, thank you. If I delete sda6 and create 2 new partitions (one for / and one for swap) . Wont that mean that I will have 1 too many partitions?

tnanks in advance and sorry for the crappy pics.

---

### Post by oldfred on 2013-03-12
Logical partitions start as sda5, so sda6 is a logical and since defined must just be unformatted. So there should be no issues shrinking sda6 by 1GB and creating sda7 as 1GB and labeling it swap. Swap also has no format. You can have an unlimited number of logical partitions, the limit is 4 primary partitions and only one  primary can be the extended which is the container for all the logicals.

Since you have partitions you use Something Else to choose format (ext4) and mount (/), if swap exists it will find it, if not create it also. Also choose to put the grub2 bootloader into the MBR of sda, not to a partition.

Another choice is just delete sda6. Since unformatted I presume it has no data. Then you should also have the option to install to the unallocated space. But installer will choose its sizes and with 2GB of RAM it may make swap bigger.

---

### Post by userqq on 2013-03-12
So you're saying that the easiest way is to just delete sda6 and then I will have unpartitioned space to install ubuntu on with whatever swap ubuntu chooses and I wont have to create any logical drives and just install from the disk UI?

If that's the case then Im all for it! 
How should I delete it?

---

### Post by oldfred on 2013-03-12
You can use gparted from liveCD or Ubuntu installer. I would not use Windows as it has been known to not always rewrite an extended partition correctly.

With liveCd, if swap already exists you often have to click on swap and swapoff. And you have to use liveCD as all partitions do have to be unmounted.

       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by userqq on 2013-03-14
hi, oldfred
I erased the partition (using windows didk , I didnt understand the rest)so now I have app 9 gb of free space  but I dont know how to add new partition table and when I click add (pic 2) I dont know what to click on (pic 3) "use as" drop down list. Also dont kow what mount point is and how to add it.
Thanks

---

### Post by darkod on 2013-03-14
Do you plan to create swap also or not? The point of oldfred was that after deleting sda6 you could have used the Install Along Side windows automatic option. It would have found the unallocated space and used it.

If you want to use the manual option (your screenshots), when creating the root partition don't use the whole space if you want to create swap also. If you don't want to use swap, use the maximum free space as suggested.
In the Use As field you put ext4 (the filesystem), and for mount point /.
After that create swap in the remaining of the free space if you decided to do so. For swap, Use As is swap area and it doesn't use a mount point. It will be greyed out.

That's it.

---

### Post by userqq on 2013-03-15
I understand and yes I would like to create a swap but if I use remainig area and dont have mount point .What are the consequences (with no mount point? if any.
thanks

---

### Post by userqq on 2013-03-15
OK NM I think I got it, Im gonna try it,

---

### Post by darkod on 2013-03-15
What do you mean you don't have mount point? For the swap partition, there is no mount point. It is used automatically because it knows it's swap when you select Use As: swap area.

As for the main system partition, the root partition, when creating it select the mount point: / and that will tell the system to use the partition as root mount point.

---

### Post by userqq on 2013-03-22
It's been a few days and I dont want to leave the thread where it was so here it is, 
The whole seperate partition thing did not work for me. *I think* because during the initial installation I may have made my swap file  a *primary* partition and since I already had 3. it just added up wrong. ??
Couldn;t even boot windows after that , it said HAL.dll was missing. (not)
Oh well, luckily I was able to use an old xp home (**only** disk that worked!) go in and delete all the linux partitions and was back where I started , logged into windows no problem.
Got gparted and with a little trying and luck was able to add the 'unpartitioned space' to my 'D' primary (my c is a seperate fat 32 for windows swap, and yes it does help with gaming),
**SO** then I saw the 'ubuntu 12.10 version windows installer' and it installed just fine , except there is a problem with NO WIRELESS. seems that the' _Dell Wireless 1350 WLAN mini pci card   US _' on the computer , inspiron 9100 was not recognized. I
 found  some terminal commands and got it working but it keeps cutting out intermittently and is a bit slow.
the commands were:

sudo apt-get remove bcmwl-kernel-source

sudo apt-get install firmware-b43-installer

and they were found here: [http://blog.tech4him.com/broadcom-wireless-on-ubuntu-11-04-and-11-10/](http://blog.tech4him.com/broadcom-wireless-on-ubuntu-11-04-and-11-10/)

Anyway that's where Im at now , with the b43.xx drivers installed, working but intermittent and slow speed.

I will probably start another thread in the networking and wireless section, I already looked for a solution and found many but not specific, I will take another look. This computer is for my niece (15 yrs) and needs to have a backup OS so I will be able to repair windows when convenient as opposed to an emergency.

Im not sure how to mark this thread. **I can't find the 'solved' or 'closed' button.** _would someone please point me to it and advise how to mark it?_
Thank You all!

---

### Post by oldfred on 2013-03-22
Glad you found a way. Once you learn Ubuntu you may want to try the full partitioned install.

See my signature. With upgrade to new forum the old solved method has to be recreated and we have a temp workaround.

---

