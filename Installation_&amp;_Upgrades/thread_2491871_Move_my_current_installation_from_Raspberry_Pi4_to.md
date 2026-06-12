---
title: "Move my current installation from Raspberry Pi4 to Raspberry Pi5"
date: 2023-10-24
forum: Installation &amp; Upgrades
---

### Post by sblantipodi on 2023-10-24
Hi all... I have an Ubuntu 23.10 server installation on my USB SSD running on a Raspberry Pi4.


I have ordered a Pi5, 
can I simply detach the USB SSD from the Pi4 and connect it to the Pi5?


Will it work?

---

### Post by MAFoElffen on 2023-10-24
Well I hear after a point in time in 2021, Rasp Pi changed their EEPROM firmware, where it will boot straight from USB without the MicroSD card, if the MicroSD card is not there. Don't quote me on that. That is just what I heard. (I really need to look that up.)

My Pi4 is older, where you "had" to change the firmware setting to tell it what boot order you wanted.

---

### Post by sblantipodi on 2023-10-24
I changed the boot order of my Pi4 to boot from USB SSD but apart this...
is the OS installed on a Pi4 "compatible" with a Pi5?

---

### Post by TheFu on 2023-10-24
They use different GPUs, so probably not.

---

