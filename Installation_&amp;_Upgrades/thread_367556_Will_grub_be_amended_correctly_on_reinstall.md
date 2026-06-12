---
title: "Will grub be amended correctly on reinstall?"
date: 2007-02-22
forum: Installation &amp; Upgrades
---

### Post by wej1971 on 2007-02-22
I've just about to reinstall Kubuntu and currently my grub menu has lots of options, 2 for each of my current kernel ubuntu installs and the other is WIndows XP.

If I do a clean install of Kubuntu onto the original linux partition, will the old menu options be removed from grub automatically?

---

### Post by MikeDX on 2007-02-22
Yes they will. if you wipe off your old linux install then you will be left with new options related to your new linux installation and an option for "microsoft operating system"

---

### Post by Kateikyoushi on 2007-02-22
Your grub menu is stored in your /boot/grub so if you have it in / and going to reinstall the partition what most likely you will do during the reinstall all those option will disappear.

By the way you could just remove the unused kernels from the system for example with synaptic and the boot options will be removed as well.

---

### Post by louis_nichols on 2007-02-22
If you make a clean install of Kubuntu, erasing the entire partition, I think the best idea is to format the boot partition. If your boot folder is on the Linux partition, there's nothing to worry about. The menu will be re-created from scratch anyways.

---

### Post by wej1971 on 2007-02-23
And funnily enough that's what it did!

I love Linux sometimes :) (I just wish it was all the time - wireless networking is getting my goat atm)

---

