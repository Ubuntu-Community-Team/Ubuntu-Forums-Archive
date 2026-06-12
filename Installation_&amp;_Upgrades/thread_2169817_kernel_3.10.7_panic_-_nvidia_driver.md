---
title: "kernel 3.10.7 panic - nvidia driver"
date: 2013-08-23
forum: Installation &amp; Upgrades
---

### Post by PABlanche on 2013-08-23
Hi,

I was running Ubuntu 13.04 with kernel 3.8.0-29 fine on a intel core i7 cpu Q840, graphic card NVIDIAGT216M [NVS 5100M].

Because a USB thumbdrive was not automounting correctly (seriously), I was suggested on this forum (no hard feeling) to upgrade my kernel to 3.10.7 ... and all hell brooke loose :(

At restart, my screen resolution was downgraded, the ubuntu launcher was not there anymoere, windows can not be moved, the Nvidia driver was not running properly. (But the USB thumbdrive was mounting, yeah)

I tried (unsuccessfully):
1/ reselecting the nvidia driver via "additional drivers" windows.
1b/selecting a different nvidia driver (I have 304, 310, 313) 
2/ nvidia-settings in terminal -> error message "you are not using nvidia X driver" and the settings left pannel has only one line where there should be a bunch
3/ nvidia-xconfig in terminal -> "new xconfig file written to /etc/x11/xorg.conf" But does not help for 2/
4/ uninstall - reinstall nvidia drivers via terminal:
sudo apt-get --purge remove nvidia-*
sudo apt-get install nvidia-current
5/ reinstall ubuntu desktop : sudo apt-get install ubuntu-desktop
6/ get back to older configuration via grup (goes back to 3.2.0-32)
7/ entering the recovery mode and running diagnostic
8/ upgrade to kernel 3.10.9-031009
9/ install bumblebee
10/ restart lightdm
99/... 

So far it is getting worst and worst:

- At restart (with 3.2.0) it is entering the low graphic mode and often do not even go to the GUI, only terminal line. Even when entering the GUI, it exits without notice goes back to command line with unreadable characters.

- when using kernel 3.10.9 I have "fail to execut /init" and "Kernel panic - not syncing: No init found"

- sarting with ubuntu on a bootable thumbdrive, it loops saying: "timeout: killing '/sbin/modprobe -bv pci"

- var/log/Xorg.1.log:
 (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

- var/log/xorg.0.log:
(EE) NVIDIA(0): fail to initialize the NVIDIA kernel module. See the system's kernel log
(EE) NVIDIA(0):Failing initialization of x screen 0
(EE) screen found but none have usable configuration

- the graphic card in the system detail graphics is NOT a NVIDIA but a VESA GT216 board (might be the onboard cpu one?)

So, I am pretty desperate at this point and any help is welcome.
Sincerely,
-- 
PAB

---

