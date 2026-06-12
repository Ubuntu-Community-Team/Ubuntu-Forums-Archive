---
title: "Lost mouse and error code during Lubuntu installation"
date: 2018-08-09
forum: Installation &amp; Upgrades
---

### Post by maurice33 on 2018-08-09
I am trying to install Lubuntu on my Dell laptop. I downloaded the Lubuntu 18.04 file and used Rufus, Universal USB Installer, Etcher and a couple others. It installed properly on my USB Sandisk drive each time. This isn't the problem. My problem is an error code I get after I select the USB drive in BIOS and hit enter to start the installer.

When the boot menu appears in BIOS, I select the USB drive and hit enter to start the installer. I have tried this several times and each time it takes me to a generic Lubuntu install menu with 4 options and I choose the install option or "try Lubuntu without installing." Each time it starts to load it then goes to a black screen informing me of a Firmware Bug.  It reads like this:

[Firmware Bug] cpu 0, invalid threshhold interupt offset 1 for b.......(and so on)

Couldn't get size: 0x800000000000000000e....(and so on)

MODSIGN: Couldn't get UEFI db list

psmouse seriol: elantech: elantech_send_cmd query 0x04 failed

(This isn't the complete list)

I have tried to change BIOS settings in setup to every imaginable configuration, including but not limited to enable/disable Firmware TPM, Secure Boot enable/disable and many other setting changes with no success. I even used Legacy in BIOS and it booted from a cold startup fine but I kept losing my mouse. Legacy gave me the best install format but I also got a "BUG" warning before going to the install options. If I lose my mouse during setup I could have serious problems. I realize using Legacy isn't ideal for this install but I was desperate.

I have tried everything possible to make this work. I also tried to install Mint with the same results. Whatever changes in BIOS you might suggest I have probably already tried. It appears if I can get rid of this error code [Firmware Bug] I could do the install with confidence.  Thank you for your help :)

---

### Post by mörgæs on 2018-08-11
Hi, welcome to the fora.

Have you tried the [alternate ISO]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO")? The installer is text-based but the final system is the same as always.

---

