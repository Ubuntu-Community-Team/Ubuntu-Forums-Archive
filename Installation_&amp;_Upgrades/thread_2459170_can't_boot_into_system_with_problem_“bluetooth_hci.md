---
title: "can't boot into system with problem “bluetooth: hci0: command 0xfc09 tx timeout”"
date: 2021-03-12
forum: Installation &amp; Upgrades
---

### Post by yindongshan on 2021-03-12
ubuntu 20.04LTS alongside with win10 are installed in my laptop, and all ubuntu packages are up-to-date. I can't boot into ubuntu after recent update software update center, boot locked during startup and show message:
[  6.000853] bluetooth: hci0: command 0xfc09 tx timeout
[14.001206] bluetooth: hci0: failed to send firmware data (-110)
[14.001374] bluetooth: hci0: sending frame failed (-19)
after I boot into safe mode, the system won't suspend after lid was closed,
I checked the boot log and got detailed messages which are listed below:
yindongshan@yindongshan-Precision-5540:~$ dmesg | grep Bluetooth
[    3.710446] Bluetooth: Core ver 2.22
[    3.710475] Bluetooth: HCI device and connection manager initialized
[    3.710479] Bluetooth: HCI socket layer initialized
[    3.710481] Bluetooth: L2CAP socket layer initialized
[    3.710483] Bluetooth: SCO socket layer initialized
[    3.725865] Bluetooth: hci0: Bootloader revision 0.3 build 0 week 24 2017
[    3.727020] Bluetooth: hci0: Device revision is 1
[    3.727021] Bluetooth: hci0: Secure boot is enabled
[    3.727021] Bluetooth: hci0: OTP lock is enabled
[    3.727021] Bluetooth: hci0: API lock is enabled
[    3.727022] Bluetooth: hci0: Debug lock is disabled
[    3.727023] Bluetooth: hci0: Minimum firmware build 1 week 10 2014
[    3.728444] Bluetooth: hci0: Found device firmware: intel/ibt-20-1-3.sfi
[    4.079305] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    4.079306] Bluetooth: BNEP filters: protocol multicast
[    4.079309] Bluetooth: BNEP socket layer initialized
[    4.546081] Bluetooth: hci0: sending frame failed (-19)
[    6.547251] Bluetooth: hci0: command 0xfc09 tx timeout
[   14.771246] Bluetooth: hci0: Failed to send firmware data (-110)
[   14.771353] Bluetooth: hci0: sending frame failed (-19)
[   14.771423] Bluetooth: hci0: Intel reset sent to retry FW download
my laptop is dell precision 5540&#65292;with intel AX200 wifi card.
it seems that this is about bluetooth drive.

---

