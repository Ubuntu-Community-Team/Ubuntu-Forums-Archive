---
title: "&quot;package-based&quot; cloning?"
date: 2006-04-13
forum: Installation &amp; Upgrades
---

### Post by akron on 2006-04-13
Hi,
Id like to reinstall an Ubuntu system and then have all packages that I installed manually (with synaptic) added automatically. This would be 'package-based cloning' in a way.
Is there any simple way to do this? Id maybe like to produce a list of all installed packages and get some script to reinstall the missing ones on another system. Might this work? How about dependencies?

Thanks for any help,
bye,
Mike.

---

### Post by McLogic on 2006-04-13
Making and loading this list of packages is a feature of Synaptic.

Make the list on the current machine:
File > Save Markings As... > [x] Save full state, not only changes

Load the list on the new machine:
File > Read Markings...


It works, just like you want it to. :p

---

### Post by akron on 2006-04-13
Ah, now that sounds reasonable. I think I like synaptic even more now. Thanks a lot ;)

---

