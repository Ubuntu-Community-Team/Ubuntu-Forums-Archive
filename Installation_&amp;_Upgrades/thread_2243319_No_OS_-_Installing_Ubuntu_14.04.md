---
title: "No OS - Installing Ubuntu 14.04"
date: 2014-09-07
forum: Installation &amp; Upgrades
---

### Post by bearacid2 on 2014-09-07
I have a Toshiba Satellite C55t-B5230 that had Windows 8.1 pre-installed.  So after failing miserably with installing Ubuntu from Windows 8.1, I tried using the Toshiba Utility to format my hard drive. I selected erase all partitions and data. When it was complete I restarted the machine and it read "Reboot and select proper Boot device or Insert Boot Media in selected Boot device and press a key".  I put in my thumb drive with the Ubuntu ISO on it in and pressed enter. The message repeated and did not boot. I tried this several times and did the F12 and looked at the settings and USB was first in the boot order. Then I burnt a DVD with and tried it with the same result. I am trying to install Ubuntu 14.04 and have used Ubuntu on many pc's in the past. This is a brand new computer, any help is appreciated.

---

### Post by Vladlenin5000 on 2014-09-07
Hi, welcome.

A few comments:

1. You need to select the correct boot device before the computer complains about the absence of an OS.
2. Considering that it came with Windows 8.1 pre-installed then it has the new UEFI instead of the old BIOS (the one you're used to). Things aren't as simple as before. Read here:  [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
3. Considering you don't want to dual boot - you'd have to reinstall Windows otherwise - you probably can disable the new advanced features and turn the UEFI into a compatibility mode that works for the most part as the old BIOS did. Ubuntu will be fine either way. How to change those settings vary a lot from vendor to vendor -> Consult your model's documentation about it.

---

### Post by bearacid2 on 2014-09-08
Thank you, this was very helpful. Just needed a little bump in the right direction. :)

---

