---
title: "Nvidia fails after applying updates"
date: 2012-08-20
forum: Installation &amp; Upgrades
---

### Post by gdesilva on 2012-08-20
Hi, I have been running Ubuntu Studio 12.04 with no problems till this afternoon....applied the regular updates and now x server fails stating that there is a mismatch between the driver version and the kernel module.

I would appreciate if someone can tell me how to revert back to the the old kernel module or find the new driver.

Many thanks.


EDIT: OK, I found a work around by 

1. rmmod nvidia
2. depmod <old nvidia-295 >

The latest kermel module is 304.xx - where can I find the nvidia-304 driver to avoid the mismatch of kernel module and driver versions?? Thanks

---

### Post by efflandt on 2012-08-21
Did you use nvidia-current package that was automatically installed during 12.04 installation (if installed on a system with nvidia)?  With that, or even if you added x-swat ppa, nvidia driver should update automatically and remain coordinated with kernel modules.  However, you need to reboot after kernel updates.

If you ran a script that you downloaded from nvidia website, Ubuntu package manager knows nothing about that, so you may need to rerun that script (or updated version of it) after kernel updates (some program updates also mention nvidia).

---

### Post by gdesilva on 2012-08-21
@efflandt, Thanks for the response. After doing the workaround as above, I tried to reinstall the driver and got the black screen of death - the system was totally unresponsive and since I had a backup of my data, I decided to just go ahead and reinstall. Cannot recall exactly what I did, but I did have a copy of nvidia-295.run and it is quite likely that I would have installed the driver using the script. All is good now - many thanks for your suggestions.

---

