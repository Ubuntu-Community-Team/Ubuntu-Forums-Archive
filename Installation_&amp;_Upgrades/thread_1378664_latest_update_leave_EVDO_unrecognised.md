---
title: "latest update leave EVDO unrecognised"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by vaxman- on 2010-01-11
I user installed the latest updates as per the update manager.

My EDVO card will now not initialize.  No /dev/ttyUSBn devcies for it.

---

### Post by vaxman- on 2010-01-11
OK.  

I booted back to the prior kernel: 2.6.31-17-generic-pae and the EVDO card functions.  I issued: #modinfo sierra which yielded:
 
```
filename:       /lib/modules/2.6.31-17-generic-pae/kernel/drivers/usb/serial/sierra.ko
license:        GPL
version:        v.1.3.7
description:    USB Driver for Sierra Wireless USB modems
author:         Kevin Lloyd, Elina Pasheva, Matthew Safar, Rory Filer
srcversion:     736DAACD92CCAED5AFA759D
alias:          usb:v1199p68A3d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6893d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6892d*dc*dsc*dp*icFFiscFFipFF*
alias:          usb:v1199p6891d*dc*dsc*dp*icFFiscFFipFF*
alias:          usb:v1199p6890d*dc*dsc*dp*icFFiscFFipFF*
alias:          usb:v1199p6880d*dc*dsc*dp*icFFiscFFipFF*
alias:          usb:v1199p685Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6859d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6856d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6855d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6853d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6852d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6851d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6850d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p683Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p683Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p683Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p683Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p683Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6839d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6838d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6835d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6834d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6833d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6832d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6822d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6821d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6820d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6816d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6815d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6813d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6812d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6809d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6808d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6805d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6804d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6803d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6802d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0029d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0028d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0027d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0026d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0025d*dc*dsc*dp*icFFiscFFipFF*
alias:          usb:v1199p0023d*dc*dsc*dp*icFFiscFFipFF*
alias:          usb:v1199p0120d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0112d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0021d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0019d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0224d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0024d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0220d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0020d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0218d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v03F0p1E1Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v03F0p1B1Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0F3Dp0112d*dc*dsc*dp*ic*isc*ip*
depends:        usbserial
vermagic:       2.6.31-17-generic-pae SMP mod_unload modversions 586 
parm:           nmea:NMEA streaming (bool)
parm:           debug:Debug messages (bool)
```

The 2.6.31-17-generic-pae kernel was running the same v.1.3.7 version of the driver.  I visited the Sierra Wireless site and according to [this link]("http://sierrawireless.custhelp.com/app/answers/detail/a_id/500"), the 2.6.31 kernels should be running version v.1.7.12 of their driver.  So, I downloaded the appropriate zipped tar source, and built and installed v.1.7.12 for 2.6.31-18-generic-pae.  Now, when I issue # modinfo sierra, I see:

```
filename:       /lib/modules/2.6.31-18-generic-pae/kernel/drivers/usb/serial/sierra.ko
license:        GPL
version:        v.1.7.12
description:    USB Driver for Sierra Wireless USB modems
author:         Kevin Lloyd, Elina Pasheva, Matthew Safar, Rory Filer
srcversion:     34939526BDA39C74B3E6CE1
alias:          usb:v1199p68A3d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6893d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6892d*dc*dsc*dp*icFFiscFFipFF*
alias:          usb:v1199p6891d*dc*dsc*dp*icFFiscFFipFF*
alias:          usb:v1199p6890d*dc*dsc*dp*icFFiscFFipFF*
alias:          usb:v1199p6880d*dc*dsc*dp*icFFiscFFipFF*
alias:          usb:v1199p685Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6859d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6856d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6855d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6853d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6852d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6851d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6850d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p683Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p683Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p683Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p683Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p683Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6839d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6838d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6835d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6834d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6833d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6832d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6822d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6821d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6820d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6816d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6815d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6813d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6812d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6809d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6808d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6805d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6804d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6803d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6802d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0029d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0028d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0027d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0026d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0025d*dc*dsc*dp*icFFiscFFipFF*
alias:          usb:v1199p0023d*dc*dsc*dp*icFFiscFFipFF*
alias:          usb:v1199p0120d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0112d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0021d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0019d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0224d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0024d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0220d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0020d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0218d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v03F0p1E1Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v03F0p1B1Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0F3Dp0112d*dc*dsc*dp*ic*isc*ip*
depends:        usbserial
vermagic:       2.6.31-18-generic-pae SMP mod_unload modversions 586 
parm:           nmea:NMEA streaming (bool)
parm:           debug:Debug messages (bool)
```

and the EVDO card functions once again.  It seems that these new kernel updates are being built with an old version of the sierra wireless driver.  They should update the build to use this v.1.7.12 driver.

---

