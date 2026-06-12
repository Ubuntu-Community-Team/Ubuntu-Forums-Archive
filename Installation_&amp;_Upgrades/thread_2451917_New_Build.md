---
title: "New Build"
date: 2020-10-13
forum: Installation &amp; Upgrades
---

### Post by Jocklad on 2020-10-13
Have just done a new build and trying to install Ubuntu 20.04 LTS.
Specs: Rog Strix B550-F gaming motherboard.
           MSI Radeon RX 580 Graphics card
           EVGA 650BQ psu
           250g Kingston M.2 NVME drive
           Corsair 16g DDR4 Ram
 

The problem is graphics,when I boot from live usb the install is perfect.

Soon as I boot into the nvme the graphics are distorted.

Graphics on Windows 10 are perfect so I doubt this is a hardware issue.

Grateful for any help. 

Ben.

---

### Post by dino99 on 2020-10-13
Does your rx580 card is well identified by the system ? (system Settings ->about  menu)
Is there error(s) (red line) inside 'journalctl -b' output from a terminal ?

---

### Post by Jocklad on 2020-10-13
Cant see any errors or red lines from journalctl -b in terminal

---

### Post by oldfred on 2020-10-13
Some similar systems.
Asus ROG Strix B450 E motherboard UEFI update worked
[https://askubuntu.com/questions/1174679/cant-dual-boot-ubuntu-with-windows-10-in-ryzen-3600?noredirect=1#comment1960921_1174679](https://askubuntu.com/questions/1174679/cant-dual-boot-ubuntu-with-windows-10-in-ryzen-3600?noredirect=1#comment1960921_1174679)
Asus Rog Strix B550 Disable IOMMU
[https://askubuntu.com/questions/1265397/unable-to-install-ubuntu-20-04-lts-via-live-usb-ryzen-5-3600?noredirect=1#comment2141726_1265397](https://askubuntu.com/questions/1265397/unable-to-install-ubuntu-20-04-lts-via-live-usb-ryzen-5-3600?noredirect=1#comment2141726_1265397)

---

### Post by Jocklad on 2020-10-13
Thanks oldfred will have a look at that

---

### Post by Jocklad on 2020-10-15
Graphics are ok now.
It needed a kernel upgrade them add nomodeset

Many thanks

Jocklad  ):P

---

### Post by CelticWarrior on 2020-10-15
'nomodeset' is not a solution, it disables graphics drivers.

---

### Post by Jocklad on 2020-10-16
> **CelticWarrior said:**
> 'nomodeset' is not a solution, it disables graphics drivers.

At the moment it is the only working solution otherwise unreadable display

---

