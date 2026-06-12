---
title: "Secure boot and Ubuntu&gt; 16.04"
date: 2016-05-22
forum: Installation &amp; Upgrades
---

### Post by EowynCarter on 2016-05-22
After banging my heads against walls for a while i finally learned what was causing my graphic card issue. Secure boot prevents installation of proprietary drivers. (among other things).

No proprietary drivers will be an issue for quitte a lots of people. Is that any plan to fix this other that "deactivate secure boot" ? 
Why, as I had the nvidia drivers installed, didn't the update told me to un-install them, to avoid a black screen at reboot ? Or at least warn me the update will cause such a severe regression ? That point really need to be sorted out before the July version. There are so many post with people going :confused: at issue with the AMD / nvidia drivers. So much for being user-friendly.

What about BIOS where secure boot can't be deactivated ? There people can't use ubuntu anymore ?

---

### Post by grahammechanical on 2016-05-22
> Secure boot prevents installation of proprietary drivers. (among other things).

I  doubt the accuracy of that statement very much. Since the release of  Ubuntu 12.10 (October 2010) Ubuntu has been secure boot compliant. On  our behalf Canonical went to the trouble of obtaining Microsoft  accreditation so that its developers could sign the Linux kernel in  Ubuntu to comply with the secure boot requirement. Many in the FOSS  community criticised Canonical for doing this. But Canonical put the  interests of its users over politics.

Proprietary video drivers  are just that. They are proprietary. There is not much the Ubuntu  developers can do with proprietary video drivers except pass bug reports  up to the owners of the driver. Sometimes they can patch the kernel to  mitigate the effects of buggy proprietary video drivers. And they do  that.

Ubuntu 16.04 comes with a version of the X Server that the  AMD proprietary video driver is not compatible with. AMD decided not to  do the work to bring its proprietary driver into compliance but to focus  its development efforts on its open source video driver amdgpu. This  left the Ubuntu developers no choice but deprecate the AMD drivers in  16.04.

The Ubuntu kernel team have done a lot of work back  porting patches from the Linux 4.5 kernel into the 4.4 kernel in 16.04  to improve things for users of AMD video adapters. This is reported on  in the 16.04 release notes as is the advice to users of 14.04 not to  upgrade until 16.04.1 is released.

Proprietary video drivers  often drop support for older hardware. The Additional Drivers utility  will not offer the newest drivers if they do not support our hardware.  On the other hand, if we (the user) download the latest driver from the  company's web site we should not be surprised if there are problems.  Especially if it needs to be signed to comply with secure boot  requirements. 

Some people rant. Some people test. They test the  development version of Ubuntu. Some even test release candidate kernels  & proprietary drivers before they get into the development version.  And they file bug reports.

Which course of action is most likely to get issues fixed before the development version becomes the released version?

---

### Post by EowynCarter on 2016-05-22
The problem comes with SE linux in kernel 4.4 being more restrictive, and insisting the kernel module be signed. Meaning that if secure boot is on, you have to do a few trick to get it to work :
[http://askubuntu.com/questions/759995/after-upgrade-from-14-04-to-16-04-login-screen-runs-in-a-loop-while-console-logi](http://askubuntu.com/questions/759995/after-upgrade-from-14-04-to-16-04-login-screen-runs-in-a-loop-while-console-logi)

And having to go though this at each drivers or kernel update is just a big no.
I'm not talinking about getting the drivers from nvidia. I'm taking about installing them from the official ubuntu repository. It build the kernel module, but can't sign it, because we need canonical's key that we don't have. So at the very least, provide a warning and / or instruction to do the proper install.

Since when is 16.04 a development version ?? It's officially released since April...

---

