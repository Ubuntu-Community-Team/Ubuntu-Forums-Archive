---
title: "Several boot and installation problems"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by scorchgeek on 2010-10-12
I started installing the beta of Maverick a few days ago, but the update server was running inordinately slow, so I canceled it. Several times, I have attempted to continue the installation, but I've been unable to reach the server. 

Shortly after this happened, I could no longer boot normally--I get the error:
```
Kernel Panic - not syncing:VFS:Unable to mount root fs on unknown-block(0,0)
```

Choosing the previous kernel fixes the problem.

So, I obviously want to upgrade to the release version now. When I open the update manager, I get asked if I want to do a partial upgrade to complete the install. I'm a bit leery of doing this since I only have one previous kernel to go back to (my list got really long and I have another operating system entry underneath, so I set my automagic boot manager to only keep two), and if I can no longer boot after the upgrade, I'll have to use Windows until it gets fixed...

So, should I finish the upgrade, try to troubleshoot the error, or do something else to jump right to the latest release, after being partway through the upgrade?

---

### Post by mörgæs on 2010-10-12
This poor machine has been through a lot of trouble. Doesn't it deserve a clean install?

---

### Post by scorchgeek on 2010-10-12
Yeah, it's a good point. I have my home directory and /etc backed up, any other config files I should make sure I have backed up first? The only reason I don't want to do a clean install immediately is the amount of time I've spent on configuration and customization.

---

### Post by mörgæs on 2010-10-13
The more tweaking you have done with your system, the riskier the online upgrade is, unfortunately.

It is good also to back up xorg.conf, if you have such one.

---

