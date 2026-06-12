---
title: "[Ubuntu 18.04] Screen tearing on notebook, only built-in monitor, external is fine"
date: 2018-04-27
forum: Installation &amp; Upgrades
---

### Post by nooneelse on 2018-04-27
Hi guys,

I have this Dell Inspiron 7567 with the bellow config:

```

bruno@funnie:~$ inxi -Fxz
System:    Host: funnie Kernel: 4.15.0-20-generic x86_64 bits: 64 gcc: 7.3.0
           Desktop: Gnome 3.28.1 (Gtk 3.22.30-1ubuntu1) Distro: Ubuntu 18.04 LTS
Machine:   Device: laptop System: Dell product: Inspiron 15 7000 Gaming serial: N/A
           Mobo: Dell model: 0P84C9 v: A01 serial: N/A UEFI: Dell v: 1.6.0 date: 03/27/2018
Battery    BAT0: charge: 65.9 Wh 96.7% condition: 68.2/74.0 Wh (92%) model: SMP DELL 71JF452 status: Charging
CPU:       Quad core Intel Core i7-7700HQ (-MT-MCP-) arch: Skylake rev.9 cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 22464
           clock speeds: max: 3800 MHz 1: 900 MHz 2: 900 MHz 3: 900 MHz 4: 900 MHz 5: 900 MHz 6: 900 MHz
           7: 900 MHz 8: 900 MHz
Graphics:  Card-1: Intel Device 591b bus-ID: 00:02.0
           Card-2: NVIDIA GP107M [GeForce GTX 1050 Ti Mobile] bus-ID: 01:00.0
           Display Server: x11 (X.Org 1.19.6 ) drivers: modesetting,nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1920x1080@60.00hz, 1920x1080@60.02hz
           OpenGL: renderer: GeForce GTX 1050 Ti/PCIe/SSE2 version: 4.6.0 NVIDIA 390.48 Direct Render: Yes
Audio:     Card-1 Intel CM238 HD Audio Controller driver: snd_hda_intel bus-ID: 00:1f.3
           Card-2 NVIDIA GP107GL High Definition Audio Controller driver: snd_hda_intel bus-ID: 01:00.1
           Sound: Advanced Linux Sound Architecture v: k4.15.0-20-generic
Network:   Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: d000 bus-ID: 02:00.0
           IF: enp2s0 state: up speed: 1000 Mbps duplex: full mac: <filter>
           Card-2: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter driver: ath10k_pci bus-ID: 03:00.0
           IF: wlp3s0 state: down mac: <filter>
           Card-3: Atheros usb-ID: 001-004
           IF: null-if-id state: N/A speed: N/A duplex: N/A mac: N/A
Drives:    HDD Total Size: 1256.3GB (0.6% used)
           ID-1: /dev/nvme0n1 model: WDC_WDS256G1X0C size: 256.1GB
           ID-2: /dev/sda model: TOSHIBA_MQ02ABD1 size: 1000.2GB temp: 37C
Partition: ID-1: / size: 87G used: 7.0G (9%) fs: ext4 dev: /dev/nvme0n1p6
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 60.0C mobo: N/A gpu: 1.0:55C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 308 Uptime: 8 min Memory: 2012.8/7842.1MB Init: systemd runlevel: 5 Gcc sys: 7.3.0
           Client: Shell (bash 4.4.191) inxi: 2.3.56 

```

And I am using this NVIDIA driver:

```

bruno@funnie:~$ nvidia-smi 
Fri Apr 27 21:05:48 2018       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 390.48                 Driver Version: 390.48                    |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX 105...  Off  | 00000000:01:00.0  On |                  N/A |
| N/A   53C    P3    N/A /  N/A |    468MiB /  4040MiB |      2%      Default |
+-------------------------------+----------------------+----------------------+
```

And at least but not last I have 1 monitor connected to the hdmi port:

```
bruno@funnie:~$ xrandr --listactivemonitors 
Monitors: 2
 0: +*HDMI-0 1920/480x1080/270+1920+0  HDMI-0
 1: +eDP-1-1 1920/344x1080/194+0+0  eDP-1-1
```

So, the issue is, it's not tearing that much (just a lil bit) in the HDMI external monitor (HDMI-0). But it's tearing a lot in the built-in monitor (eDP-1-1).

If I do use this:

```

bruno@funnie:~$ cat /etc/modprobe.d/zz-nvidia-modeset.conf
options nvidia_drm modeset=1
bruno@funnie:~$ sudo update-initramfs -u

```

The built-in monitor (eDP-1-1) stop from tearing, BUT, the external monitor/hdmi port (HDMI-0) completely stop from functioning :(

What could I possible do to stop the built-in monitor from tearing ?

Here a link showing the tearing only in the built-in monitor: [https://www.youtube.com/watch?v=fL1r5dBKXao](https://www.youtube.com/watch?v=fL1r5dBKXao)

---

### Post by mc4man on 2018-04-27
No real idea (don't have ext. monitor) though I'd probably install lightdm, switch to it from gdm3 & see if it allows both..

---

### Post by nooneelse on 2018-04-28
Tried using the LightDM but doesn't worked

---

### Post by mc4man on 2018-04-28
Could be it's not possible to get sync on both with optimus (or some optimus.
What i've always noticed in xrandr --verbose is that prime sync is always enabled for hdmi with no nvidia_drm modeset being set (i.e  disabled
Probably best bet would be to start a thread here & see if any info is forthcoming
[https://devtalk.nvidia.com/default/board/98/linux/](https://devtalk.nvidia.com/default/board/98/linux/)

---

### Post by nooneelse on 2018-04-28
> **mc4man said:**
> Could be it's not possible to get sync on both with optimus (or some optimus.
What i've always noticed in xrandr --verbose is that prime sync is always enabled for hdmi with no nvidia_drm modeset being set (i.e  disabled
Probably best bet would be to start a thread here & see if any info is forthcoming
[https://devtalk.nvidia.com/default/board/98/linux/](https://devtalk.nvidia.com/default/board/98/linux/)

Hey, I got it, now everything is working without tearing.

I have used this EXACT config that this guy suggested: [https://devtalk.nvidia.com/default/topic/957814/linux/prime-and-prime-synchronization/post/5237042/#5237042](https://devtalk.nvidia.com/default/topic/957814/linux/prime-and-prime-synchronization/post/5237042/#5237042)

Even my driver being the 390.48 it worked perfectly, now hdmi and built-in monitor are working fine, even the disconnecting and connecting procedures are seamless.

Thanks for the tip man!

Just a quick tip, for those installing Ubuntu 18.04 in a laptop I suggest doing this procedure:

- Install Ubuntu 18.04
- Install 3rd drivers (sudo apt-get update; sudo ubuntu-drivers autoinstall)
- And use the config from the link above/below (I've posted the config in here too)
- Install LightDM (sudo apt-get install lightdm)
- - And no, I couldn't get it working with GDM :( actually the external monitor simple doesn't detect at all.
- - And on the built-in monitor the login texts/strings like the username for example are bugged/missing if the hdmi cable is connected... BIZARRE! ([https://imgur.com/a/MSn26rj](https://imgur.com/a/MSn26rj))
- - But again, install LightDM and everything will work fine


> 

Step 1: Edit/Create the /etc/X11/xorg.conf file and put the content below

```
Section "ServerLayout"
Identifier "layout"
Screen 0 "nvidia"
Inactive "intel"
EndSection

Section "Device"
Identifier "nvidia"
Driver "nvidia"
BusID "PCI:1:0:0"
EndSection

Section "Screen"
Identifier "nvidia"
Device "nvidia"
Option "AllowEmptyInitialConfiguration"
EndSection

Section "Device"
Identifier "intel"
Driver "modesetting"
BusID "PCI:0:2:0"
Option "AccelMethod" "none"
EndSection

Section "Screen"
Identifier "intel"
Device "intel"
EndSection
```


Some versions of the &#8220;modesetting&#8221; driver try to load a sub-module called &#8220;glamor&#8221;, which conflicts with the NVIDIA GLX implementation. Please ensure that the libglamoregl.so X module is not installed.
As my xorg server package includes the glamor driver, I added the option "AccelMethod" "none" for the Intel driver.

Step 2: Add the xrandr lines to GDM config

For the GDM display manager create two new .desktop files, but if you have LightDM you just need to create the second line file

/usr/share/gdm/greeter/autostart/optimus.desktop
/etc/xdg/autostart/optimus.desktop

```

[Desktop Entry]
Type=Application
Name=Optimus
Exec=sh -c "xrandr --setprovideroutputsource modesetting NVIDIA-0; xrandr --auto"
NoDisplay=true
X-GNOME-Autostart-Phase=DisplayServer
```


Step 3: Add in the menu grub (/etc/default/grub) the option : nvidia-drm.modeset=1


```
GRUB_CMDLINE_LINUX_DEFAULT="quiet nvidia-drm.modeset=1 acpi_osi="
```

Step 4: Update the grub
```
sudo update-grub2
```

Then Reboot



---

### Post by cariboo on 2018-04-28
This looks more like a technical question, moved to Installation & Upgrades.

---

