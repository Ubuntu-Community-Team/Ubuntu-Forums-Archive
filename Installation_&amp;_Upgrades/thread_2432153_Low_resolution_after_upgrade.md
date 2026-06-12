---
title: "Low resolution after upgrade"
date: 2019-11-28
forum: Installation &amp; Upgrades
---

### Post by danielsender on 2019-11-28
I have an old Dell M70 (32b) that was happily running 16.04. I upgraded to 18.04 and everything went fine except of a display issue. The max resolution is 1920x1200 but I only get 1280x1024 that is very distorted. The machine has the graphic subsytem Quadro 1400G gfx. Looking around I see that the proper proprietary driver is the Nvidia-304, and this does not appear in the synaptic list nor when I click on the "Additional Drivers" tab of the software updater. I tried getting it from the repository ppa:graphics-drivers/ppa and the driver appears but it is unable to be installed because of unmet dependencies:
```

luka@falu:~$ sudo ubuntu-drivers autoinstall
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 nvidia-304 : Depends: xorg-video-abi-11 but it is not installable or
                       xorg-video-abi-12 but it is not installable or
                       xorg-video-abi-13 but it is not installable or
                       xorg-video-abi-14 but it is not installable or
                       xorg-video-abi-15 but it is not installable or
                       xorg-video-abi-18 but it is not installable or
                       xorg-video-abi-19 but it is not installable or
                       xorg-video-abi-20 but it is not installable or
                       xorg-video-abi-23
              Depends: xserver-xorg-core
E: Unable to correct problems, you have held broken packages.

```

I don't really care about getting the best performance but at least get the max resolution, shouldn't the nouveau driver be able to cover that?

Thanks

---

### Post by danielsender on 2019-11-28
Any ideas?

---

### Post by yaminb on 2019-11-28
I guess where do you source that you should be on nvidia-304?

Have you tried a newer nvidia driver. I'm currently on nvidia-driver-435. It seems to work well. 440 does not work as well for me.
Quadra is listed as supported by the newer driver. Though I can't seem to find your specific 1400G version.

---

### Post by danielsender on 2019-11-29
I got it from [https://packages.debian.org/sid/x11/nvidia-legacy-304xx-driver](https://packages.debian.org/sid/x11/nvidia-legacy-304xx-driver), I tried with the 340 and the machine wouldn't boot falling into a loop - I had to chroot to purge that driver.

---

### Post by yaminb on 2019-11-29
not 340 driver. 435 driver.

---

### Post by danielsender on 2019-11-29
The nvidia-driver-435 does not appear in my Synaptic list, remember that this is a 32b machine - when I list this in another 64b machine I see it.
I assume that the installation disk doesn't use the Nvidia proprietary drivers, but the Nouveau, and booting with this recognizes the proper maximum resolution of the machine. So my question is how to configure the Nouveau driver to properly recognize my display.

---

### Post by yaminb on 2019-11-29
I can't be too much help there. Well beyond my knowledge.

But maybe try the latest x86 Nvidia driver. (384.111)

[https://www.nvidia.com/Download/driverResults.aspx/128736/en-us](https://www.nvidia.com/Download/driverResults.aspx/128736/en-us)

---

### Post by danielsender on 2019-11-29
No problem - I think I want to stick with the Nouveau driver - I think someone around should know the subject.

Thanks anyway

---

### Post by CatKiller on 2019-11-29
> **danielsender said:**
> I don't really care about getting the best performance but at least get the max resolution, shouldn't the nouveau driver be able to cover that?

The nouveau driver just isn't as good at automatically detecting the correct resolution as the proprietary driver is. I don't know if it's to do with requesting the EDID, or parsing it, or what, but the proprietary driver definitely has some special source that nouveau lacks. 

It does seem to be the case that only the legacy 304 branch has support for that device. That branch does appear to have been dropped from the repos for bionic. That branch is in the graphics-drivers PPA for bionic. It seems to just be a package management issue that stopped you from installing it from there.

```
sudo apt install nvidia-graphics-drivers-304
```

might give you more details on where exactly the issue is. 

When you were using the installer, I suspect that it was actually using 1920×1080. For a while now the installer has taken a punt on 1080p rather than what the BIOS set it to if it can't detect the resolution automatically. If you want to manually set the resolution because it's not been automatically detected, a snippet that describes the capabilities of your monitor in /etc/X11/xorg.conf.d, particularly the HorizSync and VertRefresh values, should help. You can generally find those values in the specifications or manual of your monitor.

---

### Post by danielsender on 2019-11-30
As I said, this was an upgrade and not a fresh installation. Enabling the graphic-drivers PPA and doing:
```

luka@falu:~$ sudo apt install nvidia-304
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 nvidia-304 : Depends: xorg-video-abi-11 but it is not installable or
                       xorg-video-abi-12 but it is not installable or
                       xorg-video-abi-13 but it is not installable or
                       xorg-video-abi-14 but it is not installable or
                       xorg-video-abi-15 but it is not installable or
                       xorg-video-abi-18 but it is not installable or
                       xorg-video-abi-19 but it is not installable or
                       xorg-video-abi-20 but it is not installable or
                       xorg-video-abi-23
              Depends: xserver-xorg-core
E: Unable to correct problems, you have held broken packages.
```

I don't have a clue on how to solve this. That's why I thought that I could fix the resolution sticking with the nouveau driver. What you mentioned about /etc/X11/xorg.conf.d is not here. So I don't know where to start from.

---

### Post by CatKiller on 2019-11-30
> **danielsender said:**
> ```
 
E: Unable to correct problems, you have held broken packages.
``` 

And *have* you held broken packages? Your repositories that you've been sitting on since 2016 could be in any state, and we've got no way of knowing because you haven't told us. Or even basic stuff like whether you remembered to run an apt update after you added the PPA to refresh the list of available packages. 

> What you mentioned about /etc/X11/xorg.conf.d is not here. So I don't know where to start from.

No, it's not there by default these days. It will be used if you create one. xorg.conf.d is a directory that can hold snippets so that you don't need to do a full xorg.conf. There's a bunch of information available about it. You only need to give it the information that it would otherwise be getting from the monitor through EDID.

---

### Post by danielsender on 2019-11-30
I always run apt update when I add a PPA or prior to an upgrade. Synaptic says that I don't have any broken packages - only when I attempt to install 304 is when I get these messages. Is it possible that these dependencies cannot be installed in 18.04 but where available in 16.04? Can you give me a pointer to how to generate this folder /xorg.conf.d so the system will get the right resolution?

---

### Post by CatKiller on 2019-11-30
> **danielsender said:**
> I always run apt update when I add a PPA or prior to an upgrade. Synaptic says that I don't have any broken packages - only when I attempt to install 304 is when I get these messages. Is it possible that these dependencies cannot be installed in 18.04 but where available in 16.04?  

It's unlikely that it can't be installed at all in 18.04; the graphics-drivers team is small but generally competent. It is very likely that it's your package manager's particular history and configuration from 16.04 that's stopping you from installing it. 

> Can you give me a pointer to how to generate this folder /xorg.conf.d so the system will get the right resolution?

The folder is just a folder. You'd make it with mkdir and create a file in it. In that file you'd include the correct values for your monitor. You can read more about the file [here](https://ubuntuforums.org/showthread.php?t=2431366&p=13907333#post13907333), for example.

---

### Post by danielsender on 2019-11-30
This is my /etc/X11/xorg.conf.d/20-monitor.conf:
```

Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       30-80
        VertRefresh     49-75
EndSection


Section "Screen"
        Identifier    "Default Screen"
        Monitor        "Configured Monitor"
        Device        "Configured Video Device"
        DefaultDepth    24
        SubSection "Display"
                Depth    24
                Modes     "1920x1200" "1280x1024"
        EndSubSection
EndSection

```

but I can't still get the 1920x1200 resolution, is there anything wrong or incomplete in this file?

---

### Post by CatKiller on 2019-11-30
> **danielsender said:**
> is there anything wrong or incomplete in this file?
Yes. 

You've just copied the values for someone else's completely different monitor rather than looking up your own.

---

### Post by danielsender on 2019-11-30
How do I do that?

---

### Post by CatKiller on 2019-11-30
> **danielsender said:**
> How do I do that?
...
> **CatKiller said:**
> If you want to manually set the resolution because it's not been automatically detected, a snippet that describes the capabilities of your monitor in /etc/X11/xorg.conf.d, particularly the HorizSync and VertRefresh values, should help. You can generally find those values in the specifications or manual of your monitor.

---

### Post by danielsender on 2019-12-01
It turns out that I found an old xorg.conf file (xorg.conf.03312015) that was set up by nvidia settings in 2014 (probably Ubuntu 14.04) and is:
```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 331.20  (buildd@komainu)  Mon Feb  3 15:11:14 UTC 2014




Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
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


    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Seiko/Epson"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection


Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro FX Go1400"
EndSection


Section "Screen"


# Removed Option "metamodes" "nvidia-auto-select @3840x1200 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "nvidiaXineramaInfoOrder" "DFP-0"
    Option         "Stereo" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    Option         "SLI" "Off"
    Option         "MultiGPU" "Off"
    Option         "BaseMosaic" "off"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

so I copied what I thought would be the relevant lines into /etc/X11/xorg.conf.d/20-monitor.conf
```

Section "Monitor"
        Identifier      "Monitor0"
        VendorName      "Unknown"
        ModelName       "Seiko/Epson"
        HorizSync       30.0 - 75.0
        VertRefresh     60
        Option          "DPMS"
EndSection


Section "Screen"
        Identifier      "Screen0"
        Device          "Device0"
        Monitor         "Monitor0"
        DefaultDepth    24
        SubSection "Display"
                Depth    24
                Modes     "1920x1200" "1280x1024"
        EndSubSection
EndSection
```

but I still didn't get it to use the whole resolution.

---

### Post by danielsender on 2019-12-03
I added the following two lines to /etc/default/grub:
```

GRUB_GFXMODE=1920x1200x24
GRUB_GFXPAYLOAD_LINUX=1920x1200
```

but it didn't solve the issue

---

### Post by danielsender on 2019-12-04
I posted the issue on [https://www.linuxquestions.org/questions/ubuntu-63/ubuntu-18-04-does-not-longer-support-the-nvidia-304-driver-4175665365/](https://www.linuxquestions.org/questions/ubuntu-63/ubuntu-18-04-does-not-longer-support-the-nvidia-304-driver-4175665365/) and they solved it. In any case, thanks for your time.

Daniel

---

