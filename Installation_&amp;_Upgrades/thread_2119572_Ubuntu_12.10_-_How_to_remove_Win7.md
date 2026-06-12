---
title: "Ubuntu 12.10 - How to remove Win7?"
date: 2013-02-24
forum: Installation &amp; Upgrades
---

### Post by JayArtist on 2013-02-24
Hi guys,

I've decided to stick with Ubuntu 12.10 for the time being, but as I installed Ubuntu 12.10 as a Dual-boot alongside Windows 7, I'd like to remove the offending item (Win7).

I read various posts online regarding this, most suggesting that I use GParted with my Live Ubuntu CD - Ubuntu 12.10 doesn't come with Gparted now, and instead comes with Gnome-Disks-Utility: [https://live.gnome.org/Design/Apps/Disks](https://live.gnome.org/Design/Apps/Disks)

Although that said I managed to find a live distro that had Gparted.

But as I'm running 12.10 with 'Gnome Disks', this is the screen shot:
[http://www.pasteall.org/pic/46000](http://www.pasteall.org/pic/46000)

I also don't think that 'Gnome Disks' can resize - but I digress ;)

The suggestion was to delete and format the windows partition with said Live CD using Gparted, then drag/resize the Ubuntu partition to occupy the new partition.

It appears easy enough to delete the Win7 partition, rename it, format it - but that's as much as I appear to be able to do.

How do I get my Ubuntu partition to use and take over the whopping 156GB that was once my win7 partition?

Secondly I updated grub with "sudo update-grub", which removed the link from the boot/grub screen for Win7, but it doesn't remove the selection bootscreen altogether, how do I just get Ubuntu to boot without this?

Thanks, Jay :)

---

### Post by tartalo on 2013-02-24
> **JayArtist said:**
> 
How do I get my Ubuntu partition to use and take over the whopping 156GB that was once my win7 partition?

Resize the Ubuntu partition after deleting the Windows 7 partition (Using Gparted)

> Secondly I updated grub with "sudo update-grub", which removed the link from the boot/grub screen for Win7, but it doesn't remove the selection bootscreen altogether, how do I just get Ubuntu to boot without this?

Set GRUB timeout to 0 or hide GRUB

[http://askubuntu.com/questions/148095/how-do-i-set-the-grub-timeout-and-the-grub-default-boot-entry](http://askubuntu.com/questions/148095/how-do-i-set-the-grub-timeout-and-the-grub-default-boot-entry)

---

### Post by oldfred on 2013-02-24
While you can move partition left, make sure you have good backups. 

It can take a while and any issue, power failure, battery runs out, cat, dog, kid disconnects power and many others have been reasons users post with wanting to recover data on a system. And because it is partially copied it is about impossible to recover. 
But many have moved partitions without issue. That may be why we forget the backup step since it works most of the time.

Another alternative is to make it /home as a separate partition or just make it a data partition and mount it with fstab.

       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

    
       Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

---

### Post by JayArtist on 2013-02-24
Hi,

Sadly as I mentioned, there doesn't appear to be a way to resize the Ubuntu partition into the large 156 GB partition - I select "Resize" in GParted and a window appears with arrows, but the slider is full in both directions already - so I can't 'resize' it in either direction.

The Grub edit seems pretty easy to sort though, thanks for that ;)

---

### Post by darkod on 2013-02-24
First, you have to do it from live mode because you can't resize a partition you are running from.

Second, in standard automatic dual boot install, the ubuntu partitions are logical inside extended partition container. So, for expanding, you have to expand the extended container first, and only then it will allow you to expand the root partition.

Also, it depends where the free space it, and where your root partition is. They have to be next to each other so you can expand into it. Take a good look in Gparted of the physical positioning.

EDIT PS. One option is to convert the partitions to primary now with fixparts. Personally I hate having only logical partition on a disk. You use logical once you don't have any primary left. Now that windows is deleted, there are no other partitions, only two, root and swap. No point having them as logical.
But this is more estetics than necesity, it can work as it is too.
Having them as logical also helps with resizing since you wouldn't have to manipulate the extended partition too, like you have to right now.

---

### Post by mörgæs on 2013-02-24
It might be considered cheating, but anyway: 

After reading the posts above I assume you have taken a backup already. That means you could just do a fresh install, deleting the entire drive in the process. 20 minutes, problem solved. 

I tend to use logical partitions as much as possible, but if you want to use primary ones you can also control this during installation. In that case: 25 minutes, problem solved.

---

### Post by presence1960 on 2013-02-24
> **mörgæs said:**
> It might be considered cheating, but anyway: 

After reading the posts above I assume you have taken a backup already. That means you could just do a fresh install, deleting the entire drive in the process. 20 minutes, problem solved. 

I tend to use logical partitions as much as possible, but if you want to use primary ones you can also control this during installation. In that case: 25 minutes, problem solved.

**+1 on what oldfred said! The easiest fix** is to just make a separate data partition from the windows space. Very simple and quick and you don't have to mess with your ubuntu install which is working fine or do any partitioning operations on your ubuntu partition. 


Words from another "cheater":

make an image of your Ubuntu installation to an external disk using Clonezilla. Then repartition your disk the way you wish. The only limitation is that to restore the image you made, the partition you are restoring the image to can not be smaller than the original partition the image was made from. To help me along those lines I always put the size of the partition at the end of the file name when saving it.

Best practice to keep the new partition same as old one, i.e. sda2 > sda2, sda6 >sda6. If you restore the image to a different partition you will have to reinstall GRUB so that it points to the partition with ubuntu.

---

