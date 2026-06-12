---
title: "[SOLVED] Upgrade to Gutsy fails - File not found"
date: 2007-12-20
forum: Installation &amp; Upgrades
---

### Post by The Foz on 2007-12-20
I just tried to upgrade from Feisty (7.04) to Gutsy (7.10) using the Update Manager.

It fails with the following message:
Failed to fetch [http://www.albertomilone.com/drivers/feisty/latest/32bit/binary/Packages.gz](http://www.albertomilone.com/drivers/feisty/latest/32bit/binary/Packages.gz) 404 Not Found

Sure enough, this file does not exist.

I would like to know if there is a work-around for this. I am pretty certain that I have the latest drivers that I need, anyway.

I must say that I am rather surprised to find that an official Ubuntu Linux release is dependent on the contents of someone's private web-site, rather than an official repository.

---

### Post by linuxwizard on 2007-12-20
Remove or disable all extra repos[COLOR="Red"] YOU[/COLOR] added to your source list than try upgrading again.

Using packages from repositories not controlled by Ubuntu is not recommended as it can be a security risk and may break or [COLOR="DarkOrange"]complicate your upgrade.[/COLOR]

---

