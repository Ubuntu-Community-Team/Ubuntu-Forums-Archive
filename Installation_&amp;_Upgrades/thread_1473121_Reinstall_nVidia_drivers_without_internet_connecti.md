---
title: "Reinstall nVidia drivers without internet connection?"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by matchu on 2010-05-04
Dang, I don't even know what I did at this point.

I upgraded to Lucid easily enough. I hit an error message at first regarding low-graphics mode, so I had Ubuntu set it back to the default graphics configuration and rebooted. All seemed fine.

Once I got in, my screen resolution was 800x600, which isn't ideal, so I tried to figure out how to fix it. The Monitors menu said I had no monitors, and the Hardware Drivers said I had the nVidia driver installed, but running nvidia-settings said that I did not. I tried reinstalling the nVidia drivers a few times, with no luck.

Eventually, it wouldn't shut down correctly, so I held down the power button and killed it. Then I got impatient during an hours-long file check on next boot, and did a hard reset on that. (I now know what a horrible idea that is.) I ran a fsck from a gparted live CD, so that seems taken care of.

**So, now here's where I am.** I boot into Ubuntu, and am taken straight to a command line. startx says:

"Error: API mismatch: the NVIDIA kernel module has version 190.53, but this NVIDIA driver component has version 195.36.15."

My guess is that a simple removal of all nVidia packages and reinstalling the latest of each would solve my problem. However, for whatever reason, Ubuntu can't get far enough thru the boot process to start networking, so I can't connect to the repositories to install missing packages. ("wget http://www.google.com/" informs me that google.com can not be resolved, and "sudo apt-get update" tells me that it fails to download from any repository.)

I know that this is little technical information. What sort of files, if any, would it be helpful for me to type out?

Thanks!

EDIT: figured out enough to set up the vesa driver for xorg.conf, which seems to allow me to boot all the way through. I'll play around with it a bit more...

EDIT 2: GOT IT! Once vesa drivers installed, did "sudo apt-get remove nvidia-*", "sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings", "sudo nvidia-xconfig", reboot worked like a charm. Thanks for letting me think out loud, and here's hoping this helps someone!

---

### Post by cabbrick1243 on 2010-05-08
Hi, could you please explain how you got xorg.conf to start from the vesa driver? I followed some terrible guide trying to install my invidia driver and guess what was removed before it could be all tehway finished?

---

### Post by matchu on 2010-05-12
Here's what I typed into the file:

```
Section "Device"
    Identifier     "Stupid Temporary Vesa Device"
    Driver         "vesa"
EndSection
```

---

