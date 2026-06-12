---
title: "Ubuntu server keeps telling me there are updates"
date: 2019-09-19
forum: Installation &amp; Upgrades
---

### Post by backups-f on 2019-09-19
Hi

Ubunutu 18.04 keeps telling me there are 2 updates.

if i do apt-get update and apt-get upgrade it does not update these. It does update any available others. But this message keeps coming back every day.

i did the apt autoremove as suggested but it does not solve my issue. How can i detect which 2 packages need to be updated?

How to resolve?

Thank you for any input and your time


see attached images.

[https://cl.ly/cb9a358d0126](https://cl.ly/cb9a358d0126)

[URL="https://cl.ly/e0b816874d3b"]https://cl.ly/e0b816874d3b


[/URL]

---

### Post by howefield on 2019-09-19
Try ...

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by guiverc on 2019-09-19
From `man apt-get`

>        upgrade
           upgrade is used to install the newest versions of all packages currently
           installed on the system from the sources enumerated in /etc/apt/sources.list.
           Packages currently installed with new versions available are retrieved and
           upgraded; under no circumstances are currently installed packages removed, or
           packages not already installed retrieved and installed. New versions of
           currently installed packages that cannot be upgraded without changing the
           install status of another package will be left at their current version. An
           update must be performed first so that apt-get knows that new versions of
           packages are available.

       dist-upgrade
           dist-upgrade in addition to performing the function of upgrade, also
           intelligently handles changing dependencies with new versions of packages;
           apt-get has a "smart" conflict resolution system, and it will attempt to
           upgrade the most important packages at the expense of less important ones if
           necessary. The dist-upgrade command may therefore remove some packages. The
           /etc/apt/sources.list file contains a list of locations from which to retrieve
           desired package files. See also apt_preferences(5) for a mechanism for
           overriding the general settings for individual packages.



ie. `apt-get upgrade` has limits on what it can upgrade; dist-upgrade or full-upgrade (for `apt`) perform the upgrade fully as per Howefield's suggestion

---

### Post by backups-f on 2019-09-21
Thank you!   that fixed the issue !

Have a great day

---

