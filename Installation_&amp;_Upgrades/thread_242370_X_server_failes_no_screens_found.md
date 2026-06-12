---
title: "X server failes: no screens found"
date: 2006-08-23
forum: Installation &amp; Upgrades
---

### Post by MisterM on 2006-08-23
Hi!

I've installed Kubuntu a week ago on one of my older machines. I installed all the updates and some additional software via the packet manager and everything was working fine untill today. Now the machine goes through the normal boot process and everything loads OK, untill the X server should start. Then, when the login screen should have appeared, the "splash screen" (the logo displayed during boot) just freezes and nothing happens.

After a couple of hours browsing through various forums I figured out where the problem lies: the X server failes to start. When trying to start it up manually with startx, this error comes up:
```
(EE) No devices detected.

Fatal server error:
no screens found
```

I haven't installed nor upgraded any software since the last boot, when everything still worked, so I really have no idea, what could have gone wrong.

I've attached my xorg.conf and Xorg.0.log files if that helps. And this is all the output I get from startx:
```
xauth:  creating new authority file /root/.serverauth.5056

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux zaphod 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Aug 23 21:13:19 2006
(==) Using config file: "/etc/X11/xorg.conf"

(EE) No devices detected.

Fatal server error:
no screens found
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 0 requests (0 known processed) with 0 events remaining.
```

Any help would be greatly appreciated.

---

### Post by MisterM on 2006-08-24
I should also mention that I tried reconfiguring the X server with and without the -phigh switch, but to no avail. I also tried booting from the LiveCD and copying the generated xorg.conf to the hard disk and it didn't work either. The LiveCD works fine though.

I don't have that much experience with linux, so I really don't know what else to try. I probably just have to reset some setting to default, as it works fine with the LiveCD, but don't know which.

If anybody has any other idea, I would really appreciate it.

---

### Post by Scythe!? on 2006-08-24
Look here, there was a dodgy update. [http://www.ubuntuforums.org/showthread.php?t=241286](http://www.ubuntuforums.org/showthread.php?t=241286)

To fix it I used sudo apt-get update then sudo apt-get upgrade to get the working update.

---

### Post by MisterM on 2006-08-24
Thanks, it worked.

Although I have seen and been referred to that thread many times before, I never bothered to upgrade, since it said I have version 10.4, when I typed this:
```
sudo aptitude show  xserver-xorg-core | grep Version
```
Now I decided to try and upgrade anyway and it worked.

Thanks for the advice.

---

