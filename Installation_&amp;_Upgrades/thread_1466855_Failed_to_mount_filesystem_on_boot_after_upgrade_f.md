---
title: "Failed to mount filesystem on boot after upgrade from 9.10 to 10.04"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by amrSamir on 2010-04-30
After upgrading and restarting my laptop, The purple splash screen hangs, and the terminal gives this message.

```

mount: mount point /proc/bus/usb does not exist
mountall: mount /proc/bus/usb [354] terminated with status 32
mountall: filesystem could not be mounted: /proc/bus/usb
...

```

Also the boot menu does not show (I cannot open the recovery mode).
Thanks in advance.

---

### Post by mikeashelby on 2010-04-30
Not sure if this is the same issue, but in my 'media' directory, I don't have any of my other partitions appearing. I've got a windows one, and a 9.10 one.

Any ideas?

Also, my 9.10 boot is knackered - won't load any of the gui since I installed 10.04.

---

### Post by PingerS on 2010-05-11
See [http://ubuntugenius.wordpress.com/2010/05/07/fix-an-error-occurred-while-mounting-procbususb-bootup-error-after-upgrade-to-lucid/](http://ubuntugenius.wordpress.com/2010/05/07/fix-an-error-occurred-while-mounting-procbususb-bootup-error-after-upgrade-to-lucid/)

I.e. 

sudo gedit /etc/fstab

Find the line “none /proc/bus/usb usbfs devgid=125,devmode=664 0 0” and either comment it using a # or delete the line.

---

