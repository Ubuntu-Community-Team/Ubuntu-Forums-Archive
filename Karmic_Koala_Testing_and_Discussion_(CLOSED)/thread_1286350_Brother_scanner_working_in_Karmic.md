---
title: "Brother scanner working in Karmic?"
date: 2009-10-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mmcmonster on 2009-10-08
Anyone get a Brother scanner to work in Karmic without running xsane as root?

I tried the directions for Ubuntu 9.04 mentioned [here]("http://solutions.brother.com/linux/en_us/instruction_scn1c.html#u9"), but still no joy. :-(

---

### Post by Coltman on 2009-10-10
i had the same problem
i tried lsusb in terminal but the scanner did not show up
so i tried sudo lsusb
then my scanner showed up
my scanner was on Bus 004 Device 003: ID 04f9:01a8 Brother Industries, Ltd DCP-130C
i went to dev/bus/usb/bus 4 and device 3 was root owned
i opened it as root and changed it to my user name and took ownership
now xsane works
i am sure there is an easier way but this works for me

---

### Post by briancb on 2009-10-16
This worked for me.

---

### Post by briancb on 2009-10-16
Trouble is you have to do this every boot, as you say there must be an easier way

---

