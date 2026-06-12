---
title: "help me to upgrade/install ubuntu10.04 without losing xp,windows7"
date: 2010-06-07
forum: Installation &amp; Upgrades
---

### Post by RajuV on 2010-06-07
[FONT=Lucida Console][SIZE=4]hi

    iam a new one to this forum. i need help regarding the following matter:

    i have two hard disks(80gb, 250gb). iam using 80gb hard disk for running operating systems and 250gb for general purpose. forget about 250gb hdd for a while. 

    few months before, i decided to install 3 operating systems(xp, windows7, ubuntu9.10). so i made 4 partitions in my 80gb harddisk to make room for them. first of all i installed windows xp sp3(in 1st partition) and then windows 7-64bit(in 2nd partition). windows 7 successfully picked up the windows xp boot entry. after that i installed ubuntu 9.10(not sure 32 or 64bit) in 3rd and 4th partitons. 3rd partition is for ubuntu, 4th partition is for swap. ubuntu picked up the windows 7 boot loader entry in its GRUB boot loader. so far everything is ok. 

    whenever i boot my system, first of all i get grub boot loader showing the following entries:

** ubuntu, linux 2.6.31-14-generic
** ubuntu, linux 2.6.31-14-generic (recovery mode)
** memory test (memorytest 86+)
** memory test (memorytest 86+, serial console 115200)
** windows 7 (loader) (on /dev/sda1)

    to get ubuntu, i go for 1st option. i go for last option to get windows 7 or xp, which shows the following:
** earlier version of windows
** windows 7

    recently i updated my ubuntu online. during updation it asked me to choose some settings to update grub too. i dont remember what i did. after successful updation, i got my grub boot loader(version 1.97~beta4) like:

** ubuntu, linux 2.6.31-19-generic
** ubuntu, linux 2.6.31-19-generic (recovery mode)
** ubuntu, linux 2.6.31-14-generic
** ubuntu, linux 2.6.31-14-generic (recovery mode)
** memory test (memorytest 86+)
** memory test (memorytest 86+, serial console 115200)
** windows 7 (loader) (on /dev/sda1)

    now iam planning to upgrade ubuntu 9.10 to ubuntu 10.04 LTS(32bit). i tried to upgrade directly through online, but the setup couldnot able to fetch all updates everytime. alternatively i downloaded the torrent ubuntu-10.04-alternate-i386.iso, mounted it and tried to upgrade from that image in ubuntu. but this setup is also connecting to internet to fetch updates even i said no to do that when it asked to do so. when i allowed it to fetch updates, setup resulted the earlier situation stating that setup couldn't able to fetch all updates.(im sure my net connection is active and ok).

    so my attempt to upgrade through internet is failed. my next attempt to upgrade from a mounted image is also failed. finally i left with one option. i downloaded the torrent ubuntu-10.04-desktop-i386.iso. i made a cd from it. iam ready to install by using Installation CD directly. here my doubt arises. do i lost boot entries to xp,windows7 if i make a fresh installation by formatting linux and swap partitions? if so, what should i do to keep them with a fresh installation of ubuntu linux 10.04. i dont want to loose xp or 7. what should i do now? suggest me.

    thanks in advance. 

                            RajuV
[/SIZE][/FONT]

---

### Post by darkod on 2010-06-07
If during the install of 10.04 you select manual partitioning option, you can install on the same root and swap partitions.
You will not lose windows if installing like that and formatting root. But you will lose any personal files or data inside your ubuntu, your Home folder, etc.

---

### Post by Mark Phelps on 2010-06-07
In terms of your boot entries, once you have 10.04 up and running, boot into it, open a terminal, and enter "sudo update-grub".  That will auto-generate a new grub.cfg file, which should then contain entries for your other OSs.

---

