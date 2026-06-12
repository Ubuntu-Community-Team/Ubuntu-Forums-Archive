---
title: "NVIDIA drivers break text mode. Virtual consoles blank except for blinking cursor."
date: 2013-02-10
forum: Installation &amp; Upgrades
---

### Post by zooberman2 on 2013-02-10
I've tried Ubuntu 12.04 and 12.10. Each time I've tried something new, I've started from a totally fresh install.

Approach 1 (12.10): 
With 12.10, I installed the NVIDIA drivers with:
sudo apt-get install linux-headers-generic
sudo apt-get install nvidia-current

Approach 2 (12.10):
sudo apt-get install linux-headers-generic
Installed nvidia drivers using additional drivers feature.

Approach 3 (12.04):
sudo apt-get install linux-headers-generic
Used Jockey to add the optional NVIDIA drivers (version 310)


With all 3 approaches, after installing the NVIDIA drivers, my virtual console Windows are blank except for a blinking underscore cursor in the top left corner. 

Attempted workarounds based on random posts on the web:
1. Adding "vga=normal" OR "vga=791" to /etc/default/grub [on the GRUB_CMDLINE_LINUX_DEFAULT line, right next to 'quiet splash']

2. Tried creating a .conf file in /etc/modprobe.d with "options nvidia NVreg_UseVBios=0". Supposedly, this should have made /proc/driver/nvidia/registry contain the line "UseVBios: 0". However, the /proc/driver/nvidia/registry file is just a plain text file that contains the text: 'Binary: ""'  -- I think this tip is out of date.

Neither of these workarounds had any effect. When removing 'quiet splash', the bootup screen in Ubuntu shows the same blinking cursor (instead of the expected startup sequence).

Virtual consoles using Nouveau are fully functional. However, Nouveau is a bit slow and my graphics card fan (GTX 670) runs continuously at high speed.

---

### Post by zooberman2 on 2013-02-10
Also of note: Everything other than text-mode (or whatever the correct name is) works fine. Unlike other people who have had NVIDIA trouble, my desktop comes up working correctly, and in the correct resolution (1920 x 1080).

---

### Post by MAFoElffen on 2013-02-10
> **zooberman2 said:**
> Also of note: Everything other than text-mode (or whatever the correct name is) works fine. Unlike other people who have had NVIDIA trouble, my desktop comes up working correctly, and in the correct resolution (1920 x 1080).

I can confirm that this is a current bug on the nvidia-current presently in the Main repository and you should report it as such. You are not "alone" with this problem.

You and all affected, I encourage you to report it to launchpad so that it can be addressed and resolved. You are lucky in that you get a cursor... as most are losing the video signal all together in tty1-6.

Please post the bug number and link here.

The newest nvidia binary may have addressed this already (I haven't tested it yet personally)... but maybe if it has, a bug report and users subscribed to it will help move the fix into Main faster.

---

