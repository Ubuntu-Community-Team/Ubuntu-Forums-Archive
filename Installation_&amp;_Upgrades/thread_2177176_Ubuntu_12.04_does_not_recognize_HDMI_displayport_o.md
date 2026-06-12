---
title: "Ubuntu 12.04 does not recognize HDMI displayport outputs in Dell Precision M4700"
date: 2013-09-27
forum: Installation &amp; Upgrades
---

### Post by roberto6 on 2013-09-27
Hi, I've just bought a TV/monitor and when is connected to my laptop by DP output nothing happens. It only shows a log saying "There is  no signal coming from your computer". The same for the HDMI output.
Looking in the web I've seen this is a common problem but rather complicate to solve. I wish somebody could guide me along such a process.

I attach the following logs:


 rbaena@fajnmp2:~$ uname -a
Linux fajnmp2 3.2.0-38-generic #61-Ubuntu SMP Tue Feb 19 12:18:21 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


 rbaena@fajnmp2:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:        12.04
Codename:       precise


 rbaena@fajnmp2:~$ xrandr
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
LVDS1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1920x1080      60.0*+   59.9     40.0
   1680x1050      60.0     59.9
   1600x1024      60.2
   1400x1050      60.0
   1280x1024      60.0
   1440x900       59.9
   1280x960       60.0
   1360x768       59.8     60.0
   1152x864       60.0
   1024x768       60.0
   800x600        60.3     56.2
   640x480        59.9
VGA1 disconnected (normal left inverted right x axis y axis)


 rbaena@fajnmp2:~$ sudo lshw -C display
  *-display UNCLAIMED
       description: VGA compatible controller
       product: GK107GLM [Quadro K1000M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller cap_list
       configuration: latency=0
       resources: memory:f5000000-f5ffffff memory:e0000000-efffffff  memory:f0000000-f1ffffff ioport:e000(size=128) memory:f6000000-f607ffff
  *-display
       description: VGA compatible controller
       product: 3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:46 memory:f6400000-f67fffff memory:d0000000-dfffffff ioport:f000(size=64)

---

### Post by roberto6 on 2013-09-28
Somebody in other forum suggested the problem can be solved disabling the Optimus mode in the bios, since in that way the nvidia card can manage the HDMI port. Since this is pretty crytical (touching the bios), I would appreciate some comments/suggestions about this issue.

---

### Post by Linuxisfast on 2013-09-28
Install latest Ubuntu 12.04.3 which will install latest 319 drivers, this makes the HDMI work.

---

### Post by roberto6 on 2013-09-29
Hi. My distro is ubuntu 12.04.3 (Description:    Ubuntu 12.04.3 LTS). Is this not the same you mention?

rbaena@fajnmp2:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:        12.04
Codename:       precise

---

### Post by Linuxisfast on 2013-09-29
> **roberto6 said:**
> Hi. My distro is ubuntu 12.04.3 (Description:    Ubuntu 12.04.3 LTS). Is this not the same you mention?

rbaena@fajnmp2:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:        12.04
Codename:       precise

Yes that means nvidia is on for your machine. Are you sure you haven't switched the card off in BIOS.

---

### Post by roberto6 on 2013-09-29
I have checked the BIOS and the only option I can see related with the video cards is about enabling/disabling the Optimus mode (now is on, i.e., enabled). Somebody told me to disable it BUT: "I tried to do the same thing on my laptop and I messed it up really  bad.Because NVidia graphics card have their own XSERVER when you boot  using only the NVidia graphics card it might change the XSERVER settings  and when you you wish to run again on Optimus mode under Ubuntu it  might be impossible.This is what happened to me and I had to reinstall  Ubuntu,because It didn't know how to fix it."

I did not see in my BIOS any option which let me to choose between nVidia card or Intel one.

---

### Post by Linuxisfast on 2013-09-30
With 12.04.3, Nvidia driver runs all the time and the intel card is not used for rendering but a dummy sink. You can't use Bumblebee with this solution as the new nvidia driver in the repository is hardwired for nvidia-prime and Bumblebee doesn't work with that.

---

### Post by roberto6 on 2013-09-30
So, I am getting lost. What is the solution?

 - a new driver?
 - disabling the Optimus Mode in the BIOS?
 - Updating to a new ubuntu version, i.e., 13.04?

---

### Post by gordintoronto on 2013-09-30
Look in the manual to see if there is a key combination for external displays. On some laptops, there is a key which cycles through three presses: only the internal display, only the external display, both.

Have you installed an "Additional Driver"? I don't know where this is found in Kubuntu 12.04, in Ubuntu 12.04 it's a program. If you have "nvidia-current" installed, you can run Nvidia X Server Settings, which should at least shed some light on the situation -- and maybe let you turn on the external display.

---

### Post by roberto6 on 2013-10-01
Hi, thanks for your answer. 

 a) I do not know if I have such a key. I have downloaded the manual and will have a look into it. In the meantime...
 b) I have 'additional driver'. This says I am using privative drivers and it shows the following driver --> Broadcom STA but I think it is more related with the wifi: This package contains Broadcom 802.11 Linux STA wireless driver for use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-, BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-based hardware.
 c) and yes, I have installed the nvidia x server setting but when I started it pops up the following message: "you do not appear to be using the nvidia x driver. Please edit your X configuration file (just run nvidia-xconfig as root), and restart the x server.

 Once I do what it says I have the following:

WARNING: Unable to locate/open X configuration file.

New X configuration file written to '/etc/X11/xorg.conf'

I the xorg.conf file I have:

cat /etc/X11/xorg.conf
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 304.88  (buildmeister@swio-display-x86-rhel47-06)  Wed Mar 27 15:32:58 PDT 2013

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
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
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


I rebooted the laptop and had a terrible resolution of 640x480 with no possibility to improve it up. Furthermore, no detection of hdmi and dp anyway, at least from 'systema preferences --> monitors'.
 Then I have done 'mv xorg.conf xorg.conf.bak' and came back to the original situation, i.e., resolution of 1920x1080.

P.S.: I have checked the manual and did not see any combination of keys to choose between external displays.

---

### Post by roberto6 on 2013-10-02
I can connect the laptop with the monitor using the VGA output and a VGA-HDMI converter. Unfortunately, the resolution (1024x768) is much lower than the maximum allowed for the monitor (2560x1440) so I still would like to fix the issue related with hdmi and displayport outputs.

rbaena@fajnmp2:~/kk$ xrandr
Screen 0: minimum 320 x 200, current 2944 x 1080, maximum 8192 x 8192
LVDS1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 1
   1920x1080      60.0*+   59.9     40.0  
   1680x1050      60.0     59.9  
   1600x1024      60.2  
   1400x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9                                                            
VGA1 connected 1024x768+1920+0 (normal left inverted right x axis y axis) 0mm x 0m
   1024x768       60.0*                                                           
   800x600        60.3     56.2                                                   
   848x480        60.0                                                            
   640x480        59.9

---

### Post by gordintoronto on 2013-10-02
You need to install nvidia-current.

Unless your video card, cable and display are the very latest technology, HDMI is limited to 1920 by 1080.

---

### Post by roberto6 on 2013-10-03
I already have nvidia-current installed

BTW, the only option I get from Nvidia X server settings is "nvidia-settings configuration". Nothing else.

The display is [FONT=Geneva][SIZE=2]a Dell UltraSharp U2713H 27" IPS LED, it can reach a maximum resolution of [/SIZE][/FONT](2560x1440), at least with displayport[FONT=Geneva][SIZE=2], my laptop a Dell precision M4700, and the video cards:

[/SIZE][/FONT]lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK107GLM [Quadro K1000M] [10de:0ffc] (rev a1)[FONT=Geneva][SIZE=2]
[/SIZE][/FONT]

---

### Post by gordintoronto on 2013-10-03
Note that the M470 is actually a sizable family of computers, with many configuration options.

It's also "the latest and greatest." In my experience, the chance of problems goes right down if you choose the latest and greatest OS. Ubuntu 13.10 is two weeks away, and "the final beta" is available. If I were you, I would try that.

---

### Post by ziemowitzima on 2014-05-16
Dear UBUNTU Users,
I have similar problem.
Ubuuntu 12.04.4,
nvidia-current inttlaed,
bud HDMI port does not work...

TV says that there is no signal.

I have Dell Latitude Laptop

Did u find solution for this problem ?

thanks
Z

---

