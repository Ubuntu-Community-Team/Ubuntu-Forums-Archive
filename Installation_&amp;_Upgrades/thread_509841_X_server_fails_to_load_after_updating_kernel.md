---
title: "X server fails to load after updating kernel"
date: 2007-07-25
forum: Installation &amp; Upgrades
---

### Post by crhumber on 2007-07-25
I just compiled a custom kernel in order to fix some usb problems, and now I get the error message "Failed to load nvidia kernel modules".  I followed the instructions at 
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#WHAT_HAPPENS_IF_YOU_CHANGE_YOUR_KERNEL_OR_IF_YOUR_KERNEL_IS_UPDATED]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#WHAT_HAPPENS_IF_YOU_CHANGE_YOUR_KERNEL_OR_IF_YOUR_KERNEL_IS_UPDATED")
but that didn't help.  I already had nvidia-glx installed and working.  What else can I do to get this new kernel up and running?  thanks

---

### Post by crhumber on 2007-07-26
any help/advice whatsoever would be great!

---

### Post by DJMatty on 2007-07-26
Hi

I've had to re-install the official nvidia drivers every time that system update updates my kernel. I have an nvidia card that isn't supported by the legacy drivers that are in the repos, or at least it would never work when I tried the live CD, I could only get it to work in safe graphics mode.

In my xorg.conf file my device is set to "nvidia" not "nv", I think the "nv" device is the legacy driver. Which one is yours set to?

I used method 2 of this how-to, basically remove all the legacy drivers, download the driver from nvidia web site, and then install it. (I'm running feisty, and the link you posted was to a how-to for dapper, so I'm not sure if they will be the same)

[http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty)

Once you have the package downloaded from nvidia, (i assume you have all the other stuff needed to build the kernel) then this was the command I used to install it:

```
sudo sh NVIDIA-Linux-x86-100.14.11-pkg1.run -n -s --x-prefix=/usr/lib/xorg/ --kernel-source-path=/usr/src/linux-headers-`uname -r`
```

Put the name of the file you have downloaded from nvidia where the 'NVIDIA-Linux-x86-100.14.11-pkg1.run' is, this is the latest one, but the 9755 one has been around a while too. Notice the ` signs around the uname -r... they are not the regular apostrophes, but the other ones. Also you have to do this from a terminal that isn't in gnome, i'd suggest logging off and ctrl-alt-f2 out to a terminal, and maybe even stopping gdm. (I stop gdm from loading using rcconf and then reboot, just to be on the safe side, mainly because ctrl-alt-f2 didn't work with my video card, just got an empty screen)

Every time my desktop has failed to load it's been because of this, once I have re-installed the driver it all works fine again.

Matt

---

### Post by crhumber on 2007-07-26
thanks, djmatty, i'll give it a shot tomorrow

---

