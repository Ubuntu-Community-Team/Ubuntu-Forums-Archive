---
title: "Weird booting/rebooting behavior with bootable SD Card."
date: 2013-09-05
forum: Installation &amp; Upgrades
---

### Post by sergiome2 on 2013-09-05
I'm not sure this is a good place to get support on this issue. If there's a more appropriate one, let me know.

So, here's what I have:
 

[LIST]
[*]A bootable SD Card, with a minimal Ubuntu installation.
[*]A bootable USB stick, with exactly the same filesystem image.
[*]A Shuttle PC (much like the [XS35V2 Digital Signage Media Player seen here]("http://us.shuttle.com/Models.aspx")).
[*]The Shuttle PC has no internal storage at all, it relies entirely on bootable media, the GRUB partition is contained within the SD card and the USB stick.
[/LIST]

Now, I'm having issues when **rebooting** the shuttle PC, but only when running [B]from the SD Card.

[/B]
[LIST]
[*]**CASE 1**: If the system is turned off, turning it on with either the SD Card or the USB Stick plugged in works perfectly.
[*]**CASE 2**: If the system is turned on, and a reboot command is issued (this includes*** sudo reboot*** (with and without the --force flag), ***sudo shutdown -r now*** and ***sudo init 6***):
[LIST]
[*]**CASE 2.1: **If it was running on the **USB Stick**, it reboots just fine and I get back to the login prompt.
[*]**CASE 2.2: **If it was running on the **SD Card**, it shuts down fine, but when actually turning on again it shows the BIOS splash, but after that it gets stuck on a black screen with a blinking cursor.
[/LIST]
[/LIST]

In this last situation described, I have no input at all (I have tried ctrl+alt+f<x>, ctrl+c, etc). However, if at this point I shut down the shuttle, and turn it on, it works perfectly (as described in **CASE 1**).

Here's what I've tried:


[LIST]
[*]Enabled all kinds of grub flags, namely those of the form "reboot=xxx" where xxx can be bios, acpi, etc... with no different results achieved.
[*]Enabled all kinds of verbose flags but all I get is the blinking cursor on a black screen.
[*]I've tried extracting the SD card from the shuttle right after getting the blinking cursor with the hope to extract a useful log, but it seems like no new logs are generated in either /var/log/boot.log or /var/log/dmesg
[*]I've made sure that the SD card is the only bootable media selected in the BIOS boot order
[*]I've checked for potential BIOS options that could be causing trouble, to no avail.
[/LIST]

I'm very confused because I don't understand what the difference is between turning off and turning on the shuttle (**CASE 1**, which works fine both using the USB and SD) and issuing a reboot command (**CASE 2**, which when using the SD card as described in **CASE 2.2** fails).

I appreciate any help I can get to figure this one out, and will provide any information as required.

Regards,
Sergio

---

### Post by tgalati4 on 2013-09-05
The only thing I can think of is that the USB interface is well-defined and well-handled in the BIOS.  The SD card requires a reader that is typically connected to the internal USB bus.

```
lsusb
```

What code is loaded by the BIOS to activate the SD card reader is anyone's guess.  When you boot normally, linux will load a module to handle the sd card reader.  

I would load *acpitool* and leave power to that USB port after shutdown.  Search the forums for how to use *acpitool*.

I'm thinking that different shutdown procedures will allow some power to the SD card slot, which allow it to function during boot.

---

### Post by sergiome2 on 2013-09-05
> **tgalati4 said:**
> The only thing I can think of is that the USB interface is well-defined and well-handled in the BIOS.  The SD card requires a reader that is typically connected to the internal USB bus.

```
lsusb
```

What code is loaded by the BIOS to activate the SD card reader is anyone's guess.  When you boot normally, linux will load a module to handle the sd card reader.  

I would load *acpitool* and leave power to that USB port after shutdown.  Search the forums for how to use *acpitool*.

I'm thinking that different shutdown procedures will allow some power to the SD card slot, which allow it to function during boot.

Thanks for the suggestion. It seems to me though like they're already being left on after shutdown?:

```
[FONT=arial]sergio@shuttle:~$ lsusb[/FONT]
[FONT=arial]Bus 001 Device 003: ID 0781:5571 SanDisk Corp. [/FONT]
[FONT=arial]Bus 004 Device 002: ID 08bb:2902 Texas Instruments Japan PCM2902 Audio Codec[/FONT]
[FONT=arial]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT]
[FONT=arial]Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
[FONT=arial]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
[FONT=arial]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
[FONT=arial]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]

```

That would seem to indicate the SD card slot is device 003, which is seen as enabled when running acpitool -w:

```
[FONT=arial]sergio@shuttle:~$ acpitool  -w[/FONT]
[FONT=arial]   Device    S-state      Status   Sysfs node[/FONT]
[FONT=arial]  ---------------------------------------[/FONT]
[FONT=arial]  1. P0P1      S4    *disabled  pci:0000:00:1e.0[/FONT]
[FONT=arial]  2. AZAL      S3    *disabled  pci:0000:00:1b.0[/FONT]
[FONT=arial]  3. P0P4      S4    *disabled  pci:0000:00:1c.0[/FONT]
[FONT=arial]  4. P0P5      S4    *disabled  pci:0000:00:1c.1[/FONT]
[FONT=arial]  5. JLAN      S3    *disabled[/FONT]
[FONT=arial]  6. P0P6      S4    *disabled[/FONT]
[FONT=arial]  7. RLAN      S3    *disabled[/FONT]
[FONT=arial]  8. P0P7      S4    *disabled  pci:0000:00:1c.3[/FONT]
[FONT=arial]  9. P0P8      S4    *disabled[/FONT]
[FONT=arial]  10. P0P9      S4    *disabled[/FONT]
[FONT=arial]  11. USB0      S3    *enabled   pci:0000:00:1d.0[/FONT]
[FONT=arial]  12. USB1      S3    *enabled   pci:0000:00:1d.1[/FONT]
[FONT=arial]  13. USB2      S3    *enabled   pci:0000:00:1d.2[/FONT]
[FONT=arial]  14. USB3      S3    *enabled   pci:0000:00:1d.3[/FONT]
[FONT=arial]  15. EUSB      S3    *enabled   pci:0000:00:1d.7[/FONT]

```

I might be using acpitool wrong. Do let me know if that's the case.

---

