---
title: "[SOLVED] ubuntu to edubuntu upgrade?"
date: 2008-11-18
forum: Installation &amp; Upgrades
---

### Post by Ant68 on 2008-11-18
Hi all,
I would like to know if it and how it is possible to upgrade ubuntu 8.04 to edubuntu 8.10. 

thanks,

---

### Post by Elfy on 2008-11-18
You could try to install edubuntu-desktop and then change software sources to look for normal releases.

```
sudo aptitude install edubuntu-desktop
```

Open software sources from the Sys Admin menu - Update tab - change Release Upgrade to Normal and reload, then run Update Manager.

I'd be inclined to download the iso and do a clean install though.

---

### Post by Bartender on 2008-11-18
I've installed Edubuntu.  My impression is that it isn't really a different version of Ubuntu.  The Edubuntu package just installs to the underlying Ubuntu and runs like any other application.

I'd try upgrading your Ubuntu installation first.  Lots of instructions for that.  Then if Edubuntu did not also update, just install it from the repos.

---

