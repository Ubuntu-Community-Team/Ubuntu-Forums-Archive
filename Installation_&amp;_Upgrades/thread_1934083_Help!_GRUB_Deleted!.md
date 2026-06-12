---
title: "Help! GRUB Deleted!"
date: 2012-03-01
forum: Installation &amp; Upgrades
---

### Post by amtur_poet on 2012-03-01
I have been trying to get dual-booted Ubuntu running on my computer since I got it, and now I really need help. I screwed up my attempt to upgrade to 11.10, so I deleted my Linux partition on my computer, but that had the GRUB bootloader on it, and now whenever I start up my computer, it boots to a GRUB rescue command prompt, and I can't run Windows. What do I do? It gives me an error saying "no such device". Help! :'(

---

### Post by darkod on 2012-03-01
Do you have the windows install disc or rescue cd?

---

### Post by amtur_poet on 2012-03-01
No, my computer didn't come with one. Is there anywhere I can get a recovery disc?

EDIT: Actually, my computer came with a recovery partition, not a disc... Not that that is helpful now.

---

### Post by amtur_poet on 2012-03-01
Is there any way to reinstall GRUB alone? I can't get Ubuntu to install, because it keeps whining about a partition not being a root partition, so that's out of the question.

---

### Post by darkod on 2012-03-01
No, you can't install only grub, it has to have configuration files to work with. When you deleted the ubuntu partition you deleted those files.

The no root partition specified message is showing up when you are using the manual method to install but are not specifying which partition to use as root partition (mount point / ). If you want to reinstall ubuntu, simply make sure you specify a root partition to install onto.

There is way to install generic MBR from ubuntu live mode which should boot your windows if the boot flag is still set correctly. You can do this by booting with the ubuntu cd in live mode and in terminal:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

If your disk is not /dev/sda, change above to /dev/sdb, /dev/sdc, etc. In most cases with only one hdd, it's /dev/sda. Those commands will issue a warning about lilo configuration, just ignore it. It will work.

After that the computer should boot windows directly. Whether you install ubuntu once more is up to you.

---

### Post by amtur_poet on 2012-03-01
Thank you very much. All I needed to do was select the mount point, as you suggested. :)

---

