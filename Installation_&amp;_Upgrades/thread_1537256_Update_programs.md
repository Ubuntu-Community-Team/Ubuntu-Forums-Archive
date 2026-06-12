---
title: "Update programs"
date: 2010-07-23
forum: Installation &amp; Upgrades
---

### Post by unknown user on 2010-07-23
Is there a way that I can get the programs that I have to check for and update automatically within Ubuntu

---

### Post by Rubi1200 on 2010-07-24
> **unknown user said:**
> Is there a way that I can get the programs that I have to check for and update automatically within Ubuntu

Program and security updates are handled by Update Manager which automatically checks for newer versions and so on.

But, and here comes the caveat, this is only for programs supported by Canonical. 

This means that if you installed something from Synaptic, Ubuntu Software Center, or another source and it is not supported, then you won't receive notifications of upgrades or security fixes etc.

When you are searching for things to install on the system check to see if there is a line like this:

"Canonical does not provide updates for [program name]. Some updates may be provided by the Ubuntu community."

---

### Post by ankspo71 on 2010-07-24
Hi,
If you installed the application through Ubuntu (or Kubuntu, Xubuntu, etc), there should be future updates for those applications sometime in the future, but there is no guarantee on when that might be.

If you installed a package from an outside source, meaning you got the package from somewhere else on the internet, then there will be no updates from that source, unless they (or you) have also added a repository for you to get updates from.

One way to install packages from outside of Ubuntu, and still get updates from within Ubuntu, is to search for a Personal Package Archive (PPA) has has a version of the program you want. A PPA is one place where you can add an extra repository so you can install their software through Ubuntu, and be able to get updates for it through ubuntu, even though the software comes from an outside source. 

Another way is to add the package developer's own Ubuntu compatible repository. The homepages of "Tor" and "PlayOnLinux" are two example sites that I can think of that provide such repositories. 

Keep in mind though, that installing from third party repositories can sometimes cause problems with system stability, or application stability, and can possibly have unmet dependencies for that application. I personally haven't run into too many of these problems though.

The bottom line is, the package you have installed must have a repository in which it came from in order to get any updates, through Ubuntu's package management and update system.
Hope this helps.

---

