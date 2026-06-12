---
title: "Initramfs Errors after unsuccesfull upgrade"
date: 2012-01-07
forum: Installation &amp; Upgrades
---

### Post by Netorca on 2012-01-07
[SIZE=2]Well would you believe it, it had to happen to my wife's laptop, she's a bit of a technophobe and it took me ages to convince her to leave the dreaded Windoze behind. She been doing great until the other day. 

I dont want to ramble but I want you to understand the picture, after an update that failed and I was"too busy" to help, she rebooted and Bam..... Machine will not boot and only come to a Initrams Terminal...

I can tell you I was lost, I am  a WIntel Engineer, Novell 5 CNE, NT4 MCSE Etc but have never come across this Teminal...Well Google the problem and wow loads of bad news, your hardware has failed, need to do this and that all bad. 
Told my Wife the bad news and well you can guess "I never had this problem with Windoze" well appart from the weekly Blue screens and the 200,000 virus infections its was all swell with the Microsoft Puppy software.

Anyway I will get to the point as it may help someone else out, I found a thread on "another" Ubuntu site, if there is one, and while it pointed to the solution it did not fully explain.....

The error of the Machine  on reboot was[/SIZE]
 
[I]mount: mounting /dev/disk/by-uuid/***************************** on /root
failed: Invalid argument
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target file system doesn't have /sbin/init
No init found. Try passing init= bootarg

Busybox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands
(initramfs) _  [/I]

[SIZE=2]Basicly this means that the Initramfs the initial Ram disk file system used to boot Ubuntu is damaged or to be more precise it is not where it should be. (now do not panic, you file system and all you files are still there) it just the "Pre Boot" system of Ubuntu does not know where to start from, this is probably caused by a Unsuccessful update of the Initramfs..and related. [/SIZE]

**now there is a supposed solution for this of **

[I]1. Boot from the Ubuntu Live CD;

2. Open/Run Terminal;

3. Type:[/I][I] sudo fdisk -l (to get the device name) then press ENTER;

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: **********

 Device Boot Start End Blocks Id System
/dev/sda1 * 1 30238 242886703+ 83 Linux
/dev/sda2 30239 30401 1309297+ 5 Extended
/dev/sda5 30239 30401 1309266 82 Linux swap / Solaris

 The device name for my friend's system based on the above: [/I][I]/dev/sda1

4. Type: [/I][I]sudo fsck /dev/sda1 then press ENTER;

5. Restart the system and boot normally.[/I]

**The above did not work for me but this did**....

[SIZE=2].I hope it helps others out there..
You will need another machine installed with the same version and update of Ubuntu, I had another laptop, not exactly the same (that does cause problems later on but I will explain, if the donor machine has different hardware Ie WIFI card, you will have to follow the full solution below) you need to 
[/SIZE]
[LIST]
[*][SIZE=2]copy all of  the initrd.img-2.6.32-34-generic archives (All of them) to a USB stick" from the working machine or install, they are numbed relevant to the Kernels". [/SIZE]
[/LIST]

[LIST]
[*][SIZE=2]Then on the Machine with the problems you need to boot to a USB Live install...again from a USB stick, this was an issue for me as the machine refused to boot to another install _several times_, so be patient,[/SIZE]
[*][SIZE=2]When the install is running, Alt & F2 then Open "gksudo nautilus" Type in the run application, or equivalent, sorry all you command line warriors, you probably know a quicker way but I am still learning.[/SIZE]
[*][SIZE=2]Navigate up to the Boot Directory, and create a "Back up" Directory, cut and paste all the  "initrd.img-2.6.32-34-generic" archives from the boot directory into the "back up" directory.[/SIZE]
[*][SIZE=2]from the other USB stick copy  the working machines or Installs,  "initrd.img-2.6.32-34-generic archives" to the Boot directory.... This will allow the machine to boot if you have copied the   initrd.img-2.6.32-34-generic archives from a suitable machine that will be the fix done and dusted....[/SIZE]
[/LIST]

[CENTER]-----------------------------------------------------------------
[/CENTER]

[SIZE=2]In my case it would not support my wife's WiFI card, so I had to 
[/SIZE]
[LIST]
[*][SIZE=2]Plug the machine into my broadband router with a network cable, [/SIZE]
[/LIST]

[LIST]
[*][SIZE=2]make sure it could access the internet,(as I needed to run an update)
[/SIZE]
[/LIST]

[LIST]
[*][SIZE=2]go to the Alt & F2 gksudo nautilus and the boot directory again. [/SIZE]
[/LIST]

[LIST]
[*][SIZE=2]create another Back up directory a "Back up2" [/SIZE]
[/LIST]

[LIST]
[*][SIZE=2]cut and paste all the  initrd.img-2.6.32-34-generic archives to the back up2 directory 
[/SIZE]
[*][SIZE=2]copy the original  initrd.img-2.6.32-34-generic archives from the "back up" dir to the "Boot" Directory.....[/SIZE]
[*][SIZE=2]exit Nautilus the File Browser 
[/SIZE]
[*][SIZE=2]open a terminal screen and run "sudo update-initramfs -u" This will update the Initramfs this time hopefully with out error and will allow your machine to use all of its existing drivers and Initramfs images....[/SIZE]
[/LIST]

[SIZE=2]This worked for me...but if there are any super Ubuntu's out there that would like to add comment or put me straight please feel free......[/SIZE]

[SIZE=2]Netorca..[/SIZE].:)

---

