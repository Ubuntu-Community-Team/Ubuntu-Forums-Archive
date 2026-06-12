---
title: "i810 plus PCI video card"
date: 2004-10-26
forum: Installation &amp; Upgrades
---

### Post by burque on 2004-10-26
I installed ubuntu on an old Compaq with an i810 video chipset plus an SiS 305 PCI video card. The SiS card is not detected. Kanotix and XFLD correctly set up X on this machine, although of the two only XFLD correctly uses the "sis" driver.

I notice Mepis also does not recognize PCI video cards if onboard video is available. Is this intentional? If so, why? Surely the reaon one installs an aftermarket video card is for it to be used.

Thanks in advance,
burque

---

### Post by jayclark on 2004-10-26
It works like that on almost every os. You can't have more than one graphics card installed in a pc at a time. Of course there is software that allows this as long as you have two of the exact same  graphics cards. But its more trouble than its worth. What you need to do is go into bios, disable the on board video, or enable pci video which ever is there. Reboot and reconfigure x you can do this by using these commands.

X11 -configure
dpkg-reconfigure xserver-commom

---

### Post by burque on 2004-10-27
Actually the "easy" thing to do is edit XF86Config-4, which is what I do. My issue is not with getting X running. My issue is with hardware detection priorities. And I certainly wouldn't recommend anyone go spelunking in the BIOS when it's not necessary.

What I do in distribs that don't feel it necessary to recognize add-in cards if onboard video is present is, as mentioned, edit the config file. Here's the relevant part of my XF86Config-4 file now:
*************************
Section "Device"
        Identifier      "Intel Corporation 82810 DC-100 CGC [Chipset Graphics Controller]"
        Driver          "sis"
        BusID           "PCI:1:8:0"
*************************
(You'll notice the Identifier field is wrong. X doesn't care! It did, however, care when I edited it, so I changed it back.)
As has been posted elsewhere in this forum, the command to use to find out the Bus ID of your PCI card is "lspci". Here's the  relevant output: you'll see from that some truncating of the ID is necessary for XF86Config-4.
**************************
>ubuntu # lspci
[ . . . irrelevant stuff removed . . . ]
0000:01:08.0 VGA compatible controller: Silicon Integrated Systems [SiS] 300/305 PCI/AGP VGA Display Adapter (rev 90)
[ . . . and more irrelevant stuff removed . . . ]
**************************
My point, if there is one in this rant/howto, is that if there is a PCI video card PLUS onboard graphics detected, it should be intuitively clear that the MOST LIKELY scenario is that the computer owner installed the PCI video card to get hardware acceleration and thus, not surprisingly, would like to do that in Linux, and, also not surprisingly, would like it autodetected so he/she doesn't have to edit XF86Config-4 either by hand or with some unreliable tool like xf86config. Knoppix, Kanotix and XFLD are among the distributions that do this with varying degrees of exactitude.

Regards,
Burque

---

### Post by jayclark on 2004-10-27
Of course an OS isn't going to detect pci video if on board is present. Thats why you disable it in bios and never worry about it again. Thus it won't use up cpu cycles or ram. Even if you tell x to use the pci your on board is still running using ram/ cpu cycles. Having on board and add-on graphics cards on at the same time is also bad for the motherboard. When an os boots up, it reads the bios, the bios will tell the os what to use and not to use. The os isn't going to decided which to use because to it a graphics is a graphics no matter if its pci or on board. Also if you disable on board in bios you won't have to configure anything because then the os won't see the on board video.

---

### Post by burque on 2004-10-28
Try Kanotix, XFLD or Knoppix and THEN tell me an OS won't detect a PCI card if onboard graphics are present.

---

### Post by jayclark on 2004-10-28
Yea, I know those do. But they also use a different boot sequence than most distros. Even Windows dosen't do what your asking. You can fix your problem in a couple of seconds. But yet you want to rant about how x or an os should determine like it has a mind of its own. If you want this send it to the xorg team and maybe they'll implement it in the next realease, and when Ubuntu uses it in there next release you can be happy.

---

### Post by FLeiXiuS on 2004-10-28
Disable the onBoard card if you have an alternative PCI card that you wish to use.  If not, then (console mode) should be available.

```

lspci -v

```

This should show you the pci devices installed.  Including onBoard.  

Edit the /etc/XF86Config-4 with your favorite text editor.

Then look for your video settings and correctly modify them.  That should be all.

---

### Post by burque on 2004-10-28
:???: 
Dear Moderator:

I am unable to understand Mr. Clark's ire and will ignore it. 

However, I must take strong exception to the blanket recommendation by both of you that the onboard graphics card be disabled, unless one is NOT going to be dual-booting with Windows. Although disabling the onboard graphics often works, with some configurations it will cause endless trouble.

As a quick Google search will prove, installing a PCI video accelerator card in a Windows box with onboard graphics can be a perilous endeavor: no reason to take my word for it. As a matter of fact, on my HP Pavilion 521c (not a dual boot box) with a Rosewill GeForce MX 4000, the onboard graphics HAD TO be disabled from Device Manager and NOT from the BIOS. If you disable the onboard graphics in the BIOS Windows XP will not see this particular PCI card, despite the fact that is nVidia-based.  Obviously a number of other cards (or perhaps, more correctly put, those cards' Windows driver software) don't suffer from this problem.

Of course if you're going to be using Ubuntu exclusively on a box, then sure, just edit XF86Config-4 and disable the graphics card (if your BIOS will let you.) But many people will be dual-booting from now into the forseeable future. And although their number is (thankfully) decreasing, there are many, many otherwise okay motherboards that don't have an AGP slot. Also, none of this is a problem for anybody that works with Linux on a regular basis.

My concern is for those potential converts to Linux who have the same hardware configuration I do and decide against Linux because there isn't autodetection of their graphics cards by a distribution they try out. 

If there _is_ a concern (which I personally don't feel to be justified) that having onboard graphics and a PCI card is somehow injurious to the motherboard if the onboards are not disabled, then why not autodetect the PCI card and provide a warning message to disable the onboard graphics before rebooting?

As far as Mr. Clark's suggestion about contacting xorg goes, I don't imagine those good people will be getting into the autodetection business anytime soon. 

Regards,
burque

---

### Post by jayclark on 2004-10-28
"As far as Mr. Clark's suggestion about contacting xorg goes, I don't imagine those good people will be getting into the autodetection business anytime soon."

You never know, The folks over at the Xorg team take request seriously. I worked with them on a few projects. From my perspective I don't see a need to. Because most people will disable it in bios or via Device Manger like I did on my HP (bios didn't have the option). If you read a manual for a pci card it even tells you to. Mine did. But of course I already knew I needed to. But from your point of view I can see why this might be a good feature to have. I'll talk to some guys over at Xorg when I get a chance to see what they think. I don't know how soon they could work on it since there is quite a few problems they are working on. It would be simple to do just wouldn't be a main priority.

Jay

---

### Post by daniels on 2004-10-28
The problem is that it's actually quite non-trivially difficult to detect whether you have a PCI or on-board video card.  Also, if you install a PCI or AGP graphics card on top of your existing on-board setup, it's highly likely that you actually know what you're doing, so for X autodetection, we chose on making the most simple case (one detectable card) work perfectly, rather than two cards, which is very difficult to pull off.

---

### Post by burque on 2004-10-29
Hi, this is for Daniel Stone (or anybody else that knows :):

I had always wondered how the autodetection worked, and had assumed that, say, a Perl script would parse the output of, for example, lspci and take certain actions depending on what was in there.

I do notice that the various LiveCd distributions that DO detect the PCI card when onboard graphics are also available will hiccup before X actually starts up, suggesting probing of the graphics card itself, which certainly sounds (as you point out) non-trivial.

Any idea how XFLD, Kanotix and Knoppix do that detection, generally speaking? If you have time, that is -- 

Regards,
burque

---

### Post by daniels on 2004-10-30
There's a C program called discover, which scans the PCI bus for video cards and reports back with the name of the card and which driver is required.  We just take the first match from discover -- there is no real smart heuristic.

I don't know how Knoppix deals with this side of the world, to be honest.

---

