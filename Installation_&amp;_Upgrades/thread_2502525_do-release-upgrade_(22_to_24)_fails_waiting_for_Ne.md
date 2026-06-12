---
title: "do-release-upgrade (22 to 24) fails waiting for NetworkManager"
date: 2024-11-18
forum: Installation &amp; Upgrades
---

### Post by rptb12 on 2024-11-18
After about two hours and many stages of merging config files, do-release-upgrade gets to setting up packages, but fails with:

```

  Setting up network-manager (1.46.0-1ubuntu2) ...
  SKIP: NetworkManager is not ready ...
  SKIP: NetworkManager is not ready ...
  SKIP: NetworkManager is not ready ...
  SKIP: NetworkManager is not ready ...

```

I waited about 10 minutes, tried systemctl restart NetworkManager (from another window) and eventually killed the dpkg process that was stuck.  That caused the whole upgrade to complain, and then get stuck again.  Repeatedly killing it got me to the point of:

```

The upgrade has completed but there were errors during the upgrade 
process. 

```

So I rebooted in case that would clear the problem, but dpkg --configure -a after reboot still got stuck in the same way.  In addition, I had crashing applications, and the crash report window was sometimes only a grey rectangle without any buttons.

Pretty bad.

Thank goodness for ZFS rollback, which took me all the way back to before I started.

I have two questions:

1. Any idea what this NetworkManager problem is?

2. Is there some way to see all the stages that do-release-upgrade is attempting and do them manually, in stages?  It's an enormous and complex *and opaque* process that can fail at every stage and break your system.  Every release of Ubuntu gets bigger and it becomes more and more infeasible to make it work.  Where do I look to find all the work it's doing, especially for this 22 to 24 upgrade, which I read has a lot of package renaming.

It'll be a nightmare if I have to reinstall, but maybe less of a nightmare than hours watching a script slowly take apart my system, break it, then say "oops, sorry".

---

### Post by rptb12 on 2024-11-18
In particular, is there a reason that following steps adapted to Ubuntu from [https://wiki.debian.org/DebianUpgrade](https://wiki.debian.org/DebianUpgrade) will fail for this particular upgrade from Ubuntu 22 to 24?

And is there a reason I can't do it in a chroot from a live ISO (with appropriate mounts)?  Then at least nothing that is being upgraded is running at the time.

---

