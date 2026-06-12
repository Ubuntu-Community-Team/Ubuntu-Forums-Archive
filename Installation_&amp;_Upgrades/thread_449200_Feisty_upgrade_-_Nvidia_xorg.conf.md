---
title: "Feisty upgrade - Nvidia xorg.conf"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by NevadaDave on 2007-05-20
I recently upgraded to feisty, and I have an Nvidia GeForce MX440 video card. Initially, the upgrade seemed to work fine, but when I tried to upgrade my system to support the 1680x1050 mode of my Viewsonic 22" monitor, I ended up in a situation that I can't figure out. I used Envy to load the latest drivers, and since then, the system has worked as follows:
When I boot, I get the splash screen then, it goes blank, I see what looks like terminal commands (i.e. black backgound, white letters) scrolling by faster than I can read, then I get a screen with a message that says the X server can't start, would I like to see the log file? I select yes, and I get a log file that says that in /etc/X11/xorg.conf the file /lib/modules/2.6.20-15-386/volatile/nvidia.ko can't be located. Sure enough, if I get back to the command line, I look and there is no nvidia.ko. Instead, there is an nvidia_new.ko.
After putzing around, I found that if I run envy from the command line and reinstall the nvidia drivers, I can choose to reastart the x server, and the system will show me my normal Ubuntu desktop. If I then do a cp nvidia_new.ko nvidia.ko, then an rm nvidia_new.ko, I can successfully restart and everything works. HOWEVER - if I then look in the volatile folder, nvidia.ko is gone, and there is s new nvidia_new.ko! No matter what I do, I can't seem to get rid of this file and whatever keeps removing the nvidia.ko file.
In xorg.conf, the only reference I can find that sounds remotely relevant is in the device section:
Section "Device"
    Identifier     "NVIDIA Corporation NV17 [GeForce4 MX 440]"
    Driver         "nvidia"
EndSection
I cannot find anyhting that looks for an nvidia.ko. However, I found that if, for example, I change the driver entry to "nvidia_new" (or any other permutation, such as nvidia_new.ko, or show the entire path) I still get the same error, only this time, the info that I put into the Driver section is shown as the missing file name.
Does anyone know what to do about this? It has completely flummoxed me!

---

### Post by NevadaDave on 2007-05-20
Any Nvidia/xorg experts out there? Should I just download the dvd image and start completely over?

---

### Post by topsites on 2007-05-29
No, this crap is a royal pita, this is my 3rd time dealing with this and every single time I'm down for a good two days (translation:  several hours of fun!).

But before I go off on the below rant, I found and am printing the following (which I intend to use as soon as I am done saving here):
[http://albertomilone.com/latest_nvidia_udsf_feisty.html](http://albertomilone.com/latest_nvidia_udsf_feisty.html)
Make sure you got some 30 pages of PAPER loaded and plenty of ink lol, might want to select draft mode.

If that doesn't work for you then I can usually get it to work, but it's always the non-openglx / non-enhanced nvidia (old) stuff and everything sux.

Yes, I know about the nvidia_new.ko / nvidia.ko bit, I haven't a clue as to that nonsense, either.

If it helps, the following I found out:
You might can try under the xorg.conf to change "nv" to "nvidia" or vice versa, sometimes this clicks BUT:
NV is the NON-accelerated version.
nvidia is the full deal.

nvidia-glx is 9631 and is the correct driver for "nVidia Corporation NV17 [GeForce4 MX 440]"
nvidia-glx-new is 9775 and is the WRONG one for older cards!
nvidia-glx-legacy is way old, older than geforce4 and is also wrong.

To load the right one:
sudo aptitude install nvidia-glx

Don't forget:
sudo dpkg-reconfigure -phigh xserver-xorg

One neat thread:
[http://www.linuxforums.org/forum/ubuntu-help/91648-nvidia-api-mismatch-feisty.html](http://www.linuxforums.org/forum/ubuntu-help/91648-nvidia-api-mismatch-feisty.html)

Other documentation:
Debian GNU/Linux or Ubuntu with Xorg 7.x

If you wish to install the NVIDIA Linux graphics driver on a Debian GNU/Linux or Ubuntu system that ships with Xorg 7.x, please ensure that your system meets the following requirements:

    * development tools like make and gcc are installed
    * the linux-headers package matching the installed Linux kernel is installed
    * the pkg-config and xserver-xorg-dev packages are installed
    * the nvidia-glx package has been uninstalled with the --purge option and the file /etc/init.d/nvidia-glx or /etc/init.d/nvidia-kernel does not exist.

If you use Ubuntu, please also ensure that the linux-restricted-modules or linux-restricted-modules-common packages have been uninstalled. Alternatively, you can edit the /etc/default/linux-restricted-modules or /etc/default/linux-restricted-modules-common configuration file and disable the NVIDIA linux-restricted kernel modules (nvidia, nvidia_legacy) via:

    DISABLED_MODULES="nv"

Oh, just one more thing:  mine's still down but hopefully not for long.

---

