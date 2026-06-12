---
title: "Upgrade From 12.04 to 14.04 restart not successful"
date: 2015-03-17
forum: Installation &amp; Upgrades
---

### Post by Coemd on 2015-03-17
I am running a 64-bit Ubuntu 12.04 version on a virtual client being hosted on an ESXi server.  During the upgrade I ensure I kept original files "default" when asked.  The upgrade appeared to be complete and requested a restart to complete the upgrade.  When the VM attempted a restart, it came backup to a black screen and a "static" cursor in the left corner.  The machine appears to be powered on, however; I cannot get a ping response neither by IP or name and I am unable to make inputs via the console.

Any ideas?

---

### Post by Peter_van_Loenhout on 2015-03-17
Hi Coemd,

Reinstall GRUB:
Reboot the virtual machine with the Ubuntu 14.04 install image > Rescue a broken system >
Go through the questions that you get shown > menu 'Rescue operations': Reinstall GRUB bootloader.
This usually helps after upgrading from 12.04 to 14.04.

---

### Post by Coemd on 2015-03-17
Thank you very much for your assistance.  Reinstalling the bootloader was successful and the system was able to boot correctly and enable be to verify my upgrades.

[COLOR=#000000]Reinstall GRUB:[/COLOR]
[COLOR=#000000]Reboot the virtual machine with the Ubuntu 14.04 install image > Rescue a broken system >[/COLOR]
[COLOR=#000000]Go through the questions that you get shown > menu 'Rescue operations': Reinstall GRUB bootloader.[/COLOR]
[COLOR=#000000]This usually helps after upgrading from 12.04 to 14.04.[/COLOR]

---

