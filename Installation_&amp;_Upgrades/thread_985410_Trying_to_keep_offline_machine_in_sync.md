---
title: "Trying to keep offline machine in sync"
date: 2008-11-17
forum: Installation &amp; Upgrades
---

### Post by nemein on 2008-11-17
1st post so hopefully I'm not violating any norms of the forum here...  apologies if I am :oops:


We're running an experiment in which we have two machines running ubuntu server, one is on the I'net the other isn't, but I need to keep them synced wrt patches/security updates.  My thought was to run the apt process on the one that is connected, burn the updates to CD and upload them on the other one.  What I've been searching for, but not finding, is a simple script (either full automated script that I can run via cron to create the CD or a procedure checklist I can follow manually) that will help me w/ this.  Does anyone know of a such a thing?

I see there is [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/) but does that work on an ongoing basis like I'm trying to do?  What I mean is will it take into account the updates that have been previously loaded?  BTW nothing else will be going on on the I'net connected machine.  It is just there to d/l the updates for the other machine.

TIA

---

### Post by cariboo on 2008-11-17
WHat is the purpose of the experiment? You really don't have to do any updates, except for security updates. Server are designed for long uptimes. If a server isn't connect to the internet, there really isn't any need to update it, as it is almost as secure as a server that is turned off. :)

If the purpose is to see how much work it is to keep up to date, you're probably doing it the right way. To use a CD for updates use apton-cd (which is available in the repositorie) on the server connected to the internet. then use:

```
sudo aptitude update && aptitude safe-upgrade
```

after you have made sure the cdrom is available in /etc/apt/sources.list.

I always use aptitude safe-upgrade as that way there are no surprises if and when you reboot.

Jim

---

### Post by nemein on 2008-11-18
It's an internal/intranet/testbed sort of thing.  So it will be doing it's function as a server (DNS/mail/web) and overall I'm not too concerned about the security, but for various reasons I do want to keep the patches and apps up to date.  

I'll take a better look at apton-cd today.  If anyone has any other advice/options/hints/clues/suggestions I'd still love to hear them.

Thx

---

