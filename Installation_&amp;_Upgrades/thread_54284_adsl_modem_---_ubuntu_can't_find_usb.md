---
title: "adsl modem --- ubuntu can't find usb"
date: 2005-08-04
forum: Installation &amp; Upgrades
---

### Post by lucaflea on 2005-08-04
hi. 
i know how to install my speedtouch modem but when i try to do it in my (old) notebook and type "sudo ./speedtouchconf.sh" it says that it can't find the usb bus.

?

---

### Post by MrCheese on 2005-08-04
[QUOTE=lucaflea]hi. 
i know how to install my speedtouch modem but when i try to do it in my (old) notebook and type "sudo ./speedtouchconf.sh" it says that it can't find the usb bus.

?[/QUOTE]

Do you see anything in dmesg relating to usb detection? What happens if you "modprobe uhci" and "modprobe ohci" in a terminal?

Does the hardware show up if you lspci?

---

### Post by lucaflea on 2005-08-04
sorry.... what?

what do i have to write in a terminal?

i'm a newbie

---

