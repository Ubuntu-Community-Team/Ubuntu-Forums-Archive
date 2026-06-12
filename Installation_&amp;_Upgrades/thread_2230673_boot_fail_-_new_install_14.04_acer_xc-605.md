---
title: "boot fail - new install 14.04 acer xc-605"
date: 2014-06-20
forum: Installation &amp; Upgrades
---

### Post by johngrey on 2014-06-20
The live CD ran ok

I went through the normal install process, overwriting windows.

System now won't boot gives "reboot and select proper boot device ... message

live CD still boots as normal

In BIOS I've tried turning secure boot on and off
(I notice that main disk appears as 'ubuntu' but when in the drive the live/instalation disc appears as [UEFI: HL-DT-STDVDR...]) in the boot order list.

I've tried the boot-repair iso, but disks (and a USB) made from this don't boot - same error as above.

any ideas where to go next? thanks

---

### Post by ajgreeny on 2014-06-20
I suspect a problem has occurred as a result of the BIOS/UEFI problem.

You may have the machine set to legacy BIOS mode and booted the install USB/DVD in UEFI mode, or vice-versa.

The mode in which you boot the install medium is the mode that the OS will install, but that must match the setup of your BIOS.UEFI.

See [UEFI - Ubuntu Documentation]("https://help.ubuntu.com/community/UEFI") for all the details and how to sort out a solution.

---

### Post by johngrey on 2014-06-20
Thanks for this - but I am still struggling with this.  

I've been through the page above
There doesn't seem to be an obvious option to enable/disable UEFI in the bios on my machine - though there is a secure boot option - I assume this implies that the BIOS is set to EUFI.  The instalation DVD seems to go to UEFI mode looking at the screen shots in the page above. 
There is a launch CSM option in the Boot options which is set to never.
I have installed with and without secure boot enabled and have tried choosing 'something else' to explicitly set the mount point for the file system.

I've been through the installation several times - it always seems to go ok, but in the end the system won't boot.
I'm at a loss to know what to check.

---

### Post by johngrey on 2014-06-20
just to add I eventually got boot-repair to run but it didn't work.
 - lot of errors reported in this;  [http://paste.ubuntu.com/7677357/](http://paste.ubuntu.com/7677357/)

any ideas please?

---

