---
title: "ubuntu iso image diffrences"
date: 2023-07-28
forum: Installation &amp; Upgrades
---

### Post by Dark Charizy on 2023-07-28
hi what's the difference in the the ubuntu iso images since there a 23.04 and a 23.04 legacy?

---

### Post by tea for one on 2023-07-28
Ubuntu 23.04 has the new installer.
Ubuntu 23.04 legacy has the older version.
More info [https://www.omgubuntu.co.uk/2023/04/ubuntu-23-04-released](https://www.omgubuntu.co.uk/2023/04/ubuntu-23-04-released)

---

### Post by guiverc on 2023-07-28
If you choose the same installation options on both, on the same hardware the installation should be identical regardless of which ISO you downloaded & used.

The different in ISO as *tea for one* said, is just the installer that exists on that ISO.

The *default* ISO **for Ubuntu Desktop** now includes the new *ubuntu-desktop-installer*, where for releases of 19.10 through 22.04 the *alternate* ISO included it where it was called the *canary* installer.

The *alternate* ISO has a new name with 23.04, and is called the *legacy* ISO and uses the *ubiquity* installer, that was the default installer for prior releases.

If you have hardware that the new installer has trouble with, you've a backup ISO with different installer you can use.

One benefit of the newer installer, is that it's not *static* on the ISO, but once booted, if you have *internet* available, it can *upgrade* itself whilst its running, meaning it can get fixes to itself prior to your install.  This does require internet though.

FYI:   If you didn't notice the *alternate* ISOs for prior releases; as it was still a *canary* installer the download of it wasn't exactly highlighted, nor kept for long, but it was there if you looked (*on the ISO QA tracker; intended for testing/QA mostly*).

---

