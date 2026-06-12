---
title: "Third party software and ubuntu-restricted-extras in 13.10"
date: 2014-03-31
forum: Installation &amp; Upgrades
---

### Post by mindbox2 on 2014-03-31
Regarding ubuntu 13.10 (I haven't checked previous versions), when the option
"Installing this third-party software" is ticked in the first steps of the installation wizard,
the package **ubuntu-restricted-addons** is installed but **ubuntu-restricted-extras**
is not.

Is that the expected behavior or should it be considered a bug?
 I would expect **ubuntu-restricted-extras** to be installed, 
specially since the description of the **ubuntu-restricted-addons** package
states that:

[I]You should not install this package directly, but instead install the
ubuntu-restricted-extras package.[/I]

This has been discussed here:

[https://askubuntu.com/questions/394622/third-party-software-was-not-installed](https://askubuntu.com/questions/394622/third-party-software-was-not-installed)
[http://askubuntu.com/questions/22285/clarification-of-the-third-party-software-options-during-system-installation/22291#22291](http://askubuntu.com/questions/22285/clarification-of-the-third-party-software-options-during-system-installation/22291#22291)

but still not clear to me.

Thanks in advance for your feedback.

---

### Post by ian-weisser on 2014-04-03
Seems like a bug.
Or the package description of ubuntu-restricted-addons is wrong...which would also be a bug.

---

