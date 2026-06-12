---
title: "Yet another Duel Boot/Grub problem"
date: 2004-10-28
forum: Installation &amp; Upgrades
---

### Post by A64Biter on 2004-10-28
I have read many of the previous post and tried the recommendations but still no joy.

In the beginning Ubuntu installed and booted. I implemented the necessary changes to grubs' menu.lst but grub would just hang when windows was selected. I attempted to boot from my Partitionmagic CD to check things out and it crashed with a divide by zero error. Then even Ubuntu will not boot ( no sign of grub).

I booted a Gnoppix CD and ran QTParted. It warned me that there might be a problem with the partition table but displayed just what I expected.I next tryed to reinstall Ubuntu. Everything went well, I deleted the Ubuntu partition and the Swap partition then recreated them.

Now I get

Grub Loading stage1.5

Grub loading, please wait


then the system hangs.

I can look at menu.lst with a Gnoppix boot and it looks okay. Haven't added the stuff to boot windows yet.

My bios defaults to LBA mode so I don't think my problem is the CHS/LBA bug mentioned in previous post.

My system is an
ASUS K8V SE Deluxe AMD 64 motherboard
512k RAM
60 Gig maxtor ultra ata/133 hard drive
         20 GIG fat windows partition
         39.5 GIG ext3
          .5 GIG Swap

Any help would be greatly appreciated. 8-)

---

### Post by beesee on 2004-10-29
Could you please post your menu.lst?

---

### Post by evo_paul on 2004-10-29
Me too I have boot problems about windows after the ubuntu installation.
My menu.lst is similar as follow:

root (hd0,0)
savedefault
makeactive
chainloader +1

but when I try to start windows it appears as follow:

root (hd0,0)
filesystem type unknown, partion type 0x7
chainloader +1

and it stops, my actual partitions are:
hda1 winxp
hda5 swap
hda6 ubuntu

Please, help me, I also need windows at the moment
(and sorry for my English :mrgreen: )
bye

---

### Post by A64Biter on 2004-10-29
title		Ubuntu, kernel  
root		(hd0,1)
kernel		/boot/vmlinuz root=/dev/hda2 ro console=tty0 quiet splash
initrd		/boot/initrd.img
savedefault
boot

title		Ubuntu, kernel  (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz root=/dev/hda2 ro console=tty0 single
initrd		/boot/initrd.img
savedefault
boot

---

### Post by RayG on 2004-11-01
There should have been a Windows entry in your menu.lst. The one posted above by evo paul should work, ie.

 title Windows
 root (hd0,0)    ****assuming of course windows is on hda1. Change as required.
 savedefault
 makeactive
 chainloader +1

A search of this forum and others will indicate that some people have problems with non-booting of Windows due to a peculiarity of the 2.6.X kernel. An "AUTO" detection setting for the hard disk in question in your computer BIOS confuses GRUB. It is apparently not an Ubuntu-specific problem. It is however a serious bug, one deserving to be addessed. 

Changing the "AUTO" setting to "LBA" solves the problem for some people. You may want to try it. 

I had a similar problem and have yet to resolve it. The "LBA" trick did not work for me on my system. Good luck with yours. 

RayG

---

### Post by A64Biter on 2004-11-01
I managed to get Ubuntu to boot by deleteing the ext3 partition with a gnoppix live boot and then reinstalling Ubuntu. I can still see my windows partition (with gnoppix atleast) but still can not boot to it.

Yes I have changed my menu.lst several times using the many variations suggested on this and other forums. Currently it is;

title Windows
root (hd0,0) 
savedefault
makeactive
chainloader +1

My BIOS defaults to LBA and in fact one tool (can't remember which one, qtparted, fdisk,??) shows the partitions as type LBA. My symptom now is Grub echo's the command lines shown above then just hangs.

Can anyone point me to some documentation that would explain what Grub is looking for on hd0,0. What does "chainloader  +1" do.

I have seen many other people with this problem, but no advise beyond the LBA and menu.lst changes. If you can provide a link to some good GRUB doc's, I will RTM.

Thanks

---

### Post by cacofonix on 2004-11-01
[QUOTE=A64Biter]I managed to get Ubuntu to boot by deleteing the ext3 partition with a gnoppix live boot and then reinstalling Ubuntu. I can still see my windows partition (with gnoppix atleast) but still can not boot to it.

Yes I have changed my menu.lst several times using the many variations suggested on this and other forums. Currently it is;

title Windows
root (hd0,0) 
savedefault
makeactive
chainloader +1

My BIOS defaults to LBA and in fact one tool (can't remember which one, qtparted, fdisk,??) shows the partitions as type LBA. My symptom now is Grub echo's the command lines shown above then just hangs.

Can anyone point me to some documentation that would explain what Grub is looking for on hd0,0. What does "chainloader  +1" do.

I have seen many other people with this problem, but no advise beyond the LBA and menu.lst changes. If you can provide a link to some good GRUB doc's, I will RTM.

Thanks[/QUOTE]

can you post a print out of fdisk or tell me what your partition setup is please

Thanks

cacofonix

---

### Post by dodongo on 2004-11-27
All right... I just got done dealing with the same problem.  Here's what I did.

1.  I made a 64MB partition just for /boot -- I think this actually had nothing to do with why this procedure fixed my problem because:

2.  I also noticed that in the "partition options" or whatever it's called, there's an option which you can flag -- it's the first one in that list; sorry that I don't remember what it's called.  The option's description says that the partition containing /boot must be so marked.  So, flag that option, then do <Continue>.

3.  Then, complete the installation and see if you boot.  

Given that you're looking to maintain a dual-boot, it would probably be easier to try just step (2) by itself and see if that gives you some lovin'  :)

Good luck!

-Chuck

PS - I don't know if this is something worth considering changing in the installer.  My guess is that when you auto-partition a drive, all those options are set properly, but if you go into the advanced setup, the installer expects you to set those options yourself.  Maybe the partition containing /boot (either /boot if partitioned explicitly, or root otherwise) should automatically be flagged and marked as bootable?

---

### Post by initman on 2007-04-19
I have been searching on the net myself to have my computer dual booting with xp and ubuntu and i have come up with a better solution for you. Use a program called VM ware install Ubuntu then run an VM enviroment for windows XP! This is also great if windows decides to go potty like as we all know it happens now and again! bad thing is you have you have to pay for VM ware but here is the link 

[http://www.vmware.com/products/ws/buy.html](http://www.vmware.com/products/ws/buy.html)

Hope this helped you. (dual booting is old school and a pain in the **** when mixing windows and linux)

---

