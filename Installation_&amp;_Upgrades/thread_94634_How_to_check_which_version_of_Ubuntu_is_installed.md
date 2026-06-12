---
title: "How to check which version of Ubuntu is installed?"
date: 2005-11-24
forum: Installation &amp; Upgrades
---

### Post by doyenne on 2005-11-24
How can I see which version of Ubuntu is installed?

---

### Post by aysiu on 2005-11-24
You didn't install it yourself?
This isn't the most direct way to check, but here are a few cosmetic differences between Hoary and Breezy:

1. Breezy has a graphical boot splash--Hoary does not.
2. Breezy puts Terminal in Accessories, not System Tools.
3. Breezy has a menu item called Add Applications that's separate from Synaptic Package Manager

---

### Post by kalin on 2005-11-24
See what's written in "/etc/lsb-release"

E.g. the breezy one looks like that:

```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=5.10
DISTRIB_CODENAME=breezy
DISTRIB_DESCRIPTION="Ubuntu (The Breezy Badger Release)"

```

---

### Post by doyenne on 2005-11-24
Thanks for your answers!
[QUOTE=aysiu]You didn't install it yourself?[/QUOTE]
I did, but[LIST]
[*]...I am new to Ubuntu and after a lot of browsing for help I couldn't remember whether I had Breezy or Hoary installed.
[*]...I was curious whether the automatic update-feature of Ubuntu also updates my installation to a new release when it comes out. If so, I would be glad to be able to see which version is currently installed.
[/LIST]
So, I keep one question... Does Ubuntu automatically update itself to the new release? e.g. If you are running Hoary and connected to the internet, does your system automatically get updated to Breezy?

(Today I got a message that my kernel was updated. It surprised me -- does Ubuntu release new kernel versions between official releases?)

---

### Post by doyenne on 2005-11-24
Ah... I got the answer in this forum: [https://wiki.ubuntu.com/BreezyUpgradeNotes](https://wiki.ubuntu.com/BreezyUpgradeNotes)

As I see, updating to the new release requires me to change the packages source.

I'm still surprised that Ubuntu updates my kernel between 2 releases...

---

