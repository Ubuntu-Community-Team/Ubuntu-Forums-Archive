---
title: "shpchp: shpc_init: cannot reserve MMIO region"
date: 2010-04-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by wbar2 on 2010-04-21
Does anyone know what the following means?

```
shpchp 0000:00:01.0: Cannot reserve MMIO region
```

After the grub menu I get a flashing cursor for at least 10-15 seconds and then that message. Then it seems like everything begins to actually boot.

I didn't get this message in Karmic, but I get it in Lucid.

Here's all the lines with shchp in dmesg:

```
[   14.591293] shpchp 0000:00:01.0: HPC vendor_id 1022 device_id 9602 ss_vid 0 ss_did 0
[   14.591293] shpchp 0000:00:01.0: Cannot reserve MMIO region
[   14.591293] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4

```
I'm guessing the error has to due with my video card.

---

### Post by Souris on 2010-04-22
Same problem here:(:(

---

