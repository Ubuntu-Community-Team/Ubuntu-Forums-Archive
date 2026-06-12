---
title: "Install delivers &quot;mixed signals&quot; on wi-fi connection"
date: 2021-06-01
forum: Installation &amp; Upgrades
---

### Post by davepool on 2021-06-01
(Background) I have a Lenovo ThinkPad X131e that I bought used a couple of years ago and use it as my backup laptop. In addition to the factory HD (which now holds Kubuntu and Linux Mint) it has a 20gb mSATA card that the previous owner used for storage. I decided early on that it might be fun to put a lightweight distro on it and see how it might run. I chose Zorin 15 Lite and it worked fine...except, with an 8gb footprint and a 5gb swap area on the mSATA, there were always signs that updates were challenging.  So I decided to go shopping for another lightweight distro. Ultimately (details below), I decided on Lubuntu, a distro I'd used before on yet another laptop and liked how much of the Ubuntu experience it could deliver with less of a footprint than Zorin 15 Lite.

Okay, the problem I'm facing is this: The ThinkPad X131e is a rugged device but it is also cursed with the dreaded Broadcom BCM-4313 wi-fi adapter. After I first got it I discovered that lots of distros do not play nice with it. Also....full disclosure here...in the past few days I've also tried installations of Bodhi Linux, Linux Lite, AntiX and Peppermint before landing on Lubuntu, which I really want to make work. Some of them (looking at you, Bodhi) fail on install for other reasons. But the problem most are having is with (drum roll) wi-fi connection! And even when I run them Live, I get confirmation that a wifi connection *has* been established...but when I open Firefox and try to navigate somewhere, there's much wheel spinning and the notification that it's having trouble connecting to that page (which is to say any page). If I go ahead and attempt to perform the installation from within Live, I'm notified immediately (like, right now with Lubuntu) that the device does not have an internet connection...this despite the fact that I can check that (via the icon in the tray) and be told, again, that there's an active connection.

The two distros on the HD are still functioning properly and connect to the internet via my home wifi without problem (just now reconfirmed) so there's nothing about the BCM-4313 or my modem/router or my internet provider that's standing in the way of a proper internet connection. Any ideas why/how Lubuntu is being fooled into thinking it's got a wifi connection that *shows* connection but.....won't?

---

### Post by davepool on 2021-06-02
(Follow-up) For what it's worth, here's what has happened in the day  since I posted the first message: I'm sure this will read like I was  just throwing things at the problem but I decided to try Xubuntu  (21.04). Those attempts saw installs fail (twice, the second time with  an ethernet connection) when it would not create a partition (as with  all other attempts, I was simply putting the new distro on/in the same  partition previously occupied by Zorin 15 Lite). No previous installation attempt of any other distro had failed for this reason. Because those  installations failed, that still left me with a successful install of the last  previous distro attempt, Peppermint (which, like the others, had the  problem with the BCM-4313).

My thought was to see if I could get  *anything* to install...so I looked through my collection of USBs and  found EndeavourOS. This installed without a problem (at least as far as  the partition goes) though it had even worse problems with wi-fi: not  even recognizing that there were any signals in the area at all! But at  least I knew that there was nothing about that partition that should  prevent installation. 

I tried Xubuntu again (and again with the  ethernet connection)....and, as before, I saw install failure for the  *same* reason -- would not create a partition.

So, I decided to  regroup completely and go back to where I started. I still had the USB  for Zorin 15 Lite. And I'll bet you can guess what happened. Flawless  installation, recognition of the wi-fi signals, confirmation of the  wi-fi connection *and* a connection that worked! The wi-fi connection  delivered web sites and all of the updates since the USB was created.

From  size standpoint, I still don't think Zorin 15 Lite is the best distro  for this rather odd, shoe-horned installation on an mSATA card  (reportedly 8 gb footprint) and I still think the goal of trying to get a  smaller distro was worthy and I got to the point where I really wanted  an Ubuntu-family distro to work....but, ultimately, (and for reasons  totally unclear to me) Zorin 15 Lite works and the others don't.

---

### Post by grahammechanical on 2022-04-15
Leaving aside the problems with installing various distributions which are not related to the title of this thread. I do not understand what Zorin OS Lite has that other distributions also based on Ubuntu have. When a distribution is based upon Ubuntu as Zorin is the underlying OS in the distributions are close to being identical. The differences being the desktop environment, the user interface, system utilities and default applications.

The Linux developers provide the firmware (drivers) that distributions use. The Broadcom WiFi drivers are proprietary and are maintained by the Broadcom developers. They are not part of the Linux firmware package. When we install Ubuntu we can choose to install non-free third party software. That usually brings in proprietary drivers where necessary. I do not know if this is true regarding Broadcom WiFi adapters.

We can test if a Wifi adapter has a driver when we run the Try Ubuntu session. If we have an Ethernet connection to the modem we can download and install drivers in the Try Ubuntu session. For Broadcom this is the advice given:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Regards

---

### Post by guiverc on 2022-04-15
Ubuntu LTS releases have multiple kernel stack choices; and there are few mentions of  specifics in the first post.

Lubuntu LTS ISOs (as with other Ubuntu *flavors*) follow the pattern Ubuntu Desktop used with 18.04 LTS and before. The original media (20.04 & 20.04.1 for example) use the GA kernel stack, where as 20.04.2 and later media uses the HWE kernel stack.  Ubuntu Desktop and some *flavors* also offer OEM stack options - Lubuntu does not on it's ISOs, thus if you want OEM kernel stack, you install them yourself as per Lubuntu (*or any other Ubuntu documentation*) as they aren't on Lubuntu media.

The original post doesn't mention specifics with regards stack, and that can make a difference with kernel modules (ie. *drivers*). Ubuntu uses the ISO itself to dictate the stack that is default (except for ISOs using the `subiquity` installer which let the user select the stack; ISOs using `ubiquity` or `calamares` *or di* do not). Products that are based on Ubuntu could be opting to provide a different default stack to what Ubuntu does thus making them appear different (ie. Zorin); but with Ubuntu you can have multiple stacks installed & select at boot time which you want to use; the ISO used to install just sets the default kernel stack.

re:  *lightness* .. I still use devices that have 1GB of RAM so understand *lightness*, but the *lightest* will not be a specific system unless your chosen *apps* match the desktop/WM etc you've chosen to use.. Xubuntu now that it's all GTK3 is heavier that it was (*just like MATE when it ported years ago now*), but if you're using GTK3 apps its extra weight won't be noticed when compared to Lubuntu and its use of *LXQt/Qt5* given its libs/toolkits won't match anything need for GTK3 apps. You (OP) appear, at least to me, to be missing many details that, at least in my opinion, matter.

---

### Post by guiverc on 2022-08-01
I don't know what release of Lubuntu you're using, nor what kernel stack you opted to use (*the installation media used sets the default kernel stack as I tried to describe in my prior post*) so I can' t provide any more details.

---

