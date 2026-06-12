---
title: "Problems with X"
date: 2007-09-04
forum: Installation &amp; Upgrades
---

### Post by Delacroix on 2007-09-04
Hey people, I just got this error not too long ago.

I was in the middle of downloading a torrent and watching a video and then suddenly my HDD activity light lit up non stop. I wanted to check which process was causing the activity but I got an error trying to access the system monitor. I then tried to open one of my mounted HDDs and it gave the same error. I restarted the system and I couldn't boot into X anymore. It gave an error saying that my X server needs to be reconfigured or something and it asked me whether I wanted to take a look at the debug log to see what's causing the problem.

The only problem I saw in the log was some log file not being able to move or something. I then booted into recovery mode and it gave a lot of Input/Output Errors and finally after a few minutes I typed sudo dpkg-reconfigure xserver-xorg and the HDD activity light lit up constant again without lighting off. I waited for a few minutes and the blue screen to reconfigure Xserver didn't popup. The red light was still on by the way.

I tried startx and it gave me the same error saying that X has suffered and error and asked me whether I wanted to look at the debug log. 

Anybody know how to repair the installation without wiping my files? I have the alternate install CD here I was wondering whether I could repair the installation like Windows using the CD. Or maybe I could do something to fix this? Anybody know? I have the latest kernal with the latest updates. Ubuntu .04

---

