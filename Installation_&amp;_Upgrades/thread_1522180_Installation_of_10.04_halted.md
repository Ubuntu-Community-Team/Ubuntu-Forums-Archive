---
title: "Installation of 10.04 halted"
date: 2010-07-01
forum: Installation &amp; Upgrades
---

### Post by Thrasyllus on 2010-07-01
Tried to migrate from 8.04 LTS to 10.04 LTS. The downloading occurred without a glitch but soon after installation began I got this message: 
> Could not install the upgrades

Error during commit
'E:Couldn't configure pre-depend jre for openoffice.org-writer2latex,
probably a dependency cycle.'
Restoring original system state
 
What is this?

---

### Post by flick on 2010-07-01
Some discussion here :

[http://ubuntuforums.org/showthread.php?t=1499601](http://ubuntuforums.org/showthread.php?t=1499601)

Sounds like you might have to apt-get purge the package that has hung up, then try the update/upgrade, and if/when the upgrade succeeds, then install the offending package.

---

### Post by Thrasyllus on 2010-07-02
Thank you. flick. I hope the offending package isn't what prevents the upgrade from being installed!

---

### Post by Thrasyllus on 2010-07-03
Bump. Have tried a couple more times and the same message appears.

---

### Post by noppie on 2010-07-03
I think you problme maybe because you are suppose to go from 8.4 to the one above that and then the next one above..
it is my understanding you can't make a big jump like you are trying. I could be wrong,, but that is my understanding.

---

### Post by arpanaut on 2010-07-03
noppie, that is incorrect because 8.04 is a LTS release, It can leap the intervening releases to the next LTS which is 10.04.

My only suggestion would be to remove the offending package and then reinstall it afterward.   Is "openoffice.org-writer2latex," a specially installed addon or part of the standard OOo?

P.S. Did you remove any PPA's and third party repositories before you tried the upgrade?

---

### Post by Thrasyllus on 2010-07-04
Thank you arpanaut!

> **arpanaut said:**
> My only suggestion would be to remove the offending package and then reinstall it afterward. Is "openoffice.org-writer2latex," a specially installed addon or part of the standard OOo?
 
P.S. Did you remove any PPA's and third party repositories before you tried the upgrade?
To answer your last question, no I did not. As for openoffice.org-writer2latex, I certainly did not add it and nobody has been upgrading my 8.04 except Ubuntu.
 
However, I *did* get this message at the beginning of the upgrade:
> Third party sources disabled

Some third party entries in your sources.list were disabled. You can
re-enable them after the upgrade with the 'software-properties' tool
or your package manager.
Whatever this is about, I thought it did not matter since the message says I can re-enable whatever needs to be re-enabled after the upgrade. (I admit I don't know what this is about.)

---

