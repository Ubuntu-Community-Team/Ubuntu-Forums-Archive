---
title: "will it disturb windows?"
date: 2012-03-21
forum: Installation &amp; Upgrades
---

### Post by jekylhyde on 2012-03-21
Hi
if i'll install linux in the same hdd will it disturb windows?
(will it disturb anti viruses in windows?)

---

### Post by Rex Bouwense on 2012-03-21
No.  Many people dual boot with Microsoft Windows and a Linux OS.

---

### Post by jekylhyde on 2012-03-21
> **Rex Bouwense said:**
> No.  Many people dual boot with Microsoft Windows and a Linux OS.

i ask because in the 90's i installed linux & it messed up my windows :)
so you're 100% sure i can install it?
(it will resize my windows partition & make a new one to linux?)

---

### Post by Rex Bouwense on 2012-03-21
I am 100% sure that you can install it.  As to whether it will mess up your Windows OS, I cannot say.  In the first place that maximum number of primary partitions that you may have on a hard drive is four.  You probably already have four, so one of them has to be made into an extended partition on which you may create any number of logical partitions.
You will need to make a back-up of your OS and your data just in case the installation fails and you cannot recover what is on your hard drive.  That very rarely happens but you are talking about 100% so you better do that.

---

### Post by jekylhyde on 2012-03-21
> **Rex Bouwense said:**
> I am 100% sure that you can install it.  As to whether it will mess up your Windows OS, I cannot say.  In the first place that maximum number of primary partitions that you may have on a hard drive is four.  You probably already have four, so one of them has to be made into an extended partition on which you may create any number of logical partitions.
You will need to make a back-up of your OS and your data just in case the installation fails and you cannot recover what is on your hard drive.  That very rarely happens but you are talking about 100% so you better do that.

how could i check how many primary partitions i have?
& how to make logical?

---

### Post by MasterGamerJK on 2012-03-21
Use Wubi....its MUCH easier!

---

### Post by mastablasta on 2012-03-22
> **jekylhyde said:**
> how could i check how many primary partitions i have?
& how to make logical?
 
 
boot ubuntu (using liveCD or USB) and then run gparted. it will show you how disk is partition and what kind of partitions you have.
 
the only thing that Ubuntu touches and that belongs to windows is master boot record (mbr). it replaces it with it's own called GRUB. this is what boots before lInux or windows is loaded and it gives you a menu with selection of which system to boot.

---

### Post by otherethe on 2012-03-22
> **jekylhyde said:**
> how could i check how many primary partitions i have?
& how to make logical?


Easy way for you, Just boot Ubuntu from live cd, or USB, were it ask what type of install just select side by side with windows and you will be fine Don't goto messing with your partitions because if you do you will mess them, I know this just because of the questions you have asked It's best to just do the side by side installing until you go study more about partitions and how they work.

---

### Post by ottosykora on 2012-03-22
> **otherethe said:**
> Easy way for you, Just boot Ubuntu from live cd, or USB, were it ask what type of install just select side by side with windows and you will be fine Don't goto messing with your partitions because if you do you will mess them, I know this just because of the questions you have asked It's best to just do the side by side installing until you go study more about partitions and how they work.

the danger of blindly doing this is you can completely mess up partitioning on some on many computers, as they will arrive today with 4 primary partitions and attempt to create other partition can cause the existing partitions to change to dynamic one. This happens very often in recent times, as computers , started with HP mainly, arrive in such malconfigured state.
Using 'instal along...' will end up in unusable system quite often.

The best is to check partitioning in advance, crate partitions with proper tools, shrink windows partitions with windows tools and make linux partitions with linux tools.

First then go and install using the 'something else' method in the installer.

---

### Post by jekylhyde on 2012-03-22
the thing is - i think i want to install 2 linuxes side by side windows
(why 2? i didn't decided which i want... ubuntu,xubuntu or mint)

---

### Post by ottosykora on 2012-03-22
well then you should really do partitioning and proper plan for all first and not just go and install and then have dead system.

ubuntu and xubuntu, you do not need to install them separately. This is just the same -buntu, the only difference is the graphical interface. You can install ubuntu and then install xubuntu-desktop from the repository. You will then be asked at login which one desktop you want and you can select ubuntu or xubuntu.

Most of my installs have both desktops installed.

---

### Post by jekylhyde on 2012-03-22
> **ottosykora said:**
> well then you should really do partitioning and proper plan for all first and not just go and install and then have dead system.

ubuntu and xubuntu, you do not need to install them separately. This is just the same -buntu, the only difference is the graphical interface. You can install ubuntu and then install xubuntu-desktop from the repository. You will then be asked at login which one desktop you want and you can select ubuntu or xubuntu.

Most of my installs have both desktops installed.

if i'll resize my windows partition & make out from this partition - 3 partitions (1 - were windows is & 2 more for 2 linuxes, ubuntu & mint)
will that be ok?

---

### Post by ottosykora on 2012-03-23
> **jekylhyde said:**
> if i'll resize my windows partition & make out from this partition - 3 partitions (1 - were windows is & 2 more for 2 linuxes, ubuntu & mint)
will that be ok?

basically yes, but you should also make a swap partition of size abt twice your ram.
It is also fair practice to have separate /home partition.
While some people managed to have same /home partition for more then one linux installation, I personally would recommend to have own partition for each distro.

Also it is often useful to have some extra data partition in windows format, which then can act as universal exchange partition between linux and windows.


Also depends on what windows do you have. If you have w7, then it will have at least 2 partitions alone and they need to be there this way.

---

