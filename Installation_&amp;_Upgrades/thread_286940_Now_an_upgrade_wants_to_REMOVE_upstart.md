---
title: "Now an upgrade wants to REMOVE upstart"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by mlmurray on 2006-10-28
Okay, so after finally getting my Kubuntu Dapper upgraded to Edgy with some amount of trouble yesterday. I decided to check to see if any files had been updated in the interim so I did an update and upgrade through aptitude and this is what I got:

```
mark@mlmurray1:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages are unused and will be REMOVED:
  startup-tasks system-services tasksel tasksel-data
  ubuntu-standard upstart upstart-compat-sysv upstart-logd
  util-linux-locales
0 packages upgraded, 0 newly installed, 9 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 6128kB will be freed.
Do you want to continue? [Y/n/?] n
Abort.
```

I also executed a dist-upgrade and aptitude told me that "The following packages are unused and will be REMOVED:"

I kind of thought those packages were sort of important.  I suspect of I went through with this it would remove these packages, then another update/upgrade would want to go back to the old startup/service start-stop method.  I haven't changed anything with regard to packages since I did the upgrade from Dapper to Edgy.

Anyone have any thoughts on this?

---

### Post by mlmurray on 2006-10-28
I figured it out.  

After the upgrade my vi was not behaving as it did before and was basically pissing me off.  Apparently it overwrote my old, comfortable, vimrc.conf file so my solution, rather than trying to fix it, was to remove vim and install vile (which I always liked better, anyway).  Well, in the process of doing this, aptitude also removed ubuntu-minimal, which is dependant on those other 9 packages and is a dependancy of vim (I should have notice, but didn't).

Anyway, I re-installed ubuntu-minimal (which also re-installed vim but thankfully left file as the 'default' vi editor in /etc/alternatives) and the problem of aptitude wanting to remove those 9 "orphaned" (but terribly important) packages.

---

