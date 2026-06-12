---
title: "Cannot Boot Kernel 3.13.0-32 after upgrade for HWE support"
date: 2014-07-23
forum: Installation &amp; Upgrades
---

### Post by Bisneff on 2014-07-23
Hi everyone.

I'm writting from my Acer N550-JV with Ubuntu 12.04 . I can now be here only because I've booted with a previous kernel version ( 3.8.0-42). Back in time, I faced those problems:

A couple of days ago, doing system updates, I came into [this problem]("http://askubuntu.com/questions/493541/hardware-enablement-stack-hwe-out-of-support"). Since the warning message was quite annoying, I choose to go ahead and try a workaround. The first thing I do was to follow the procedure in the first comment, so I run:

_**(1)**_
 ```
sudo apt-get install -V libglapi-mesa-lts-trusty libgl1-mesa-glx-lts-trusty xserver-xorg-lts-trusty xserver-xorg-input-all-lts-trusty xserver-xorg-video-all-lts-trusty libgl1-mesa-dri-lts-trusty x11-xserver-utils-lts-trusty libglapi-mesa-lts-trusty:i386 libgl1-mesa-dri-lts-trusty:i386 libgl1-mesa-glx-lts-trusty:i386 libgles2-mesa-lts-trusty libglapi-mesa-lts-trusty mesa-vdpau-drivers-lts-trusty

```

After that, my system was able to do upgrade, I was very happy, Ubuntu was very happy and the whole world seemed a better place. After reboot for complete upgrade I notice that my kernel was upgraded (really? è_é) from 3.8.0-42 to 3.13.0-32 . What's the matter? When I select the grub option the screen became black and wont go further.

Come on, I just need to boot with a previous kernel, remove the new kernel and boot again.

Yesterday I do this, boot with 3.8.0-42 . The list of my kernel was like:
```
dpkg --list | grep linux-image
ii  linux-image-3.13.0-32-generic                 3.13.0-32.57~precise1                               Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-29-generic                  3.8.0-29.42~precise1                                Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-34-generic                  3.8.0-34.49~precise1                                Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-35-generic                  3.8.0-35.52~precise1                                Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-36-generic                  3.8.0-36.52~precise1                                Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-37-generic                  3.8.0-37.53~precise1                                Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-38-generic                  3.8.0-38.56~precise1                                Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-39-generic                  3.8.0-39.58~precise1                                Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-41-generic                  3.8.0-41.60~precise1                                Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-42-generic                  3.8.0-42.63~precise1                                Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-44-generic                  3.8.0-44.66~precise1                                Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-generic-lts-trusty                3.13.0.32.28                                        Generic Linux kernel image


```

So I decided to remove the first and the last entries of that list. Reboot and 3.8.0-44 wont work. Then I boot again with 42 and remove 44 to. 

After that I focus my night on solving some Virtualbox problems that comed up and go to sleep happy. (without trying to reboot)

EDIT: I forgot that here I also unistall all the package installed in _**(1)**_ :) maybe unistall the kernel but preserve the other packages cuold be a solution, but I need to upgrade to maintain the support for HWE Stack (even if I'm not really sure to know what is the HWE Stack :P)

this morning I've turn on my pc to come into an annoying error, that was: *"Could not* write byte: *broken pipe*" showed on startup after select grub entry, after that my PC became a stone, totally unresponsive. Boot in recovery mode and, logging without graphic shell, the system show me the error on HWE Stack Support.

I repeat the procedure _**(1)**_ and I found the 3.13 kernel installed but now I can boot from 3.8.0-42.

I came into [this thread]("http://askubuntu.com/questions/453411/ubuntu-14-04-not-booting-after-error-message-tmp-could-not-be-mounted") , not exactly my problem but quite akin, so I decide to try. But editing the grub entry doesn't make my system boot.

Any suggestion?

(Thank you everyone :) )

---

### Post by Bisneff on 2014-07-24
Bump

---

### Post by Bisneff on 2014-07-28
UP! No one?

---

### Post by kansasnoob on 2014-07-28
In less than two weeks the only currently supported kernels will be those in the 3.2 and 3.13 series:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.LTS_Kernel_Support_Schedule](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.LTS_Kernel_Support_Schedule)

So IMHO the best thing would be either a fresh install of 14.04.1:

[http://releases.ubuntu.com/14.04.1/](http://releases.ubuntu.com/14.04.1/)

Or a fresh install of 12.04.1 which still uses the 3.2 series kernel:

[http://old-releases.ubuntu.com/releases/12.04.1/](http://old-releases.ubuntu.com/releases/12.04.1/)

Not an ideal situation for sure, please read what I said here:

[http://ubuntuforums.org/showthread.php?t=2236096&page=2&p=13082770#post13082770](http://ubuntuforums.org/showthread.php?t=2236096&page=2&p=13082770#post13082770)

---

### Post by Bisneff on 2014-08-02
Format my system partition and install 14.04 did the trick.

I miss my 12.04, but it's ok.

Thanks

---

