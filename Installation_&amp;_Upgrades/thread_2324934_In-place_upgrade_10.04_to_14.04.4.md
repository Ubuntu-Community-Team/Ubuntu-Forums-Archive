---
title: "In-place upgrade 10.04 to 14.04.4"
date: 2016-05-17
forum: Installation &amp; Upgrades
---

### Post by moot2 on 2016-05-17
Is it possible to do an in-place upgrade from 10.04 to 14.04.4 using the DVD? i.e., should I get an upgrade option when booting the DVD?
If not, what sudo commands would I need to run from terminal?

---

### Post by Bashing-om on 2016-05-17
moot2; Ouch .

The software repository for release 10.04 no longer exists If one were to attempt an inplace upgrade will have to go the EOL path. That in and if it's self is fraught with doubt; as so much in the operating system has changed from 10.04 . Make sure you have all your data backed up prior to proceeding with:
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

While it is possible
[INDENT][INDENT]may not be the best solution
[/INDENT][/INDENT]

---

### Post by oldos2er on 2016-05-17
I would think you'd need to go from 10.04 to 12.04 then 14.04; but so much has changed since 10.04 you'd be better off backing up any sensitive data, then doing a clean install of 14.04 or 16.04.

---

### Post by grahammechanical on 2016-05-17
> should I get an upgrade option when booting the DVD?

When booting the DVD the only options are Try Ubuntu or Install Ubuntu. It has always been that way. If we load the Ubuntu DVD in an already running Ubuntu installation, well, then we might get an offer to upgrade. I, personally, would only risk doing that to upgrade from 10.04 to 14.04 as an experiment. Expect failure.

Regards.

---

### Post by moot2 on 2016-05-17
Thanks all for the replies. I am relatively new to Ubuntu and want to use old laptops (32 bit, Pentium 4, etc.) as learning tools for beginners to see that they don't need MS to spoon-feed them everything. That said... I have to learn too.
I was trying to find i386 based .iso images - but - for some reason it seems difficult, for me anyway. I did finally find 10.04 and while installing that found 14.04.4 in i386 flavor. I would like to just start with clean installs of 16.04 (or most resent ver) but I cannot find a i386 32bit image.
Can anyone tell me where to get a Ubuntu 16.04 .iso - from a authorized Ubuntu.org site?

---

### Post by oldos2er on 2016-05-17
[http://releases.ubuntu.com/16.04/](http://releases.ubuntu.com/16.04/)

---

### Post by moot2 on 2016-05-17
Thank you very much.

---

### Post by oldos2er on 2016-05-17
You're welcome. Good luck!

---

### Post by $yl9pAR%t on 2016-05-17
> [COLOR=#000000]want to use old laptops (32 bit, Pentium 4, etc[/COLOR]

I guess you will be more happy with Xubuntu or Ubuntu MATE:

[http://cdimage.ubuntu.com/xubuntu/releases/16.04/release/](http://cdimage.ubuntu.com/xubuntu/releases/16.04/release/)

[http://cdimage.ubuntu.com/ubuntu-mate/releases/16.04/release/](http://cdimage.ubuntu.com/ubuntu-mate/releases/16.04/release/)

---

### Post by moot2 on 2016-05-17
Thanks for the suggestions... I will give them a try... any pros-cons for them vs Ubuntu? I would like to keep the resource usage at an absolute minimum, but still have browser, email, etc...

---

### Post by RobGoss on 2016-05-17
Hello and welcome, If you're concerned about conserving resources then you might want to try a lighter distro like **Lubuntu** it works well on older machines [https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu) of course there a few more you can try but this is a starting point. Ubuntu.16.04 will require more Ram and resources.

It will also help others if we knew what the specs were for your machine

---

### Post by Bashing-om on 2016-05-17
moot2; Humm,,,,

Depending :
> 
. any pros-cons for them vs Ubuntu? I would like to keep the resource usage at an absolute minimum,

on your will to do, experience level and aggravation threshold;
consider:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
Where ALL that is installed is the kernel, and minimal networking . You can boot the kernel and then install only what you want .

I run minimal and let me assure you I am impressed .. FAST on old hardware.

There is that learning curve
[INDENT][INDENT]do you have what it takes
[/INDENT][/INDENT]

---

### Post by grahammechanical on 2016-05-17
All the flavours of Ubuntu are complete distributions. They all have the usual set of applications. Maybe not the exact same applications but the same set of useful applications. The system utilities will most likely be different.

The differences as regards system resource usage are a matter of different window managers and window compositors. Ubuntu uses something called Compiz that is both a window manager and a window compositor and so the user can have special effects at the expense of increased use of system resources when compared with the other flavours which do not do compositing.

They also have different Desktop Environments and User Interfaces. In this case it comes down to a matter of personal taste. All the flavours of Ubuntu are built on Ubuntu. They have the same Linux kernel and hardware modules. And receive the same support from the Ubuntu kernel team in regard to security fixes.

Regards.

---

### Post by moot2 on 2016-05-18
Thank you all for the good input and advise... I will be going through everything said...
First, the system I'm on:
IBM ThinkPad T30, Memory: 1000.3 MiB, Processor: Mobile Intel® Pentium(R) 4 - M CPU 1.80GHz, Graphics: R100 (RV200 4C57) x86/MMX/SSE2 DRI2, OS type: 32-bit

Where I am now: I'm running 14.04.4, try from dvd. The reason is as follows...
I installed 16.04 (iso from releases.ubuntu.com), first time with Internet connection and updates options checked. It got to a point of downloading language packages and was taking forever, some of the download time estimates where hundreds of minutes+. Tried to skip... things just got worse, so I did a hard power down.
Next I did the install without Ethernet and selected not to start Wi-Fi. The installation succeeded and I was able to boot from HDD to desktop. I still left the cable out and when I went to connect to my Wi-Fi there were duplicate wi-fi networks (Intersil ISL3874 [Prism 2.5] / ISL3872 [Prism3] (wireless 802.11b MiniPCI Adapter))
I saw my SSID and when I clicked I got the Authentication dialogue - but it would not connect.
I booted off the install dvd and selected the 'try' option - same thing, duplicate, no connect.

Right now I'm running the desktop from the 14.04.4 dvd and am connected wireless, interface 802.11 WiFi(wlan0), Security WEP 40/128-bit Key(Hex or ASCII), Mode: Infrastructure, Authentication: Open System

What I would like to do, and hopefully someone can help...
First remove duplicate WiFi Networks from 16.04 and install the proper drivers for this adapter, i.e., the same one 14.04.4 is using now... or better...

I'm going to reboot now to the 16.04 and use the Ethernet connection...

---

### Post by Bashing-om on 2016-05-18
moot2; Ouch .. 

May want to re-consider what distribution you want to install/
[https://help.ubuntu.com/community/Installation/SystemRequirements/](https://help.ubuntu.com/community/Installation/SystemRequirements/)
The top of the line ubuntu releases need 2 Gigs of ram for a good experience.

WIFI: the drivers in the liveDVD and the install are different. Once up on a wired connection, try and install the WIFI drivers from the "Additional Drivers" utility. The system will try and match a driver to the hardware.

A better choice might be (l)ubuntu:
" Lubuntu is a faster, more lightweight and energy saving variant of Ubuntu using LXDE, the Lightweight X11 Desktop Environment. It is targeted at "normal" PC and laptop users running on low-spec hardware."
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

In any case ->
[INDENT][INDENT][INDENT]Welcome to 'buntu
[/INDENT][/INDENT][/INDENT]

---

### Post by moot2 on 2016-05-18
> **Bashing-om said:**
> 
The top of the line ubuntu releases need 2 Gigs of ram for a good experience.

I understand but these laptops are maxed at 1 Gig. Anyway, I want my students to have a learning experience first... patience is something these young kids need to learn... to much 'instant gratification'... 

> **Bashing-om said:**
> 
WIFI: the drivers in the liveDVD and the install are different. Once up on a wired connection, try and install the WIFI drivers from the "Additional Drivers" utility. The system will try and match a driver to the hardware.


Tried, no joy...

So is there a sudo command that can remove the device? Once removed maybe another check could find the right driver.
Is there a way to get/use the driver from the liveDVD?
Is there a way to see what driver 14.04.4 is using when running from dvd boot?
Another thought that came to mind is that the adapter is wireless and modem... would explain duplicate entry...
The adapter is Intel, Model: M3AWEB56GA and it does say 802.11b on the label. 

any help out there is appreciated

-----------------------------------------------------------------------------------------
You can lead a horse to water... but you can't make 'em think

---

### Post by Bashing-om on 2016-05-19
moot2; Sorry;

When it comes to WIFI I am real short on experience. I can add no more; others here will have to advise.

I do a lot of old hardware installs, and I can tell you that each and every one is different, sometimes it is a challenge. There are those times I go as low as (D)amn (S)mall (L)inux or tiny core to get a usable system. You and your students may have a different experience if the hardware is all the same  and with the 1 Gig of ram -> a piece of cake.

[INDENT][INDENT]If I knew everything
[INDENT][INDENT]I would not be me
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by moot2 on 2016-05-19
> **Bashing-om said:**
> moot2; Sorry;

 ...others here will have to advise.


Sure hope someone can...

> **Bashing-om said:**
> 

...sometimes it is a challenge. There are those times I go as low as (D)amn (S)mall (L)inux or tiny core to get a usable system...


I'm working on making disks for all the versions (supported) and of the suggested 'lite' flavors' ... I am going to start a thread in the Hardware forum in the Compatibility List area...

Anyway, thanks to all that replied... will keep hope that someone has an answer to the Authentication/connection issue... 
------------------------------------------------------------
You can lead a horse to water... but you can't make 'em think

---

### Post by deadflowr on 2016-05-19
To forgo the hardship of having a rather confusing thread,
Start a thread specific to the wireless issues in this sub-forum:
[http://ubuntuforums.org/forumdisplay.php?f=336]("http://ubuntuforums.org/forumdisplay.php?f=336")

I would also suggest a quick read through of this sticky:
[http://ubuntuforums.org/showthread.php?t=370108]("http://ubuntuforums.org/showthread.php?t=370108")

It's better to simply do this, and have a thread for the wifi, than hoping you get lucky one of the networking gurus passes by and catches this thread.
Good Luck

---

### Post by moot2 on 2016-05-20
> **deadflowr said:**
> To forgo the hardship of having a rather confusing thread,
Start a thread specific to the wireless issues in this sub-forum:
[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

Will do as soon as I collect the wireless-info as suggested below...
> **deadflowr said:**
> 
I would also suggest a quick read through of this sticky:
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

It's better to simply do this, ...

Thank you

PS... I'm using the T30 (wireless connection) with 14.04.4 and it is working pretty good... better than when running XP :P

---

### Post by Bashing-om on 2016-05-20
moot2; Hey, hey ///

If your originating query has been addressed to your satisfaction:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Please to advise us what your decision is/was .

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]all for one and
[INDENT][INDENT]1 for all
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

