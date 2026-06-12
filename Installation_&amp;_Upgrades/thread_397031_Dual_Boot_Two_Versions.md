---
title: "Dual Boot Two Versions?"
date: 2007-03-30
forum: Installation &amp; Upgrades
---

### Post by AlanRogers on 2007-03-30
I'm happy on Dapper and like the whole LTS scenario but I'm curious about the improvements available in Edgy (and Feisty when launched) but I only have one machine.

Is it possible / advisable / worthwhile installing Edgy as a Dual Boot on my existing Dapper install? I'll use PartImage to take a backup first because I need the machine to work.

---

### Post by tonym on 2007-03-30
Its certainly possible to Dual boot and is a good idea if you want to try things out - I once had my machine quintuple boot  -  don't ask!  An alternative would be to use an emulator such as qemu or vmware.

Its easy to set up once you have a partition to install to.  When you install,  avoid installing grub to the MBR,  instead install to the partition holding /boot.  Then amend the grub config of your main distribution and add an entry at the bottom pointing to the secondary /boot using the config example for Windows.

Regards

Tony.

---

