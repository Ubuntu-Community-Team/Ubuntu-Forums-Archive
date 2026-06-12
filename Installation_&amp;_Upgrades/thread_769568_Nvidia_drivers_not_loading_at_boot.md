---
title: "Nvidia drivers not loading at boot"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by teoryn on 2008-04-26
I've just upgraded 7.10->8.04 and I had some trouble getting the nvidia drivers working with my 8800GT. After following the directions on a post here I was able to purge all the nvidia stuff I had on my computer and install the drivers fresh, which got everything working with I restarted X, but then when I restarted the computer it stopped and I've gotten stuck.

After turning my computer on it goes to the low graphics mode gdm login screen and I do:
```

[Ctrl-Alt-F2]
sudo /etc/init.d/gdm stop
sudo apt-get install --reinstall linux-restricted-modules.2.6.24-16-generic
sudo modprobe nvidia
sudo /etc/init.d/gdm start
```

And then I get the Nvidia splash screen and everything works until I restart the the system, at which point the nvidia module isn't found and the low graphics mode comes up again.

If I don't execute the apt-get command above I get the following error from modprobe:
```
FATAL: Could not open '/lib/modules/2.6.24-16-generic/volatile/nvidia.ko': No such file or directory.
```

If I don't execute the modprobe line I just end up in low graphics mode again.

I do have nvidia listed in in /etc/modules

So, any ideas why the nvidia kernel isn't being found at boot?

Thanks in advance,
-Kevin

---

### Post by jgriffinpark on 2008-04-26
Same problem. I really need help, I'm going insane :( From what I can tell, my menu.lst file is still loading the Gutsy kernel. I dont know how to properly fix this, though. I hate this release, never should have upgraded, and never will recommend to anyone, ever.

---

### Post by teoryn on 2008-04-26
My menu.lst has the 2.6.24-16-generic kernel as it's boot option and is being properly loaded, it's just the nvidia module I'm having trouble with.

I believe there was an option while upgrading to keep/replace menu.lst, and if you kept the old one that would explain the old kernel being loaded.

---

### Post by teoryn on 2008-04-27
I've followed the directions in other threads, including re-purging all the nvidia stuff and reinstalling, but I'm still getting the same problem. I've included my xorg.conf and 'lshw -C video' if that helps.

```
Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "Monitor"
    Identifier     "Samsung SyncMaster 226BW"
    HorizSync       30.0 - 81.0
    VertRefresh     50.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA GeForce 8800GT"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GT"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA GeForce 8800GT"
    Monitor        "Samsung SyncMaster 226BW"
    DefaultDepth    24
    SubSection     "Display"
        Modes      "1680x1050"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1680x1050_60 +0+0"
    Option         "AllowGLXWithComposite" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

```

```
  *-display               
       description: VGA compatible controller
       product: GeForce 8800 GT
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia

```

Thanks again for any help.

---

### Post by PhilB on 2008-04-27
Have had more than a few problems myself. 
Late yesterday came across a thread where some people with nvidia driver/screen problems had discovered that they were still booting the Ubuntu 7.10 kernel, and not the 8.04. Definitely the case with me, but have not had the time to sort it out-hope to do it tomorrow.
Seems the menu 1st file had not been changed during the update, and will need to be edited with the new data 

Hope this page helps
[http://ubuntuforums.org/showthread.php?t=766515&highlight=kernel&page=3](http://ubuntuforums.org/showthread.php?t=766515&highlight=kernel&page=3)

---

### Post by bioShark on 2008-04-27
> **teoryn said:**
> I've just upgraded 7.10->8.04 and I had some trouble getting the nvidia drivers working with my 8800GT. After following the directions on a post here I was able to purge all the nvidia stuff I had on my computer and install the drivers fresh, which got everything working with I restarted X, but then when I restarted the computer it stopped and I've gotten stuck.

After turning my computer on it goes to the low graphics mode gdm login screen and I do:
```

[Ctrl-Alt-F2]
sudo /etc/init.d/gdm stop
sudo apt-get install --reinstall linux-restricted-modules.2.6.24-16-generic
sudo modprobe nvidia
sudo /etc/init.d/gdm start
```

And then I get the Nvidia splash screen and everything works until I restart the the system, at which point the nvidia module isn't found and the low graphics mode comes up again.

If I don't execute the apt-get command above I get the following error from modprobe:
```
FATAL: Could not open '/lib/modules/2.6.24-16-generic/volatile/nvidia.ko': No such file or directory.
```

If I don't execute the modprobe line I just end up in low graphics mode again.

I do have nvidia listed in in /etc/modules

So, any ideas why the nvidia kernel isn't being found at boot?

Thanks in advance,
-Kevin

Hi

I have had some similar problem in 7.10. I also needed to re-install the nvidia drivers every time I rebooted the PC. Here is what I have done:

```
sudo apt-get update
```
and then

```
sudo apt-get upgrade
```


I hope it helps.

Now with the upgrade from 7.10 to 8.04 I have also problems with the KDE4 and Nvidia driver not getting along, but thats another story.

---

