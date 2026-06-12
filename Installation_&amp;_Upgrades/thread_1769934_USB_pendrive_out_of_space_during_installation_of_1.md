---
title: "USB pendrive out of space during installation of 11.04"
date: 2011-05-28
forum: Installation &amp; Upgrades
---

### Post by lightstream on 2011-05-28
While installing Ubuntu from USB (made with usb-creator), I began getting errors such as 'ubi-timezone has failed with exit code 1', with a retry / continue / cancel option, finally getting 'Installer has failed with exit code 1'

Now when I try to run Ubuntu directly from the USB key, it won't start properly, giving errors about zero drive space.

I'm now unable to continue the installation or even use Ubuntu from the USB!

How I can fix this? At least, how can I remove whatever has filled up the USB so I can run from it?

---

### Post by mörgæs on 2011-05-28
Try creating the USB stick with Unetbootin.

---

### Post by lightstream on 2011-05-29
Unetbootin worked - although it didn't seem to install any additional drivers, which this laptop needs for its WiFi. Therefore I wasn't able to get on the web to download them.

I'm about to try it again, this time having designated some space on the USB for remembering settings from a Live Session.

---

### Post by mörgæs on 2011-05-29
This is normal. Always have wired internet access while installing Ubuntu.

When that works, we can focus on the wirefree.

---

### Post by lightstream on 2011-05-29
> **mörgæs said:**
> This is normal. Always have wired internet access while installing Ubuntu.

Thanks for your help. I don't have a network cable here but it seems that tethering the laptop to my mobile phone was enough to allow it to install the proprietary wireless drivers.

I don't think my experience was entirely normal though.

The first attempt to install, using the usb-creator app, did appear to be working until I encountered the unexplainable 'out of memory' error. It was using the proprietary Wireless drivers during the install.

For some reason, the subsequent two attempts to install, using the unetbootin app, Ubuntu could not enable the proprietary WiFi driver until I'd got internet access by tethering my phone.

Anyway, so far it appears the installation is at last working correctly. Thanks again.

---

