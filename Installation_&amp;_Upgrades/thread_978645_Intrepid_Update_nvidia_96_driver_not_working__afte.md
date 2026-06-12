---
title: "Intrepid Update: nvidia 96 driver not working * after following instructions"
date: 2008-11-11
forum: Installation &amp; Upgrades
---

### Post by eskhool on 2008-11-11
Hi all,
 I've tried everything tried here and looked around on launchpad and google as well. Here is the setup:

- AMD Duron 700 MHz machine, GeForce2 MX400 card, worked fine with Compiz, nvidia binary driver in Hardy.
- Upgraded to Intrepid from Hardy...all went fine (besides the warning about the degradation of driver)...nv driver worked fine.

Now, after reading this thread, I've enabled the proposed repository per comment 51 and installed the nvidia 96 package (96.43.09) ...confirmed the version in synaptics.

The error in the Xorg.0.log:

(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0): enabled.
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0): *** Aborting ***
(II) UnloadModule: "nvidia"

------------------------
apt/term.log:

Setting up nvidia-96-kernel-source (96.43.09-0ubuntu1) ...
Cleaning up the DKMS tree
Done.
Removing all DKMS Modules
Done.
Adding Module to DKMS build system
driver version= 96.43.09
Doing initial module build

Error! Bad return status for module build on kernel: 2.6.27-7-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/nvidia/96.43.09/build/ for more information.^MInstalling initial module^M^MError! Could not locate nvidia.ko for module nvidia in the DKMS tree.^MYou must run a dkms build for kernel 2.6.27-7-generic (i686) first.
Done.
---------------------
/var/lib/dkms/nvidia/96.43.09/build# cat make.log
DKMS make.log for nvidia-96.43.09 for kernel 2.6.27-7-generic (i686)
Tue Nov 11 01:15:26 IST 2008

The C compiler 'cc' does not appear to be able to
create executables. Please make sure you have
your Linux distribution's gcc and libc development
packages installed.

*** Failed CC sanity check. Bailing out! ***

make: *** [select_makefile] Error 1

------------------------------------------------------------------------

I've tried building dkms build manually but I keep getting the same error and google isn't of much help.

Kernel: 2.6.27-7
Ubuntu Intrepid 8.10 (Upgraded from Hardy 8.04)
(Envy-ng was installed earlier but has been removed)

Thanks a lot in advance,
Anshuman

---

### Post by Repabil on 2008-11-12
I also got problems with this driver and I've got the same gfx card. Would appreciate any help.

---

### Post by Partyboi2 on 2008-11-12
Have you got build-essential package installed?

---

