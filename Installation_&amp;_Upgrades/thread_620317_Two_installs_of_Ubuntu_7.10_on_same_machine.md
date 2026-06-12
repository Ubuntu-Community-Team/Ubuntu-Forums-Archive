---
title: "Two installs of Ubuntu 7.10 on same machine"
date: 2007-11-22
forum: Installation &amp; Upgrades
---

### Post by kansas_plainsman on 2007-11-22
Well, I had installed KUbuntu 7.10 on a friend's PC, but he was having problems with the Intel 810 video chip-set on the motherboard (video artifacts from sharing RAM) so I wrangled another box with a separate Nvidia board and it came with a better hard drive.

Thinking that I would install his original hard drive as a slave on the first IDE channel, in order to preserve his data, I did so.  Then I installed Ubuntu 7.10 on the better hard drive.

During the install, Ubuntu saw the other hard drive and asked if it could import certain things from it - I said YES - just what I wanted.

To my surprise, once the install was done and I had rebooted, I see that the boot manager is able to give me various boot options, including booting from the original drive (/dev/sdb1).

Great!

But there's a catch - while I can *see* that there is the other drive, the GUI file manager can not mount and access the other drive.  It's as though Ubuntu is having to isolate the other drive to get a clean boot and/or run environment.

I am considering re-formating the better drive and mounting it as a data drive - but I'm unclear about implications.  Several questions: how do I edit the configuration of the boot system?  How do I deal with the 'locked away' nature of the 'other' drive.

Being an old slackware guy, I'm reasonably comfortable at the command line - but I need to understand the location and nature of the various configuration files before I go changing things.  I certainly don't want to take my friend's system down for any length of time.  Things are working well right now, as it is.

---

