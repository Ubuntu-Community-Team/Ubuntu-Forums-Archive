---
title: "Adding Hardware + Loading Modules"
date: 2004-12-10
forum: Installation &amp; Upgrades
---

### Post by ayam on 2004-12-10
I have been using Slack 9.1 and 10 for about 10 months now so still a new at using Linux. One thing I know abotu Slack is that when you have want to add modules to support your hardware, then you just uncomment /etc/rc.d/modules

For example, I just installed a Adaptec 2920 SCSI card and all I haveto do was to uncomment the relevant line. 

How would you do the equivalent in Ubuntu. My fresh install detected the SCSI card and installed the relevant modules but what would I have done if I added the SCSI card after my Ubuntu installation? How would I have known which module was needed? Is there a hardware detection option? Should I boot off my Ubuntu Install CD and try to run the hardware detection part of the install again? Or does the hotplug option do something everytime I start up.

Unlike Slackware, there are no files to uncomment. And unlike a Video card you cant run xf86config or install your nvidia/ati drivers.

Yours curious

---

### Post by wallijonn on 2004-12-22
/etc/modules ?

---

