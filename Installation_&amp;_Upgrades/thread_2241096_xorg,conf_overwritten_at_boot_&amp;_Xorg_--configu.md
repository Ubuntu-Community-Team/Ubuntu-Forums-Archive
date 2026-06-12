---
title: "xorg,conf overwritten at boot &amp; Xorg --configure erroring out"
date: 2014-08-24
forum: Installation &amp; Upgrades
---

### Post by marc-defossez-c on 2014-08-24
[FONT=Ubuntu]
Hi,
  
System: Dell Latitude M6800 with Intel Haswell and Nvidia Quadro K3100M graphics cards.
OS: Ubuntu 14.04.1LTS
Intel Haswell drivers 1.0.6 installed from Intel site:  [https://01.org/linuxgraphics/downloads/2014/intelr-graphics-installer-1.0.6-linux](https://01.org/linuxgraphics/downloads/2014/intelr-graphics-installer-1.0.6-linux)
Nvidia version 331.38 drivers installed via "Software & Updates - Additional Drivers" .
  
Everything was working fine until I docked the PC and wanted two external monitors.
I modified the xorg.conf file so that [/FONT][FONT=Ubuntu][FONT=Ubuntu]each graphics card gets it's monitor and defines one monitor next to the other.
 This is a setup I used [/FONT]for 12.04 on another old Dell latitude - docked PC.
  
After reboot I got all blank screens, even un-docked the PC only booted in command line mode.
After a while a pop-up appeared telling something as: "You are running in low graphics mode, configure the setup yourself"
Examining the xorg.conf file showed that my own xorg.conf was  overwritten and that the new xorg.conf who took over was wrongly  formatted.
therefore X-server error-ed out and made the system boot in text/command mode.
  
I tried to solve that first via the text/command line and found on the web two "solutions".
- remove the: ~/.config/monitors.xml file
- modify the: /etc/init/gpu-manager.conf file (comment the first line starting with "start on (...".
Nothing worked, not when applied combined or separate. 
  
In an attempt to get my system back I removed (purged) all Nvidia stuff from the machine.
After reboot the machine starts back in graphics mode on the Intel Haswell and with "nouveau" drivers.
Trying now to get the system as clean as possible for a new attempt using the docking station and two monitors.
    Execute following:
        sudo dpkg-reconfigure xserver-xorg -phigh
        sudo install build-essential
        sudo install linux-source
        sudo install linux-headers-generic
        sudo-apt-get update
        sudo apt-get upgrade
Now reboot the PC.
Seems OK it nicely boots in graphics mode on the Intel Haswell setup with "nouveau" drivers.
  
Before doing anything else I wanted to see what X-server had to say and executed in a text login (ALT-CTRL-F1):
    sudo service lightdm stop
    sudo Xorg -configure
  
But that ends in an error: "Number of created screens does not match number of detected devices - configuration failed"
When I open the generated xorg.conf.new file in my home directory it  looks partially as the earlier overwritten xorg.conf file I generated  myself but stuffed with extras.
Especially the "ServerLayout" section looks as in my corg.conf file.
    Section "ServerLayout"
        Identifier     "X.org Configured"
        Screen      0  "Screen0" 0 0
        Screen      1  "Screen1" RightOf "Screen0"
        InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
    EndSection
It is normal that X errors out because the PC is not docked and working on its laptop LCD screen.
  
Two questions:
    - Is there a solution for the issue "overwriting the xorg.conf file at boot" that works?
    - Where is xorg -configure finding the contents of the previously overwritten xorg.conf file?
  
Thanks for any help and/or hints.[/FONT]

---

