---
title: "xorg.conf for Radeon X300 with TV-Out anyone?"
date: 2011-04-02
forum: Installation &amp; Upgrades
---

### Post by mikeydeeeee on 2011-04-02
Just loaded Kubuntu 10.10 amd64.  Love it, but I'm having trouble getting persistant video settings across logins.  Every time X restarts, the server comes up in 800x600 clone mode between the DVI monitor and the S-Video outputs.

Granted, it isn't a huge issue (I just use krandrtray to put the S-Video 'RightOf' the DVI and set the sizes to 800x600 and 1152x864 repectively) but that gets to be a drag after a while, since one then has to resize a lot of the screen elements (like the toolbars and some of the apps) by hand also.

Tried setting up a '.xprofile' but that seems to have no effect, and even if it did, I still think I'd have to resize the screen elements by hand again.

It would be great if krandrtray would remember it's settings across logins, but that functionality doesn't seem to exist.  Be a great improvement for the next version, though, especially if the goal of all of this to _really_ get rid of the xorg.conf.

So anyway, I believe that leaves me with xorg.conf.  Tried using xconfig to generate one, but the file it comes up with is so generic as to be useless.  Tried customizing that one, but had no real luck.  Tried pulling a few off the net, but again, no luck.  Tried customizing them, again poor results.  Plus I hate working on these files, go figure. 

So I was just hoping somebody out there has a good, working file I could load and go with.  That, or somone could point me in the right direction of a less manual solution.

Anyone?
MikeD

---

### Post by mikeydeeeee on 2011-04-09
Again nobody?

OK, went and found an alternate solution, which involves putting your xrandr commands into a file named .xsessionrc, not .xprofile.

Got it from [this article]("http://ubuntuforums.org/showthread.php?t=1130521&highlight=.xprofile").

MikeD

---

