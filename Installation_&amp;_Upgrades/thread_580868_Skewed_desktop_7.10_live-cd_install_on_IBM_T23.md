---
title: "Skewed desktop 7.10 live-cd install on IBM T23"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by Caroon on 2007-10-19
Trying to run the live-cd to do a fresh install on an IBM T23 laptop produces an stretched out desktop with lines all through it that cannot be viewed. The videocard is a SuperSavage 16MB, and currently working with Ubuntu 7.04.

I've tried going to a shell and reconfiguring X with: sudo dpkg-reconfigure xerver-org but it only gives an error saying xserver-org is not installed.

Also while in the shell the following error pops up too: bcm43xx: Error: "Microcode "bcm43xx_microcode4.fw" not available or load failed.

Any ideas how to get Gusty working on a IBM T23 Laptop?

---

### Post by ppkkss on 2007-10-20
I've been trying Xubuntu 7.10 with the Live CD after 7.4 had multiple problems on myT23.  I see this same problem if I boot off the CD with an odd 3COM wireless card plugged in. I was just experimenting with various wireless cards I have sitting around to see if they work now and a 3COM 3CRGPC10075 PC Card produced this same result. Can't imagine why, hope this helps.

---

