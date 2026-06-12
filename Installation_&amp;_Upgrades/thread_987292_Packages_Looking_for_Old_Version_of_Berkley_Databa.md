---
title: "Packages Looking for Old Version of Berkley Database Libraries"
date: 2008-11-19
forum: Installation &amp; Upgrades
---

### Post by TheRealTerry on 2008-11-19
I keep running into packages having a dependency on libdb4.3, but that package itself is not found on any of my archive (restricted, main, universe, multiverse).  I have version 4.6 of the Berkley Database Libraries installed, and my sources seem to show that I have access to versions 4.0-4.2 and then 4.4-4.6 but the one dependency I need seems to be skipped.

Is there any way to A) force these packages (specifically Postfix) to use the newer libdb4.6 or to install this old version from somewhere side by side.

I have searched forums and the web high and low and I don't see anyone else having this issue.

I am in Ubuntu Hardy Heron desktop version

---

### Post by TheRealTerry on 2008-11-19
Figured it out. I went into Synaptic Package Manager and opened the settings for sources. I selected the "main" Ubuntu sources instead of US specific and the 4.3 package became available.

---

