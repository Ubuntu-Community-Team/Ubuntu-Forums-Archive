---
title: "Firefox 3.6.23 crashes on 2.6.32-34"
date: 2011-10-04
forum: Installation &amp; Upgrades
---

### Post by tobiz on 2011-10-04
I've recently applied the latest upgraded from the repository to my 10.04 system and Firefox now crashes very, very frequently. It is not possible to determine which web pages cause the problem.  Has anyone else had this problem?  Is it known by ubuntu support?
System:
Intel Atom D510
Kernel 2.6.32-34-generic
Gnome 2.30.2
Firefox 3.6.23

---

### Post by lovinglinux on 2011-10-04
Please start Firefox in safe mode and check if you can reproduce the problem:

```
firefox -safe-mode
```

If the problem persists, try a clean profile.

```
firefox -P
```

Let me know about the results.

I also suggests that you get Firefox 7. See [Firefox 7 & Beyond Mega Thread](http://ubuntuforums.org/showthread.php?t=1712247)

---

### Post by tobiz on 2011-10-05
> **lovinglinux said:**
> Please start Firefox in safe mode and check if you can reproduce the problem:

```
firefox -safe-mode
```

If the problem persists, try a clean profile.

```
firefox -P
```

Let me know about the results.

I also suggests that you get Firefox 7. See [Firefox 7 & Beyond Mega Thread](http://ubuntuforums.org/showthread.php?t=1712247)
I tried running Firefox in safe-mode as suggested.  It eventually crashed on trying to login on one particular website, all retries had the same result. I then ran the 'standard' Firefox, ie not in safe-mode and this gave exactly the same result for the web page concerned. I re-installed Firefox from the ubuntu repository and was then able to access the web page. Since re-installing Firfox it has been stable.  If this situation changes I'll try your step 2 and let you know the results. At the moment it looks like it could be an issue with the upgrade, however that is achieved.  BTW I won't install Firefox 7 until it is available in the ubuntu repositories; I'm trying to keep to the LTS plan.

---

