---
title: "SHIM UEFI boot message on encrypted laptop 16.04.1 (with AMD R7 M370 video)"
date: 2016-12-16
forum: Installation &amp; Upgrades
---

### Post by dpcole72 on 2016-12-16
I downloaded the new video driver from AMD's website and installed to the letter, also ensuring my user profile was in the "video" group.  

Before rebooting, the driver install asked me  to disable Secure Boot and create a passcode - which I did.  After rebooting, I immediately get a SHIM UEFI screen for 8 seconds and then the system boots, asking me for the passcode to boot and so on--

To make a long story short, with the bizarre hangup it was safe I pretty much toasted the Ubuntu install so I reformatted/reinstalled from scratch, *without any encryption of the SSD or Home directory*, after disabling UEFI Secure boot - but still got the blue SHIM EFI screen anyway.  I ignored it and then reinstalled the new video drivers, paying more attention to how GLXGEARS wouldn't load because it couldn't get a RGB double-buffer visual, or how the whole system would lock up/freeze when going to shut down...  (Note that 16.04.1's vanilla install w/ "download from internet" enabled does install the open source Radeon driver that allows Glxgears to run.)  Still had the shutdown lockup and double-buffer visual error...

I reformatted again, going back to the standard installation with encryption of the SSD and home folder.  Being a laptop, if it gets stolen and all...

For issues I know are video driver-related I'll send my findings to AMD (it's great to see these newer versions being supported!!)  But it seems like I'm stuck with an extra 8 second boot process because of this SHIM UEFI thing.  How can I disable all that?  Before the last reinstall I had set the secure boot back to Enabled and the latest install (I would guess?) would have updated everything accordingly?  

If I need to reformat again as part of the process, that's no problem.  I've yet to fully restore my VM and doublecheck VMWare to see if I have to tweak to re-enable 3D acceleration from before (the very first installation prior to attempting AMDGPU-PRO was using the HD530 video integrated in my i7-6820HQ CPU, the first reformat to 16.04.1 installed the open source generic Radeon driver "AMDGPU" (non-Pro).)

Specs:
Dell Latitude e5570
16GB RAM
i7-6820HQ CPU w/HD530 GPU
AMD R7 M370
Ubuntu 16.04.1

Thanks!

---

