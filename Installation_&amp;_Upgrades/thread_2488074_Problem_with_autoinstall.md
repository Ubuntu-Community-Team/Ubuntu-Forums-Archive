---
title: "Problem with autoinstall"
date: 2023-06-22
forum: Installation &amp; Upgrades
---

### Post by Jaxilian on 2023-06-22
Hi all

I have this autoinstall config, but it doesn't work. I can't find enough examples to figure it out. I hope someone here can help.
I wanna install from a local repository on the actual usb-drive (ot copied down to drive). Tried below, but doesn't do the part under late-commands at all, but completes the autoinstall so that works.
The "--force-overwrite" is there cause of that package cannot be installed without it.

```
#cloud-config
autoinstall:
  version: 1
  identity:
    hostname: ubuntu-host
    username: ubuntu
    password: -
  keyboard:
    layout: se
  locale: sv_SE.UTF-8
  timezone: Europe/Stockholm

late-commands:
  - apt update
  - cp -r /cdrom/nocloud/packages/ /target/usr/local/
  - apt -o Dpkg::Options::="--force-overwrite" install -y /usr/local/packages/package.deb
```

---

