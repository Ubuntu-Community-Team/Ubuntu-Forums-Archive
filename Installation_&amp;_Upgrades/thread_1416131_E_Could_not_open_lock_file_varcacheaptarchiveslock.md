---
title: "E: Could not open lock file /var/cache/apt/archives/lock"
date: 2010-02-25
forum: Installation &amp; Upgrades
---

### Post by distorted on 2010-02-25
Hey all,

I'm a newbie and my problem is the terminal:
[I]
[SIZE=2]*E*: *Could not open lock file* /*var*/*lib/*dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/*var*/*lib/*dpkg/) , are you root?[/SIZE][/I][SIZE=2]
[/SIZE]
[SIZE=1]Thanks, in advance.[/SIZE]

---

### Post by howefield on 2010-02-25
You have another package manager running, whether that be apt-get, Software Center, Update Manager, Synaptic Package Manager, Adept Package Manager, ect ect.

You can only have one package manager running at a time.

Try closing all package managers or if that doesn't work, reboot and try again. ?

---

### Post by distorted on 2010-02-25
Thanks for the help.

---

