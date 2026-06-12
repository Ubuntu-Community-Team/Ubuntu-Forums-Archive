---
title: "Lost USB ports after a 20.04 software update. Options short of reinstalling OS?"
date: 2022-11-13
forum: Installation &amp; Upgrades
---

### Post by ozark_hillbilly on 2022-11-13
Ubuntu 20.04 LTS

I made a mistake letting "Software Updater" work its "magic" on my Linux Desktop. Now after the
latest update and reboot my serial ports ttyUSB0 and ttyACM0 are gone -vanished. And I need them to
run Arduino IDE software. I am also having messages generated at boot about usb device errors.
I did revert from Grub kernel 5.15.0-52-generic to 5.15.0-48-generic trying to remedy problem.
Is a new install of Ubuntu my only best option. And do you recommend updates to your OS if things are currently
working ok? Updates seem to cause a lot of unnecessary headaches. I have a big one right now.

lsusb output after update:

```
 ed@ed-G41MT-S2PT:~$ lsusb
Bus 001 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

lsusb output before update:

```
ed@ed-G41MT-S2PT:~$ lsusb
Bus 001 Device 006: ID 046d:c315 Logitech, Inc. Classic Keyboard 200
Bus 001 Device 005: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 003: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 007: ID 10c4:ea60 Silicon Labs CP210x UART Bridge     <  for ESP32
Bus 004 Device 013: ID 03eb:2145 Atmel Corp. ATMEGA328P-XMINI (CDC ACM)  < for UNO Wifi
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Before update:

```
ed@ed-G41MT-S2PT:~$ ls -l /dev/ttyACM0
crw-rw---- 1 root dialout 166, 0 Oct 23 21:31 /dev/ttyACM0           
ed@ed-G41MT-S2PT:~$ ls -l /dev/ttyUSB*
crw-rw---- 1 root dialout 188, 0 Oct 23 20:47 /dev/ttyUSB0           
 
```

---

### Post by ActionParsnip on 2022-11-14
Is this a dual boot setup, please?

---

### Post by ozark_hillbilly on 2022-11-14
No sir. Ubuntu is only OS installed on this computer.

---

### Post by ozark_hillbilly on 2022-11-15
Solved!!!!!!!!!!!!
Picked up a little Dell Laptop w/ Win 10 for $75 bucks to strictly run the Arduino IDE software. 
NO MORE PORT ISSUES...... :popcorn::popcorn::popcorn:

---

