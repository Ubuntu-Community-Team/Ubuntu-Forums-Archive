---
title: "Hard disk not responding ?"
date: 2009-04-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ashwat on 2009-04-09
Once upon a time I was using Ubuntu 9.04 and I went into hibernation. And all of a sudden ( after a good 2 months of using it without any troubles), it would not boot and it gave this error.> Boot from (hd0,2) ext4 ad4752e8-18ad-4796-8489-37a9d40722dc

Starting up....
Loading, please wait...
udevadm trigger is not permitted while udev is unconfigured.
usplash: Setting mode 1152x 864 failed
usplash: Using mode 1024x768
Gave up waiting for root device. Common problems: 
 - Boot args ( cat /proc/cmdline) 
  - Check rootdelay= ( did the system wait long enough?) 
  - Check root= ( did the system wait fro the right device?)
 - Missing modules ( cat /proc/modules; ls /dev)
ALERT! /dec/disk/by-uuid/ad4752e8-18ad-4796-8489-37a9d40722dc does not exist. Dropping to a shel!

BusyBox v1.10.2 ( Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash) 

Enter 'help' for a list of built-in commands

(initramfs)


I use a Dell Vostro 1400, No dual boot. Any other specific details that you might be required for diagnosis, can be submitted provided the process to procure that information in these dire straits is also described. I have loads of submissions over the weekend and I will need some very quick help. In the name of the Flying Spaghetti Monster, HELP ME.

---

### Post by iponeverything on 2009-04-10
Boot off the live CD and pull your important data off. 

It looks to me like your drive has become corrupted (maybe some kind of hardware fault) -- The thing about situations like this, is that its tempting to reinstall on the original drive and continue using it -- when its likely to happen again. I have had my data get scrambled once, but was because of an early version of reiserfs and not the drive.

---

### Post by ashwat on 2009-04-10
[QUOTE=iponeverything;7046015]Boot off the live CD and pull your important data off. 

QUOTE]

When I tried booting off the LiveCD, it kept giving I/O errors from sr0. I thought that my drive died so I called Dell Support who were very unhelpful since they believed they had no liability( 3 Party software ****). Luckily I had a 40GB FAT32 partition which I had created to install Windows for dual boot on a future date. And that has come to the rescue now and I installed Vista ( croaking to death, well almost) and first thing I am doing is getting back upto this forum. 

What this means is that my HDD has not died. But for some odd reason ( Is it Jaunty updates killing the boot record or some odd thing like that )I am not able to boot into Ubuntu and boy do I have data that I need badly from that or what. 

Any suggestions people? To all those who help me get back to using Ubuntu, I promise infinite supply of candy.

---

### Post by stalkier on 2009-04-10
> **ashwat said:**
> [QUOTE=iponeverything;7046015]Boot off the live CD and pull your important data off. 

QUOTE]

When I tried booting off the LiveCD, it kept giving I/O errors from sr0. I thought that my drive died so I called Dell Support who were very unhelpful since they believed they had no liability( 3 Party software ****). Luckily I had a 40GB FAT32 partition which I had created to install Windows for dual boot on a future date. And that has come to the rescue now and I installed Vista ( croaking to death, well almost) and first thing I am doing is getting back upto this forum. 

What this means is that my HDD has not died. But for some odd reason ( Is it Jaunty updates killing the boot record or some odd thing like that )I am not able to boot into Ubuntu and boy do I have data that I need badly from that or what. 

Any suggestions people? To all those who help me get back to using Ubuntu, I promise infinite supply of candy.

Say dude I had the same thing happen to me in Hardy. boot off of Live CD and hit F6, type pci=nomsi. I believe that is correct. I am not sure what it does but it worked for me. I had to do it on 2 PCs.

---

### Post by skitching on 2009-04-14
I'm not sure there is anything wrong with your drive. I'm also getting the same problem after updating jaunty a couple of days ago. But booting to a different kernel on the same install works. So it appears to be a problem specifically with the kernel image.

There is a thread here too, but this isn't necessarily correct either; the cause certainly isn't a partial-update in my case:
 [http://ubuntuforums.org/showthread.php?t=1121567](http://ubuntuforums.org/showthread.php?t=1121567)
 [https://bugs.launchpad.net/ubuntu/+source/devmapper/+bug/358654](https://bugs.launchpad.net/ubuntu/+source/devmapper/+bug/358654)

---

