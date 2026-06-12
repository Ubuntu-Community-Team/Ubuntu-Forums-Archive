---
title: "multiple updates"
date: 2007-06-15
forum: Installation &amp; Upgrades
---

### Post by smokiedbest on 2007-06-15
i use a dial up connection for internet, it can sometimes be a pain cause of the slow speed, and i have ubuntu (dapper)on 2 system.
 
i was wondering if there is a way to like transfer updates from one system to the other without having to update from the net all over again

---

### Post by zvacet on 2007-06-15
[http://aptoncd.sourceforge.net/]("http://aptoncd.sourceforge.net/")

---

### Post by _duncan_ on 2007-06-15
> i was wondering if there is a way to like transfer updates from one system to the other without having to update from the net all over again

The folder /var/cache/apt/archives contains the .deb packages downloaded from the ubuntu repo during update / package installation.

It basically boils down to finding the most convenient way to transfer these files to the same folder of other unupdated installations, then going through the motion of updating the system. The update manager (synaptic, apt-get, aptitude or whatever you are using) will recognize the presence of these files and not download them anymore.

The easiest I suppose is to just share these files if both systems are networked. If not, maybe burning to writable CD/DVD, thumb drives, etc.

In my case, I always keep an updated copy of these files in a CD-RW disc as a backup in case I have to reinstall.

---

### Post by smokiedbest on 2007-06-16
thanx. both solutions would do fine

---

