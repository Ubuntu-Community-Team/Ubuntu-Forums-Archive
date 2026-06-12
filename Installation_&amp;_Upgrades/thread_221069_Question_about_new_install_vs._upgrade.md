---
title: "Question about new install vs. upgrade"
date: 2006-07-22
forum: Installation &amp; Upgrades
---

### Post by Soulstorm on 2006-07-22
I'm currently running Breezy (I think).  I noticed that there's a new version... Dapper Drake (DD).  Is there a way to upgrade to DD and keep my old settings or do I need to format and install DD from the ground up?

---

### Post by Ziox on 2006-07-22
you can do "gksu update-manager -d" to upgrade from breezy to dapper without reinstall

---

### Post by taurus on 2006-07-22
If you want to upgrade from Breezy to Dapper, first, edit /etc/apt/sources.list and replace breezy with dapper.  Then, update and upgrade...

```

sudo gedit /etc/apt/sources.list
sudo apt-get update
sudo apt-get upgrade

```

---

### Post by Soulstorm on 2006-07-22
Thanks... 

I did that and the update manager popped up with like 115 different things I could update, but I don't see Drake on the list.  Am I missing something obvious?

I'm doing the updates, hopefully one of those was Dapper

---

### Post by taurus on 2006-07-22
What do you mean you don't see any drake on the list?  If you replace breezy with dapper in /etc/apt/sources.list, then you are upgrading your machine to Dapper, period.

---

### Post by Ziox on 2006-07-22
> **Soulstorm said:**
> Thanks... 

I did that and the update manager popped up with like 115 different things I could update, but I don't see Drake on the list.  Am I missing something obvious?

I'm doing the updates, hopefully one of those was Dapper

I don't think you should see drake on there, if there is any indications of upgrade, then it should just be newer version numbers. (and maybe "dapper" but definately not "drake")

---

### Post by Soulstorm on 2006-07-22
I think my problem was when I was updating:

> 99% [Connecting to us.archive.ubuntu.com (146.137.96.15)]

  Could not connect to us.archive.ubuntu.com:80 (146.137.96.15), connection timed out

99% [Connecting to us.archive.ubuntu.com (146.137.96.7)]

  Could not connect to us.archive.ubuntu.com:80 (146.137.96.7), connection timed out

I'll try again in a bit, see if the connection is back up.

---

### Post by Ziox on 2006-07-22
i suggest edit the xorg.conf file and remove all the "us." things that is in front the websites url.

---

### Post by taurus on 2006-07-22
Looks like the us.archive.ubuntu.com is currently down...

---

