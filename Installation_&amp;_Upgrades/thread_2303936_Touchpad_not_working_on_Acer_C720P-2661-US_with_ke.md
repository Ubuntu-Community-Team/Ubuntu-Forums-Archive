---
title: "Touchpad not working on Acer C720P-2661-US with kernel &gt;= 3.19"
date: 2015-11-22
forum: Installation &amp; Upgrades
---

### Post by nbr on 2015-11-22
I know problems with the touchpad in this Chromebook have been extensively talked about but no solution is working for me.

I have an Acer C720P-2661-US Chromebook and I installed Ubuntu 14.04.3. The default kernel is 3.19.0-33-generic, which should make the touchpad work out of the box but it doesn't.
The touchscreen works great but the touchpad does not respond.
The kernel seems to have the modules needed:

$ ls /lib/modules/3.19.0-33-generic/kernel/drivers/i2c/busses/i2c-designware-*
/lib/modules/3.19.0-33-generic/kernel/drivers/i2c/busses/i2c-designware-core.ko
/lib/modules/3.19.0-33-generic/kernel/drivers/i2c/busses/i2c-designware-pci.ko
/lib/modules/3.19.0-33-generic/kernel/drivers/i2c/busses/i2c-designware-platform.ko

But there are errors in dmesg:

[    0.919449] i2c /dev entries driver
[    3.279206] __add_probed_i2c_device failed to register device 0-67

I read every single thread I found about this problem but most people own the C702 without the touchscreen, which may have a different touchpad.
I tried other methods to make the touchpad work, including hugegreenbugs's Chromebook driver and Benson Leung's patch. None of these methods made the touchpad work.

I also tried kernels 4.1 and 4.3 from the official repository and downloaded from kernel.org.

Does anyone know how to make the touchpad work in the Acer C720P?

Thank you!

---

### Post by nbr on 2015-11-29
I solved my problem by installing stock Ubuntu 14.04.3 to make the touchscreen work and then installed Hugh Greenberg's GalliumOS kernel 4.1.6-galliumos version 30 to make the touchpad work.
Now both the touchscreen works (except two finger touch for right-click and pinch-to-zoom) and fully works in Google Chrome, and the touchpad also works as expected. Two finger touch on the pad activates right-click, the buttons work, pointer works fine.

Hopefully these fixes will be permanently added to future kernels and the Acer C720P will work under a regular Ubuntu installation!

The kernel was downloaded from: [http://galliumos.org/apt/pool/main/l/linux-upstream/](http://galliumos.org/apt/pool/main/l/linux-upstream/)
I used 4.1.6-galliumos_30_amd64, didn't try the others.

Thanks, Hugh, for all the hard work!!

---

