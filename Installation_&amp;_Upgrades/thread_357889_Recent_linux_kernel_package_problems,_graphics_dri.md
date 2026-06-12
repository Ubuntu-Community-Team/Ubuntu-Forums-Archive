---
title: "Recent linux kernel package problems, graphics driver installs, updater"
date: 2007-02-10
forum: Installation &amp; Upgrades
---

### Post by blueglow on 2007-02-10
Hi, I was just about to post this in the [WARNING RE LATEST UPDATE: Broken dependency: linux-image-generic]("http://ubuntuforums.org/showthread.php?t=356408") thread when it was closed.

I wanted to give some feedback and ask a couple of questions... Firstly this was a fantastic help with driver installs:
> **clickwir said:**
> If you have any troubles with the Nvidia or ATI drivers, I'd give this script a try. Even if you are having some trouble starting X and suspect maybe theres a possibility that it could be driver related. I'd try this script.

Info: 
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Download:
[http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.1-0ubuntu6_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.1-0ubuntu6_all.deb)

It will automatically download the latest version, compile it with everything it needs and do the config for you. I've run it on several systems and has been the easiest way to install a driver I have ever done.

This also fixed my X600 Fglrx/Mesa problem, though I did have to uninstall all the fglrx and xorg-drivers first and reboot before running it again.

This script/package is very good and it - or something very similar (with a GUI) - really should be part of all future Ubuntu releases. There are so many part-accurate or out of date graphics driver/Beryl/Compiz etc. install HowTos all over these forums and the web that often contradict one another. Good work and kudos to the creator. I know there's a free driver, but it is very slow and perhaps should be a 2nd-to-last resort. Video driver install should be a fundamental and totally automatic part of any convincingly user-friendly OS IMHO. 

I'd just like to echo the comments made by Steve.K, Nda and others in the above thread that while many people will see no problem in the last 48h's events, in reality it did Ubuntu's reputation no good whatsoever. Forum staff and developers get a thumbs up though (and some :popcorn: )

Can someone in the know please outline why the updater continued to advertise a broken package for so long? The error was first reported quickly but its persistence in the updater (despite lots of 'check for updates' clicking) meant the number of users affected rose dramatically. This is one area I think some improvement could be made; pulling back updates as soon as they are reported faulty by a significant number of users.

Well done on getting it fixed chaps :KS , though I'm sure there are lessons to be learned :redface: .

Kind regards,

Jim

---

### Post by guice on 2007-02-10
Just have to add, using the envy script fixed it for me, too. I see it just downloads the latest driver from nvidia and compiles it on the spot.

---

