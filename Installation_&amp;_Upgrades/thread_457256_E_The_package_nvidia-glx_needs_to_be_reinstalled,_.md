---
title: "E: The package nvidia-glx needs to be reinstalled, but I can't find an archive for it"
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by dreadlord_chris on 2007-05-28
That's the error that apt-get/Synaptic gives me - and then fails, no updates/installs possible.

This started after I got bored and decided to try my hand at compiling a new kernel ( [http://ubuntuforums.org/showthread.php?t=311158&highlight=compile+kernel](http://ubuntuforums.org/showthread.php?t=311158&highlight=compile+kernel) ). I got the new kernel from kernel.org - the latest stable 2.6.21.3. All *seemed* to go well with the compiling. Since I have an NVIDIA GeForce 7300 I knew I was going to have to reinstall the GPU drivers - so I changed xorg.conf to load the VESA drivers for the first boot into the new kernel. I booted to my desktop just fine. I fired up the latest Envy and tried to install the latest drivers - but got an error something about it not being able to find the kernel source. Envy told me to read the log - but it was empty. So next I tried installing by hand - downloaded the the driver package from NVIDIA (9755). Switch to tty1, shutdown kdm, and sudo run the installer. Again, install *seemed* to go fine - until I tried to start X - at which point I get a black screen w/ a blinking cursor.

A little frustrated, it's been a few hours since my box has been usable - so I reboot into the previous kernel (2.6.20-15) - everything seemed fine - except apt seems to be completely **borked**.

Things I have done/tried:
apt-get update - this works just fine, no errors
apt-get upgrade - I get the error in the subject line
apt-get remove -f nvidia-glx - same error
apt-get remove -f nvidia-glx --purge - same error
dpkg --configure -a - no errors but deosn't seem to have changed anything
apt-get install -d nvidia-glx - same error

So, I know it's something I did that screwed things up -but I'm at a loss as to how to fix it.

HELP!!

Update: ok, I fixed it. I downloaded nvidia-glx_1.0.8776-4_i386.deb from [http://packages.debian.org](http://packages.debian.org). Installed it, then uninstalled it. Everything wokrs now....

---

