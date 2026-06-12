---
title: "Random Black Screen Crashes"
date: 2010-02-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by FatalChaos on 2010-02-15
Hey, I just started using Lucid Lynx (again, gave it a shot before but it was too unstable), but now I'm getting random crashes where the screen just turns black with a nonblinking cursor at the top left corner and an immobile mouse. No crash report is detected on reboot, and a quick glance in the log file viewer didn't reveal anything. Has anyone had any experiences like this? 

When these crashes have occurred, here are the programs that have been running: 

codeblocks, pidgin, and chromium.

---

### Post by dmitrijledkov on 2010-02-15
Me too!

I blame Chromium =) happens when I start typing a reply in gmail / textareas on webpages.

You?

---

### Post by Peter09 on 2010-02-15
I think a lot of people are having similar problems, some seem to be graphics driver related, others kernel/gnome related. I have exactly the same problem as you. Lucid is the first release of three that I have followed that I given up on. This is simply because I cannot maintain a desktop or a wireless connection that is useable.

---

### Post by blazemore on 2010-02-15
I blame a conflict between the ATI driver and the current version of X.
Sometimes it does this for me on login, and I have to kill GDM and start x manually. Sometimes it'll just do it, even when I'm not at my computer.

---

### Post by dmitrijledkov on 2010-02-15
Hmm.... But I'm running Intel with 950 soldered on graphics card which doesn't have graphics issue. And the Black Screen of Death doesn't show up unless I open Chromium.....

---

### Post by FatalChaos on 2010-02-16
Yeah I'm using intel integrated graphics too, so I don't think this is a video card related issue. Chromium seems to be a pretty common factor, but those builds update often so hopefully it'll be fixed soon/is fixed (I've been using firefox).

---

### Post by dmitrijledkov on 2010-02-17
I got it with firefox yesterday.

Hypothesis: Is it flash related?

Reason: As far as I remember it was always on the websites that have flash.

---

### Post by dmitrijledkov on 2010-02-17
Tracking it in [https://bugs.edge.launchpad.net/ubuntu/+bug/522937]("https://bugs.edge.launchpad.net/ubuntu/+bug/522937")

Nothing special there yet.

---

### Post by VMC on 2010-02-17
When you say black screen crash, does that mean it will eventually reboot? 

Once its end one of those black screens, first type Alt+F2 and see if you get a pop up dialog. If not try Alt+Ctrl+F1(or F2-6), these are virtual terminals. If you get there then you can investigate some log files. Start with your home dir and view (vi) ".xsession-errors" or ".xsession-errors.old".

If none of this works, try Alt+SysRq+k and see if your brought back to a log in prompt.

Also check out "/var/log" files or "System>Admin>LogFileViewer" is a graphical viewer for var files.

---

### Post by dmitrijledkov on 2010-02-17
> **VMC said:**
> When you say black screen crash, does that mean it will eventually reboot? 

Once its end one of those black screens, first type Alt+F2 and see if you get a pop up dialog. If not try Alt+Ctrl+F1(or F2-6), these are virtual terminals. If you get there then you can investigate some log files. Start with your home dir and view (vi) ".xsession-errors" or ".xsession-errors.old".

If none of this works, try Alt+SysRq+k and see if your brought back to a log in prompt.

Also check out "/var/log" files or "System>Admin>LogFileViewer" is a graphical viewer for var files.

No it will not reboot by itself. I need to press and hold power button to do a hard shutdown.

Keyboard is not responsive. I can't get to tty nor dimm the screen nor bring up "run application". There is nothing in the logs. I'll try more experimenting later on today though. I'm currently busy having fun =)

---

### Post by VMC on 2010-02-17
> **dmitrijledkov said:**
> No it will not reboot by itself. I need to press and hold power button to do a hard shutdown.

Keyboard is not responsive. I can't get to tty nor dimm the screen nor bring up "run application". There is nothing in the logs. I'll try more experimenting later on today though. I'm currently busy having fun =)

It might be Plymouth. Try a test and purge plymouth: 'sudo aptitude purge plymouth' , and see if things improve. Also try 'nomodeset' at the end of linux boot string.

---

### Post by hd_sheena on 2010-02-20
Could someone please direct me to information about this error in Jaunty? I'm also running chrome, but not Lucid. I'm pretty new to linux and the error only happened once, but I'd like to report/share my problem if it helps anyone else out..

---

### Post by FatalChaos on 2010-02-20
Hey, 

Has anyone gotten this crash while using Ethernet, or has everyone been using wireless when this happens? 

I got a crash recently that actually gave me an error, and it said 

invalid framebuffer id 
ath5k phy0: noise floor calibrattor timeout 

Since then I've gotten a few black screen crashes when using wifi, and although this time they don't spit out an intelligble error (just a bunch of random non-english characters including plenty of white blocks), I think it might be bad wifi drivers that are at the bottom of these crashes.

---

### Post by omegamormegil on 2010-03-10
I'm getting these crashes - black screen, with no cursor and my monitor goes into standby.  Chrome/Chromium is not installed.  I am running Ubuntu Lucid with an ethernet connection with ATI graphics.  Alt-Ctrl-F1 and trying to restart blind via the command line does not work.  I have to hold in the power button to get anywhere.

---

### Post by Trespasser on 2010-03-10
From out of the blue my Lenovo G530 with an Intel graphics card, running wireless, will give me a black screen. No cursor...nothing. Alt-F2 or Alt-F5 and Alt F6 did bring me back to the login screen today. An Xorg crash file was in the /var/crash folder but it was locked. Running Firefox, not Chromium. Sometimes just hitting Enter key send me back to the login screen. Again, out of the blue. I hope the Devs get this sorted out before the release date otherwise I'll be sticking with Karmic. Very irritating. But, Lucid still is in the alpha stage so I guess you have to expect this type of thing to happen.

Later...

---

### Post by zika on 2010-03-10
I have a thread about this. First there were freezes, now they became balck-outs. They do not happen if I turn KMS off. I do not have Plymouth installed. It takes from several minutes to couple of days to get a black-out. Totally random. Flash is not common factor for all the black-outs. It is certainly connected to KMS (I have ATI card, xorg-edgers) since I did not have a single black-out while in UMS...
[http://ubuntuforums.org/showthread.php?t=1347430](http://ubuntuforums.org/showthread.php?t=1347430)
[http://ubuntuforums.org/showthread.php?t=1425325](http://ubuntuforums.org/showthread.php?t=1425325)

---

### Post by omegamormegil on 2010-03-10
Bryce says that a new kernel with a patch for DRM might fix this.  Get it here:  [https://edge.launchpad.net/~apw/+archive/red](https://edge.launchpad.net/~apw/+archive/red)

I installed it a couple hours ago, an I haven't gotten a crash since then.  I know it wasn't that long ago, but I was crashing every 15 minutes give or take.  Reply to this post if the new kernel stops the crashes for you.

---

### Post by zika on 2010-03-10
I'm using, currently 2.6.34, but I've got black-outs in all the kernels, 32, 33, 34... I'll think about what...

---

### Post by omegamormegil on 2010-03-10
To be clear, the kernel in that PPA is 2.6.32-16, but it includes a new DRM bugfix backport from upstream, which is intended to fix crashes like this.

---

### Post by zika on 2010-03-10
> **omegamormegil said:**
> To be clear, the kernel in that PPA is 2.6.32-16, but it includes a new DRM bugfix backport from upstream, which is intended to fix crashes like this.Yes, I figured that. But I'm not ready (yet) to regress to 2.6.32... Nomodeset works for me quite well. I do not need KMS... I would like it to work but... On the other hand, since the black-outs are happening in 33 and 34, on my system, with the latest drm from xorg-edgers, I'm a bit reluctatnt to think that solution is in DRM update. I have that update... At least I think I have...

---

### Post by zika on 2010-03-17
I found the location of the bug. If I revert (ppa-purge) from xorg-edgers to "official" Lucid stuff that resides in xorg-edgers, I can have KMS and stable machine for indefinite periods. The moment I upgrade to current xorg-edgers, I get crash... So, I do not have solution, just a hint... This might help someone that knows about or develop this to locate the bug... Yes, I've wrote on this on Phoronix, also, in the proper thread... I do not have enough material to raise a bug, but...

Update: No, I've got crash several minutes ago in KMS with "official" set of packages that are, also, at xorg-edgers. So ball is not in their court... Back to UMS and xorg-edgers... Still hunting... Crashes and not-working-shutdown makes this Lucid testing experience a bit tainted...

The first good advice on where to look for a troublemaker: [http://ubuntuforums.org/showpost.php?p=8986907&postcount=47](http://ubuntuforums.org/showpost.php?p=8986907&postcount=47) Thank You dino99!!!!!

The rest of history of the events is in that thread. It might be useful if Mod's would merge these two threads...

---

### Post by aetherane on 2010-03-28
I have this issue also (ATI card if that matters).

My screen goes into sleep mode randomly and nothing responds. There is nothing in the logs about this.

---

### Post by jaco223 on 2010-03-28
I just reinstalled beta 1 today and have had 2 black screen crashes, not blank screen, but black screen, and I have to hard boot.

---

### Post by aetherane on 2010-03-31
What graphics cards do you all have?

---

### Post by jaco223 on 2010-03-31
> **aetherane said:**
> What graphics cards do you all have?

ATI Raedon HD 2400 XT here.

---

### Post by omegamormegil on 2010-03-31
01:00.0 VGA compatible controller: ATI Technologies Inc RV610 video device [Radeon HD 2400 PRO]

Still crashing, btw.

---

### Post by aetherane on 2010-03-31
I have a ATI Radeon 4850.

It is most likely a problem with the ATI driver, then so I opened a bug report: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/553014](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/553014)

---

### Post by aetherane on 2010-04-09
Did anyone find the problem yet?

---

