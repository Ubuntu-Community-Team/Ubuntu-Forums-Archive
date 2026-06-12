---
title: "Best practice for resolving &quot;Unknown key pressed&quot;"
date: 2010-04-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Edward C on 2010-04-10
Hi,

The MSI Wind12 U200 laptop needs the following command to enable the "decrease brightness" hotkey:

setkeycodes e077 224

I could just put that command into /etc/rc.local, per the instructions here - [https://help.ubuntu.com/community/LaptopSpecialKeys](https://help.ubuntu.com/community/LaptopSpecialKeys) - but I was wondering whether Lucid has some other best-practice solution, perhaps via udev/devicekit?

Thanks,
Ed.

---

### Post by ranch hand on 2010-04-10
I think I would go with the instructions on your link.

---

