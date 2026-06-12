---
title: "Upgrade kernel fail"
date: 2011-07-27
forum: Installation &amp; Upgrades
---

### Post by peu.buntu on 2011-07-27
Hi

I recently set up my notebook with Ubuntu Maverick (10.10). After installing, i updated it right away, downloading including newer versions of the linux kernel.
After all the downloads ended, the update-manager asked me if i would want to install/update the grub boot file to the newer kernel, but i accidentally said 'no'. 
The result is that i'm still booting with the kernel 2.6.35-22 that came with the installation.

Since it is already  downloaded, i didn't manage to resolve trough the UM itself. How can i work this out?
Also, i would like to remove the options to boot with the oldests kernels that usually apears on the grub list. 
I kwon that this is to boot safelly if there's something wrong in the new installation, so i will just do it after check that is all right.

Thanks in advance.
Cheers from brazil.

---

### Post by Bobhuber on 2011-07-27
> **peu.buntu said:**
> Hi

I recently set up my notebook with Ubuntu Maverick (10.10). After installing, i updated it right away, downloading including newer versions of the linux kernel.
After all the downloads ended, the update-manager asked me if i would want to install/update the grub boot file to the newer kernel, but i accidentally said 'no'. 
The result is that i'm still booting with the kernel 2.6.35-22 that came with the installation.

Since it is already  downloaded, i didn't manage to resolve trough the UM itself. How can i work this out?
Also, i would like to remove the options to boot with the oldests kernels that usually apears on the grub list. 
I kwon that this is to boot safelly if there's something wrong in the new installation, so i will just do it after check that is all right.

Thanks in advance.
Cheers from brazil.
I'm not quite sure what it asked you and what you did but if the update installed with the new kernal from a terminal > sudo update-grub should set the new kernal as the default.

---

