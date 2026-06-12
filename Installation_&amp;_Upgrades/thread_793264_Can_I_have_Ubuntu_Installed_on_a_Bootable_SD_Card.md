---
title: "Can I have Ubuntu Installed on a Bootable SD Card"
date: 2008-05-13
forum: Installation &amp; Upgrades
---

### Post by yogiman_uk on 2008-05-13
Hi Everyone...

I have a Toshiba Tecra M5-390 which comes with an SD Card slot as standard.

I would like to have a bootable SD card containing the latest version of Ubuntu.

However having installed ubuntu to a 4GB card everything went fine but once installed it did not ask me to shutdown or reboot.

Attempting to boot from the SD card fails.  No errors it just doesn't see it as a bootable device.

Can anyone help with this problem, suggestions welcome.

thanks for any help.

Yogiman!

---

### Post by Pumalite on 2008-05-13
How is the SD card seen in your computer?. Post:
sudo fdisk -l

---

### Post by Rallg on 2008-05-13
Are you sure that your computer can boot from SD (asuming that your SD card really is bootable)?

My computer, a different model, will boot from USB or from some kinds of "removable media," but not from its built-in SD slot. Possibly that's because the SD hardware driver is not loaded by BIOS.

---

