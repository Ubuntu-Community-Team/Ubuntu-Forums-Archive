---
title: "Wireless USB Adaptor Issue"
date: 2011-04-06
forum: Installation &amp; Upgrades
---

### Post by coly13 on 2011-04-06
I have recently installed Ubuntu 10.10 on my desktop but cannot for the life of me get my Wireless USB Adaptor working.
Its a 
Tenda 54M Wireless USB Adaptor
Model No. W54U
Software Version Number.:Ver2.0

lsusb gives me this:

[I]Bus 002 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 1286:1fab Marvell Semiconductor, Inc. 88W8338 [Libertas] 802.11g
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/I]

I presume the Marvell Semiconductor is my Wireless USB Adaptor??

I have also downloaded a linux driver for this model off the tenda website, but ive got no idea what to do with it or where to put it.

Any help would be great.
Thanks

Colin

---

### Post by lkraemer on 2011-04-06
Power up your Ubuntu machine WITHOUT the USB to Serial Adapter
inserted into a USB Port. Then Open a Terminal (Console) and
Copy & Paste the following to the Terminal Window:
```

lsusb >junk.txt
echo ------------------------------------- >> junk.txt

```
Then Plug in your USB to Serial Adapter and wait 1 Minute. Then again do:
```

lsusb >> junk.txt
echo ------------------------------------- >> junk.txt
dmesg | tail
echo ------------------------------------- >> junk.txt

```
You should see a difference as your device should be detected.......................

This will return a Manufactuer & Product Number, so use it to get more information.... example.....0a5c:2101...)
```

Bus 008 Device 003: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b091 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
Then do:
```

lsusb -v -d 0a5c:2101 >> junk.txt
echo ------------------------------------- >> junk.txt

```

You may also want to include:
```

lshw -C network >> junk.txt
echo ------------------------------------- >> junk.txt
lsmod >> junk.txt
echo ------------------------------------- >> junk.txt
ndiswrapper -l >> junk.txt
echo ------------------------------------- >> junk.txt
cat /etc/modprobe.d/blacklist.conf >>junk.txt
echo ------------------------------------- >> junk.txt
iwconfig >> junk.txt

```
Then post junk.txt


lk

---

