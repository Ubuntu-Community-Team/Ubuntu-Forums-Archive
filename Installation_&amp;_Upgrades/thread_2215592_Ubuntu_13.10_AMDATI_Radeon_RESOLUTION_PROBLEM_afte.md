---
title: "Ubuntu 13.10 AMD/ATI Radeon RESOLUTION PROBLEM after upgrade from 13.04"
date: 2014-04-07
forum: Installation &amp; Upgrades
---

### Post by JNx4TnT on 2014-04-07
0 down vote favorite
    

I have a problem with my screen resolution after I upgraded from Ubuntu 13.04 to Ubuntu 13.10.

My computer: HP ProBook 4720s :: Intel® Core™ i7 CPU M 640 @ 2.80GHz × 4 :: 64-bit

In System settings -> Displays:

The screen resolution seems stuck on "Built-in Display resolution 1600x900 (16:9)". I cannot change to any other resolution neither on my laptop screen nor when I connect to my external monitor. "Detect displays" doesn't work.

Here is a screenshot: [https://drive.google.com/file/d/0Bw6YqPXyv7V8Y21TTmpYU1ZNUVk/edit?usp=sharing](https://drive.google.com/file/d/0Bw6YqPXyv7V8Y21TTmpYU1ZNUVk/edit?usp=sharing)

When I connect my external monitor, I see black stripes on the side. The resolution is incorrect: [https://drive.google.com/file/d/0Bw6YqPXyv7V8Z1VnTGx1RmdEaVk/edit?usp=sharing](https://drive.google.com/file/d/0Bw6YqPXyv7V8Z1VnTGx1RmdEaVk/edit?usp=sharing)

I removed AMD Legacy drivers as described here: [URL="http://askubuntu.com/questions/363255/lubuntu-13-10-amd-ati-radeon-laptop-screen-is-black-after-upgrade-from-13-04"]http://askubuntu.com/questions/363255/lubuntu-13-10-amd-ati-radeon-laptop-screen-is-black-after-upgrade-from-13-04
[/URL]

Here is the output from glxinfo:

```
henry@henry-prbook:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_INTEL_swap_event, 
    GLX_MESA_copy_sub_buffer, GLX_OML_swap_method, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGI_make_current_read
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_fbconfig_float, 
    GLX_ARB_framebuffer_sRGB, GLX_ARB_get_proc_address, GLX_ARB_multisample, 
    GLX_EXT_buffer_age, GLX_EXT_create_context_es2_profile, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_buffer_age, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_make_current_read
OpenGL vendor string: VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits)
OpenGL version string: 2.1 Mesa 10.2.0-devel
OpenGL shading language version string: 1.30
```

More info:

```

$ lspci | grep -i vga
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV710/M92 [Mobility Radeon HD 4350/4550]


```

More info (full lspci):

```

henry@henry-prbook:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV710/M92 [Mobility Radeon HD 4350/4550]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] RV710/730 HDMI Audio [Radeon HD 4000 series]
44:00.0 Network controller: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe
45:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 03)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```

More info:
```

henry@henry-prbook:~$ sudo lshw -c video
sudo: unable to resolve host henry-prbook
[sudo] password for henry: 
  *-display               
       description: VGA compatible controller
       product: RV710/M92 [Mobility Radeon HD 4350/4550]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:47 memory:c0000000-cfffffff ioport:5000(size=256) memory:d4500000-d450ffff memory:d4520000-d453ffff

```

More info:

```

henry@henry-prbook:~$ lspci -nnk | grep -iA3 vga
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV710/M92 [Mobility Radeon HD 4350/4550] [1002:9555]
    Subsystem: Hewlett-Packard Company ProBook 4720s GPU (Mobility Radeon HD 4350) [103c:1411]
    Kernel driver in use: radeon
01:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] RV710/730 HDMI Audio [Radeon HD 4000 series] [1002:aa38]

```

I see a lot of these errors in my /var/log/Xorg.0.log:

```

[ 15368.317] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 15368.317] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 15368.317] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 15368.317] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 15368.317] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 15368.317] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument

```

I cannot find the solution. I'm stuck with this resolution. Please help!!! If any other information is needed, please ask.

Thank you!

---

### Post by ajgreeny on 2014-04-07
The only driver for that card is the open source one that was used when you installed, so you must remove the proprietary driver you had and restore the OS driver.

Did you do all this?
```
sudo apt-get remove --purge fglrx*
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
(No point running [COLOR=#ff0000]sudo dpkg-reconfigure xserver-xorg[/COLOR] as it is now a deprecated command and does nothing any more.)
sudo shutdown -r now
```

---

### Post by Mark Phelps on 2014-04-07
I used to use an AMD 4290, also with the default Radeon drivers, and found that I had to add "xforcevesa" to the kernel boot parameters in order to get both multiple screens and full resolution on each.

---

### Post by JNx4TnT on 2014-04-07
Hello, I tried your commands. 

> **ajgreeny said:**
> The only driver for that card is the open  source one that was used when you installed, so you must remove the  proprietary driver you had and restore the OS driver.

Did you do all this?
```
sudo apt-get remove --purge fglrx*
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
(No point running [COLOR=#ff0000]sudo dpkg-reconfigure xserver-xorg[/COLOR] as it is now a deprecated command and does nothing any more.)
sudo shutdown -r now
```


I received an error in the 3RD command. Here's the output:

```


henry@henry-prbook:~$ sudo apt-get remove --purge fglrx*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'fglrx-driver-dev' for regex 'fglrx*'
Note, selecting 'fglrx-pxpress' for regex 'fglrx*'
Note, selecting 'fglrx-updates' for regex 'fglrx*'
Note, selecting 'fglrx-dev' for regex 'fglrx*'
Note, selecting 'fglrx-control' for regex 'fglrx*'
Note, selecting 'xorg-driver-fglrx' for regex 'fglrx*'
Note, selecting 'fglrx-kernel-source' for regex 'fglrx*'
Note, selecting 'fglrx-amdcccle-updates' for regex 'fglrx*'
Note, selecting 'xfree86-driver-fglrx' for regex 'fglrx*'
Note, selecting 'xfree86-driver-fglrx-dev' for regex 'fglrx*'
Note, selecting 'fglrx-modaliases' for regex 'fglrx*'
Note, selecting 'fglrx-12-dev' for regex 'fglrx*'
Note, selecting 'xorg-driver-fglrx-dev' for regex 'fglrx*'
Note, selecting 'fglrx-13-dev' for regex 'fglrx*'
Note, selecting 'fglrx-amdcccle-12' for regex 'fglrx*'
Note, selecting 'fglrx-amdcccle-13' for regex 'fglrx*'
Note, selecting 'fglrx-glx' for regex 'fglrx*'
Note, selecting 'fglrx-control-qt2' for regex 'fglrx*'
Note, selecting 'fglrx-amdcccle' for regex 'fglrx*'
Note, selecting 'fglrx-driver' for regex 'fglrx*'
Note, selecting 'fglrx-12' for regex 'fglrx*'
Note, selecting 'fglrx-13' for regex 'fglrx*'
Note, selecting 'fglrx-updates-dev' for regex 'fglrx*'
Note, selecting 'fglrx' for regex 'fglrx*'
Package 'fglrx-glx' is not installed, so not removed
Package 'fglrx-control-qt2' is not installed, so not removed
Package 'xfree86-driver-fglrx-dev' is not installed, so not removed
Package 'xorg-driver-fglrx-dev' is not installed, so not removed
Package 'fglrx-kernel-source' is not installed, so not removed
Package 'fglrx-modaliases' is not installed, so not removed
Package 'xfree86-driver-fglrx' is not installed, so not removed
Package 'xorg-driver-fglrx' is not installed, so not removed
Package 'fglrx-pxpress' is not installed, so not removed
Package 'fglrx-amdcccle-updates' is not installed, so not removed
Package 'fglrx-updates' is not installed, so not removed
Package 'fglrx-updates-dev' is not installed, so not removed
Package 'fglrx-amdcccle' is not installed, so not removed
Package 'fglrx' is not installed, so not removed
Package 'fglrx-dev' is not installed, so not removed
Package 'fglrx-12' is not installed, so not removed
Package 'fglrx-12-dev' is not installed, so not removed
Package 'fglrx-amdcccle-12' is not installed, so not removed
Package 'fglrx-13' is not installed, so not removed
Package 'fglrx-13-dev' is not installed, so not removed
Package 'fglrx-amdcccle-13' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

henry@henry-prbook:~$ sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'xserver-xorg-video-ati' is not installed, so not removed
Package 'xserver-xorg-video-radeon' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


henry@henry-prbook:~$ sudo apt-get install xserver-xorg-video-ati
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 xserver-xorg-video-ati : Depends: xorg-video-abi-14
                          Depends: xserver-xorg-video-glamoregl but it is not going to be installed
                          Depends: xserver-xorg-video-radeon but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


```

Thanks for responding. I will be awaiting if you or anyone can continue to help ;)

---

### Post by JNx4TnT on 2014-04-07
> **Mark Phelps said:**
> I used to use an AMD 4290, also with the default Radeon drivers, and found that I had to add "xforcevesa" to the kernel boot parameters in order to get both multiple screens and full resolution on each.

Hi, I tried this and this did not solve my problem. Still hoping for some help... THANK YOU.

---

### Post by JNx4TnT on 2014-04-07
I see dependencies problems. Could that be the problem?

Here is info:

```


henry@henry-prbook:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ saucy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ saucy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ saucy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ saucy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ saucy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ saucy universe
deb http://us.archive.ubuntu.com/ubuntu/ saucy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ saucy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ saucy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ saucy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ saucy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ saucy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ar.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://ar.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu saucy main
deb-src http://extras.ubuntu.com/ubuntu saucy main

deb http://us.archive.ubuntu.com/ubuntu/ saucy-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ saucy-security main restricted
deb http://us.archive.ubuntu.com/ubuntu/ saucy-security universe
deb-src http://us.archive.ubuntu.com/ubuntu/ saucy-security universe
deb http://us.archive.ubuntu.com/ubuntu/ saucy-security multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ saucy-security multiverse


```

Thanks.

---

### Post by JNx4TnT on 2014-04-10
anyone?? any pointer for the problem?? :(

---

### Post by JNx4TnT on 2014-04-13
Hello. I solved this problem. This might help anyone in the future that has the same problem I came across. I solved with:

```


sudo apt-get install ppa-purge
sudo ppa-purge xorg-edgers
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install xserver-xorg-core

```

After a reboot... I had a black screen. So then I ran:

```

sudo apt-get install ubuntu-desktop

```

I rebooted and everything is perfect. I have all screen resolutions for built-in laptop screen and external monitor.

:)

---

