---
title: "Installing firefox translations with unattended upgrades"
date: 2012-03-01
forum: Installation &amp; Upgrades
---

### Post by MrHara on 2012-03-01
Hi,

We have ubuntu 10.04 machines that are running unattended-upgrades from a custom repository, and firefox is now being upgraded from 3.6 to 10.02. The problem is, that after the upgrade, firefox loses the finnish translation that it had before. It seems that an additional language pack is needed for firefox 10.02, firefox-language-fi. After installing this package manually, the translation works as intended. I think the translations for firefox 3.6 were in gnome language packs.

If i've understood correctly, unattended-upgrades can't do a dist-upgrade and install new packages, only update old ones. Is there a way we can install a new package (firefox-language-fi) with unattended-upgrades? One other solution I've thought about is to give up using unattended-upgrades, and place a dist-upgrade script in cron, so this sort of problem wouldn't occur again.

---

