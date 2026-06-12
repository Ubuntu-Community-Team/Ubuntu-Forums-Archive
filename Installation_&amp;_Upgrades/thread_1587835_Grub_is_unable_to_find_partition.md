---
title: "Grub is unable to find partition"
date: 2010-10-04
forum: Installation &amp; Upgrades
---

### Post by walterwerner on 2010-10-04
I have a 9.10 ubuntu desktop on a tower (bought 2004) working fine, and wanted to add a 10.4 server on an additional partition. After install, I stated grub may be newly written, as the list of os was fine. After reboot I got "grub rescue>"

I managed to get the system working again, and now I have a grub2 menu list stating correct entries. But when I select the server entry the boot fails telling "disk not found" (The UUID of the partition given is correct, and also shown when accessing the partition from the 9.10 desktop (this needs an additional authentification when mounting)

grub shell command ls does not show the partition, all other tools (life-CD, working installation, gparted etc.) do show it normally, I cannot find any difference.

The partition is on the beginning of the disk

Please help! I have no idea what might be wrong, and where to put the next step.

Walter.

---

### Post by ajgreeny on 2010-10-04
When you get into the OS which is supplying the grub menu (is that the server you just installed?) run ```
sudo update-grub
``` to see if that helps.

If you are not sure which OS grub is from when you boot, simply get into your 9.10 OS and run the same update-grub command from that.  It should find the server for you and allow you to boot it with no problem.

---

### Post by walterwerner on 2010-10-04
Grub was after the server install on the server partition, and this lead to complete failure ("grub rescue>"). 
Now grub is (again) on the 9.10 partition, grub updatet to newest code, also update-grub was done, (this detected the server installation and created two menu items!), but when I select this menu item grub cannot find the partition.
What strikes me is that I do need additional authentification (it says "protected file-system", maybe this is "server-default") when mounting this partition from the 9.10 system.

Walter

---

### Post by walterwerner on 2010-10-06
I finally identified the problem! The bios only shows the first of two jbod drives an the raid controller. Therefore there is no way to start an os on any partition of this drive. The drive is well seen once the os is up nd running....
I still have no clue what to do, but this is more a bios trouble than a grub or Ubuntu one. "solved" is not correct, but finished.

Thanks to all supporters!

---

