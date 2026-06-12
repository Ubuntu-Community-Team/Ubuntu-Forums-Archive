---
title: "Broken dependencies trying to install Mac On Linux on Gutsy PS3"
date: 2008-01-06
forum: Installation &amp; Upgrades
---

### Post by rwfsmith on 2008-01-06
I'm trying to install Mac On Linux onto my PS3 running Gutsy, 7.10. The mol and mol-drivers-linux installs just fine. But when I "sudo apt-get install mol-drivers-macosx" I get the error back:

The following packages have unmet dependencies: 
  mol-drivers-macosx: Depends: mol (>= 0.9.68+20030225-1) but it is not going to be installed
E: Broken packages

trying to install through synaptic it tells me its going to remove mol and mol-drivers-linux, then gets the same error. I've tried it without mol and mol-drivers-linux installed and it gives the same error, just doesn't say its going to remove them.

I also tried running "sudo aptitude install mol-drivers-macosx", but it says the mol package is broken, then pretty much the same error as apt-get

The following packages have unmet dependencies:
  mol: Conflicts: mol-drivers-macosx (< 0.9.72.1-1) but 0.9.71-1 is to be installed
Resolving dependencies...
Inable to resolve dependencies!  Giving up...
Abort.


I've tried a few things I saw on other forums, dpkg --configure -a, apt-get -f install, uninstalled and reinstalled mol and mol-drivers-linux, but nothing seems to get it working.

any help with this would be appreciated.

Thanks,
            Ryan

---

### Post by slacka-vt on 2008-04-15
Same problem here. I suppose we'll have to compile our own mol-modules but I have been unsuccessful at that as well. shame

~s

---

