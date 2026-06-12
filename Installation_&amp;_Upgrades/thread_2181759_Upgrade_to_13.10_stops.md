---
title: "Upgrade to 13.10 stops"
date: 2013-10-18
forum: Installation &amp; Upgrades
---

### Post by shochatd on 2013-10-18
After upgrading my old rcubed 32-bit machine to 13.10 without incident, I initiated the upgrade on my System76 Lemur Ultra (64-bit). Everything seemed to be going normally, but during the "Installing the upgrades" phase, it seems to have stopped after "Installed cups-common". It has been sitting like that for an hour. The system appears to be fully functional otherwise (mouse, indicator menus, Unity launcher, and bash in a terminal). I ran top, but do not see anything obviously in trouble. Any suggestions on how to diagnose what is (or isn't) going on? Is there any way to restart things?

---

### Post by jdier on 2013-10-21
Had same problem.   I downloaded the ISO image, burned a bootable DVD and went through the install and am now reinstalling apps...   All my home directory stuff was still there.

---

### Post by shochatd on 2013-10-21
Well, I'm glad to hear I wasn't the only one. I did the same as you except I used a bootable USB made from the ISO. I was pleasantly surprised to see that there was a "re-install" option. I thought I would lose all my data. During the re-install process, it said it had encountered errors trying to re-install packages that I had before, and that I may have to re-install some manually. This turned out to be true. I had to re-install yasm, numerous -dev packages, imagemagick and Google Chrome. But again, I thought I'd have a lot more to do than that. Odd that this failure would have occurred now. I have been using Ubuntu since Dapper Drake and have never encountered anything like this before.

---

