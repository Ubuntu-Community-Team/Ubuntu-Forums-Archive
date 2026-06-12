---
title: "ubuntu 9.10 display problem"
date: 2010-06-18
forum: Installation &amp; Upgrades
---

### Post by rovinsan on 2010-06-18
Hi 

i just installed ubuntu 9.10 on my pc which originally had XP Pro

i have a asus a7n266-vm motherboard with nvidia nforce chipset.

my resolution is set to 800X600(max) and i am not able to see any thing higher in the drop down.

The XP install had a higher resolution ( 1024X768 ) and it used to detect the monitors automatically
 
Is there anything i have to do extra after installing ubuntu to get higher resolution in my configuration?

Thanks.

---

### Post by byStanderone on 2010-06-18
...yes, you will have to install the driver for your nvidia...system>administration>hardware drivers

once the nvidia driver is installed...you will have to do some reconfiguration:

sudo dpkg-reconfigure -phigh xserver-xorg

sudo nvidia-xconfig

then reboot

...after reboot, findout from the dropdown menus system>administration if the nvidia x server setting menu exist. if it does exist click on it so as to enter into the nvidia control gui....go to xserver display configuration and adjust your display resolution using it.

if the nvidia x server setting is not present in the dropdown menu...do a sudo apt-get install nvidia-settings

---

### Post by byStanderone on 2010-07-27
...should you still not find the resolution you wanted on the nvidia xserver setting, review the xorg.conf file, add the desired resolution as sampled here:

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection

Note: the desired resolution will not be attained and a resolution error will also occur if the horizontal and vertical range under the monitor section of xorg.conf is incorrect. this ranges is monitor dependent, newer monitor would automatically report their horizontal and vertical ranges, but for older ones, a manual edit of the xorg.conf file is necessary.

example:

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 85.0
    VertRefresh     50.0 - 60.0
    Option         "DPMS"
EndSection

---

