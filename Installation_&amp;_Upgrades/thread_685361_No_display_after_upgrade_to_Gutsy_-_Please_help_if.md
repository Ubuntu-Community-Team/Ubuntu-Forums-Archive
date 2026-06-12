---
title: "No display after upgrade to Gutsy - Please help if you can."
date: 2008-02-02
forum: Installation &amp; Upgrades
---

### Post by AlchemyMan on 2008-02-02
Very odd. I chose to upgrade via update manager, and the process was, all in all, a pretty smooth run. No error messages or anything of the sort. Some of the changes even became apparent before the required reboot. As soon as I restarted to PC I got the familiar Ubuntu splash screen. However, as soon as the bar is full and the system is due to start, all I get is blackness, at least on my second try (on the first try I got some flickering and a frequency error on the monitor). The monitor light begins to blink.

I believe I can get into the recovery mode, but, being something of a greenhorn still, I don't even know where to start. I hope one of you kind people might know something about this, as I'd very much like to keep running Ubuntu on that machine. I have not yet tried a clean install or a Live CD, but I just dled the iso and will hopefully try that tomorrow. Before then, any ideas or thoughts are very, very much appreciated.

---

### Post by AlchemyMan on 2008-02-02
Oh, its an Athlon processor, 32bit, I think, with a gig of ram and, I believe, an Nvidia card (which I've heard might be the perpetrator?) The monitor is a bulky, ancient 19" CRT. Unfortunately I can't remember more off the top of my head. I got the whole setup used off of various folks on craigslist a couple of months back, and it has since served, running Feisty, as the official desktop of my studio.

---

### Post by zvacet on 2008-02-02
Boot in recovery mode and type 

```
dpkg-reconfigure xserver-xorg
```

When it comes to drivers choose **vesa** and continue to the end.Restart and you should have basic graphic.Now you can look for your video card drivers.

---

