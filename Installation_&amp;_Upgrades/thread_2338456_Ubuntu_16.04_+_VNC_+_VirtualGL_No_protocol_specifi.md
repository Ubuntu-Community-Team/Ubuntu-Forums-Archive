---
title: "Ubuntu 16.04 + VNC + VirtualGL: No protocol specified /unable to open display :0"
date: 2016-09-28
forum: Installation &amp; Upgrades
---

### Post by wover on 2016-09-28
Dear all,

First of all it's my first post here, so sorry if i'm in the wrong sub-forum or sth else. Just let me know and i'll try to correct it.

Regarding my problem:
I'm using a workstation for visualisation of some simulation data. For this we were using Ubuntu 14.04 + VNC and VirtualGL for 3D applications (gnome, xfce4 as Desktop environment). Everything was working, but after upgrading to 16.04 i just cannot get VirtualGL running properly utilizing the Nvidia Titan Z.
```

wolfgang@WS-Mikro:~$ lspci | grep VGA
07:00.0 VGA compatible controller: ASPEED Technology, Inc. ASPEED Graphics Family (rev 30)
83:00.0 VGA compatible controller: NVIDIA Corporation GK110B [GeForce GTX TITAN Z] (rev a1)

wolfgang@WS-Mikro:~$ lspci | grep NVIDIA
83:00.0 VGA compatible controller: NVIDIA Corporation GK110B [GeForce GTX TITAN Z] (rev a1)
83:00.1 Audio device: NVIDIA Corporation GK110 HDMI Audio (rev a1)
84:00.0 3D controller: NVIDIA Corporation GK110B [GeForce GTX TITAN Z] (rev a1)

```

```

wolfgang@WS-Mikro:~$ vglrun +v glxgears
[VGL] Shared memory segment ID for vglconfig: 950279
[VGL] VirtualGL v2.5 64-bit (Build 20160215)
[VGL] Opening connection to 3D X server :0
No protocol specified
[VGL] ERROR: Could not open display :0.

```

in /etc/log/Xorg.0.log i get some error messages, but to be honest i have no idea how to resolve this issue...
```

wolfgang@WS-Mikro:~$ tail /var/log/Xorg.0.log
[   251.081] (WW) Disabling Mouse0
[   251.081] (WW) Disabling Keyboard0
[   251.081] (EE) [drm] Failed to open DRM device for (null): -22
[   251.081] (EE) [drm] Failed to open DRM device for (null): -22
[   251.081] (EE) [drm] Failed to open DRM device for (null): -22
[   251.082] (EE) [drm] Failed to open DRM device for (null): -22
[   251.082] (EE) [drm] Failed to open DRM device for pci:0000:83:00.0: -22
[   251.082] (EE) [drm] Failed to open DRM device for pci:0000:84:00.0: -22
[   251.082] Number of created screens does not match number of detected devices.
  Configuration failed.

VNC-Screen
wolfgang@WS-Mikro:~$ tail /var/log/Xorg.4.log
[    10.046] xorg-server 2:1.15.1-0ubuntu2.6 (For technical support please see http://www.ubuntu.com/support)
[    10.046] Current version of pixman: 0.30.2
[    10.046]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[    10.046] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    10.046] (==) Log file: "/var/log/Xorg.4.log", Time: Mon Mar  2 10:46:31 2015
[    10.046] (==) Using config file: "/etc/X11/xorg.conf"
[    10.046] (==) Using system config directory "/usr/share/X11/xorg.conf.d"

```

X server is running, also e.g. xclock works on the VNC screen.
```

wolfgang@WS-Mikro:~$ w
 16:02:51 up 30 min,  2 users,  load average: 2,16, 2,35, 1,67
USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
dummy_us tty7     :0               15:32   30:42   8:57   0.09s update-notifier
wolfgang pts/0    10.132.2.119     15:36    5:27   7.77s  0.23s -bash

wolfgang@WS-Mikro:~$ nvidia-smi
Wed Sep 28 16:02:54 2016       
+------------------------------------------------------+
| NVIDIA-SMI 361.42     Driver Version: 361.42         |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX TIT...  Off  | 0000:83:00.0      On |                  N/A |
| 36%   50C    P8    28W / 189W |     95MiB /  6143MiB |      0%      Default |
+-------------------------------+----------------------+----------------------+
|   1  GeForce GTX TIT...  Off  | 0000:84:00.0     Off |                  N/A |
| 33%   47C    P8    33W / 189W |     15MiB /  6143MiB |      0%      Default |
+-------------------------------+----------------------+----------------------+

+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID  Type  Process name                               Usage      |
|=============================================================================|
|    0      2968    G   /usr/lib/xorg/Xorg                              33MiB |
|    0      3262    G   /usr/bin/gnome-shell                            43MiB |
+-----------------------------------------------------------------------------+

```

xorg.conf (which was working on 14.04 LTS):
```

Section "DRI"
    Mode 0666
EndSection

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "BenQ G2200W"
    HorizSync       31.0 - 83.0
    VertRefresh     55.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Dell DEL 1908FPBLK"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX TITAN Z"
    BusID          "PCI:83:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX TITAN Z"
    BusID          "PCI:84:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "nvidiaXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DVI-I-1: nvidia-auto-select +0+0"
    Option         "SLI" "Off"
    Option         "MultiGPU" "On"
    Option         "BaseMosaic" "off"
    Option         "AllowGLXWithComposite" "true"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "metamodes" "DVI-D-0: nvidia-auto-select +0+0"
    Option         "SLI" "Off"
    Option         "MultiGPU" "On"
    Option         "BaseMosaic" "off"
    Option         "AllowGLXWithComposite" "true"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

I hope somebody can give me a hint how to resolve that issue. If some additional info is needed let me know.

regards
wover

---

### Post by wover on 2016-10-07
In the end it came down to a known bug with gdm with virtualgl. switching to loghtdm resolved the issue.

---

