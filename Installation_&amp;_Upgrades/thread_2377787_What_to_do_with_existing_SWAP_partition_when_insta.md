---
title: "What to do with existing SWAP partition when installing Artful"
date: 2017-11-16
forum: Installation &amp; Upgrades
---

### Post by kansasnoob on 2017-11-16
This is probably a dumb question but I haven't found an answer (either smart or dumb), but if you're manually reinstalling Ubuntu in a multi-boot arrangement what's the proper thing to do with the existing SWAP partition that's shared with other distros? Typically you'd do NOTHING and the installer automatically "sniffs out" all existing SWAP partitions and uses them with the fresh install.

Now that Artful uses a SWAP file rather than a SWAP partition I'm not sure if I should mark the SWAP partition "do not use" or just leave it alone. Will it choose to use that SWAP partition rather than use the SWAP file? Or would it use both? I guess I could just give it a try and see what happens. It wouldn't kill me to do some experimenting, but I thought it couldn't hurt to ask.

---

### Post by howefield on 2017-11-16
> **kansasnoob said:**
> ... Typically you'd do NOTHING and the installer automatically "sniffs out" all existing SWAP partitions and uses them with the fresh install.

That is what would happen, should a swap partition exists then 17.10 will use it and won't create a swap file.

---

### Post by kansasnoob on 2017-11-16
> **howefield said:**
> That is what would happen, should a swap partition exists then 17.10 will use it and won't create a swap file.

Cool, that seems sensible.

---

