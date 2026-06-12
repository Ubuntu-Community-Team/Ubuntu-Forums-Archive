---
title: "how to allocate more disk space for ubuntu"
date: 2012-06-21
forum: Installation &amp; Upgrades
---

### Post by saipranav on 2012-06-21
Hi, ):P
I have installed Ubuntu version 12.x on my laptop just a few minutes back, while installation i was given the option of allocating a maximum of 30 GB on my C drive which has a capacity of 75 GB. I was also given an option of installing Ubuntu on my D drive but i didnt go for it. Now my question is, how can i uninstall Windows Vista and allocate my D drive and the remaining C drive to Ubuntu. I also have a couple of files in my D drive which i want to use here. Thanks in advance for the help.
Regards
Sai

---

### Post by dino99 on 2012-06-21
the solution is :

- to boot on the livecd (liveusb) to be able to use a formatting tool like gparted
- if you want the erase winblow, then format its partition

then take care to organize your hhd with less than 4 primary partitions, ideally create the first one as "primary", then create an "extended" partition using the rest; in which you'll be able to create as many secondary partitions as you want.

- but you need to remember where the grub loader has been installed ; aka if it has been installed on the winblow partition, then after removal you need to install it on the ubuntu hdd , with (sudo grub-install /dev/sda or /dev/sdb , aka the ubuntu location)

here is how i do installation:
[http://ubuntuforums.org/showpost.php?p=11843514&postcount=9](http://ubuntuforums.org/showpost.php?p=11843514&postcount=9)

---

### Post by saipranav on 2012-06-21
Hey dude,i'am a total beginner when it comes to linux/ubuntu, just started today and i find it difficult to follow our instructions.
This is what i'am going to do. I'll download EasyBCD or something and try uninstalling ubuntu which is on the same drive as my vista, after this i'll download ubuntu freshly and put it in a CD.
What should i do after this step?

---

### Post by black veils on 2012-06-21
hey people, wait, they used Wubi !  so the short answer is, you need to backup your data, and applications settings. then do a clean install of ubuntu to your disk, not just within windows.

are you wanting to wipe your harddrive clean of any windows etc, and have just ubuntu on the computer?

---

### Post by Mark Phelps on 2012-06-21
> **saipranav said:**
> Hi, ):P Now my question is, how can i uninstall Windows Vista and allocate my D drive and the remaining C drive to Ubuntu.
Apparently, as has been noticed, you installed using Wubi.  That means that Ubuntu is in a file INSIDE your "C" partition.  If you remove Windows, you will also remove Ubuntu.
>  I also have a couple of files in my D drive which i want to use here. Thanks in advance for the help.
Your "D" drive is a partition, and most probably, an NTFS format at that.  You can't install to an NTFS partition other than using Wubi.  So, the best thing to do is leave the "D" partition alone.  You will be able to use that from inside Ubuntu as it can read and write NTFS partitions.

---

### Post by jmate24 on 2012-06-21
Hey just get a 2nd usb hdd and backup your files to it then scrub the whole thing by formating it with gparted in the live cd environment with the option of "Try Ubuntu Before Installing" and put Ubuntu on it if you would like.

---

### Post by saipranav on 2012-06-22
Hey guys,
You guys are right, i used wubi to install ubuntu, sorry for not mentioning that, and yes, i would like to uninstall windows completely and run ubuntu only.

@Mark Phelps:Can you tell me how i can access my D partition from inside Ubuntu currently?

@jmate24: Dude, Ibacked up all my data as you said. Now how do i format the system? And after formatting how do i get ubuntu back into the computer from the USB drive.

@black veils: Hey! I finished backing up my data, now i'm in the process of downloading ubuntu to my USB drive.
what steps should i follow next to remove windows and have just ubuntu on my system.

Thank you all for your replies.
Regards,
-Sai

---

### Post by black veils on 2012-06-22
get your .iso image md5sum:
[https://help.ubuntu.com/community/UbuntuHashes]("https://help.ubuntu.com/community/UbuntuHashes")

Verify .iso integrity:
Scroll down to.. MD5SUM with "Checksums
calculator" 
[https://help.ubuntu.com/community/HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")

put .iso image to usb flash drive:
[http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/")

install ubuntu:
[http://news.softpedia.com/news/Installing-Ubuntu-12-04-LTS-266201.shtml]("http://news.softpedia.com/news/Installing-Ubuntu-12-04-LTS-266201.shtml")

---

### Post by zombifier25 on 2012-06-22
> **saipranav said:**
> @Mark Phelps:Can you tell me how i can access my D partition from inside Ubuntu currently?

@jmate24: Dude, Ibacked up all my data as you said. Now how do i format the system? And after formatting how do i get ubuntu back into the computer from the USB drive.

@black veils: Hey! I finished backing up my data, now i'm in the process of downloading ubuntu to my USB drive.
what steps should i follow next to remove windows and have just ubuntu on my system.

Thank you all for your replies.
Regards,
-Sai

Ubuntu can read/write NTFS partitions.

If you want to remove Windows, install Ubuntu to a partition of its own first, so that Grub can overwrite the MBR. When you're done, boot again into a liveCD/USB, remove Windows' main partition (keeping the D partition), and then allocate the unused space to Ubuntu.

---

### Post by saipranav on 2012-06-23
Hey guys,
I have downloaded an iso file from the ubuntu website and created a disk containing ubuntu. When i tried to boot through the DVD and install ubuntu, my keyboard ad mouse stopped working, i search about this on the net and found a lot of similar problems in the case of ubuntu, but im not able to understand anything and im totally new to linux, somebody please help me.

Edit: I was not facing this problem when i used ubuntu installed through 'wubi'

---

### Post by nipunshakya on 2012-06-24
[http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/)
 tells you how you can install a dual boot.... 
look at the following link too to run gparted in liveCD mode...
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Regarding LiveCD download, whenever you download a liveCD, always boot from it first, select 'check drive for errors' and after the cd is error free, try running it in live mode, i.e. select 'try ubuntu' before actually going for an installation on your HDD. Then, follow link #1 and see link #2 for partitions and all.. Goodluck

---

### Post by saipranav on 2012-06-24
> **saipranav said:**
> Hey guys,
I have downloaded an iso file from the ubuntu website and created a disk containing ubuntu. When i tried to boot through the DVD and install ubuntu, my keyboard ad mouse stopped working, i search about this on the net and found a lot of similar problems in the case of ubuntu, but im not able to understand anything and im totally new to linux, somebody please help me.

Edit: I was not facing this problem when i used ubuntu installed through 'wubi'

> **WinuxUser said:**
> [http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/)
 tells you how you can install a dual boot.... 
look at the following link too to run gparted in liveCD mode...
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Regarding LiveCD download, whenever you download a liveCD, always boot from it first, select 'check drive for errors' and after the cd is error free, try running it in live mode, i.e. select 'try ubuntu' before actually going for an installation on your HDD. Then, follow link #1 and see link #2 for partitions and all.. Goodluck

Thanks for the links.
But my problem is not solved yet, i do understand that trying out a liveCD before installing it is a safe option, but i'm not able to move my cursor or use the keyboard, so i'm not able to select the option of booting from my cd also... ubuntu is just not recognizing my keyboard/optical pad.

**EDIT:** Forgot to add one more thing, when i try to put the ubuntu CD and boot through it, before the window where i can "choose to try ubuntu from the cd or install it on my system" appears for a few seconds on the bottom of the screen i find two small icons, one looks like a keyboard and the other is a human with a circle around him, i dont know what these icons mean, after the window with the options come, i also see a keyboard symbol on the top right corner of my screen...

---

### Post by nipunshakya on 2012-06-24
Those symbols in your bottom screen about a human and keyboard? well just ignore them, they are nothing... when they appear, press any key from keyboard... you would be asked to select the language i guess.. and then you can see a list of options like checking disk for errors, installing ubuntu, trying ubuntu etc...

---

### Post by saipranav on 2012-06-25
Hey guys, thanks for all the help.
I managed t install ubuntu 12.04 and its working like a gem.
Ubuntu is 9.5 times faster than vista in starting the system!!!
Just one last doubt, is there any program like 'readyboost' on ubuntu?

---

### Post by nipunshakya on 2012-06-25
[http://ubuntuforums.org/showthread.php?p=11418246](http://ubuntuforums.org/showthread.php?p=11418246) might help..

---

### Post by saipranav on 2012-06-26
> **WinuxUser said:**
> [http://ubuntuforums.org/showthread.php?p=11418246](http://ubuntuforums.org/showthread.php?p=11418246) might help..

Thanks for the link. I'm running ubunto 12.04 OS now, but i'm having lot of problems with it, to start with, the ubuntu software center is not working, its hanging and force closing when ever i open it.

When i type sudo apt-get update, after downloading some stuff i get an error...
The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Automatic Signing Key <ftpmaster@ubuntu.com>

The continuation of the error is also on the top bar (error symbol).
It says "Error opening the cache (E:Encountered a section with no Package:header, E:Problem with mergeList/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.)'

---

### Post by nipunshakya on 2012-06-26
[https://answers.launchpad.net/ubuntu/+source/update-manager/+question/194077](https://answers.launchpad.net/ubuntu/+source/update-manager/+question/194077) this problem is similar you yours..and i had it in my system too for a while... try it..

---

### Post by saipranav on 2012-06-26
> **WinuxUser said:**
> [https://answers.launchpad.net/ubuntu/+source/update-manager/+question/194077](https://answers.launchpad.net/ubuntu/+source/update-manager/+question/194077) this problem is similar you yours..and i had it in my system too for a while... try it..

Thanks a lot, that solved all my issues. You have been of great help to me :D

---

### Post by nipunshakya on 2012-06-26
Oh wow... please mark the thread as [SOLVED] selecting the 'Mark thread as solved' from the 'Thread Tool' located on the top right corner of this thread. That way, others can find help easier with similar issues to yours too....


Goodluck and Happy Linuxing

---

