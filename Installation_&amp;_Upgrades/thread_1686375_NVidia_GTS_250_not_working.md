---
title: "NVidia GTS 250 not working"
date: 2011-02-12
forum: Installation &amp; Upgrades
---

### Post by grogling on 2011-02-12
I just installed a fresh copy of Ubuntu 10.10 x86 Desktop of my machine with a Nvidia GTS 250 video card.

Once installed, as expected it popped up informing me I should use the binary drivers, which i followed the prompts to do. Upon rebooting, xwindows did not start at all. I tried manually starting it with the 'startx' command and was given the message about there not being any nvidia kernel drivers loaded.

I checked out dmesg and found this.

[    3.602798] NVRM: The NVIDIA GPU 0000:02:00.0 (PCI ID: 10de:0615) installed
[    3.602799] NVRM: in this system is not supported by the 260.19.06 NVIDIA Linux
[    3.602800] NVRM: graphics driver release.  Please see 'Appendix A -
[    3.602802] NVRM: Supported NVIDIA GPU Products' in this release's README,
[    3.602803] NVRM: available on the Linux graphics driver download page at
[    3.602804] NVRM: [www.nvidia.com](www.nvidia.com).
[    3.602839] NVRM: The NVIDIA probe routine failed for 1 device(s).
[    3.602842] NVRM: None of the NVIDIA graphics adapters were initialized!


I presume this is the root cause of the problem, but I'm completely stumped as to what to do to fix the problem. I have checked the nvidia website and it seems this driver version should support my video card, so I'm at a loss.

Can anybody advise what I can do to get this thing working.

---

### Post by grogling on 2011-02-12
I have found the temporary workaround to get Ubuntu working with the Nvidia video card.

You need to install an older version of the Kernel (apparently the one suppled with 10.10 had had some mods done by the Ubuntu team which has broken something).


Here is a step by step on how i fixed it.

Step 1 : go into /etc/X11 and rename xorg.conf to something else. That allows xwindows to start. You can then start xwindows with the startx command.

Step 2 : Go into System>Admin>Aditional Drivers and remove the drivers Ubuntu has already tried to install and reboot. This will put you back to the vesa driver.

Step 3 : Install a repository from an older release.
Add the following line into your sources 'deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid main'

Step 4 : Install the older Kernel
sudo apt-get install linux-headers-2.6.32-21 linux-headers-2.6.32-21-generic-pae linux-image-2.6.32-21-generic-pae

Note: The page I got this from specified a non-pae kernel, but that meant I am wasting 1GB of my ram. This PAE version I have specified seems to work fine.

Step 5 : Install the startup-manager utility. Once installed run it (system>admin) and set the newly installed kernel as the default.

Step 6 : Reboot, then you should be able to install the nvidia driver using the SYstem>Admin>Aditional Drivers way.




I'd still love to hear from anybody who would know how to get the nvidia drivers working with the latest kernel.

---

### Post by grogling on 2011-02-12
Just to add to this thread for anybody that has the same problem.

I just realised that ubuntu updator will keep trying to update the kernel, SO i went into aptitude, uninstalled the defult version of the kernel then clicked on the current kernel, chose package and lock version.

Ohh, and after doing this, you need to go back into startup-manager and change the default entry. The default is set by the menu number, after removing the default kernel, all the numbers shift around and the default now becomes memtest86+.

Hopefully this makes the machine stable through updates without having to mess around.

---

