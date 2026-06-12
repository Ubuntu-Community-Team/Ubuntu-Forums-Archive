---
title: "Help installing kernel module for SAS card drivers"
date: 2011-10-18
forum: Installation &amp; Upgrades
---

### Post by ohboyotero on 2011-10-18
Hey guys, I got an SAS card for my media server and need to get its drivers installed and working.

My machine is running Ubuntu 11.04 LTS (desktop).

The problem is that the instructions they give don't seem to apply on late-gen Ubuntu. Here are the instructions verbatim:


```
**********************************************************************************
** 2. Compile and install arcmsr RAID driver on the running system              **
**********************************************************************************
        Notice!! Before all of steps below, please make sure there are complete development tools in your system.
        If not, the driver module can not be built successfully.
        2.1 make binary driver file,
                #make
        2.2 insert the driver on your system,
                #insmod arcmsr.ko,
        2.3 if you need the driver being inserted automatically after every reboot,
                make a new initrd image with the driver as following steps.
        Example:
                #cp arcmsr.ko /lib/modules/`uname -r`/kernel/drivers/scsi/arcmsr/
                #vi /etc/modprobe.conf, and add "alias scsi_hostadapter arcmsr"
                #mkinitrd -f -v /boot/initrd-2.6.18-8.el5.custom.img 2.6.18-8.el5
        2.4 Add new items for new kernel into /boot/grub/grub.conf, and designate new kernel
                as the bootup default item,
                #vi /etc/grub.conf
                Example:
                @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
                @ default=0
                @ timeout=5
                @ ......
                @ title Red Hat Linux (2.6.18-8.el5)custom
                @       root (hd0,0)
                @       kernel /vmlinuz-2.6.18-8.el5-custom ro root=/dev/sda1
                @       initrd /initrd-2.6.18-8.el5-custom.img
                @ title Red Hat Linux (2.6.18-8.el5)
                @       root (hd0,0)
                @       kernel /vmlinuz-2.6.18-8.el5 ro root=/dev/sda1
                @       initrd /initrd-2.6.18-8.el5.img
                @ ......
                @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
        2.11 Reboot,
                #shutdown -r now

```

I don't even have mkinitrd available on my machine and I can't get it from aptitude. I'm not sure whether I need both insmod and modprobe, as at least based on my quick read, they seem to do the same thing (install a module in the kernel).

Could somebody who knows how to install a kernel module get back to me about the best way to do this in Natty?

***One more thing:*** How do I set it up so that the module auto-loads on boot?

Thanks very much!

---

### Post by ohboyotero on 2011-10-18
Bump?

---

