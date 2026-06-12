---
title: "Kernel modules: nvidia, nvidia-173, nvidia-current, nouveau, nvidiafb"
date: 2011-05-19
forum: Installation &amp; Upgrades
---

### Post by Dáire Fagan on 2011-05-19
Since upgrading from Ubuntu 10.10 I have had problems with graphics. The problems started after I initially upgraded to Ubuntu 11.04 but then installed xubuntu-desktop over it, but I have had the same problem all my fresh installs of Xubuntu 11.04 too. 

FPS previously averaging about 30 or 35 FPS while playing an OpenGL game with WINE now starts at 20 FPS for 2 or 3 minutes and then slows down to 2-5 FPS.

Unfortunately *Applications Menu >> System >> Additional Drivers* or *jockey* shows:

> The driver is activated but not currently in use.[IMG]http://oi56.tinypic.com/345hh91.jpg[/IMG]

Restart and/or switching to the other driver, and/or back, and/or restarting does nothing.

```
dusf@banshee:~$ lspci -k
...
01:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 LE] (rev a1) 
   Subsystem: Dell Device 0405 
   Kernel driver in use: nvidia 
   Kernel modules: nvidia-current, nvidia-173, nouveau, nvidiafb
```Although now Kernel modules also includes 'nvidia' after my attempts to fix the problem which I shall get on to.

I was advised on the WINE HQ forums:

> You are using both the proprietary and FOSS drivers.  Remove the FOSS  
drivers (nouveau) and use only the nVidia supplied drivers. I used *synaptic to uninstall xserver-xorg-video-nouveau as there is no package which is just 'nouveau'.

Edited a line in */etc/default/grub* to:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset rdblacklist=nouveau"
```Then:

```
sudo update-grub
```On rebooting none of these measures made any difference to FPS performance, or the kernel modules listed in lspci -k.

Further following advice from the WINE HQ forums I executed:

```
sudo modprobe -r nouveau
```but the above also made no difference to FPS performance, or the kernel modules listed in lspci -k.

I tried another fresh install of Xubuntu 11.04, formatting /home and /boot partition (if relevant), and as advised from #Xubuntu on freenode I installed all updates before going near *jockey* or *Applications Menu >> System >> Additional Drivers* but nothing had changed from there or the output of lspci -k.

On further advice last night from #Xubuntu I *executed:

```
sudo apt-get --purge remove xserver-xorg-video-nouveau
```And then added the following lines to the bottom of */etc/modprobe.d/blacklist.conf*:

```
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
```I saved the file, and then rebooted into recovery mode to bring up a tty without x running where I had to chmod +x NVIDIA-Linux-x86-270.41.06.run  before installing which warned me there was a problem with the preconfigured distribution script but installed anyway.

On logging in *lspci -k* now outputs

```
01:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 LE] (rev a1)
    Subsystem: Dell Device 0405
    Kernel driver in use: nvidia
Kernel modules: nvidia, nvidia-173, nvidia-current, nouveau, nvidiafb
```...which includes the additional *nvidia* module but *jockey *still is the same and I just confirmed my FPS will still start at 20 FPS and drop to 2-5 FPS shortly after starting an OpenGL game with WINE.

[I]dusf@banshee:~$ jockey-text -l
xorg:nvidia_173 - NVIDIA accelerated graphics driver (Proprietary, Disabled, Not in use)
xorg:nvidia_current - NVIDIA accelerated graphics driver (Proprietary, Enabled, Not in use)[/I]

*etc/X11/xorg.conf*:

```
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
```My post is [#21]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/726496/comments/21") on [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/726496](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/726496) although I'm not sure it's the exact same bug, as I seem to have two of the different problems mentioned, and then some.

Where do I go from here? I want to keep trying to fix this problem, but I will downgrade to Xubuntu 10.10 if absolutely necessary.

Tried:

```
dusf@banshee:~$ echo options nouveau modeset=0 | sudo tee -a /etc/modprobe.d/nouveau-kms.conf
[sudo] password for dusf: 
options nouveau modeset=0
dusf@banshee:~$ sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-2.6.38-8-generic
cryptsetup: WARNING: failed to detect canonical device of /dev/sda9
cryptsetup: WARNING: could not determine root device from /etc/fstab
```

But unfortunately after a reboot lspci -k still outputs:

```

Kernel driver in use: nvidia
Kernel modules: nvidia, nvidia-173, nvidia-current, nouveau, nvidiafb
```

---

### Post by MAFoElffen on 2011-05-19
> **dusf said:**
> Tried:

```
dusf@banshee:~$ echo options nouveau modeset=0 | sudo tee -a /etc/modprobe.d/nouveau-kms.conf
[sudo] password for dusf: 
options nouveau modeset=0
dusf@banshee:~$ sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-2.6.38-8-generic
cryptsetup: WARNING: failed to detect canonical device of /dev/sda9
cryptsetup: WARNING: could not determine root device from /etc/fstab
```But unfortunately after a reboot lspci -k still outputs:

```

Kernel driver in use: nvidia
Kernel modules: nvidia, nvidia-173, nvidia-current, nouveau, nvidiafb
```
Something going on there... Mine doing fine using bridged SLI,  but shows this:
```

mafoelffen@maf-ubuntu-01:~$ lspci -k | grep nvidia
    Kernel driver in use: nvidia
    Kernel modules: nvidia-current, nouveau, nvidiafb

```Your is showing multiple concurrent modules in use? (nvidia, nvidia-173 and nvidia current).

Here's my blacklist:
```

mafoelffen@maf-ubuntu-01:~$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

# XPad conflicts with XBoxDrv
blacklist xpad

``````

mafoelffen@maf-ubuntu-01:~$ cat /etc/X11/xorg.conf
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 260.19.06  (buildd@yellow)  Mon Oct  4 15:59:51 UTC 2010


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#    InputDevice    "Keyboard0" "CoreKeyboard"
# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#Section "InputDevice"
#
#    # generated from default
#    Identifier     "Mouse0"
#    Driver         "mouse"
#    Option         "Protocol" "auto"
#    Option         "Device" "/dev/psaux"
#    Option         "Emulate3Buttons" "no"
#    Option         "ZAxisMapping" "4 5"
#EndSection

# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#Section "InputDevice"
#
#    # generated from default
#    Identifier     "Keyboard0"
#    Driver         "kbd"
#EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "HSP LM02"
    HorizSync       30.0 - 83.0
    VertRefresh     55.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6800 Ultra"
    BusID          "PCI:3:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6800 Ultra"
    BusID          "PCI:3:0:0"
    Screen          1
EndSection

Section "Screen"

# Removed Option "metamodes" "nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "TV: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```
Not having problems with that driver and blacklist... But it is 64bit kernel <> You didn't say what version your kernel was.

---

### Post by Dáire Fagan on 2011-05-19
> **MAFoElffen said:**
> Not having problems with that driver and blacklist... But it is 64bit kernel <> You didn't say what version your kernel was.

dusf@banshee:~$ cat /proc/version
Linux version 2.6.38-8-generic (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011

I'm x86.

I've since executed the following and rebooted:

```
dusf@banshee:~$ echo options nouveau modeset=0 | sudo tee -a /etc/modprobe.d/nouveau-kms.conf
[sudo] password for dusf: 
options nouveau modeset=0
dusf@banshee:~$ sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-2.6.38-8-generic
cryptsetup: WARNING: failed to detect canonical device of /dev/sda9
cryptsetup: WARNING: could not determine root device from /etc/fstab
```I don't think the warnings are of consequence, and only relate to the fact my /home partition was encrypted on installing Xubuntu 11.04.

There is no change in jockey/Additional Drivers, or in the output from lspci -k, but lsmod does not show nouveau and does show nvidia, I only wish I had checked the output of lsmod before rebooting.

I'm in an online queue now to see if it has made any difference to the OpenGL game running with WINE.

Unfortunately after 90 seconds playing it went from 15fps to 3fps and hovered around there.

---

### Post by theSpaceAmoeba on 2011-05-20
I want to confirm this problem. I am running Ubuntu 11.04 64-bit on a Nvidia 8600GT. When I play the game Nexuiz I get a framerate of around 60 fps for several minutes (usually about 10 or so) and then it drops to around 10. Sometimes (but not always) I can get a good fps again (for a few minutes) by changing an effects setting and forcing Nexuiz to reload the game. 

Jockey shows the same strange configuration for me: Nvidia active but "not in use".

lspci gives:

```
Kernel driver in use: nvidia
Kernel modules: nvidia-current, nouveau, nvidiafb
```

When I had Ubuntu 10.10, Nexuiz had problems with the original kernel (different, worse problems) but I upgraded to the 2.6.36 kernel, which fixed it and gave me a consistent 60 fps.

Important to note: the bug report that dusf linked to does not seem to apply to at least my problem because even when I use Ubuntu Classic with no effects I still have the same issue.

I'd really like to figure out how to fix this.

---

### Post by MAFoElffen on 2011-05-23
> **theSpaceAmoeba said:**
> I want to confirm this problem. I am running Ubuntu 11.04 64-bit on a Nvidia 8600GT. When I play the game Nexuiz I get a framerate of around 60 fps for several minutes (usually about 10 or so) and then it drops to around 10. Sometimes (but not always) I can get a good fps again (for a few minutes) by changing an effects setting and forcing Nexuiz to reload the game. 

Jockey shows the same strange configuration for me: Nvidia active but "not in use".

lspci gives:

```
Kernel driver in use: nvidia
Kernel modules: nvidia-current, nouveau, nvidiafb
```When I had Ubuntu 10.10, Nexuiz had problems with the original kernel (different, worse problems) but I upgraded to the 2.6.36 kernel, which fixed it and gave me a consistent 60 fps.

Important to note: the bug report that dusf linked to does not seem to apply to at least my problem because even when I use Ubuntu Classic with no effects I still have the same issue.

I'd really like to figure out how to fix this.
I hadn't seen anything on this in a while and I thought I'd update you... Like I hinted, before > I thought your problem was "the multiples" of nvidia drivers you had installed.  Since then, this has come to light as other peep's problems.  I've in the process of writing the instructions for someone else... and I'll pop back here and add the link to that in this post.  The message you see in jockey, is a current jockey bug (installed but not active)

---

### Post by Dáire Fagan on 2011-05-23
> **MAFoElffen said:**
> I hadn't seen anything on this in a while and I thought I'd update you... Like I hinted, before > I thought your problem was "the multiples" of nvidia drivers you had installed.  Since then, this has come to light as other peep's problems.  I've in the process of writing the instructions for someone else... and I'll pop back here and add the link to that in this post.  The message you see in jockey, is a current jockey bug (installed but not active)

Is your fix for what jockey tells us about the drivers, or the drivers themselves, will it make sure we're using the correct driver?

---

### Post by MAFoElffen on 2011-05-23
> **dusf said:**
> Is your fix for what jockey tells us about the drivers, or the drivers themselves, will it make sure we're using the correct driver?
About the drivers themselves.  There seems to be a bug with jockey that is telling them that the driver is installed but not active... When it actually may or may not be.  That doesn'r really seem to help us and causes more problems with people trying to fix "that."

I tried to expand and explain what each is doing and some of the "why's..." in that post.  It combines some of the current fixes, patches and workarounds for nvidia problems.

Look at the instructions in this post and see if they help you:
[http://ubuntuforums.org/showpost.php?p=10853222&postcount=186](http://ubuntuforums.org/showpost.php?p=10853222&postcount=186)

---

### Post by theSpaceAmoeba on 2011-05-24
Thanks for the input, MAFoElffen. I tried the steps suggested in your post, but unfortunately it did not fix my problem. Specifically, I re-installed the kernel headers, uninstalled/purged nvidia drivers, re-installed nvidia drivers (but used nvidia-current because from my reading it should work), ran nvidia-xconfig, and rebooted. No change.

---

### Post by murthy on 2011-05-24
I am also facing the same problem with frequent hangs.  Nvidia 6100 AMD athlon 64 bit.  "This driver is activated but not currently in use".  Is there no solution?

---

### Post by theSpaceAmoeba on 2011-05-26
I think I figured out what my framerate problem is. I found out that the fan on my card is no longer working so its temperature gets way too high and the card throttles after getting above 100C. Interestingly, this did not happen before Ubuntu 11.04 so either the fan broke at the same time as I upgraded or 11.04 is more power hungry with video which exacerbated the problem. Reports (see Phoronix) show that 11.04 (and recent Linux kernels) are more power hungry in general.

I will be able to confirm this when I receive my new Nvidia GT 240 tomorrow. I will post after I test it out.

---

### Post by theSpaceAmoeba on 2011-05-30
The new video card with working fan seems to have fixed my framerate problem.

---

### Post by airspoon on 2011-05-31
I seem to have the same issue, at least with my nvidia driver in 11.04. "Additional Drivers" states that nvidia (173) is activated but not currently in use.

"This driver is activated but not currently in use"

Booting into Gnome Classic is fine, at least for me, but not being able to have any 3d effects (especially with things like AWN), is becoming a pain.

From my extremely limited understanding, is that it isn't a problem with the driver, so much as it is with how Ubuntu acknowledges or uses the driver. Is this correct? 

Thanks, 

--airspoon

---

