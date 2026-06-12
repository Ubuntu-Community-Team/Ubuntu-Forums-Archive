---
title: "Installation of Ubuntu on a new HDD??"
date: 2010-10-17
forum: Installation &amp; Upgrades
---

### Post by pepperwood on 2010-10-17
Just received an installation CD of Ubuntu 10.10 to be installed on a new HDD by itself. By that I mean that Windows OS is not preinstalled at this time. This is a Home Built PC with a single HDD & no OS. What procedure to follow and How should I partition the HDD for Ubuntu? I have 80 GB to work with. Would like to install Ubuntu and possibly install Windows OS at a later time on same HDD? If I was to install Windows later would I be able to repartition the drive to accommodate Windows, for now? Just a thought! Your assistance would be very much appreciated. PW

---

### Post by garvinrick4 on 2010-10-17
> **pepperwood said:**
> Just received an installation CD of Ubuntu 10.10 to be installed on a new HDD by itself. By that I mean that Windows OS is not preinstalled at this time. This is a Home Built PC with a single HDD & no OS. What procedure to follow and How should I partition the HDD for Ubuntu? I have 80 GB to work with. Would like to install Ubuntu and possibly install Windows OS at a later time on same HDD? If I was to install Windows later would I be able to repartition the drive to accommodate Windows, for now? Just a thought! Your assistance would be very much appreciated. PW Just install
for now using whole drive can always resize later if wanted. Put Cd in and boot off of it
hit install and answer questions using whole drive and if asked where do you want grub it is in sda which is your drive. Then the grub will be put in the mbr (master boot record) where it belongs and system will be bootable. That is the simplest way for you to do it on first go
around. Enjoy. Ubuntu will partition for you do not worry about that.

---

### Post by JBAlaska on 2010-10-17
If your going to be installing windows, You might want to install it first and when it asks about partitioning, make a primary partition with the amount of space you want for windows NTFS and leave the rest unallocated.

Then install Ubuntu as garvinrick4 suggested using the "Largest continuous free space" option.

Installing windows first saves a bit of hassle in the long run.

---

### Post by pepperwood on 2010-10-20
> **garvinrick4 said:**
> Just install
for now using whole drive can always resize later if wanted. Put Cd in and boot off of it
hit install and answer questions using whole drive and if asked where do you want grub it is in sda which is your drive. Then the grub will be put in the mbr (master boot record) where it belongs and system will be bootable. That is the simplest way for you to do it on first go
around. Enjoy. Ubuntu will partition for you do not worry about that.

I decided to take this step and everything has gone satisfactory. Ubuntu is now up and running on the PC. Will need some time to become familiar with its applications & to see if it will work for me. Thank you! PW

---

### Post by pepperwood on 2010-10-20
> **JBAlaska said:**
> If your going to be installing windows, You might want to install it first and when it asks about partitioning, make a primary partition with the amount of space you want for windows NTFS and leave the rest unallocated.

Then install Ubuntu as garvinrick4 suggested using the "Largest continuous free space" option.

Installing windows first saves a bit of hassle in the long run.

Thanks JBAlaska - You make a good point. At this time I will have one PC for Linux and one PC for Windows. That may lead to one PC an one HDD with dual boot, or one PC with dual HDDS one for Linux and Windows. Depends on how much I can comprehend with Linux, etc. :confused: PW

---

### Post by ratcheer on 2010-10-20
> **pepperwood said:**
> Thanks JBAlaska - You make a good point. At this time I will have one PC for Linux and one PC for Windows. That may lead to one PC an one HDD with dual boot, or one PC with dual HDDS one for Linux and Windows. Depends on how much I can comprehend with Linux, etc. :confused: PW

It took me a little over a year to almost completely wean myself from Windows. I now use Ubuntu about 99% of the time. About the only thing I still use Windows for is iTunes. I also still have an NTFS formatted 1.5 TB external drive connected to it containing many years of data archives, such as photos. I would like to have that on my Linux machine, but I don't care to fool with doing it.

However, I still keep the Windows machine running all the time, because everyone else in the house (including me, from Ubuntu) accesses the networked laser printer. I find it easier to do that than to try to set up the printer on the Linux host and get everyone satisfactorily connected to it.

But, yes, I think separate hosts machines is the best way to go for running Linux and Windows.

Tim

---

### Post by pepperwood on 2010-10-29
Installation has been successful - SOLVED!:)

---

