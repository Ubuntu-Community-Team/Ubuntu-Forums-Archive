---
title: "Install of 9.10 on usb hdd"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by Allan Reed on 2010-01-07
I have a winxp set-up with two hard drives on a pci raid card. The drives are set as two ide drives, one system and one copy for backup. I would like to install 9.10 on a usb drive(40gig) but the installer will not give me any other choice than to partition the system hdd.
I have tried the 'Try Ubuntu' option from the setup menu and I can find all three drives in the disk management menu. Running setup from here will still only allow access to hdd0 - the system drive.
The usb drive appears in the bios as a boot option!

---

### Post by darkod on 2010-01-07
Did you try selecting the Erase and use whole disk option? Even if you don't want to proceed with that option, if you just temporarily select it, it should enable the drop down list beneath in which you can select the ext drive. Then choose another option if that's what you wanted, for example Manually partitioning.

---

### Post by C.S.Cameron on 2010-01-07
Is unplugging the internal drives while installing an option?

---

### Post by Allan Reed on 2010-01-07
Thanks Darko, that worked.
I was looking for a way to avoid unplugging if possible.

---

