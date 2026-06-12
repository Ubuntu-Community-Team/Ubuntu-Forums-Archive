---
title: "Operating System Not Found"
date: 2012-04-30
forum: Installation &amp; Upgrades
---

### Post by sagarvarule on 2012-04-30
Hi All,
 
I had Windows 7(64 bit) and Ubuntu 11.10 (32 bit) dual boot configuration on my Acer 4750 laptop.
 
I downloaded the Ubuntu 12.04 lts (64-bit) from there offical site and Installed it via USB.
 
I did fresh installation. 
 
Option taken for Install : Erase everything and install 12.04 lts.
 
So everything was wiped out of my HDD and it performed Installation successfully. After Restart I got below Error.
 
Broadcom UNDI PXE-2.1 v12.2.0
Copyright (C) 2000-2009 Broadcom Corporation
Copyright (C) 1997-2000 Intel Corporation
All rights reserved.
PXE-E61: Media test failure, check cable
PXE-M0F: Exiting Broadcom PXE ROM.

Operating System not found
 
I have googled..and majority of forum say "Hardware Issue"...and none provide any solutions.
 
Interesting point is: After getting this error I installed Ubuntu 11.10 32bit..I it works properly(So I am convinced its not hardware issue for sure).
 
But Again I install Ubuntu 12.04 with same option. And again this error comes
 
PXE-E61: MEDIA TEST FAILURE, CHECK CABLE...
Operating System not found
 
...Please help....Ubuntu 12.04 is disappointing me!!!!...And dont want to give up !!!

---

### Post by hakermania on 2012-04-30
Have you tried the 32 bit version of ubuntu?

---

### Post by sagarvarule on 2012-04-30
yes....i tried it last night..I tried Ubuntu 11.10 32 bit (It works fine).
 
 
Then Ubuntu 12.04 ; I tried it via USB but its not working...all its shows is scrambled Ubuntu wallpaper..I suppose file may have corrupted while downloading...I will try it today...And keep things posted...

---

### Post by hakermania on 2012-04-30
I mean, if it still fails, you should totally give 12.04 32 bit a try!

---

### Post by sikander3786 on 2012-04-30
Welcome to the forums sugarvarule! :)

So, currently 12.04 is installed there but is not bootable, right? What we need you to do is to boot an Ubuntu Live CD/USB and post the output of bootinfoscript as per instructions here:

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

The output of this script will help us diagnose the problem and offer any possible solutions.

While posting, please make use of the [code] tags by clicking the # icon in post menu and pasting the text in between the generated code tags for better readibility.

And I don't think this is a 32-bit/64-bit issue. If you PC isn't 64-bit capable, the installation might well fail at the first step. ;)

Thanks.

---

### Post by mikeyb5753 on 2012-04-30
The error is because your laptop is trying to boot from PXE boot ROM.  You need to disable it in BIOS.  If it still won't work then it's probably an issue with GRUB bootloader.  Why don't you install windows then install ubuntu in a VM?  That would eliminate any booting problems

---

### Post by sagarvarule on 2012-04-30
My BIOS boot priority is
1. HDD
2. USB
3.CD/DVD.
4. Network....
 
I tried restoring win7 thru recovery CD.. Bt after all installation it restart...and thn all i see is blank screen...
 
And if I boot Ubuntu from USB I can see the Windows files and partition created from Recovery CD (of Win7).
 
ubuntu 12.04 64 bit.. is rewriting GRUB i suppose..yet it doesnt recognize OS..
 
and ubuntu 11.10 32bit installation working fine...
 
I will try out the step given by sikander3786. which i think will give more
clear view on this....(btw im new to Liux world...and trouble shooting in Linux..Im blank!)

---

### Post by darkod on 2012-04-30
Boot into live mode with the cd, open Gparted and set the boot flag on your root partition. Some BIOS give an error if there is no boot flag present even though only windows needs the boot flag, linux doesn't use it.

You can set flags on a partition in Gparted by right click- Manage Flags. Don't forget to click the green tick button in Gparted toolbar to execute changes.

Try if it helps.

---

### Post by jadtech on 2012-04-30
i think that boot order is not right  if HDD is first you could never boot from cd or usb it will alway go right to the frist drive bootable so HDD first you will always boot  directly to windows or Ubuntu ..

i have a new computer here  that was set this way I just had to change the boot order  so cd and usb would be checked first for boot..

the next issues darkod  is making is you need to set the boot flag, even though it is set first in order it is not being noticed with out that flag and trying to boot the only thing it sees in line which is youe net work card or wireless ..

---

### Post by AlienCoffee on 2012-04-30
I had the very same problem you have now. Maybe you can read this for "inspiration". [http://ubuntuforums.org/showthread.php?t=1969479](http://ubuntuforums.org/showthread.php?t=1969479)

Eventually an efi partition flagged boot solved the situation, but I still can't understand why. I have been using linux for some years, I had zillions of problems, but I've never seen anything similar.

---

### Post by sagarvarule on 2012-05-01
I tried installing Linux Mint 12...Installation crashed with error.

The 'grub-efi' package failed to install into /target/. Without the GRUB boot loader, installed system will not boot.

This is error message is appropriate as, this is what is happening OS is getting installed successfully but some problem in Grub...

How to I solve this issue...I dont know anything about grub,efi and all...

---

### Post by darkod on 2012-05-01
It mentions the grub-efi package. If you are using EFI boot you need to take further steps so that both windows and ubuntu can boot. Also, if your disk partition table is gpt you need to create one small 1MB partition, without any filesystem, with the bios_grub flag set on it.
That is so that grub2 can install there. Not sure if it's needed with EFI boot, but you can create it just in case.

For EFI dual boot, it's best to copy the windows boot files from the efi system partition because ubuntu install sometimes overwrites them. You need to copy them first so you can put them back.

---

### Post by sagarvarule on 2012-05-11
Problem is Solved...
Solutions:

1.Buy Windows 7 cd format everything on HDD and Install it. ( Windows is worth giving money, dont fall for statements Ubuntu is free and Linux for Human being.)
2. Linux is not Human being its for Geeks who like to type each and every command (In world which is moving towards advance GUI from mouse interface to Touch screen...I wonder how linux geeks will still promote typing crap commands when everything will b touch screens)
3. Windows have self diagnostic tools , friendly error messages which helps non experts user...(for eg When my Internet connection is lost Ubuntu still never shows any error message about wt just went wrong....all it shows is Wired Connection Disconnected....Plzz dont tell me to find error log and all....Becozz we cant understand that ****.

4. Thousand of times I hv encounter boot error/ grub rescue ****...But It dont have option to repair bootloader, grub in live cd / usb itself as it there in Windows 7.

5. Software Center tht is again bull ****...Try installing Ruby n Rails its takes month to do that for average users becozz there are so many issues that keeps comming about versions of dependent libraries....Same try it with Windows 7  an average person can do tht same installation in 1-2 hrs...This scenario is tested on ppl in my organisation.

6. All s/w there in Software Center which are free are also there for Windows . So best strategy Buy WIN OS and use those open source s/w....I still support those Open source s/w I have used them till now and i have never bought a s/w in my life.

7. I was never able to install  Linux distro 64 bit ... it never worked...But with windows it works like charm..

Moral of Story : Use WIN OS use Open Source s/w 's and have Peace of Mind...

---

