---
title: "Mythbutu 11.04 -&gt; 11.10 breaks X-server"
date: 2012-01-06
forum: Installation &amp; Upgrades
---

### Post by rkannan55 on 2012-01-06
Hello,

I had a working version of Mythbuntu 11.04 on my laptop  and I gave in to frequent suggestions from it to upgrade to Ubuntu 11.00  this afternoon. Friday afternoon is not a good time to update. After  installing the updates, it restarted and I found that the X server is  broke.

I can login to the consoles Alt-F1...Alt-F5 fine but the X server  shows a blank seen. The Myth backend seems to be running fine and so is  Mythweb web server (Apache). The file system seems OK but the X-display  flashes for a few times and there is a blank screen. I have tried..

init 3
init 5

to restart the X server with the same result.

I  see an error message flash by just after grub but I cannot make out  anything. It switches then to purple splash screen before the flashing  followed by 

I thought the update should not change the configuration files and so should work as before.

Any ideas?

Thanks

---

### Post by rkannan55 on 2012-01-08
looked at /var/log/Xorg.0.log file and found the following

[    77.000] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Jan  7 08:35:29 2012
[    77.000] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    77.000] (==) No Layout section.  Using the first Screen section.
[    77.000] (==) No screen section available. Using defaults.
[    77.000] (**) |-->Screen "Default Screen Section" (0)
[    77.000] (**) |   |-->Monitor "<default monitor>"
[    77.000] (==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
[    77.001] (==) Automatically adding devices
[    77.001] (==) Automatically enabling devices
[    77.001] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.

So there is no configuration but using defaults. The conf files under /usr/share/X11/xorg.conf.d did not have Screen or Monitor sections. They had several input sections similar to

Section "InputClass"
        Identifier "evdev pointer catchall"
        MatchIsPointer "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

So I tried to create a new configuration file with

Xorg -configure

I ot the following:

(EE) Failed to load module "vmwgfx" (module does not exist, 0)
(EE) vmware: Please ignore the above warnings about not being able to to load module/driver vmwgfx
(++) Using config file: "/root/xorg.conf.new"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
Number of created screens does not match number of detected devices.
  Configuration failed.
 ddxSigGiveUp: Closing log

I cannot understand where the two screens are coming from.

At one time with my old configuration I had added an external monitor and disabled it in Xfwm window manager. I tried turning the external monitor on without any luck. 

Someone had suggested that I should turn off the autologon off (/etc/gdm/custom.conf). That did not help.

Thanks

---

### Post by MAFoElffen on 2012-01-08
> **rkannan55 said:**
> looked at /var/log/Xorg.0.log file and found the following

[    77.000] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Jan  7 08:35:29 2012
[    77.000] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    77.000] (==) No Layout section.  Using the first Screen section.
[    77.000] (==) No screen section available. Using defaults.
[    77.000] (**) |-->Screen "Default Screen Section" (0)
[    77.000] (**) |   |-->Monitor "<default monitor>"
[    77.000] (==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
[    77.001] (==) Automatically adding devices
[    77.001] (==) Automatically enabling devices
[    77.001] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.

So there is no configuration but using defaults. The conf files under /usr/share/X11/xorg.conf.d did not have Screen or Monitor sections. They had several input sections similar to

Section "InputClass"
        Identifier "evdev pointer catchall"
        MatchIsPointer "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

So I tried to create a new configuration file with

Xorg -configure

I ot the following:

(EE) Failed to load module "vmwgfx" (module does not exist, 0)
(EE) vmware: Please ignore the above warnings about not being able to to load module/driver vmwgfx
(++) Using config file: "/root/xorg.conf.new"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
Number of created screens does not match number of detected devices.
  Configuration failed.
 ddxSigGiveUp: Closing log

I cannot understand where the two screens are coming from.

At one time with my old configuration I had added an external monitor and disabled it in Xfwm window manager. I tried turning the external monitor on without any luck. 

Someone had suggested that I should turn off the autologon off (/etc/gdm/custom.conf). That did not help.

Thanks
Please post the whole /var/log/Xorg.0.log file and the results of 
```

lspci -vnn | grep VGA

```
Then install hwinfo
```

sudo apt-get install hwinfo

```
And post the results of 
```

sudo hwinfo --monitor && sudo hwinfo --framebuffer

```
When posting that file and the above results, please press the "#" icon in the posting toolbar and paste the text inside the code tags (for each results or log file).

---

### Post by rkannan55 on 2012-01-08
I found out the issue is with LDM (Light Display Manager) used with Ubuntu 11.11. I could do the following and get X going..

sudo service lightdm stop # Stop LDM
sudo service gdm start # Start the old Graphics display manager
 
after renaming custom.conf file in /etc/gdm which had auto log-on enabled. 

BTW, The graphics card information on my laptop is as below.

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960  Integrated Graphics Controller (primary) (rev 0c) (prog-if 00 [VGA  controller])
        Subsystem: Lenovo T61
        Flags: bus master, fast devsel, latency 0, IRQ 46
        Memory at f8100000 (64-bit, non-prefetchable) [size=1M]
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 1800 [size=8]
        Expansion ROM at <unassigned> [disabled]
         Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
        Capabilities: [d0] Power Management version 3
        Kernel modules: intelfb, i915

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
         Subsystem: Lenovo T61
        Flags: bus master, fast devsel, latency 0
        Memory at f8200000 (64-bit, non-prefetchable) [size=1M]
        Capabilities: [d0] Power Management version 3

---

