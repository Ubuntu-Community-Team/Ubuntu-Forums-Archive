---
title: "gutsy tribe to gutsy rc: kdesu &quot;adept_manager --version-upgrade&quot; does not work"
date: 2007-10-12
forum: Installation &amp; Upgrades
---

### Post by jamadagni on 2007-10-12
I installed Kubuntu Gutsy Tribe 5 and from then I am doing daily updates with sudo apt-get update && sudo apt-get dist-upgrade. So I think effectively I have all latest packages.

But after reading latest Kubuntu RC release notes, I tried procedure at [https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades) and though the gutsy-proposed repo gets added to my /etc/apt/sources.list and update+dist-upgrade the procedure bonks at the following step:

```
kdesu "adept_manager --version-upgrade"
```

I get:

> 
adept_manager: Unknown option '--version-upgrade'.
adept_manager: Use --help to get a list of available command line options.


While the version of adept-manager I am using is:

> 
$ apt-cache policy adept-manager
adept-manager:
  Installed: 2.1.3ubuntu15


and I get:

> 
$ adept_manager --help
...
Options:
  --dist-upgrade            add toolbar button to launch the version upgrade tool to the latest release
  --dist-upgrade-proposed   add toolbar button to launch the version upgrade tool to proposed next release
  --dist-upgrade-devel      add toolbar button to launch the version upgrade tool to development version


So which command should I use instead of adept_manager --version-upgrade?

Are those wiki instructions for Feisty -> Gutsy RC only?

---

### Post by Pumalite on 2007-10-12
If you are up to date on the updates on your Gutsy Tribe, you already have Gutsy RC

---

### Post by LaneLester on 2007-10-12
> **Pumalite said:**
> If you are up to date on the updates on your Gutsy Tribe, you already have Gutsy RC
Just to be sure this is a general principle. Are you saying that updates will take you from any versiion of Gutsy all the way to the release version?

I'm too impatient; I'd like to install the RC1, but I'd like it if I could just do the updates and end up with the release version.

Lane

---

### Post by Pumalite on 2007-10-12
Don't worry. If you've done the updates, you already have it. And it will take you all the way to Final Release October the 18th.

---

### Post by LaneLester on 2007-10-12
> **Pumalite said:**
> Don't worry. If you've done the updates, you already have it. And it will take you all the way to Final Release October the 18th.
Great news! Thanks.

Lane

---

