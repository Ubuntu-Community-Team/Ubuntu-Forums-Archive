---
title: "Kubuntu release upgrades vs NIS"
date: 2019-05-20
forum: Installation &amp; Upgrades
---

### Post by sasasasasasa on 2019-05-20
Recently a couple of NIS client upgrades (14->16 and 18->19) have gone wrong and I can't work out why.

Both are clients of a 16.04 ~NIS/NFS server the release upgrades appear to go well but once they reboot it appears that the NIS supported accounts are not accessible and it is impossible to log in.

There is no useful information in the NIS/NFS server logs.

I'm not sure where the problem lies or how to go about trying to fix it - we don't hold any local account information on these machines so it is a significant pain especially as we have a lot of clients to move to 19.04 at the moment from various older releases.

Any hints: where to start fixing this? any obvious gotchas that are missing on the client or server side? Any way to fix or avoid these problems?

We can fresh install but it would be much more convenient to upgrade.

---

### Post by mastablasta on 2019-05-20
well 14 can't upgrade to 16.: [https://wiki.kubuntu.org/XenialXerus/ReleaseNotes/Kubuntu](https://wiki.kubuntu.org/XenialXerus/ReleaseNotes/Kubuntu)

18--> 19 can't be directly upgraded, but has to first be upgraded to 18.10 and then to 19.04. 18.04 is LTS and the next LTS will be 20.04

---

### Post by sasasasasasa on 2019-05-20
Ok, I did do-release... on 14.xx and got 16.04 [not working] and 18.10 to 19.04 by the same route.

Now back to the question, how to fix NIS?

---

### Post by sasasasasasa on 2019-05-20
[https://bugs.launchpad.net/ubuntu/+source/rpcbind/+bug/1558196](https://bugs.launchpad.net/ubuntu/+source/rpcbind/+bug/1558196)

The solution for 16.04 not working is:

systemctl add-wants multi-user.target rpcbind.service

untested on 18->19 but the symptoms were very similar

---

