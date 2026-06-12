---
title: "Install problems"
date: 2014-12-03
forum: Installation &amp; Upgrades
---

### Post by rymar on 2014-12-03
This is my setup Asus sabertooth X79 Mobo, 12 GB Ram, two SSD's two SATA HDD's, two Nvidia cards
This is the issue(s) I'm having;

Installed Windows 7 to first SSD Samsung 240 GB, Ubuntu to second SSD. Intel 180 GB. UEFI is on for both drives. Installation is auto and proceeds just fine, finshes and boots into Ubuntu 14010 no problems.
Now when I reboot it boots into Ubuntu no option for Windows. After it's up and running the only drives visible are the Ubuntu partitions. No Windows no HDD's. Now my 3 Tb Hdd is dynamic and I understand that this is another issue, however the Other Hdd isn't but remains inaccessible. Gparted can see all of them but file manager can't. If I switch boot drives in the BIOS I can boot from Windows. This problem has been driving me crazy for some time now. I have worked with Ubuntu for a number of years but this has me stumped. 

I'm going to make one more attempt by setting the BIOS to non-secure and try installation by using "something else" if that doesn't work I'm going to throw in the towel until this problem is solved.

---

### Post by veddox on 2014-12-04
Just some suggestions:

Have you set up your fstab to automount the HDDs?

Run "sudo update-grub", that will at least tell you if GRUB can see the Windows drive. I would also have a look at /etc/default/grub, perhaps the option GRUB_TIMEOUT is set to 0 or something like that. (The latter would mean that GRUB doesn't wait at all for you to choose which OS you want to boot, but goes straight to the default.)

---

