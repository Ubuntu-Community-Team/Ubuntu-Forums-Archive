---
title: "p54usb module loading problem"
date: 2009-04-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by scalawag_ on 2009-04-14
Ubuntu 9.04 Beta i386 without updates.
I've already put the right firmware for my wireless dongle (from [http://wireless.kernel.org/en/users/Drivers/p54](http://wireless.kernel.org/en/users/Drivers/p54)), but i can't have it working.
When USB Wireless dongle is inserted the booting stops for a long time.
I have retrieved the following info with dmesg:

[ 267.820569] cfg80211: Calling CRDA to update world regulatory domain
[ 267.835503] usb 1-4: firmware: requesting isl3890usb
[ 267.859230] cfg80211: World regulatory domain updated:
[ 267.859235] (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 267.859238] (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 267.859241] (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 267.859244] (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 267.859247] (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 267.859250] (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 267.866751] p54: LM86 firmware
[ 267.866755] p54: FW rev 2.13.1.0 - Softmac protocol 5.5
[ 269.758731] p54: unknown eeprom code : 0x1
[ 269.758735] p54: unknown eeprom code : 0x3
[ 269.758738] p54: unknown eeprom code : 0x1007
[ 269.758740] p54: unknown eeprom code : 0x1008
[ 269.758742] p54: unknown eeprom code : 0x1100
[ 269.758744] p54: unknown eeprom code : 0x1905
[ 269.758752] phy0: hwaddr 00:04:e2:81:5f:f1, MAC:isl3886 RF:Frisbee

When i try to remove module p54usb (sudo modprobe -r p54usb) the console stops responding.
Ifconfig and iwconfig don't show any wireless.
I'm sure the firmware is the correct one since i use it on fedora 10 amd64 with great success.
lsusb shows :
Bus 001 Device 003: ID 0707:ee06 Standard Microsystems Corp. EZ-Connect 802.11g Adapter
so the chip is the ISL3886 (firmware 2.13.1.0.arm.0 for kernel 2.6.28)

---

