---
title: "required boot option for installation from usb drive"
date: 2011-09-19
forum: Installation &amp; Upgrades
---

### Post by 2lid8xh2o8 on 2011-09-19
I need help adding a boot option to the kernel's boot line to start the installation process. I've never dealt with boot options before, and it seems like all the resources for adding boot options to a kernel's boot line is for an installation of Grub that already exists. Since, I'm installing a fresh install, there is no Grub installation that I'm aware of, correct me if I'm wrong.

This is the boot option: cdrom-detect/try-usb=true

I've used Unetbootin to create a bootable usb drive to install Ubuntu Server 10.4.3 LTS. The server I'm using doesn't have a CD drive. Since the installation isn't via CD, the installation process gets stopped because its looking for a non-existant CD drive (instead of a USB drive) to install from. To get around this, I've used this guide: [http://blog.smalleycreative.com/linux/fix-for-ubuntu-10-04-server-usb-install/#comment-294](http://blog.smalleycreative.com/linux/fix-for-ubuntu-10-04-server-usb-install/#comment-294) The boot option mentioned above is part of the solution in the guide.

---

