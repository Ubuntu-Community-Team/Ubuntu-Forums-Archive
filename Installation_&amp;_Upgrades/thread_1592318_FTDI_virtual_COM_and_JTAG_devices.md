---
title: "FTDI virtual COM and JTAG devices"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by drwho9437 on 2010-10-10
Okay, so I have two devices I would like to use on my Ubuntu 10.04 install both are based on FTDI chips. Skip to ********** for the problems...

One is a Luminary ICDI which is based on the FT2232 and the other is a generic serial to usb based on FT232R.

The former is used with OpenOCD for embedded JTAG work. It has two devices in the chip one is a FIFO I believe and the other is a USART.

WIth OpenOCD there is a contrib/rules file, this file is edited to this (81-openocd.rules):


ACTION!="add|change", GOTO="openocd_rules_end"
SUBSYSTEM!="usb", GOTO="openocd_rules_end"
ENV{DEVTYPE}!="usb_device", GOTO="openocd_rules_end"


# TI/Luminary Stellaris In-Circuit Debug Interface (ICDI) Board
ATTRS{idVendor}=="0403", ATTRS{idProduct}=="bcda", MODE="664", GROUP="plugdev"

# Just an extra serial port (Sparkfun FT232R)
ATTRS{idVendor}=="0403", ATTRS{idProduct}=="6001", MODE="664", GROUP="plugdev"

LABEL="openocd_rules_end"

I have checked vendor/product IDs against lsusb. They match.

This rules file lets me use the JTAG. I believe even without the second line, the FT232 is found and a ttyUSBx devices is created. More on this in a second.

I also created a second rules file, (99-usbftdi.rules):
ATTRS{idVendor}=="0403", ATTRS{idProduct}=="bcda", RUN+="/sbin/modprobe -q ftdi-sio product=0xbcda vendor=0x0403"

I believe I got this code (more or less) from an app note from FTDI. 

***************************************************

Here are the issues and what works:

If the FT232R is plugged in at boot and the FT2232 device. Only the FT232R devices has a ttyUSBx device created, and this device file is not accessible without sudo. I am a member of both plugdev and dialup (which ls -l says is the device's group).

If I don't have the FT232R devices plugged in on boot the FT2232 device is assigned ttyUSB0 and ttyUSB1. However ttyUSB0 does not open properly with gtkterm or cutecom. 

If you then run OpenOCD which successfully talks to the device then ttyUSB0 is unregistered. At this point if you connect to ttyUSB1 (which you can do as my standard user) you get data from the JTAG polling rather than the USART device on the chip.

If you connect the FT232R after boot it is assigned the lowest number ttyUSBx device available. It can only be opened by sudo, however the USART works correctly and this shows the serial data I expect from my embedded system.

What I would like is to be able to leave the FT2232 and FT232R plugged in and have the JTAG/USART (FT2232) and the USART (FT232R) work on boot with user permissions.

I thought that adding the second line in the openocd.rules file would give the FT232R user permissions but it doesn't seem to have done that. 

Everything works properly in Win 7 for what it is worth, so I know all of the hardware is fine.

I know this is somewhat convoluted. Please ask if something isn't clear. I have spent many hours trying to get everything to work at this point.

Oh yes and britty is not installed...

---

### Post by dino99 on 2010-10-10
it seem to me that ubuntu devs have made a different choice about usb. You might talk directly with them for your needs:

[https://answers.launchpad.net/ubuntu/+questions](https://answers.launchpad.net/ubuntu/+questions)

---

### Post by drwho9437 on 2010-10-10
I understand you are telling me I should ask elsewhere but not why you think there are other choices nor about what these choices are made...

---

### Post by drwho9437 on 2010-10-11
It appears to be a bug introduced in the FTDI driver in the kernel reverting to 2.6.32-24 resolves the issue. (Issue is in 2.6.32-25)

---

