---
title: "Package blah blah has no installation candidate."
date: 2010-11-07
forum: Installation &amp; Upgrades
---

### Post by Elktro on 2010-11-07
I frequently get error "Package blah blah blah has no installation candidate." while commanding "apt-get install". What does that mean?

---

### Post by geoffmcc on 2010-11-07
sounds like the package is not in the repository, or are you saying you get this for things that you know are?

---

### Post by tommcd on 2010-11-07
> **Elktro said:**
> I frequently get error "Package blah blah blah has no installation candidate." while commanding "apt-get install". What does that mean?
Do you have any third party repos added to your system? This includes those all to frequently problematic PPA repos.
Post the exact package(s) you are trying to install. Also post the exact error message you get.
Also post your */etc/apt/sources.list* file. Also post any files in your */etc/apt/sources.d* directory.

Try commenting out or removing any third party repos. Then run "*sudo apt-get update*". Then see if the errors go away.

---

