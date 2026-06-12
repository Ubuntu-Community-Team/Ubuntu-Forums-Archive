---
title: "How remove fglrx?"
date: 2009-07-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by christian.convey on 2009-07-23
When the Karmic Alpha3 desktop told me there was a proprietary driver available for my ATI card, I went with the suggestion and installed it.   However, when I rebooted, my graphical display was garbled and unusable.

From a console I removed the fglrx driver, but upon reboot I still don't have a working X display.

How can I get my system back to the X configuration it had when I first installed Alpha3?   That worked fine.  I assume it was using the open-source ATI driver.

Thanks,
Christian

---

### Post by ktp on 2009-07-24
> **christian.convey said:**
> When the Karmic Alpha3 desktop told me there was a proprietary driver available for my ATI card, I went with the suggestion and installed it.   However, when I rebooted, my graphical display was garbled and unusable.

From a console I removed the fglrx driver, but upon reboot I still don't have a working X display.

How can I get my system back to the X configuration it had when I first installed Alpha3?   That worked fine.  I assume it was using the open-source ATI driver.

Thanks,
Christian

Look at /etc/X11/xorg.conf and remove

 Driver          "ati"

or just rename/delete the xorg.conf file.

---

### Post by christian.convey on 2009-07-24
> **ktp said:**
> Look at /etc/X11/xorg.conf and remove

 Driver          "ati"

or just rename/delete the xorg.conf file.

Thanks! That did it.

---

