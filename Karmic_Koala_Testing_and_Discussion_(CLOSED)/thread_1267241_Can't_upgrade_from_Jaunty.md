---
title: "Can't upgrade from Jaunty"
date: 2009-09-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Eestlane on 2009-09-15
While doing distribution upgrade via sudo update-manager -d, the update manager gave

> Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.

I had once tried to do it before, but cancelled the upgrade when it asked if I want to install the upgrades, so this might be the issue.

Also, I can't do normal upgrades anymore. Also sources are set to karmic by the upgrade-manager already.

I remember some command to fix it when the packages information were corrupt. What could it be?

I feel stupid.

EDIT: sudo apt-get dist-upgrade tells this:
> The following packages have unmet dependencies:
  sysv-rc: Breaks: initscripts (< 2.86.ds1-63) but 2.86.ds1-61ubuntu11 is to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

---

### Post by ranch hand on 2009-09-15
Just;
```

gksudo gedit /etc/apt/sources.list

```
and where ever you find the word " karmic" replace it with "jaunty".
Run;
```

sudo apt-get update

```
and you are good to go.

---

### Post by Eestlane on 2009-09-15
Thanks, I'll try that.

EDIT: The Distribution upgrade failed, but normal upgrade works. I'll see if I can make the dist-upgrade after the normal one.

---

### Post by Eestlane on 2009-09-15
Mhmm, the sudo update-manager -d still doesn't work.


EDIT: Okay, I'm trying aptitude safe-upgrade

---

### Post by jermyandhisbass on 2009-09-15
There are broken dependencies preventing a clean upgrade.  Best to try later after the repos have settled down.

---

### Post by Eestlane on 2009-09-15
Thanks for the reply.

I'll try anyways, though.

EDIT: Well I got it to work. Only got the problem with NetworkManager, but that was for everybody.

---

