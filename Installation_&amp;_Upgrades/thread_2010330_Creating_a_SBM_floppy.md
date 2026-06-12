---
title: "Creating a SBM floppy"
date: 2012-06-25
forum: Installation &amp; Upgrades
---

### Post by ronoweb on 2012-06-25
Need help creating SBM floppy as described in install folder of the installation disc. Floppy is supposed to help boot to install on old or out dated bios. I can't figure out how to put sbm.bin on floppy to make it bootable. refer to readme in install folder of 11.04 or 12.04

---

### Post by sudodus on 2012-06-25
Are you planning to create it for a particular computer? In that case, please let us know the specification:

- brand name and model (if available)
- cpu type and speed
- ram type and size
- graphics chip or card

If you are planning to make something more general, maybe you should look at some really small distro, for example

- DSL [[COLOR="Red"]_http://damnsmalllinux.org/faq.html_[/COLOR]]("http://damnsmalllinux.org/faq.html")

---

### Post by black veils on 2012-06-25
use this to allow booting from usb, put it on a floppy, then boot from your usb: [http://www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/](http://www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/)

---

### Post by plucky on 2012-06-25
> **ronoweb said:**
> Need help creating SBM floppy as described in install folder of the installation disc. Floppy is supposed to help boot to install on old or out dated bios. I can't figure out how to put sbm.bin on floppy to make it bootable. refer to readme in install folder of 11.04 or 12.04

In Linux,try from a terminal ```
dd if=sbm.bin of=/dev/fd0
``` 

fd0=fdzero 

Assuming you are in the same directory as the sbm.bin file.

Good Luck

---

