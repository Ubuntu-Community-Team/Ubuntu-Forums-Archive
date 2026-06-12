---
title: "Problems after upgrade to Kubuntu 13.10 from 13.04"
date: 2014-03-25
forum: Installation &amp; Upgrades
---

### Post by panKleks on 2014-03-25
Hi all,

I have recently bought a second monitor. However, once I hooked it up to my 13.04 system I experienced the "screen tearing" problem. I tracked the problem down to KDE and found out that KDE 4.11 now shipped with Kubuntu 13.10 takes care of the problem. So I did a dist-upgrade following the instructions. I had to do dpkg --configure -a and apt-get update -f to fix a broken upgrade, but I don't think that has anything to do with the issue I am having now. The screen tearing problem was indeed taken care of after the upgrade but soon I found out that after putting the PC to sleep I couldn't wake it up. After pressing the power button I would get a black screen
with a cursor blinking. Nothing works then. I cannot drop to the console with ALT+CTRL+F1 and I need to manually restart. Does this have anything to do with Grub? Anyway I did some research, unplugged the second monitor, reinstalled grub, nvidia drivers (nvidia-319), the kernel (3.11), removed /etc/X11/xorg.conf and now I cannot boot into X. When I check the Xorg.0.log I see an error saying: (EE) NVIDIA(1): Failed to initialize the NVIDIA kernel module. So I ssh into the PC and load the nvidia module manually and then issue startx. X now starts. What is going on? Adding nvidia_319 to /etc/modules doesn't work. The failed X start doesn't fall back to a text based login screen. In fact, I cannot boot the kernel in text mode by substituting "quiet splas" with "text" in the Grub menu. When I do get back into X using the method I outlined above the text consoles usually accessible with ALT+CTRL+F1 are not there. This key sequence has no effect. 

I would appreciate any help as I have spend many hours trying to figure out what is going on. 

relevant system specs:
RAM: 12 GB 
GRAPHICS: Nvidia 9800 GT

EDIT: My motherboard does have an onboard intel grahics chipset, I have blacklisted i915 module but I see entries in the Xorg.0.log that mention both intel and nouveau drivers being loaded. I have updated the nvidia driver to nvidia-331 that I got from x-swat ppa. All above problems still persist.

---

### Post by panKleks on 2014-03-25
I was able to fix the issue with X not starting at boot time. In case someone else might be having a similar issue here is what was the problem with my setup. My nvidia driver installation was correct but it was the bumblebee package that got installed somewhere along the way that caused all the trouble. Unless you have an optimus system the bumblebee package is not needed. I knew that so I uninstalled it. However, it turns out that simple remove with apt-get doesn't get rid of /etc/modules.d/bumblebee.conf which contains blacklisted nvidia driver modules: nvidia-304, nvidia-319, nvidia-331 and so on. Removing that file and rebooting brought me to X with no problems. The issues I'm having with suspend is still there though. Any ideas on how to possibly fix it?

---

### Post by panKleks on 2014-03-26
I solved the suspend and missing consoles problem. My motherboard has an onboard intel graphics chipset with kernel support provided by the i915 module which apparently conflicted with the nvidia module on my system. The i915 module is loaded during the init process at startup and simple blacklisting it doesn't work. Once blacklisted, one must rebuild initramfs using (as superuser):

```

depmod -ae
update-initramfs -u -k "all"

```

The above will regenerate initramfs for all kernels you have installed. Once I have performed the above, both problems went away. I can access the consoles with CTRL+ALT+F1-F6 keys and the system wakes up from suspend without problems.

---

