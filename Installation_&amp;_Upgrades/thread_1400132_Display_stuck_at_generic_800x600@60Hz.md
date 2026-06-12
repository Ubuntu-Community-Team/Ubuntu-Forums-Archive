---
title: "Display stuck at generic 800x600@60Hz"
date: 2010-02-06
forum: Installation &amp; Upgrades
---

### Post by TinOfSoup on 2010-02-06
Hi,

I've just installed Ubuntu 9.10, but I can't get my display to go above 800x600 at 60Hz, which really isn't satisfactory by any standards.

Display preferences offers 640x480 or 800x600 at 60Hz and states "Monitor : Unknown". "Detect Monitors" doesn't do anything. My monitor is an old Iiyama Vision Master Pro 1413 CRT, and the graphics are Intel 845 based. (Yes, this is a relatively ancient system, but that shouldn't be causing problems like this...)

I'd be quite happy to select my settings manually like Windows' "List All Modes" lets you do, but I'm not being given the option.

While messing about, I managed to get a xorg.conf file, but I can't get settings for that which'll give me what I want anyway >:-(

Any help would be appreciated, thank you.

- TinOfSoup

---

### Post by lemming465 on 2010-02-07
According to the [Iiyama documentation]("http://www.iiyama.com/Download/documents/manuals/102/ms_GL/LM704UT-en.pdf") it has .25mm dot pitch, resolutions up to 1280x1024, 110Mhz dot clock, and is recommended for 1024x768 at 85 Hz refresh, which should be fairly nice.  It's supposed to do VESA standard DDC, too.

First question: how sure are you that the monitor still works correctly?  E.g., has it worked properly recently with anything else, such as Windows XP, Ubuntu 8.04, Fedora, anything?

If you have confidence in it, or especially if it works properly with something other than Ubuntu 9.10, you may be a victim of the underlying churn in the linux kernel & Xorg driver support.  There is a major re-engineering project underway; we're about 1.5 years into a 3-4 year journey, and some of us are temporarily ending up as collateral damage along the way.  Various Intel, ATI, and Nvidia users have all been victims; you needn't feel singled out :-(

If reinstalling with something that happens to work better such as perhaps Ubuntu 9.04 or 10.04 alpha 2 isn't a good option, then you are going to have to create and fiddle with /etc/X11/xorg.conf.  I don't know if you have any experience with that.

Some helpful things to read in preparation include *man xorg.conf*, *man xvidtune*, the [Xorg video modes FAQ]("http://www.x.org/wiki/FAQVideoModes"), and perhaps [Eric Raymonds' old Xfree86 mode setting howto]("http://tldp.org/HOWTO/text/XFree86-Video-Timings-HOWTO"), which was indispensible back around 1995.

The first thing I'd try is a really simple Xorg.conf asking for the VESA driver, along the lines of:```

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "vesa"
EndSection
```
See if that offers you any more video choices.  If not, you are going to have to write your own *Section "Monitor"* paragraph with hand-crafted modelines.  If that seems daunting, post the contents of */var/log/Xorg.0.log* and we may be able to offer more specific advice.

---

### Post by TinOfSoup on 2010-02-08
> **lemming465 said:**
> According to the [Iiyama documentation]("http://www.iiyama.com/Download/documents/manuals/102/ms_GL/LM704UT-en.pdf") it has .25mm dot pitch, resolutions up to 1280x1024, 110Mhz dot clock, and is recommended for 1024x768 at 85 Hz refresh, which should be fairly nice.  It's supposed to do VESA standard DDC, too.

Yes, but for some reason it doesn't appear to be passing the EDID info to the computer. I thought connecting it directly to my computer might help (it normally goes through a KVM), but it didn't seem to work.

> **lemming465 said:**
> First question: how sure are you that the monitor still works correctly?

Yes, it definitely works fine under Windows XP using 1024 x 768 @ 85 Hz. (1280x1024 @ 60Hz is also possible but- flicker aside- is pushing it picture/usability-wise).

> **lemming465 said:**
> you may be a victim of the underlying churn in the linux kernel & Xorg driver support.  There is a major re-engineering project underway; we're about 1.5 years into a 3-4 year journey, and some of us are temporarily ending up as collateral damage along the way.  Various Intel, ATI, and Nvidia users have all been victims; you needn't feel singled out :-(

I'd much rather it was an isolated incident; that sounds pretty worrying for the state of Linux. 2 1/2 years (possibly) is a very long time in the computer world.

Would the problem be with the Intel 845 drivers specifically?

> **lemming465 said:**
> If reinstalling with something that happens to work better such as perhaps Ubuntu 9.04 or 10.04 alpha 2

IIRC I also had display problems with installing 9.04 on my other machine, though I didn't spend much time with it. (To be fair, that had an ATI card, which isn't as great for Linux AFAIK).

As for the alpha... no offense, but if I have to resort to that simply to get Ubuntu to work, it'd probably be more sensible just to use another distro.

> **lemming465 said:**
> isn't a good option, then you are going to have to create and fiddle with /etc/X11/xorg.conf.  I don't know if you have any experience with that.

I have varying brief experience messing around with XF86/xorg.conf, but nothing serious. IIRC, the older distros used to include setup tools for it. Ubuntu doesn't seem to include that, though given that it doesn't even include xorg.conf by default, it's probably not surprising :-)

The FAQ is interesting, and no doubt informative, but... more reminiscent of the "roll your own" Linux era of the 90s that made even the aforementioned XF86 setup tools seem luxurious than Ubuntu's "modern" reputation. :neutral:

Your VESA xorg code was a snippet rather than a whole xorg.conf file, right? (It looks pretty short, and it didn't do anything on its own when I C&Ped it).

Thanks for the info anyway; I'll have another go at this tomorrow or when I have more time. :)

- TinOfSoup

---

### Post by lemming465 on 2010-02-12
> I'd much rather it was an isolated incident; that sounds pretty worrying for the state of Linux. 2 1/2 years (possibly) is a very long time in the computer world.

From Ubuntu release to Ubuntu release the open source video drivers get better for 99% of the users.  Unfortunately, there are temporary regressions for the other 1%, possibly including you.  With proprietary vendor binary drivers, e.g. nvidia, it's always a question of a) how stable is it and b) have they ported it to your kernel yet.  In terms of releasing documentation to allow open source drivers, ATI (after being acquired by AMD) is currently the best.  In terms of paid staff writing open source drivers, Intel might be on top.  I'm not sure about the '845 specifically; all of my own systems currently have ATI or Nvidia video chips.

> As for the alpha... no offense, but if I have to resort to that simply to get Ubuntu to work, it'd probably be more sensible just to use another distro.
And none taken; I routinely deal with 5-6 different distributions myself.  Ubuntu happens to be my current home desktop of choice, but tastes and needs vary, and there are hundreds of possibilities.  For a possibly different video experience, I'd try either Fedora or OpenSUSE.

> ... the older distros used to include setup tools for [Xorg.conf]...
This is more of an Xorg consortium thing than an Ubuntu thing; everyone is trying to move to auto-configuration.  These days xorg.conf is just an override option, I think, for cases where autoconfiguration isn't doing what you want or need.
> Your VESA xorg code was a snippet rather than a whole xorg.conf file
Just a snippet, yes.  I'm not enough of an expert on xorg.conf to be sure if you need a more extensive file with all the various paragraphs; I was naively imagining you didn't, and that autoconfiguration would cover the rest, but I could be wrong about that.

---

