---
title: "proprietary drivers not showing up"
date: 2019-02-03
forum: Installation &amp; Upgrades
---

### Post by roomboy on 2019-02-03
Currently running 390 (proprietary)  Would like to be able to update to 396 (proprietary). but it is only showing up as (open source)

I have followed a few online tutorials as to install Proprietary drivers, But it never works.

---

### Post by CatKiller on 2019-02-03
The proprietary drivers installed from the PPA are listed as open source for some reason, even though they aren't. Ignore that part of the description.

---

### Post by roomboy on 2019-02-03
I installed the new driver,  and now the game Im trying to run on Steam Play fails to join server. it freezes up.  If I go back to the 390 driver, the game loads and runs. 
The game, War of Rights was released after the Valve release/+support for linux (Steam Play).

---

### Post by roomboy on 2019-02-04
Im currently using [COLOR=#333333]ppa:graphics-drivers/dev   ,   ppa.launchpad.net/graphics-drivers/dev/ubuntu bionic

[/COLOR]https://launchpad.net/~graphics-drivers/+archive/ubuntu/dev

When I tried another PPA for drivers, I received 4 different options. All 4 drivers failed to work on my game. all open source. The only driver that allows me to play is 390 proprietary.  I heard that having the 396 driver is the best one to date for Steam while gaming with Linux. it's not working. But I want to get it to work.

---

### Post by Bashing-om on 2019-02-04
roomboy; Hello - Welcome to the forum.

What release is this ?
and
what card ?
show us - between code tags - the output of terminal command:
```

lspci -nnk | grep -iA3 vga

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

And verify there are no driver conflicts:
```

dpkg -l | grep nvidia

```

[INDENT]we see where we go from here[/INDENT]

---

### Post by roomboy on 2019-02-05
```
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GP107 [GeForce GTX 1050 Ti] [10de:1c82] (rev a1)
	Subsystem: Gigabyte Technology Co., Ltd GP107 [GeForce GTX 1050 Ti] [1458:3746]
	Kernel driver in use: nvidia
	Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia
```


```
ii  libnvidia-cfg1-390:amd64                   390.77-0ubuntu0.18.04.1                      amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-390                       390.77-0ubuntu0.18.04.1                      all          Shared files used by the NVIDIA libraries
ii  libnvidia-common-396                       396.54.09-0ubuntu0~gpu18.04.1                all          Shared files used by the NVIDIA libraries
ii  libnvidia-compute-390:amd64                390.77-0ubuntu0.18.04.1                      amd64        NVIDIA libcompute package
ii  libnvidia-compute-390:i386                 390.77-0ubuntu0.18.04.1                      i386         NVIDIA libcompute package
rc  libnvidia-compute-396:amd64                396.54.09-0ubuntu0~gpu18.04.1                amd64        NVIDIA libcompute package
rc  libnvidia-compute-396:i386                 396.54.09-0ubuntu0~gpu18.04.1                i386         NVIDIA libcompute package
rc  libnvidia-compute-410:amd64                410.78-0ubuntu1~gpu18.04.1                   amd64        NVIDIA libcompute package
rc  libnvidia-compute-415:amd64                415.25-0ubuntu0~gpu18.04.1                   amd64        NVIDIA libcompute package
ii  libnvidia-decode-390:amd64                 390.77-0ubuntu0.18.04.1                      amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-390:i386                  390.77-0ubuntu0.18.04.1                      i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-390:amd64                 390.77-0ubuntu0.18.04.1                      amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-390:i386                  390.77-0ubuntu0.18.04.1                      i386         NVENC Video Encoding runtime library
ii  libnvidia-fbc1-390:amd64                   390.77-0ubuntu0.18.04.1                      amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-390:i386                    390.77-0ubuntu0.18.04.1                      i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-390:amd64                     390.77-0ubuntu0.18.04.1                      amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-390:i386                      390.77-0ubuntu0.18.04.1                      i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-ifr1-390:amd64                   390.77-0ubuntu0.18.04.1                      amd64        NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  libnvidia-ifr1-390:i386                    390.77-0ubuntu0.18.04.1                      i386         NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  nvidia-compute-utils-390                   390.77-0ubuntu0.18.04.1                      amd64        NVIDIA compute utilities
rc  nvidia-compute-utils-396                   396.54.09-0ubuntu0~gpu18.04.1                amd64        NVIDIA compute utilities
rc  nvidia-compute-utils-410                   410.78-0ubuntu1~gpu18.04.1                   amd64        NVIDIA compute utilities
rc  nvidia-compute-utils-415                   415.25-0ubuntu0~gpu18.04.1                   amd64        NVIDIA compute utilities
ii  nvidia-dkms-390                            390.77-0ubuntu0.18.04.1                      amd64        NVIDIA DKMS package
rc  nvidia-dkms-396                            396.54.09-0ubuntu0~gpu18.04.1                amd64        NVIDIA DKMS package
rc  nvidia-dkms-410                            410.78-0ubuntu1~gpu18.04.1                   amd64        NVIDIA DKMS package
rc  nvidia-dkms-415                            415.25-0ubuntu0~gpu18.04.1                   amd64        NVIDIA DKMS package
ii  nvidia-driver-390                          390.77-0ubuntu0.18.04.1                      amd64        NVIDIA driver metapackage
ii  nvidia-kernel-common-390                   390.77-0ubuntu0.18.04.1                      amd64        Shared files used with the kernel module
rc  nvidia-kernel-common-396                   396.54.09-0ubuntu0~gpu18.04.1                amd64        Shared files used with the kernel module
rc  nvidia-kernel-common-410                   410.78-0ubuntu1~gpu18.04.1                   amd64        Shared files used with the kernel module
rc  nvidia-kernel-common-415                   415.25-0ubuntu0~gpu18.04.1                   amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-390                   390.77-0ubuntu0.18.04.1                      amd64        NVIDIA kernel source package
ii  nvidia-prime                               0.8.8.2                                      all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                            415.25-0ubuntu0~gpu18.04.1                   amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-390                           390.77-0ubuntu0.18.04.1                      amd64        NVIDIA driver support binaries
ii  xserver-xorg-video-nvidia-390              390.77-0ubuntu0.18.04.1                      amd64        NVIDIA binary Xorg driver
```




Thank you :)
I switched from windows to Linux this past year. I really want to make a go at it. all of my friends keep telling me to just stop and re-install windows. 
Never Again!

---

### Post by Bashing-om on 2019-02-05
roomboy; Uh Huh ...

There is a driver conflict:
> 
ii libnvidia-common-396 396.54.09-0ubuntu0~gpu18.04.1 all Shared files used by the NVIDIA libraries
ii libnvidia-compute-390:amd64 390.77-0ubuntu0.18.04.1 amd64 NVIDIA libcompute package

ii nvidia-settings 415.25-0ubuntu0~gpu18.04.1 amd64 Tool for configuring the NVIDIA graphics driver

where that leading 'ii' is desired state= (i)nstalled and the status = (i)nstalled.

Let's clean things up and give it a whirl for the system to choose the correct driver in install.
Run terminal commands:
```

sudo apt remove --purge nvidia*
dpkg -l | awk '/^rc/{print $2}' | xargs sudo dpkg -P
sudo apt update
sudo apt full-upgrade
sudo ubuntu-drivers autoinstall

```
rc:
While there is no built in way to remove all of your configuration information from your removed packages you can remove all configuration data from every removed package. To purge all removed but not yet purged packages, where The state is rc, the package is removed, but the config files are not removed.

Reboot the system for the changes to take effect.

Now what is the status ?

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by roomboy on 2019-02-05
did everything. Computer rebooted and running the open source 396 driver. game freezes at loading. 390 proprietary is still available as an option, which I know will work with it.

When I switch back to 390, a bunch of error popups, pop up. but the game works.

---

### Post by Bashing-om on 2019-02-05
roomboy;  Well -

> 
When I switch back to 390, a bunch of error popups, pop up. but the game works.


Show us the errors :)

Is the GPU manager happy ?
Post back:
```

cat /var/log/gpu-manager.log

```

see what we can work out from here.

[INDENT]gots to be a reason
[/INDENT]

---

### Post by roomboy on 2019-02-05
```
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /opt/amdgpu-pro/bin/amdgpu-pro-px
Looking for nvidia modules in /lib/modules/4.17.0-041700-generic/updates/dkms
Found nvidia module: nvidia-modeset.ko
Looking for amdgpu modules in /lib/modules/4.17.0-041700-generic/updates/dkms
Is nvidia loaded? yes
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is intel loaded? no
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is amdgpu versioned? no
Is amdgpu pro stack? no
Is nouveau loaded? no
Is nouveau blacklisted? yes
Is nvidia kernel module available? yes
Is amdgpu kernel module available? no
Vendor/Device Id: 10de:1c82
BusID "PCI:1@0:0:0"
Is boot vga? yes
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Does it require offloading? no
last cards number = 1
Has amd? no
Has intel? no
Has nvidia? yes
How many cards? 1
Has the system changed? No
Single card detected
Nothing to do
```

---

### Post by hgkrug1 on 2019-02-08
I have  a similar problem.  Freshly install Ubunto 18.10 Desktop and the system does not see the internal Video or a USB based video.  I used the commands (as mentioned above):

sudo apt remove --purge nvidia*
dpkg -l | awk '/^rc/{print $2}' | xargs sudo dpkg -P
sudo apt update
sudo apt full-upgrade
sudo ubuntu-drivers autoinstall

Response: "No drivers found for automatic installation"

Any help?
Thanks! Gert Kruger

---

### Post by Bashing-om on 2019-02-08
hgkrug1; Hello -

> 
Response: "No drivers found for automatic installation"


Are we looking at Intel/AMD graphics, as these are provided in the kernel ?

Please show is what we are working with:
```

lspci -k|grep -iEA5 'vga|3d'

```

See where we go from here.

[INDENT][INDENT]ain't nothing but a [/INDENT][/INDENT]

---

### Post by roomboy on 2019-02-08
I have Ubuntu 18.04, my GPU is recognized, along with the internal Video or a USB based video.
There is no )proprietary) driver for 396.  Only (opensource).

All of my drivers do show up when I load their PPA.  There is only one that shows up as (proprietary). the most recent one is (opensource), and doesn't work with my game. I just want to play it.

---

### Post by hgkrug1 on 2019-05-21
I worked on this ubuntu 18.10 for several weeks (several updates).  When I tried again:

sudo ubuntu-drivers autoinstall

It worked, but after reboot my system was completely jammed.  No Desktop etc.  I had to reinstall.

I have now upgraded to 19.04 and will test it.

---

### Post by hgkrug1 on 2019-05-21
Same problem with Ubuntu 19.04.  After "sudo ubuntu-drivers autoinstall" the system is busted. I have a Dell Vostro 3670 PC with the following deatils:

Intel(R) Core(TM) i7-8700 CPU @ 3.20GHz; 
Motherboard: Dell Ince OV8F20;
12 GB RAM;
NVIDIA Corporation GP107 [GeForce GTX 1050] [10de:1c81] (rev a1) (prog-if 00 [VGA controller]);

---

### Post by hgkrug1 on 2019-05-21
I see this is issue described at [https://medium.com/datadriveninvestor/install-tensorflow-gpu-to-use-nvidia-gpu-on-ubuntu-18-04-do-ai-71b0ce64ebc5](https://medium.com/datadriveninvestor/install-tensorflow-gpu-to-use-nvidia-gpu-on-ubuntu-18-04-do-ai-71b0ce64ebc5) with a potential solution if the logon does not work after reboot.

---

### Post by hgkrug1 on 2019-05-23
I found several proposed solutions for this issue to install the Nvidia drivers.  None of them work for me.  I found 2 methods that enable you to recover the Desktop environment when this happens:

First by Fossfreedom at - [https://discourse.ubuntubudgie.org/t/nvidia-390-black-screen/97/14](https://discourse.ubuntubudgie.org/t/nvidia-390-black-screen/97/14)

You have to do a safe boot and go to root, then:
sudo apt-get remove nvidia-*
sudo apt install nvidia-prime
sudo prime-select intel

Then reboot.

Second form sgian entry #3 at [https://ubuntuforums.org/showthread.php?t=2399985](https://ubuntuforums.org/showthread.php?t=2399985)

Also do a safe boot and go to root.  Then:

sudo apt purge nvidia*
sudo apt install --reinstall xorg xserver-xorg-core

Tten reboot.

---

### Post by hgkrug1 on 2019-05-23
I found a solution for this Nvidia driver issue (on ubuntu 18 and 19). See instructions at the top at [https://ubuntuforums.org/showthread....nvidia+drivers]("https://ubuntuforums.org/showthread.php?t=2419319&highlight=nvidia+drivers"), it worked for me!

Unfortunately, I could not reproduce the installation on a freshly installed system.

However, I found a suitable fix at entry #19 of [https://bugs.launchpad.net/gdm/+bug/1798790](https://bugs.launchpad.net/gdm/+bug/1798790)

Try this as a workaround: edit /etc/gdm3/custom.conf 
and uncomment the line: 
#WaylandEnable=false

---

