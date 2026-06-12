---
title: "Ubuntu refusing to install"
date: 2007-02-14
forum: Installation &amp; Upgrades
---

### Post by al1b1 on 2007-02-14
I have just got a new 160Gb hard drive and want to let ubuntu  use it. THe install goes fine but when i restart the computer it comes up with this error "DISK BOOT FAILURE PLEASE INSERT SYsTEM DISK AND PRESS ENTER". In gparted it says the partitons are all there fine. I have installed ubuntu on that computer before with an 80Gb hard drive that dual boots with windows

---

### Post by renzokuken on 2007-02-14
it sounds to me like your mobo is reading the new drive as master and trying to boot (searching for grub) from the new drive. your drive with the ubuntu install has probably been pushed back to slave

you can either switch the jumper settings or change the boot device order in your bios

---

### Post by al1b1 on 2007-02-14
the 160 gb is the only hard drive running currently and my bios reads it as the primary so i doubt  that is the problem

---

### Post by housam on 2007-02-14
Reinstall grub , it maybe the problem : [http://doc.gwos.org/index.php/Restore_Grub]("http://doc.gwos.org/index.php/Restore_Grub")

---

### Post by al1b1 on 2007-02-23
Anybody still here, i tried using super grub boot disk to reinstall, restore grub to no avail and tried setting up but was plagued with errors any help or definitive howtos on reinstalling grub?

---

