---
title: "installed ubuntu but can do nothing"
date: 2014-06-16
forum: Installation &amp; Upgrades
---

### Post by betty3 on 2014-06-16
I've just installed ubuntu 14.04 in my working machine which is a Dell CPU with AMD 64 Athlon x2, that came with XP but had Vista installed in. 
The installation went fine, although I'd previously installed a ubuntu 14.04 32-bit and realized that was 64 bit (I removed completely the previous installation and did a new one with the 64-bit Ubuntu 14.04 CD). However once I'm in the desktop, mouse moves freely until I click or type a shortcut like ctrl+shift+T. I'm not sure if its the RAM which I've no idea of how much memory capacity it has. Is ubuntu that heavy? should I try lubuntu for instance and install the minimal version?? is that going to cause incompatibility issues. Or should I just re install it one more time...
Thanks anyway.

---

### Post by LastDino on 2014-06-16
Post out put of 
```
sudo lshw
```

In ''code'' tags.

---

### Post by grahammechanical on 2014-06-16
Ubuntu 14.04 uses less memory than Ubuntu 12.04 does but 14.04 does have a fall back video driver for graphic adapters that cannot support 3D accelerated graphics. It tries to approximate the 3D experience but things do move slowly.

2 key questions. How much memory does that graphic adapter have? Is it capable of running 3D Unity? Run this command in the terminal.

```
/usr/lib/nux/unity_support_test -p
```

This is what I see

> OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NVA5
OpenGL version string:  3.0 Mesa 10.1.3


Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes


Unity 3D supported:       yes


Gallium = Open Source video driver. You might also want to go to System Settings>Software and Updates>Additional Drivers tab and experiment with proprietary video drivers. Allow time for the utility to find the drivers.

Regards.

---

### Post by betty3 on 2014-06-17
I can't tap anything... that's the problem

---

### Post by Mark Phelps on 2014-06-17
XP machines typically came with very little memory -- often, 1GB was the default. While this is enough to run Ubuntu, it's not going to run particularly fast.

And, you should not have to install proprietary drivers just to see a desktop.

If this was a preinstalled machine, at least tell us the model number to see what hardware it has.

---

### Post by betty3 on 2014-06-17
Ok I've managed to access the recovery mode and even to run the terminal while it momentarily worked. I found out that it has 4 Gb of memory which I think is enough and the HDD has 160 Gb.
I even tried to fix the boot which was giving me some problems with the boot repair program. It gave me this report : [http://paste.ubuntu.com/7658526/](http://paste.ubuntu.com/7658526/)
when I was in the recovery mode I updated the boot, I repaired broken packages and checked system info. After doing that I could use ubuntu properly. I think some graphical components had to be restarted and it worked better but without going into the recovery mode and without unmounting some things by doing this checks and repairs it was impossible to do anything.
I thought that this would do it but no. Maybe it is something that has to do with the graphical part. 
The computer is Dell Dimension C521

---

### Post by betty3 on 2014-06-17
By the way. When I checked the sytem status (or configuration) in the recovery (or safe) mode there were two important statements :
No software RAID detected (mdstat) 
No LVM detected (vgscan)

---

### Post by betty3 on 2014-06-17
there was a moment where I entered ubuntu normally (not on safe mode) and opened the terminal. I was typing my password and then this came out in the terminal
```
[COLOR=#555555][FONT=sans-serif]PCI (sysfs)[/FONT][/COLOR]
```

---

### Post by betty3 on 2014-06-18
There is something about media card readers related to PCI sysfs
When I go to the BIOS  and then system settings in the Onboard devices the USB floppy is enabled and it says that if this option is chosen the USB contoller must be set to on. Effectively it is set to on but there is also a way to enable the usb controller but not at Boot.  
In the Floppy onboard settings (where the usb floppy is listed) there is stated that if the computer supports USB the changes made will just affect the BIOS.. However since the keyboard and mouse are USB devices I'm afraid that setting USB floppy to off or at least changing USB controller to enabled but not at boot will make me loose the keyboard and mouse. 
Any ideas ??

---

### Post by Digital_Man on 2014-07-15
My parents both have [COLOR=#000000][FONT=Helvetica]Dell Dimension C521's, and I just encountered this problem too.

Here is how I solved it. I booted into recovery mode and installed Nvidia's own drivers (from the PPA) that way:

[/FONT][/COLOR][COLOR=#696969][FONT=courier new][I]sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current[/I][/FONT][/COLOR][COLOR=#000000][FONT=Helvetica]

After the install and rebooting, I was able to get into 14.04 without any difficulty.[/FONT][/COLOR]

---

