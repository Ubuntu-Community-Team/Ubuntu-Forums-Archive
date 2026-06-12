---
title: "Exceptionally Poor Performance on Virgin Freedom Netbook"
date: 2010-03-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by DougEdey on 2010-03-26
I'm not exactly sure why, but on my Virgin Freedom Netbook I get horrifically poor performance with the either the Netbook Remix or the Kubuntu Netbook Remix. It's fine with 9.10 and 9.04 but as soon as I stick 10.04 beta on it it grinds to a halt with rollovers on the launchers taking upto a minute to respond (not even clicking just rolling over for the highlight to come up).

A friend on an NC10 has no issues with UNR10.04.

Specs are:

Main Features
Processor	Intel® Atom™ Processor N270, 1.60 GHz, 533 MHz FSB, 512K L2 Cache
Chipset
BIOS	Intel® 945 GSE Chipset + ICH-7M FSB 533 MHz
EFI based BIOS, 1 MB
Operating System	Operating System Genuine Microsoft® Windows® XP Home Edition
System Memory	1GB DDR2 533 MHz (1 x So-DIMM slot, Max. 2GB)
Storage
Hard Drive	120GB SATA Hard Drive
Display
Size	10.2" TFT LCD
Resolution	WSVGA 1024x600
Backlight	TFT LCD Backlight
Video/Audio Features
Graphics	 
Type	Integrated Intel Graphics
Controller	Intel® Gen 3.5 Integrated 133 MHz GFX core
VRAM	64MB Shared Video Memory
Audio	 
Controller	Intel® High Definition Audio, Stereo output
Internal Speaker	2 x 1 W
Internal Mic	yes
Built-in Webcam	 
Resolution	0.3 megapixel

---

### Post by DougEdey on 2010-03-28
So from researching this I have determined that it's the Intel driver (I've tried both .9 and .10) and neither are any good. 

Is there anyway to Force a vesa driver on this now?

---

### Post by macstevejb on 2010-03-28
I have the same Netbook and you are right it is a problem associated with the onboard intel graphics.

As a workaround, you need to add the option nomodeset to the kernel boot options in the grub config (for GRUB 2: edit /etc/default/grub and add nomodeset to GRUB_CMDLINE_LINUX, then run sudo update-grub

HTH

regards,

---

### Post by NCLI on 2010-03-28
Add [this PPA]("https://launchpad.net/~ubuntu-x-swat/+archive/x-retro"), add nomodeset to the Grub boot commands, then go to Synaptic and install the oldest version of the xorg-xserver-video-intel package (Which should be the one from this PPA), then lock it, and do further upgrades with synaptic until the problem is resolved.

 That should help. Oh, and then, [SIZE=6]**_report a bug!!_**[/SIZE]

---

### Post by DougEdey on 2010-03-28
I will report a bug when I've confirmed with myself that I'm happy that I've done as much debugging as possible. There's no point in me just saying "Slow performance" since that doesn't help the developers to do anything, especially when it involves a piece of hardware which isn't easily obtainable or the issue doesn't reproduce on other hardware.

The issue appears to be in the netbook-launcher and I've had to completely replace Ubuntu Netbook Remix in order to install a different flavour that works.

The nomodeset option doesn't sort the performance issue out it just makes it possible for me to get to the display manager.

---

### Post by macstevejb on 2010-03-29
Since we are both using the exact same hardware and Lucid works fine for me, I can only assume that it has something to do with the Lucid Netbook version you are using.

I am using a highly-personalised version of the default Lucid with Gnome which works fine, in fact it's far better than Karmic ever worked on my netbook.

I am sure these teething problems will be sorted come release date, after all we are still only into beta testing here.

regards, :D

---

### Post by DougEdey on 2010-03-30
> **macstevejb said:**
> Since we are both using the exact same hardware and Lucid works fine for me, I can only assume that it has something to do with the Lucid Netbook version you are using.

I am using a highly-personalised version of the default Lucid with Gnome which works fine, in fact it's far better than Karmic ever worked on my netbook.

I am sure these teething problems will be sorted come release date, after all we are still only into beta testing here.

regards, :D

It's *just* the netbook launcher, if I use alt+F2 to launch apps the applications run perfectly fine. I've gone to Lubuntu and it's working super speedy for me

---

### Post by psyke83 on 2010-03-30
DougEdey,

Please paste the output of the following:

```
$ cat /proc/mtrr
```

---

