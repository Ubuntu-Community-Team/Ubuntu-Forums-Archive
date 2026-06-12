---
title: "held back kernel updates"
date: 2012-10-09
forum: Installation &amp; Upgrades
---

### Post by reach on 2012-10-09
Hi there!
this is about Ubuntu Server 12.04 LTS

Whenever I log in the system is telling me that there are 6 updates pending, 6 of them being security updates.

I'm doing apt-get update followed by apt-get upgrade and then it tells me it held back:
linux-headers-server linux-image-server linux-server

So, apparently these are kernel updates and I know I have to do a dist upgrade to get rid of this.

But I went for 12.04 because of the LTS, and doing a dist upgrade would move away from that, wouldn't it?. So my questions are:
- is there a way to "hide" these update informations? I'm a bit monkish and they are driving me crazy
- is it even wise for me to insist on the LTS version, or should I just install whatever is new? I'm not using fancy stuff, just Apache (no PHP, SQL), Samba, Squid. To my understanding LTS is only if I don't want kernel updates because they could make other software incomapatible or cause update hassle. Don't think this is relevant for the mentioned modules, is it?

Thx!
Reach

---

### Post by nothingspecial on 2012-10-09
dist-upgrade does not upgrade you to a new version of Ubuntu, it installs new packages rather than update existing ones.

---

### Post by snowpine on 2012-10-09
I never use "apt-get upgrade" by itself; I always use "apt-get dist-upgrade" personally. (Assuming you *want* kernel updates of course.)

I think that sticking with the LTS for your server is a great choice. :)

---

### Post by reach on 2012-10-09
Thx a lot guys! Didn't know that a dist-upgrade leave me in the same version. That's the major point for me, thanks!

---

### Post by KegHead on 2012-10-09
Hi!

sudo aptitude install linux-image -f

It's always worked for me.

(you may have to install aptitude in terminal)


sudo apt-get install aptitude

KegHead

---

