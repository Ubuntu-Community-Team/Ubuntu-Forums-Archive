---
title: "What's wrong with Ubuntu 24.04 Release?"
date: 2024-08-25
forum: Installation &amp; Upgrades
---

### Post by jfha73 on 2024-08-25
Hey guys,

I've been trying to upgrade my Ubuntu 22.04 to the latest 24.04, but Software updates says it's up to date and the CLI is saying this:

```
Checking for a new Ubuntu release
There is no development version of an LTS available.
To upgrade to the latest non-LTS development release 
set Prompt=normal in /etc/update-manager/release-upgrades.
```

What's happening?

---

### Post by deadflowr on 2024-08-25
The point release has been delayed, and with that the upgrade path.
[https://discourse.ubuntu.com/t/ubuntu-24-04-1-point-release-delayed-until-august-29/47110](https://discourse.ubuntu.com/t/ubuntu-24-04-1-point-release-delayed-until-august-29/47110)

---

### Post by grahammechanical on 2024-08-25
Using the terminal to upgrade one Ubuntu release to the next Ubuntu release is usually done with Ubuntu Server versions.

Please note these two quotes from the Official documentation

[https://ubuntu.com/server/docs/how-to-upgrade-your-release](https://ubuntu.com/server/docs/how-to-upgrade-your-release)

> Upgrading to a development release of Ubuntu is available using the -d flag. However, using the development release (or the -d flag) is **not recommended** for production environments.

> Upgrades from one LTS release to the next one are only available after  the first point release. For example, Ubuntu 18.04 LTS will only upgrade  to Ubuntu 20.04 LTS after the 20.04.1 point release. If users wish to  update before the point release (e.g., on a subset of machines to  evaluate the LTS upgrade) users can force the upgrade via the -d flag.

Using the -d flag works during the 26 weeks development period of a Ubuntu release. Now that Ubuntu 24.04 LTS is released we will not get access to another LTS development version until after Ubuntu 25.10 is released.

By the way the dist-upgrade command does this

> dist-upgrade in addition to performing the function of upgrade, also intelligently handles changing dependencies with new versions of packages; apt-get has a "smart" conflict resolution system, and it will attempt to upgrade the most important packages at the expense of less important ones if necessary. The dist-upgrade           command may therefore remove some packages

Regards

---

### Post by Dennis N on 2024-08-25
> **jfha73 said:**
> Hey guys,

I've been trying to upgrade my Ubuntu 22.04 to the latest 24.04, but Software updates says it's up to date and the CLI is saying this:

```
Checking for a new Ubuntu release
There is no development version of an LTS available.
To upgrade to the latest non-LTS development release 
set Prompt=normal in /etc/update-manager/release-upgrades.
```

What's happening?

Two things:
1) In Software & Updates utility > Updates Tab
set "Notify me of a new Ubuntu version" to "For any new version"

Then,
Checking for new release in 22.04 will now show this:
```
dmn@Tyana-vm:~$ do-release-upgrade -c
Checking for a new Ubuntu release
New release '24.04 LTS' available.
Run 'do-release-upgrade' to upgrade to it.

```
and,
2) Don't add the -d to the do-release-upgrade command when upgrading.

---

