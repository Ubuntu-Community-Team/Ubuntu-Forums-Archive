---
title: "Install Intrepid daily alternate from USB memory stick--- multiple failures"
date: 2008-10-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by me13221 on 2008-10-12
Hello everyone,

I am trying to install the Intrepid daily alpha (alternate installer) from 2008-10-12 via USB memory stick.  I have worked around many problems but arrived at one that I cannot solve.  Briefly:

[LIST]
[*] I extracted the contents of the alternate-installer ISO to the memory stick, moved files from /isolinux to the root directory, copied the files from /install to the root directory, renamed isolinux.cfg to syslinux.cfg, edited text.cfg to remove references to /cdrom, all as described here:  [https://help.ubuntu.com/community/Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick") (using **manual** instructions.  Note: no instructions for Hardy or Intrepid, on that page or anywhere else that I could find).  After that point then I could access the GRUB menu on the target machine.

[*] the GRUB menu does not work.  No options work.  When I select 'Help' the boot prompt tells me "Invalid or corrupt kernel image."   I can boot manually by entering "[FONT="Fixedsys"]vmlinuz initrd=initrd.gz file=/cdrom/preseed/ubuntu.seed[/FONT]" at the boot menu.  The installer begins properly.

[*] At the first dialog, I follow the instructions further down on the above page to mount the USB stick on /cdrom.  


[*] The installer then fails to find any packages.  this is because USB sticks cannot contain symlinks.  I renamed /cdrom/dists/intrepid to /cdrom/dists/stable and that allowed the installer to proceed.

[*] The installer completes through HDD partitioning.

[*] Now I arrive at the problem I cannot solve.  At the menu item "Install the Base System", the installer reports "Failed to determine the codename for the release."  This error is fatal.  Syslog reports 

```
INFO: Menu item 'bootstrap-base selected
error: exiting on error base-installer/no_codename

```

[/LIST]

Any advice from here on?

Thanks in advance.

---

### Post by me13221 on 2008-10-13
Can anyone point me to a semi-official guide to installing an Intrepid daily build via USB stick?

---

