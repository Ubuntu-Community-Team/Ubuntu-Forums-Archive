---
title: "firmware for HWE enabled install"
date: 2022-06-01
forum: Installation &amp; Upgrades
---

### Post by adfhnapo on 2022-06-01
Hello all,

I have updated my machine to the HWE kernel in my 18.04 install.

However the firmware package is still at the generic release.

I can manually update the firmware with a download of firmware that matched the kernel supported by the HWE stack.

However this seems a little silly. I can get updates to the drivers that support my newer hardware, but i need to manually update the firmware out of the _apt world_. This means i manually have to monitor the auto updates to get the firmware that matches those updates. 

dpkg -l | egrep hwe\|firmware
ii  amd64-microcode                                       3.20191021.1+really3.20181128.1~ubuntu0.18.04.1 amd64        Processor microcode firmware for AMD CPUs
ii  intel-microcode                                       3.20210608.0ubuntu0.18.04.1                     amd64        Processor microcode firmware for Intel CPUs
ii  linux-firmware                                        1.173.21                                        all          Firmware for Linux kernel drivers
ii  linux-generic-hwe-18.04                               5.4.0.113.127~18.04.97                          amd64        Complete Generic Linux kernel and headers
ii  linux-headers-generic-hwe-18.04                       5.4.0.113.127~18.04.97                          amd64        Generic Linux kernel headers
ii  linux-hwe-5.4-headers-5.4.0-107                       5.4.0-107.121~18.04.1                           all          Header files related to Linux kernel version 5.4.0
ii  linux-hwe-5.4-headers-5.4.0-113                       5.4.0-113.127~18.04.1                           all          Header files related to Linux kernel version 5.4.0
ii  linux-hwe-5.4-headers-5.4.0-89                        5.4.0-89.100~18.04.1                            all          Header files related to Linux kernel version 5.4.0
ii  linux-hwe-5.4-headers-5.4.0-99                        5.4.0-99.112~18.04.1                            all          Header files related to Linux kernel version 5.4.0
ii  linux-image-generic-hwe-18.04                         5.4.0.113.127~18.04.97                          amd64        Generic Linux kernel image
ii  xserver-xorg-core-hwe-18.04                           2:1.20.8-2ubuntu2.2~18.04.6                     amd64        Xorg X server - core server
ii  xserver-xorg-hwe-18.04                                1:7.7+19ubuntu8~18.04.3                         amd64        X.Org X server
ii  xserver-xorg-input-all-hwe-18.04                      1:7.7+19ubuntu8~18.04.3                         amd64        X.Org X server -- input driver metapackage
ii  xserver-xorg-input-libinput-hwe-18.04                 0.28.1-1~18.04.1                                amd64        X.Org X server -- libinput input driver
ii  xserver-xorg-legacy-hwe-18.04                         2:1.20.8-2ubuntu2.2~18.04.6                     amd64        setuid root Xorg server wrapper
ii  xserver-xorg-video-all-hwe-18.04                      1:7.7+19ubuntu8~18.04.3                         amd64        X.Org X server -- output driver metapackage
ii  xserver-xorg-video-amdgpu-hwe-18.04                   19.1.0-1~18.04.1                                amd64        X.Org X server -- AMDGPU display driver
ii  xserver-xorg-video-ati-hwe-18.04                      1:19.1.0-1~18.04.1                              amd64        X.Org X server -- AMD/ATI display driver wrapper
ii  xserver-xorg-video-fbdev-hwe-18.04                    1:0.5.0-1ubuntu1~18.04.1                        amd64        X.Org X server -- fbdev display driver
ii  xserver-xorg-video-intel-hwe-18.04                    2:2.99.917+git20171229-1ubuntu1~18.04.1         amd64        X.Org X server -- Intel i8xx, i9xx display driver
ii  xserver-xorg-video-nouveau-hwe-18.04                  1:1.0.16-1~18.04.1                              amd64        X.Org X server -- Nouveau display driver
ii  xserver-xorg-video-qxl-hwe-18.04                      0.1.5-2build2~18.04.1                           amd64        X.Org X server -- QXL display driver
ii  xserver-xorg-video-radeon-hwe-18.04                   1:19.1.0-1~18.04.1                              amd64        X.Org X server -- AMD/ATI Radeon display driver
ii  xserver-xorg-video-vesa-hwe-18.04                     1:2.4.0-1~18.04.1                               amd64        X.Org X server -- VESA display driver
ii  xserver-xorg-video-vmware-hwe-18.04                   1:13.3.0-2build1~18.04.1                        amd64        X.Org X server -- VMware display driver

---

### Post by mikewhatever on 2022-06-01
There is no "HWE-firmware", if that is what you wanted to ask, but forgot. In case you are concerned about poor support for "my newer hardware", there is an option to upgrade to 20.04, or to install 22.04. Some firmware, included into the "linux-firmware" package did get updated since the release of 18.04, but I doubts we can expect many more updates, unless a serious problem is discovered.

---

### Post by adfhnapo on 2022-06-01
thanks for the reply.
I was just wondering if anyone had a _clean_ solution, without upgrade.
I have all the _hack_ solutions covered.
22.04 doesn't have the kernel, yet, that i require. at least  as of a week ago.

---

### Post by MAFoElffen on 2022-06-01
What kernel series covers the hardware you have? HWE Series kernels go by the LTS version. And there are already tutorials out to upgrade Kernels for 22.04, since there are now already 2 stable kernel versions there which support newer, bleeding-edge hardware, than the initial 22.04 is supporting in the release Generic Series of Kernels... 

Just saying, if you have new hardware, staying at 18.04 is tying your hands and hampering your capabilities. You aren't going t get that with an old release.

---

### Post by armadefuego on 2022-06-02
(this is my thread, i am on my personal account)
The kernel is on the head. ( custom build.) using a modified packaging procedure. (think PPA)
I can, easily, just slam the current firmware in, and the specific problem is resolved. 
In the general case the upgrade to 22.04 is an easy solution.
Not as easy on multiple machines where the software is not directly supported by Ubuntu (other open source software that is not directly supported by ubuntu).
I could do the same for firmware, but this seems like a problem _anyone_might have.
Ubuntu has HWE for a reason. the same issue is present in other LTS versions, 20.04, 22.04, when you _need_ HWE you _most likely_ will need the FW.
IIRC its why FW was split from the main release cycle of the kernel.

---

### Post by MAFoElffen on 2022-06-02
Refreshing that you have an understanding of how things work in Linux. Yes. I understand. Though my preferred home is Ubuntu, I help support Linux as a whole. I have experience with Upstream, Downstream, and differing Branch flavors. And how things can work or fall apart between all.

I do a lot of system testing... Especially when it comes to helping people resolve problems in the Linux Graphics Layer... I know when changing kernels in any Distro, that it has a waterfall effect in other things in the target suite. (not just the kernel). I've upgraded kernels and seen what else that affects and falls out. A lot of things depend on versioning dependencies and the relationships between. You hear that this certain kernel version supports this new hardware (GPU's for my support)... And the adventure begins.  

I don't like to blindly recommend a solution without testing it first. As for kernel versions... I test it, then all these other things stop working. It is 'entertaining'. I have found that you can get away with it when you don't go too crazy and stay within a range of versions. Otherwise the range that the Linux Utilities and others within the framework structure just falls apart. LOL As you say, it's not as easy as just changing "one piece" of it.

With 22.04, everything in the suite is already built for in that higher range of version dependencies... It would be a higher expected success of going higher with a kernel version, with having to change less other pieces. Tough, the patches for 22.04 LTS 'Stable' won't officially be applied until July, as 22.04.1. 

It is very refreshing that you understand that the Hardware Enablement Stack is not just the kernel... And now I understand the skill and experience level of who I am addressing. Thank you for your support and dedication. I appreciate you in your journey, and endeavors.

As you say, lots of people don't realize that utilities and applications wrapped up in a Distribution are not wholly controlled by one entity. Just as an example, a specific basic Linux Utility, may or not be a default app for all Linux Branches or Distributions... (experience in writing Linux support scripts as opensource...)

---

### Post by mikewhatever on 2022-06-02
> **armadefuego said:**
> (this is my thread, i am on my personal account)
The kernel is on the head. ( custom build.) using a modified packaging procedure. (think PPA)
I can, easily, just slam the current firmware in, and the specific problem is resolved. 
In the general case the upgrade to 22.04 is an easy solution.
Not as easy on multiple machines where the software is not directly supported by Ubuntu (other open source software that is not directly supported by ubuntu).
I could do the same for firmware, but this seems like a problem _anyone_might have.
Ubuntu has HWE for a reason. the same issue is present in other LTS versions, 20.04, 22.04, when you _need_ HWE you _most likely_ will need the FW.
IIRC its why FW was split from the main release cycle of the kernel.

This made little sense from the biginning, and does even less now. 
First, if "armadefuego" is your personal account, what is " parcelistsupport"? Your fake account?
Second, if it is easy for you to get new firmware, what is the point of this thread?
Third, if you want to improve things, file bug reports on launchpad.

---

### Post by MAFoElffen on 2022-06-02
@mikewhatever

There are some conflicts in what he says so far. But let's see where this goes. My curiosity is up for it...

---

