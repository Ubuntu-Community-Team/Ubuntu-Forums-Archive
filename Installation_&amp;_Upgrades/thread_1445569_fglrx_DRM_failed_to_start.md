---
title: "fglrx: DRM failed to start"
date: 2010-04-02
forum: Installation &amp; Upgrades
---

### Post by quadproc on 2010-04-02
Once again I visit the arcane world of drivers and learn things that may be useful to others.  And I hope that someone can explain to me why things are as they are.

I upgraded from Ubuntu 9.04 to 9.10.  I had been using a dual HD 4870 ATI graphics system using the 10.3 ATI driver with no problems.  When the upgrade finished and the new boot happened, I was presented with graphics that had errors and which was running in "low graphics mode".  Looking in the Xorg.0.log I found that there were a couple of error messages indicating that DRM had failed to start.

I studied the situation for a while, learned that my xorg.conf file was just the same as it used to be, tried blacklisting the Intel graphics module (because I don't have any Intel graphics hardware), and still had the same problem.

Then it occurred to me that the last time I did an OS upgrade, I had to remove and reinstall the fglrx driver to get the graphics to work at all.  So I did that and things started to work OK.  So, if you have done an OS upgrade and your ATI graphics are unhappy, this remove/reinstall approach might work for you.

My questions are: could someone please explain why I would need to remove and reinstall the same driver?  Alternatively, was there something else that I could have done to make the system happy?  Thanks.

quadproc

---

