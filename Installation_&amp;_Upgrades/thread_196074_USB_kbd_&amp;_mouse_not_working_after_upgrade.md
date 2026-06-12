---
title: "USB kbd &amp; mouse not working after upgrade"
date: 2006-06-13
forum: Installation &amp; Upgrades
---

### Post by ericgrog on 2006-06-13
The upgrade to dapper went quite well, the only major issue I seem to have is that my USB keyboard and mouse no longer work. (On an Inspiron 5100 laptop, but I don't think it's a laptop specific issue.) The standard laptop kbd and touchpad work fine.

When I plug in my USB kbd and mouse, it seems to see it as messages come out in /var/log messages:

  Jun 13 15:05:59 localhost kernel: [4314658.091000] usb 1-1: new low speed  USB device using uhci_hcd and address 4
  Jun 13 15:05:59 localhost kernel: [4314658.297000] input: Composite USB   PS2 Converter USB to PS2 Adaptor  v1.09 as /class/input/input5
  Jun 13 15:05:59 localhost kernel: [4314658.297000] input: USB HID v1.10   Keyboard [Composite USB PS2 Converter USB to PS2 Adaptor  v1.09] on   usb-0000:00:1d.0-1
  Jun 13 15:05:59 localhost kernel: [4314658.333000] input: Composite USB   PS2 Converter USB to PS2 Adaptor  v1.09 as /class/input/input6
  Jun 13 15:05:59 localhost kernel: [4314658.333000] input: USB HID v1.10   Mouse [Composite USB PS2 Converter USB to PS2 Adaptor  v1.09] on    usb-0000:00:1d.0-1

If I boot up my old 2.6.12-9 kernel, it seems to work fine.  

A couple more possible hints: 

1. I don't have 'hotplug' in dapper (nor can I find it) - is this no longer used?  I do have usbmgr - perhaps that fills the same bill?  Should there be a new entry in /etc/usbmgr-2.6.conf?

2. In my 2.6.12 system, I had modules named 'psmouse' and 'mousedev' - in dapper (2.6.15) I only have psmouse.

Any ideas?  I really believe it's an issue of configuration, as I haven't seen anyone else post a similar problem.

Thanks for your help...
Eric

---

