---
title: "Clean install USB just flashing cursor"
date: 2016-10-01
forum: Installation &amp; Upgrades
---

### Post by peterqb on 2016-10-01
Used Ubuntu running in VBox to create a bootable USB using startup disk creator. It seems to have done that sucessfully, but when I try to install on a Toshiba Satellite there is just a flashing  cursor.

Is there anything I can check? I thing the iso file downloaded properly, and the USB stick works. The computer has been showing occasional errors, but has worked none the less. An upgrade from 14.04 finished with the computer shutting itself down and what I conclude is a corrupted OS.

TIA

---

### Post by colmax on 2016-10-01
would suggest don't make boot-up or install stuff in a virtual environment
Mayb use LinuxLive or UnetBootin in windows or your main os
If your system refuses to boot from usb burn the iso to dvd and boot from that
cheers

---

### Post by peterqb on 2016-10-01
Thanks, colmax.
In the end I found this site:
[https://en.opensuse.org/SDB:Create_a_Live_USB_stick_using_Mac_OS_x](https://en.opensuse.org/SDB:Create_a_Live_USB_stick_using_Mac_OS_x)
It did the trick.

If anyone uses this give the computer time to write to the USB.

---

