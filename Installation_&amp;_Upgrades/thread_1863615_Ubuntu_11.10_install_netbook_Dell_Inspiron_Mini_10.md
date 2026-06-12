---
title: "Ubuntu 11.10 install netbook Dell Inspiron Mini 10 Fails"
date: 2011-10-18
forum: Installation &amp; Upgrades
---

### Post by SirWeazel on 2011-10-18
Unable to install ubuntu 11.10 on a Dell Inspiron Mini 10 Netbook. I'm booting from a bootable usb made using the instructions made on ubuntu's site using windows.  I've tested the usb stick on other computers and it works.

The problem: 
When tyring to boot up ubuntu, it starts to load. Then i'm presented with menu to "try ubuntu/install ubuntu/advanced options/test memory" When trying to install/try ubuntu starts to load, but then crashes to a screen with text stating "lightdm mainprocess terminated with status 1". --- sometimes the status # changes, but lightdm always terminates. I've tried starting lightdm again from one of the terminals, but it always terminates.

Sometimes it drops to me a root login, sometimes not. ctrl/alt/# keys take me to various terminals.

---

### Post by SuperDupes on 2011-10-20
Same problem here.

When I try to run 11.10 from USB without installing I get errors like:

No screen found, cannot start X server

When I try to install 11.10 I get errors pertaining to wireless firmware and I get the whole

List ...[ok]
List... [ok]

screen for a wile, and then a blinking cursor indefinetly.

Can't really tell if it's a problem with wireless drivers, or screen drivers.  Went to edit Xorg.conf, but it wasn't there.  Guess I'm living in the past!

Thanks for any help!

---

### Post by persapiens on 2011-10-25
Unfortunately, I have the same problem too :(

Thanks for advance for any help.

---

### Post by SirWeazel on 2011-10-25
I have also tried using universal-usb installer and unetbootin to make a bootable usb. I've tried the alternate install cd also. They all seam to fail in one way or another. I was surprised when the alternate installer failed. It fails during the install process. Any help or info from anyone can help, thanks in advance.

---

### Post by jmadero on 2011-10-25
I was really disheartened when my wife's computer failed with Ubuntu 11.10 (also running a mini). After years of her mini "just working" (Ubuntu 9.04-11.04), now I'm going to have to spend a bunch of time diagnosing problems. Going to bug report if you haven't already, I'll post a link and you can add your info to it as well.

---

### Post by jmadero on 2011-10-25
[https://bugs.launchpad.net/unity/+bug/881462](https://bugs.launchpad.net/unity/+bug/881462)

---

### Post by Terralthra on 2011-10-30
The X server not finding a usable screen has to do with the Mini 10 using the (infamous) GMA500 graphics driver. [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)

I had to fall back to 10.10 to get it to install, and upgrading is fraught with peril, so to speak. 11.04 was not included in the Canonical repos, and there's no sign of 11.10 support.

Working on a fix.

---

### Post by SirWeazel on 2011-10-31
Thanks for the info, please keep us posted if you find a good fix that works. Also, isn't it strange/bad that support just dropped? I'm pretty sure at one point in time one could purchase this netbook model with ubuntu on it, or did the ubuntu version of the netbook come with a different video card?

---

### Post by bjaast on 2011-11-01
Well the funny thing is this one:
[http://www.ubuntu.com/certification/make/Dell/netbooks](http://www.ubuntu.com/certification/make/Dell/netbooks)
Mini 10 and Mini 10v appear as certified and supported....
It's probably not the same model I have, I guess, even if is called "Inspiron Mini 10"...
also the specs don't look the same to me:
[http://www.ubuntu.com/certification/hardware/201010-6646](http://www.ubuntu.com/certification/hardware/201010-6646)
as the network card in mine is clearly a broadcom.

I bought that in sweden, I think Dell ships different components in different countries :(

---

### Post by bjaast on 2011-11-01
An i forgot to mention. Booting from an usb stick systematically dumps to a login screen (for sure a video problem when starting X, but it's silent and doesn't complain about anything...)

---

### Post by Terralthra on 2011-11-01
Potential installer workaround:

MUST BE USING A USB STICK.

Use UNetBootIn to make a USB installer for whatever flavor you favor (I lean towards Xubuntu, personally). Reboot onto the USB stick (on a computer with a working internet connection using the installer).

From there, either from one of the terminals (ctrl-alt-f1) or from within Xubuntu (Try (X|L|K)Ubuntu without installing):

sudo add-apt-repository ppa:gma500/emgd-fix
sudo apt-get update
sudo apt-get install xorg-emgd emgd-dkms
sudo emgd-xorg-conf

If all that completes successfully, put it in your Dell Inspiron Mini 10 and attempt to boot off of it. It **may** work. 

If it does, you may need to follow the above steps again once your install is complete and you attempt to boot off the hard drive again.

All of the packages on the emgd-fix PPA are experimental, and some may be broken on your system. Usual provisos about backing up and inexperienced users beware.

---

### Post by SirWeazel on 2011-11-05
> **Terralthra said:**
> 

sudo add-apt-repository ppa:gma500/emgd-fix
sudo apt-get update
sudo apt-get install xorg-emgd emgd-dkms
sudo emgd-xorg-conf



Did not work for me, also i think the line above should have read "sudo apt-get install xorg-emgd emgd-dkms emgd-xorg-conf"

Either way, it did not work for me. It installed correctly using the bootable usb on another pc, but netbook still errors out when trying to load ubuntu. Did this method work for you? If it did, i'll keep plugging away at, otherwise i'm about to give up. Thanks.

---

### Post by SirWeazel on 2011-11-05
I just found some good info, that i'm currently trying. I'm going to try the "custom iso" that lucazade appears to have made. I started searching, and did find a lot of info for the gma500 intel video. Here are some of the links i found, and i'll post if i get it working.

1. [http://ubuntuforums.org/showpost.php?p=11356431&postcount=4605](http://ubuntuforums.org/showpost.php?p=11356431&postcount=4605) (link to custom iso)
2. [http://ubuntuforums.org/showthread.php?t=1229345](http://ubuntuforums.org/showthread.php?t=1229345) (alot of info to sort through) (this is the thread from the link above, but the thread is growing faster than i can read, so if someone finds better info, please post)
3. [http://askubuntu.com/questions/68935/dell-mini-1010-doesnt-boot-past-splash-screen](http://askubuntu.com/questions/68935/dell-mini-1010-doesnt-boot-past-splash-screen)

There is alot of info out there to sort through, more than i thought. One just needs to know what to search for. I'll post back and let you know how it works out. If someone finds a better thread related to The dell mini 10 then please post.

... just when i was about to give up, something told me to keep looking.

---

### Post by SirWeazel on 2011-11-05
The iso image from the forum I mentioned above (link #1 & #2 from the post above) appears to be working good. It only works well with unity 2d, so if you have a problem then logout and change settings to unity 2d and log back in. I'll work with it some more, but for now I'm recommending this great build that someone (i think lucazade) put together. If credit for the build belongs to someone else then please let me know. Like I said earlier, the thread was growing faster than I could read and had to skim sections.

---

### Post by tarsofagundes on 2011-12-08
I have two dell. Both were installed with the same flash drive installation.

In the Mini 1010 (with 1GB RAM, HDMI input): ubuntu 11.10 i386 desktop did not work. He began to install but stopped talking after a firmware that I do not which. And start show a root login.

In inspiron 1428: ubuntu 11.10 i386 desktop worked perfectly.

Excuse me for bad English.

---

### Post by SirWeazel on 2011-12-08
tarsofagundes, try the custom iso from member lucazade. It worked perfect for me. I provided a link to it in my previous post (post#13 link#1).

---

### Post by jmadero on 2011-12-15
Anyone try this with Gnome-Shell instead of Unity? I have become a "Unity hater" as I've found it ridiculously buggy even on my Dell Studio 1737. I don't particularly love Gnome-Shell but for my wife on her mini I think she'll prefer that over my setup (I'm running E17 with Bodhi). I know there are other options out there but I think Gnome-Shell offers less technical users a lot of options plus a decent looking setup and relatively good stability. If no one has tried I may be attempting it tomorrow evening.

---

### Post by adrianlancer on 2012-03-22
Hi, i make it work for my Inspiron mini 10 **(AKA mini 1011 or mini 10v)**. It have a Broadcom card on it.
I went into the BIOS for that you have to press F2 on the POST screen(dell logo).
I'm using BIOS version A00. 
I went into the "Advanced" tab and chage some of the default settings and here is how its on mine.
	[I]Boot-time Diagnostic Screen 		[Disabled]
	QuickBoot Mode              		[Enabled]
	Intel (R) SpeedStep(TM) Technology	[Enabled]
	**On Board LAN Control			[Disabled]**
	WLAN Control				[Enabled]
	Blootooth				[Enabled]
	USB BIOS Legacy Support			[Enabled]
	USB Wake Support			[Enabled]
	Function Key Behavior			[Multimedia][/I]
*****The important stuff here is to disable the On Board LAN Control*****


i hope this helps):P

---

### Post by radard on 2012-10-01
Thanks adrianlancer

My Dell Mini would not recognize the USB key (with Ubuntu 12.04 on it).

At least, with you solution, I have some reaction from my laptop. I feel I need to continue trouble shooting a bit, as the screen displays as if it was seriously drunk...

---

### Post by mikewhatever on 2012-10-02
> **radard said:**
> Thanks adrianlancer

My Dell Mini would not recognize the USB key (with Ubuntu 12.04 on it).

At least, with you solution, I have some reaction from my laptop. I feel I need to continue trouble shooting a bit, as the screen displays as if it was seriously drunk...

Do you know the exact model of your netbook? Dell Mini 10 is not it, it's rather a generic name, that covers several products, namely Dell Mini 1010, 1011, 1012, and possibly more. Can you elaborate on what's the problem, then someone might be able to offer help.

---

