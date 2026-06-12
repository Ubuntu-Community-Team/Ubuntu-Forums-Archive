---
title: "Bootrepair cannot open display"
date: 2016-06-06
forum: Installation &amp; Upgrades
---

### Post by Mintastic on 2016-06-06
I'm trying everything under the sun to try and undo what windows 10 did to my laptop's dual boot setup.

I've gotten so far as running boot-repair in failsafe mode where it suddenly stops after a wall of texts.

I press ctrl alt f1 which allows me to input commands, wherein I try to install boot repair and it says it's already installed. I type in boot-repair & or boot-repair and it gives me the above error message. What do I do from here?

---

### Post by oldfred on 2016-06-06
Boot-Repair is not totally terminal based.

What video card/chip do you have?

---

### Post by grahammechanical on 2016-06-06
It is best to run a Ubuntu live session and install Boot Repair in the live session and then run boot repair. Use the option to create a BootInfo Summary report and the post the URL in this thread so we can see what Boot Repair sees.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Please describe what the Windows 10 update has done to your dual boot with Ubuntu. Do you see a boot menu (Grub)? What happens when you select to load Ubuntu? Have you tried loading Ubuntu from the UEFI settings utility?

Are you actually using Advanced options for Ubuntu>Recovery Mode kernel and not Boot Repair?

Some have found that Windows 10 updates re-write the partition table and do not record Linux partitions. That would break any dual boot with Windows. But we do not know if that is the situation you are in.

Your real problem is being no longer able to dual boot. Boot Repair will re-install the boot loader (Grub) but it will not fix the partition table if Windows has indeed messed up the partition table. Concentrate on the real problem.

Regards

---

### Post by Mintastic on 2016-06-06
I do believe the update rewrote my partition tables. At first I was getting an "error: unknown filesystem grubrescue: " prompt. After fiddling around between a Linux Mint disk(could not get it to load to a desktop) , boot-repair( 64bit session(failsafe mode)), my startup screen is now a gnu grub minimal bash screen. 

I've been attempting to follow the steps provided in this link: [https://help.ubuntu.com/community/Grub2/Troubleshooting#Search_.26_Set](https://help.ubuntu.com/community/Grub2/Troubleshooting#Search_.26_Set)
Provided to me by a patient soul in Reddit, and it seems quite useful. 

I've narrowed the possible partitions I need to focus on to these two: [https://i.imgur.com/zk9aPDE.jpg](https://i.imgur.com/zk9aPDE.jpg)
Either (hd0,msdos5) or (hd0,msdos3).

 I've tried setting the root and prefix with both partitions but I can't seem to figure out how to set the kernel or the initrd img as the first link suggests to do under the task section, or if I'm inputting it in correctly as I'm fairly new to Linux and unfortunately found myself in quite a mess.

Apologies for the double post, but regarding the boot-repair disc, it probably isn't too applicable anymore but when I choose the disc as the boot option it gives me this menu screen: [http://i.imgur.com/muLPwPW.jpg](http://i.imgur.com/muLPwPW.jpg) 
And when I choose the failsafe option, i get a wall of text and the screen goes blank after a minute until I press ctrl alt f1, which then displays: [http://i.imgur.com/JUDbPTA.jpg](http://i.imgur.com/JUDbPTA.jpg)
And when I type in boot-repair, it gives me that "cannot open display" message.

---

