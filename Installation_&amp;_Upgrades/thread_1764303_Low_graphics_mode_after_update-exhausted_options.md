---
title: "Low graphics mode after update-exhausted options"
date: 2011-05-21
forum: Installation &amp; Upgrades
---

### Post by _Smiler_ on 2011-05-21
Hi there,

I'd appreciate help with this. I was running Natty on a Dell Studio 1558 with an ATI Radeon 5740. I'm aware there are threads with the same or similar problem, but I've tried all solutions suggested with no luck. After updating and restarting I hit "low graphics mode" which give me some options like enter mode just once, restart X, etc. The only option that works is to work in the console. I've tried to upload log files but they are too large. I can copy&paste here but would the length annoy moderators?

Anyway, I tried editing the xorg file to incluse vesa as the driver but it said I only had default for everything - didn't know what the meant and don't know what my laptop screen would be known as. I didn't see anywhere to enter "vesa" so I left it. I tried copying the contents of xorg.conf.failsafe file to just xorg.conf but that made no difference. I also tried installing ATI proprietary drivers but it wouldn't work - I can't remember the error but when I googled it, a reply to a similar problem suggested that my card wasn't supported. I did this because I thought the open source drivers may have been the problem. Now when I look at the /var/log folder there are no xorg.conf. files, failsafe or not, just a xorg.0.log file and a xorg.failsafe.log file with non of the information the last files did. 

I am now reinstalling Natty but when I run update manager I'll run into the same problem. Thanks for any replies and sorry for my awful memory - I've tried to be as detailed as possible but I'm not a linux-head and have a flimsy grasp on the concept of how everything works. Learning though!

UPDATE: When the OS was reinstalled, I noticed that fglrx is the proprietary driver. So I must have messed up when trying to install it from the command line. I can't remember whether I installed it on the last installation because I was having freezing problems - fixed by fixing pm-utils at v1.30.

Here are the logs uploaded on ubuntuone:
[My commands history, I think. I couldn't find any info on how to get a log of terminal activity. Console.app was mentioned but couldn't find it in natty so this might be the same thing.]("http://ubuntuone.com/p/ukj/")
[boot.log]("http://ubuntuone.com/p/ukm/")
[dmesg.txt]("http://ubuntuone.com/p/ukn/")
[dpkg.log]("http://ubuntuone.com/p/uko/")
[jockey.log]("http://ubuntuone.com/p/ukt/")
[kern.log]("http://ubuntuone.com/p/ukv/")
[syslog]("http://ubuntuone.com/p/ukw/")
[Xorg.0.log]("http://ubuntuone.com/p/ukx/")
[Xorg.failsafe.log]("http://ubuntuone.com/p/ul7")

Okay, I've added every log I thought could relate to anything and hopefully someone can glean some info! Thanks so much.

---

