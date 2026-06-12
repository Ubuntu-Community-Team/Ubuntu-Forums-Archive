---
title: "A fresh Install with a  Encrypted partition and LVMs"
date: 2014-02-07
forum: Installation &amp; Upgrades
---

### Post by p2bc on 2014-02-07
&#65279;
Please let me start by saying I truly miss the "Alternate" CD
 

Back story / original configuration and setup:
 
Back in 2012, I use Ubuntu Alternate Install CD (ubuntu-12.04-alternate-amd64.iso) to create a:
 - Primary partition (sda1) 200 MB - /boot
 - Logical partition (sda5) 650 GB - crypto /w pass phrase
 -- LVM Group (systm) on the crypto partition
 --- LVMs (systm-lv-root) for / (ie root)
 --- LVMs (systm-lv-usr) for /usr
 --- LVMs (systm-lv-var) for /var
 --- LVMs (systm-lv-tmp) for /tmp
 --- LVMs (systm-lv-swap) for /swap
 --- LVMs (systm-lv-home) for /home
 
For the reasons why, a few quick Google search and that would illustrate the benefits. Just to scratch the surface would be security, because your entire drive is encrypted, including your swap partition. Secondly re-installing were a breeze, since /usr and /home were on their own separate "partition" as long as you did not format these partitions during the install once you re-boot your system everything would be there. [Which I have had to do, using the Alternative CD I must add]("http://ubuntuforums.org/showthread.php?t=2149328"). 

This configuration was beautiful. I really must thank [Uwe Hermann]("http://www.hermann-uwe.de/blog/towards-a-moderately-paranoid-debian-laptop-setup--part-1-base-system"), although I am not as paranoid.
 
Anyways, until recently I haven't had any problems. My laptop has been sluggish and running hot, so I figured I would put Lubuntu on my aging machine. Lubuntu only come as a Desktop release. I boot from the usb stick I see my partition, able to unlock the crypto by clicking on it and entering the pass phrase, all is good. All though Lubuntu is not what I am accustom to it seem to be running smoothly so I play with is for a couple of days before installing.
 
The big day, boot up feeling confiddent after backing up with RSYNC the /home partitions, and since I plan to install I don't hit "Try Lubuntu" I hit "Install Lubuntu" everything thing is pretty boringly standard to this point. I get to the drive selection, I like that I see "Encrypt Partition" and "Use LVM", I start to think, "this won't be half bad", boy was I wrong. I choose "Other..." (ie manual selection). It is a nice graphical interface with rudamentary functionality (MHO) but there is "+" , "-" , "Change". Pretty straight forward I thought. Add a partition, delete a partition, and modify a partition.
 
So I click on sda1 and click "change" and say "use partition", and set mount point to "/boot". So far pretty much identically to the Alternative CD, other than clicking, verse "Tab" "Enter".
 
Now for sda5 (logical encrypted partition). Click on it and click on "change", select "use physical drive for encryption", drop down field ask for pass phase, which I enter the one for the existing crypt partition. Up to this moment absolutely nothing has been different from past experiences. I will say there is no "activate" or "configure" option, just "Ok". So I click "Ok". In the past, using the Alternative CD the LVMs would be listed, and I could select each one and set whether it was to be used for "/" "/home" "swap", and so on. This time not so much, nothing was displayed, but sda1, and sda2 with their appropriate label, /boot and crypto-ads. I get this not so OK feeling. So I click "Quit", reboot, and boot into my primary drive, prompted for my pass phrase, it is accepted, and then prompted that it is empty "No partition found". ??? I shutdown, reboot into the LiveCD of Lubuntu, click on the encrypt partition in PCmanFM again, and prompted for the pass phrase, and nothing. The lock symbol is gone, but the partition was empty. I shut down and put that computer aside.

On an old computer I decide to do some tests:

[LIST]
[*]Test 1: 
[*=1]Install Ubuntu using the Alternative CD recreating all the partitions, encryption, and LVMs from the original configuration. 
[*=1]Using the LiveCD from Lubuntu using PCmanFM, I activate the encrypted partition using the pass phrase. 
[*=1]I proceed to start the install from the desktop icon, following the instructions. 
[*=1]Get to the partition selection window and the LVs are listed since they were previously unlocked. 
[*=1]Everything installed without any problems or errors. 
[*=1]Reboot, system starts without being prompted for a pass phrase I get: 
[/LIST]
[INDENT]  
[/INDENT]
[INDENT=2]```

Gave up waiting for root device. Common problem:
- Boot args (cat /proc/cmdline)
- Check rootdelay= (did the system wait long enough?)
- Check root= (did the system wait long enough?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/mapper/systm-lv--root does not exist. Dropping to a shell!

BusyBox v.1.20.2 (Ubuntu 1:1.20.0-8.1ubuntu1) built-in shell (ash)
Enter ‘help' for a list of built-in commands.

(initramfs)  _

```[/INDENT]
[INDENT] 
[/INDENT]
[INDENT=2]Of course since I unlocked, or  activated the encrypted partition before the install process, the system  did not know to prompt for pass phrase.

Moving forward, thinking ahead, and not always having an Alternate CD,  or wanting to install a system twice to get a similar configuration for  every new iteration or year of Ubuntu. I decided to do further testing.
[/INDENT]


[LIST]
[*]Test 2 : 
[*=1]From LiveCD, using GParted I wiped the drive clean to ensure no residual configurations. 
[*=1]I run the install from the desktop icon. 
[*=1]Get to the partition selection window. Instead of selecting “Other...” I choose "Erase entire drive", and to use “Encryption” and “LVM”. Enter pass phrase and continue. 
[*=1]Quit the installation shortly after when I realized that I could not select separate LVs for mount point. 
[/LIST]
   

[LIST]
[*]Test 3: 
[*=1]Download the [ Minimal Ubuntu CD iso]("https://help.ubuntu.com/community/Installation/MinimalCD"), and burn it to a CD. 
[*=1]It is exactly like the Alternative CD, so much so I have to check twice that I did not accidentally leave the Alternative CD in the cd-rom during the installation. I could configure the drive with all the similar setting and LVs from my original configuration. 
[*=1]The problem as I see it, I won’t always have the ability to be connected to the internet while installing. I am looking for a long term solution here. Downloading a complete ISO, and having on a USB drive is convenient. 
[/LIST]
[INDENT]
[/INDENT]
 So my question is two fold:

[LIST=1]
[*]Is there an easy way, thinking ahead of Ubuntu 14.04 LTS coming in a few months, to set the partitions similar to my original configurations, and use or “activate” encrypt partitions giving access to the LVMs that are already existing, to future Desktop installers? Also not requiring an internet connection as with the Minimal CD ISO.
[*]An secondly, is there a way to salvage the original LVs from the encrypted partition, that did not actually get formatted, but I am assuming the Partition Table got rewritten. Can it be re-built?
[/LIST]


Thanks for your help, and advice.

---

### Post by sudodus on 2014-02-08
There are alternate iso files for Lubuntu 32-bit and 64-bit versions of the current 13.10 version and Trusty Tahr to become 14.04 LTS. I have tested them. See this link for Trusty (you may need to be logged in)

[http://iso.qa.ubuntu.com/qatracker/milestones/308/builds/62684/downloads](http://iso.qa.ubuntu.com/qatracker/milestones/308/builds/62684/downloads)

and I think the security is quite good, even if it might be hard (maybe impossible, I have not tried) to get exactly the configuration you want.

The Ubuntu flavours are portable between different computers (except when proprietary drivers are needed). So you can install your system and make an image of it, which can be ported to other computers. This is true for the desktop versions, but the standard network of Ubuntu Server is not portable.

A cloning tool like ***Clonezilla*** or dear old ***dd*** can do it, clone or make a compressed image, which works in other computers as long as the target drive is at least as large as the source drive.

---

