---
title: "Asus 1000he and Jaunty - Is wifi working?"
date: 2009-03-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by crispeto on 2009-03-28
I know there have been a bunch of problems with 8.10 and wifi on the eee 1000he. Has anyone tried Jaunty on the 1000he? If so, how's the wifi? Thanks.

---

### Post by zelabby on 2009-03-29
I just installed 9.04 this evening on my 1000he, and WiFi is working right away.  No tweaks or anything were necessary.

Incidentally, the brightness fn keys work, and so do the volume keys.  Multi-touch works, to a certain extent, but it's not customizable at this point, as far as I can tell.

---

### Post by crispeto on 2009-03-29
Awesome, thanks for posting. My 1000he will be here Monday. Can't wait. I put Jaunty on my son's eee 900 and so far everything's working. Even compiz works. Very cool. By the way Zelabby, how did you install 9.04? On the same partition as windows or the other blank partition?

---

### Post by justinjstark on 2009-03-30
I just got my 1000he today.  I installed Jaunty and everything is working 100% out of the box.  Wifi connects to my airport router with WEP perfectly.

---

### Post by IanW on 2009-03-31
I found my 1000he wouldn't reconnect to wireless after resuming from suspend, until I installed "linux-backports-modules-jaunty".
Otherwise, it's perfect.

---

### Post by chris062689 on 2009-03-31
I have 8.10 on my Eee 1000HE and it's working fine, out of the box.
What "problems" have you heard about?

---

### Post by crispeto on 2009-03-31
If you do a search for "1000he" you'll see that some (including me) are having some wifi connectivity issues.

---

### Post by justinjstark on 2009-03-31
After playing with the netbook for a day, I have found that connecting to networks can be a bit finicky.  The other day it just wouldn't connect but a simple reboot seemed to solve the problem.  I am using a stock Jaunty install with no backport-modules.  Most of the time, it has worked all of the time.

---

### Post by zelabby on 2009-04-06
Well, maybe I'm lucky, I don't know...I didn't install any of the backport modules that I've ready about elsewhere, and I've yet to run into any problems regarding resume after suspend, disconnections, etc.

As far as dual booting goes, with partitioning, I decided to get rid of the "spare" partition (D:), and I removed the restore partition as well, since I backed up the stock hard drive to a spare I had first.  So I was left with one, big, all-encompassing partition.  When I installed Jaunty, I just used the installation partition editor to add a ext3 partition to the existing NTFS setup, and resized according to my needs.

---

### Post by Guffles on 2009-04-08
Works most of the time for me on the 1000he I just got a few days ago, but connectivity is pretty fickle.  My wireless network, which is currently about 15 feet away from me is being picked up rather weakly, though all my other devices pick it up just fine.  Same thing with other networks.

I don't recall experiencing any issues like this on Windows with the 1000he, though admittedly I only used it for an hour or two.

Anybody know if there's any way to increase the sensitivity or otherwise get it to uh, well, not drop the connection whenever it feels like it?  I don't want to have to switch to Windows. :(

Oh, and I do have the linux-backports-modules-jaunty package installed.

---

### Post by crispeto on 2009-04-08
Hmmm, I'm not sure now. Once I installed the "linux-backports-modules-jaunty" I haven't really had any problems. Just curious, what type of router do you have? I've wondered if it's the combination between Ubuntu and certain routers.

---

### Post by Guffles on 2009-04-08
> **crispeto said:**
> Hmmm, I'm not sure now. Once I installed the "linux-backports-modules-jaunty" I haven't really had any problems. Just curious, what type of router do you have? I've wondered if it's the combination between Ubuntu and certain routers.

Off the top of my head, I forget the exact model but it's by D-Link.  Thing is, though, the networks at school and other places that both my Macbook and iPod touch pick up just fine are picked up just as poorly by my 1000he as my home network.

---

### Post by justinjstark on 2009-04-08
> **Guffles said:**
> Off the top of my head, I forget the exact model but it's by D-Link.  Thing is, though, the networks at school and other places that both my Macbook and iPod touch pick up just fine are picked up just as poorly by my 1000he as my home network.

I have noticed that the 1000he doesn't pick up a signal very well.  There are places on campus at my university where I have trouble connecting because the signal strength is poor.

I have no idea whether this is a linux issue or a hardware issue but signal strength seems to be fairly poor on all the networks I have tried.

BTW: I do NOT have the jaunty backport modules installed.

---

