---
title: "Upgrade 9.04 alph5 and &quot;out of range&quot;"
date: 2009-03-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ITA003 on 2009-03-02
Hi all,
Hope this is the right section...

I a 8.10 user, last week I upgraded to 9.04 alpha 5 without problem during install steps. But when I restarted the pc I can not see the login page, the monitor show the "out of range" message.

I try to use xfix command from recovery section but I have the same result... so I try to delete the xorg.conf file but nothing change...

So I make a CD to install, but I have the same result with live CD...

Any Idea?

---

### Post by bodhi.zazen on 2009-03-02
If you are using an alpha release that implies you are willing to file a bug report :)

Be sure to include your hard ware (video card ? monitor ? ).

---

### Post by ITA003 on 2009-03-02
> **bodhi.zazen said:**
> If you are using an alpha release that implies you are willing to file a bug report :)

Be sure to include your hard ware (video card ? monitor ? ).

Bug Report filled.. :popcorn:

---

### Post by bodhi.zazen on 2009-03-02
Thank you for that, may a fix for your problem be swift ...

---

### Post by budluva04 on 2009-03-03
> **ITA003 said:**
> Hi all,
Hope this is the right section...

I a 8.10 user, last week I upgraded to 9.04 alpha 5 without problem during install steps. But when I restarted the pc I can not see the login page, the monitor show the "out of range" message.

I try to use xfix command from recovery section but I have the same result... so I try to delete the xorg.conf file but nothing change...

So I make a CD to install, but I have the same result with live CD...

Any Idea?

If your using an nvidia card, which I was, you might have to manually edit your xorg.conf by hand, which is what I had to do to resolve this.  In my case I had to manually set my depth and resolutions, as this is why your monitor is going out of range, its trying to use a resolution your monitor can't handle.  Either that or try using the "vesa" driver to get a working X setup until you can figure out whats going on...

If you could pastebin your xorg.conf somewhere so we can look at it that would help out alot. Oh yes, along with some hardware info.

A simple google for "nvidia xorg.conf example" will show you what depth and resolution lines you need to add in...I left the rest of my xorg.conf untouched...

---

### Post by ITA003 on 2009-03-03
My Card is

ATI technologies Inc Rage 128 Pro Ultra TF

I tried to use the fglrx driver also, but now I can see the cursor on black screen.

I can not paste the xorg.conf file, I can't use that pc... the only option that use is in Recovery mode and select netroot option.

After work I will copy some line from the xorg.conf file.

What are the changes between 8.10 and 9.10 for video driver?? With the 8.10 works fine.:(

---

### Post by ELD on 2009-03-03
Boot into your pc with an older ubuntu live cd and then copy it ;), the joys of live cds.

---

### Post by ITA003 on 2009-03-03
Good idea!!:D

---

### Post by forcecore on 2009-03-03
this bug was issue to me too with 8.10 on several computers but safe graphics mode (vesa) helped.

---

### Post by ITA003 on 2009-03-03
> **forcecore said:**
> this bug was issue to me too with 8.10 on several computers but safe graphics mode (vesa) helped.

I can enable the safe graphics mode?

---

### Post by ITA003 on 2009-03-03
This is my xorg.cong after xfix command from recovery section:

```
Section "Device"
	Identifier	"Configured Video Device"
        Driver          "r128"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

---

### Post by bodhi.zazen on 2009-03-03
Change > Driver          "r128"

To```
Driver          "vesa"
```

Then re-start X

---

### Post by ITA003 on 2009-03-03
> **bodhi.zazen said:**
> Change 

To```
Driver          "vesa"
```

Then re-start X

Didn't work!

I tried also with "ati" and remove the line "Driver"

---

### Post by ITA003 on 2009-03-04
If I use the Live CD 9.04 alpha5 I have the same problem.

---

### Post by ITA003 on 2009-03-06
In attachment my xorg.conf e Xorg.0.log files.

My video board is a **ATI Technologies Inc RV350 AS [Radeon 9550]**

---

### Post by bodhi.zazen on 2009-03-06
I can not help much, but thank you for using an attachment rather then posting long text :)

---

### Post by Elfy on 2009-03-07
I've never had much dealings with ati cards, but I have seen that there are issues with them until they release a driver.

You could try running the open source driver until it get's a release - there's a bug report here - 
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/313027](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/313027)

```
sudo apt-get remove --purge xserver-xorg-video-ati
sudo apt-get remove --purge xserver-xorg-video-radeon
sudo apt-get install xserver-xorg-video-ati
```

Might help ... 

I know you say you filed a bug report - but you don't give a link so can't see which it is ;)

---

### Post by ITA003 on 2009-03-07
Here the link to the bug:

[336898]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/336898")

Later I will look the 313027.. thanks!

---

### Post by ITA003 on 2009-03-07
> **forestpixie said:**
> 
```
sudo apt-get remove --purge xserver-xorg-video-ati
sudo apt-get remove --purge xserver-xorg-video-radeon
sudo apt-get install xserver-xorg-video-ati
```


Doesn't work... :(

---

### Post by hyperdude111 on 2009-03-08
dont try to upgrade to an alpha always do a fresh install on a different partition this removes some incompatibility issues and allows you go back without loss of data easily.

---

### Post by ITA003 on 2009-03-08
Ok, but I have the same problem with the Live CD, which don't use my Ubuntu installation files...:o

---

### Post by forcecore on 2009-03-08
> **ITA003 said:**
> Ok, but I have the same problem with the Live CD, which don't use my Ubuntu installation files...:o

do safe graphics works it should enter Driver "vesa" in xorg.conf automatically like 8.10 ???

---

### Post by ITA003 on 2009-03-08
> **forcecore said:**
> do safe graphics works it should enter Driver "vesa" in xorg.conf automatically like 8.10 ???

I tried it but doesn't work, after reboot Jaunty tell me that run in low mode ad chose the actions:

- Run in low model
- Reconfigure graphics

The first action can not login, there a blue screen that tell me don't run (or conenct, I don't remember the word) display to port :0, in both answer (yes or no) doesn't change anything.

If I select the second action "reconfigure", after reboot I saw a black screen and the mouse cursor, anything else.

I read that the driver for RV350 are not supported, I tried to install the proprietary driver but the result does not change.

Ps. Sorry for my bad english.

---

### Post by tormod on 2009-03-15
> **ITA003 said:**
> I read that the driver for RV350 are not supported, I tried to install the proprietary driver but the result does not change.
ITA003, did you exchange your r128 card for a RV350 card? RV350 should work fine with the default driver (-ati).

---

### Post by ITA003 on 2009-03-15
> **tormod said:**
> ITA003, did you exchange your r128 card for a RV350 card? RV350 should work fine with the default driver (-ati).

Yes I changed the card to RV350, but with this card I can't see the login page (with th r128 the monitore return a "out of range" error), I see a black screen and the mouse, nothing else. This install is not an upgrade from 8.10 but a new install of 9.04.

I started with default driver and next the proprietary driver.

---

### Post by tormod on 2009-03-15
> **ITA003 said:**
> Yes I changed the card to RV350, but with this card I can't see the login page (with th r128 the monitore return a "out of range" error), I see a black screen and the mouse, nothing else. This install is not an upgrade from 8.10 but a new install of 9.04.

I started with default driver and next the proprietary driver.

Please file a bug if RV350 does not work. But make sure you have no fglrx stuff installed when using the default drivers.

The usual problem on these cards is wrong AGPMode, see [https://wiki.ubuntu.com/X/Quirks#ATI%20AGP%20Mode%20Quirk](https://wiki.ubuntu.com/X/Quirks#ATI%20AGP%20Mode%20Quirk)

---

### Post by ITA003 on 2009-03-16
Sorry, but I re-install the 8.10 version, in this days I need to use the pc.
But I sure that I dont'have the fglrx installed.

In the next Day I retry the upgrade to 9.04
Thanks.

---

