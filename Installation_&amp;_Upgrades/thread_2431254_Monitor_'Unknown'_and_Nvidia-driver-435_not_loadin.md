---
title: "Monitor 'Unknown' and Nvidia-driver-435 not loading"
date: 2019-11-13
forum: Installation &amp; Upgrades
---

### Post by yaminb on 2019-11-13
I went though some updates recently 19.10 and for some reason I can't change my resolution beyond 1024x768.
Everything used to work fine before this update which did included some kernel headers.
When I go to nvidia-settings it says the driver is not loaded
 nvidia-settings 
ERROR: NVIDIA driver is not loaded
ERROR: Unable to load info from any available system

Everything was working fine before the ubuntu updates on nvidia-driver-435.

I've google and tried everything I've seen. Purging the drivers. Reinstalling them.
When I purge the nvidia drivers, it goes to the nouveau ones and it looks like the proper screen resolution, but it just loops on the login screen (as I experienced in the past). So I drop to the terminal and install the 435 driver.

Not sure if it helps, but in the Ubuntu About, it shows this as the graphics
llvmpipe (LLVM 9.0, 256 bits) I honestly can't remember what this used to say when it was working, but that just looks weird


Any ideas?

---

### Post by CatKiller on 2019-11-14
> **yaminb said:**
>  So I drop to the terminal and install the 435 driver.

The command that you use and the output that you get are critical information if you hope for someone to be able to help you.

---

### Post by yaminb on 2019-11-14
> sudo apt-get purge nvidia-*

reboot. do terminal login with ctrl-alt-f3

> sudo apt-get install nvidia-driver-435


Everything installs fine. It just doesn't work anymore. If there are output commands you need me to run, I can provide them.
> $ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1024 x 768, current 1024 x 768, maximum 1024 x 768
default connected primary 1024x768+0+0 0mm x 0mm
   1024x768      76.00* 




> nvidia-smi
NVIDIA-SMI has failed because it couldn't communicate with the NVIDIA driver. Make sure that the latest NVIDIA driver is installed and running.

> [B]lsmod | grep nvidia
i2c_nvidia_gpu         16384  0

[/B]


> [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) eoan main

---

### Post by yaminb on 2019-11-14
also just tried 440 driver. same as 435. I can login to Gnome, but the monitor is stuck at a the 1024 768 resolution and it says nvidia driver not loaded
> sudo apt-get install xserver-xorg-video-nvidia-440
sudo apt-get install nvidia-driver-440

---

### Post by yaminb on 2019-11-14
Also just tried 
> /etc/default/grub
GRUB_CMDLINE_LINUX="video=default:d
sudo update-grub
 No impact. used default as that what comes up in xrandr

---

### Post by yaminb on 2019-11-14
> nxi -SMCGx 
System:
  Host: XXXX Kernel: 5.3.0-23-generic x86_64 bits: 64 compiler: gcc 
  v: 9.2.1 Desktop: Gnome 3.34.1 Distro: Ubuntu 19.10 (Eoan Ermine) 
Machine:
  Type: Desktop Mobo: ASRock model: H87M-ITX serial: <root required> 
  UEFI: American Megatrends v: P2.40 date: 01/13/2016 
CPU:
  Topology: Quad Core model: Intel Core i5-4670K bits: 64 type: MCP 
  arch: Haswell rev: 3 L2 cache: 6144 KiB 
  flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx 
  bogomips: 27190 
  Speed: 800 MHz min/max: 800/3800 MHz Core speeds (MHz): 1: 800 2: 800 
  3: 800 4: 800 
Graphics:
  Device-1: NVIDIA TU106 [GeForce RTX 2060 Rev. A] vendor: Micro-Star MSI 
  driver: N/A bus ID: 01:00.0 
  Display: x11 server: X.Org 1.20.5 driver: fbdev,nouveau 
  unloaded: modesetting,vesa resolution: 1024x768~76Hz 
  OpenGL: renderer: llvmpipe (LLVM 9.0 256 bits) v: 3.3 Mesa 19.2.1 
  direct render: Yes 


> xrandr --verbose
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1024 x 768, current 1024 x 768, maximum 1920 x 1080
default connected primary 1024x768+0+0 (0x2b3) normal (normal) 0mm x 0mm
    Identifier: 0x2b2
    Timestamp:  656420
    Subpixel:   unknown
    Clones:    
    CRTC:       0
    CRTCs:      0
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    _MUTTER_PRESENTATION_OUTPUT: 0 
    non-desktop: 0 
        supported: 0, 1
  1024x768 (0x2b3) 59.769MHz *current
        h: width  1024 start    0 end    0 total 1024 skew    0 clock  58.37KHz
        v: height  768 start    0 end    0 total  768           clock  76.00Hz
  1920x1080_60.00 (0x2be) 173.000MHz -HSync +VSync
        h: width  1920 start 2048 end 2248 total 2576 skew    0 clock  67.16KHz
        v: height 1080 start 1083 end 1088 total 1120           clock  59.96Hz


note the 1920x1080 I had tried to add manually, but it doesn't work.

---

### Post by yaminb on 2019-11-14
sudo vi /var/log/Xorg.0.log


>     39.282] (II) LoadModule: "glx"
[    39.369] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    39.581] (II) Module glx: vendor="X.Org Foundation"
[    39.581]    compiled for 1.20.5, module version = 1.0.0
[    39.581]    ABI class: X.Org Server Extension, version 10.0
[    39.581] (II) LoadModule: "nvidia"
[    39.582] (WW) Warning, couldn't open module nvidia
[    39.582] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    39.707] (==) Matched nouveau as autoconfigured driver 0
[    39.707] (==) Matched modesetting as autoconfigured driver 1
[    39.707] (==) Matched fbdev as autoconfigured driver 2
[    39.707] (==) Matched vesa as autoconfigured driver 3
[    39.707] (==) Assigned the driver to the xf86ConfigLayout
[    39.707] (II) LoadModule: "nouveau"
[    39.708] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    39.817] (II) Module nouveau: vendor="X.Org Foundation"
[    39.817]    compiled for 1.20.3, module version = 1.0.16
[    39.817]    Module class: X.Org Video Driver
[    39.817]    ABI class: X.Org Video Driver, version 24.0
[    39.817] (II) LoadModule: "modesetting"


---

### Post by yaminb on 2019-11-14
> Section "Files"
#    ModulePath "/usr/lib/x86_64-linux-gnu/nvidia/xorg"
EndSection



Also tried this (uncommented it), but then gnome wouldn't boot. So commented it out. xorg.conf

---

### Post by yaminb on 2019-11-14
Tried to install the Nvidia drivers from Nvidia
[https://www.nvidia.com/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86_64/440.31/NVIDIA-Linux-x86_64-440.31.run&lang=us&type=TITAN](https://www.nvidia.com/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86_64/440.31/NVIDIA-Linux-x86_64-440.31.run&lang=us&type=TITAN)
> ERROR: Failed to run `/usr/sbin/dkms build -m nvidia -v 440.31 -k
         5.3.0-23-generic`: Error! Your kernel headers for kernel
         5.3.0-23-generic cannot be found.                                     
         Please install the linux-headers-5.3.0-23-generic package,           
         or use the --kernelsourcedir option to tell DKMS where it's located   






sudo apt-get install linux-headers-5.3.0-23-generic

> pkg: error processing archive /var/cache/apt/archives/linux-headers-5.3.0-23_5.3.0-23.25_all.deb (--unpack):
 unable to open '/usr/src/linux-headers-5.3.0-23/arch/mips/include/asm/mach-lasat/irq.h.dpkg-new': Operation not permitted
Selecting previously unselected package linux-headers-5.3.0-23-generic.
Preparing to unpack .../linux-headers-5.3.0-23-generic_5.3.0-23.25_amd64.deb ...
Unpacking linux-headers-5.3.0-23-generic (5.3.0-23.25) ...
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-5.3.0-23_5.3.0-23.25_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



---

### Post by #&amp;thj^% on 2019-11-14
Always wise with Ubuntu to stay within Ubuntu repo drivers. ;)
Anyway if your can remove/purge all nvidia drivers you have tried to this point and start fresh.
Also can you provide this:
```
inxi -G
```
I'll see if I can help here.

---

### Post by yaminb on 2019-11-14
Alright. looks like it is fixed


> 
sudo apt-get install --reinstall linux-headers-5.3.0-23-generic 
[FONT=monospace][COLOR=#c20cb9]**sudo**[/COLOR] apt update [COLOR=#660033]--fix-missing[/COLOR][/FONT]

[FONT=monospace][COLOR=#c20cb9]**sudo**[/COLOR] apt [COLOR=#c20cb9]**install**[/COLOR] [COLOR=#660033]-f[/COLOR][/FONT]
sudo **apt**-**get install** --**reinstall nvidia-drivers-435**


i think something previously mucked up when doing the inux-headers-5.3.0-23-generic package.
after getting that properly installed. everything worked. Don't know why I didn't see this before. But when using the nvidia installer, the error message was pretty clear, so the resolution was easy.
I don't recall seeing this error when using the apt install of nvidia-drivers, but I could just have been blind.

---

### Post by #&amp;thj^% on 2019-11-14
Nice. :) and the Old Saying "All's well that ends well"

---

