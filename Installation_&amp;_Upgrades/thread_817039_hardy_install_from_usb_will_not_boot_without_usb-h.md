---
title: "hardy install from usb will not boot without usb-hdd"
date: 2008-06-03
forum: Installation &amp; Upgrades
---

### Post by anparks on 2008-06-03
hi. i installed a minimum netinstall from my usb key, but i'm pretty sure the installation didn't write an mbr sector to my hdd, so now all my mobo will see is a bootable usb drive, while the hard drive is not bootable. ubuntu runs fine but won't boot without the usb key in the drive. what sort of script or app do i need to run to install a master boot record to my primary hdd?

---

### Post by anparks on 2008-06-03
i'll try when i get home but i think i might be able to just install mbr from the repositories and then edit grub. but i'll have to wait to get home from work to do this... if anybody has more direct sure-fire solutions please post!

---

### Post by louieb on 2008-06-03
> **anparks said:**
> ...but won't boot without the usb key in the drive...

When you installed Ubuntu on the usb key the installer did change the MBR to load the GRUB boot loader on the usb key. 

What you need to do will depend on what OS is on your hdd.  (Some type of windows OS I guess) 

You have a couple of options  my favorite [IDBS make a dedicated GRUB partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_")

OR replace the GRUB stage1 code with code that boots the OS on your hdd. [IDBS Remove/Replace/Uninstal Grub]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

In any case if you want to boot without the usb key inserted. Your right you will have to alter the MBR of the hdd.  
Regards,
lou

---

