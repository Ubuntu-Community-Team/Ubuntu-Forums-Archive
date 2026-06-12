---
title: "Dependencies - Conditional Dependencies"
date: 2021-03-07
forum: Installation &amp; Upgrades
---

### Post by Alan5127 on 2021-03-07
Hi All,

I understand that packages can have dependencies, and that, by default, 'apt install' will also install all the dependencies of the packages I ask it to install.

Where I *may* be confused is where the dependencies are conditional.

If am documenting a process, and a dependency is unconditional, I don't list them (seems redundant).  I have also been excluding conditional dependencies, but am I correct to do that?

For example, if I do:

```
# apt install libvirt-daemon-system
```

I expect it to also install:

libvirt-clients
libvirt-daemon

as both of those are listed as dependencies of libvirt-daemon-system:

```
# apt show libvirt-daemon-system

Package: libvirt-daemon-system
Version: 6.0.0-0ubuntu8.7
...
Depends: debconf (>= 0.5) | debconf-2.0, libc6 (>= 2.4), libgcc-s1 (>= 3.3.1), libglib2.0-0 (>= 2.12.0), libvirt0 (>= 6.0.0-0ubuntu8.7), libxml2 (>= 2.9.2+really2.9.1+dfsg1-0.2), adduser, gettext-base, libvirt-clients (= 6.0.0-0ubuntu8.7), libvirt-daemon (= 6.0.0-0ubuntu8.7), libvirt-daemon-system-systemd | libvirt-daemon-system-sysv, iptables (>= 1.8.1-1) | firewalld, logrotate, policykit-1
...

```


However, if I look closer, I see:

libvirt-clients (= 6.0.0-0ubuntu8.7)
libvirt-daemon (= 6.0.0-0ubuntu8.7)


So, does that mean that those two dependencies only get installed along with 'libvirt-daemon-system Version 6.0.0-0ubuntu8.7'?

In other words, if someone follows my notes in some months time, and the current version of libvirt-daemon-system at that time is now, say, Version 7, and if they also need to get libvirt-clients and libvirt-daemon, then would they need to install those manually?


I realise that the best option would be to include all required dependencies in my notes at all times, and I am going to do that going forwards, since 'why not', but do I need to be concerned regarding notes I have already made?


Hope that makes sense, but if not, please ask me to clarify.

Also, whilst I have used the packages in my example above (to hopefully make my question clear), my query is more general in nature.


Thanks,

Alan.

---

### Post by Impavidus on 2021-03-07
> **Alan5127 said:**
> 
However, if I look closer, I see:

libvirt-clients (= 6.0.0-0ubuntu8.7)
libvirt-daemon (= 6.0.0-0ubuntu8.7)


So, does that mean that those two dependencies only get installed along with 'libvirt-daemon-system Version 6.0.0-0ubuntu8.7'?


It means that when you install libvirt-deamon-system version 6.0.0-0ubuntu8.7, you have to install version 6.0.0-0ubuntu8.7 of those dependencies too. Which all happens automatically if you let apt handle this stuff. If some update later provides a later version of libvirt-deamon-system, it will probably depend on later versions of those dependencies, so they get upgraded at the same time. Again automatically.

---

### Post by Alan5127 on 2021-03-07
Hi Impavidus,

Appreciate your reply:
> **Impavidus said:**
> It means that when you install libvirt-deamon-system version 6.0.0-0ubuntu8.7, you have to install version 6.0.0-0ubuntu8.7 of those dependencies too. Which all happens automatically if you let apt handle this stuff. If some update later provides a later version of libvirt-deamon-system, it will probably depend on later versions of those dependencies, so they get upgraded at the same time. Again automatically.

If I were, for some reason, to install an older version of libvirt-deamon-system (say, Version 5 - assuming that exists / existed), would 'apt' then look (backwards) and check the exact dependencies for that version of the package?

Thanks,

Alan.

---

### Post by CelticWarrior on 2021-03-07
APT uses online repositories for checking, downloading and installing software.
No old versions (and dependencies) are kept in the same repository.

---

### Post by Alan5127 on 2021-03-07
Thanks Guys - Think I have it now.

Alan.

---

