---
title: "Currently on non-LTS, want to upgrade to 16.04"
date: 2016-04-23
forum: Installation &amp; Upgrades
---

### Post by KayeNg on 2016-04-23
My desktop is running Lubuntu 15.04. Is it possible to directly upgrade to the current LTS, which is 16.04?

How?

Thanks guys.

---

### Post by MikeCyber on 2016-04-23
I would wait some months as it's buggy. Wait for the announcement in package manager (set check for lts)

---

### Post by KayeNg on 2016-04-23
MikeCyber, thank you, but could you elaborate a bit? Are you talking about Synaptic Package Manager?

---

### Post by ajgreeny on 2016-04-23
You can not safely upgrade from 15.04 to 16.04 in one jump; you can only upgrade from one version to the next, ie 15.10 to 16.04 or from one LTS to the next, ie from 14.04 to 16.04.

From 15.04 you would have to go via 15.10; not worth the hassle in my opinion.

Backup your system and do a clean install would be my recommendation.  You should certainly do something as 15.04 no longer receives any updates of any kind, having lost support in January this year.

---

### Post by Topsiho on 2016-04-23
I support the advise of ajgreeny.

I think MikeCyber is indeed talking about Synaptic. 
In Settings>Packet sources (I am translating back from Dutch) there is a setting that you can set for getting a warning when a new LTS (first point release 16.04.1) release is out. I am not sure whether this is true for an intermediate release such as 15.04, you might see this for your self :)

Topsiho

---

### Post by vasa1 on 2016-04-23
*Software & Updates* offers something similar and I think such a notification will be generated when 16.04.1 is released sometime in August (?):

---

### Post by KayeNg on 2016-05-07
Thanks guys. So upgrading from 14.04 to 16.04 via terminal is possible, correct? Then how come when I type:

sudo do-release-upgrade

it says, "No new release found." ?

I've already selected "For long-term support versions" in Updates tab of "Software & Updates"

This is from my laptop which is currently running 14.04.

---

### Post by yancek on 2016-05-07
Have you done the steps suggested at the link below?

[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes)

---

### Post by Topsiho on 2016-05-07
As vasa1 said, the new release will be available for upgrade from 16.04.1, which will be due in a few months time. The present 16.04 version is not yet considered good enough for the upgrade from 14.04 to 16.04.
So please be patient for now, if you prefer a stable Ubuntu.
If not, you can always download Ubuntu and do a fresh install :)

Topsiho

---

