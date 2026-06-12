---
title: "Default Install Resolution Too Low"
date: 2015-03-02
forum: Installation &amp; Upgrades
---

### Post by Gareth_Jones on 2015-03-02
I'm trying to install 14.04 LTS on a basic old motherboard (Aopen MX46-533V) and have hit a problem. My monitor won't display in 640x480 and the default resolution once installed seems to be 640x480 for some reason. The display works fine throughout the install, it's only when booting to the new install that I have a problem. Is there any way at install that I can force the resolution at install something higher, preferably 1280x1024 at 60Hz? 

I had been told that it was just grub and the splash screen that were at 640x480 and if I let the boot complete things would be fine, but I've let the boot complete and still the same issue. I didn't have the same problems with this monitor and a previous version of Ubuntu.  I am assuming that it's something to do with the installer having trouble with the inbuilt graphics card on the motherboard and selecting a default low resolution mode. However that puzzles me since it's an old and basic motherboard so Ubuntu shouldn't have a problem with the card. What also puzzles me it why the installer would choose 640x480. These days there are an awful lot of displays around that won't display 640x480 so that resolution would be a problem for quite a few users.

I have considered trying an older version of Ubuntu and upgrading to 14.04 LTS, but I don't want to go to that trouble unless I'm sure it's going to work.

Thanks in advance

Gareth

---

### Post by dino99 on 2015-03-02
what is that builtin graphic chipset ? and which driver is supported ?
That issue rely on the graphic driver installed.

---

### Post by Gareth_Jones on 2015-03-02
The chipset is an SiS Real256. Just one more question though, how do you tell what driver you have installed when you can't boot?

---

### Post by grahammechanical on 2015-03-02
How did the Try/live session run?

One of the differences between the live session and the installed session is that the live session uses an open source video driver. When we install and if we tick the box "Install third party software" we get a proprietary video driver and it will be the latest stable version. Manufacturers are in the habit of removing support for what they see as obsolete video adapters. And so we get issues like this if we install a proprietary video driver.

If the live session worked OK, then try installing without ticking the box "Install third party software." We can always install the audio and visual codecs by installing Ubuntu Restricted Extras from the Software Centre and we can experiment with video drivers by going to System Settings>Software and Updates>Additional Drivers tab.

I also recommend getting familiar with Recovery Mode. We find it at the Grub boot menu under the Advanced Options sub-menu. The Resume option should load Ubuntu using a fall back open source video driver called llvmpipe and not any installed proprietary video driver.

Please explain what you mean by "can't boot." From your first post it seemed as if you could load Ubuntu but the screen resolution was too low. That comment "can't boot" is confusing me.

---

### Post by Gareth_Jones on 2015-03-03
As I said my monitor won't display 640x480 so all I get at is a message telling me that the screen resolution does not match the monitor's optimal setting. So while the PC does boot, to all practical purposes it does not as it has no display.

I will try installing as you suggest tonight.

---

