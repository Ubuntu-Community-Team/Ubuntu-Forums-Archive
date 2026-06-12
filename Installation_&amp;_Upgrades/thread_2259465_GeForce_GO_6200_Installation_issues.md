---
title: "GeForce GO 6200 Installation issues"
date: 2015-01-04
forum: Installation &amp; Upgrades
---

### Post by AirbusFreak on 2015-01-04
Hi There, please let me know if this is the wrong section. This is my first post to this forum.

I am attempting to install Ubuntu on my Sony Vaio VGN-FS28GP which contains a NVIDIA GEFORCE GO 6200 Graphics chip.

Firstly, the bios does not support USB boot and I do not have a blank DVD. So I am booting from USB using plop boot manager, but this shouldn't be causing me any issue I don't think. It boots great.

I have tried 14.04, when it boots, I get a very glitchy and unusable live environment. Same with 14.10.
When I use 12.04, the environment is usable but eventually freezes. I can only put this behavior down to the graphics driver.

So my questions are, can I include hardware specific drivers into the install to save the hassle prior the install?

If not, is the GEFORCE GO 6200 supported? What would the process be prior installation?

What is the best way for me to move forward? 


Any help would me much appreciated and I am happy to provide further details. I'm not a noob, but have been out of practice for a few years.

Thank you

---

### Post by egeezer on 2015-01-04
I have run a GEFORCE 6200 series with the Lubuntu version of 14.04 at least, so I think you'll be okay eventually.  There is probably a way to boot to runlevel 1 and get the driver issue sorted out, but since jockey-text is no longer in use (post-12.04) I'm out of information.

However, there may be a way to get around it: when you boot to install the live version, check the box "Install third party software" which will at least give you the Restricted Drivers choice; then you can boot your installation with limited graphics and install the drivers you need (as I recall it was the Nvidia 304 for that card).

Edited to add: look at this post on this same forum - it might help:

[http://ubuntuforums.org/showthread.php?t=2252884](http://ubuntuforums.org/showthread.php?t=2252884)

---

### Post by efflandt on 2015-01-04
When you start live/install try using **nomodeset** by hitting any key when you see the first color screen with symbols at bottom (keyboard & mouse). Select language. Hit F6, select **nomodeset**, space to select it, then Esc back and select which boot from the menu. I don't know it that will work for you for 14 versions, but may help for 12.04.

Current nvidia drivers might not recognize your old card, so you may need to install **nvidia-173** described as:
> The binary driver provide optimized hardware acceleration of OpenGL
applications via a direct-rendering X Server. AGP, PCIe, SLI, TV-out
and flat panel displays are also supported.

This package also includes the source for building the kernel module
required by the Xorg driver.

GPUs ranging from GeForce series 5 to GeForce series 9 are supported.

See /usr/share/doc/nvidia-173/README.txt.gz for a complete list
of supported GPUs and PCIIDs

Look through these links about installing nvidia-173 or web search "nvidia 173 ubuntu 12.04" (or 14.04 if you want to try that):
[http://askubuntu.com/questions/451631/nvidia-173-driver-package-comes-with-a-wrong-and-useless-nvidia-settings-app](http://askubuntu.com/questions/451631/nvidia-173-driver-package-comes-with-a-wrong-and-useless-nvidia-settings-app)
[URL="http://askubuntu.com/questions/164054/correct-way-to-install-nvidia-173-driver-on-ubuntu-12-04"]http://askubuntu.com/questions/164054/correct-way-to-install-nvidia-173-driver-on-ubuntu-12-04
[/URL][http://forums.linuxmint.com/viewtopic.php?f=42&t=102602](http://forums.linuxmint.com/viewtopic.php?f=42&t=102602)
[https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/1313504](https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/1313504)

---

### Post by AirbusFreak on 2015-01-04
Thank's for your responses. I am unable to enter the F6 menu using 14.04. When I boot, I get the boot screen with the 5 moving dots directly after the unetbootin menu, then straight to the desktop which is well and truly ugly and unusable......

I also recall booting 12.04 with a usable desktop, entering proprietary drivers and none were available...?

Thanks

---

