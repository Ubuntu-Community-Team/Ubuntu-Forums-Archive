---
title: "installing ubuntu on a 1gb usb pen drive"
date: 2006-05-15
forum: Installation &amp; Upgrades
---

### Post by laraza on 2006-05-15
Hello,
In order to install ubuntu on a usb pendrive I need to have control over the installer, that is I need to be able to type "expert" or "custom" so I can change some stuff necessary for the successful usb installation (i.e usb modules etc). I'm trying to do this on an ibm thinkpad x41 (a little black tank ;-) which has no cdrom nor floppy so I have to use another usb pendrive with syslinux and the kernel and initrd.gz from the installer in ubuntu archives (hd-drive/vmlinuz and netboot/initrd.gz) in order to start the installer. My problem is that I cannot enter this "expert" mode or "custom" or anything under this configuration. It always boots into the default "questionless" installation mode regardless of typing "expert" in the boot prompt or modifying the syslinux.cfg file. When the installer attempts to let the computer reboot to the newly installed system then the rest of the installation fails (cannot mount /root) because it doesnt load the usb modules necessary. Does anybody have an idea how to get to install in expert mode using an installer from a usb pendrive with syslinux? do I need to use a different installer kernel image? a different/modified initrd.gz?
Any help greatly appreciated.

laraza.

---

