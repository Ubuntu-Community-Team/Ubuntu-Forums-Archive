---
title: "Upgrading Breezy server to Dapper?"
date: 2006-10-14
forum: Installation &amp; Upgrades
---

### Post by jolt256 on 2006-10-14
I have a server that's happily running Breezy, but I'd like to upgrade it to Dapper. Since it's a headless server, it doesn't have {x,k}ubuntu-desktop installed (I have no use for X or GNOME/etc on this machine), but all the dist-upgrade guides insist that one of these desktop metapackages is necessary. Is there any way to do an upgrade without either installing one of these or going with a clean install?

---

### Post by taurus on 2006-10-14
Just edit your /etc/apt/sources.list and replace breezy with dapper.

```
sudo nano /etc/apt/sources.list
```
Save it and then upgrade it away...

```
sudo aptitude update
sudo aptitude dist-upgrade
```

---

