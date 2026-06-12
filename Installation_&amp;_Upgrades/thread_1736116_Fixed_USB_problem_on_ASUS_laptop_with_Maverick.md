---
title: "Fixed USB problem on ASUS laptop with Maverick"
date: 2011-04-22
forum: Installation &amp; Upgrades
---

### Post by trevbus on 2011-04-22
After upgrading to Maverick I found that lsusb command would hang or omit any device I plugged in (flash drive or portable hard disk)


So I did

dpkg -i /var/cache/apt/archives/*usb*

and

dpkg -i /var/cache/apt/archives/*udev*

using packages from a lucid install I had on another laptop which didn't have the USB problem

Now everything is fine. Maverick has some problem with USB.

---

### Post by dino99 on 2011-04-22
is it installed ?

AcpiTool is a Linux ACPI client. It's a small command line application,
intended to be a replacement for the apm tool. The primary target audience are
laptop users, since these people are most interested in things like battery
status, thermal status and the ability to suspend (sleep mode). The program
simply accesses the /proc/acpi or /sysfs entries to get or set ACPI values.
It also supports various extensions for Toshiba, Asus, and IBM Thinkpad
laptops.

sudo update-pciids && sudo update-usbids

---

