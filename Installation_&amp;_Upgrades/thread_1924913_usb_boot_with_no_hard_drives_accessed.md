---
title: "usb boot with no hard drives accessed"
date: 2012-02-13
forum: Installation &amp; Upgrades
---

### Post by nobody00 on 2012-02-13
I want to boot into xubuntu installed on a USB drive without the OS having access to the two existing hard drives on the PC. In addition the USB drive, itself, would be hardware switched into read-only mode. In other words, I want the OS to run solely in memory (6GB). I realize that the boot sector will have to be accessed by the BIOS on the first drive, but thereafter the OS would not have access.

I have no intention of running this OS for long periods of time. I primarily want to use a browser and then shutdown.

Is this feasible and if so how can I get it to work? I realize there are linux boot options such as noprobe and nohd, but don't know if they are what I want nor do I know how to turn them on via an USB drive boot.

Thanks for your help.

---

### Post by gordintoronto on 2012-02-13
Use Puppy to run entirely from memory. However, it will still have write access to the hard drives.

---

