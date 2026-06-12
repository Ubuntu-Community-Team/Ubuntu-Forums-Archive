---
title: "How do I install xbuntu to an external HDD"
date: 2013-02-28
forum: Installation &amp; Upgrades
---

### Post by snowlizard31 on 2013-02-28
I have a 500gb my passport external HDD and I have partitioned it to have a usb install for xbuntu so i can install xbuntu on the other partition how do I setup the partition on xbuntu so I can use the 
other partition. I've tried install it but it says no root directory selected. but it looks like theres no option to select one it has an option for mount point and I selected /dos

---

### Post by presence1960 on 2013-02-28
> **snowlizard31 said:**
> I have a 500gb my passport external HDD and I have partitioned it to have a usb install for xbuntu so i can install xbuntu on the other partition how do I setup the partition on xbuntu so I can use the 
other partition. I've tried install it but it says no root directory selected. but it looks like theres no option to select one it has an option for mount point and I selected /dos

Mount point should be " / "

To be safe you should disconnect your internal disk so GRUB gets installed to external drive. You can install to external with internal disk connected, but you must select the external disk from the drop down box asking where to install boot loader. If you are not versed in ubuntu installs I would disconnect the internal disk to be 100% sure you don't foul up your internal disk MBR or any partitions/data. Once install finishes reboot, go into BIOS and set your external USB as first device to boot in boot order. Save changes and exit BIOS. This will accomplish two things for you: When the external is connected at boot you will get the GRUB menu to boot ubuntu, if your external is not connected your OS(s) on your internal will boot as they normally do.

---

### Post by snowlizard31 on 2013-03-01
Thanks!!

---

