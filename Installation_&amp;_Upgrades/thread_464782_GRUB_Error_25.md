---
title: "GRUB Error 25"
date: 2007-06-05
forum: Installation &amp; Upgrades
---

### Post by sixfoottallrabbit on 2007-06-05
Ok,

I'll give you the scenario.

My friend has to tried to install Linux. At first, he had two hard drives, one of which was 80GB and the other 60GB. Each has only one partition, the first one has Windows (NTFS) and the second one simply has his files stored on it. When installing Linux, he first tried to shrink the Windows partition down and create a swap and an ext3 partition after it. Both the installer or gparted would not allow him to resize the Windows partition.

So then he tried to install it on the second hard drive. He was able to resize the partition on that hard drive without fail and create the two new ext3 and swap partitions after it. Then he installed using those partitions. On boot, he changed the boot sequence to boot from his second hard drive first, but GRUB simply gives him an error 25. He is now unable to boot from either Linux or Windows until he fixes GRUB.

How can he do this?

PS. He was installing Feisty 7.04 x86

---

### Post by confused57 on 2007-06-05
Here's a description & possible solution(s) for grub error 25:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#25](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#25)

Are you getting a grub boot menu, when booting first to the drive with Ubuntu?

---

### Post by sixfoottallrabbit on 2007-06-05
Wow. That website looks great. I'll see if it helps later today.

Thanks a lot =]

And no he doesn't get the boot menu.

---

### Post by confused57 on 2007-06-05
He might also want to try reinstalling grub to the Ubuntu drive's mbr, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

It would be something like this:
whatever the output of "find /boot/grub/stage1" returns, e.g. "root (hd1,2)"
I'll use letter substitutions for the actual output:
```
root (hdx,y)
setup (hdx)
```

If the root was (hd1,y) and he gets a grub boot menu...highlight the Ubuntu entry, press "e", change root from (hd1,y) to (hd0,y), then press "b" to boot...this is temporary, but can be made permanent in /boot/grub/menu.lst.

I wanted to give you the above to try, if he is able to get a grub boot menu after reinstalling grub...good luck.  Here's the main page of the website I provided earlier:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

You might want to make a copy of the Super Grub Disk, it's an excellent utility for booting problems.

---

### Post by Roo-Kun on 2007-06-05
Hey, I'm the idiot that sixfootrabbit is talking about.

I've uninstalled grub via the windows CD and then reinstalled it via the live CD.. Still get error 25.

I would like to point out that the HDD that linux is installed on looks like this.

|_____ NTFS 60gb________________|_linux-swap 1gig_|__ext3 20gig___|


It might have something to do with the order they are partitioned.

---

### Post by confused57 on 2007-06-05
> **Roo-Kun said:**
> Hey, I'm the idiot that sixfootrabbit is talking about.

I've uninstalled grub via the windows CD and then reinstalled it via the live CD.. Still get error 25.

I would like to point out that the HDD that linux is installed on looks like this.

|_____ NTFS 60gb________________|_linux-swap 1gig_|__ext3 20gig___|


It might have something to do with the order they are partitioned.

I would definitely recommend burning a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

You might want to boot the Ubuntu live cd, open a terminal(Applications---Accessories---Terminal), post the output of:
```
sudo fdisk -l
```
the -l is a lowercase "L"
this will show your partitions on both hard drives

You can mount your root partition from the Ubuntu live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

Once you mount your root partition, you might want to post your menu.lst & device.map:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/hdb3 /media/ubuntu
gedit /media/ubuntu/boot/grub/menu.lst
gedit /media/ubuntu/boot/grub/device.map
```

substitute your root partition as determined from "fdisk -l" for /dev/hdb3

Hopefully, this may give a clue as to why you're getting the grub error...since none of the suggestions in the link I provided in my first reply helped:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#25](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#25)

Added:  If I understand correctly, Windows is on your primary drive and Ubuntu on your 2nd drive...if your bios is capable of booting first to your drive with Ubuntu on it, I would try setting your system up this way:
Reinstall Window's IPL to your Window's drive mbr.
Then use the live cd to install grub to the 2nd drive's mbr:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
I think you would do "setup (hd1)"

Boot first to your Ubuntu drive and if you happen to get a grub boot menu, highlight your Ubuntu entry, press "e", change root from (hd1,x) to (hd0,x), then press "b" to boot...this is temporary if it works.

You'll more than likely still get the error 25, but at least you'll be able to boot Windows while you're troubleshooting getting Ubuntu to boot...you should be able to mount your root partition, with your pc set up this way.

---

### Post by adrian15 on 2007-06-07
> **Roo-Kun said:**
> Hey, I'm the idiot that sixfootrabbit is talking about.

I've uninstalled grub via the windows CD and then reinstalled it via the live CD.. Still get error 25.

I would like to point out that the HDD that linux is installed on looks like this.

|_____ NTFS 60gb________________|_linux-swap 1gig_|__ext3 20gig___|


It might have something to do with the order they are partitioned.

If you want not to have problems... Set your bios so that your first hard disk is the second one and viceversa... once you have done this... install ubuntu again to the second hard disk... as long as the first hard disk will be the second one...

The BIOS trick of selecting the second hard disk to boot will work.

You can not wait to install Ubuntu in a BIOS setup and work with another BIOS setup.

If you want not to reinstall it is possible to fix grub right now... just ask me if you do not want to go under reinstallation procesus.

adrian15

---

