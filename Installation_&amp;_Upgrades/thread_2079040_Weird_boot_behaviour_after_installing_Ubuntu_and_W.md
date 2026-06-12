---
title: "Weird boot behaviour after installing Ubuntu and Win7 on separate hard disks"
date: 2012-11-01
forum: Installation &amp; Upgrades
---

### Post by zaibotrenktas on 2012-11-01
Hello,

I had Ubuntu 12.04 on sda. I decided to install Win7 on sdb. So I removed HDD with Ubuntu and installed Win7 on the another HDD. I also updated GRUB.

Both Win7 and Ubuntu can boot from the GRUB now. But after booting into Win7 I can't boot to them again from the GRUB unless I modify BIOS settings. I have to change HDD boot priorities in BIOS from (1st, 1st) to (1st, 2nd). By the way, 2nd HDD in BIOS is no longer shown with proper name. It's 'Unknown' now. After modifying BIOS like this, the HDD in BIOS is not recognized as 'Unknown' anymore and I can boot to Win7 from the GRUB.

Any help would be very appreciated. :)

---

### Post by darkod on 2012-11-01
Sounds like hardware/connectivity issue. The disk has to be recognized correctly in bios.

Double check the connections, cables, try it in another sata port, etc. Also, usually it's best to leave the windows disk in a lower sata port, so that it's /dev/sda, and the ubuntu disk in a higher port so that it's /dev/sdb. It doesn't matter much, but windows is often picky if not on the first disk.

---

### Post by zaibotrenktas on 2012-11-03
I switched disk in places. So that Windows is sda and Ubuntu is sdb. Still the same problem.

---

### Post by Tranas on 2012-11-03
> **zaibotrenktas said:**
> I switched disk in places. So that Windows is sda and Ubuntu is sdb. Still the same problem.

I have pretty much the same setup, but with XP on sda. Have 12.04/Grub on sdb and the bios has to be configured with sdb as the boot drive. To get XP as an functional option from the grub menu, you also have to write grub to the MBR on sda.

HTH

---

### Post by darkod on 2012-11-03
In general, you don't need grub on both disks. Only on the disk that you set up as first boot option.

Also changing the places of the disks is not crucial, but sometimes it's better for windows.

I still think your main issue is that one disk is showing as Unknown in bios sometimes. You need to investigate when does this happen. If any disk is not recognized in bios correctly, it's like it doesn't exist for the system. I would focus my efforts there.

The disks have to show up correctly without difference which OS you boot (use) and in which order are the disks connected to the board.

---

### Post by funicorn on 2012-11-03
Try this, make sure both sda and sdb are shown correctly in BIOS, then boot into Ubuntu
```

sudo grub-mkdevicemap

```
Reboot

---

