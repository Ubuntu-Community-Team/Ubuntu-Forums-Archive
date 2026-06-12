---
title: "Ubuntu dual-boot hard drive partition question"
date: 2012-01-25
forum: Installation &amp; Upgrades
---

### Post by SocProf on 2012-01-25
Hi, I am new to Linux and Ubuntu and have a question about my new harddrive partition.  Last night I successfully installed Ubuntu  11.10 from a USB alongside Windows 7,  partitioning the hard drive.  I allocated 20GB to Ubuntu, and the  during the first attempt to install Ubuntu, the installation crashed  (had to do with installing some third party software).  At any rate, I  just installed it again with a modification and everything turned out  alright.  When I look at how the hard drive is partitioned though, I  think it might have made two separate partitions!  In short, Ive got 40  GB (not 20GB) approx.  allocated to Ubuntu on an 'extended drive.'  When  I look at my harddrive using the Gparted Partition editor, the system  is divided into these partitions:

/dev/sda1    ntfs     Label = "system"   Size = 1.46 GB
/dev/sda2    ntfs     Label = "TI106140W0C"   Size = 238.25 GB
/dev/sda3    ntfs   Hidden Recovery    11.18GB

/dev/sda4    extended   Size = 47.20 GB   [twice the size its supposed to be]
/dev/sda7   ext4    Size = 19.47 GB
/dev/sda8   linux-swap     Size = 3.87GB
/dev/sda5   ext4   Size =  19.98 GB   [I am thinking this is a copy of sda7]
/dev/sda6   linux-swap   Size = 3.87GB  [I am thinking this is a copy of sda8]


Basically, it seems that linux is located in sda4, which is  twice as big as it should be and there are two copies of everything in  this extended partition.  When I turn on my computer also, it is  confusing because instead of having a few options (e.g. start windows  normally, Ubuntu, or some Windows recovery), there are like 8 or 9,  which seem redundant.   There doesn't seem to be any problem running  anything, but I think I may have wasted some hard drive space.  I am  wondering if this partition schema is normal for Ubuntu 11.10, and if  not, whether I can allocate just 20GB to linux, and the rest to  Windows. I have already checked out a few support pages, including:  
[https://help.ubuntu.com/8.04/switching/installing-partitioning.html](https://help.ubuntu.com/8.04/switching/installing-partitioning.html)
[https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows)

I'm including a screen shot of my hard drive too.  What should I do to get rid of these extra copies of partitions, and to allocate 20GB to linux and the rest to windows?

Thank you!
[[IMG]http://img7.imagebanana.com/img/ybfftz57/thumb/LinuxScreenshotPartition.png[/IMG]]("http://www.imagebanana.com/view/ybfftz57/LinuxScreenshotPartition.png")

[[IMG]http://img7.imagebanana.com/img/ybfftz57/LinuxScreenshotPartition.png[/IMG]]("http://www.imagebanana.com/")

---

### Post by BC59 on 2012-01-25
1. You have 2 swap partitions. You can delete the second one, without problem-delete sda6
2. The sda7 partition is your system ( / ) and is a little big, should be something like 12-14GB.
3. The sda5 should be the /home partition and you can use the maximum of the space existing.

Can you run:
```
sudo parted /dev/sda print
```and
```
sudo fdisk -l #(it's a lower case L)
```
Post the results

---

### Post by darkod on 2012-01-25
This happened because of the second install. If you use the automated methods it will simply create new root and swap partitions. How does it know you want to use existing partitions? What if it deletes some data you have there?

Because of this ubuntu will never install to existing partitions unless you manually tell it to.

In your case, with one failed install, you should have:
1. Used the manual partitioning option (Something Else) and specify where you want ubuntu installed manually.
2. Delete the partitions of the failed install and use the auto method again. In this case the old partitions wouldn't have existed, and two new would have been created.

---

### Post by SocProf on 2012-01-25
Thank you very much.  I also thought the second installation was the problem, good to know.   I just tried deleting the sda6 swap drive, using Gparted and it says it cannot be deleted:  "Please unmount any logical partitions having a number higher than 6".   I'm not actually sure what this means.   

Second, I was thinking sda7 and sda5 were basically two installations of linux, the same thing, and I was using one of them, but not the other, so one of them would be wasted space.   Is this not right?   The sda7 is system and the sda5 is the home, (or vice versa)- so they do different things?  I only therefore need to delete the extra swap drive? sda6?  Which drive am I using right now?  Is it just sda4 as a whole, or one of the 'logical' partitions, say, sda7 or sda5?

Third, when I delete a partition, where does the extra space go?  I assume its unused until I allocate it somewhere?  If I wanted the extra 3 GB allocated to Windows, would I need to go into Windows and run another partition program to get that 'free space'?

---

### Post by BC59 on 2012-01-25
You have to run Gparted after boot from a live CD. To delete the swap you have first to unmount it. When is deleted you will have unallocated space. If you delete sda6 you can extend your sda5 partition to the right, to take the space. But still we are not sure, what is the sda5. Do you use it for /home?

---

### Post by darkod on 2012-01-25
You are right, partially.
sda5 is your first install, with sda6 the swap for it.
sda7 is the current working install (hence the keys symbol that is mounted and the mount point / displayed), and sda8 the swap for it.

Because you used the standard auto method it doesn't create a separate /home partition. Otherwise Gparted would show sda5 as mounted too with mount point /home.

You can't delete sda5 and sda6 because even though they are not mounted, they do belong inside the extended partition sda4 which has sda7 and sda8 mounted. The message was clear.

You will need to boot into live mode, then open Gparted. Note that swap is mounted in live mode too, so you need to right-click it and select Swapoff until the keys symbol is gone. It should also be gone from sda4. Only then you can delete sda5 and sda6. After you do that, you need to hit the big green tick mark button in Gparted otherwise the changes are not applied if you only exit it. Watch out for that when using Gparted.

After you delete them the space will remain unallocated, and you can use it. But your option will be limited since it will be unallocated space inside your extended partition sda4, and also it's towards the end of the disk so it is not easy to add it to windows, nor ubuntu (sda8 is in the way).

---

### Post by SocProf on 2012-01-25
Yes, i am using this from home.  It is my personal laptop.  Can I boot from my USB?  Do I need to d/l Gparted onto my USB drive?  and will booting from my USB 'unmount' this sda6 swap drive, or the sda7-  is it the swap drive or the 'drives higher than 6' (sda7) that need to be unmounted?  

I was originally thinking that sda5 was the partition from the first, failed installation, and that during the second installation, it created sda7, and that I am using sda7 now, but not sda5, because that was created during the first failed installation.  I don't know if this is right or not.  So basically I Thought I had two separate Ubuntu systems on my hard drive and needed to get rid of one of them.  Might that be a possibility?  

Thank you

---

### Post by BC59 on 2012-01-25
Better follow the directions of @darcod, he is one of the best on these problems.

---

### Post by SocProf on 2012-01-26
Thank you Darkod and BC59.  I was able to boot ubuntu from my usb and use Gparted as advised.  To avoid all the mess, I ended up just deleting all of the partitions, allocating all of it to windows, and then reinstalling from scratch.  Ubuntu 11.10 is up and running now with no problems!

---

