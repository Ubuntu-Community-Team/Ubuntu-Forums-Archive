---
title: "Upgrade problem"
date: 2023-04-28
forum: Installation &amp; Upgrades
---

### Post by mtasilva on 2023-04-28
Hell, i have this problem :

[FONT=arial][SIZE=2]you might want to run 'apt --fix-broken install' to fix this.
The following packages have unsatisfied dependencies:
 apt-utils : Depends: apt (=2.4.8) but 2.4.9 is installed
E: Unsatisfied dependencies. Try 'apt --fix-broken install' without any packages (or specify a solution).
When try apt --fix-broken install i have this :
[/SIZE][/FONT]
[FONT=arial][SIZE=2]dpkg: error: parsing file '/var/lib/dpkg/status' near line 58410 package 'ri':
 name field 'Original-Maintainer>' has to be followed by a colon
E: Sub-process /usr/bin/dpkg returned an error code (2)
What can i do?[/SIZE][/FONT][FONT=arial][SIZE=2]
[/SIZE][/FONT]

---

### Post by Impavidus on 2023-04-28
I can't remember seeing that problem before.

Somehow, your dpkg status file got corrupted. That's the file where your package manager stores the current status of all (partially) installed packages. That could be a serious problem.

It keeps a backup of the old version, which isn't entirely correct, but should be close. Check some files:```

cd /var/lib/dpkg
ls -l status status-old
wc status status-old
head status status-old
tail -n30 status
tail -n30 status-old
head -n58425 status | tail -n31
```Just hoping anything interesting pops up. The final command should print 31 lines near the offending line in your status file.

---

