---
title: "laptop monitor issue"
date: 2011-02-20
forum: Installation &amp; Upgrades
---

### Post by Jeffreylb94 on 2011-02-20
This is my laptop [http://www.thinkwiki.org/wiki/Category:T30](http://www.thinkwiki.org/wiki/Category:T30)... IBM Thinkpad T30, my graphics card is ATI Mobility Radeon 7500... I can get ubuntu working great, but I have major issues... I like to animate with blender, but I need 2 monitors. I hook my external monitor up by vga, and the same thing is showed on both screens. I go to preferences, and select monitor. I found an options that says show same image on both monitors. I uncheck it, and my screen glitches. I still see the same on both screens, except my computer freezes and I do my original screen on the bottom half, and random glitched lines on the top half. I have searched, and searched, but how do I get my graphics card to support multi monitor split? I went to the website and I can find a single driver for linux. I try updating my computer, and nothing works... Please help! I love ubuntu, but I have to stick with xp until this can be fixed... When I do this, and select to show different things on each monitor, my computer will freeze, and my monitor looks like [http://i1199.photobucket.com/albums/aa475/Jeffreybrown94/Extra/123_0549.jpg](http://i1199.photobucket.com/albums/aa475/Jeffreybrown94/Extra/123_0549.jpg)

---

### Post by realzippy on 2011-02-20
What you want is [MergedFB]("http://dri.freedesktop.org/wiki/MergedFB") mode,since you need 3D (Blender).
according to
[http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7500](http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7500)   :
MergedFB works on 7500.
Have  a look [here]("http://en.gentoo-wiki.com/wiki/HOWTO_Dual_Monitors"),*Occasional Dual-Monitors*
You could use that xorg.conf when editing the resolution to your needs for
a quick test.
BTW,..formerly driver installation attempts (?)ensure everything is redone.

---

### Post by Jeffreylb94 on 2011-02-20
> **realzippy said:**
> What you want is [MergedFB]("http://dri.freedesktop.org/wiki/MergedFB") mode,since you need 3D (Blender).
according to
[http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7500](http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7500)   :
MergedFB works on 7500.
Have  a look [here]("http://en.gentoo-wiki.com/wiki/HOWTO_Dual_Monitors"),*Occasional Dual-Monitors*
You could use that xorg.conf when editing the resolution to your needs for
a quick test.
BTW,..formerly driver installation attempts (?)ensure everything is redone.

I'm new to linux, so how do I install the commands? I know the terminal, but the commands it shows doesn't seem to work with terminal

---

