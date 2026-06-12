---
title: "Installing Debian Unstable package in Ubuntu"
date: 2011-02-20
forum: Installation &amp; Upgrades
---

### Post by bkpsusmitaa on 2011-02-20
How can I install a particular unstable package of Debian in Ubuntu. The issue seems to be of authentication keys.
[ATTACH]183970[/ATTACH]
I have installed Ubuntu in order to test and install my Umax Astra 4100 scanner, and I did not want to use the Unstable sid flavour of Debian. I have stable Lenny and it works fine.
Regards

---

### Post by zvacet on 2011-02-21
You can add repo for that package you need,but it is not recommended to mix repos.

---

### Post by cascade9 on 2011-02-21
Thats right zvacet, but sometimes its not so bad. 

You do know that squeeze is now stable? Its possible that squeeze would have the driver you want, maybe you should dist-upgrade, or do  a fresh install of squeeze.  

If you dotn want to dist-upgrade, or install stable squeeze, then AFAIK you should edit /etc/apt/sources.list, put a new sid repo under the stable repos, apt-get update, apt-get install *package name*, check its working, go back to /etc/apt/sources.list and remove the sid repo.

---

### Post by bkpsusmitaa on 2011-02-21
Dear friends,
I am sorry I could not explain myself properly. The scanner is not listed. A programmer tried to make a custom driver for me. The entire issue is in the following Debian Forum: [http://forums.debian.net/viewtopic.php?f=7&t=46057#p298362](http://forums.debian.net/viewtopic.php?f=7&t=46057#p298362)
Since Lenny is backdated, I needed to upgrade to the latest package. Debian Sid is not available as BitTorrent. So I had to upgrade via Ubuntu.
The next thing is that I have to import the authentication keys for using Debian Sid repository. I know how to put the apt line, but how to import the authentication keys. See the screenshot in my earlier post.
Hope I have been able to explain myself
Regards,
bkpsusmitaa

---

