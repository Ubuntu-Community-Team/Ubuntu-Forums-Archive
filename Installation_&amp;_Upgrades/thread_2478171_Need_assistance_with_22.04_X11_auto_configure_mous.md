---
title: "Need assistance with 22.04 X11 auto configure mouse at start"
date: 2022-08-18
forum: Installation &amp; Upgrades
---

### Post by touretts on 2022-08-18
Hello all,  I recently updated from 20.04 focal to 22.04 jammy and need some assistance with understanding the X11 .xsessions script as to how to build it and where to store it for auto config upon start/logon. In focal i ran a .Xmodmap line in my user home directory which looked like this :  ```
 ! Remap button 8 to 10 and disable button 9.  pointer = 1 2 3 4 5 6 7 12 9 0 
```.   This script/file would remap my mouse button 8 to button 12, thus stopping it from sending the back command to applications. After my initial upgrade I looked for options in Wayland to do this and found that they do not seem to exist, thus I switched to the X11 env instead of wayland.  After switching the environment I was able to find this command to accomplish the same thing for mouse button 8: ```
 xinput set-button-map "input-remapper Razer Razer Viper Ultimate Dongle forwarded" 1 2 3 4 5 6 7 12 9 0 
```  This line of code works great but my issue is I am having a hard time understanding how to configure my .xsessionrc file to work on startup and where I should be placing it to accomplish this upon startup. I assume I could just script this into a generic bash command and have it run everytime Ubuntu starts but I was hoping I could set it up correctly within the X11 framework as I had done with Xmodmap.  I created the .xsessionrc file in my home directory but everytime I  reboot it does not get run. I tried a few different ways such as   ```
 set-button-map "input-remapper Razer Razer Viper Ultimate Dongle forwarded" 1 2 3 4 5 6 7 12 9 0 
```  ```
 #!/bin/bash xinput set-button-map "input-remapper Razer Razer Viper Ultimate Dongle forwarded" 1 2 3 4 5 6 7 12 9 0  
```   from my reading on X11 it runs .xsessionrc file from the usr folder upon login but I am not able to get it working.

---

### Post by touretts on 2022-08-18
this is one site I was referencing to try and understand how to set up this [https://wiki.debian.org/Xsession](https://wiki.debian.org/Xsession)

---

