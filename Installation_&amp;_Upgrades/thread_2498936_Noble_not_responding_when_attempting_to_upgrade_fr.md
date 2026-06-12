---
title: "Noble not responding when attempting to upgrade from 22.04 to 24.04"
date: 2024-07-04
forum: Installation &amp; Upgrades
---

### Post by pedroluiznogueira on 2024-07-04
Basically I am trying to upgrade with `sudo update-manager -d` and when the following is in progress:

```shell
authenticate 'noble.tar.gz' against 'noble.tar.gz.gpg' 
extracting 'noble.tar.gz'
```

it crashes saying the Noble is not responding and I am not able to procceed. Any ideas?

---

### Post by TheFu on 2024-07-04
Backup your data, settings, and do a fresh install.

Before starting any upgrade, be 100% certain you 
[LIST=1]
[*]sudo apt update
[*]sudo apt full-upgrade
[*]sudo shutdown -r now
[*]Backup anything you don't want to lose - sometimes things break, badly. If you don't have a backup or 20 of them, you'll be much more likely to need it.  OTOH, if you do have a backup, something about this seems to keep Murphy away. It is a law.
[*]sudo do-release-upgrade
[/LIST]

---

### Post by Dennis N on 2024-07-04
Don't use the -d option. It works with the **lastest** supported release (which is 24.04).

From the man page of do-release-upgrade:

> -d, --devel-release
              If using the latest supported release, upgrade to the development release


How to check for available upgrades from 22.04: 

```
dmn@Sydney-vm:~$ do-release-upgrade -c
Checking for a new Ubuntu release
New release '23.10' available.
Run 'do-release-upgrade' to upgrade to it.

```

So, the available upgrade is to 23.10 at this time:

What you can do at this time to get 24.04 now (other than a new installation) is first upgrade 22.04 to 23.10 and then upgrade again to 24.04. That works. Time is of the essence. 23.10 goes out of support on July 11. Do it before that date to be sure it works.

Later, there will be a one step upgrade 22.04 to 24.04, but it is not ready yet.

---

