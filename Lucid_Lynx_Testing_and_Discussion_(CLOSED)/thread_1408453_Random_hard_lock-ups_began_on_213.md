---
title: "Random hard lock-ups began on 2/13"
date: 2010-02-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2010-02-16
Just as the title says beginning on 2/13 I started experiencing hard lockups which is scary to me because that's how Karmic is on my hardware to this day. Needless to say that renders an OS unusable!

Anyway last night I started to do some searching, well I had previously tried downgrading all kernel related packages without success, and that pretty much left Xorg as the culprit so I ended up finding this:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/370292/comments/53](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/370292/comments/53)

I decided to give it a whirl and so far so good :D

Needless to say but I will anyway:

**If it ain't broke don't fix it, and if this breaks it you own it!**

I should clarify a bit. Random may not be accurate in describing these lockups, they always seemed to happen when the computer was 'idle" for 2 to 10 minutes at a time. But never long enough for any power management progs to kick in, nor even the screensaver. (The lockups in Karmic are truly random and therefore nearly impossible to troubleshoot!)

As mentioned previously I tried a fresh install and avoided upgrading any kernel related packages past 2.6.32-12. To clarify; I avoided any updates related to 2.6.32-13! That made no difference. So I decided it was likely a bug in X. That also made sense because I had no clock activity, PS2 keyboard and mouse were totally dead, etc.

Now regarding that patch I don't understand the proper file name????????? Because I'm dumb;) But the packages updated are:

```
libdrm-intel1 (2.4.17-0ubuntu2) to 2.4.17-0ubuntu2+freezefix~gomyhr1
libdrm-nouveau1 (2.4.17-0ubuntu2) to 2.4.17-0ubuntu2+freezefix~gomyhr1
libdrm-radeon1 (2.4.17-0ubuntu2) to 2.4.17-0ubuntu2+freezefix~gomyhr1
libdrm2 (2.4.17-0ubuntu2) to 2.4.17-0ubuntu2+freezefix~gomyhr1
```

The scary part is that it doesn't include ppa-purge support so if the patch breaks things, and since X is involved, you would probably only be able to revert by mounting and chrooting your Lucid and then using nano to comment out this PPA, then using "apt-get --purge remove" on all four packages, and of course reinstalling those packages along with any dependencies that were removed during the "purge".

**[COLOR="Red"]Not for the faint of heart![/COLOR]** If things really go to the devil you could end up having to reinstall.

Just thought I'd share this in case it's helpful to anyone.

---

### Post by kansasnoob on 2010-02-16
Oh, we might also want to consider nominating this for immediate release unless the devs beat us to it.

---

### Post by kansasnoob on 2010-02-16
Ouch!

Machine just rebooted with no interaction whatsoever.

Seriously I was sitting here rolling a smoke with nothing running on the box and it just randomly rebooted :p

That was strange, and no - I wasn't rolling wacky-tobaccy!

---

### Post by kansasnoob on 2010-02-16
Uh oh! Second random reboot.

This time I was just sitting here eating a burger and it totally rebooted on it's own.

Ghosts I tell ya! It's ghosts, lol!

---

### Post by Ibidem on 2010-02-16
Do the patches switch freezes to reboots?
What hardware is this?

---

### Post by kansasnoob on 2010-02-17
> Do the patches switch freezes to reboots?

It appears so.

> What hardware is this? 

VIA PC2500 Mainboard
VIA Esther C7 CPU 1500MHz
System Memory 2GB DIMM
VT8233/A/8235/8237 AC97 Audio Controller
CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] Graphics

I also had trouble with Karmic freezes with a Biostar mobo w/AMD Sempron CPU, the one thing in common is the CN700/P4M800 GPU. 

It seems that the Openchrome drivers can't get any Xorg love :(

The same GPU has worked great with Gutsy, Hardy, Intrepid, & Jaunty. I'm using Jaunty right now as my stable OS and it's great.

---

### Post by Seventh Reign on 2010-02-17
> **kansasnoob said:**
> Uh oh! Second random reboot.

This time I was just sitting here eating a burger and it totally rebooted on it's own.

Ghosts I tell ya! It's ghosts, lol!

I've seen this too many times.  It sounds to me, like your CPU is overheating.  Either your CPU fan is failing or you need to add/replace thermal grease.  Another possibility is a short or a loose connection from your PSU.  The CPU Overheating causes this problem more often, but I've seen the PSU cause the issue a few times.

---

### Post by gomyhr on 2010-02-17
> **kansasnoob said:**
> 
CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] Graphics


The patched libdrm only touches intel-specific code, so it shouldn't have any effect  with this graphics chipset.

> 
The same GPU has worked great with Gutsy, Hardy, Intrepid, & Jaunty. I'm using Jaunty right now as my stable OS and it's great.

I'm also using Jaunty as my stable OS.

> 
The scary part is that it doesn't include ppa-purge support so if the patch breaks things, and since X is involved, you would probably only be able to revert...


I don't understand what you mean. The easiest way to revert is to use ppa-purge which I usually get from the xorg-edgers PPA.


> 
Now regarding that patch I don't understand the proper file name?????????


The source package name is libdrm. When a source package is uploaded to a PPA, it builds all the binary packages that comes from it.

This is the patch:
[http://cgit.freedesktop.org/mesa/drm/commit/?id=4f0f871730b76730ca58209181d16725b0c40184](http://cgit.freedesktop.org/mesa/drm/commit/?id=4f0f871730b76730ca58209181d16725b0c40184)

---

### Post by kansasnoob on 2010-02-17
@ Seventh Reign,

> It sounds to me, like your CPU is overheating.

I'm certain it's not. I have sensors-applet setup in my panel and also have thermal monitors for CPU, GPU, and HD setup on my tower just because I do a lot of testing.

> Another possibility is a short or a loose connection from your PSU.

I doubt it. Jaunty runs fine on the same hardware.

I'd never encountered "hard-lockups" prior to Karmic, and in Karmic they truly are "random". It might happen anytime after X starts regardless of app usage. Using Xorg-edgers (fresh-crack) reduces the frequency.

So far in Lucid it seems to be a different deal. It was freezing when idle, now "ghost-booting" when idle. I've found nothing so far in the logs. And Lucid's X had been stable with this GPU for quite some time.

Not a big deal at the moment, but I certainly hope for hardware compatibility w/Lucid because I've built over 30 computers for seniors that all have the VIA UniChrome P4M800 chipset.

Most are still on Hardy, a few on Jaunty, none will run Karmic. No sweat yet because Jaunty's good until October and Hardy's good until next April but I definitely need to watch Xorg development.

---

### Post by kansasnoob on 2010-02-17
@gomyhr,

Thanks for taking the time to reply.

> The patched libdrm only touches intel-specific code, so it shouldn't have any effect with this graphics chipset.

I wondered about that.

> I'm also using Jaunty as my stable OS.

It's a great OS. It's always just worked out-of-box so to speak.

> I don't understand what you mean. The easiest way to revert is to use ppa-purge which I usually get from the xorg-edgers PPA.

I've used xorg-edgers (fresh-crack) in Karmic (and it did reduce the frequency of X-crashes) but I didn't know if ppa-purge would work with your PPA or not. I just like to warn people before they "leap".

I could care less if I break my own stuff but some people get steamed so I make a big deal of warning people. Just in case :)

Thanks again. This may be just a temporary development issue. If it doesn't resolve in a few days I'll try filing a new bug report.

---

### Post by kansasnoob on 2010-02-17
I was just doing some note checking and I see the last time I had an issue with Lucid X-freezes was over 2 months ago with the Alpha 1 iso:

[https://bugs.launchpad.net/ubuntu/+bug/494642](https://bugs.launchpad.net/ubuntu/+bug/494642)

Hopefully this will just be resolved with dev updates :)

---

### Post by kansasnoob on 2010-02-17
Not absolutely sure yet but I found this:

> gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
bluetooth-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
polkit-gnome-authentication-agent-1: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
The application 'nautilus' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
gnome-screensaver: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gdu-notification-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
applet.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
update-notifier: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-panel: ../../src/xcb_io.c:385: _XAllocID: Assertion `ret != inval_id' failed.

in /home/<username>/.xsession-errors and at the same time I noticed that some .gconf settings were not staying set where I put them.

Anyway I backed up my /home and generated a new one from the Live CD, then copied my docs, browser profiles, etc. back to /home and so far so good.

This particular installation of Lucid has been running since I downloaded the tool-chain in November so lots of things could be partially hosed :D

In fact I just checked var/log/apt and I see that I did this install of Karmic in October to do some Ubuntuzilla testing.

---

