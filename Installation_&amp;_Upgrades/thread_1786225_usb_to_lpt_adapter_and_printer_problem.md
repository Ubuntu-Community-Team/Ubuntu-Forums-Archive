---
title: "usb to lpt adapter and printer problem"
date: 2011-06-19
forum: Installation &amp; Upgrades
---

### Post by live2trance on 2011-06-19
Hi.

I've a usb to lpt adapter to connect a ESC/POS printer. The adapter is detected correctly and installed under /dev/usb/lp0. And I've tested two different adapters with same results, one from HQ, and other from SUNIX.

Here is at dmesg:

[   16.056665] usblp0: USB Bidirectional printer dev 2 if 0 alt 1 proto 2 vid 0x067B pid 0x2305
[   16.056715] usbcore: registered new interface driver usblp

My problem is that with some printers i don't know why. With a good printer i connect the cables, and using 'lpinfo -v' i can see it, so after it i can use cups to install the printer and print jobs.
With other printers it doesn't appear with 'lpinfo -v', and so cups will never install the printer.
I've tried on cups to set manually the URI for the printer, but with no luck also, the jobs will never go out to printer.

After some reading i see that linux when i connect the cables, and when installing the /dev/usb/lp0 device, will ask the printer for its major and minor device numbers. And what i've seen is that with the printers that doesn't work when viewing 'ls -l /dev/usb/'  have the minor number set to 0. here is a example:

crw-rw---- 1 root lp 180, 0 2011-06-19 15:22 lp0

My question is if there is a way to force this device number by hand, because as i can see, it isn't well set, and i think because of that i can't use the printers.
Or if someone have some idea of what i can do more, i will be grateful

I've tested this on different machines and with different versions of ubuntu, 9.04, 9.10, 10.04. And with same results on all.

Best Regards

---

