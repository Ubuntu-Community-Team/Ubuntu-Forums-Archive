---
title: "nvidia glx/kernel mismatch in edgy"
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by spiderworm on 2006-10-31
Hello,

Just upgraded to edgy, and now I am getting this error when trying to restart the X server..

"This server has a video driver ABI version of 1.0 but this driver is designed to work with versions before 1.0.  The driver will continue to load, but may behave strangely."

... and ...

"Version mismatch detected between the NVIDIA X driver and the NVIDIA GLX module.  X driver version: 1.0-8762; GLX module version: 1.0-8774.  Please try reinstalling the NVIDIA driver"

I tried this:

apt-get remove linux-restricted-modules-`uname -r` nvidia-glx
apt-get install linux-restricted-modules-`uname -r` nvidia-glx

... to no avail.

Any ideas on fixing this mismatch?

Thanks in advance,
spiderworm

---

### Post by The J on 2006-10-31
I had this error as well.  I fixed it by following tseliot's guide [here]("http://doc.gwos.org/index.php/Latest_Nvidia_Edgy") and using Method 2.  For this you'll need to get an installer from nVidia's website.  I used the beta 9625 x86_64 driver. I uninstalled all the old nVidia drivers first.

The only difference is that there is a part in the guide that says to run
```
sudo sh NVIDIA-Linux-x86_64-1.0-8776-pkg2.run **-n -s** --x-prefix=/usr/lib64/xorg/ --kernel-source-path=/usr/src/linux-headers-`uname -r`
```

The way I got it to work correctly was to remove the bolded "-n -s" from the command.  Read the guide first before doing anything so you can get the instructions you need for your system.

---

