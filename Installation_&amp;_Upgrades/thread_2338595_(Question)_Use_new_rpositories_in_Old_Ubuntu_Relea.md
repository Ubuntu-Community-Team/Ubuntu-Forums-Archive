---
title: "(Question) Use new rpositories in Old Ubuntu Releases"
date: 2016-09-29
forum: Installation &amp; Upgrades
---

### Post by Jvinas on 2016-09-29
Hi , guys 
I have shure that my question is a little weird , but in a hypothetical situation can i use for example Ubuntu 16.04 repos in Ubuntu 10.10, updating the sources.list to Xenial to
use the newest versions of programs without updating the system to 16.04 ?

PS: Sorry for my typing errors :)

---

### Post by ian-weisser on 2016-09-29
1) 10.10 is past End of Life, is not receiving security updates, and is vulnerable to known, published exploits. Do not put a 10.10 system on the internet.

2) No.
Don't do it.
Trying to use 16.04 packages on *any* other release of Ubuntu is very likely break your system horribly.

You see, packages are not independent bundles of software. Packages have dependencies, which in turn have other dependencies. The OS and software are *integrated*. A distro release is a snapshot of software (OS and applications) that all uses the same dependencies and libs and system calls...and that is exactly the gordian knot you are trying to untie merely to update a couple applications. Those lib and system calls have evolved since 10.10 - they are not the same anymore...which is why distros use snapshots. Ubuntu is *designed* to upgrade the entire system at once, including applications.

---

### Post by Bucky Ball on 2016-09-30
Bottom line: you shouldn't be using 10.10 at all, as noted. It is well out of support and a vulnerability.

As for this idea? Forget and install a supported release. I suggest 16.04 LTS, supported until 2021. Good luck. Whatever you decide to do, get off 10.10. If you must have it, get the machine offline. It is a security vulnerability. Also, if you stick with it, it is way too old to expect much support with it. The community's moved on ... :|

PS: If the only reason you're doing this is because you have an old machine that won't run a modern Ubuntu, try a lighter flavour: Xubuntu or Lubuntu. They are MUCH more like what you are using now. 16.04 doesn't even use the same desktop environment as 10.10 anymore (and the 10.10 DE hasn't been used as default for years; it is now Unity).

---

### Post by Jvinas on 2016-09-30
Ok Guys , thanks
 So,all packages are made to work with their respective version of Ubuntu. All Ubuntu versions have their respective repos,packages and dependencies and this is why we cant use other Ubuntu version repos ? 
Ps: i not using 10.10. I was using 14.04
and already upgraded to 16.04.1 with a clean install. It was just my curiosity.

---

### Post by howefield on 2016-09-30
> **Jvinas said:**
>  So,all packages are made to work with the respective version of Ubuntu. All Ubuntu versions have their respective repos,packages and dependencies and this is why we cant use other Ubuntu version repos ? 

That's pretty much it, mixing the repositories is likely to lead to all sorts of issues with dependancies.[/QUOTE]

Likewise if using other repositories eg PPAs it is good to make sure that there is one that corresponds with your version of Ubuntu.

---

