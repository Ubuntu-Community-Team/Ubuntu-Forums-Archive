---
title: "White Screen instead of desktop in 10.10 (Radeon 7500 card)"
date: 2010-10-03
forum: Installation &amp; Upgrades
---

### Post by ubanksy on 2010-10-03
I have upgraded an IBM T41 laptop from UNR 10.04 to 10.10 beta.  Upgrade ran fine.

After rebooting, I see the splash screen, and eventually the screen goes white.  It does this over a few transitions, most likely in the time between X starting and having the desktop loading (I have auto logon enabled).  

Once it is all white, I can Ctrl-Alt-F1 to the terminal.  Since then I have disabled auto login but same result.  I have also removed Unity (I use UNR and the T41 doesn't have a 3d graphics card), and have the same white screen.

Only after removing xserver-xorg-video-radeon, can I get to the Ubuntu Desktop (in 16 colour glory).

The Thinkpad T41 has a Radeon Mobility 7500 in it, and ran fine in UNR 10.04 (which is also a different kernel).

There was no xorg.conf in use (although I have added one during testing and forced the radeon driver to load) and I reviewed xorg log but didn't see anything.

Any ideas on how to get X working properly again?

---

### Post by marcog on 2010-10-03
Same problem here on a Lenovo S10-2. Did you manage to find a fix?

---

### Post by Mark Phelps on 2010-10-03
To both of you ...

If you're going to upgrade to pre-release versions of Ubuntu, then you need to keep a close check on the appropriate Development forum -- which is where these kinds of posts (and answers) are supposed to go.

As a matter of fact, if you check the Maverick Development forum and do a search on ATI, you will find a post dealing with radeon-driver problems that also contains a fix.

So, please go to THAT forum with your questions, not here.

And in the future, please post your Beta-related questions to the proper Development forum.  You'll get answers a lot quicker that way.

---

### Post by marcog on 2010-10-03
Sorry, this was the first result I saw when searching for the problem. I have re-posted here: [http://ubuntuforums.org/showthread.php?p=9921026#post9921026](http://ubuntuforums.org/showthread.php?p=9921026#post9921026)

---

### Post by ubanksy on 2010-10-03
OK cheers.  I did try #ubuntu+1 irc channel with no response,  and reviewed the Beta page to try and work out which forum this post belongs in.  I would suggest clarifying the beta page with a direct link to the relevant forum.

For others, the correct forum is: 
Ubuntu Forums > The Ubuntu Forum Community  > Other Community Discussions  > Development & Programming  > [Maverick Meerkat Testing and Discussion]("http://ubuntuforums.org/forumdisplay.php?f=385")

This question has been reposted and **solved** [in there]("http://ubuntuforums.org/showthread.php?p=9921466")

---

