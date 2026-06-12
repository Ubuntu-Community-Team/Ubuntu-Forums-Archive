---
title: "Problems with 6.06 kernel after upgrade"
date: 2006-06-30
forum: Installation &amp; Upgrades
---

### Post by wgscott on 2006-06-30
I updated to 6.06 from 5.10 using apt-get.  Everything seemed to work fine until I rebooted, or more accurately, didn't reboot.

In grub, I was able to reboot in the previous kernel, and then I reinstalled the new kernel.  After that, I was able to reboot in the new kernel, but the reboot hangs where it needs to communicate with the nvidea driver.  It all works fine with the previous kernel, so I reinstalled all the video driver stuff, and I am still having the problem, but only with the most recent kernel.

Other minor irritations:

gl.h was not present until I force-reinstalled the mesa dev files.

Although my /etc/fstab is unchanged, my nfs disks are no longer mounted.  They appear as icons on the desktop, but aren't mounted.  WTF?

But I am mainly worried about the new kernel.  Should I keep reinstalling it until it works, or what?  

:confused:

---

### Post by wgscott on 2006-06-30
Specifically, here is the entry from the log file:


(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found



Again, this works fine with the previous kernel.

---

### Post by tseliot on 2006-06-30
Try this:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#WHAT_HAPPENS_IF_YOU_CHANGE_YOUR_KERNEL_OR_IF_YOUR_KERNEL_IS_UPDATED](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#WHAT_HAPPENS_IF_YOU_CHANGE_YOUR_KERNEL_OR_IF_YOUR_KERNEL_IS_UPDATED)

---

### Post by wgscott on 2006-06-30
Thanks very much.  I have in fact already used method 1, and I can verify that everything works perfectly with the earlier revision (2.6.15-23-386) of the kernel.  The problem is specific to 2.6.15-25-386.  I'll go through the whole thing again later today just in case I missed something.

---

### Post by wgscott on 2006-06-30
Well, I got it to work.  I installed every package with "686" in it and suddenly I have a proper functioning kernel.  So, oddly, revision 23 worked fine, but revision 25 required one or more new packages to work on my i686 machine.  

Thanks for your help, and great website.  (I have a similar sort of thing going for OS X).

---

