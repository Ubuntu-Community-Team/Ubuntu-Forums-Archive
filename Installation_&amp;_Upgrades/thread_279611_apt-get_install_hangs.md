---
title: "apt-get install hangs"
date: 2006-10-18
forum: Installation &amp; Upgrades
---

### Post by samm on 2006-10-18
When I tried to install flash this morning, apt-get appears hung:

```

root@joule:~# apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree... 50%

```

It has been like this for close to 20 minutes, is there a log file somewhere I can check to see if it's actually doing something?

edit: I should clarify, when I run top I can see apt-get using around 95% of my CPU, so it is still running I'm just not sure what's taking so long.

---

### Post by taurus on 2006-10-18
Stop the process and try to run the update first...

```

aptitude update
aptitude install flashplugin-nonfree

```
p.s.  I hope you know what you are doing for logging directly in as root instead of using su...

---

### Post by samm on 2006-10-18
> **taurus said:**
> Stop the process and try to run the update first...

```

aptitude update
aptitude install flashplugin-nonfree

```
p.s.  I hope you know what you are doing for logging directly in as root instead of using su...


I ran apt-get update, then apt-get install flashplugin-nonfree and it worked, thanks.  I guess I already had it installed though, so now I have to figure out why flash does not seem to be working in firefox!

---

### Post by TheWizzard on 2006-10-18
> **samm said:**
> I ran apt-get update, then apt-get install flashplugin-nonfree and it worked, thanks.  I guess I already had it installed though, so now I have to figure out why flash does not seem to be working in firefox!

it's a common problem, but easy to fix. check the unofficial dapper guide or another howto.

---

