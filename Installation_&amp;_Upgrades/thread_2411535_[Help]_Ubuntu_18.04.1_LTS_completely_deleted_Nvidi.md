---
title: "[Help] Ubuntu 18.04.1 LTS completely deleted Nvidia drivers"
date: 2019-01-31
forum: Installation &amp; Upgrades
---

### Post by kdx2 on 2019-01-31
Hello community,
my issue is the following. I went sleeping and I had Nvidia drivers, I woke up and I didn't anymore. The screen said: Ubuntu internal error occured and from that point on I have no Nvidia drivers. The cudNN library is also completely wiped off. The laptop was not even doing anything overnight. Usually I used to train neural network models overnight, that night I didn't do absolutely anything, the laptop was on and idle. The graphics card is G970M. I need to get it back, and I think without good reason Ubuntu shouldn't allow such destructive operations without permission.
The picture currently is:
llvmpipe (LLVM 6.0, 256 bits) <<< that is what it's using for the graphics at the moment.
lsmod | grep nouveau            <<< prints nothing
lsmod | grep nvidia                <<< prints nothing
nvidia-smi                             <<< prints "NVIDIA-SMI has failed because it couldn't communicate with the NVIDIA driver. Make sure that the latest NVIDIA driver is installed and running."

[ATTACH=CONFIG]282363[/ATTACH]
I also have that.
I blacklisted nouveau drivers like pointed out in the following guidelines:
[https://askubuntu.com/questions/481414/install-nvidia-driver-instead-of-nouveau?fbclid=IwAR3x5THkKQI6owIp-uBmfkNtbdkW7zb-PxcdzNrhXvCDmH9wzrOaTS7fiwU](https://askubuntu.com/questions/481414/install-nvidia-driver-instead-of-nouveau?fbclid=IwAR3x5THkKQI6owIp-uBmfkNtbdkW7zb-PxcdzNrhXvCDmH9wzrOaTS7fiwU)

My computer is using gdm3. None of the following commands do anything useful to me:
    sudo service lightdm stop  <<< this command makes the screen go black with a blinking cursor at (0,0) of the screen. Not allowing me to enter anything.

    sudo /etc/init.d/gdm stop  <<< this command does not even exist on my computer

    sudo service gdm3 stop     <<< executes, nothing visually changes
    
    ctl+alt+f1
the last one just makes me re-log-in in my ubuntu account and then starts up the GUI. As far as I understood, it should be Ubuntu in text-mode, it's not, it is a perfect GUI version of GUI, just like another workspace.

Lastly, I am trying to install manually downloaded Nvidia drivers from an executable installer from the official Nvidia website and what the installer complains about is:
[ATTACH=CONFIG]282364[/ATTACH]

nvidia-settings          <<< prints, ERROR: NVIDIA driver is not loaded, ERROR: Unable to load info from any available system


I hope that info gives you enough of the full picture. If you can offer any help, that would be highly valuable. I spoke to another person who experienced EXACTLY the same problem and ended up re-installing the whole ubuntu OS. I cannot afford that because I had heavy-to-compile libraries which took me tons of time and I am rather trying to avoid that.

I really need the cuda optimizations because my work is now blocked because of that. The last time I had absolutely no problem installing Nvidia drivers, this time is a mess. For comparison an Epoch would take me 30min. with the cuda, without is 6h now.

---

### Post by Autodave on 2019-01-31
Do not attempt to install the drivers right from the Nvidia site: this will cause nothing but problems.  Always install from the repositories.

Where did you originally get the Nvidia driver from?

---

### Post by ubfan1 on 2019-01-31
Check the little gear icon at the login screen -- it should NOT have wayland selected.  Selecting Wayland will (now) automatically switch the video drivers off Nvidia, probably to i915 for the integrated video hardware.

---

