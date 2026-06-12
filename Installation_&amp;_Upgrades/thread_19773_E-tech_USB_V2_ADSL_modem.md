---
title: "E-tech USB V2 ADSL modem"
date: 2005-03-13
forum: Installation &amp; Upgrades
---

### Post by popeye on 2005-03-13
Hello,

I'am having trouble installing this  modem.

It is a USB modem and that seems to be rather difficult.

It's a e-tech USB V2 modem and i found that there are mandrake drivers for it. Also there is a page [http://dsl.linux.it/DebianNetinstall?action=highlight&value=ChipsetConexantUsb](http://dsl.linux.it/DebianNetinstall?action=highlight&value=ChipsetConexantUsb) wich is about this modem, it appears to be a conexant and i should be able to confirm that with the Vendor ID. But i don't know how to find that one. I think i have to connect it first.

However i installed already the newest kernel linux-image-2.6.10-3-k7-smp and still have a working machine. According to [http://accessrunner.sourceforge.net/driver.shtml](http://accessrunner.sourceforge.net/driver.shtml)  i should have a kernel later than 2.6.10.

My first question is:

- How can i check that the hotplug is working. 

When i stick in the USB cable nothing happens. I have a usb memory stick wich i also cannot find

---

### Post by popeye on 2005-03-14
Well when i stick in the cable i see with dmesg:

usb 1-2: new full speed USB device using uhci_hcd and address 2


I tried the same with the knoppix livecd and then i get:

USB device (vend/prod 0x572/0xcb00) is not claimed by any active driver 

the vend/prod is according the before mentioned webpage. But stil i have to figure out how to implement the  driver.

---

