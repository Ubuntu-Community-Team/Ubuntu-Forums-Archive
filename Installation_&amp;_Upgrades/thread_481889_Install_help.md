---
title: "Install help"
date: 2007-06-23
forum: Installation &amp; Upgrades
---

### Post by ChopperX on 2007-06-23
i think i know there is an easier way to install things and that is by placing them into the usr/lib directory but i dont have the right permissions. Can someone help?

---

### Post by 5-HT on 2007-06-23
To modify a file outside of your home directory, you will need to use 'sudo' to escalate your privileges. Please refer to [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for more information.

FWIW: It is the Ubuntu way to use Ubuntu's package manager to manage your packages (overall: it'll lead to far less headaches; or rather, no headaches at all).

FWIW2: Anything in /usr/local will be ignored by the package manager, so you can install stuff there to be 'off-the-radar' so to speak.
cheers,

---

