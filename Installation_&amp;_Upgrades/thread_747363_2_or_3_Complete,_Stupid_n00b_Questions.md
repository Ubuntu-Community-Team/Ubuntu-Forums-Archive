---
title: "2 or 3 Complete, Stupid n00b Questions"
date: 2008-04-06
forum: Installation &amp; Upgrades
---

### Post by colourmeawesome on 2008-04-06
Okay. You'll have to forgive my idiocy and potential long-windedness, but I'm a total idiot when it comes to Ubuntu/Kubuntu/Linux/Whatever.

Okay, so I think that all of my questions have to do with installation and upgrading.

Question Number 1: I decided to run a dual-boot configuration with Kubuntu 7.1 (GG) and Windows Vista Home Premium on my Dell Inspiron 1501 to test out whether or not Kubuntu was going to be worth keeping. I decided about 3 minutes in that I absolutely love the system, and I'm going to find out the best way to use it as my primary operating system. The actual question: Is it possible to, from Kubuntu, get rid of Windows and the partition that it's on, so that I'll have full use of my harddrive (or even like, expanding the Free Space partition on my HDD).

Question 2: I'm pretty sure I already know the answer to this, but once I have it fully controlling my system, at the end of the month, when they release 8.04 (HH), can I apt-get 8.04 (HH) from Terminal and update 7.1 (GG) to Hardy Heron, without having to burn it onto another disk, etc?

Thanks in advance for any help offered.

-Cass

---

### Post by Rocket2DMn on 2008-04-06
1) Using the GParted LiveCD you can delete the windows partition and grow your Ubuntu partition to use the free space - [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
Of course, make sure you have all your important data backed up first.

2) You can use the Update Manager to upgrade from Gutsy to Hardy.  Details are found here - [https://help.ubuntu.com/community/HardyUpgrades](https://help.ubuntu.com/community/HardyUpgrades) - but you should wait until Hardy is stable before upgrading.  It will have to download a lot of packages, so the upgrade might take awhile, but you won't have to reinstall.

---

### Post by mgmiller on 2008-04-06
> Question Number 1: I decided to run a dual-boot configuration with Kubuntu 7.1 (GG) and Windows Vista Home Premium on my Dell Inspiron 1501 to test out whether or not Kubuntu was going to be worth keeping. I decided about 3 minutes in that I absolutely love the system, and I'm going to find out the best way to use it as my primary operating system. The actual question: Is it possible to, from Kubuntu, get rid of Windows and the partition that it's on, so that I'll have full use of my harddrive (or even like, expanding the Free Space partition on my HDD).

Use synaptic package manager to install gparted, or you can install it from the command line:
```
sudo apt-get install gparted
```

Once it's installed, you will find it in System > Administration > Partition Editor.

This should let you wipe out the old NTFS partition.  I am not sure if it will let you expand your current linux Ext3 partiition into the unused space because it's mounted while you use it.

If you go here: 
[http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/")

you will find a link to down load a live CD version of gparted.  You would burn that to Cd, and then boot off of it.  This will allow you to expand your entire disk to the Ext3 partition.  Be very careful how you do this, it is easy to wipe out the stuff you want to keep.

Of course, if you do mess up, it is easy to install Ubuntu fresh from the live CD and tell it to use your entire hard drive.  This would also wipe out any existing ntfs partions in the process.  Just be sure you have backed up anything from the old partitions before you do this.


> Question 2: I'm pretty sure I already know the answer to this, but once I have it fully controlling my system, at the end of the month, when they release 8.04 (HH), can I apt-get 8.04 (HH) from Terminal and update 7.1 (GG) to Hardy Heron, without having to burn it onto another disk, etc?

When 8.04 goes to final release, your update manager will tell you there is a new release available and will ask you if you want to install it.  This will upgrade the whole system to 8.04 keeping all your programs intact.  

If you look at my signature line below, you will see that I have been doing this for quite a while.  It used to take some real tweaking to get things running again, but for the last few upgrades it's gone very smoothly.  

The trick is to have installed things, especially your video drivers only from the ubuntu repositories.  As long as you didn't use any 3rd party things like easy ubuntu or envy, it should work just fine.

---

### Post by colourmeawesome on 2008-04-06
Thank you for that info. Those answers were exactly what I was looking for.

There's another thing I love about Open Source. Communities of people who know what they're talking about.

---

### Post by Darkdelusions on 2008-04-06
1) If you havent installed Kbuntu the installer will take care of this for you. If you have you can use gparted to resize your drives. 

2) You are correct. The update manager will alert you there is a new release out or you can use sudo apt-get upgrade. Normally when a new release come out I will download the live CD and format my root partition. I have upgrade blow (Not Just ubuntu) blow up on me in the past and thing would not work correctly.

---

