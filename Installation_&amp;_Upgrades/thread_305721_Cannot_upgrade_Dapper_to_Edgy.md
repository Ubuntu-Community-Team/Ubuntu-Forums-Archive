---
title: "Cannot upgrade Dapper to Edgy"
date: 2006-11-23
forum: Installation &amp; Upgrades
---

### Post by madcow72 on 2006-11-23
Hello!

I've been using Dapper now for almost 3 months, before that I was Windows...ie. I'm fairly new, but have learned enough to get around.  I'm running Kubuntu on both my desktop and laptop and am trying to upgrade from Dapper to Edgy.  

I've downloaded and burned the Live DVD, Live CD, and Alternate CD for Kubuntu 6.10 and tried: ```
gksu "sh /cdrom/cdromupgrade"
```  After installing the package "python-vte", I tried the same command again, (I've tried all 3 CD's with this) but always run into the same error:  "can't find DistUpgradeViewGtk"

So, next I decided to try official route #2: ```
gksudo "update-manager -c -d"
``` which always gives me the same error:  "sudo: update-manager: command not found"
I've tried this on 2 separate computers and always get the same result...I didn't see any other posts describing this problem.  Any ideas?  Anyone else out there run into the same problems?

Thanks!

---

### Post by deepwave on 2006-11-23
update-manager is part of the Synaptic package.  Synaptic being the standard in Ubuntu, while Adept is the start in Kubuntu.

In my experience, the best, easiest route is running ```
sudo apt-get dist-upgrade
``` from Konsole (command line).

---

### Post by madcow72 on 2006-11-23
Hey, thanks for the reply!  From what I've read, the apt-get solution is not really recommended...supposed to give trouble with X and other hang-ups.  Did that not happen to you?

Maybe another stupid question, but if I were to just install the gnome desktop also on here, could I then use the Synaptic update-manager?

Cheers!

---

### Post by deepwave on 2006-11-23
No question is stupid.

You could install ubuntu-desktop.  But that will bring a whole wack-load of unneccessary apps.  I would just install the synaptic package.

I upgraded to Edgy when it was in beta, but most of the issues have been dealt with.  I did have to run apt-get dist-upgrade a few times to get it right.  And remove sysvinit and install upstart (the new improved init script manager).  The only real problem I found, was that the xorg package complained a bit.  I found a quick work-around with that, and now everything runs smoothly.

---

### Post by confused57 on 2006-11-23
I've used this method to dist-upgrade from breezy to dapper and from dapper to edgy(not the same installation as the previous dist-upgrade to dapper):
[http://www.psychocats.net/ubuntu/dapper](http://www.psychocats.net/ubuntu/dapper)

You might have problems with X if you installed proprietary video drivers, that won't work with the new kernel...

---

### Post by madcow72 on 2006-11-24
Thank you both for your posts to my problem.  However, since my /home directory and all important data exist on separate hard drives from /, I'm presently just installing over 6.06 with the live DVD.  It seems like this method will be the least problematic in the long run.

Thanks again though!

---

