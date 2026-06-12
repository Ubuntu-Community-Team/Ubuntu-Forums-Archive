---
title: "Problems in the upgrade to 15.10 (kernel 4.2 error)"
date: 2015-10-22
forum: Installation &amp; Upgrades
---

### Post by leillo1975 on 2015-10-22
Hello.

I upgrade my system (Ubuntu 15.04 64bits) to the new release. The process seems to be alright. When I restart my system, all works fine, but when I do a "uname -r", I see that my kernel is 3.19 (like in 15.04). 

I try to update to 4.2 manually (sudo apt-get install linux-image-4.2.0-16-generic). The process works with no errors, but when I restart the system by default (4.2 systemd), the resolution are wrong (too low) and I can't logon because mouse and keyboard don't works. The problem is the same with upstart

If I restart my computer with 3.19 Kernel and I don't have problems.

I have this error in two different PC's. The two PC's have an NVIDIA card with the 355.11 propietary drivers.

Can you help me to installl 4.2 kernel? Why this kernel is not installed in the release upgrade?

---

### Post by martins-k on 2015-10-23
Hello,

I have exactly same issue in my computer.

---

### Post by Bostin_Wang on 2015-10-23
[COLOR=#000000]Hello,[/COLOR]

[COLOR=#000000]I have exactly same issue in my computer.[/COLOR]

---

### Post by ChrisGaeth on 2015-10-23
Same here though I did not try to force the 4.2 kernel in.

---

### Post by kansasnoob on 2015-10-23
Possibly this bug I reported during QA testing:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1508157](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1508157)

If so I'd appreciate you all marking that the bug affects you too.

My hair has almost literally been on fire since they chose to release Wily with sooooooooo many show-stopper bugs :o

---

### Post by sudodus on 2015-10-23
Kansasnoob,

Which version would you recommend now? I know that it depends on the computer hardware, but where would you suggest people to start (or stay)?

14.04.1 LTS, 14.04.3 LTS, 15.04 or some other version?

*Edit:* by the way, making a fresh installation of 15.10 works well for me in several different computers.

---

### Post by kansasnoob on 2015-10-23
> **sudodus said:**
> Kansasnoob,

Which version would you recommend now? I know that it depends on the computer hardware, but where would you suggest people to start (or stay)?

14.04.1 LTS, 14.04.3 LTS, 15.04 or some other version?

*Edit:* by the way, making a fresh installation of 15.10 works well for me in several different computers.

I always try 14.04.1 first because it has continuous kernel support throughout April 2019:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A14.04.x_Ubuntu_Kernel_Support](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A14.04.x_Ubuntu_Kernel_Support)

Only if 14.04.1 doesn't work with specific hardware do I jump into a later point release with updated HWE, unless of course the user wants the latest packages, then interim releases are the only game in town.

Regarding Wily, in addition to finding that the kernel fails to upgrade in some (now appears to be many) cases, I encountered all of the following:

[Wily user UI shows auto-login off after selecting on during install]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/1487819")

[Garbled graphics in Wily with Intel GMA4500 chip]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1507255") 

[Booting live Wily image results in black screen with or without random text]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1489147")

The latter of those three affects every set of hardware I tested on to some degree but may be limited to Ubuntu GNOME. The fact that they went ahead and released anyway left me wondering why I even bother testing ..................... I've been an iso-tester since 2008, I was the one who asked that upgrade tests be added to the tracker! Now I honestly think it's time to retire.

---

### Post by grahammechanical on 2015-10-23
@leillo1975

Some questions. When you upgraded were you using the open source video driver or the proprietary video driver? When you manually installed Linux kernel 4.2.0-16 did you also update the grub configuration file? Unless we update grub the newly installed kernel will not appear in the Grub menu. It will not be the default loading option.

```
sudo update-grub
```

Personally, if I was upgrading from one release to another I would always do it running the open source video driver. When I fresh install I never tick the box "Install third party software" for that will install a proprietary video driver. New versions of Ubuntu bring in the latest stable proprietary video drivers. In my case the latest Nvidia drivers do not support my old Nvidia adapter. And that prevents a kernel module being generated for my video adapter.

I have an fresh install of 15.10 from an image built just before release day. I did not let it install a proprietary video driver and it has kernel 4.2.0-16 and Additional drivers offers me Nvidia drivers 340.93 or 304.128 (not the latest, you will see) and I have no problems activating the 304 driver with the 4.2.0-16 kernel. I offer this information for those who do not have the same video adapter as you.

Regards.

---

### Post by licois-dorian on 2015-11-05
is this problem solved?


I too wasn't upgraded to kernel 4.2 (going from ubuntu gnome 15.04 64bits to gnome 15.10 64bits, nvidia graphic card with 352.41 drivers), I'm still on 3.19.0-31

---

### Post by sudodus on 2015-11-06
Hi licois-dorian,

Welcome to the Ubuntu Forums :-)

The original poster has not posted back [yet], so we don't know.

Please start an own thread with a good title and first post, where you describe your problem and your computer's hardware. That way you have better chances to get good advice.

---

