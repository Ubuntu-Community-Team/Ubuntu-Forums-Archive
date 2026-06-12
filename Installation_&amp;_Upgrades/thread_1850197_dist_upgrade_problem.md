---
title: "dist upgrade problem"
date: 2011-09-26
forum: Installation &amp; Upgrades
---

### Post by hotshot247 on 2011-09-26
i'm using ubuntu 11.04 64-bit and everytime i try to do a dist-upgrade from the terminal, it says, 
"Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Failed
The following packages have unmet dependencies:
 ia32-libs : Depends: lib32v4l-0 but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages." i've been trying to fix this for a while with no luck. any help would be great! thanks.

---

### Post by mikewhatever on 2011-09-26
Probably has something to with the multiarch support in Oneric.
[https://wiki.ubuntu.com/OneiricOcelot/TechnicalOverview/Beta2#Improved_handling_of_32-bit_compatibility_on_amd64_systems](https://wiki.ubuntu.com/OneiricOcelot/TechnicalOverview/Beta2#Improved_handling_of_32-bit_compatibility_on_amd64_systems)

Try removing ia32-libs along with the 32bit applications.

---

### Post by hotshot247 on 2011-09-26
> **mikewhatever said:**
> Probably has something to with the multiarch support in Oneric.
[https://wiki.ubuntu.com/OneiricOcelot/TechnicalOverview/Beta2#Improved_handling_of_32-bit_compatibility_on_amd64_systems](https://wiki.ubuntu.com/OneiricOcelot/TechnicalOverview/Beta2#Improved_handling_of_32-bit_compatibility_on_amd64_systems)

Try removing ia32-libs along with the 32bit applications.

i'm using 11.04 not 11.10. do you think it would work on the version i have?

---

### Post by mikewhatever on 2011-09-26
Yes, but you've tried upgrading, and the only candidate for upgrading from 11.04 is 11.10.

---

### Post by oldos2er on 2011-09-26
If you run ```
sudo aptitude safe-upgrade
``` do you get the same error?

---

