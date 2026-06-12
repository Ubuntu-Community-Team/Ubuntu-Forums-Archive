---
title: "grub problem with multiple disks"
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by alenis on 2007-05-06
Hello
until yesterday I had two disks in my box, one with Xp installed, the other with Ubuntu. Ubuntu was on the default boot drive, so when I wanted to use XP I just selected the other disk as boot device in the bios.
Yesterday I installed a third HD and I put Kubuntu there.The problem is that now, no matter which drive I select from the bios menu, the same Grub menu shows, and it has the Kubuntu installation as the default choice. I would like to revert to the previous situation. I tried fixmbr and fixboot on the XP disk and grub-install on the Ubuntu disk, but still the same grub menu (the one Kubuntu installed on its disk) always shows up, no matter which disk I boot from.
I searched the forum and googled a lot to no avail. Please help!
Thank you
Alessandro

---

### Post by derrekito on 2007-05-06
You can actually just edit the grub config file.  

[http://www.gnu.org/software/grub/manual/html_node/](http://www.gnu.org/software/grub/manual/html_node/)

This link might help you out.

---

### Post by alenis on 2007-05-07
I checked the documentation but I couldn't find any solution. It seems that the installation of Kubuntu overwrote the MBR in every disk in the system.  Ichecked the MBR of the Windows disk with hexedit and actually I found grub there. I tried again fixmbr from the Windows repair console with no results.

---

### Post by derrekito on 2007-05-07
> **alenis said:**
> I checked the documentation but I couldn't find any solution. It seems that the installation of Kubuntu overwrote the MBR in every disk in the system.  Ichecked the MBR of the Windows disk with hexedit and actually I found grub there. I tried again fixmbr from the Windows repair console with no results.

EEEK sounds like you got owned.  If the MBR is screwy, you might have to reinstall grub... or however they do it, run the grub thing again to overwrite the MBR.  I don't know how to do this outside of a new installation.

---

