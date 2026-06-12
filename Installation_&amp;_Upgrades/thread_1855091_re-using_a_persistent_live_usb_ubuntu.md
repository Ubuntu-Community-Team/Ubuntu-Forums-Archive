---
title: "re-using a persistent live usb ubuntu"
date: 2011-10-05
forum: Installation &amp; Upgrades
---

### Post by h313 on 2011-10-05
booting ubuntu from usb helps overcome a lot of issues in my day to day work. 
I recently found out that we can make persisten live usb of a distro to store settings and other data on the same live usb.
An easy method to create such a copy is given [here]("http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/")

however, please suggest me any other method which is easier than the one above.

Another important query regarding the same is; Can i clone my existing live usb to create multiple persistent live usb copies of the same usb.
Or can i back up the whole os to use the same persisten os again.

---

### Post by Rebelli0us on 2011-10-05
You can do a regular install from Desktop CD and point to the USB drive and also make sure to select the option to boot from the same drive as well (so this will install grub on the USB as well).

Or use 
System > Administration > "Startup Disk Creator"

... should give you the same result.

---

