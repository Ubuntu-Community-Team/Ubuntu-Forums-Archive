---
title: "dpkg can't unpack package lvm2"
date: 2006-07-13
forum: Installation &amp; Upgrades
---

### Post by ToneDispenser on 2006-07-13
Hi there,

I did a debian sarge netinst and "migrated" to dapper like stated in
[this wiki entry]("https://wiki.ubuntu.com/WartyUpgradeNotes")...

I installed ubuntu-base, but can't install anything else right now,
because of a dependency problem.

Here's the error I get:
```
ubuntu-standard: Depends: lvm2 but it is not going to be installed
E: Unment dependencies. Try 'apt-get -f install' with no packages (or specify a solution)
```


When I run 'apt-get -f install':
```
Unpacking lvm2 (from .../lvm2_2.02.02-1ubuntu1_powerpc.deb) ...
dpkg: error processing /var/cache/apt/archives/lvm2_2.02.02-1ubuntu1_powerpc.deb (--unpack):
  subprocess pre-installation script returned error exit status 10
Errors were encountered when processing:
/var/cache/apt/archives/lvm2_2.02.02-1ubuntu1_powerpc.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I already tried clearing the cache and removing the file and running "apt-get install lvm2" again, but I end up getting the same error.

I get the same error when i 'dpkg --unpack lvm2_2.02.02-1ubuntu1_powerpc.deb'


any ideas on how to solve this?
If I could just get the error message from the pre-installation script, I could probably solve it myself.

Thanks for helping ;)

---

### Post by linear on 2006-07-13
Perhaps it's the same issue as [this thread]("http://www.ubuntuforums.org/showthread.php?t=178695")?

(Also reported as a bug [here]("https://launchpad.net/distros/ubuntu/+source/lvm2/+bug/47972/").)

---

### Post by ToneDispenser on 2006-07-14
Thnaks for the hint.
I'll have a look.

Looks like I didn't search thoroughly before posting :/

---

