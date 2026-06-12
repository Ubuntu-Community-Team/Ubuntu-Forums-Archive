---
title: "Just upgraded Ubuntu to 12.04 LTS...got a few errors"
date: 2015-03-05
forum: Installation &amp; Upgrades
---

### Post by Ka Fish on 2015-03-05
I'm running a tower I built on the 32-bit OS. I has 1.5 gigs of ram, AMD Sempron Processor 3100+. I have a 256 k Nvidia GeForce 6200/PCI/SSE2/3DNOW AGP card in it. My first issue is my main monitors resolution has only one choice, 640 x 480 (3:4). It has the label AOC on the front  of it, but the OS reads Unknown DV1-1-0 & it's a little blurry. The second monitor, a dell is working just fine. I also can't seem to find a few things like games & my favorite Linux Multimedia System. I checked the software center, it said they where installed. I've tried reinstalling LMMS, still I can't open it. I used a picture slideshow as my screensaver before, now I don't seem to have a screensaver. I can't change my background color or get the mouse to single click, like the options just aren't there. I am fairly new so I hope this is a good start to figure out whats going on here.

---

### Post by TheFu on 2015-03-06
Did you have a question? Didn't see any in the first post and don't want to guess.

Let's stick to 1 question - the video.  Do you have the nvidia driver loaded or are you using the open source driver?
Can you use the proprietary GPU configuration tool?  nvidia-settings was the name, I think.
[http://blog.jdpfu.com/2011/03/11/nvidia-gt-430-install](http://blog.jdpfu.com/2011/03/11/nvidia-gt-430-install) might provide some more ideas for you to work through this. It is for 10.04, but the nvidia stuff was very similar - just different versions of the software.  You'll need to be careful to get drivers that are known to work with your specific GPU.

BTW, 12.04 is 3 yrs ago, so many people will have forgotten the desktop issues with that release since 14.04 was released. I know I don't recall any of those clearly anymore.  Most companies and individuals should load 14.04 for new installations today, even though 12.04.5 is supported until 2017.  Desktop users move quicker to new releases, in general.

---

### Post by Ka Fish on 2015-03-06
It says Nvidia accelerated graphics driver (version 304) recommended. I think it's an open source driver. I'm just gonna upgrade to 14.04 & go from there. Thanks

---

### Post by Ka Fish on 2015-03-09
I have upgraded to the latest version & now it seams I have a few more issues. I only have internet access threw a wifi card connected to a hot spot on my phone. It was working before the upgrade, now I get this '(32) Not authorized to control networking' or 'You do not have the required privileges to perform this action org.freedesktop.policy kit error failed: (system-bus-name, name: :1.188) org.debian.apt.update-cache'. When it's booting it gives a list of 'unable to execute...' sorry it's to fast for me to read all of it. I tried to open the system settings to see what I could fix on my own but that box pops up mysteriously empty. It won't allow me to change any of my user settings either. It says I'm admin, but it's like I'm locked out. It sent 3 error reports. It strangely says I have wifi access before I log in. How do I figure out what is wrong & fix what's missing?

---

