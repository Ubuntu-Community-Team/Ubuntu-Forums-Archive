---
title: "Did not configure X when installing"
date: 2006-03-13
forum: Installation &amp; Upgrades
---

### Post by tompaten on 2006-03-13
Yeah, I messed up. I did not select a resolution when installing now X won't start. How do I configure it with out the GUI running?

---

### Post by taurus on 2006-03-13
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by tompaten on 2006-03-13
<sigh> that was not the problem. It looks like Ubuntu does not support my on-board ATI Xpress 200. I even set non-plug and play setting in the BIOS and reconfigured X anyway. No luck. It says "Unable to find a frame buffer deice" in the report I can hardly read. I'm have another (PCI E) card I'm going to install on saturday. If it dosn't work then, I'll start to worry. :(

---

### Post by mstlyevil on 2006-03-13
[QUOTE=tompaten]<sigh> that was not the problem. It looks like Ubuntu does not support my on-board ATI Xpress 200. I even set non-plug and play setting in the BIOS and reconfigured X anyway. No luck. It says "Unable to find a frame buffer deice" in the report I can hardly read. I'm have another (PCI E) card I'm going to install on saturday. If it dosn't work then, I'll start to worry. :([/QUOTE]

If you have a Nvidia card you will have the best results.

---

### Post by tompaten on 2006-03-13
I wish, I already bought it. ATI X850 XT. It's sitting in my dorm at school. It was the best bang for my buck at the time. I dislike Nvidia anyway. It like the "Intel" of the video card world. There are some things I just won't buy, even if it fits togather better with Linux.

---

### Post by brucehohl on 2006-03-20
I think you can get your ATI Xpress 200 video working.  With Ubuntu 5.10 you have to change to the vesa driver or use the latest ATI drivers from their web site.  See this post:  [http://www.ubuntuforums.org/showthread.php?t=144053&highlight=xpress+200](http://www.ubuntuforums.org/showthread.php?t=144053&highlight=xpress+200)

Bruce

---

