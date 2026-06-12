---
title: "grub2 does not count down without USB legacy"
date: 2009-10-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by davidmohammed on 2009-10-18
query -please can some one confirm an observation with grub2

I disabled legacy USB support in my bios - grub2 then does not automatically count down but waits for you to select the kernel to load.  Switching on legacy USB support in the bios lets grub2 count down to correctly work.

---

### Post by kansasnoob on 2009-10-18
> **davidmohammed said:**
> query -please can some one confirm an observation with grub2

I disabled legacy USB support in my bios - grub2 then does not automatically count down but waits for you to select the kernel to load.  Switching on legacy USB support in the bios lets grub2 count down to correctly work.

I'm like totally in a "duh" moment.

Why would you have to fiddle with anything in the BIOS to deal with grub?

---

### Post by davidmohammed on 2009-10-18
... I was looking at another problem about why my boot time was taking so long.  One thread I was looking at was reporting that removing legacy USB support reduced the boot time (something about the Kernel not having to do certain lookups).  Well, that didn't work.  However, I did notice the side-effect of Grub2 not performing the normal count-down if you remove USB legacy support from the bios.  Bizarre I know.

---

### Post by VMC on 2009-10-18
> **davidmohammed said:**
> ... I was looking at another problem about why my boot time was taking so long.  One thread I was looking at was reporting that removing legacy USB support reduced the boot time (something about the Kernel not having to do certain lookups).  Well, that didn't work.  However, I did notice the side-effect of Grub2 not performing the normal count-down if you remove USB legacy support from the bios.  Bizarre I know.

Perhaps once usb is enabled it looks for any active devices. Did you have any external usb device attached at the time you installed karmic?

---

### Post by davidmohammed on 2009-10-19
No - its just a laptop with a usb mouse connected.  The laptop was an upgrade from jaunty to karmic - but no other usb devices were connected at the time of the upgrade.
This is just a minor obs - just wanted to know if anybody else can replicate this.

---

