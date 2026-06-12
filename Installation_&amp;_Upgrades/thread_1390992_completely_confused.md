---
title: "completely confused"
date: 2010-01-26
forum: Installation &amp; Upgrades
---

### Post by coolwalker on 2010-01-26
I'll admit it. I'm completely confused. I have tried and tried to get my Ubuntu installation to load but it won't. Perhaps because I have two other OS on my pc, one being Win XP Pro 64 Bit and the other W-7 64 bit. I have the Ubuntu CD (somewhat older, 8.4 I believe) and I loaded it, it didn't work so I ripped it out and reinstalled. Now I have two instances showing up at boot time but when looking in easyBCD I only see one instance as well as the XP and W-7.

I've tried all the diddling around in easyBCD and now I can't get into XP or Ubuntu, but I can in W-7. I am **very** confused and I do want my XP to show up. My main reason that I want Ubuntu is to see how well it stacks-up when playing CODUO. I've heard good things and I would like to see how well it runs altogether...plus I do like the way it looks. But I am stumped. I don't want to uninstall stuff to reinstall again because of losing some programs, especially CODUO because that takes so much installation time. Does anyone know what I should do? I am at work so I can't really get deep into details but I could really use some assistance here. I know it is free, so I won't complain about bogus help...I'll try anything.

ThankX in advance.

---

### Post by audiomick on 2010-01-26
Hallo.
There is a good chance that solving this will be over my head, but as a first step I would suggest following the steps here
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
and posting the RESULTS.TXT here so we can see exactly what your situation is.

---

### Post by darkod on 2010-01-26
The one thing you didn't specify is what are you actually trying to achieve and what happened. Since you mentioned EasyBCD, are you trying to keep it as bootloader and didn't install grub?
Any reason you don't want to simply use grub?
I'm not a fan of EasyBCD and I think the default installation with grub (or grub2 for 9.10) on some of your disk's MBR would have worked. Unless there is valid reason you can't use grub.

---

### Post by coolwalker on 2010-01-26
> **darkod said:**
> The one thing you didn't specify is what are you actually trying to achieve and what happened. Since you mentioned EasyBCD, are you trying to keep it as bootloader and didn't install grub?
Any reason you don't want to simply use grub?...


I loaded Grub and it simply doesn't make any sense to me. I didn't see and executable file to start it off. The easyBCD really isn't all that easy either. tell me, why is Ubuntu so difficult to get started? I see literally hundreds if not thousands of entries with everyone confused or with problems. With windows if I have a problem I can usually fix it right away in the registry. This Ubuntu, while it looks cool, does appear to be somewhat of a pain. I am going to keep struggling with it and if necessary I will simply load it on a secondary HD.

---

### Post by garvinrick4 on 2010-01-26
I do believe you are out of Primary partitions. Win 7 and XP pro might just take up 4 primarys
and that is all you get. Sometimes real hard to load two windows on 1 drive. Clean install of 7 takes 3. System/OS/recovery (which for no good reason is called Vista in boot.) XP pro needs to
boot though has a different boot loader than Windows 7. Linux grub2 will overwrite them both
in System partition(sda1) and you can boot to them all no problem. I will give you a link to read
to see if you are all used up in Primary partitions. Must read for Dual or triple boot.

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by coolwalker on 2010-01-27
Thanks **garvinrick4**, I will read this carefully and hopefully resolve my issue. I am taking half a day off so I can do this in quiet, with no children or wife in the background...and if you're married, you know exactly what I mean. Thanks again for the link and I will get started after I go to work and come home early.

---

### Post by Brett.Townsend on 2010-01-27
Yeah, It sounds to me like you have used up all of your primary partitions. If you just want to play with ubuntu you could use wubi as it will not require an extra partition. Could be an easy fix, although i'm not pushing wubi here if all you are after is to get it working I beleive that this will work.

---

### Post by Bartender on 2010-01-27
coolwalker, look up GParted LiveCD.  It's hosted at SourceForge.  Download the latest stable .iso and create a bootable CD.  This is a super handy tool for looking at your partitions and for tweaking on them if you desire.

My guess was also that you're up against the stops with four primary partitions.  Might have to get rid of one of the Windows OS'es, or run one virtually, or ?

---

### Post by Brett.Townsend on 2010-01-27
I can't really see any reason why he couldn't run one virtually, I'm not a fan of wubi, and that would solve the problem of not having enough primary partitions without having to go into the whole wubi thing.

---

### Post by darkod on 2010-01-27
> **coolwalker said:**
> I loaded Grub and it simply doesn't make any sense to me. I didn't see and executable file to start it off. 

What executable file are you looking for in grub??? Grub is a bootloader, you'll see no executable files. In fact, except the config files inside ubuntu, you'll see no grub files at all.
It sounds to me like you are trying to do something very different from the default. Maybe that's why it didn't work.
Take your time and tell us what are you trying to do, like we are two year olds. :)
For example:
I want to install ubuntu next to my windows on my single hdd, and I have unallocated unpartitioned space on the hdd (not belonging to any partition).
Or I want to install it next to windows, but windows takes whole of my drive and I don't know how to shrink it.... etc

We'll surely come up with some ideas but at the moment I don't know what you are trying to do honestly.

---

### Post by Brett.Townsend on 2010-01-27
So whats the did you ever get it to work.

---

