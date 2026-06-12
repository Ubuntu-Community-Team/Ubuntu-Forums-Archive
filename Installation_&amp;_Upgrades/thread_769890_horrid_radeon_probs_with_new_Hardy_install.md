---
title: "horrid radeon probs with new Hardy install"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by tomhorsley on 2008-04-26
lspci says I have a Radeon R100 QD [Radeon 7200] in the AT7-MAX system I just installed 8.04 on using the alternate text installer. When X comes up, the colors are wacko, the text is horribly fuzzy, yet xdpyinfo claims to be running at the 1280x1024 truecolor mode that it should be using for my samsung LCD. If I take a screen shot, and look at it on a different system, all is fine (see [http://home.att.net/~Tom.Horsley/ubuntu.png](http://home.att.net/~Tom.Horsley/ubuntu.png) for screen shot), but what shows up on the screen is nothing like that, so I had to resort to taking a photograph (see [http://home.att.net/~Tom.Horsley/ubuntu2.png](http://home.att.net/~Tom.Horsley/ubuntu2.png) for the photo). Note that the horrible text in the photo isn't that fuzzy due to the process of taking the picture, it really looks about that bad with eyeballs. I swear this isn't a hardware problem because the OS formerly on this system produced perfectly wonderful video (in fact, centos, debian, and Win XP have all been on this box very recently with no display problems).

On the plus side, it did install on the AT7-MAX motherboard (7.10 wouldn't).

---

### Post by tomhorsley on 2008-04-27
OK, explicitly setting the driver to "vesa" in the (rather bare) xorg.conf file makes everything look much more normal, so it appears to be somthing unique to the radeon driver (which, according to the log is the one X picks when given the default xorg.conf file).

---

