---
title: "Preparing a hard drive for installation"
date: 2010-05-21
forum: Installation &amp; Upgrades
---

### Post by MJMC on 2010-05-21
Hi Guys
 
Ive an IBM Thinkpad T41 that im hoping to isntall Ubuntu on.
I installed it with dual boot as windows xp was already on it and all went fine.
 
Now Ive downloaded the lastest Ubuntu release and burnt it to disk. Here's my question
 
I have several spare hard drives that will slot internally into my Thinkpad
Most if not all are formated to NTFS
 
My question is, and believe me i have search for days about this.
From what I have searched, 
-I dont need to format this drive to ext3 to install ubuntu?
-However any drives Ive tried all NTFS and tried booting from the CD just cause my installation to hang, just boots to a black screen
 
-The same CD will allow me to install a dual boot so I know its not the Disk.
 
Do i need to format my drive first? I dont want a dual boot system I just want a fresh install 
 
Thanks for the help

---

### Post by darkod on 2010-05-21
It's not necessary to format the disk first because the ubuntu installer will format it during the install process.

However, you need to figure out why it doesn't want to boot the cd now. It should boot the cd even if the hdd has no OS on it, that's the point of installing an OS. :)

Can the hdd be faulty and is blocking the laptop from proceeding with boot? But it seems you said you tried a few disks.

---

### Post by iponeverything on 2010-05-21
there are quite a few options for filesytems. 

ext2, ext3, reiserfs, xfs, etc. etc. etc. ntfs is not one of options though. 

having an ntfs formated drive in system should cause install to hang, and have not heard of anyone having a similar issue -- so I assume that is not the cause of your install hang. 

Assuming you can get the system to make it that part install, there will be an option to tell it use the entire disk. 

10.04 seems to very picky compared to past releases when it comes to older hardware -- so my guess is that it is that it is not that fact that drive is formated ntfs that is causing your problems -- but rather just 10.04.  Nothing later than 9.04 seems to agree with X31 -- and for me that is not really a big deal -- as I have all of the functionality that require in 9.04.. no biggie -- I don't really care that much about about all of cosmetic enhancement and the updates in the interface tools. 

Granted they are nice, cool, pretty and I am sure handy for some they don't affect at all what I use my machine for on a day to day basis.  I do find quite amusing that many people it seems to be the latest release or nothing! IMO 8.04, 8.10, 9.04 and 9.10 are all very good releases. 

My point is that perhaps you should give 9.10 a shot and start working your back. If you don't want to go that route there are many other very high quality distributions out there beside Ubuntu that might want to experiment with. 

I am not putting down ubuntu at all, I love it and have used it now since 8.04 coming from debian -- its just that its big world out there - don't limit yourself.

---

### Post by MJMC on 2010-05-21
iponeverything & darkodThanks both of you for your help.
 
This has been driving me mad, im dying to move from windows and teach myself ubuntu.
 
Darkod,
Yeah as you've said ive tried a few disks so im unsure what the problem is.
The laptop just boots from cd then just a black screen with a blinking cursour.
Thanks for the reply mate
 
iponeverthing
After reading your post I think you've made up my mind for me, what i'll do is download 9.04 to a cd see does that install and see can I update it from there if needs be.
 
Thanks both of you for your help, i'll let you know how it goes.

---

### Post by srs5694 on 2010-05-21
Try downloading [PartedMagic](http://partedmagic.com/) and [System Rescue CD](http://www.sysresccd.org/) and see if they'll boot. If either one boots, you should be able to set up your partitions using it rather than the Ubuntu installer. The GParted program is the usual choice for this, but there are others, such as the text-mode parted, fdisk, and gdisk. I'd set up three partitions:


[list]
[*]A 5-20GB partition (depending on the available disk space and how much software you plan to install in Ubuntu) to be used as the root (/) filesystem in Linux.
[*]A partition of 1-2 times the size of RAM in the computer to be used as swap space.
[*]Everything else to be used as a /home partition to store user data.
[/list]


The root (/) and /home partitions should hold Linux-native filesystems, such as ext3fs, ext4fs, ReiserFS, XFS, or JFS. Ext4fs is the default for Ubuntu, but it's not likely to be much better than the older and better-tested ext3fs or ReiserFS. Any of these filesystems should work fine, though. The swap partition holds swap space, not a filesystem per se. The GParted and parted programs will both create partitions and filesystems (or swap space). If you use fdisk or gdisk, you create the partitions in the partitioning program (fdisk or gdisk) and then create filesystems or swap space with other text-mode programs (mkfs or mkswap); however, the Ubuntu installer should also enable you to create filesystems at install time.

When you install Ubuntu, assuming the install gets further, you should select the "manual" or "advanced" partitioning option (I don't recall which term is used) and then assign the root (/) and /home partitions to the like-named mount points. Swap should be detected and used automatically, IIRC.

---

