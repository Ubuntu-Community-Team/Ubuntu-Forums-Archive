---
title: "Add RAID driver during install problem"
date: 2020-04-28
forum: Installation &amp; Upgrades
---

### Post by andyx981 on 2020-04-28
Hello guys!

Im installing Ubuntu Server 16.04 x64 on Huawei Server with Megaraid SAS Raid adapter.
Boot mode - UEFI.

First of all - created Raid 5 Virtual disc (3 SAS discs).

During install, Ubuntu dont see the raid disc(it has megaraid_sas driver but its outdated).
After visiting manifacturing site I found the needed [driver ]("https://docs.broadcom.com/docs/MR_LINUX_DRIVER_7.13-07.713.02.00.tgz")and its supports Ubuntu 16.
And what a joke - they have a driver in .deb format:-(
According to they manual we have to install it with dpkg
```
#dpkg -i <DRIVER_PACKAGE>.deb
```.
For sure it wont works before system not installed yet.

What I did:
I installed DEB on virtual os and extracted megaraid_sas.ko needed driver file.
During Ubuntu install I switched terminal window (ALT+F2) and activated that module:
```
insmod megaraid_sas.ko
```
After that Ubuntu detected raid and successfully finished installation.
But, after reboot the system failed to start with the mdadm issues, partitons wasnt mounted and system dropped me into ***initramfs shell***.

Im really tired with that ](*,)](*,)](*,)
 Great thanks with any advices!

p.s. I tryed ```
 update-initramfs -u
``` but it doesnt works during install.
p.p.s. I have some mind regards run commands via chroot into /target, but dont know exactly what to do yet.

---

### Post by CelticWarrior on 2020-04-28
The OS runs on anything.
Most admins I know run it from a USB stick inside. The other drives in RAID are used for data only.

---

