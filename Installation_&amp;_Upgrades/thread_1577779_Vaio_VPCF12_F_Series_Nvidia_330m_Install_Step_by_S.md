---
title: "Vaio VPCF12 F Series Nvidia 330m Install Step by Step"
date: 2010-09-19
forum: Installation &amp; Upgrades
---

### Post by mxgold on 2010-09-19
I have spent days trying to get the nvidia 330m on my new sony vaio VPC122FX to work and finally I have a process that works. Most of this was collected around the internet from different posts so I only take credit for trial and error. 
I have done this using Ubuntu 10.04, 32 and 64 bit versions. 

The main issues with the VPCF12 is the touchpad does not work, there's no sound from the speakers unless you plugin the headphone jack and the big one was the NVIDIA drivers do not install correctly even when using the "Hardware Drivers" administration app. The problem is the nouveau drivers that need to be disabled properly before install but it seems that the order in which you install and configure the xorg.conf file needs to be correct as well. So here is what I did step by step.

Also, I tried using Nouveau for a while but you get screen lockups every now and then for no reason. The fan just kicks up faster and the screen freezes, then you have to hard restart and lose all of your PHP code you forgot to save.   ](*,)

***** Install ubuntu 10.04 64bit ********
note: this also worked on the 32bit as well[INDENT]10GB swap
15GB     /
400GB     /home
[/INDENT]version: kernel linux 2.6.32-24-generic [GNOME 2.30.2]
On boot the resolution should be a 1600x900 due to the nouveau driver.

1. start installing all updates:  System -> administration -> update manager

While updates are happening, enable the touchpad mouse and disable the nouveau driver for the next bootup sequence.

2. Open terminal
3. sudo gedit /etc/default/grub
4. Change to:[INDENT]           GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nouveau.modeset=0"
           GRUB_CMDLINE_LINUX="i8042.nopnp"
[/INDENT]NOTE: 2 different lines, too many times I tried adding everything to the bottom one.. does not work.

5. sudo update-grub
6. After the Ubuntu updates are finished, Reboot.

7. At grub menu hit e to edit config and make sure nouveau is disabled.
    The line looks like: "i8042.nopnp quiet splash nouveau.modeset=0"

 8. Do not change anything, Hit ESC and boot as normal
Display should be the default grub 800x600, this means the nouveau driver is not working. YEAH!

9. Run System -> Administration -> Hardware Drivers
10. Choose "Activate"

After completion open a terminal window to create the config, 
NOTE: DO NOT REBOOT YET!

11. sudo nvidia-config 
12. sudo gedit /etc/X11/xorg.conf
13. Change:[INDENT]    Section "Device"
            Identifier     "Device0"
            Driver         "nvidia"
        VendorName     "NVIDIA Corporation"
[B]            Option        "ConnectedMonitor" "DFP-0"
            Option        "CustomEDID" "DFP-0: /proc/acpi/video/NGFX/LCD/EDID"[/B]
[/INDENT]14. Reboot again, you will see a green screen then the nvidia logo (real quick).

Login and go to:  Administation -> NVIDIA X Server Settings
nvidia version 195.36.24 is installed (terminal does this kool opacity thingy too)
Touchpad should also be working as well.

Now, lets enable the onboard speakers.. [sound only works through the headphone jack]

15. Open Synaptic:  System -> Administration -> Synaptic Package Manager
16. Search for:  Backports
17. Choose:[INDENT]    linux-backports-modules-alsa-2.6.32-24-generic
    linux-backports-modules-headers-lucid-generic
    linux-headers-lbm-2.6.32-24-generic
[/INDENT]18. and Apply

\\:D/
Now do the Hokey Pokey because in the end,... That IS what it's all about!

-Steve

---

### Post by mxgold on 2010-09-19
One more thing I had to mes with,.. the externalk monitor is not detected automatically so I had to modify the xorg.conf to get that thing working. Instead of a big long explanation here is my Device and Screen section form xorg.conf. I do not fully understand what these guys are for, so maybe someone else can explain it. All I know is this is working with my external monitor now.

Notice that CRT-0 is because I am using the CRT cable not an HDMI, I think you use the DFP-1 if its HDMI. 

* Also notice that the EDID location is the same.
* EnableBrightnessControl so you can control brightness using the ubuntu applet.
* NoLogo, cuz nvidia is great but I dont need to see it all the time.[INDENT]Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 330M"
    Option       "NoLogo" "true"
    Option       "ConnectedMonitor" "DFP-0"
    Option       "CustomEDID" "DFP-0: /proc/acpi/video/NGFX/LCD/EDID"
    Option            "RegistryDwords" "EnableBrightnessControl=1"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "ConnectedMonitor" "DFP-0,CRT-0"
    Option         "CustomEDID" "DFP-0: /proc/acpi/video/NGFX/LCD/EDID"
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+768, CRT-0: 1600x900 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

-Steve
:popcorn:
[/INDENT]

---

### Post by theanswriz42 on 2010-10-05
Out of curiosity, have you tried the 260 driver yet for nvidia with this setup? 

Thanks for the writeup.

---

### Post by empoulator on 2010-10-06
Dear Mxgold,

Thank you very much for posting this detailed solution. This might be very helpful for many people.

Unfortunately, these procedures did not work for me... 
After step 14, I do not see the Nvidia  logo and I have to use failsafe mode to see a graphical interface again.  
When I did System->Administration-> Nvidia X server settings, I got the following message :
You do not appear to be using the NVIDIA X driver.  Please edit your X  configuration file (just run `nvidia-xconfig` as root), and restart the X  server.

What finally worked for me is describe here :
[[all variants] [HOWTO] Install NVIDIA drivers manually on Lynx - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1467074") 

The steps are roughly (see the post for a detailed solution):
- remove nvidia and nouveau drivers
- go to the Nvidia official page and download the latest driver adapted to your card (typing lspci in a terminal will give you its type).
- Force Disabling the nouveau driver. 
sudo gedit /etc/modprobe.d/blacklist.conf
and add the following lines:
blacklist vga16fb blacklist nouveau blacklist rivafb blacklist nvidiafb blacklist rivatv
- Disable X server (ctrl+alt+f1 + sudo service gdm stop)
- Install the downloaded driver (sudo sh NVIDIA-Linux-x86-256.53.run (in my case))
- reboot (sudo reboot)

It worked for me after 10 hours of intense research, 
I wish good luck to the hair of the people who fall on this post.

All the best,
Empoulator

---

### Post by ic3man on 2010-11-05
did you manage to get it work with maverick?
Because although i did all these i still get a purple blank screen.
Thanks!

---

### Post by cevertje400 on 2010-11-06
Thanks to you i have a vaio (F12M1E) with ubuntu running aswell.

---

### Post by thiagopromano on 2010-11-22
Really thank you, but my printscreen is not working, any idea why? I am using ccsm, i am going to test it...

---

