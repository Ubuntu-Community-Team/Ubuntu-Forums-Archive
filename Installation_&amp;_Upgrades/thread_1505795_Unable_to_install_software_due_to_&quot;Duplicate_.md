---
title: "Unable to install software due to &quot;Duplicate Source lists&quot;"
date: 2010-06-09
forum: Installation &amp; Upgrades
---

### Post by Woody_Paranoia on 2010-06-09
Hi, I've had Ubuntu a while but I'm no expert. So go easy please.

Basically. I upgraded to 10.04 a while back, probably within a few days of it coming out. I have had no problems with it until just the other day. Now I don't install software much on the system. But I have recently tried to install software and all seems fine up until the end. I get an error message that reads as follows:

> W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_binary-i386_Packages)

Now this has never come up before, but it seems to have come up since a recent system update, which I can't actually do either I may add. Both installing software and updating the system comes up with the same error shown above.

I have googled the problem and looked into it, but I can't seem to find a solution. As far as I am aware there is no thread similar to this, I also hope this is in the right section. 

Help please, like I said I'm quite new so go easy please :D

Sam.

---

### Post by aysiu on 2010-06-09
The easy way to do this is go to System > Administration > Software Sources, click on the second tab, and then uncheck or untick the box next to the Partner repository.

If that doesn't work, I (or someone else) can walk you through the process of looking directly at the /etc/apt/sources.list file and deleting the offending entry.

---

