---
title: "using xserver-xorg-video-intel driver on Feisty may fix sound and network problems?"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by rrwo on 2007-05-03
First off: apologies for starting a separate thread on this, but it's easier than posting the same message to several different threads about what seems to be inter-related problems.

I've been having several problems on Feisty:
[LIST]
[*]Sound worked from a cold boot, but rarely from warm boot or resume
[*]Intermittent problems with network cards (particularly wireless)
[*]Other vodeo modes than the default not recognised
[/LIST]
I also note that my sound, video and network cards are all Intel cards (I have a ThinkPad Z60m).

While trying to fix video problems, I changed my driver from xserver-xorg-video-i810 to xserver-xorg-video-intel.  It recognizes the video resolutions, but won't let me change to them (xserver stops with errors.)

However, it seems the sound now works from a warm boot (I still need to check resuming form hibernation), and so far the network cards are working better.  So it may be worth a try for others who are having these various problems.

Also: from [this thread]("http://ubuntuforums.org/showthread.php?t=420185&page=3&highlight=915gm") it seems that the 915resolution driver is no longer needed.

---

