---
title: "reintalling ubuntu - dual boot with vista"
date: 2010-01-17
forum: Installation &amp; Upgrades
---

### Post by kannandv on 2010-01-17
Hi All,

I have a pc with dual boot ubuntu with vista os.
I need to re-install ubuntu without affecting vista.
i searched google, but i cant understand the loader functions!.
So any one please guide me to re-install ubuntu in my PC.

Regards,
Kannan DV

Note :i need either - step by step notes or any links that guide me to uninstall ubuntu.;)

---

### Post by audiomick on 2010-01-17
I think that if you just run the installer, maybe with manual partitioning, it will allow you to choose to install into the partitions where the old Ubuntu is.

If you want to do it "step by step", boot into the live cd and start gparted
system> administration> gparted
and delete the existing Ubuntu partition(s)

If you have /home on a separate partition, you can leave it alone and re-mount it without re-formatting during the install. This will retain your data and personal settings. If you don't have /home on a separate partition, you might consider installing that way so that this possibility is available in the future.

Once the old Ubuntu is removed, install into the empty space.

---

