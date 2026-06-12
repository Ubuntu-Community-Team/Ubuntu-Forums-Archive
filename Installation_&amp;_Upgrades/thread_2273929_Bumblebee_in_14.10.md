---
title: "Bumblebee in 14.10"
date: 2015-04-16
forum: Installation &amp; Upgrades
---

### Post by stepheny on 2015-04-16
I have been using Bumblebee for years now to change my nVidia Optimus laptop from the onboard Intel GPU to the nVidia Geforce GPU when I watch DVD's or TV. Bumble works perfectly on my 14.04 32-bit partition, glxgears runs at 60 FPS but running "optirun glxgears" gives over 900 FPS. However in the new 14.10 64-bit partition running "optirun glxgears gives the same 60FPS as just glxgears. 

I have tried purging the nVidia drivers and Bumblebee installations and reinstalling them, installing different nVidia drivers etc but I cannot get the nVidia drivers to work at all.

Anyone else experience this problem?

---

### Post by stepheny on 2015-04-17
I have noticed that the NVIDIA X Server Settings is almost empty, so I launched it from the terminal and got this feedback. As it warned that Prime wasn't supported I ran  "sudo apt-get install nvidia-prime" but that didn't help. Can anyone tell me what is going wrong with the nVidia driver?

```
$ sudo nvidia-settings -V

WARNING: NV-CONTROL extension not found on this Display.


WARNING: Unable to determine number of NVIDIA GPUs on ':0'.


WARNING: Unable to determine number of NVIDIA Frame Lock Devices on ':0'.


WARNING: Unable to determine number of NVIDIA VCSs on ':0'.


WARNING: Unable to determine number of NVIDIA SDI Input Devices on ':0'.


WARNING: Unable to determine number of NVIDIA Fans on ':0'.


WARNING: Unable to determine number of NVIDIA Thermal Sensors on ':0'.


WARNING: Unable to determine number of NVIDIA 3D Vision Pro Transceivers on
         ':0'.


WARNING: Unable to determine number of NVIDIA Display Devices on ':0'.


WARNING: Unable to determine number of NVIDIA X Screens on ':0'.

** Message: PRIME: No offloading required. Abort
** Message: PRIME: is it supported? no

ERROR: nvidia-settings could not find the registry key file. This file should
       have been installed along with this driver at
       /usr/share/nvidia/nvidia-application-profiles-key-documentation. The
       application profiles will continue to work, but values cannot be
       preopulated or validated, and will not be listed in the help text.
       Please see the README for possible values and descriptions.
```

---

### Post by stepheny on 2015-04-28
Apparently what is happening is that the FPS is being limited to the maximum refresh rate of the monitor, which is 60FPS on my laptop.

---

