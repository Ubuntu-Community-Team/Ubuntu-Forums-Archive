---
title: "upgrade &quot;unresolvable problem&quot; redux"
date: 2022-12-17
forum: Installation &amp; Upgrades
---

### Post by fmouse on 2022-12-17
I've poked around on my system extensively, and in various forums, but can find nothing helpful. I'm running Ubuntu MATE 20.04.5 LTS and trying to upgrade to 22.04. When I run 'do-release-upgrade' I get the following after the "Updating repository information" list::

```
Checking package manager
Reading package lists... Done    
Building dependency tree          
Reading state information... Done

Calculating the changes

Calculating the changes

Could not calculate the upgrade 

An unresolvable problem occurred while calculating the upgrade. 

If none of this applies, then please report this bug using the 
command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal. If 
you want to investigate this yourself the log files in 
'/var/log/dist-upgrade' will contain details about the upgrade. 
Specifically, look at 'main.log' and 'apt.log'. 


Restoring original system state

Aborting
Reading package lists... Done    
Building dependency tree          
Reading state information... Done

```

There is no source given for the "unresolvable problem". 

/var/log/dist-upgrade/main/log contains:

```
ERROR Dist-upgrade failed: 'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'
DEBUG abort called
DEBUG openCache()
DEBUG Comparing 5.4.0-131 with
DEBUG Comparing 5.4.0-135 with 5.4.0-131
DEBUG /openCache(), new cache size 82822

```

There are no held packages that I can find.

/var/log/dist-upgrade/apt.log contains a lengthy list of broken packages, but running

```
apt-get --fix-broken install
```

finds no broken packages, and some of the packages listed as broken in apt.log aren't even installed. Many of them are -dev packages.

The desktop system seems to work just fine - I just can't upgrade it.

I did have a freeze-up on this system earlier (it's as VMware VM) and had to cold-conk the iMac host to get back to square one with the Ubuntu-MATE VM so there *may be* some correupted files. I have no idea where to go with this.

---

### Post by ian-weisser on 2022-12-17
Show us the complete output of "sudo apt update" and "sudo apt upgrade"

---

### Post by fmouse on 2022-12-17
> **ian-weisser said:**
> Show us the complete output of "sudo apt update" and "sudo apt upgrade"

# apt update
```
Hit:1 http://us.archive.ubuntu.com/ubuntu focal InRelease
Get:2 http://us.archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu focal-backports InRelease [108 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu focal-security InRelease [114 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu focal-updates/main i386 Packages [763 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages [2,270 kB]
Fetched 3,368 kB in 2s (2,197 kB/s)                        
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
```

# apt upgrade
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  courier-authdaemon courier-authlib-userdb courier-base libnet-cidr-perl
Use 'apt autoremove' to remove them.
#
# News about significant security updates, features and services will
# appear here to raise awareness and perhaps tease /r/Linux ;)
# Use 'pro config set apt_news=false' to hide this and future APT news.
#
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

I've removed the courier-mta packages before in trying to solve this problem. To the best of my knowledge, they're not part of the problem.

---

### Post by ian-weisser on 2022-12-18
Apt considers the four listed packages to be orphaned. Either autoremove them or explicitly apt-mark them as non-orphans.

The use of -backports is untested. If you installed anything using that repo, it might cause conflicts...but those are very rare.

A common source of hidden held packages is PPAs/Non-Ubuntu sources that were disabled. When the non-Ubuntu packages from those sources remained installed, they sometimes cause version conflicts.

Next, try an apt full-upgrade.

If that works without any error or complaint, try do-release-upgrade again.

If do-release-upgrade still aborts without useful output or log, then backup your data and clean-install 22.04.

---

### Post by fmouse on 2022-12-18
Well the problem wasn't the courier-mta packages. When I looked at /var/log/dist-upgrade/apt.log there were a great many dependency problems which didn't show up otherwise. I went through and resolved a number of these and the upgrade completed properly. A lot of these were on "-dev" (development) packages. I don't how I ended up with so many of these.

the dist-upgrade didn't go smoothly, though. I have *numerous* issues with my MATE desktop and am having to basically rebuild it from scratch. Now it's just a matter slogging through the process of rebuilding panels.

---

### Post by Tadaen_Sylvermane on 2022-12-18
While PPA's are helpful for many things they cause problems with upgrades if you don't handle them correctly. It's bit me more than once over the years because I just forget they are there. Now PPA's are my last resort. I even backport packages manually from a ppa's deb-src line following the typical debian instructions where possible rather than adding the ppa deb line into my sources.list. Bit of manual effort of course but haven't had a problem since.

---

