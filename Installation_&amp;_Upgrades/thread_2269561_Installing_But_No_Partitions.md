---
title: "Installing But No Partitions"
date: 2015-03-16
forum: Installation &amp; Upgrades
---

### Post by justin.m.kincaid on 2015-03-16
Hello, I am having a bit of trouble installing Ubuntu. I am using a bootable USB and everything goes smoothly until I get to the Installation Type menu. 

Please note, that my installation seems to proceed differently than the videos I have watched. It goes like this:

Choose Language
Choose Wifi
Preparing to install Ubuntu
--this checks for drive space, wireless, and power source. It also has me check off download updates
It then takes me directly to this window [http://i.stack.imgur.com/wCxpN.png](http://i.stack.imgur.com/wCxpN.png) but the place where partitions are supposed to be is blank and the New Partition Table and Revert buttons are greyed out. The Device for Boot Loader just has one option: /dev/sda. And the + - and change buttons are clickable. At this point, my USB is a solid red, telling me that it's working, and if i click the + - or change buttons, my laptop sits there for at least five minutes seemingly pondering the situation. 

The videos that I have watched have a step in between the Preparing and Installation Type window, which I never see. 

What should I do?

---

### Post by Mark Phelps on 2015-03-16
> but the place where partitions are supposed to beImplies you already have partitions in place on your drive.

You should tell us what is already there.

---

### Post by ajgreeny on 2015-03-16
What you show is exactly what I would expect to see if I attempted to install Ubuntu onto a hard disk which has a partition table but no partitions made yet or has had previous partitions deleted.

Has your disk previously had an OS on it or is it totally new?  If it has had an OS in the past have you deleted the partitions to leave unallocated space?

---

### Post by justin.m.kincaid on 2015-03-16
I had Windows 7 installed on one partition and another partition that supposedly had Windows 7 installer and drivers. Unfortunately, and the entire reason I'm trying to install Ubuntu, is that I woke up this morning to the message 'Missing operating system' at boot. I couldnt access my installation partition or alter either partition. I figured that I would be able to reformat via Ubuntu installation, but that hasn't worked out. 

Long story short, I ended up downloading  DBAN and it's been chugging away all day. Im hoping that when it's done, I'll be able to do a fresh reformat and install ubuntu.

---

### Post by ajgreeny on 2015-03-17
It could, of course, simply be that the hard disk has died.  I have no idea about Win7 error messages of that sort, so Idon't know if there might have been a simpler way to deal with the problem, but it's too late now for that install of Windows, so good luck with what you're trying to do now.

DBAN can be a slow process, but I'm not sure about taking all day.  Let us know what eventually happens.

---

