---
title: "Nvidia 8600GT on Dell Inspiron 1520 / start in tty1 login console mode"
date: 2010-12-17
forum: Installation &amp; Upgrades
---

### Post by sherbieny on 2010-12-17
Hello,

I tried most methods suggested on many sites to install drivers

## through the additional driver panel only
## through the Nvidia.run file I downloaded
## through the terminal using apt-get

all failed to start ubuntu gui it takes me to the console login and I noticed it says "saned disabled" edit /etc/..something..

this problem made me install ubuntu again three times and every time I activate the driver then install the driver Nvidia.run or through apt-get and both leads to a black screen tty1 login 

so what to do now I installed and removed many things and I won't reinstall ubuntu again

Also I typed compiz and this came on


root@ubuntu:/home/sherbieny# compiz
Xlib:  extension "GLX" missing on display ":1.0".
compiz (core) - Fatal: Root visual is not a GL visual
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :1.0

Launching fallback window manager

please help I wan't to install properly so that I can start normally and enable the extra visual effects and the custom effects

Please elaborate the steps clearly

New Info:
when I enter nvidia-settings : server X opens and says
You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server

when i enter nvidia-xconfig as root and restart nothing happens

and when I enter:
nvidia-detector it says none

and when I enter: nvidia-smi 

Error: API mismatch: the NVIDIA kernel module has version 260.19.21,
but this NVIDIA driver component has version 260.19.29.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
Failed to allocate an RM client
Could not allocate resources!
root@ubuntu:/home/sherbieny# apt-get update kernel
E: The update command takes no arguments

A new and very exciting error everyone :D
now also the windows 7 that I have besides linux has also crashed and cannot open the login window hahahahahahahahahah I don't know whats happening all I know is that few hours ago I logged in to windows normally now I cannot login to either one of them and the funny part is: I'm working on my thesis on this computer and I cannot work anymore and I'm supposed to meet with the professor on monday hahahahahhahahah

pleeeeeeeeeaaaaaaaaaaaaaaaseeeeeeeeeeeee help

---

### Post by sherbieny on 2010-12-24
A new ubuntu installation with the normal driver activation solved everything :D

---

