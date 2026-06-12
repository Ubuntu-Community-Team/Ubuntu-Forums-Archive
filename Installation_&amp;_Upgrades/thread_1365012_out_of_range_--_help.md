---
title: "out of range -- help"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by nkalle2 on 2009-12-26
Help
 
I tried installing Ubuntu for the first time (9.10) and I'm getting "out of range" error on my screen whenever I try to launch graphical environment.  I've been Googling for hours; I know its something to do with configuration of my monitor/refresh rates, but I cant find any setting that works.
 
I have a Sony SDM-hs53.  According to Sony docs, it should support Horiz 28-61 and Vertical 48-75.  However I read through the Xorg.log and saw that it was autodetecting a narrower range, H 28-48 and V 57-63.  So as of now my xorg.conf has:
 
Section "Monitor"
 Identifier "Monitor Vendor"
 ModelName "Monitor Model"
 HorizSync 28-48
 VertRefresh 57-63
EndSection
 
I saw one post that recommended "sudo dpkg-reconfigure xserver-xorg". I've tried this a few times but it seems to do nothing.  When I hit enter, it pauses for a couple of secs, and then returns to command prompt.  Any ideas what I might be doing wrong here?  Or any suggestions on how else  I can resolve this?
 
Thanks.

---

