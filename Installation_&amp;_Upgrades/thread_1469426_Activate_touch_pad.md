---
title: "Activate touch pad??"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by thelugnut on 2010-05-02
Can some kind soul tell me how I can activate and deactivate the laptop touchpad?:confused:

---

### Post by P4man on 2010-05-02
it should be activated by default.
Can you open a terminal and provide us with the output of these two commands:

```
lspci
```

```
lsusb
```

---

### Post by thelugnut on 2010-05-02
I have to apologize for the very poor post. Somehow a portion didn't make it to the thread and I failed to check to see if it was all right. 

First of all, I am using Ubuntu 10.04. I have been using Ubuntu for a few years now. I never had any problems with activating and deactivating the touch pad, because it was easily found under System>Preferences>Mouse.

Now however, that part seems to be missing. I am assuming that it has been moved, but understand it could have inadvertently left out.

So, that is why I asked for some direction. :)

---

### Post by P4man on 2010-05-02
well, now I still dont know if you have an alps or synaptics touchpad and whether or not its recognized as such, or just as a ps2 mouse. 

Anyway, try installing gpointing-device-settings (you'll then find it in system > preferences > input device settings) but do provide the above info pls. Im using lucid as well, and I still have the touchpad tab in my mouse preferences, but I do think I installed or configured something to enable smhconfig (I got a synaptics touchpad)

---

### Post by wilee-nilee on 2010-05-02
On my computer holding down Fn and hitting F7 turns the pad on or off in Lucid/XP/W7

---

### Post by thelugnut on 2010-05-02
P4man - 
james@james-laptop:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 1267:0212 Logic3 / SpectraVideo plc 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
----------------------------------------------------------------------------------------------------------------------------------------------
james@james-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 13)
04:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
05:03.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
05:03.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
05:03.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
james@james-laptop:~$

wilee nilee - Nope doesn't work for me.

---

### Post by thelugnut on 2010-05-02
I don't see this option -
"system > preferences > input device settings"

---

### Post by P4man on 2010-05-02
You have to install it first

```
sudo apt-get install gpointing-device-settings
```

I see no reference to alps or synaptics, maybe check your dmesg output for either.

---

### Post by thelugnut on 2010-05-02
> sudo apt-get install gpointing-device-settings

That did it for me. Thank you, very much P4man
I can mark this one solved.

---

