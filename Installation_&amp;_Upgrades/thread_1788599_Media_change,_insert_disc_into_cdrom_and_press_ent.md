---
title: "Media change, insert disc into /cdrom/ and press enter."
date: 2011-06-22
forum: Installation &amp; Upgrades
---

### Post by Donzieja on 2011-06-22
Whenever I try to install something (like flashplugin-nonfree), it says:

```
Media change: please insert the disc labeled
 'Kubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)'
in the drive '/cdrom/' and press enter
```

This is very irritating. I also encounter the problem where every time after I perform (or attempt to) perform an apt-get operation, and wish to perform another, I get this:

```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

Anyone out there know of a solution to this? I'm running Kubuntu 11.04.

Thanks,

-Don

---

### Post by Beacon11 on 2011-06-23
Sounds like your installation disc is in the repository sources list. It's been a while since I've used Kubuntu, but I think you can edit this list by opening Adept and hitting Manage Repositories. Just remove the CD from that list.

---

