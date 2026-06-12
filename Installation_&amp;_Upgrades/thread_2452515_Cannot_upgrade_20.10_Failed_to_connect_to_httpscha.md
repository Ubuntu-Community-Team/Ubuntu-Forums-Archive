---
title: "Cannot upgrade 20.10 Failed to connect to https://changelogs.ubuntu.com/meta-release"
date: 2020-10-23
forum: Installation &amp; Upgrades
---

### Post by nhasian on 2020-10-23
Trying to upgrade Kubuntu 20.04.1 LTS to Kubuntu 20.10.

When I run ```
sudo do-release-upgrade
```, the output says:

Checking for a new Ubuntu release
Failed to connect to [https://changelogs.ubuntu.com/meta-release](https://changelogs.ubuntu.com/meta-release). Check your Internet connection or proxy settings
No new release found.

EDIT:

I found the solution at [https://ubuntu-mate.community/t/cant-update-upgrade-anymore-um-18-04-v2-lts/19745/2](https://ubuntu-mate.community/t/cant-update-upgrade-anymore-um-18-04-v2-lts/19745/2)

After a bit of googling I simply edited the file "**/etc/update-manager/meta-release**" and changed the URI to use http instead of https so I changed:

```
URI = https://changelogs.ubuntu.com/meta-release
```

to

```
URI = http://changelogs.ubuntu.com/meta-release
```

This allowed me to upgrade to Kubuntu 20.10 normally.

---

### Post by Dennis N on 2020-10-23
You have to wait a week or two when moving to the next non-lts release. Software-updater will inform you when it's possible if it's configured to notify you of any new release. If you want it now, you have to do a new install.

---

### Post by nhasian on 2020-10-23
> **Dennis N said:**
> You have to wait a week or two when moving to the next non-lts release. Software-updater will inform you when it's possible if it's configured to notify you of any new release. If you want it now, you have to do a new install.

That is not correct. You can upgrade as soon as a new release is available. I believe what you are thinking of is that an LTS will not upgrade to a new LTS release until after the point release is available.

---

### Post by Dennis N on 2020-10-23
> **nhasian said:**
> That is not correct. You can upgrade as soon as a new release is available. I believe what you are thinking of is that an LTS will not upgrade to a new LTS release until after the point release is available.

Wow! You are correct. Got the notice this evening with today's (23 Oct). software updates.

UPDATE: Completed the upgrade using the Software Updater. Everything seems normal after restart. Total time 17 minutes. The updater window title reads "Updating Ubuntu to version 20.04" instead of 20.10, but the result is indeed 20.10.

---

