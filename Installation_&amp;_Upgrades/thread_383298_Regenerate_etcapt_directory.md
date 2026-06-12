---
title: "Regenerate /etc/apt directory"
date: 2007-03-13
forum: Installation &amp; Upgrades
---

### Post by Pionner on 2007-03-13
I think I have a "bizarre" apt problem in one of my production servers.

My machine has been running Ubuntu Dapper for the last 3 months, but yesterday it stops updating/upgrading. When I checked the config files I noticed that the /etc/apt directory is missing :confused: .
Manually adding Dapper's cdrom to the repository with
```
apt-cdrom add
```
and tipical apt commands like
```
apt-get -f install
```
didn't work. All complain about missing config files under /etc/apt.

I've searched some method to "regenerate" apt configuration files (mainly security keys and packages database) with no success.

Any idea?  Thanks in advance.

---

