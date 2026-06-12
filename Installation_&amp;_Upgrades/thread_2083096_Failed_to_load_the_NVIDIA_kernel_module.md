---
title: "Failed to load the NVIDIA kernel module"
date: 2012-11-11
forum: Installation &amp; Upgrades
---

### Post by cbalasubramanian on 2012-11-11
I upgraded ubuntu 11.04 to 11.10. I have a nvidia graphics card. After up gradation I did the following to install the nvidia driver
 

 sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current
 

 Installation was successful. When I tried to set nvidia setting: it gave  me the following message.
“You do not appear to using the NVIDIA X driver. Please edit your X configuration file (just run 'nvidia-xconfig' as root), and restart the X server”
  

 sudo nvidia-xconfig
 sudo service [COLOR=#cc0000]lightdm [/COLOR]restart
 

 Then I rebooted the system. The booting did not happen. 



Then I pressed Cntrl + Alt + F1 to enter into the login mode and gave the following commands to start the xserver
 

 start xserver
 

 I get the following message.
 

 FATAL: Module nvidia_current not found
 EE: NVIDIA: Failed to load the NVIDIA kernel module.  Please check your system's kernel log for additional error messages.
 EE: Failed to load module 'nvidia' (module -specific error, 0)
 EE: No drivers available
 

 Fatal screen error:
 no screens found
 

 Someone please help where should I proceed now to get the xserver starting.

---

### Post by oldfred on 2012-11-13
Ubuntu provides the current nVidia drivers and in the newer versions offers current, current-updates and nvidia-current-experimental-XXX, not sure if they offer all three for older installs or not.

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
See post #19 by Bogan on nVidia drivers from nVidia.
[http://ubuntuforums.org/showthread.php?t=2075318](http://ubuntuforums.org/showthread.php?t=2075318)

---

