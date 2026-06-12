---
title: "Surface Book Pro 4 install ubuntu 18.04.2 on USB SSD and dump to grub shell"
date: 2019-02-27
forum: Installation &amp; Upgrades
---

### Post by shypwang on 2019-02-27
Hi,

Below is how I install:
MS surface pro 4 + usb hub + usb stick + usb SSD
1. downsload 18.04.2 amd 64iso
2. use rufus to burn the iso to usb stick, select gpt + uefi
3. boot from usb stick
4. install ubuntu on usb SSD
    a. sda1 ext4 mount to /
    b. sda2 swap
    c. install ubuntu and bootloader on sda1
5. boot from usb ssd, I cannot go into ubuntu but dump into grub shell

Can anybody help? What's the cause? Any mistake I made? How to solve?

Thanks,

---

### Post by oldfred on 2019-02-27
Did you install in UEFI boot mode?
The boot files will be on internal drive not on external drive. So external drive can only boot from this one system.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

