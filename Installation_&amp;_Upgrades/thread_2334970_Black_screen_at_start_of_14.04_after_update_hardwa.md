---
title: "Black screen at start of 14.04 after update hardware enablement"
date: 2016-08-24
forum: Installation &amp; Upgrades
---

### Post by hako1 on 2016-08-24
I was running 14.04 64bit with Linux 4.3.3 on an AMD A8-6600K APU. My  graphic was shown as "Gallium 0.4 on AMD GPU" (or sth like that).

  With the recent EOL of the hardware enablement of 14.04, I updated using software updater. It updated several modules, also some related to graphic, and installed Linux  4.4.0-36-generic. The update was shown to be partial, which I subsequently could overcome  by running update again, and taking out the xorg-edger ppa.

  At start of the system the screen turns off loading Ubuntu after the  grub menu. The sound of the login screen come up, but the screen remains off. The only way I found is to select recovery mode in grub, and then  continue with normal boot. That takes me to the login screen, and I can  work normally.

  However, the graphics is now shown as "Gallium 0.4 on llvmpipe (LLVM 3.8, 128 bits)", and the system tends to run hot.

  Questions:
  
[LIST=1]
[*]Is the graphics shown correctly? I expected improvements compared to the old driver (which was running ok in normal use, but was not enough for games like Xplane). 
[*]How to let the system boot normally without the de-tour via recovery? Maybe I need to install some extra modules? 
[/LIST]
      (the same question I posted on askubuntu, but did not get any answer)

---

### Post by grahammechanical on 2016-08-24
When we use recovery mode>Resume we get llvmpipe. It is an open source video driver that is used as a fallback video driver. Sometimes when there are video driver conflicts the system will load to llvmpipe. Such as installing a kernel that does not come with a driver module for our video hardware. It has gotten you to a working desktop.

You now need to go to System Settings>Software & Updates>Additional Drivers and change video drivers. Start using the regular open source video driver. That will also be Gallium 0.4 but without the llvmpipe. Once the system is loading correctly and a good profile has been established. You can use Additional Drivers to experiment with the available proprietary video drivers.

Upgrades, whether to the hardware enablement stack or to a newer version of Ubuntu cannot account for all the changes that we users do to our systems. The upgrade process cannot account for our using a PPA to bring in different kernels or video drivers to those provided by the Ubuntu maintainers.

At some point you will need to upgrade to 16.04. If you are not going to do a fresh install then, revert to using an open source video driver; the standard kernel; disable all PPAs and revert the desktop to as near as possible default condition. It will lessen the risk of something like this happening again.

Regards

---

### Post by hako1 on 2016-08-24
Under "Additional Drivers" I find:
 (green dot) Advanced Micro Devices, Inc. [AMD/ATI]: Richland [Radeon HD 8570D]
 This device is using the recommended driver.
 (donut) Using X.Org X server - AMD/ATI display driver wrapper from xserver-xorg-video-ati (open source, tested)
two other options for proprietary drivers are not selected.

I suppose I will need to re-install some modules, but which ones?
Or, would it be possible to re-install the graphic system after disabling the xorg-edgers ppa? How to do that?

---

### Post by kansasnoob on 2016-08-24
Just for reference:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_14.04_LTS_-_Trusty_Tahr](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_14.04_LTS_-_Trusty_Tahr)

I'd begin by using ppa-purge to purge (not just disable) the Xorg ppa(s) in use.

Then try the command from the link above:

```
sudo apt-get install --install-recommends linux-generic-lts-xenial xserver-xorg-core-lts-xenial xserver-xorg-lts-xenial xserver-xorg-video-all-lts-xenial xserver-xorg-input-all-lts-xenial libwayland-egl1-mesa-lts-xenial 
```

I'm thinking that apt-get install may sufficiently reconfigure the xserver packages after purging the one from the ppa? If not you may have to "dpkg-reconfigure" but I'm not 100% sure how to do that :redface:

---

### Post by hako1 on 2016-08-24
Since I am using multiarch, I followed the wiki mentioned above: sudo apt-get install --install-recommends linux-generic-lts-xenial xserver-xorg-core-lts-xenial xserver-xorg-lts-xenial xserver-xorg-video-all-lts-xenial xserver-xorg-input-all-lts-xenial libwayland-egl1-mesa-lts-xenial libgl1-mesa-glx-lts-xenial libgl1-mesa-glx-lts-xenial:i386 libglapi-mesa-lts-xenial:i386

and got:
libgl1-mesa-glx-lts-xenial is already the newest version.
libwayland-egl1-mesa-lts-xenial is already the newest version.
xserver-xorg-core-lts-xenial is already the newest version.
xserver-xorg-input-all-lts-xenial is already the newest version.
xserver-xorg-lts-xenial is already the newest version.
xserver-xorg-video-all-lts-xenial is already the newest version.
xserver-xorg-video-all-lts-xenial set to manually installed.
libgl1-mesa-glx-lts-xenial:i386 is already the newest version.
libglapi-mesa-lts-xenial:i386 is already the newest version.
libglapi-mesa-lts-xenial:i386 set to manually installed.
linux-generic-lts-xenial is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.

Then, I tried dpkg-reconfigure the graphics system:
sudo dpkg-reconfigure xserver-xorg-core-lts-xenial xserver-xorg-lts-xenial xserver-xorg-video-all-lts-xenial xserver-xorg-input-all-lts-xenial libwayland-egl1-mesa-lts-xenial
response: Processing triggers for libc-bin (2.19-0ubuntu6.9) ...

and rebooted. --> no change, still need to go via recovery

---

### Post by hako1 on 2016-08-24
In the description of the xorg-edgers ppa there are some other modules for Xenial listed in "http://www.ubuntuupdates.org/ppa/xorg-edgers?id=87&page=2":
     libtxc-dxtn, libdrm, mesa, xserver-xorg-video-amdgpu, ppa-purge
should I try the amdgpu version? do I need to install the others as well?

---

### Post by hako1 on 2016-08-26
I tried the following:
sudo add-apt-repository ppa:xorg-edgers/ppa 
sudo apt-get update
sudo apt-get install xserver-xorg-video-amdgpu-lts-xenial
--> Note, selecting 'xserver-xorg-video-amdgpu-lts-xenial' instead of 'xserver-xorg-video-amdgpu'
    xserver-xorg-video-amdgpu-lts-xenial is already the newest version.

"sudo apt-get upgrade" results in:
The following packages have been kept back:
  libgbm1
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

it seems the amdgpu driver for Xenial is installed, but not working.
I tried to attach Xorg.0.log, but the site won't let me do that. (12k zip file, too big?)
How to get back to a working graphics system?

---

### Post by hako1 on 2016-08-26
**Solution for now:**
I installed **Linux 4.5.3 Kernel** downloaded from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.5.3-wily/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.5.3-wily/)
after reboot, the system starts normally, graphics shown: "Gallium 0.4 on AMD ARUBA (DRM 2.43.0, LLVM 3.8.0)".
So far, so good. But, which driver version is it using now? Any way to find that out?

---

