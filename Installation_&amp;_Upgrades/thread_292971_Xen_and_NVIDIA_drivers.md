---
title: "Xen and NVIDIA drivers"
date: 2006-11-04
forum: Installation &amp; Upgrades
---

### Post by frspin on 2006-11-04
I have installed on a new PC (Asus M2NPV-VM with a AMD X2 and a on-board GeForce 6150) latest ubuntu release (6.10)
For good video refresh I have to install package for restricted modules and nvidia drive (from Ubuntu repository). All is now working correct.

Now I want test XEN and I have installed, from Ubuntu repository, XEN, Xen kernel and restricted modules.
When I start XEN kernel X don't start with a message:

**Failed to load the NVIDIA kernel module!**

A lsmod show no nvidia module

A "modprobe nvidia" command produce an error:

**FATAL. Error running install command for nvidia**

I suppose this is a problem with lrm-video and so.
But I am no able to find a file named nvidia.ko so I suppose it is produced at boot time starting from files in nvidia directory of restricted modules.

If I use nv module, XEN work OK.
I can not use this solution because mv module, with my motherboard, have a very bad refresh time.

Regards
Franco

---

### Post by skenliv on 2006-11-09
You will have to use Nvidias install program to fix this.

---

### Post by stahnma on 2006-11-10
Doesn't the xen-restricted-modules-2.6.17-6-generic-xen0 provide the nvidia drivers for Dom0 already?  

I just installed it, though I am still having issues using it....

---

### Post by frspin on 2006-11-11
Nvidia drivers installed in Edgy restricted modules and Xen restricted modules have a different version.

So, if you boot Xen kernel you get new Nvidia graphic module but old Nvidia kernel module.

Installing from Nvidia package, after removing Xen restricted modules, and compile only kernel module for Xen kernel (you need to patch Nvidia module for using it in Xen) resolve the problem

---

### Post by jschneider on 2007-01-04
Can you explain the necessary steps to get Xen working with Nvidia? I have tried it many hours but did not succeed :(.

Thanks,

---

### Post by frspin on 2007-01-05
Download drive from Nvidia site
Download patch for Xen on same drive from Nvidia - I have used this link

[http://www.nvnews.net/vbulletin/showthread.php?t=77298](http://www.nvnews.net/vbulletin/showthread.php?t=77298)

Apply patch
Compile & install drive for both ordinary kernel and Xen kernel
No need to compile for ordinary kernel if used version is same as installed from Ubuntu repository.
No need to compile graphic module for same situation

When you reboot in Xen, new drive will be used, at same level as ordinary kernel and graphic Xorg module.

Regards

---

### Post by jschneider on 2007-01-12
Thanks for your fast response. I have read the answer but did not find the time to test it out. But I definitely will try it ;).

---

### Post by jschneider on 2007-03-02
The patch for the latest version is available here:

[http://www.nvnews.net/vbulletin/showthread.php?t=85037](http://www.nvnews.net/vbulletin/showthread.php?t=85037)

---

