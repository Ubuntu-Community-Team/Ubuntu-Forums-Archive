---
title: "Automatic Updates, need setup assistance"
date: 2012-03-13
forum: Installation &amp; Upgrades
---

### Post by theoneness on 2012-03-13
Hi, I've posted a similar thread under the newbies forum, but it's not getting many views, possibly because it's the wrong forum. [http://ubuntuforums.org/showthread.php?t=1940284](http://ubuntuforums.org/showthread.php?t=1940284) it is about enabling automatic upgrades.

I'm a newbie installing 11.04 server on a little machine my small office would like to use as a LAMP staging server for web development.

My problem is that in the Ubuntu Server Guide documentation, where is says to enable automatic upgrades (after configuring with in 50unattended-upgrades) it says to create "/etc/apt/apt.conf.d/10periodic", but it also says "read /etc/cron.daily/apt for more information", and in /etc/cron.daily/apt it says i should create "/etc/apt/apt.conf.d/02periodic" to enable automatic updates.

Do I create /etc/apt/apt.conf.d/10periodic as per the Ubuntu Server Guide, or /etc/apt/apt.conf.d/02periodic as per the /etc/cron.daily/apt script notes?

Kind thank yous, and apologies if i've committed an infraction by posting similar threads to two forums.

reference: [https://help.ubuntu.com/11.04/serverguide/C/automatic-updates.html](https://help.ubuntu.com/11.04/serverguide/C/automatic-updates.html)

---

### Post by 2F4U on 2012-03-13
If I were you, I would follow the Server guide, which is consistent with the 10.04 version and the community documentation

[https://help.ubuntu.com/community/AutomaticSecurityUpdates](https://help.ubuntu.com/community/AutomaticSecurityUpdates)

In my experience, script headers are often outdated.

---

### Post by theoneness on 2012-03-13
> **2F4U said:**
> In my experience, script headers are often outdated.

Appreciate your weighing in on this. I will err to community docs over script headers as a general rule from now on :) cheers

---

