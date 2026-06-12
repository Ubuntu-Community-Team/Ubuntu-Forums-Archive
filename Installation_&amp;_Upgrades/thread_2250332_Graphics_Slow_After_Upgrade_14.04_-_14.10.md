---
title: "Graphics Slow After Upgrade 14.04 - 14.10"
date: 2014-10-28
forum: Installation &amp; Upgrades
---

### Post by r-launchpad-celian-dk on 2014-10-28
Using Gnome Ubuntu, Dell XPS 13, intel 915 Graphics

After upgrading from 14.04 to 14.10 there are a lot of places where the graphics are working much slower than they were before:

- Gnome Shell Interface is very sluggish, visible "chops" (redrawing) when pressing the [Super] key.

- Selecting text in Gedit takes a full second pr. line

Experiences some subjective improvement when I booted kernel 3.13.0-37 instead of 3.16.0-23, but that may be my imagination as the problem persists.

I've searched google, forums, found a couple of relevant links that point to the issue being the Intel drivers.


[LIST]
[*][http://askubuntu.com/questions/539629/intel-graphics-speed-regression-14-04-%E2%86%92-14-10](http://askubuntu.com/questions/539629/intel-graphics-speed-regression-14-04-%E2%86%92-14-10) 
[*][http://www.webupd8.org/2014/10/ubuntu-1410-available-for-download.html#comment-1652086424](http://www.webupd8.org/2014/10/ubuntu-1410-available-for-download.html#comment-1652086424) 
[/LIST]

But the drivers currently in 14.10 should be newer than those supplied by Intel to 14.04 so that doesn't make sense to me. As one Intel developer wrote:

"[I]I would like to point out that since what we do is bring more ecent  versions of the software to the target distributions than they ship  with, a 14.04 targeted installer is unlikely to bring much to a 14.10  installation, which most likely has the same or more recent versions  already anyway."
[/I]
Source: [https://01.org/linuxgraphics/node/375](https://01.org/linuxgraphics/node/375)

---

### Post by r-launchpad-celian-dk on 2014-10-28
Video choppy with new kernel, slightly better using older but still pauses every 2 seconds or so.

---

### Post by r-launchpad-celian-dk on 2014-10-28
Reported Bug: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1386721](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1386721)

---

### Post by macsociety on 2014-11-11
OK, an oddity for me today I thought I would post.

I also had very slow UI since updating from Ubuntu Gnome 14.04 to 14.10.   Workspace or window switching was slow as molasses.  Seemed the two  apps for me that made window switching real slow were Evolution and  Firefox.  Once I quit those things seemed normal.

I have been running my i7 based system from the Intel 4000 based on  board graphics as I could not get my nVidia 750ti to work.  Therefore I  had BIOS set to use the on-board video.

Today I decided to set video back to PCI1 that my nVidia is connected to  but leave the HDMI display connected to my on-board video.  Took longer  to boot but she did boot and guess what..... my system is running much  faster UI now.  Those problem apps from before that bogged down the  workspace switching.... not doing it any more.

Really strange but for me.... the UI is peppy again.

I will run like this for a day or two to see what happens.

TJ

---

### Post by macsociety on 2014-11-11
Maybe during boot since my system does not see a display connected to my nVidia switches back to on-board with with something "new and different" video driver wise that still allows my on-board to work but working better now than what it had before when I told it to boot to that on-board video.  Not a computer guru so no idea but as I type this, speed is back to quality I had with 14.04 yet I am on 14.10.  No more slow workspace switching at all!

TJ

---

