---
title: "boot from external encrypted USB HDD fails (7.10)"
date: 2007-12-27
forum: Installation &amp; Upgrades
---

### Post by R@llo on 2007-12-27
Hello all!

I installed 7.10 on an empty external USB HDD that is connected to my laptop. I used the alternate desktop CD, option 'full disc encryption using lvm' for this. The installation went through, but the system drops to busyox during boot with an error:
'ALERT! /dev/mapper/... does not exist!' (... is a name I don't remember). Some lines above there is a 'cryptsetup: Source device: /dev/disk/by-uuid/... not found'.
When I look in /dev/mapper, there is only control. As far as I understand it the USB HDD takes to long to get initialized. How can I solve this? The boot parameter rootdelay did not help.

I tried an installation with the same hardware without encryption and everything is fine, so this is no hardware issue. I need encryption and I would love to have it on 7.10, so any help is appcreciated! :KS

Thank you very much.

Regards,
Ralph

---

### Post by holahoo on 2008-03-07
Hi Ralph,

I have the same problem. Is yours solved?

Regards,

Hola

---

### Post by holahoo on 2008-03-07
In my case, I edited scripts/init-premount/ps3 (in initrd.img) by adding following lines after line case  "$DPKG_ARCH". It works for me.

  i386)
     modprobe ehci-hcd
     modprobe ohci-hcd
     modprobe uhci-hcd
     modprobe scsi-hcd
     modprobe usb-storage
     /bin/sleep 10
     modprobe sd_mod
     ;;

Enjoy,

Hola

---

### Post by R@llo on 2008-03-08
Hi Hola,

no, my problem is not solved yet.
Thank you very much for your reply and the hints to get it working!
Unfortunately it won't be possible for me to test your suggestion, because after I could not get it working I switched back to Debian, where an encrypted lvm installation is working even on an external usb disc.

Thanks again,

Ralph

---

### Post by biriachan on 2008-04-05
> **holahoo said:**
> In my case, I edited scripts/init-premount/ps3 (in initrd.img) by adding following lines after line case  "$DPKG_ARCH". It works for me.

  i386)
     modprobe ehci-hcd
     modprobe ohci-hcd
     modprobe uhci-hcd
     modprobe scsi-hcd
     modprobe usb-storage
     /bin/sleep 10
     modprobe sd_mod
     ;;

Enjoy,

Hola

I have Gusty (7.10) Installed on a USB drive, (encrypted-LVM) and would really like to get it working.  So far I have found out how to unpack the initrd.img file but ran into problems fully understanding how to modify the script, and then also how to recompress initrd.img.  Could you point me in a helpful direction in order to edit the initrd.img-2.6.22-14-generic file.

---

