---
title: "Can't boot usb"
date: 2019-09-23
forum: Installation &amp; Upgrades
---

### Post by xdontstarve on 2019-09-23
Hello, I'm new here so I don't know how things work here. But j need some help.
I burned the Ubuntu 18 L version on a DvD, then I booted from that and installed Ubuntu on my another usb (so I don't have to use live version), I followed this tutorial: [https://www.fosslinux.com/10212/how-to-install-a-complete-ubuntu-on-a-usb-flash-drive.htm](https://www.fosslinux.com/10212/how-to-install-a-complete-ubuntu-on-a-usb-flash-drive.htm)
The installation went great, but when I try to boot with the usb the system won't load it just shows a "_" popping out and off, it's been like that for half an hour now. I don't know what to do please help me

---

### Post by xdontstarve on 2019-09-23
If you guys don't know what am I tryna to, I'm trying to do this:
Install Ubuntu in a usb so I can use it anywhere and with the files saved in the usb (not live version). I'm using a DvD for the installation and a SanDisk Ultra 32GiB memory stick, if you guys know how to install it properly or how to fix it please it'd be grateful if you helped me ):, i need it for tomorrow school and I'm already about to sleep ;-;

---

### Post by CatKiller on 2019-09-23
> **xdontstarve said:**
> The installation went great, but when I try to boot with the usb the system won't load it just shows a "_" popping out and off, it's been like that for half an hour now. I don't know what to do please help me

I have no idea if it's the cause of your issue, since you've not given any details of your hardware, but that symptom shows up when you're trying to boot on a machine with Nvidia graphics without having the Nvidia proprietary drivers. If that is the case, you can edit your boot line from the Grub menu and replace "quiet splash" with "quiet splash nomodeset"

That would mean that you'd be able to boot successfully, but you may well only have a low-resolution display.

---

### Post by xdontstarve on 2019-09-23
Nevermind i think the problem is that I installed the boot file in the hard drive and not in the usb, I am trying to install it again now with an ego partition and without the HDD connected, will it work? Also how much space does the efi partition and the swap need?

---

### Post by yancek on 2019-09-24
Efi partitions are usually 200MB and an Ubuntu install will use a swap file rather than a swap partition.  If you want an EFI bootable usb, you need to create the EFI partition on the usb before installing.

---

### Post by xdontstarve on 2019-09-24
ok, so how can i create a swap file?

---

### Post by sudodus on 2019-09-24
Maybe one of the links from the following web page will lhelp you,

[Persistent live Ubuntu system or portable installed Ubuntu system](https://askubuntu.com/a/1175823/55537)

---

