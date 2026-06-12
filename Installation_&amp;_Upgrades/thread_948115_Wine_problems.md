---
title: "Wine problems"
date: 2008-10-14
forum: Installation &amp; Upgrades
---

### Post by MistaMista on 2008-10-14
I get this problem when I try to reinstall wine.....my computer says i have held broken packages.....whats next

---

### Post by weirdtalk on 2008-10-14
> **MistaMista said:**
> I get this problem when I try to reinstall wine.....my computer says i have held broken packages.....whats next
hmm.
Copy and paste the results of these commands if you would.
```
sudo apt-get -f install
sudo apt-get install wine
```

---

### Post by MistaMista on 2008-10-14
I get this message....Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: binfmt-support (>= 1.1.2) but it is not installable
E: Broken packages

---

