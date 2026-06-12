---
title: "Ubuntu 14.04 daily don't installs ACPI fail error"
date: 2015-06-27
forum: Installation &amp; Upgrades
---

### Post by girtsz on 2015-06-27
Hello all!

Whant to install Ubuntu 14.04 daily 64bit 27.06.2015 version and in beginning of installation I get error:
ACPI PCC probe failed.

How to avoid this error to start installation process?

Thanks.

---

### Post by Dennis N on 2015-06-27
> **girtsz said:**
> Hello all! Whant to install Ubuntu 14.04 daily 64bit 27.06.2015 version and in beginning of installation I get error:
ACPI PCC probe failed. How to avoid this error to start installation process?
Thanks.

That information can't be right. Do you mean Ubuntu 15.10?

---

### Post by v3.xx on 2015-06-27
ACPI PCC probe failed

I get the same thing in 15.10, however it does not stop the installation.  Also get it on every boot, nothing seems to fail from it.

---

### Post by girtsz on 2015-06-27
I am using Trusty daily iso. F6 options don't help. How to solve this?

---

### Post by Dennis N on 2015-06-27
> **girtsz said:**
> I am using Trusty daily iso. F6 options don't help. How to solve this?

How could a Trusty daily iso have a date in 2015? Trusty had a final release in Apr 2014. In any case, does it stop the installer from working, or is it just displaying and then continuing?

EDIT: I think you are maybe referring to 14.04.3 and not 14.04? Then it makes sense.

---

### Post by girtsz on 2015-06-27
Installation from this link:
[http://cdimage.ubuntu.com/trusty/daily-live/](http://cdimage.ubuntu.com/trusty/daily-live/)
Daily isos with integrated latest updates.

Installation stops after error message.

---

### Post by Dennis N on 2015-06-27
So it's 14.04.3 and not 14.04. It's an issue with the 3.19 kernel (or later?). There are a lot of problem reports if you google "PCC probe failed." Can be serious for some (unable to boot) or inconsequential (has no effect on operation). 

Here is one case where it prevented installation:
[http://ubuntuforums.org/showthread.php?t=2279597](http://ubuntuforums.org/showthread.php?t=2279597)

In the last post, thread starter says a solution was to use a CD (maybe he means DVD?) instead, and it installed.

Maybe you can find other options if you google "Ubuntu installer PCC probe failed". 

I have the message on screen with two of our computers, but it does not affect booting or operations (Obviously, on those it did not affect the installation).

---

### Post by Dennis N on 2015-06-27
An obvious solution is to avoid 14.04.3, and use 14.04.1 which uses 3.13 kernel I believe, and doesn't have this issue. That is a reason why I don't plan to go beyond 14.04.1 on my LTS systems. Those two machines I mentioned  are multi-boot and have the problem with the 15.04 release we were trying out.

---

### Post by kansasnoob on 2015-06-27
According to [the 14.04.3 manifest]("http://cdimage.ubuntu.com/trusty/daily-live/current/trusty-desktop-amd64.manifest") it currently still has the Utopic kernel:

> linux-generic-lts-utopic	3.16.0.41.33
linux-headers-3.16.0-41	3.16.0-41.57~14.04.1
linux-headers-3.16.0-41-generic	3.16.0-41.57~14.04.1
linux-headers-generic-lts-utopic	3.16.0.41.33
linux-image-3.16.0-41-generic	3.16.0-41.57~14.04.1
linux-image-extra-3.16.0-41-generic	3.16.0-41.57~14.04.1
linux-image-generic-lts-utopic	3.16.0.41.33
linux-libc-dev:amd64	3.13.0-55.94
linux-signed-generic-lts-utopic	3.16.0.41.33
linux-signed-image-3.16.0-41-generic	3.16.0-41.57~14.04.1
linux-signed-image-generic-lts-utopic	3.16.0.41.33

And the Utopic Xstack:

> xserver-xorg-core-lts-utopic	2:1.16.0-1ubuntu1.2~trusty2
xserver-xorg-input-all-lts-utopic	1:7.7+7ubuntu2~trusty1
xserver-xorg-input-evdev-lts-utopic	1:2.9.0-1ubuntu2~trusty1
xserver-xorg-input-mouse-lts-utopic	1:1.9.0-1build2~trusty1
xserver-xorg-input-synaptics-lts-utopic	1.8.1-1ubuntu1~trusty1
xserver-xorg-input-vmmouse-lts-utopic	1:13.0.0-1build2~trusty1
xserver-xorg-input-wacom-lts-utopic	1:0.25.0-0ubuntu1~trusty1
xserver-xorg-lts-utopic	1:7.7+7ubuntu2~trusty1
xserver-xorg-video-all-lts-utopic	1:7.7+7ubuntu2~trusty1
xserver-xorg-video-ati-lts-utopic	1:7.4.0-2ubuntu2~trusty1
xserver-xorg-video-cirrus-lts-utopic	1:1.5.2-2build1~trusty1
xserver-xorg-video-fbdev-lts-utopic	1:0.4.4-1build2~trusty1
xserver-xorg-video-intel-lts-utopic	2:2.99.914-1~exp1ubuntu4.2~trusty1
xserver-xorg-video-mach64-lts-utopic	6.9.4-2~trusty1
xserver-xorg-video-mga-lts-utopic	1:1.6.3-2build1~trusty1
xserver-xorg-video-modesetting-lts-utopic	0.9.0-1build1~trusty1
xserver-xorg-video-neomagic-lts-utopic	1:1.2.8-1build2~trusty1
xserver-xorg-video-nouveau-lts-utopic	1:1.0.11-1ubuntu2~trusty1
xserver-xorg-video-openchrome-lts-utopic	1:0.3.3-1build2~trusty1
xserver-xorg-video-r128-lts-utopic	6.9.2-1build2~trusty1
xserver-xorg-video-radeon-lts-utopic	1:7.4.0-2ubuntu2~trusty1
xserver-xorg-video-savage-lts-utopic	1:2.3.7-2ubuntu3~trusty1
xserver-xorg-video-siliconmotion-lts-utopic	1:1.7.7-2build2~trusty1
xserver-xorg-video-sisusb-lts-utopic	1:0.9.6-2build2~trusty1
xserver-xorg-video-tdfx-lts-utopic	1:1.4.5-1build2~trusty1
xserver-xorg-video-trident-lts-utopic	1:1.3.6-0ubuntu6~trusty1
xserver-xorg-video-vesa-lts-utopic	1:2.3.3-1build2~trusty1
xserver-xorg-video-vmware-lts-utopic	1:13.0.2-3ubuntu1~trusty1

But it will ship with the Vivid [HWE]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack") when released in early August.

I personally use [the archived 14.04.1 images]("http://old-releases.ubuntu.com/releases/14.04.0/") unless I'm working with newer hardware that requires a newer series kernel and Xstack.

---

### Post by Dennis N on 2015-06-27
> According to the 14.04.3 manifest it currently still has the Utopic kernel

Well then, we can add another kernel to the list! I have never used that one (3.16). 

That message popping up on every start gives the everyday user the idea there is something wrong with his system, or that Ubuntu is an unpolished product. It should be dealt with summarily.

---

### Post by girtsz on 2015-06-28
If I install Ubuntu 14.04.2 and install all updates will I get the same problem after reboot?

---

### Post by sudodus on 2015-06-28
No, update/dist-upgrade will stay within the same series of kernels, 3.13 for 14.04 and 14.04.1, 3.16 for 14.04.2 and 3.19 for 14.04.3 when it arrives.

In order to upgrade to the next series of kernels (within an LTS) you must upgrade the HWE stack (and it is risky, I agree with kansasnoob to stay with what works. There will be security updates). See this link: [HWE]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack").

---

### Post by Bucky Ball on 2015-06-28
15.10 will be released in late October. That is why it is 15.10 = 2015, tenth month = October. ;)

That is how the release numbers work. The .04 releases come out late April, .10 releases late October. It's odd, but I guess having a date as a release number, 04.15 or 10.15 is odd in its own way.

---

### Post by girtsz on 2015-06-29
Many thanks friends!

---

