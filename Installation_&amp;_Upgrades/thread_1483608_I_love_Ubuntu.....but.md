---
title: "I love Ubuntu.....but"
date: 2010-05-14
forum: Installation &amp; Upgrades
---

### Post by skoh on 2010-05-14
I have a finicky graphics adapter. I just bought a new Asus eee pc 1005PE to replace my aspire one D250.  The display first off flickers with "dim on idle" enabled but I temporarily resolved that by disabling it. Also the adjust brightness funtion key is not working, it's completely confused when I try to adjust it and keeps jumping all over the place on the slider bar. Here is the lspci, thanks if you can help a fellow ubunter. I am not using the Ubuntu remix install, i like the user interface of the desktop ubuntu better.

ccna@ccna-netbk:~$ lspci
[B]00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller[/B]
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

---

### Post by Geo411m on 2010-05-14
I have the same netbook. Open up terminal and type:

sudo nano /etc/default/grub

where it says "quiet splash" add

acpi_osi=Linux acpi_osi=Linux acpi_backlight=vendor splash

type: ctrl o and then ctrl x

then type:

sudo grub-mkconfig

sudo update-grub2

Then reboot.

---

### Post by skoh on 2010-05-14
Nice, that worked but I have no idea what is going on here. I'm more experienced with network not OS's . I thought grub handled the boot loading process. I'm glad that worked, if you can explain what it did that would be great, if not OK too. How do you like the Asus eee . I just went from an acer aspire one N250 with SSD and really really miss the SSD . I find that it really really helps these netbooks performance wise. Also I don't see how ill ever get 11 hours of battery life in GNS3 / Dyamips even with remote hyper-visors Thanks again.

---

