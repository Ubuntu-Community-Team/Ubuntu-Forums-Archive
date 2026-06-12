---
title: "Eclipse updates don't work because of missing plugin"
date: 2008-06-05
forum: Installation &amp; Upgrades
---

### Post by peterdm on 2008-06-05
When installing Eclipse from the repo, the **Eclipse Java Development Tools 2.2.2.r322** is disabled because of **Plug-in "org.eclipse.jdt.junit4.runtime" version "0.0.0" referenced by this feature is missing.**. Checking out forum history, this appears to be a known problem since Gutsy or even before, and it is still not fixed in Hardy. The consequence is that the dependent plugins, i.e. **Eclipse Project SDK 3.2.2.r322** and all the updates are also disabled. This is very inconvenient for all developers out there. Sure, I can get probably get it to work if I avoid using the Ubuntu packaging system, and manually download and install Eclipse. Surely that is not the Ubuntu spirit, so here is my cry to the Ubuntu package maintainers: *please please please* fix the Eclipse package!

---

### Post by babuu on 2008-08-28
> **peterdm said:**
> When installing Eclipse from the repo, the **Eclipse Java Development Tools 2.2.2.r322** is disabled because of **Plug-in "org.eclipse.jdt.junit4.runtime" version "0.0.0" referenced by this feature is missing.**. Checking out forum history, this appears to be a known problem since Gutsy or even before, and it is still not fixed in Hardy. The consequence is that the dependent plugins, i.e. **Eclipse Project SDK 3.2.2.r322** and all the updates are also disabled. This is very inconvenient for all developers out there. Sure, I can get probably get it to work if I avoid using the Ubuntu packaging system, and manually download and install Eclipse. Surely that is not the Ubuntu spirit, so here is my cry to the Ubuntu package maintainers: *please please please* fix the Eclipse package!

Yes I just installed Eclipse with JDT and configured with the Android SDK, but I am stuck on this. Same problem. So if someone knows how to fix this, please let me know, I want to start writing applications for Android. I run Hardy.

---

