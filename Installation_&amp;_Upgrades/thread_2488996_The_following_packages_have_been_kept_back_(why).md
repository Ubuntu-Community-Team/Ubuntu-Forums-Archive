---
title: "The following packages have been kept back (why?)"
date: 2023-07-15
forum: Installation &amp; Upgrades
---

### Post by kifou on 2023-07-15
Running apt update and upgrade, tells me:
The following packages have been kept back:
  evince evince-common libevdocument3-4 libevview3-3
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

Why is that, isn't just safe to upgrade them?

---

### Post by deadflowr on 2023-07-15
Phased updates.
In general Ubuntu's non-security updates run through it's phased update system,
which staggers the release to users slowly.
They do this so that if any issue come up they can halt the update and fix it before it hits all potential users.

Can you just update them anyway?
Yes, or at least i think this still works. But not by using the upgrade commands.
To install packages that are being phased update simply run the install command for the packages.
basically
```
sudo apt install packageA packageB packageC
```
that should still work. Unless something has changed recently.

If you want to break your brain and maybe learn more then read this:
[https://discourse.ubuntu.com/t/phased-updates-in-apt-in-21-04/20345]("https://discourse.ubuntu.com/t/phased-updates-in-apt-in-21-04/20345")

---

