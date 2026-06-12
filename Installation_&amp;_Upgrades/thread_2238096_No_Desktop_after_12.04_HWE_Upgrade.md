---
title: "No Desktop after 12.04 HWE Upgrade"
date: 2014-08-05
forum: Installation &amp; Upgrades
---

### Post by jhoppa2 on 2014-08-05
After installing the 12.04 HWE upgrade my system boots to a black screen with the message "The system is running in low-graphics mode - Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself."  I am able access the system thru the command line log-on.

Here are some details that I've gleaned with my limited knowledge and beginer's command line skills.

xserver log file states "failed to load the NVIDIA kernel module"

kernel version = Linux 3.13.0-32-generic x86_64

VGA compatable controller = NVIDIA Corporation C51 GeForce 6150 LE (rev a2)

lspci -v -s lists "Kernel modules: nvidia_173, nouveau, nvidiafb but shows none installed

Any help to resolve the problem is greatly appreciated.

---

### Post by jhoppa2 on 2014-08-06
Researched the problem a bit more and found solution at [http://askubuntu.com/questions/503724/12-04-x-hwe-hardware-enablement-update-broke-nvidia-proprietary-drivers](http://askubuntu.com/questions/503724/12-04-x-hwe-hardware-enablement-update-broke-nvidia-proprietary-drivers).

Downloaded and installed nvidia-304 drivers

All is good!!

---

