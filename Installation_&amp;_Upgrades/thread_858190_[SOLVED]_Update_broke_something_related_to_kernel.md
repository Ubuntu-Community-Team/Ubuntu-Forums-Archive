---
title: "[SOLVED] Update broke something related to kernel"
date: 2008-07-13
forum: Installation &amp; Upgrades
---

### Post by steelaz on 2008-07-13
Ubuntu 8.04 - 2.6.24-19.

Few weeks ago Update Manager was working on new updates and something went wrong. When I restarted my PC it would boot into "low graphics mode". So now I boot into older 2.6.24-18 and everything works well, but every time I'm installing something I get an error similar to this:

> 
WARNING: Module /lib/modules/2.6.24-19-generic/kernel/drivers/usb/serial/cypress_m8.ko is not an elf object
WARNING: Module /lib/modules/2.6.24-19-generic/kernel/drivers/usb/serial/cyberjack.ko is not an elf object
WARNING: Module /lib/modules/2.6.24-19-generic/kernel/drivers/usb/serial/funsoft.ko is not an elf object
WARNING: Module /lib/modules/2.6.24-19-generic/kernel/drivers/usb/serial/digi_acceleport.ko is not an elf object
WARNING: Module /lib/modules/2.6.24-19-generic/kernel/drivers/usb/serial/hp4x.ko is not an elf object
WARNING: Module /lib/modules/2.6.24-19-generic/kernel/drivers/usb/serial/cp2101.ko is not an elf object
WARNING: Module /lib/modules/2.6.24-19-generic/kernel/drivers/usb/serial/io_ti.ko is not an elf object
WARNING: Module /lib/modules/2.6.24-19-generic/kernel/drivers/usb/serial/keyspan.ko is not an elf object
WARNING: Module /lib/modules/2.6.24-19-generic/kernel/drivers/usb/serial/empeg.ko is not an elf object
WARNING: Module /lib/modules/2.6.24-19-generic/kernel/drivers/usb/serial/ftdi_sio.ko is not an elf object
WARNING: Module /lib/modules/2.6.24-19-generic/kernel/drivers/usb/serial/ipw.ko is not an elf object
WARNING: Module /lib/modules/2.6.24-19-generic/kernel/drivers/usb/serial/io_edgeport.ko is not an elf object
WARNING: Module /lib/modules/2.6.24-19-generic/kernel/drivers/usb/serial/ipaq.ko is not an elf object
WARNING: Module /lib/modules/2.6.24-19-generic/kernel/drivers/usb/serial/garmin_gps.ko is not an elf object
Failed to run depmod
dpkg: error processing linux-image-2.6.24-19-generic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-19-generic:
 linux-ubuntu-modules-2.6.24-19-generic depends on linux-image-2.6.24-19-generic; however:
  Package linux-image-2.6.24-19-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-19-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-19-generic:
 linux-restricted-modules-2.6.24-19-generic depends on linux-image-2.6.24-19-generic; however:
  Package linux-image-2.6.24-19-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-19-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-19-generic
 linux-ubuntu-modules-2.6.24-19-generic
 linux-restricted-modules-2.6.24-19-generic


Usually programs and updates install successfully regardless the error and I was hoping it will go away when I update kernel.

Today I tried updating kernel manually (using KernelCheck) and it failed with message above. Can someone help me with this?

Thank You.

---

### Post by bapoumba on 2008-07-13
Do you have an error output to :
```
sudo dpkg --configure -a
```

---

### Post by steelaz on 2008-07-13
Yes, its:

> 
Setting up linux-image-2.6.24-19-generic (2.6.24-19.34) ...
Running depmod.
WARNING: Module /lib/modules/2.6.24-19-generic/kernel/drivers/usb/serial/cypress_m8.ko is not an elf object
WARNING: Module /lib/modules/2.6.24-19-generic/kernel/drivers/usb/serial/cyberjack.ko is not an elf object
WARNING: Module /lib/modules/2.6.24-19-generic/kernel/drivers/usb/serial/funsoft.ko is not an elf object
WARNING: Module /lib/modules/2.6.24-19-generic/kernel/drivers/usb/serial/digi_acceleport.ko is not an elf object
WARNING: Module /lib/modules/2.6.24-19-generic/kernel/drivers/usb/serial/hp4x.ko is not an elf object
WARNING: Module /lib/modules/2.6.24-19-generic/kernel/drivers/usb/serial/cp2101.ko is not an elf object
WARNING: Module /lib/modules/2.6.24-19-generic/kernel/drivers/usb/serial/io_ti.ko is not an elf object
WARNING: Module /lib/modules/2.6.24-19-generic/kernel/drivers/usb/serial/keyspan.ko is not an elf object
WARNING: Module /lib/modules/2.6.24-19-generic/kernel/drivers/usb/serial/empeg.ko is not an elf object
WARNING: Module /lib/modules/2.6.24-19-generic/kernel/drivers/usb/serial/ftdi_sio.ko is not an elf object
WARNING: Module /lib/modules/2.6.24-19-generic/kernel/drivers/usb/serial/ipw.ko is not an elf object
WARNING: Module /lib/modules/2.6.24-19-generic/kernel/drivers/usb/serial/io_edgeport.ko is not an elf object
WARNING: Module /lib/modules/2.6.24-19-generic/kernel/drivers/usb/serial/ipaq.ko is not an elf object
WARNING: Module /lib/modules/2.6.24-19-generic/kernel/drivers/usb/serial/garmin_gps.ko is not an elf object
Failed to run depmod
dpkg: error processing linux-image-2.6.24-19-generic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-19-generic:
 linux-restricted-modules-2.6.24-19-generic depends on linux-image-2.6.24-19-generic; however:
  Package linux-image-2.6.24-19-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-19-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-19-generic:
 linux-ubuntu-modules-2.6.24-19-generic depends on linux-image-2.6.24-19-generic; however:
  Package linux-image-2.6.24-19-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-19-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-19-generic
 linux-restricted-modules-2.6.24-19-generic
 linux-ubuntu-modules-2.6.24-19-generic


---

### Post by bapoumba on 2008-07-13
Hmm..

Please try :
```
sudo apt-get install --reinstall linux-image-2.6.24-19-generic linux-restricted-modules-2.6.24-19-generic linux-ubuntu-modules-2.6.24-19-generic
```

---

### Post by steelaz on 2008-07-13
Didn't work. Got exactly the same error.

---

### Post by bapoumba on 2008-07-13
I guess the files got corrupted during the update.
Please try 
```
sudo apt-get dist-upgrade
```
and make sure you have **linux-generic** installed beforehand.

If none of this works, one option would be to download the packages and install them with dpkg, but i've never done this with a kernel package.. Not sure if it is even possible.

---

### Post by steelaz on 2008-07-13
Thanks for trying to help. The above command did not work.

I think I'll have to wait till new version of Ubuntu comes out and do a fresh install.

---

### Post by bapoumba on 2008-07-13
> **steelaz said:**
> Thanks for trying to help. The above command did not work.

I think I'll have to wait till new version of Ubuntu comes out and do a fresh install.
You're welcome :)
Why wait for a new version? Do you have special hardware (such as "serial") that prevents the -19 kernel from /installing/working properly ? May be if you blacklist the module, it could work, but I have no idea which module it could be.
I have been looking on the internets with this idea, but did not find anything relevant.

---

### Post by steelaz on 2008-07-13
No special hardware, it's just dell inspiron 8600 laptop and external usb drive.

I spent a lot of time moving my development platform (PHP, Apache, MySQL, Zend Studio, etc.) from windows, so I'm not too eager to do it again. Besides, everything else is working just fine. Now when Ubuntu 8.10 is released I will have good enough reason to do a fresh install.

---

### Post by steelaz on 2008-07-18
Well... this Linux thing seems to be pretty cool. This morning Update Manager offered me to do some updates related to kernel, so I did. Install went without a hitch, I rebooted and now my 2.6.24-19 kernel works like a charm. Whatever was in that update, it fixed my problem.

---

### Post by bapoumba on 2008-07-18
> **steelaz said:**
> Well... this Linux thing seems to be pretty cool. This morning Update Manager offered me to do some updates related to kernel, so I did. Install went without a hitch, I rebooted and now my 2.6.24-19 kernel works like a charm. Whatever was in that update, it fixed my problem.

Cool :)
here is the security notice I beleive you are talking about : [https://lists.ubuntu.com/archives/ubuntu-security-announce/2008-July/000728.html]("https://lists.ubuntu.com/archives/ubuntu-security-announce/2008-July/000728.html")

Imho, the security fixes described do not make me think they fixed your problem. I'd rather say the upgrade allowed the package to be downloaded again and be correctly reinstalled and configured. No matter what happened, welcome back :)

---

