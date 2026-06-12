---
title: "Ubuntu 20.04 to 22.04 upgrade seems impossible on DELL latitude E6430"
date: 2022-09-02
forum: Installation &amp; Upgrades
---

### Post by Semn on 2022-09-02
I have an old, but excellent laptop, Dell Latitude E6430, and I am running Ubuntu 20.04 on it. Unfortunately, it seems upgrading to 22.04 seems impossible. 

I have checked with Dell forum, but "no guarantee - no  help". So I am stuck.

I have tried $sudo apt full-upgrade$ and pressing Upgrade on the button that appears via the Software Update icon on the menu of Ubuntu, but neither of the two find the Upgrade. It seems the second option knows there is an upgrade available, but it doesn't trigger the upgrade process.


Any ideas what I can do?

Thanks

---

### Post by vanadium on 2022-09-02
>  Any ideas what I can do?
Obviously. A fresh install. Very much guaranteed to work well on Dell hardware.

---

### Post by Semn on 2022-09-02
thanks.

---

### Post by grahammechanical on 2022-09-02
Please read the man page for apt.

```
man apt
```

It says:

> **full-upgrade** (apt-get(8))
           full-upgrade performs the function of upgrade but will remove currently installed packages if this is needed to upgrade the system as a whole.

The command that you are using does not upgrade one Ubuntu LTS version to the next Ubuntu LTS version. Many people also misunderstand the work of this command.

```
sudo apt-get dist-upgrade
```

the man page for apt-get says this:

> [B]dist-upgrade
[/B]           dist-upgrade in addition to performing the function of upgrade, also intelligently handles changing dependencies with new versions of packages; apt-get has a "smart" conflict resolution system, and it will attempt to upgrade the most important packages at the expense of less important ones if necessary. The dist-upgrade command may therefore remove some packages. The /etc/apt/sources.list file contains a list of locations from which to retrieve desired package files. See also apt_preferences(5) for a mechanism for overriding the general settings for individual packages.

If you open Software & Updates>Updates tab, is the setting Notify me of a new Ubuntu version set for long term support versions?

When I run Software Updater on 20.04 I get an offer to upgrade to 22.04. Do you not see that offer?

Regards

---

