---
title: "nvidia 190 on hardy: I've got nvnews.net stumped!"
date: 2009-12-19
forum: Installation &amp; Upgrades
---

### Post by jsundqui on 2009-12-19
Situation: hardy/8.04.  New nv g210 video card.  g210 needs the 190 driver, not the 169 that comes with 8.04 (nvidia-glx-new is 169).

So I added [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu) hardy main to my sources list, and installed nvidia-glx-190 

Things seem to be installed correctly, as you can see:

```
user@mythtv:~$ dpkg -l | grep nvidia
ii  dkms    2.1.0.1-0ubuntu1~nvidiavdpauppa1    Dynamic Kernel Module Support Framework
ii  nvidia-190-kernel-source   190.53-0ubuntu1~karmic~nvidiavdpauppa6   NVIDIA binary kernel module source
ii  nvidia-190-modaliases     190.53-0ubuntu1~karmic~nvidiavdpauppa6      Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-glx-190    190.53-0ubuntu1~karmic~nvidiavdpauppa6     NVIDIA binary Xorg driver
rc  nvidia-glx-195   195.22-0ubuntu1~karmic~nvidiavdpauppa2     NVIDIA binary Xorg driver
rc  nvidia-glx-new    169.12+2.6.24.18-26.3     NVIDIA binary XFree86 4.x/X.Org 'new' driver
ii  nvidia-kernel-common    20051028+1ubuntu8      NVIDIA binary kernel module common files
rc  nvidia-settings     1.0+20080304-0ubuntu1.1      Tool of configuring the NVIDIA graphics driv
ii  nvidia-settings-190    190.42-0ubuntu1~karmic~nvidiavdpauppa1    Tool of configuring the NVIDIA graphics driv
```

(note, I as you can see I also tried the 195 drivers, but when that didn't work either, I went back to 190).  What's interesting is that these package names say karmic in them, even though I added the hardy repo.  Strange, but they load into the kernel, so it should be OK:

```
user@mythtv:~$ lsmod | grep nvidia
nvidia               4718832  0
i2c_core               24832  13 dvb_pll,lgdt330x,cx88_vp3054_i2c,tuner,tea5767,tda8290,tuner_simple,mt20xx,tea5761,cx88xx,i2c_algo_bit,tveeprom,nvidia
agpgart                34760  2 nvidia,intel_agp
```

What I think is the problem is that for some reason the card is not recognized:

```
user@mythtv:~$ lspci | grep nVidia
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0a65 (rev a2)
01:00.1 Audio device: nVidia Corporation Unknown device 0be3 (rev a1)
```

It just says "Unknown device"
That is with 8.04

What is interesting is that I have a separate partition with 9.10 on it (long story why both), and it is recognized there:

```
user@mythtv:~$ lspci | grep nVidia
01:00.0 VGA compatible controller: nVidia Corporation GT200 [GeForce 210] (rev a2)
01:00.1 Audio device: nVidia Corporation Device 0be3 (rev a1)
```

This would explain why X would not work with 8.04.  Here is the only (EE) in the 8.04 X log:

```
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
```

Looking into this further, how do I reconcile these two outputs:
```

user@mythtv:~$ cat /proc/driver/nvidia/version
NVRM version: NVIDIA Linux x86 Kernel Module  96.43.05  Tue Jan 22 19:36:58 PST 2008
GCC version:  gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)

user@mythtv:~$ for i in `locate nvidia.ko`; do ls -la $i; done
ls: cannot access /lib/modules/2.6.24-24-generic/kernel/drivers/video/nvidia.ko: No such file or directory
-rw-r--r-- 1 root root 9587988 2009-12-16 19:32 /lib/modules/2.6.24-24-generic/updates/dkms/nvidia.ko
```
 
The first one says I have a module loaded that was compiled in Jan 2008.

I posted much of this over at the [nvnews.net linux forum]("http://www.nvnews.net/vbulletin/showthread.php?p=2146881").  Aaron from nvidia said:

[QUOTE=AaronP]That first date is when the driver was built at NVIDIA and the second date is when the kernel module was compiled for your system (i.e. when you installed that package).  You're right that the wrong version of the driver is installed.  I'd suggest contacting Ubuntu's support forum to figure out why the Ubuntu packages are not working correctly.[/QUOTE]

So:

[LIST]
[*]I have the 190 driver loaded, and apt-get and dpkg confirms this.  However it appears an older one is loaded into the kernel.

[*]nvidia says that this appears to be a packaging issue, and I need to "check with ubuntu. 
[/LIST]

any ideas?

---

### Post by RedSingularity on 2009-12-19
Interesting, have you tried the card with an older set of drivers?

---

### Post by jsundqui on 2009-12-19
Yes.  I have tried with older drivers.  I am leaving out lots of stuff I tried for brevity.  But before I added in the launchpad VDPAU repos, I tried loading the nvidia 190 driver using the shell script-driven driver from the NV website.  That really screwed things up, and I couldn't get the old 8300GS card to work any more even.  I did the --uninstall with the script and reloaded the 169 drivers (nvidia-glx-new) and got the old 8300GS card working again.

Then I put the new G210 card in and it didn't work (as expected, since it needs the 190 drivers).  I added in the the nvidia-glx-190 drivers and here I am.

Latest bit of investigation:  The location of those nvidia.ko files are that "locate nvidia.ko" found were in the /lib/modules/2.6.24-24-generic tree, but I am running 2.6.24-26!  The 2.6.24-26 module tree does not have any nvidia modules anywhere.  But the system continues to tell me I have nvidia-glx-190 installed.  

This is all very strange because lsmod clearly shows an nvidia module being loaded into the kernel.  But they are not from the /lib/modules/2.6.24-26-generic directory, and in any case are not driver version 190!

---

### Post by delectate on 2009-12-19
ubuntuforums.orgubuntuforums.org/newreply.php
I hope my 1080p movies could play well with it……

now i use 185 driver,some time ,vdpau doesn't work

---

### Post by jsundqui on 2009-12-20
It seems to me there must be an error in the launchpad packaging for the 190 driver.

This is what I've done now:

Went back to the old 8300GS card, backed out the 190 driver and loaded nvidia-glx-new (169) again. 

hardy works.  /proc/driver/nvidia/version says 169...

removed 169 and added in nvidia-glx-190

doesn't work.  /proc/driver/nvidia/version says 96.something

removed 190 and added in nvidia-glx-195 (which is still beta, so not too wild about that).

works.  /proc/driver/nvidia/version says 195...

Put the G210 back in.  

works (although first time came up with the nv driver, just had to run nvidia-xconfig and now comes up with the proprietary driver).

Hopefully this beta driver is stable enough.

---

