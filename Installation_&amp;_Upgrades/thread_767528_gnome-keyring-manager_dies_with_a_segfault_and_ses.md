---
title: "gnome-keyring-manager dies with a segfault and session fails to start after upgrade."
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by Ovation1357 on 2008-04-25
Hi All,
   After upgrading from Gutsy to Hardy I was unable to log in. I could successfully enter a username and password, but then was left with just the default background picture and a moveable mouse cursor. This happened for *all* users including root and a newly created test user.

I've been through as many log files as I can find and have checked the binaries for gnome-keyring-daemon and x-session-manager against the ones on the Ubuntu CD (I originally upgraded live using the Update Manager).

In /var/log/messages I get repeated messages like this:
 Apr 24 22:23:39 evo kernel: [   61.761619] gnome-keyring-d[6276]: segfault at 00000014 eip 080759c7 esp bfd29db0 error 6
Apr 24 22:23:40 evo kernel: [   62.845727] gnome-keyring-d[6396]: segfault at 00000014 eip 080759c7 esp b799fdc0 error 6

I removed the following line from /etc/pam.d/gdm :
session optional        pam_gnome_keyring.so auto_start

Now my session starts fine, but of course all the stuff that uses keyring stored credentials (like my wireless network connection) doesn't work.

I've found Bug #218434 in gnome-keyring (Ubuntu):
[https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/218434](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/218434)

This is a real show-stopper for Hardy IMO as it cripples the GUI - My last update from Feisty to Gutsy was smooth as anything so I'm really disappointed that a bug as significant as this has escaped Beta testing.

Ultimately I can't use my laptop properly until this is fixed so if anyone can help me set up some proper debugging to root-cause this (I'm used to using dbx on Solaris but haven't done any debugging in Linux) - I'd be happy to give it a go if anyone can get me started..

Many thanks
Jonathan Heard

---

### Post by zehel on 2008-04-26
You're not the only one having these kinds of problems.  Apparently there is a problem with the update path for Hardly.

[http://ubuntuforums.org/showthread.php?t=762718&highlight=218434](http://ubuntuforums.org/showthread.php?t=762718&highlight=218434) clearly documents this, but the discussion thread has been closed.  I guess if you close your eyes, 8.04 Herring works fine.

You might want to post a confirmation to [https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/218434](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/218434)

I suggest we rename Hardy Herron to Helpless Hamster.](*,)

---

### Post by Ovation1357 on 2008-04-26
Thanks for your reply Zehel. 

What shocks me the most is that Ubuntu must have be making changes all the time right up to the release date as people have reported that this bug is not seen in a beta from a few days before the actual release.
Surely there should have been a period of time where the code tree was frozen to be sure that they actually released a stable version.

I'm pretty disappointed with Ubuntu for this - I've been a happy user since Feisty and hit the 'Upgrade' button with confidence that it wouldn't screw up my machine (upgrade to Gutsy worked like a dream) - And what have I been left with :-(

Hopefully this will get fixed soon, but so far no one has managed to get a proper backtrace from gnome-keyring-manager as it comes and goes so quickly and doesn't appear to be loaded in any kind of hackable script.

I've posted a comment in the bug as several people appear to mention seeing this bug when using flash based boot devices. I'm also booting off a flash card. Don't see why boot media should matter but I wonder if there's any link...

Cheers
Jonathan

---

### Post by sunbird on 2008-04-27
I can confirm this bug on my Macbook Pro 3,1 on an upgrade from Gutsy. Boots to login window fine but then freezes, with dmesg: 

```
gnome-keyrind-d: segfauly at ______ rip ___ rsp ___ error 15
```

I will try the workaround, but I agree this needs priority fixing. Pretty disappointing.

---

### Post by kainam00 on 2008-04-28
I was trying to upgrade from Gutsy and ended up with the same problem as well. I finally gave up trying to fix it and did a clean reinstall... to my surprize, it was still doing the same thing! 

So this is a problem with Hardy (8.04) in general, not just the upgrade.

Gah!

HH seems to be a big flop in the mud for Ubuntu, I think they spent more time making the fancy graphic on the front page than testing the release!

---

### Post by sunbird on 2008-04-30
FYI, a bug has been created [upstream]("http://bugzilla.gnome.org/show_bug.cgi?id=530316").

---

### Post by zehel on 2008-05-01
It looks like this bug has made it to bugzilla/gnome.org.  Most of the reports include a USB/Flash drive install configuration, which is where I have Ubuntu installed.  It looks like we may be on the road to recovery.;)

---

### Post by rennen01 on 2008-05-01
Occurred on my test box from an upgrade.  Re-installed and the is no longer happening.  Too bad, I have had clean upgrades since Edgy on my test box.  :(

---

### Post by zehel on 2008-05-19
Looks like there has been a fix released.  The update is located here:

[https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/218434](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/218434)

Looks like we can call 8.04 Hopefull Herron at least.

---

