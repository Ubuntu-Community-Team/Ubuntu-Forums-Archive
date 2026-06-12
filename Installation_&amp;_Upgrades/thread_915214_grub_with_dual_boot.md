---
title: "grub with dual boot ?"
date: 2008-09-09
forum: Installation &amp; Upgrades
---

### Post by bradw on 2008-09-09
I have read many posts here and I cannot find one addressing my ?. I am so tired of windows and want to dual boot to hardy 8.04.1. Lets say everything goes well and grub works well with dual booting. Now lets say I have a / partition, a home partition and a swap. Now I want to delete the / partition and install hardy 8.10 when it comes out. I assume I just delete root and recreate it and load 8.1. Ok now what happens to grub. When I delete the root, recreate it and reinstall is grub affected at all. I am so tired of reinstalling everything and this is a major reason Im going to switch to ubuntu. Is grub in the root so when I delete the root partition and recreate it to reload the 8.1 version have I hosed myself. If not what do I do when I get to the screen to install.load grub in one of the advanced screens. Do I reload it, uncheck or what.

thanks

Brad

---

### Post by mikewhatever on 2008-09-09
Grub gets reinstalled too. While being reinstalled, it should redetect other OSs and add them to the menu. There is nothing special you'll need to do.

---

### Post by bradw on 2008-09-09
> **mikewhatever said:**
> Grub gets reinstalled too. While being reinstalled, it should redetect other OSs and add them to the menu. There is nothing special you'll need to do.

thanks and here I go

---

### Post by mr.moch on 2008-09-09
When 8.10 comes out, you can always use the Update Manager in Ubuntu itself.  It'll download the update for you, and you don't have to do anything else!

---

### Post by zvacet on 2008-09-09
Or you can upgrade with alternate CD.Result will be the same as upgrading with update manager,but you wil allways have CD if you need it.Just an option.

---

