---
title: "Cannot boot anymore other than Win 10"
date: 2018-06-05
forum: MINT
---

### Post by Algar on 2018-06-05
Hi,

My laptop got repaired and after this only win10 is starting as it was the unique operating system installed in the laptop.
Before sending the laptop to reparation, I had a Linux install alongside. The guy from the reparation the RAID in the SATA configuration mode in the bios :(

I used a usb key with a linux inside and can see the partitions.
Tried to use boot-repair but does not work :(
Details with the partitions here:
[http://paste.ubuntu.com/p/CKWKdnnTvJ/](http://paste.ubuntu.com/p/CKWKdnnTvJ/)

Please help me.

---

### Post by Quarkrad on 2018-06-05
I've had this problem - my solution was to reboot and go into bios (hit Del key normally).  Go to the boot order - it is probably set on Windows (boot manager), change this to ubuntu, Save and reboot.  You should now boot to your grub screen.  (Also, you may need to boot into Win10 and check your Power settings. Make sure the laptop is set to shut down completely and not in hibernation mode when you power off/shut down.  There are plenty of instructions on 'Google' on how to do this).

---

### Post by Algar on 2018-06-05
Hello,

Thanks for your reply.

In BIOS if I change the RAID to IDE I see a new Boot option (SATA SM: SanDisk SD5SE2128G10). Choosing this produces the error :

"Reboot and Select proper Boot device or Insert Boot Media in selected Boot device and press a key"

Thanks!

---

### Post by oldfred on 2018-06-05
Moved to Mint.

If your installs are UEFI, be sure to boot live installer in UEFI boot mode and then add Boot-Repair to make UEFI repairs. It looks like you booted in BIOS mode.

---

### Post by Algar on 2018-06-05
> **oldfred said:**
> 
If your installs are UEFI, be sure to boot live installer in UEFI boot mode and then add Boot-Repair to make UEFI repairs. It looks like you booted in BIOS mode.

Thank you.
How can I boot live in UEFI mode?

The only option I see in BIOS is "Launch CSM". If I disable this, I cannot use the USB to boot. "Secure boot control" is disabled. USB configuration has "Legacy USB Support" Enabled and "XHCI Pre-Boot Mode" in Auto.

I don't see any other option possibly referring to UEFI.
What can I do to start in UEFI from USB?
Thanks

EDIT: If I deactivate "Launch CSM" a new option appears called "Fast Boot" that is disabled by default but it seems to me that I cannot use the USB anymore.

---

### Post by oldfred on 2018-06-05
Most UEFI have another setting for enabling USB boot particularly if UEFI Secure boot is on.
As USB boot when Secure Boot is on, is then not secure.

CSM is BIOS.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  
    
One of my systems has UEFI boot settings under the CSM (which seems backwards to me).
And many systems have "Windows" or "Other" where Other is Secure boot off as fine print says to use Other for Windows 7. Windows 7 does not support Secure Boot.

Be very careful with RAID. Make sure you have good backups.
The RAID could be RAID 0 which is striped or half on one drive and half on other drive. If you break that RAID, you have to reinstall. If RAID 1 or mirrored then you may be able to break RAID without destroying system.

RAID 0 is often used just for a system to game or compile software, where no data is on system. As if one drive fails all data is lost.
       Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

---

