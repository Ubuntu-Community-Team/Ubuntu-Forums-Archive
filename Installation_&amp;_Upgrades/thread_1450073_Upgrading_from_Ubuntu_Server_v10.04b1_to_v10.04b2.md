---
title: "Upgrading from Ubuntu Server v10.04b1 to v10.04b2"
date: 2010-04-08
forum: Installation &amp; Upgrades
---

### Post by Resilldoux on 2010-04-08
Hi there,

Right, so I'm having a bit of a problem updating my server. I just got the news that the second beta of v10.04 released today, so I wanted to upgrade. The problem is, however, my server didn't get the news (so to speak, hehe). I went to this link: [http://www.ubuntu.com/testing/lucid/beta2](http://www.ubuntu.com/testing/lucid/beta2) and figured I should run this command:
```
sudo do-release-upgrade -d
```Now, when I run that command, my server can't find the new release.

```
resilldoux@svr-elysium:~$ sudo do-release-upgrade -d
Checking for a new ubuntu release
No new release found
```What am I doing wrong? Or am I just too impatient to upgrade because, maybe, it's not yet available through this command as the second beta was released only hours ago?

---

### Post by cariboo on 2010-04-08
If you already running Lucid server, there won't be an announcement about a newer version. If you are running an older version, I'd stick with what you are using now and update after the final release.

---

### Post by Resilldoux on 2010-04-08
Thanks for replying. Is this standard procedure for all Ubuntu Server development releases? I mean, once you installed, let's say, Ubuntu Server 9.10 Alpha 3, you can never update to the Beta 1 (for safety reasons I guess, which I can understand)?

---

