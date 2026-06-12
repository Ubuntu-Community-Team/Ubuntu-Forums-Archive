---
title: "Ubuntu plus kubuntu desktop"
date: 2013-03-04
forum: Installation &amp; Upgrades
---

### Post by jimbo99 on 2013-03-04
I did a clean install of Ubuntu 12.04 (64bit), then updated to 12.10 (64bit) over the web.  I then added the kubuntu backports so that I could install KDE (kubuntu-desktop).  Did an update of the repository.  Then tried to install kubuntu-desktop.  It is complaining that xorg won't be updated, and thus I can't install kubuntu-desktop. 

I installed synaptic, checked to see that the repository for kubuntu backports is there.  It is.  I searched for xorg.  I clicked to upgrade it.  It wants to uninstall ubuntu-desktop.

Anyone else having this issue?  Did someone mess up and make some changes to the kubuntu backports ppa?

Would love any help on this.  

TIA - 

-Jim

---

### Post by oldos2er on 2013-03-05
It's safe to remove ubuntu-desktop since it's just a metapackage: [https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages)

---

