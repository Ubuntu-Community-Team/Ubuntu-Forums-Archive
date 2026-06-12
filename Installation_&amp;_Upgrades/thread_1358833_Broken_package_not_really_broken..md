---
title: "Broken package not really broken."
date: 2009-12-18
forum: Installation &amp; Upgrades
---

### Post by DejitaruJin on 2009-12-18
Okay, to make a long story short, I have a package installed that is incorrectly labeled as broken. It depends on one package, but that package is not installed. Why? Because I have a newer version of the package it wants. This newer package works perfectly fine, and is necessary for what I need to do with it, but it is also under a different name than what the "broken" package looks for. The new version and old version are mutually exclusive - installing one will uninstall the other (and this is unavoidable because they're the same files - only the package is named differently).

So, what I need to do, is somehow tell the system, "This package does **not** have any dependencies." Or switch the name of the package it depends on, either way works. How do I go about doing that?

---

