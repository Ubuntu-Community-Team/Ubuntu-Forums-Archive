---
title: "do-release-upgrade 18.04 LTS to 20.04 LTS"
date: 2020-08-10
forum: Installation &amp; Upgrades
---

### Post by rsteinmetz70112 on 2020-08-10
I just checked and 20.04.1 is available for download.  I thought that when that happened 18.04 LTS was supposed to tell me a new release was available. I checked  the settings in Upgrade Manager and it is set to tell me about new LTS releases. I tried do-release-upgrade and got an error message.

```
$ do-release-upgrade
Checking for a new Ubuntu release
There is no development version of an LTS available.
To upgrade to the latest non-LTS develoment release 
set Prompt=normal in /etc/update-manager/release-upgrades.
```

This is on the 20.04 upgrade page:
> Launch the upgrade tool with the command sudo do-release-upgrade on 19.10; use sudo do-release-upgrade -d if you are using 18.04 LTS. 

The -d switch is necessary to upgrade from Ubuntu 18.04 LTS as upgrades have not yet been enabled and will only be enabled after the first point release of 20.04 LTS. 

What am I missing, or have the admins just not gotten around to flipping the switch?

---

### Post by deadflowr on 2020-08-10
> have the admins just not gotten around to flipping the switch?
This.
Purposely delayed to refine it so fewer issues for users who want the upgrade.
Hopefully it'll be available by the end of the week, if not sooner.

---

### Post by rsteinmetz70112 on 2020-08-10
Thanks

---

