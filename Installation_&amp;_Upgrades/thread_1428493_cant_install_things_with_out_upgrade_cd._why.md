---
title: "cant install things with out upgrade cd. why?"
date: 2010-03-12
forum: Installation &amp; Upgrades
---

### Post by steve19137 on 2010-03-12
i had to restore my system because i had to much junk and i thought that it would be easier to restore. now i am regretting that. 

i am trying to install gparted so i can format my thumb drive. when i go to install it (from either the terminal or synaptic) and i get this message

> Media change: please insert the disc labeled
 'Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091027)'
in the drive '/cdrom/' and press enter



see when i installed ubuntu, i had to go from 8.10 to 9.04 to 9.10. i had to do that because 8.10 is the only time ubuntu has my wireless drivers installed in the system, available to activate. i then put in my 9.10 alternate disc to get the error that i couldnt skip 9.04. so i downloaded 9.04 with the update manager, then used the 9.10 alternate disc. everything was going fine, the restore of the user folders, and it was all good. now i get that error. how can i fix it and what does it mean?

---

### Post by srs5694 on 2010-03-12
APT is configured to use your local CD/DVD media as well as remote sources, so when it finds that a package is on the local media (according to its on-disk database), it asks for that rather than go to the network.

The solution is fairly simple: Open up /etc/apt/sources.list and comment out all references to CD-ROM media. On one of my systems, they look like this (commented out):

```

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted

```

You can do this from Synaptic, too. Select Settings->Repositories. I believe you'd then uncheck the CD-ROM media in the field at the bottom of the "Ubuntu Software" tab.

---

### Post by steve19137 on 2010-03-12
> **srs5694 said:**
> APT is configured to use your local CD/DVD media as well as remote sources, so when it finds that a package is on the local media (according to its on-disk database), it asks for that rather than go to the network.

The solution is fairly simple: Open up /etc/apt/sources.list and comment out all references to CD-ROM media. On one of my systems, they look like this (commented out):

```

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted

```You can do this from Synaptic, too. Select Settings->Repositories. I believe you'd then uncheck the CD-ROM media in the field at the bottom of the "Ubuntu Software" tab.

haha, i didnt think about that. thanks for the reminder.

---

