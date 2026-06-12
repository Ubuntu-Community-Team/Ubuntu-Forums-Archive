---
title: "Not finding hdd in cd boot installation"
date: 2013-05-12
forum: Installation &amp; Upgrades
---

### Post by Nargluj on 2013-05-12
[COLOR=#ff0000]***Update****: After trying some things, I've posted an update, [http://ubuntuforums.org/showthread.php?t=2144553&p=12720142#post12720142](http://ubuntuforums.org/showthread.php?t=2144553&p=12720142#post12720142) .*[/COLOR]
Hello, I've reached a dead end when trying to install Ubuntu 13.04, please help me. (Boring introduction has now been skipped.)

I want to install Ubuntu to run alongside windows 7. I don't have cd's to reinstall windows if something went wrong.

I've got a Packard Bell ixtreme M5140.

[IMG]http://i1312.photobucket.com/albums/t529/Nargluj_/2013-05-12210626_zps2c16e955.jpg[/IMG]
*At which point in the installation I get stuck. Note the stage in orange and white dotes.*


[IMG]http://i1312.photobucket.com/albums/t529/Nargluj_/2013-05-12210723_zpscfcf5592.jpg[/IMG]
[I]Text shown when I click at any option in the window except "Install now" (back and quit also excluded).
[/I]
As you can see I get an error message at this point in the installation. The installer obviously doesn't find my hard drive or its partitions.



If Ubuntu is run live from the CD, it can find the hdd and it's partitions, as shown below.

[IMG]http://i1312.photobucket.com/albums/t529/Nargluj_/2013-05-12211318_zps06f92964.jpg[/IMG]


[IMG]http://i1312.photobucket.com/albums/t529/Nargluj_/2013-05-12211558_zps70ea9c08.jpg[/IMG]


As you can see I've got two main partitions of my hdd. The partitioning where done when I bought my PC from the store. I want to either install it on the partition named DATA (/dev/sda4) or partition Packard Bell (/dev/sda3) into two partitions, one with Windows that's already installed and one with Ubuntu.

Here's the error log from page three that shows up when you press "Show Details".

[IMG]http://i1312.photobucket.com/albums/t529/Nargluj_/2013-05-12210917_zps75d201c6.jpg[/IMG]

[IMG]http://i1312.photobucket.com/albums/t529/Nargluj_/2013-05-12210955_zps139c8f9e.jpg[/IMG]

I hope i haven't uploaded the images in too high resolution, if so, I apologise.


I've done my best to put up as much information as I thought would be useful. Tell me if you feel something's missing and I'll add it if I can.

And to round it off, a photo of my PC's interior for good measure.

[IMG]http://i1312.photobucket.com/albums/t529/Nargluj_/2013-05-12212313_zps0aae5bc1.jpg[/IMG]
*Please note my new graphic card. =)*


Thanks in advance.:D
Sincerely, Lukas.

---

### Post by dabl on 2013-05-12
Very complete question -- congrats on that!

Issues:

1.  You're not going to install Ubuntu on a partition that is formatted NTFS -- it needs a linux filesystem, and ext4 is recommended.

2.  The two partitions that you have in mind for Ubuntu are equally large at 690GB, but probably you want one for the OS, which only needs to be on a 20GB or 30GB partition, allowing plenty of space for downloads and such, and you probably want the largest space for data.

3. If you were thinking that Windows and Ubuntu would share the data partition, then that is not a problem, but it will max out your allowable 4 primary partitions, leaving none available for a swap space.

So, my approach if I  were in your situation would be first to make a Parted Magic Live CD or USB stick, using Windows 7 (I don't actually know how that works, but I know that is a common method to make the Live USB stick).  Parted Magic Live is available [**[color=green]here[/color]**](http://partedmagic.com/doku.php?id=downloads).  You don't HAVE to use Parted Magic, most Linux Live CDs, including Ubuntu, have GParted on them, so if you happen to have one of those, that's fine.  One way or another, you need to boot a linux system that has GParted on it, and Parted Magic is my preferred way to do that.

I'll assume you want to maximize the shared NTFS data partition, and then install Ubuntu in a 30GB partition, and also have a swap space.

With GParted up and showing the hard drive on the graphic, delete the fourth partition (/dev/sda4).  Now you need to shutdown the booted Parted Magic Live CD, boot Windows 7, and use the Windows Disk Management tool to enlarge /dev/sda3 (the one presently labeled "Packard Bell" -- you can change the label to DATA), and enlarge it so that there is only about 35GB left unallocated on the drive.

Now shutdown Windows and boot your Parted Magic Live USB stick again.  In the unallocated space, make a new partition and the type of this new partition is "extended".  In the new extended partition, you can make two logical partitions.  The first one for Ubuntu, formatted ext4, can be 30GB, and the second one, formatted "linux swap" is for swap, and can be the rest of the hard drive, which should amount to about 5GB.  Don't worry if swap comes out a bit less -- you could probably do fine with only 3 or 4GB of swap space.

Now you are ready to install Ubuntu, which can go on the 30GB partition, with swap on the small one.  Once Ubuntu is installed, if the ntfs-3g package is not installed, you'll need to install it.  There is a lot of guidance on the internet and this forum about how to make a mount point on /mnt and then mount your NTFS data partition with a line in /etc/fstab.

I have tried not to go too high-level with this guidance, but I have skipped some minor details, so if you need more details post back.


NOTE:  I am not familiar with the motherboard and BIOS in that computer model. If it uses UEFI, then there is a whole other list of issues to deal with, beyond the scope of this guidance, and you'll have to address those first, before installing Ubuntu and grub.  Note the many, many forum posts about Windows not booting after installing Ubuntu on a UEFI motherboard -- there are challenges on that which you should familiarize yourself with if UEFI is an issue on your system.

---

### Post by westie457 on 2013-05-12
Hi. Welcome to the Forum.

Before suggesting a plan of action to install Ubuntu buy some DVDs or CDs and make a full back-up of your Windows partitions including the PQSERVICE partition. Do these things before doing anything else in case anything does go wrong.

Also could you boot the LiveCD into 'Try' mode and open a terminal - pressing Ctrl+Alt+T at the same time is the quick way - and run this command ```
sudo fdisk -l
``` the l in the command is a small L. In the terminal window highlight the output and copy - Ctrl+Shift+C - then in a New Reply in this thread click on the # at the top of the writing pane and paste between the [code] brackets.

Further advice will be available after these tasks have been done.

Thank you.

---

### Post by grahammechanical on 2013-05-12
What option did you select when it came to installing Ubuntu? Did you choose Do Something Else? Or Install alongside? It seems to me that you already have 4 primary partitions on that disk. If that is true then you would have to delete at least one of those partitions and turn it into an Extended partition (a special kind of primary partition) and then create logical partitions (as many as you need) inside the extended partition.

I am guessing that Windows is install in sda3 but what do you have in sda4?

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Regards.

---

### Post by Nargluj on 2013-05-12
Thank you for three fast replys. =)

It's 0:15 right now for me, so I'll look into it more deeply tomorrow (hopefully) when I'm not tired. Less risk of doing something bad.


1) Thank you dabl for your fast long reply, it's very much appreciated. I'll go with a bit more than 30 GB for the Ubuntu partition, something along the lines of 600 GB. I've got the space so I might as well use it.

2) I don't know about UEFI, never heard about it before. I'll look into it.

3) What does ```
sudo fdisk -l
``` do? It's late now so I'm booting the Live CD tomorrow to try it and post here shortly after that.

4) Regarding the options grahammechanical asked about, this stage came before those. If you're talking about stage four from [_**this**_]("http://www.ubuntu.com/download/desktop/install-desktop-latest").

5) As shown in image three and four image, sda4 is empty.

---

### Post by Mark Phelps on 2013-05-12
> **Nargluj said:**
> I want to install Ubuntu to run alongside windows 7. I don't have cd's to reinstall windows if something went wrong.

The FIRST thing you should do is use the Win7 Backup feature to create and burn a Win7 Repair CD.  IF you don't do that, you will not have a way to repair your Win7 boot loader, should something go wrong.

The SECOND thing you should do is download and install the free version of Macrium Reflect in Win7.  Then, use the option to create and burn a Linux Boot CD.  Then, do an image of your Win7 OS and boot partitions to an external drive.  This will allow you to restore Win7, should something go wrong.

Only AFTER you have done these, should you move forward with installing Ubuntu.  IF you rush into it, you will virtually guarantee that (1) you will hose up Win7 in some way, and (2) you will not have a way to repair it or restore it.

---

### Post by dabl on 2013-05-12
Yes, I concur with Mark Phelps -- you need to protect yourself against "inadvertencies", wrt the Windows installation.


> **Nargluj said:**
>  I'll go with a bit more than 30 GB for the Ubuntu partition, something along the lines of 600 GB. I've got the space so I might as well use it.

No problem Lukas -- just be aware that data that you accumulate on your ext4 Ubuntu partition will not be available when you're running windows.  The Ubunto OS itself only needs around 7 GB of space.

---

### Post by oldfred on 2013-05-13
Also some BIOS have trouble finding boot files in large / (root) partitions. We are not sure if a BIOS issue or grub bug. But better to keep / (root) at the 10 to 25GB size and have separate data partition(s) or separate /home.

Sometimes issue can be avoided by making sure you have BIOS in AHCI, but may have to install those drivers in Windows first if not installed already.

---

### Post by Nargluj on 2013-05-13
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7f67eba2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    33556479    16777216   27  Hidden NTFS WinRE
/dev/sda2   *    33556480    33761279      102400    7  HPFS/NTFS/exFAT
/dev/sda3        33761280  1481742335   723990528    7  HPFS/NTFS/exFAT
/dev/sda4      1481742336  2930143231   724200448    7  HPFS/NTFS/exFAT
ubuntu@ubuntu:~$ 
```

---

### Post by Nargluj on 2013-07-06
Hello again!

I've been quite busy for a while with school, work and other stuff and haven't had an whole day for which to do this. I really don't want to rush things like this. Better to do it on a day when I know I wont get interrupted.

It turns out I still get an error message at the same place. The only real change in results during the installation is that it's a longer wait time to get to the "error-stage" from the previous stage. Don't know why, or even if it matters. I did get a about 3 tries in which it just crashed back to "try Ubuntu" from the installation at the same place, don't know why. Worth to note is that I also got the error message doing the same thing as when it just crashed. Probably just a stupid coincidence that I didn't get an error report.

Things I've done or tried:

1) I've followed dabl's very good advice/guide and changed my partitions.

2) Tried out booting in AHCI, didn't work. Did this after changing my partitions.

3) Ran 'sudo fdisk -l' command.


Here comes some updated screen shots:

[[IMG]http://i1312.photobucket.com/albums/t529/Nargluj_/2013-07-06142941_zpsd6af50f5.jpg[/IMG]]("http://s1312.photobucket.com/user/Nargluj_/media/2013-07-06142941_zpsd6af50f5.jpg.html")
[I]Partitions on my PC as of 2013-07-06. I've waited to extend my sda3 until the first problem is fixed. One thing at a time.



[/I][[IMG]http://i1312.photobucket.com/albums/t529/Nargluj_/2013-07-06152313_zpsc36404d7.jpg[/IMG]]("http://s1312.photobucket.com/user/Nargluj_/media/2013-07-06152313_zpsc36404d7.jpg.html")
*My dxdiag box. It's in Swedish. Should be obvious what each thing means. Most likely in same order as if it where in English.*



[[IMG]http://i1312.photobucket.com/albums/t529/Nargluj_/2013-07-06143333_zps417c7796.jpg[/IMG]]("http://s1312.photobucket.com/user/Nargluj_/media/2013-07-06143333_zps417c7796.jpg.html")
*This one looks familiar. Where have I seen it before???   Right! Each and every time I've said "Let's install Ubuntu today!".*


I took photos of the full error log and put them [[COLOR=#ff0000]_[SIZE=2]**here**[/SIZE]_[/COLOR]]("http://s1312.photobucket.com/user/Nargluj_/library/Error%20report%20Ubuntu%20install%206%20July%202013?sort=3&page=1")! Wasn't able to copy it as text unfortunately.
[http://s1312.photobucket.com/user/Nargluj_/library/Error%20report%20Ubuntu%20install%206%20July%202013?sort=3&page=1](http://s1312.photobucket.com/user/Nargluj_/library/Error%20report%20Ubuntu%20install%206%20July%202013?sort=3&page=1)


Updated "sudo fdisk -l":
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7f67eba2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    33556479    16777216   27  Hidden NTFS WinRE
/dev/sda2   *    33556480    33761279      102400    7  HPFS/NTFS/exFAT
/dev/sda3        33761280  1481742335   723990528    7  HPFS/NTFS/exFAT
/dev/sda4      [2407903232]("tel:2407903232")  2930143231   261120000    5  Extended
/dev/sda5      [2407905280]("tel:2407905280")  2919903231   255998976   83  Linux
/dev/sda6      2919905280  2930143231     5118976   82  Linux swap / Solaris
```


Thank you in advance.
Sincerely Lukas.

---

### Post by oldfred on 2013-07-08
Please attach screen shots not post in your reply. You can use Go Advanced and use paperclip icon to attach your screen shots.

You seem to have  large / (root) partition very far into a large hard drive. Some have had issues with very large . and either needed a small about 25GB / and a separate partition for /home to use the rest of the space you want for Ubuntu. Or you can create a /boot partition fully within the first 100GB of the hard drive, for some that solves boot issues.

---

