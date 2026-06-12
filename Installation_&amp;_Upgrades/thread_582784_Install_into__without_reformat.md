---
title: "Install into / without reformat"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by dacha on 2007-10-20
My / filesystem is XFS, and I want to delete everything except /home and install into there without reformatting. 

However I get the following error:

+--------------------------------------------------------------------+
| System partition not formatted                                          |
+----------------------------------------------------------------- --+
| The file system on /dev/hda2 assigned to / has not          |
| been marked for formatting. File systems used by the      |
| system (/, /boot, /usr, /var) must be reformatted for       |
| use by this installer. Other file systems (/home, /media*, |
| /usr/local, etc.) may be used without reformatting.          |
+--------------------------------------------------------------------+

Is there some workaround to get what I want, like replacing mkfs.xfs with /bin/true and telling it to format? And where is the program that gives this message, grepping around didn't find anything?

I don't have Internet access at home so I can't upgrade to 7.10 except through a complete reinstall (besides, I really prefer clean reinstalls).

---

### Post by Arenlor on 2007-10-20
let it format everything except for /home, it says that / /boot /usr and /var MUST be reformatted.

---

### Post by dacha on 2007-10-20
> **Arenlor said:**
> let it format everything except for /home, it says that / /boot /usr and /var MUST be reformatted.

Sadly /home is on the same partition as / :-).

---

### Post by Arenlor on 2007-10-20
> **dacha said:**
> Sadly /home is on the same partition as / :-).
Well then you can't do it. Why don't you want to reformat?

---

### Post by dacha on 2007-10-20
> **Arenlor said:**
> Why don't you want to reformat?

My /home is > 30 GB and even if I had enough free space on another partition (which I don't), copy + reformat + copy back would take > 4 hours (tried it for Feisty, and won't ever again).

Dapper supported this, that's how I changed from Gentoo to Ubuntu in the first place.

> **Arenlor said:**
> Well then you can't do it.

My motto as a programmer, is "when there isn't a way, make one" :-).

Now which program gives that stupid error?

---

### Post by Arenlor on 2007-10-20
I'm not sure, but it seems to be the main installer, have you tried using gparted to make your partitions to begin with?

---

### Post by dacha on 2007-10-20
Looks like there is a way:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/72897](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/72897)

I think I should try it on a virtual machine first though.

---

