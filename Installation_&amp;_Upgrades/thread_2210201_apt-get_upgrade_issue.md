---
title: "apt-get upgrade issue"
date: 2014-03-09
forum: Installation &amp; Upgrades
---

### Post by mpmckinnon on 2014-03-09
E: Some index files failed to download. They have been ignored, or old ones used instead.
W: Not using locking for read only lock file /var/lib/dpkg/lock
root@ubuntu-phablet:/# sudo apt-get upgrade
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.

I am having this issue when I run sudo apt-get upgrade can someone help please.

---

### Post by Bashing-om on 2014-03-09
mpmckinnon; Hi !

Let's see if we can get to the bootom of this, as to why/what has a lock on the package management system.
Insure that all instances of package management are closed out ( synaptic, Ubuntu Software Center, apt, dpkg, ect ect) as only one instance may be active at any given time.

Now let's look at the status: post back the out puts of terminal commands:
```

ls -la /var/lib/dpkg/lock
sudo lsof /var/lib/dpkg/lock

```
Depening on the situation, we will then try and remove the lock.

[INDENT][INDENT]there is cause and
[INDENT][INDENT]effect
[/INDENT][/INDENT][/INDENT][/INDENT]

---

