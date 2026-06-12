---
title: "change primary partitions into logical"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by luig on 2011-05-09
Hi there.
My first post. I am not new to partitioning a hard disk but this particular problem is beyond me and I couldn't find any help in other posts.
I have first installed Windows7 to sda2 (sda1 being the MBR). Then I installed Ubuntu as follows: sda3 /boot, sda5 swap (sda4 being the Extended partition), sda6 /, sda7 /home. So far so good. Windows and Ubuntu worked fine. I also planned to create another partition for data and two more partitions for Arch Linux. And here is the problem.
I just assumed that the Extended partitions were created logical but actually they are also primary. So, as things stand, all my 7 partitions are primary and I cannot create any more partitions. I must've erred somewhere during the Ubuntu installation. 
Is it possible ti change the Extended partitions into logical, without affecting all the stuff within? Any ideas? Otherwise I will have to delete everything after Windows and install Ubuntu again, making sure that I create logical partitions in the Extended part.
Many thanks for any advice.
luig

---

### Post by oldfred on 2011-05-09
Welcome to the forums.

The extended partition is primary and is one of the 4 primary partitions allowed under MBR partitioning. But it is just a container for all the logical partitions.

You may be able to expand the extended partition and add more logical partitions. It depends on where you have unallocated or want to make space. It has to be next to the extended or you end up having to move partitions around a lot. Make sure you have good backups.

Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Post a screenshot from gparted and explain what you want to do.

I also do not recommend separate /boot partitions unless you have an old system with the 137GB boot limit or have a server with RAID or LVM.

---

### Post by Quackers on 2011-05-09
If you are viewing the partitions from Windows, it may appear that all partitions are primary. This is not the case. It seems to be a problem with the way Windows is reading Linux partitions. As oldfred has said, the maximum number of primary partitions on an mbr formatted hard drive is 4 (one of which can be an extended partition).
If you post a screenshot of your gparted screen (as oldfred has said) things are likely to be reported more accurately :-)

---

### Post by luig on 2011-05-09
Thanks, Quack,
I know that there should be only 4 partitions, including the Extended partition. That's why I don't quite understand what is going on here. I neglected to mention that there is 797 GiB of space left at the end. Anyhow, here are the two screenshots, one of gparted and the other of the screen I get when trying to create a new partition in the unallocated space.
Cheers.

---

### Post by Quackers on 2011-05-10
Your partitions are not all primary, which is what we suspected. They look fine.
The problem in creating new partitions is because the remaining free space is not within the extended partition. You first need to extend the extended partition. When this is done you can create more logical partitions within it. As partitions within the extended partition are in use, you must do this from the live cd/usb desktop - not from within Ubuntu.

---

### Post by luig on 2011-05-10
Thanks Quack.
I will try that later, as I am busy with other things now.
luig

---

### Post by Quackers on 2011-05-10
Hokey cokey :-)
Have fun!

---

### Post by Quackers on 2011-05-10
Actually I just thought of something else.
Have you been trying to create a partition with type "Primary" by mistake? If so, select type "Logical" and see what happens :-)

---

### Post by luig on 2011-05-10
Right, I booted the live CD, gparted, but the result was the same. When trying to create a new partition in the unallocated space, I got the same error. Can't be done.
Looking at the gparted view of partitions, I notice that the Extended sda4 is 95 GiB. shouln't that be 0 or possibly the reminder of harddisk, about 892 GiBs? Anyway, I am not wasting any more time on this. Obviously, I was careless when I did the original installation.
So, I am changing to Mint instead, which I used previously and found it simpler and faster. I will delete all the partitions, except the windows of course, and install Mint. I will also take oldfred's advice and will not use a separate partition for /boot. So, sda1 ntfs MBR, sda2 ntfs Win7, sda3 ntfs data, sda5 ext4 /, sda6 ext4 /home, sda7 linux-swap and the rest left unallocated for possible future installation of ArchLinux. I like to fiddle with Arch and see what can be broken. You know, fix it 'till it breaks. :)

---

### Post by Quackers on 2011-05-10
Obviously that decision is yours to make :-)
Did you see post #8?

---

### Post by coffeecat on 2011-05-10
> **luig said:**
> Right, I booted the live CD, gparted, but the result was the same. When trying to create a new partition in the unallocated space, I got the same error. Can't be done.
Looking at the gparted view of partitions, I notice that the Extended sda4 is 95 GiB. shouln't that be 0 or possibly the reminder of harddisk, about 892 GiBs? Anyway, I am not wasting any more time on this. Obviously, I was careless when I did the original installation.

That's a pity really, because Quackers has already told you how to get round this.

> **Quackers said:**
> The problem in creating new partitions is because the remaining free space is not within the extended partition. You first need to extend the extended partition. When this is done you can create more logical partitions within it.

You need to resize the extended partition to the full extent of the HD, and then you will be able to create as many logical partitions as you want.

One tiny little gotcha. When using the live CD it will activate the swap partition. What you have to do is to right-click on the swap partition and choose "swapoff". Then you will be able to resize the extended partition.

---

### Post by luig on 2011-05-10
I've installed the latest Mint and it works fine. Checked that I can create new partitions from the unallocated space and I can. So, everything is peachy.
As for post #8, as I said before, I wasn't able to create ANY new partitions, primary or logical.
Thank you oldfred and quack for your input.
Happy surfing. :P
luig

---

### Post by Quackers on 2011-05-10
Very strange that, but nevermind now.
You're welcome :-)
Happy Kubuntuing!

---

