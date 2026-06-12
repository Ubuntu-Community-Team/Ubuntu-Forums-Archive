---
title: "nvidia installed but not loading/working"
date: 2008-07-17
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by phidia on 2008-07-17
This is my card: ibexx:~$ lspci | grep VGA
05:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GS] (rev a1)
I installed the nvidia kernel through synaptic (alpha2 w/latest updates x86_64) The xorg.conf nvidia-xconf created was really bad-called out vesa and the highest rez was 640x480 although it did see my 19" optiquest monitor correctly. Odd. I copied my gutsy xorg and am using it in intrepid now. The really odd thing is x loads with the nvidia driver called out but it's not being used?? When I open "NVIDIA X Server Settings" I get this: "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

 Below are the other outputs:
> Reading state information... Done
nvidia-glx-173 is already the newest version.
nvidia-glx-173 set to manually installed.
Reading state information... Done
linux-headers-2.6.26-4-generic is already the newest version.
ibexx:~$ glxgears 
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual
@ibexx:~$ sudo apt-get install nvidia-glx
The following packages have unmet dependencies:
  nvidia-glx: Depends: xserver-xorg-core (>= 1:0.99.0-1) but it is not going to be installed
E: Broken packages


lsmod does show the nvidia module.

---

### Post by ronacc on 2008-07-17
the easiest way to get out of this is to copy a known good xorg.conf file into your /etc/X11 directory replacing the bad one then reboot . I have been using the same xorg.conf file since fiesty I just copy it from install to install .

---

### Post by ronacc on 2008-07-17
also I have a 7600gs also and I'm using nvidia-glx-177

---

### Post by phidia on 2008-07-17
Thanks ronacc but as i said > I copied my gutsy xorg and am using it in intrepid now.  It's there but not really working for some reason. 
I'm suprised x loads with xorg.conf listing the "nvidia" driver and yet it's not being used???

---

### Post by philinux on 2008-07-17
I assume you've got the 177 or other driver installed in synaptic.

Make sure you've got your xorg.conf backup safe.

sudo dpkg-reconfigure xserver-xorg -phigh 
To create the default xorg.conf

Then added the two lines.
Driver "nvidia"
Option "NoLogo"

Reboot.

---

### Post by ronacc on 2008-07-17
hmm it works fine for me ? sorry I missed the part about your gutsy xorg.conf , attached are a screenshot and a txt file with my monitor , device and screen sections in case they may help . my monitor is a 19" widescreen samsung lcd so your mode lines may differ .

---

### Post by phidia on 2008-07-17
> nvidia-glx-173 is already the newest version.

My current xorg.conf (showing the device section):
> Section "Device"
    Identifier     "nVidia Corporation G70 [GeForce 7600 GS]"
    Driver         "nvidia"
    BoardName      "nv"
    BusID          "PCI:5:0:0"
    Screen          0
EndSection

Section "Device"
 # 
    Identifier     "device1"
    Driver         "nvidia"
    BoardName      "nv"
    BusID          "PCI:5:0:0"
    Screen          1
EndSection
As i said-look at my ist post-this is strange since x starts without complaining but the nvidia driver isn't working-even though it's the driver called out in xorg.conf.
Added: btw my modelines are fine now after the last issuing of "sudo nvidia-xconf".
Hey it a dev release-i realize that :)

---

### Post by jfernyhough on 2008-07-17
I've done the following two-step procedure many times to fix a borked X setup:

$ sudo dpkg-reconfigure -phigh xserver-xorg
$ sudo nano /etc/X11/xorg.conf

in

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Add the line ' Driver "nvidia" ' to get:

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "nvidia"
EndSection

Save, restart X. Nvidia logo should come up. The only thing on Intrepid at the moment is this also wipes any customisation for synaptics touchpads etc.

---

### Post by phidia on 2008-07-17
:confused: Ok on this reboot the nvidia driver works glxgears shows the gears and a decent frame rate too. The login screen was huge though and off center too-but I hardly think that's hardly worth reporting.
I did reboot before and it didn't work then. The logo did not show on boot up and I didn't add the hide line to xorg. ?
I guess I'll play with the nvidia setting gui. Thanks for helping!

---

### Post by jadacyrus on 2008-07-19
I'm getting the same problem. I tried the dpkg-reconfigure as mentioned above and edited the Xorg as shown but still no luck. Im getting the same error messages as op.

---

### Post by cariboo on 2008-07-19
Phidia you are using the wrong driver according to detail panel in synaptic the correct driver for your gforce 7800gs is the nvidia-glx-177

Jim

---

### Post by tseliot on 2008-07-19
> **phidia said:**
> 
 Below are the other outputs:
```
Reading state information... Done
nvidia-glx-173 is already the newest version.
nvidia-glx-173 set to manually installed.
Reading state information... Done
linux-headers-2.6.26-4-generic is already the newest version.
ibexx:~$ glxgears 
Xlib: extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual
@ibexx:~$ sudo apt-get install nvidia-glx
The following packages have unmet dependencies:
nvidia-glx: Depends: xserver-xorg-core (>= 1:0.99.0-1) but it is not going to be installed
E: Broken packages
```

nvidia-glx can't be installed for obvious reasons.

Please attach your /var/log/Xorg.0.log and your /etc/X11/xorg.conf

---

