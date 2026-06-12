---
title: "Windows 10 update messed UEFI boot setup"
date: 2018-11-30
forum: Installation &amp; Upgrades
---

### Post by brasilino on 2018-11-30
Hello!

I'm with a major problem in my Lenovo G50 laptop. When I bought it in 2016, I kept the original Windows 10 partition and installed Ubuntu 16.04.
The dual boot always worked fine.
But yesterday I had to run a Windows program and so booted it. It was updated in backgroud and changed somehow the UEFI  boot configuration. Dang!!
Now, the message I'm getting from the BIOS is: "Failed to load image \EFI\BOOT\grubx64.efi".
I can still boot Windows. 
After a lot of googling, I tried the "boot-repair-disk" image flashed in USB drive, which generated the following information log:

[https://paste.ubuntu.com/p/5XPRwJjbR9/](https://paste.ubuntu.com/p/5XPRwJjbR9/)

However, to "boot-repair-disk" repair boot procedure, it must be booted in UEFI mode. **But my Lenovo laptop doesn't allow me to boot from** [B]USB
in UEFI mode[/B]! I can only manage to boot from USB in legacy mode.  That's really frustrating!

One last thing, setting BIOS to "legacy mode", I can boot Windows, but not Ubuntu.

Any help or suggestion in my case? 

regards
Lucas

---

### Post by oldfred on 2018-11-30
If your system came with Windows pre-installed it has to be UEFI boot mode.
And report shows you installed Ubuntu in UEFI boot mode, so system must have let you boot installer in UEFI mode as that is the only way to get an UEFI install.

      But you now do not show any UEFI boot enties?

Major Windows updates will make Windows first in boot order. A reinstall of grub will make grub/Ubuntu first in boot order, so that is all normal.

But Windows updates usually turn fast start up back on and may turn UEFI Secure Boot back on.
And if UEFI Secure Boot is on, boot from flash drive is not allowed as that is not secure. BIOS/CSM/Legacy boot is only with Secure boot off, or system may let you boot that?
Check & change UEFI settings for Secure Boot and allow USB full support or boot.

Boot Windows and turn fast start up off, even if you have done that before.
      
 Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by ubfan1 on 2018-11-30
The error message looks like it would be from shim (running as /ERI/Boot/bootx64.efi) not finding grubx64.efi in the same directory.  Check the sizes, and if bootx64.efi matches shimx64.efi, just copy /EFI/ubuntu/grubx64.efi to /EFI/Boot/grubx64.efi.
You are booting the signed kernel for secure boot, so putting shimx64.efi as bootx64.efi would be correct for the install -- but grubx64.efi is required too, which is a (new?) bug.  
Lenovo's may let you select a preference, UEFI or legacy, but they will fall back to the other one if the preferred mode fails.  With a gpt disk, Windows requiring UEFI on gpt, and no bootloader in the MBR of sda, Windows must be booting in UEFI mode regardless of your order preference.  The order preference will boot the install media in legacy if that is the preferred, since the install media has both boot mechanisms.

---

