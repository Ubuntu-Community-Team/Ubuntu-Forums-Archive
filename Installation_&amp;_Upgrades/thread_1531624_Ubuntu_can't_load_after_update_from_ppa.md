---
title: "Ubuntu can't load after update from ppa"
date: 2010-07-15
forum: Installation &amp; Upgrades
---

### Post by Novarg on 2010-07-15
Hi.
I tryed to update my ubuntu (10.04) from this ppa [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/)
because on my new laptop i can't change backlight. That ppa contain freshest nvidia drivers.

After update i can't load my ubuntu, getting  freezed boot screen with ubuntu logo and dots under it that not changed.

Can anyone suggest how to fix this? Maybe i can rollback all updates from certain ppa somehow?

---

### Post by andrewthomas on 2010-07-15
> **Novarg said:**
> Hi.
I tryed to update my ubuntu (10.04) from this ppa [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/")
because on my new laptop i can't change backlight. That ppa contain freshest nvidia drivers.

After update i can't load my ubuntu, getting  freezed boot screen with ubuntu logo and dots under it that not changed.

Can anyone suggest how to fix this? Maybe i can rollback all updates from certain ppa somehow?
To revert to official packages, you can install the **ppa-purge** package and run ```
sudo ppa-purge ubuntu-x-swat
``` If you have driconf it is recommended to remove ~/.drirc when changing versions!

---

### Post by Novarg on 2010-07-15
Thanks, it work.

---

### Post by andrewthomas on 2010-07-15
glad to be of help

---

