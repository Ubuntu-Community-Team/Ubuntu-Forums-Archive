---
title: "Problem installing with Samsung HDTV as monitor"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by neilkelly21 on 2007-10-26
My computer is connected to a Samsung HDTV via an RGB cable.  My problem is that the TV displays a "not supported mode" during installation, and I can't move on from there.  I learned from a Windows XP installation that the TV needs to see 1024x768 resolution.  Is there any way to force a resolution during install, or alternatively install from Windows?

---

### Post by oxmyx on 2007-10-27
I've got the same problem. You can force the resolution with F4 on the CD boot screen, but it doesn't help me. I'm pretty sure that it's the refresh rate. Ubuntu is probably trying to query the TV for the rate and setting the wrong one from the info it gets. I've even tried in Safe Graphics Mode and lower rez settings with no luck.

I'll post the fix if I figure it out.

---

### Post by oxmyx on 2007-10-28
The only way I could get 7.10 on my computer was to install 7.04 and upgrade it to the latest version. It seems that 7.10 is a step backwards in terms of compatibility for HDTV's and newer hardware. Search for the HP Gutsy install thread for some theories and rants.

From what I could tell, my system wanted to set 1280x1024 rez no matter what monitor was connected to it with the Gutsy Live CD. The Ubuntu 7.04 works right from the start as it runs at 1024x768, which my Samsung likes.

My lesson learned is to test the beta's in live CD mode from now on and scream loudly to the dev team when they don't work on all the various systems I use Ubuntu on. Could it be that the user community was so comfortable with Feisty that we failed to provide a much needed service? I know that's what I did, I never downloaded or tested Gutsy until now.

From now on, I'll try the latest dev builds burned to a CD-RW from time to time and give these wonderful programmers a heads up.

---

