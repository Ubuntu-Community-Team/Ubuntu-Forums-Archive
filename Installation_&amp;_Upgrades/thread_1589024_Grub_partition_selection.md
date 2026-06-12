---
title: "Grub partition selection"
date: 2010-10-05
forum: Installation &amp; Upgrades
---

### Post by rshol on 2010-10-05
Installing 10.10 RC dual boot with Win7.  Is there no place in the installer to specify where Grub will be installed?  I don't want it installed in the MBR I want it in the partition with / (I usually only create two partitions for Linux / and swap). I prefer to chain load grub from my windows bootloader.

---

### Post by wilee-nilee on 2010-10-05
> **rshol said:**
> Installing 10.10 RC dual boot with Win7.  Is there no place in the installer to specify where Grub will be installed?  I don't want it installed in the MBR I want it in the partition with / (I usually only create two partitions for Linux / and swap). I prefer to chain load grub from my windows bootloader.

The choice for grub placement is at the bottom of the first partitioning window in the install.

Are you able to chainload grub2, without a 3rd party helper like easbcd2

---

### Post by rshol on 2010-10-05
No I will be using easybcd to chainload.  Thanks for the information.

---

### Post by wilee-nilee on 2010-10-05
> **rshol said:**
> No I will be using easybcd to chainload.  Thanks for the information.

Cool, I just didn't want to miss any different methods.

---

### Post by psusi on 2010-10-05
You can have windows chain load grub2 the same way it chain loads anything:  you copy the boot sector to a file and add an entry to boot.ini to chain load that file.

---

