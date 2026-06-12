---
title: "Edgy totally broke X config; can't repair"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by kkinder on 2006-10-28
After upgrading to edgy, I get this when X tries to start:

```

xauth:  creating new authority file /home/kkinder/.serverauth.684

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux lennon 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Oct 27 23:46:24 2006
(==) Using config file: "/etc/X11/xorg.conf"

(EE) module ABI major version (0) doesn't match the server's version (1)
(EE) Failed to load module "ati" (module requirement mismatch, 0)
(EE) No drivers available.

Fatal server error:
no screens found
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 0 requests (0 known processed) with 0 events remaining.

```

I've tried reconfiguring X. No dice.

What gives? Can I revert?

---

### Post by overdose on 2006-10-28
Perhaps post the output from your /var/log/Xinit.0.log.  Perhaps that may give more insight into the problem?

---

### Post by kkinder on 2006-10-28
Hmm, apt-get remove x-window-system followed by apt-get install x-window-system solved that problem... Now if I could get it booting without using safe mode!

---

### Post by overdose on 2006-10-28
Heh.  I wasnt aware ubuntu (linux in general) had a "safe mode"  does it just dump you into a single user environment or something?

---

### Post by Johnsie on 2006-10-28
I had the same problem that the poster of this topic had... It was very easy to fix:

> 
sudo aptitude install xserver-xorg-video-savage



As you can see my card was a savage card. Doing this apt-getted the savage card driver.


**To find out what driver YOU need to apt-get:**

When the blue screen comes up fress alt_ctrl-F1 and login

do:
> 
sudo dpkg-reconfigure xserver-xorg


Do all the autodetect stuff. You will see a screen with a list of possible drivers. It is usually a list of things like nividia,nv,s3,s3 virge, savage etc. Write down the one that was selected.

Then all you need to do is apt-get the driver as shown at the top of this post only replacing "savage" with whatever driver your need.

---

### Post by kkinder on 2006-10-29
Actually I had tried to dpkg-reconfigure it, and it found my card fine and everything, but that didn't solve the problem. I think it must have missed a dependency? Or the setup scripts needed to be rerun?

---

