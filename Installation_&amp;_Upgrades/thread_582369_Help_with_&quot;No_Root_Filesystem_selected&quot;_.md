---
title: "Help with &quot;No Root Filesystem selected&quot; during installation of 7.10"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by plinydogg on 2007-10-19
Hi peeps,

Here's my setup: I've got a system that dual booted Vista and 7.04. Updates to 7.04 in anticipation of the upgrade to 7.10 killed my wifi connection so I decided to upgrade via the alternate CD. I did so but when I tried it I got some kind of Broadcomm IRQ conflict thingee and the booting process hung. I decided instead to just completely overwrite my existing installation and just use the LiveCD to install 7.10. 

However, when attempting to do so, I get as far as the part where I select the partition. I highlight the proper partition and click "next" and repeatedly receive some sort of "no root filesystem specified" error. I can't get any farther. What's up with this? 

Because Vista is particularly territorial, I let it manage the boot process (with EasyBCD) but I don't know why this should prevent me from selecting the proper partition on install. 

Am I missing something painfully obvious here? Thanks in advance!

Plinydogg

---

### Post by rsambuca on 2007-10-19
When you select the partition for installation, you still have to define it as the root '/'.

---

### Post by plinydogg on 2007-10-19
Thanks for the response, rsambuca!

How do I specify "/"?

I don't know what my problem is...I installed it this way for 7.04 a few months ago. It seems I've forgotten a lot (or perhaps things are complicated by teh fact that I'm trying to install onto an occupied partition). 

In any event, thanks!

---

### Post by jgarriso on 2007-10-19
If you are doing "Manual Partitioning" click on the partition you want, click edit partition button, and change the mount point to /. You'll have to do this for all your partitions.

For whatever reason Gusty automounted all my partitions as /media/sdb# whereas previous versions of Ubuntu (and most other Linuxes I've installed) have at the very least made it much more clear how to set the mount points. The manual partition editor seemed much less intuitive this time around. I seem to remember Feisty making that ridiculously simple. I wonder why it went backwards?

My own problem is way interesting. I'm getting the black screen of doom like some many people are reporting, but when I go into text mode it reports that my root partition is mounted read only. I can fix it, but I'm reinstalling just to see if it does it every time. Talk about a show stopper for Linux newbies!

---

### Post by plinydogg on 2007-10-19
Thanks, jgarriso! 

The only thing I'm worried about (and my know-how is sparse!) is overwriting Windows' control of the boot process. Does that make sense?

---

### Post by rsambuca on 2007-10-19
I understand, but don't worry, the grub loader is very stable and easy to use.

---

### Post by jgarriso on 2007-10-19
As the previous poster said, GRUB should make that as painless as possible.

Reinstalling fixed my problems and I'm very impressed with Gusty's performance on my laptop. ATI Drivers, Wireless, even the crappy modem all picked up by the Restricted driver manager. Even the media card reader, which I never managed to get working at all under Feisty. A+ for that bit anyway.

Good look with Ubuntu. Hope you like it.

---

### Post by plinydogg on 2007-10-20
But I want Windows to manage the boot process. What I'm worried about is if I select "/" that it will overwrite the Windows boot stuff. Does that make sense?

---

### Post by rsambuca on 2007-10-20
There is a way to use the Vista bootloader to control everything, but I am afraid I have never tried it myself.  Guess you'll just have to google it.  What is your problem with Grub?  It is an excellent bootloader, and much more configurable than the Vista loader.

---

### Post by plinydogg on 2007-10-20
Oh, I don't have a problem with GRUB at all, it's just that before I installed a dual boot with Vista and 7.04 I did a lot searching of these forums and found that Vista users experienced major problems unless they allowed Vista's bootloader to control things. 

So, it's not that I dont' like GRUB, it's just that I've always allowed Vista to control things as a cautionary measure. 

And installing Ubuntu on a partition and calling it "/" seems like it may mess that up. "/" seems like it's as primary as you can get, which makes me worry that I might be messing up my Vista bootloader (even though Vista is on another partition). 

Does that sound crazy?

---

### Post by rsambuca on 2007-10-20
The '/' (root) that is referred to in the Ubuntu installer is specific to the linux filesystem.  I think what you are scared of overwriting is the MBR - the Master Boot Record.  The MBR is where the boot instructions go, and can be controlled by the Vista Longhorn loader or Grub.  So don't worry during the installation about the '/' file.  It is main component where all of the files go for the linux OS.  If you wish to keep the Vista loader, make sure that when it gets to the last part of the installation - the grub loader - have the installer put grub onto the new linux partition, and not the MBR, and you will be fine.  You will then have to add Ubuntu to the Vista loader, though.

Just as an aside, you might want to note that the problems that people have with booting Vista has nothing to do with grub.  It is usually problems from shrinking the Vista partition incorrectly.

---

### Post by plinydogg on 2007-10-21
Thanks for the clarification rsambuca! Very helpful. 

I went ahead and installed Ubuntu on my linux partition (made the linux partition "/"). On the last screen I pressed the "advanced" button and told it not to install the bootloader, thinking that I would let Vista control this. Upon installation completion and a reboot I got this error:

"Cannot load from harddisk"
"Insert systemdisk and press a key"

At this point I figured I needed to re-install the OS with the bootloader installed also this time so that's what I did. So I reinstalled and this time checked the box to install the bootloader. I left the location for installation at its default: "(hd0)"

The installation was a success and I can now access 7.10, the only issue is that GRUB now takes over the boot process. Here's what happens when I turn my computer on:

(1) GRUB screen;
(2) If I select the Windows Vista option, I am then taken to a screen where I can select from Ubuntu or Vista;

In other words, I have two screens where I can choose the OS to load! This isn't horrible per se, but I'd rather just have one (preferably, Vista's). 

If I reinstall the OS and put the bootloader somewhere else (i.e., not hd0) do you think it will allow Vista's to take back control? If so, where should I install the bootloader?

Thanks for your continuing help.

---

### Post by rsambuca on 2007-10-21
Unfortunately you made a little mistake when you let it install to (hd0), which is the mbr.  Sorry, forgot that it doesn't really say 'mbr', but rather refers to it as hd0.

If you want to get rid of the grub part, you will have to do two things:  Restore the Vista loader using the Vista installation disc, and then use the Ubuntu liveCD to restore grub to the linux partition instead of hd0.

---

### Post by plinydogg on 2007-10-21
Oh well, it's not that big of a deal...just a minor annoyance really.

Is there any way to make GRUB take a certain action (select Ubuntu or Vista) by default after inaction for a certain period of time? So that when I reboot if I don't do anything it will automatically boot one or the other after, say, 30 seconds?

BTW, for future reference, where should I have installed GRUB?

---

### Post by rsambuca on 2007-10-21
> **plinydogg said:**
> Oh well, it's not that big of a deal...just a minor annoyance really.

Is there any way to make GRUB take a certain action (select Ubuntu or Vista) by default after inaction for a certain period of time? So that when I reboot if I don't do anything it will automatically boot one or the other after, say, 30 seconds?

BTW, for future reference, where should I have installed GRUB?

It already does that by default.  You can change the settings to boot into whichever OS you want, and after whatever time you want.  You can change the settings in your menu.lst file, by entering

gksudo gedit /boot/grub/menu.lst

---

### Post by plinydogg on 2007-10-21
Awesome! Thanks.

---

