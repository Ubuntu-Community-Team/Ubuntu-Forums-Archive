---
title: "Jaunty Alpha 3 released"
date: 2009-01-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by nhandler on 2009-01-16
[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-January/000524.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-January/000524.html)

> Hello Ubuntu developers,

Welcome to Jaunty Jackalope Alpha-3, which will in time become Ubuntu 9.04.

Pre-releases of Jaunty are *not* encouraged for anyone needing a stable
system or anyone who is not comfortable running into occasional, even
frequent breakage.  They are, however, recommended for Ubuntu developers and
those who want to help in testing, reporting, and fixing bugs.

Alpha 3 is the second in a series of milestone CD images that will be
released throughout the Jaunty development cycle.  The Alpha images are
known to be reasonably free of showstopper CD build or installer bugs, while
representing a very recent snapshot of Jaunty. You can download it here:

  [http://cdimage.ubuntu.com/releases/jaunty/alpha-3/](http://cdimage.ubuntu.com/releases/jaunty/alpha-3/) (Ubuntu)
  [http://cdimage.ubuntu.com/edubuntu/releases/jaunty/alpha-3/](http://cdimage.ubuntu.com/edubuntu/releases/jaunty/alpha-3/) (Ubuntu Education Edition)
  [http://cdimage.ubuntu.com/kubuntu/releases/jaunty/alpha-3/](http://cdimage.ubuntu.com/kubuntu/releases/jaunty/alpha-3/) (Kubuntu)
  [http://cdimage.ubuntu.com/xubuntu/releases/jaunty/alpha-3/](http://cdimage.ubuntu.com/xubuntu/releases/jaunty/alpha-3/) (Xubuntu)
  [http://cdimage.ubuntu.com/ubuntustudio/releases/jaunty/alpha-3/](http://cdimage.ubuntu.com/ubuntustudio/releases/jaunty/alpha-3/) (UbuntuStudio) 
  [http://cdimage.ubuntu.com/mythbuntu/releases/jaunty/alpha-3/](http://cdimage.ubuntu.com/mythbuntu/releases/jaunty/alpha-3/) (Mythbuntu) 

See [http://wiki.ubuntu.com/Mirrors](http://wiki.ubuntu.com/Mirrors) for a list of mirrors.

Alpha 3 includes a number of software updates that are ready for large-scale
testing.  Please refer to [http://www.ubuntu.com/testing/jaunty/alpha3](http://www.ubuntu.com/testing/jaunty/alpha3) for
information on changes in Ubuntu.

This is quite an early set of images, so you should expect some bugs.  For a
list of known bugs (that you don't need to report if you encounter), please
see:

  [http://www.ubuntu.com/testing/jaunty/alpha3](http://www.ubuntu.com/testing/jaunty/alpha3)

If you're interested in following the changes as we further develop
Jaunty, have a look at the jaunty-changes mailing list:

  [http://lists.ubuntu.com/mailman/listinfo/jaunty-changes](http://lists.ubuntu.com/mailman/listinfo/jaunty-changes)

We also suggest that you subscribe to the ubuntu-devel-announce list
if you're interested in following Ubuntu development. This is a
low-traffic list (a few posts a week) carrying announcements of
approved specifications, policy changes, alpha releases, and other
interesting events.

  [http://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce](http://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce)

Bug reports should go to the Ubuntu bug tracker:

  [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

Enjoy,
-- 
Steve Langasek
On behalf of the Ubuntu release team



---

### Post by vishalrao on 2009-01-17
OMG It boots like a rocket!

My previous Jaunty EXT3 install updated from 8.10 took about 40 sec to boot to login screen on my tablet PC. A fresh reformat and install of Alpha 3 with EXT4 now boots in about 30 sec which is a 25% improvement - impressive!

Even more so on my desktop which boots in about 20 sec :D

---

### Post by vishalrao on 2009-01-17
Couple of bootcharts from my desktop and tablet PC :D

[[img]http://www.imgx.org/thumbs/small/29488_o6a8b/jaunty-20090117-4.png[/img]](http://www.imgx.org/view/full/29488_o6a8b)          [[img]http://www.imgx.org/thumbs/small/29487_3uggy/jaunty-20090117-1.png[/img]](http://www.imgx.org/view/full/29487_3uggy)

The times are actually 15 sec and 24 sec if you see the actual chart and not 30 sec, some issue with the bootchart "time:" field?

---

### Post by scradock on 2009-01-17
That's nice - but today's updates have the same effect:

64-bit AMD laptop:    before updates 38 sec from Grub menu to login;
                      after updates 28 sec from Grub menu to login.

No reformat, no ext4, no alpha3 CD..........

---

### Post by SlowJet on 2009-01-17
Very nice release.
Installed on Pent III 800 with a 120GB disk, 1GB PC133 mem.
Not one bug and extra popup, crash, hang up.

Using ext4 on / and /home (where is my LVM???)

Connected to Windows share, windows shared printer, OO0 3 working good, Fx ok. It has been running all night without a burp. :KS

Bring on the updates. :guitar:

Until then, :popcorn:

SJ

---

### Post by Mazza558 on 2009-01-17
I'm impressed too, no issues here except the User Switcher crashing. Looking good for Jaunty! 

However, boot speeds aren't that much faster than they were - at the moment around 40 seconds, as opposed to about 45 before.

---

### Post by lexe-cc on 2009-01-17
Just curious, any signs of DRI2 yet? Or have i missed something :)

---

### Post by vishalrao on 2009-01-18
> **scradock said:**
> That's nice - but today's updates have the same effect:

64-bit AMD laptop:    before updates 38 sec from Grub menu to login;
                      after updates 28 sec from Grub menu to login.

No reformat, no ext4, no alpha3 CD..........

nice. and here i was thinking EXT4 was the main reason for the speedup :) i was on jaunty via updates too but didnt notice bootup speed until i reinstalled... must have been leftover cruft from intrepid :)

---

### Post by dxxvi on 2009-01-18
I installed Jaunty on an Inspiron E1505 (64MB ATI X1300 graphic card) from a daily build which is only 2 days before alpha3 and have every package up-to-date. I want to make a dual monitor but running System | Preferences | Screen Resolution (which is gnone-display-properties) gives "Segmentation fault (core dumped)" even though I disable compiz.

Does anybody has any opinion about fixing it?

---

