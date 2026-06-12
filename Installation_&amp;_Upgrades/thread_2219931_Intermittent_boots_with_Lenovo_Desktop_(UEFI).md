---
title: "Intermittent boots with Lenovo Desktop (UEFI)"
date: 2014-04-26
forum: Installation &amp; Upgrades
---

### Post by jessica9 on 2014-04-26
I am fairly new to Ubuntu, and tried to install Ubuntu 14.04 on a Lenovo K410 desktop. The desktop came pre-equipped with Windows 8, but I tried to install Ubuntu as a stand-alone OS because dual-boot with Ubuntu 12.04 worked only momentarily. I thought the problem was caused by a Windows update.

Here is the latest boot-repair link:
[http://paste.ubuntu.com/7333983/](http://paste.ubuntu.com/7333983/)

My partitions include an EFI boot partition, EXT4, and swap.

Ubuntu boots right after the install, but after the computer is restarted, I get the following error message:
"Error 1962: No operating system found"

I can trick the OS into booting if I press F12 during startup, but only after I run Ubuntu from a CD and restart from there. F12 from a subsequent restart shows entries from the boot manager, but leads to the error above. :confused:

I added a "Windows Boot Manager" entry to the UEFI boot manager as outlined below:
[https://forums.lenovo.com/t5/ThinkStation/UEFI-Mode-installation-of-Linux-distributions-on-Thinkstation/td-p/1018555](https://forums.lenovo.com/t5/ThinkStation/UEFI-Mode-installation-of-Linux-distributions-on-Thinkstation/td-p/1018555)

I tried installing Ubuntu in Legacy, and UEFI with quickboot and fastboot disabled. Only UEFI is close to working. I also tried everything from this thread:
[http://askubuntu.com/questions/141879/error-1962-no-operating-system-found-after-installing-12-04-lenovo-thinkcentre](http://askubuntu.com/questions/141879/error-1962-no-operating-system-found-after-installing-12-04-lenovo-thinkcentre)

What puzzles me is being able to boot immediately after using Ubuntu on a CD, but not otherwise. Weird? Never switching off my computer again, and doing the CD trick every time are not ideal solutions.

Thanks for your help!!!

---

### Post by ubfan1 on 2014-04-26
Well, the legacy boot doesn't work because the disk has a gpt partition table, so no room right after the Master Boot Block for the core.img, and you don't have a grub_bios flagged small 1M partition for it.  How does the UEFI boot fail?  Looks like you have a secure boot set up which should work.  Check that the efi boot is trying the shim, not the grub when you select ubuntu.   you can use sudo efibootmgr -v   to list the paths of the choices.  You can add the shim entry to the choices if not present, or turn off secure boot and use the grubx64 entry.

---

### Post by oldfred on 2014-04-26
Some others with Lenovo posted this:

 > Lenovo's  buggy EFI Bios is will not boot from a DVD at all unless you enable 'legacy' (which you can't do because it screws with Windows 8!)
 The work around was to turn ON 'Legacy' boot mode in the BIOS and turn OFF "secure-boot" mode from locking out Ubuntu), and also make sure to turn OFF 'Legacy' SATA AHCI to ATA.
Then I installed Ubuntu from a USB stick (because these settings would only boot the Ubuntu installer from USB, but not DVD). 

   
 linux	/boot/vmlinuz-3.5.0-25-generic.efi.signed root=UUID=07df2e4a-8ef3-4f35-9b9c-43bf0570d04b ro   quiet splash $vt_handoff
initrd	/boot/initrd.img-3.5.0-25-generic

 }
Another lenovo solution copy grubx64.efi to bootx64.efi & boot hard drive not anyother entry
[http://ubuntuforums.org/showthread.php?t=2185869&p=12884470#post12884470](http://ubuntuforums.org/showthread.php?t=2185869&p=12884470#post12884470)

---

