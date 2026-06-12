---
title: "Too many updates makes everyone crazy!"
date: 2011-01-20
forum: Installation &amp; Upgrades
---

### Post by maatthc on 2011-01-20
Hi there,
I'm a developer with a LPI level 2 with 15 years experience with Linux. I know how that stuff works but an single update with 30-50Mb make everyone crazy..
How about thinking a way to make sort of a diff for packages updates? Updating only the changed lib or executable? Linux is going the same way of Windows to make updates, what is really annoying for some user that dont have a broadband connection every time. Sometimes I prefer to no update my system to wait for an idle time of my downloads to avoid any delay on my torrents or only because I dont have enough bandwidth to do so. 
I guess it is not my problem..

Regards,

Alexandre Andrade

---

### Post by hintss on 2011-01-20
well, theres a reason why I disabled the update notifier and started updating via the command line. However, you could just disable checking for new updates, then just check it manually when you decide to update it. also, wasn't this kinda the point of shared libraries?

---

### Post by akand074 on 2011-01-20
What's wrong with updates? In Ubuntu I've had my system on for 52 days straight updating every time I'm notified and the stability of the system hasn't decreased the slightest even when notified to restart after the update. That is nothing like Windows. But yeah, if you don't have broadband all the time or just plain prefer not to update the system as often then just don't.. set it to check less often or just check yourself whenever you prefer to get the updates.. not a big deal. Also, I don't think Ubuntu updates very often at all.. I think most of the time I only get notified every 3-4 days. In Windows I sometimes used to get notified for new updates, immediately after I finished installing the last set of new updates.

---

### Post by presence1960 on 2011-01-20
Linux is like everything else- no matter what is done someone will find a reason to complain.

---

### Post by amauk on 2011-01-20
AFAIK, Delta Debs would only work in certain use-cases

Imagine in the repos of Ubuntu-A, there's an app, foo-2.1
Then foo-2.2 comes out, and someone puts it in a PPA
Then Ubuntu-B comes out with foo-2.3

1. Stock Ubuntu-A upgrading to Ubuntu-B
2.1 -> 2.3 = 1 delta update on upgrade
delta deb applied on upgrade

2. Using the PPA on Ubuntu-A, then upgrading to Ubuntu-B, results in
2.1 -> 2.2 -> 2.3 = 2 delta updates needed
But when you come to upgrade to Ubuntu-B, you'll end up trying to apply the 2.1 -> 2.3 delta to 2.2, which will fail

Using out-of-repo stuff (either PPA or source compiled) would choke upgrades

---

### Post by tommcd on 2011-01-21
> **maatthc said:**
> 
I'm a developer with a LPI level 2 with 15 years experience with Linux. ... Linux is going the same way of Windows to make updates, what is really annoying for some user that dont have a broadband connection every time. Sometimes I prefer to no update my system to wait for an idle time ...
Why don't you just use Slackware? With your level of experience you should be able to use Slackware as well as anybody. Slackware only gets security updates; and you can install the updates whenever you want to. 
I have no technical background at all; and I have been using Slackware for several years with no problems.

---

