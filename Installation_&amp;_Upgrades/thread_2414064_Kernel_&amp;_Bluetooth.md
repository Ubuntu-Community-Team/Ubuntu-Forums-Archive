---
title: "Kernel &amp; Bluetooth"
date: 2019-03-05
forum: Installation &amp; Upgrades
---

### Post by capemayal on 2019-03-05
18.10 -  I've always had, like others, problems with Bluetooth.  18.10shipped with kernel 4.19, and now a upgrade to 4.20 is ready.  I rolled the kernel back to 4.15 and now my Bluetooth works.  I don't know if running 4.15 with 18.10 is okay, but it seems to be.  The question - am I missing something by using 4.15 with 18.10?

Al

---

### Post by deadflowr on 2019-03-05
None of those kernels come with Ubuntu 18.10.
Nor will any ever be part of Ubuntu 18.10
Ubuntu 18.10 comes with the 4.18 kernel and only 4.18 kernel.

Are you using a 3rd party kernel updater tool?

Have you tried to run the regular 4.18 kernel?

---

### Post by capemayal on 2019-03-05
I am using Grub Customizer[SIZE=2] [/SIZE]which shows available kernels.  BT didn't work until I installed 4.15.

---

### Post by jeremy31 on 2019-03-05
Please post results from terminal for ```
lspci -nnk | grep -iA3 net; lsusb; dmesg | egrep -i 'blue|firm'
```
I take it you upgraded from 18.04 to 18.10?

---

### Post by capemayal on 2019-03-05
My 18.10 is fresh install.

01:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
    Subsystem: CLEVO/KAPOK Computer RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1558:2425]
    Kernel driver in use: r8169
    Kernel modules: r8169
02:00.0 Network controller [0280]: Intel Corporation Wireless 8260 [8086:24f3] (rev 3a)
    Subsystem: Intel Corporation Dual Band Wireless-AC 8260 [8086:1010]
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f2:b550 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0a2b Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[    0.028000] Spectre V2 : Enabling Restricted Speculation for firmware calls
[    0.102841] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    2.430651] [drm] Finished loading DMC firmware i915/skl_dmc_ver1_27.bin (v1.27)
[   13.052167] Bluetooth: Core ver 2.22
[   13.052184] Bluetooth: HCI device and connection manager initialized
[   13.052187] Bluetooth: HCI socket layer initialized
[   13.052190] Bluetooth: L2CAP socket layer initialized
[   13.052199] Bluetooth: SCO socket layer initialized
[   13.101063] Bluetooth: hci0: Bootloader revision 0.0 build 2 week 52 2014
[   13.104112] iwlwifi 0000:02:00.0: loaded firmware version 36.e91976c0.0 op_mode iwlmvm
[   13.105866] Bluetooth: hci0: Device revision is 5
[   13.105868] Bluetooth: hci0: Secure boot is enabled
[   13.105869] Bluetooth: hci0: OTP lock is enabled
[   13.105870] Bluetooth: hci0: API lock is enabled
[   13.105871] Bluetooth: hci0: Debug lock is disabled
[   13.105872] Bluetooth: hci0: Minimum firmware build 1 week 10 2014
[   13.108388] Bluetooth: hci0: Found device firmware: intel/ibt-11-5.sfi
[   13.167692] Bluetooth: hci0: Failed to send firmware data (-38)
[   13.840540] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   13.840542] Bluetooth: BNEP filters: protocol multicast
[   13.840546] Bluetooth: BNEP socket layer initialized

---

