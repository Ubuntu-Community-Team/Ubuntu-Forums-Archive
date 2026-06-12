---
title: "Upgrade 15.04 to 15.10 do-release-upgrade hang"
date: 2015-11-25
forum: Installation &amp; Upgrades
---

### Post by brucew2 on 2015-11-25
First, I must disclose this started with [FONT=courier new]do-release-upgrade[/FONT] from Kubuntu 14.04 (Trusty) to 15.04 (Vivid) which went okay but my Nvidia display card didn't have enough memory to manage SDDM so it was really slow and choppy despite updating to the latest driver version. Soon later, I was unable to get an login screen to show despite SDDM runnning. It would start then go straight to command line on [FONT=courier new]tty1[/FONT] and switching to [FONT=courier new]tty7[/FONT] showed an orange flashing cursor on a black screen. So, I installed a working Nvidia EVGA 9600GT-AR w/ 1GB, purged the Nvidia drivers and installed [FONT=courier new]nvidia-352 & nvidia-settings[/FONT]. Still did not fix the issue. So, I decided to upgrade to 15.10 as many people here reported has fixed their display issues.

Since I only have CLI access at this point, I performed [FONT=courier new]do-release-upgrade -d[/FONT]. All was going so well until it was setting up GRUB2 and just stopped cold there. I opened tty2 and ran [FONT=courier new]top[/FONT] to find that the [FONT=courier new]'wily'[/FONT] process was still running but not much change as far as processing is concerned. Just seemed to hang. I then ran [FONT=courier new]dmesg[/FONT] to see what happened and saw several entries for [FONT=courier new]"task systemd-udevd:1906 blocked for more than 120 seconds."[/FONT]

What does this mean and is it the reason the installation hangs at setting up GRUB2?
What more information is needed to determine a fix?

Thank you in advance.

---

### Post by grahammechanical on 2015-11-25
> as many people here reported has fixed their display issues.

I have not seen that. I am running 15.10 by the way and without problems with an Nvidia GT220 but I do need to use a legacy driver as the latest Nvidia drivers do not support the GT220 anymore.  I have just searched the Nvidia driver download site for a driver for the Nvidia 9600GT and it comes up with the 340.96 driver.

And I cannot see your card listed in the Supported Products tab for the 352 driver

[http://www.nvidia.com/download/driverResults.aspx/90279/en-us](http://www.nvidia.com/download/driverResults.aspx/90279/en-us)

Regards.

---

### Post by brucew2 on 2015-11-25
Oooh, I thought it was listed. Yep, you're absolutely right! Ok, I'll purge again and reinstall but either way, *this is not the problem of the moment*. It's stuck at "Setting up Grub2" and hasn't budged in 12 hours. What do I do? Reboot, then "sudo apt-get install -f" and/or "sudo dpkg --configure -a"?

---

### Post by brucew2 on 2015-11-26
Bump

---

