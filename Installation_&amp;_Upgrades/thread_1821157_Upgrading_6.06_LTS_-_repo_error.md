---
title: "Upgrading 6.06 LTS - repo error"
date: 2011-08-08
forum: Installation &amp; Upgrades
---

### Post by notrobb on 2011-08-08
Trying to upgrade a server from 6.06 to 8.04 with no luck at all.

I think it's failing because it can't find [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main/debian-installer

That missing repo seems to automatically get added to /etc/apt/sources.list.d/prerequists-sources.dapper.list

I have do not have any backports enabled in /etc/apt/sources.list. I've tried commenting out the line in prerequists-sources.dapper.list and making the file read-only, but it still gets added when I try to upgrade.

Has anyone else run into this? 

Here is a copy of /etc/apt/sources.list and /etc/apt/sources.list.d/prerequists-sources.dapper.list -- 
[http://pastebin.com/vnsfvvdq](http://pastebin.com/vnsfvvdq)

---

### Post by Hakunka-Matata on 2011-08-08
[https://answers.launchpad.net/ubuntu/+source/update-manager/+question/166342](https://answers.launchpad.net/ubuntu/+source/update-manager/+question/166342)

---

### Post by mörgæs on 2011-08-08
I would not recommend upgrading an unsupported version to another (partly) unsupported one.

Better to try 10.10 or 11.04 in a live boot and doing a fresh install after that.

---

