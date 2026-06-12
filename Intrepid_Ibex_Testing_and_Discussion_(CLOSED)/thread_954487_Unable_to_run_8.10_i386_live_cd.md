---
title: "Unable to run 8.10 i386 live cd"
date: 2008-10-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by rudy.elgato on 2008-10-21
Hi,

I'm currently running 8.04.1 i386, mobo is a GeForce 7050M-M, processor is an AMD Atlon LE-1620, and I'm interested in having a closer look at 8.10.  I've downloaded the current 8.10 i386 iso and burned to cd.  I've started the system from the cd, see the initial set of screens (select language, run without changing system) which I expect.  I hear the cd loading for a minute or so, but eventually get a popup window indicating "Ubuntu is running in low graphics mode:  (EE) No device is detected", then another popup window asking "What would you like to do?"  

The two selections are "reconfigure graphics" or "trouble shoot the error".  Selecting "trouble shoot the error" presents a new window with several logs available to look at, but I honestly do not know what I'm looking for.  I've tried "reconfigure graphics", and tried the several options on the next screen, but the live cd install never goes any further.

Any ideas on what I could/should be checking?  Or is 8.10 live cd mode just not available and maybe I should just wait another couple of weeks for the real 8.10 release?

Any help, guidance is appreciated.

Thanks...

---

### Post by pedro_orange on 2008-10-21
Perhaps this explains your problem: 

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+bug/276180](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+bug/276180)

Have you tried re-downloading the ISO? I've seen a few installs go bad because the image was faulty.

---

### Post by rudy.elgato on 2008-10-21
Wow...  That looks exactly like what I'm running into.  I should have mentioned that I've run 2 seperate i386 iso download and burns, checked their md5 values, and have run the check disk prior to trying to run the live cd.  Everything there all looks fine, just cannot get past that low-graphics mode error.

Thanks for the prompt reply pedro_orange.  I'll keep an eye, maybe add to that bug report.

---

### Post by phidia on 2008-10-21
Some hardware is a nogo with 8.10 (still in testing). A laptop I've tried with the 7150M GPU will not start x even if xorg.conf is replaced with one that works on it in 8.04.

---

### Post by forcecore on 2008-10-21
Similar problem affects me and even using safe graphics mode do not work because it wont enter Driver "vesa" in xorg.conf

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-chips/+bug/272814](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-chips/+bug/272814)

---

### Post by nanog on 2008-10-21
I looked at some of the bugs posted and there is absolutely no information provided that could help the developers solve the problem.

Please refer to these directions for posting X bugs:

[https://wiki.ubuntu.com/X/Reporting](https://wiki.ubuntu.com/X/Reporting)


A summary:

Description of problem

Paste in output of lspci -nn | grep VGA

Get a full backtrace ([COLOR="Red"][X/_Backtracing_]("https://wiki.ubuntu.com/X/Backtracing")[/COLOR])

List any versions you tried that did not have this issue

Steps to reproduce

How complete is the X failure?
+ Does ctrl+alt+f1 take you to a console?
+ Does ctrl+alt+backspace restart X?
+ Does mouse pointer still move?
+ Does the keyboard LED come on when hitting the CAPSLOCK key? + Can you ssh into the system from another computer?

/var/log/Xorg.0.log

/var/log/Xorg.0.log.old

~/.xsession-errors

---

### Post by rudy.elgato on 2008-10-22
The problem I reported at the start of this thread mentions that this happens when trying to run from the live cd.  The commands and information you ask to run and provide in your summary list, is a person suppose to do that while still in the live cd session, or while running from their good installation?  Not sure if I'm clear in the start of this thread, but I have 8.04.1 currently running on my system, and the problem I report happens when I try to run 8.10 from the live cd.

Thanks...

---

### Post by jfernyhough on 2008-10-22
"the problem I report happens when I try to run 8.10 from the live cd."

You should run all that from the LiveCD - the bit that doesn't work.

There's not much point in providing information about a working configuration from what's effectively a different system.

---

### Post by rudy.elgato on 2008-10-22
Right, makes perfect sense, but how do I capture and save all this information while within the live cd session?

---

### Post by Matthewthegreat on 2008-10-22
I have this same problem on my desktop computer! I take the same liveCD and it worked fine in my laptop. I have a 7100 GeForce NVIDIA card on my desktop could this be the problem? Please tell me if some one can help!

BTW 8.04 works fine on my desktop it's just 8.10 BETA liveCD doesn't

---

### Post by rudy.elgato on 2008-10-22
I'm getting exactly the same problem using the 10/22/08 intrepid desktop i386 iso image.

I have been able to save the :0.log, xorg.conf, and Xorg.0.log file that were generated during the live cd session, and have delivered them to [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+bug/276180](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+bug/276180) and hopefully it helps.

What's interesting is the Xorg.0.log contains a huge list of "driver for NVIDIA chipsets:" but my GeForce 7050 is not in that list.  The last couple of lines in Xorg.O.log shows:

(II) Primary Device is: PCI 00@00:12:0
(WW) NV: Ignoring unsupported device 0x10de053b (GeForce 7050 PV / nForce 630a) at 00@00:12:0
(EE) No devices detected.

Fatal server error:
no screens found

---

### Post by Matthewthegreat on 2008-10-22
It's the video card. I took the video card out of my parents computer and put it in my desktop. The live CD booted up fine. I'm going to get a new video card because I have been wanting to do that anyways.

---

### Post by rudy.elgato on 2008-10-23
Mathewthegreat, what kind of card did you take out of your parent's system and put in your desktop?

I'm not a developer, but seems like there's a problem for those of us with NVIDIA GeForce 70** and 71** series chips/cards and the "nv" video driver that is used by default by the live cd. 

I added some more information to Bug #276180 (and 284492 which seems to be a related bug.  hope I don't get into trouble for dumping so much information...) in launchpad...

---

### Post by Matthewthegreat on 2008-10-23
> **rudy.elgato said:**
> Mathewthegreat, what kind of card did you take out of your parent's system and put in your desktop?

I'm not a developer, but seems like there's a problem for those of us with NVIDIA GeForce 70** and 71** series chips/cards and the "nv" video driver that is used by default by the live cd. 

I added some more information to Bug #276180 (and 284492 which seems to be a related bug.  hope I don't get into trouble for dumping so much information...) in launchpad...

My parent's card is a ATI Radeon 9250 (I don't recommend this card for any one who does any gaming). 

If you look at the Xorg.0.log it list the NVIDIA drivers it supports and the 70** and 71** series cards are not listed and it says near the bottom

 (WW) NV: Ignoring unsupported device (and then lists your video card) 

 I just ordered a NVIDIA GeForce 8600 GT because I was wanting to get it anyways. This just gave me reason to buy it now :)

---

### Post by rudy.elgato on 2008-10-23
was thinking of using the problem to get a new video card myself... :)

from this, [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/261977](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/261977), it looks like a fix was committed a little while ago.  I'm guessing, and hoping, this is fixed in the next image.

---

