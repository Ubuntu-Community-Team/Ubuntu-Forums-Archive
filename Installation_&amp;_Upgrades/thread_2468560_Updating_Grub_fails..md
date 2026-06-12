---
title: "Updating Grub fails."
date: 2021-11-03
forum: Installation &amp; Upgrades
---

### Post by elmurdoque on 2021-11-03
I have multiple Drives in my system. The boot drive has Ubuntu 21.04 installed. 
I recently made some changes to my hardware and this entailed a new setup of GRUB. 

My Windows 10 install has disappeared from the boot menu in that process. 
The drive is still there and it's still working, only updating grub does not add it to the boot menu: 

```
root@zap:/# os-prober 
/dev/sdb1@/efi/Microsoft/Boot/bootmgfw.efi:Windows Boot Manager:Windows:efi
root@zap:/# 
root@zap:/# 
root@zap:/# update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.11.0-38-generic
Found initrd image: /boot/initrd.img-5.11.0-38-generic
Found linux image: /boot/vmlinuz-5.11.0-37-generic
Found initrd image: /boot/initrd.img-5.11.0-37-generic
Found linux image: /boot/vmlinuz-4.13.0-37-generic
Found initrd image: /boot/initrd.img-4.13.0-37-generic
Found linux image: /boot/vmlinuz-4.13.0-36-generic
Found initrd image: /boot/initrd.img-4.13.0-36-generic
Found Windows Boot Manager on /dev/sdb1@/efi/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings
done
root@zap:/# 
```

As far as my knowledge reaches, the shown output means that both os-prober and update-grub can see the Windows system on /dev/sdb, but for some reason I cannot fathom, a reboot only shows The Ubuntu options and the UEFI Firmware entry in the boot menu.

---

### Post by oldfred on 2021-11-03
Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by yancek on 2021-11-03
Using boot repair suggested above by oldfred would get the most complete information so I would agree with that.

I see your windows 10 is on sdb and your windows EFI partition is on sdb1.  I you mount sdb1 under /boot/efi, check to see if you have an ubuntu directory there.  Do you have another OS other than Ubuntu and windows?  It would be helpful if you indicated what changes to your hardware were made?  And why would that entail a new Grub setup?  I guess these questions and more will be answered if you post the output of boot repair suggested by oldfred.

---

### Post by VMC on 2021-11-03
Also ```
lsblk -f
``` would show where the efi and all your installs are located.

---

