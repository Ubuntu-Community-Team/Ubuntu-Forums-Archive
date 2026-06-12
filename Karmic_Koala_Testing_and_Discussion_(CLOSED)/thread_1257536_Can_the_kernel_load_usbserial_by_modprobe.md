---
title: "Can the kernel load usbserial by modprobe ?"
date: 2009-09-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by taaheel on 2009-09-03
Hi .. I had an annoying problem with the jaunty kernel version so does the new kernel support commands like this :
```
# modprobe usbserial vendor=0x???? product=0x????
```??:?

---

### Post by crimsun on 2009-09-03
Note that they're ushorts.

$ modinfo usbserial
filename:       /lib/modules/2.6.31-9-generic/kernel/drivers/usb/serial/usbserial.ko
license:        GPL
description:    USB Serial Driver core
author:         Greg Kroah-Hartman, [email]greg@kroah.com[/email], [http://www.kroah.com/linux/](http://www.kroah.com/linux/)
srcversion:     13256BAE0ABBC731310F3F3
depends:
vermagic:       2.6.31-9-generic SMP mod_unload modversions
parm:           vendor:User specified USB idVendor (ushort)
parm:           product:User specified USB idProduct (ushort)
parm:           debug:Debug enabled or not (bool)

---

### Post by taaheel on 2009-09-03
> **crimsun said:**
> Note that they're ushorts.

$ modinfo usbserial
filename:       /lib/modules/2.6.31-9-generic/kernel/drivers/usb/serial/usbserial.ko
license:        GPL
description:    USB Serial Driver core
author:         Greg Kroah-Hartman, [email]greg@kroah.com[/email], [http://www.kroah.com/linux/](http://www.kroah.com/linux/)
srcversion:     13256BAE0ABBC731310F3F3
depends:
vermagic:       2.6.31-9-generic SMP mod_unload modversions
parm:           vendor:User specified USB idVendor (ushort)
parm:           product:User specified USB idProduct (ushort)
parm:           debug:Debug enabled or not (bool)

thanks...
so I can use mopdprobe  usbserial without putting the module in the menu.lst like jaunty , with any device(usb wireless card).

---

