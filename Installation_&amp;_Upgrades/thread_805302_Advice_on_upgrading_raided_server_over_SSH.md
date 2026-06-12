---
title: "Advice on upgrading raided server over SSH"
date: 2008-05-23
forum: Installation &amp; Upgrades
---

### Post by SixedUp on 2008-05-23
I'm currently running 7.10 on my home server. I've been holding off from upgrading to 8.04LTS as this server provides a bunch of services that my family consider to be "in production", but I'd really like to upgrade.

This system runs headless, and is built on software raided disks. To administer it I SSH into it. No keyboard, no screen. Does anyone know of any "gotcha's" before I try running a release-upgrade over SSH ?

---

### Post by Riom on 2008-05-30
It should be possible.  A couple of weeks ago I upgraded my dedicated web server from 7.10 to 8.04 over ssh (and thousands of miles away).  During the process my live web site was running, and with the reboot etc the total down time was less than 5 minutes.  After, everything just worked.  But I was probably lucky!  (I had a backup server ready in case I did mess up).

When you do the install over ssh, the install sets up a second ssh for you on a different port in case you get problems.  I didn't need that.

Having said that, you might get hardware problems or compatibility problems, especially with multimedia stuff, so no guarantees!  But it worked for me.

---

### Post by SixedUp on 2008-08-16
I finally found some time to go ahead with this, and as Riom described, the basic upgrade worked flawlessly. 

I did have some problems with a couple of extra packages that I'd installed, simply because they had changed so much between Ubuntu releases that my "old" configurations for them were no longer valid. Total downtime on the major applications (mail, web server etc) was about 5 minutes during the reboot, and about another 30 minutes or so to "hand-crank" the few other things that I needed. All in all, impressively smooth.

---

