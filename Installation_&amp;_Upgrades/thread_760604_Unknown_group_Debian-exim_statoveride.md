---
title: "Unknown group Debian-exim statoveride"
date: 2008-04-20
forum: Installation &amp; Upgrades
---

### Post by cmnorton on 2008-04-20
I suddenly cannot perform apt-get -y upgrade because of this error.

Need to get 0B/1692kB of archives.
After unpacking 0B of additional disk space will be used.
dpkg: syntax error: unknown group `Debian-exim' in statoverride file 
E: Sub-process /usr/bin/dpkg returned an error code (2)

Here is the content of the statoveride file.

root Debian-exim 0640 /etc/exim4/passwd.client
hplip root 755 /var/run/hplip

How do I resolve this?

---

### Post by cmnorton on 2008-04-20
I got around this problem the wrong way by

sudo groupadd Debian-exim

and then performing the upgrade.

I would still like to know how to fix this problem to get updates. In using Ubuntu for nearly a year now, I have never had the upgrades break, not once.

---

