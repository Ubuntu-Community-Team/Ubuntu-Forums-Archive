---
title: "Gimp wont install"
date: 2011-10-09
forum: Installation &amp; Upgrades
---

### Post by matborda on 2011-10-09
```
matborda@matborda-laptop:~$ sudo apt-get install gimp
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

what am i supposed to do?

---

### Post by Dy1anW on 2011-10-09
> **matborda said:**
> ```
matborda@matborda-laptop:~$ sudo apt-get install gimp
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```what am i supposed to do?

If you can't get lock it's because you have something else using it, like Synaptic. Make sure that's closed first before trying again.

---

### Post by matborda on 2011-10-09
you were right, but anyway

```
matborda@matborda-laptop:~$ sudo apt-get install gimp
[sudo] password for matborda: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gimp: Depends: gimp-data (<= 2.6.8-z) but 2.6.11-1~getdeb1~maverick is to be installed
E: Broken packages

```

---

### Post by Dy1anW on 2011-10-09
I've actually seen a situation similar to this when an update "broke" AWN, and I couldn't install the new version because of some broken package. IIRC I simply removed the package causing problems (in your case gimp-data), which then allowed apt to install all packages properly.

Alternatively, and I should've tried this when it happened to me, is to just run sudo apt-get update (which *should* satisfy the dependency). If that doesn't do the trick then uninstalling everything to do with the previous Gimp is the best bet.

---

### Post by Elfy on 2011-10-09
moved to new thread - please don't tag onto an old thread please

---

