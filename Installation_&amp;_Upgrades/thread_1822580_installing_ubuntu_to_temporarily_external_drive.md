---
title: "installing ubuntu to temporarily external drive"
date: 2011-08-10
forum: Installation &amp; Upgrades
---

### Post by bollschweiler on 2011-08-10
I don't have access to a CDROM drive or a USB flash drive.  I have access to three IDE hard-drives (let's call them S="source", T="target", and E="extra"), and a single USB enclosure.

On S there are two partitions; on the first partition, Windows 7 is installed, and on the second, Windows 2000 is installed.  Wubi was executed within Windows 2000 and Ubuntu installed on that same partition.
On booting, the Windows 7 boot selector is shown; it now includes Ubuntu as an option, but selecting this option fails.  However, upon selecting Windows 2000 from the Windows 7 boot menu, a Windows 2000 boot menu appears; Ubuntu is an option here and booting is successful.  

From Ubuntu, I ran LVPM in order to copy this installation onto drive T, which had been loaded into the USB enclosure.  This procedure completed successfully.  However, when I removed T from the USB enclosure and placed it in the primary internal IDE hard-drive slot, a grub boot menu appeared.  The options on the grub menu were "UnknownOS" and "Windows 7 (loader)".  Selecting either of these resulted in failure.

Consequently, I would like to try a different approach.  I would like to install Ubuntu to T from within the Wubi Ubuntu on S.  Alternatively, perhaps it would be possible to alter the boot sequence on T in order for it to boot directly into Ubuntu.

Thanks in advance!
nate

---

### Post by lmarmisa on 2011-08-10
Welcome to the forums!!!. :D

If you want to install Ubuntu to T from the Wubi Ubuntu on S, you could install the package **ubiquity-frontend-gtk**:

```

sudo apt-get install ubiquity-frontend-gtk

```

Finally select System -> Administration -> Install RELEASE. If you wish to install the GRUB loader in the MBR of the hard drive T, consider to define manually the partitions of the installation.

Best regards,

Luis

---

### Post by bollschweiler on 2011-08-11
Thanks for your quick response Luis!  Unfortunately I wasn't able to test it out the method you outlined.

For folks in this position in future, I'll briefly outline the steps employed.

Running from the Wubi-made Ubuntu install on S, I placed E within the enclosure, attached it via USB, and transformed it into a startup disk using Startup Disk Creator (System->Administration->Startup Disk Creator): first I erased E by, after choosing the appropriate drive from the lower list, selecting "Erase Disk"; next, I set up E to be a startup disk by, after choosing the correct disk image (pressing the button "Other..." and browsing to and selecting the .iso file), selecting "Make Startup Disk".

Next I shut down the computer and replaced S with T, keeping E attached via USB in the external enclosure.  Rebooting, I altered the boot order to boot from E rather than T (it was still booting grub).  At this point I booted from E and was able to install Ubuntu without any difficulty.

Hope someone out there somewhen finds this useful.
nate

---

