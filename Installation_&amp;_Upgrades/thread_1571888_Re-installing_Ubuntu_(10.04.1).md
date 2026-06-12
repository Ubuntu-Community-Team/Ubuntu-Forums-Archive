---
title: "Re-installing Ubuntu (10.04.1)"
date: 2010-09-10
forum: Installation &amp; Upgrades
---

### Post by prroots on 2010-09-10
I am a relative Ubuntu newbie. I've been running a dual boot WindowsXP and Ubuntu 10.04 system without problems for about 1 month. I want to do a clean install using Ubuntu 10.04.1 to get a fresh start. I'm using the manual partition option. Here is my intended layout (at the moment I'm using gparted from the Live CD to steal 2G from the Data partition to create the Ubuntu swap partion):[INDENT]   /dev/sda1     ntfs   Windows XP       24.41G
  /dev/sda2     extended
     /dev/sda5  ext3   Ubuntu main        9.75G  mount = /
     /dev/sda6  ext3   Ubuntu swap       2.00G
     /dev/sda7  ntfs    Data               112.88G
[/INDENT]I use the Data partition for my Windows data. I also copy from Ubuntu home to Data for backup.I have just done several installs with 10.04 (from bootable thumbdrive and receive an I/O error abut 60% into the install (errno 5) for no apparent reason. I since downloaded 10.04.1 and will give that a try. My questions is that during the install you can click on Advanced and it gives you some options for boot loaders. What is the correct choice so that I have the options of booting to either Windows or Ubuntu? Also, I'd appreciated any feedback on the appropriateness of my partition layout above. Thanks
Pete

---

### Post by andrewthomas on 2010-09-10
> **prroots said:**
>  What is the correct choice so that I have the options of booting to either Windows or Ubuntu? Also, I'd appreciated any feedback on the appropriateness of my partition layout above. Thanks
PeteLet it install grub to the MBR of sda.  As for your partition layout.  I would say that your ubuntu root partition is a bit small.

---

### Post by lindsay7 on 2010-09-10
i agree,  i would set up the partitions like this


sda1 for windows --ntfs
sda2 for the "root /" partition assign 20gig --ext4
sda3 for the "home" partition assign 50gig --ext4
sda4 extended partion 
sda5 for the "data" partition assign 50gig --ntfs or fat32
sda6 for the "swap" partition assign 2gigs


when you do a clean install for updating in the future you will only install the operating system i.e the new version of Ubuntu to the / or root partition and and leave the other partiions alone (do not reformat them).. this way all your other settings and data remains untouched.

---

### Post by prroots on 2010-09-10
> **lindsay7 said:**
> i agree,  i would set up the partitions like this


sda1 for windows --ntfs
sda2 for the "root /" partition assign 20gig --ext4
sda3 for the "home" partition assign 50gig --ext4
sda4 extended partion 
sda5 for the "data" partition assign 50gig --ntfs or fat32
sda6 for the "swap" partition assign 2gigs


when you do a clean install for updating in the future you will only install the operating system i.e the new version of Ubuntu to the / or root partition and and leave the other partiions alone (do not reformat them).. this way all your other settings and data remains untouched.Thanks for the feedback. I understand your logic about future updates, etc. I see you suggest placing Ubuntu in a primary partition vs a logical partition. The swap partition is in a logical partition. What are the pros and cons for your layout vs the one I used? Also, why ext4 and not ext3?
Pete

---

### Post by lindsay7 on 2010-09-10
windows wants to be on a primary and i think that the ubuntu os and home is better of on one too. ext4 is the newest and fastest for linux plus it supports the new grubs. My suggestion will let you do upgrades and not mess with your other partitons, just be sure when you do a clean install that you only mark the root or / partiton as being reformatted and do not mark any of the others for formatting. This way updating or repairs will not screw up your system.  ext4 is the newest and why would you not want to format your linux drives that way, I could be wrong but that is why the new os is created that way.  You could put the home partition under the extended one if you want but i find it eaiser to work with primary partitions if you ever need to grow or shrink one vs working with an extended partition.

---

