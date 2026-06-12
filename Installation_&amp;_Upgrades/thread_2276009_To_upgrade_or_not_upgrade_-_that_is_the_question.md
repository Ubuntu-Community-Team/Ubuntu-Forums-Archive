---
title: "To upgrade or not upgrade - that is the question"
date: 2015-04-29
forum: Installation &amp; Upgrades
---

### Post by zkab on 2015-04-29
I am a little bit confused about upgrades and LTS.
Right now I have 15.04 installed but what happens when 15.10 is out and 15.04 is no more supported - can I upgrade 15.04 -> 15.10 without a reinstall ... ?
And when 16.04 LTS is out and 15.10 is not supported ... can I upgrade 15.10 -> 16.04 LTS without reinstall ?
Not sure how to decide which way to go when new releases are popping-up.
Wish to take advantages of the new future releases and have no trouble when upgrading.
Appreciate recommendations ...

---

### Post by Bashing-om on 2015-04-29
zkab; Hello;

Real short answers:
> 
can I upgrade 15.04 -> 15.10 without a reinstall ... ?

Yes

> 
can I upgrade 15.10 -> 16.04 LTS without reinstall ?

Yes

It is all in the update-manager process. 
Food for thought, open a terminal and run:
```

cat /etc/update-manager/release-upgrades

```

[INDENT][INDENT]'buntu takes care of it's own
[/INDENT][/INDENT]

---

### Post by grahammechanical on 2015-04-29
Because you have installed 15.04 which only has 9 months support you have no choice but to upgrade to 15.10 and then 16.04 to get to an LTS (5 year support) release. 

Some of us recommend backing up our data and doing a fresh install. That is a personal preference. I think that before upgrading we should revert the user interface back to default and change the video driver to the open source video driver to avoid the problems that some people seem to have.

Regards.

---

### Post by craig10x on 2015-04-29
Also, uncheck any ppas you have installed in the software sources and re-check after upgrade is finished and you boot into the new version...Upgrading using the update manager works well if you do the things already suggested, but still a good idea to back up any important data on an external drive (even a usb flash drive is fine) just in case...nothing wrong with upgrading into each new version....that way you have the newest features and apps and full support until the next version arrives...

---

### Post by zkab on 2015-04-30
Thanks for the information- most valuable to me.
Ubuntu is pure magic ... getting more and more impressed by this software :cool:

---

