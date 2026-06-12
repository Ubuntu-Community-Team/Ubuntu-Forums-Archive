---
title: "Laptop freezes after boot with fresh install 10.04."
date: 2010-05-22
forum: Installation &amp; Upgrades
---

### Post by lone_wolf45 on 2010-05-22
Hi all, 
I have a Sony Vaio PCG-k195hp laptop, in which i've installed Ubuntu 10.04. Before installation i tried the Livedisk environment to make sure that everything would work out okay. 

The results were fine, ubuntu even got the onboard Wireless card working which was causing problems in windows. But after the install ubuntu has become erratic. It sometimes boots and does a lot of work but other times it'll boot and freeze as soon as i move the mouse, or even earlier. I am pretty certain the CD was not the cause as i've already used it to install 10.04 in another system and i'm writing from it right now. I got the 10.04 iso on the day it came out and thought that maybe it wasn't complete so tried updating my install, but it had an error during the update installation. 

Now even the live CD won't work as it hangs in the loading screen.

I am at my wits end, and cannot understand the reason for this at all. If any one can suggest anything at all i would be very grateful.

---

### Post by davidmohammed on 2010-05-22
correct me if I'm wrong - but you've got an ATI graphics card - correct?

What happens if you boot with "nomodeset" in your grub settings (i.e. grub reads nomodeset quiet splash)?

---

### Post by lone_wolf45 on 2010-05-22
> **davidmohammed said:**
> What happens if you boot with "nomodeset" in your grub settings (i.e. grub reads nomodeset quiet splash)?

Sorry, i don't understand, how do i boot with "nomodeset", If you could please explain.
And yes its an ati radeon graphics card.

---

### Post by davidmohammed on 2010-05-22
if you are using the live CD - press F6 when you see the language screen - you'll notice the boot line at the bottom - edit it and add nomodeset.

If you've managed to install already, press shift when booting to display grub, followed by e to edit.  Navigate to the line containing "quiet splash" and add nomodeset before quiet splash

---

### Post by lone_wolf45 on 2010-05-22
Ok, I've tried that, i entered nomodeset before quiet splash, and then pressed Ctrl+x to boot after reading the paragraph at the bottom, I logged in to my system, but after starting firefox and mounting a usb flash drive, i'm back to square one, it crashed again. I'm dual booting ubuntu with Win XP, and i tried modifying the partitions during the installation of ubuntu (there wasn't enough space) if that make any difference.

Oh and after i tried nomodeset that line on which quiet splash was is gone.

---

### Post by davidmohammed on 2010-05-22
ok - at least you got to boot ok.


can you try booting with nomodeset xforcevesa

This should give you a stable but low resolution display.

Then check if there are any drivers available through administration - hardware drivers.

---

### Post by lone_wolf45 on 2010-05-22
Ok, i tried that, twice just to make sure. i didn't get a low resolution display, just the same one as before, and there weren't any drivers available in Hardware Drivers, (as a matter fact there wasn't any there, is there a way to update it or add lists for it or something).

---

### Post by davidmohammed on 2010-05-23
ok - very confused...

if you follow this [link ]("https://help.ubuntu.com/community/RadeonDriver")- does it make your desktop more stable?

---

### Post by Vinnare on 2010-05-23
> **davidmohammed said:**
> if you are using the live CD - press F6 when you see the language screen - you'll notice the boot line at the bottom - edit it and add nomodeset.

If you've managed to install already, press shift when booting to display grub, followed by e to edit.  Navigate to the line containing "quiet splash" and add nomodeset before quiet splash


thnx davidmohammed! it worked for me. But the other problem I'm facing is that in System-> Preferences -> Monitors (i.e Monitor Preferences), It says that Monitor: Unknown and the resolution is default 1280*720 instead of what my monitor's originally is- 1600*900. And how do I know that whether the nvidia drivers are installed or not? or it is the problem of drivers not being able to detect the LCD? My laptop is Sony Vaio CW26FG.

---

### Post by davidmohammed on 2010-05-23
If you go to administrator-hardware drivers it should list the nvidia drivers you can install.  I would choose the recommended one and press activate to install.

---

### Post by lone_wolf45 on 2010-05-24
Tried to install The radeon driver as opposed to the flgrx driver as suggested by the article in the link you provided, but this made the laptop to boot to the splash screen then a black screen appears and nothing happens after that.   I've heard that there are some problems with 10.04 and ati drivers so i thought i'd give 9.10 a try. i have installed it but haven't had the chance to test it out yet. i'll post here again if that fixes the problem.

---

### Post by SupriyaJay on 2010-05-24
Hi
I am totally new to Ubuntu. I dont know what is going on ..
Even I am facing some thing similar as described in original message of this thread. I have installed Ubuntu 10.4 on foxconn nt330i with nVidia chipset. 
After ubuntu installation everything was ok (except sound). So intalled nVidia driver.
After the nVidia driver is updated everything worked for one day. 2nd day when system is started no applications are launched (I can't even see the shut down pop up; I have to remove power to my netbox !!). By chance if anything is started system just hangs within 2minutes.
Any advice is greatly appreciated.

---

### Post by davidmohammed on 2010-05-24
> **SupriyaJay said:**
> Hi
I am totally new to Ubuntu. I dont know what is going on ..
Even I am facing some thing similar as described in original message of this thread. I have installed Ubuntu 10.4 on foxconn nt330i with nVidia chipset. 
After ubuntu installation everything was ok (except sound). So intalled nVidia driver.
After the nVidia driver is updated everything worked for one day. 2nd day when system is started no applications are launched (I can't even see the shut down pop up; I have to remove power to my netbox !!). By chance if anything is started system just hangs within 2minutes.
Any advice is greatly appreciated.

Hi there - please can you start a new thread - lone_wolf45 is having issues with ATI graphics.  Your issues, whilst sounding similar, are nvidia related.  thanks.

---

### Post by lone_wolf45 on 2010-05-25
Hi,  Back from trying out 9.10. It can only be described as a slightly improved version of 10.04 on my laptop. I managed to install virtualbox (two reboots), and then Xp inside it (no reboot), which means the laptop ran for about an hour (a new record, yay). but then it started freezing again, 

I thought i could maybe get all the updates for 9.10 and maybe that would solve the problem, but it freezed during install and i think some files didn't get written to properly and the laptop is no longer stable.   

The freezes may be caused by a hardware problem since both 9.10 and 10.04 didn't work properly, but xp runs fine on it (albeit, a bit slow).   

I have seen a record of this same laptop working perfectly although with a older version     

[https://wiki.ubuntu.com/LaptopTestingTeam/SonyPCG-K195HP](https://wiki.ubuntu.com/LaptopTestingTeam/SonyPCG-K195HP)    

Maybe support for it has been removed over time, though maybe unintended.

---

### Post by davidmohammed on 2010-05-25
Hi there,
  has the laptop been upgraded at any time, such as a wireless card, ram, new dvd drive - or is it a 'vanilla-straight-from-manufacturer' laptop?

---

### Post by lone_wolf45 on 2010-05-25
> **davidmohammed said:**
>   has the laptop been upgraded at any time, such as a wireless card, ram, new dvd drive - or is it a 'vanilla-straight-from-manufacturer' laptop?

No, it hasn't been i'm afraid. I bought it second hand, but the person who sold it didn't seem tech savvy enough to want to open up his laptop's innards. I recently opened it myself to make sure it isn't a clogged fan heating up the system that's causing the freezes, and i noticed the screws didn't have any scratches on them, any where. I'm probably the first person to open it since it got sold.  I'm thinking about using openSuse on it just to see what happens. 10.04 and 9.10 has worked out brilliantly on my two desktop machines, (without any unprecedented glitches of anykind) but my laptop doesn't seem quite up to it. I will also try out the netbook remix edition just to check if that has a better result.  EDIT: I have just noticed the following thread where users are adding symptoms in 10.04 similar to what i described in the beginning of the thread:  [http://ubuntuforums.org/showthread.php?t=1478787&highlight=panel](http://ubuntuforums.org/showthread.php?t=1478787&highlight=panel)  from the first 4 pages that i've read through a bug has been reported.

---

### Post by davidmohammed on 2010-05-26
interesting ...

if you are willing - try doing a complete reinstall, but when partitioning, partition using ext3 file-system rather than ext4.

If this works then you can report this freezing as a ext4 issue.

---

### Post by lone_wolf45 on 2010-06-02
Well, back from testing. So far I have installed Opensuse 11.2 kde version, and Windows 7 (just for variety) Neither made it past the 10 min limit after several attempts. This leads me to believe that it may not be a software problem (as far as drivers and operating systems go) I have also discovered something that points to a different reason as to why the freezing may have been occurring. When i boot up the laptop, both of the two laptop  fans start up and then stop, but no matter how long i leave the laptop on for, the secondary(i think) one does not start up again. The laptop may be over heating, causing freezes. Or may its just too old to function well any more, or something.

But whatever the real cause may be for the freezes it's most likely not Ubuntu.

---

