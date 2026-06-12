---
title: "Attention: Toshiba Tecra A4 Users"
date: 2006-06-16
forum: Installation &amp; Upgrades
---

### Post by Gtaylor on 2006-06-16
If your ethernet/USB are broken at time of install, see the "Restoring Network/USB (Dapper)" section of the Tecra A4 wiki page.

[http://wiki.ubuntu.com/LaptopTestingTeam/ToshibaTecraA4](http://wiki.ubuntu.com/LaptopTestingTeam/ToshibaTecraA4)

This will happen until they either publish a new install image or Edgy is released. The basic gist of it is, if you're running BIOS 1.60, upgrade to 1.70. If that doesn't work, boot with the irqpoll option and you should be able to stay connected long enough to download the latest kernel, which fixes ethernet connectivity issues. Ubuntu will force pci=noacpi on any Tecra A4 running BIOS 1.60, causing the USB issue, and probably the ethernet problem as well.

---

### Post by Gtaylor on 2006-07-29
I should have titled this "Attention Tecra owners" as it appears this problem expands beyond the A4.

---

