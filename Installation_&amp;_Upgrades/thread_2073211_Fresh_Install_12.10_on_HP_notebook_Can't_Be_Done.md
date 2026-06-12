---
title: "Fresh Install 12.10 on HP notebook Can't Be Done"
date: 2012-10-19
forum: Installation &amp; Upgrades
---

### Post by wildabdat on 2012-10-19
i try installing 12.04 yesterday, and get some problem with ATI AMD graphic drivers, some solution that i found didn't solve it. so i download the 12.10 64 bit version since its already listed everywhere. . now it can't be installed at all, installation freez from the beginning when you choose "Install Ubuntu"...

i've tried nomodeset  and other options.. still no luck. moreover i get something like this on the screen when try to use ACPI=OFF options 
> udev (1111): timeout: killing '/sbin/modprobe -bv pci

my notebook is HP Pavilion g4-1214tx
graphic :  AMD Radeon HD 6470M (1 GB DDR3 dedicated)
Memory : 8 Gb
Proc :  core i5
and so...

do you guys have a suggestions?

Thank You

---

### Post by 2F4U on 2012-10-19
When the installation freezes, it is often due to a corrupt download or a bad burn. Did you verify the checksum of the downloaded iso image? Did you install from USB or DVD?

---

### Post by wildabdat on 2012-10-19
> **2F4U said:**
> When the installation freezes, it is often due to a corrupt download or a bad burn. Did you verify the checksum of the downloaded iso image? Did you install from USB or DVD?

thought it so, but then i installed it on vmware virtual machine... smooth,  no froze or anything bad happen... 

thanks

---

### Post by darkod on 2012-10-19
If I remember correctly, nomodeset is usually for nvidia.

For ATI there was a parameter like radeon.modeset=1 or radeon.modeset=0. Not sure if this is a video issue, but you can give that a shot.

Also, try to boot in live mode first (Try Ubuntu), don't install right away. Booting into live mode lets you see whether it will boot correctly, or what parameters you need so that it boots correctly.

Once you know the parameters, it's easy to use them on first boot after the install because probably you will have to.

---

