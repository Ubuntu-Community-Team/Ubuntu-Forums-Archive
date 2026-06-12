---
title: "microcode post install synaptic"
date: 2008-03-21
forum: Installation &amp; Upgrades
---

### Post by ear9mrn on 2008-03-21
Ubuntu 7.1

When I apply updates or add/remove packages using synaptic i get the following error.

[IMG]http://www.nevill.uk.net/bblog/Pictures/ZZ_Misc/error.png[/IMG]

Everything appears to install ok. Is this a problem ? if so, how do I fix it ?


Thanks,

Pete.

---

### Post by bapoumba on 2008-03-23
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/microcode.ctl/+bug/123145](https://bugs.launchpad.net/ubuntu/+source/microcode.ctl/+bug/123145) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				There is a bug report
Which version of microcode?
Please see [here too]("http://www.mail-archive.com/debian-bugs-rc@lists.debian.org/msg105955.html").

---

### Post by ear9mrn on 2008-03-23
SOLVED..............

Just did the following and problem has gone away.

sudo modprobe microcode
sudo apt-get -f install

Hope this helps others.

Pete.

---

