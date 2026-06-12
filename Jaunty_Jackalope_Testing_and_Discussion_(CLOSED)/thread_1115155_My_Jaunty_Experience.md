---
title: "My Jaunty Experience"
date: 2009-04-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Sam Lars on 2009-04-03
I have a second Linux partition on my computer that I can boot to, so I updated that to Jaunty a while ago.  The biggest change was how fast it booted.  However, between the 2.6.28-10 and 2.6.28-11 kernels, I lost my wireless...
So I upgraded my main Linux partition to Jaunty.  Big mistake.  It ended up stuck with a bunch of packages, including all of the kernels, that were stuck and refused to configure.  I'm not sure what caused this to happen.  This meant that I couldn't finish the upgrade, and on top of that, the computer totally froze whenever I tried to log in through GDM.
Glad that I have a separate /home partition, I installed Jaunty Beta, and it worked great.  Quite fast on boot.  Feels a little bit faster elsewhere.  UXA works well on my Intel graphics, though I had to disable the "Sync to vblank" in Compiz.  I'm able to use the Compiz wallpaper plugin now (made things slow before).  In Intrepid I could only ever suspend once... then it would always fail and come right back.  I'll have to see how that goes in Jaunty.
Oh, and I also used ext4 for my / partition and converted my /home directory to ext4.  Not sure if it's any faster, it might be.
Overall, pretty nice.  A few of the usual problems, but I'm liking the improvements.

---

### Post by Therion on 2009-04-03
Whenever my updates get stuck the first thing I try is switching to a different server.  

It's about a 99% solution.

---

### Post by Sam Lars on 2009-04-03
Yeah, I think that the server was still changed to default from when I did the upgrade.  I couldn't get into X, and the packages were stuck trying to configure, and I couldn't get them to uninstall or anything.

---

