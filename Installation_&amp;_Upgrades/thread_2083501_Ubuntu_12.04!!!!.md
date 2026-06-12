---
title: "Ubuntu 12.04!!!!"
date: 2012-11-12
forum: Installation &amp; Upgrades
---

### Post by FepzHz on 2012-11-12
I have recently finished building my computer and i currently have no OS installed. I wanted to use my usb 3.0 flash drive as a bootable drive and run ubuntu. I read that ubuntu only needed 2GB of space so i figured my 8GB usb would be enough...but when i poped in the dvd and ran ubuntu live...i tried to install ubuntu(i had all my sotrage drive unplugged from the SATA ports on my mobo, a 128 GB SSD and a 1TB HDD) on the usb drive but it prompt me that i needed at least 8.6GB.... I will be installing windows 7(for gaming and video editing) on the 128 GB ssd, but i won't be doing that untill i get win7 which might take me a couple of weeks....so What i want to know, is, if it would be better to install ubuntu on a larger usb drive(32 GB) or if i should get a 64GB SSD to install ubuntu, or if i should partition the SSD and install ubuntu on there( i read that this is not a good option because it might complicate the windows install )....In other words im not sure on how i should install ubuntu...Ive never used linux in my life but from what i saw in the ubuntu live, reviews, videos, and magazines about ubuntu and linux, im positive i want to make the change but i still need windows for reasons listed, so i will be dual booting, im just not sure on how to go about it, i would appreciate any help

---

### Post by oldfred on 2012-11-12
Welcome to the forums.

Was this a DVD download? I have never used that. I just use the CD versions and then download additional software from repository.

You should be able to create an installer flash drive in less than 1GB, a full install is about 4.5GB but then does not have any room for updates. Normally a full install should be 10GB as a minimum.

If you have not used Ubuntu a lot I would create the USB installer and install to the hard drive. It then will not be as fast as SSD, but if you decide you like Linux then you can install it to SSD.

I have a 60GB SSD with two installs of Ubuntu, each in a little less than 28GB. All data is on  my spinning drives. Windows though needs a lot larger system partition even if you still have most of your data on the rotating drive.

Is this system a new UEFI/BIOS system? If so you have to partition with gpt not MBR(msdos) for the installs. If you just want BIOS mode then you have to partition with MBR. Windows only installs to gpt drives with UEFI. And UEFI needs gpt partitioned. Ubuntu will boot from rotating drive in either gpt or MBR with either BIOS or UEFI. But how you install Windows has to the the way you install Ubuntu, both UEFI or both BIOS. Each will boot 64 bit installers in either UEFI or BIOS mode and how installer is booted is how it will install.

---

### Post by FepzHz on 2012-11-12
It was a Ubuntu 12.04 Precise Pangolin bootable&Installable Live DVD from..Its an intel core i5 3570k on an Asrock z77 exteme 4, i believe its UEFI.... so i'd have to install both win 7 and ubuntu with a gpt partition on the ssd. Is it better to install windows first? Would it be ok if win7 is on a 30 GB partition and ubuntu on a 15GB? Or how should i distribute the partitions on the ssd?

---

### Post by oldfred on 2012-11-13
Someone posted this, so be sure to use the correct ports. Do not use A0 or A1.

AsRock calls BIOS mode AHCI.
> "Launch EFI Shell from Filesystem Device" in the Exit tab of Asrock motherboard
Asrock Extreme4 Z77 motherboard, which has 4 SATA3 ports: 2 Intel ports (0 & 1) and 2 Asmedia ports (A0 & A1).Had my DVD drive connected to one of the Asmedia ports (A1), and so I tried switching the connection to one of the Intel SATA2 ports and the errors went away.


UEFI, Windows on SSD, Ubuntu on HD ASRock Z77 Pro4 motherboard
[http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/](http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/)

I prefer to have an operating system on every hard drive which I do. But I also want to boot and run system partitions from SSD, since it is much faster. Data then can be on rotating drive as you access that a lot less. 
Most report Windows wants lots of space. I would install Windows first as it also wants several partitions. Then Ubuntu. 
Ubuntu would be fine in 25GB, so you could use the rest as Windows as the support partitions are small.

I also keep /home inside my / on the SSD as the hidden user settings are used more. But all data folders and most of the hidden data folders in /home get moved to data partitions on rotating drive & linked back into /home. I use 9GB of my 25GB root partition. About 2GB is my /home and most of that is .wine for the Windows version of Picasa as I do not move that.

[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)

[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell)

---

### Post by FepzHz on 2012-11-13
Ok understood, the links you provided were very helpful also. I think for right now, I'll install ubuntu 12.04 on 25 GB partition on my HDD. Im not to worried about speed right now, i just want to have an OS on my system. As soon as i got windows7 installed on my ssd with its partitions then i'll delete the ubuntu on my HDD(i keep all the files i use on multiple flash drives, so i won't be having too much data saved on there) and then I'll do a fresh install of ubuntu on a  partition in the SSD. Keeping the /home in the / (im guessing / means root? root folder?) on the ssd and having the data folders moved to data part ions on the HDD might be a bit to confusing for me as far as making those multiple partitions and having /home data folders linked back to the /home SSD. I think, I understand the idea but im just not sure if i would be capable of doing it successfully. One last thing would you recommend 30 GB partition for ubuntu, once its finally moved to the ssd (to have extra space just in case i make any changes) or is 25 GB more than enough? Also, is there i way i can make it so ubuntu saves all the files, docs, media files, etc. automatically to my HDD or will i have manually select the drive when i choose to save? Im terribly sorry if im asking too much, i know i got a little bit of topic, but i just want to get my doubts out of the way.

---

### Post by oldfred on 2012-11-13
I am real aggressive about moving data from /home into my data partitions, so a little more space in / (root) is ok. I have two data partitions, one NTFS to share with Windows and now since not booting XP anymore most data goes into a shared LInux formatted partition.

In my data partition I created folder for all the standard folders in /home like Documents, Music etc. Then with one command I can link them all back. All data is then automatically saved to data partition but system still sees all the standard folders. I then also moved some of the hidden folders like the Firefox & Thunderbird profiles to a shared NTFS partition so I have same email & bookmarks in both Windows & Ubuntu.


Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)

You need to mount data partition(s) in fstab to use them first. You have to create a mount point or name, I use shared for my NTFS and data for my Linux partition (real creative I know :) ). And add them to fstab. Best just to copy example and edit to your exact UUID and name of mount point.

[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6

---

