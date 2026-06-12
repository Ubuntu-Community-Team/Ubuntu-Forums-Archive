---
title: "USB stopped working today"
date: 2008-09-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by OliW on 2008-09-27
Please excuse the following message of panic and extended peril.

ARGL WE'RE ALL GOING TO DIE!!

That's better. Well my USB controller appears to have ceased working after some updates I applied and restarted with. I couldn't tell you which update did it because it has been almost 4 days (with 300 updates) since my last reboot.

I'd really appreciate any help I could get on tracking the problem down.

Edit 1: Okay, some usb works! My DVB-T tv dongle still works fine. But flash drives, my ipod and two mice all refuse to work.

Edit 2: I reinstalled my nvidia driver then restarted and all was well. I'm sure the restart on its own might have fixed it. Very odd but fine now.

---

### Post by olskar on 2008-09-27
> **OliW said:**
> Please excuse the following message of panic and extended peril.

ARGL WE'RE ALL GOING TO DIE!!

That's better. Well my USB controller appears to have ceased working after some updates I applied and restarted with. I couldn't tell you which update did it because it has been almost 4 days (with 300 updates) since my last reboot.

I'd really appreciate any help I could get on tracking the problem down.

Edit 1: Okay, some usb works! My DVB-T tv dongle still works fine. But flash drives, my ipod and two mice all refuse to work.

Output of lsusb?

---

### Post by OliW on 2008-09-27
How I'd love to copy and paste =) I'm going to type it out manually, but there could be some subtle typos.

```
Bus 002 Device 004: ID 14aa:0226 AVerMedia (again) or C&E
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

The first is my DVB-T. I've tried both mice on both buses.

---

### Post by OliW on 2008-09-27
```
Bus 002 Device 005: ID 046d:c51a Logitech, Inc. MX Revolution/G7 Cordless Mouse
Bus 002 Device 004: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 002 Device 002: ID 0556:0001 Asahi Kasei Microsystems Co., Ltd AK5370 I/F A/D Converter
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 14aa:0226 AVerMedia (again) or C&E 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Yeah baby. No idea what happened. I restarted again and it all just worked.

---

