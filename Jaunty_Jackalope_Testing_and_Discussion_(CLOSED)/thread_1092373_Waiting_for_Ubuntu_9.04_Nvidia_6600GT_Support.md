---
title: "Waiting for Ubuntu 9.04/ Nvidia 6600GT Support?"
date: 2009-03-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Nightstrike2009 on 2009-03-10
Hello everyone, I'd like to know is installing 3D desktop effects with an Nvidia 6600GT (using offline .deb files) possible yet in Ubuntu 9.04?  

I am currenly downloading the 9.04 Alpha 5 version (I will use final on release but can't wait LOL) & once I've got my machine set-up for dual-boot will attempt this for myself. I was using 8.10 and got desktop effects working. I found bluetooth support only worked one way, from mobile to PC but not vice versa, hope this has been fixed in new version.;)

I am looking forward to testing out another great Ubuntu release. :D

---

### Post by stchman on 2009-03-10
> **Nightstrike2009 said:**
> Hello everyone, I'd like to know is installing 3D desktop effects with an Nvidia 6600GT (using offline .deb files) possible yet in Ubuntu 9.04?  

I am currenly downloading the 9.04 Alpha 5 version (I will use final on release but can't wait LOL) & once I've got my machine set-up for dual-boot will attempt this for myself. I was using 8.10 and got desktop effects working. I found bluetooth support only worked one way, from mobile to PC but not vice versa, hope this has been fixed in new version.;)

I am looking forward to testing out another great Ubuntu release. :D

The 6600GT card is supported fully since Feisty I believe.  Just enable the Nvidia driver in 

System--->Administration--->Hardware Drivers

I have a 7600GT and 8800GT that work very well with Hardy.

---

### Post by Nightstrike2009 on 2009-03-10
In Ubuntu 8.10 this was neccesary;[http://ubuntuforums.org/showthread.php?t=1035634](http://ubuntuforums.org/showthread.php?t=1035634). Thanks for your help but I am enquiring specifically about *Offline installation* for non-internet PCs'> Hello everyone, I'd like to know is installing 3D desktop effects with an Nvidia 6600GT (using offline .deb files) possible yet in Ubuntu 9.04? by downloading .deb files and placing them on non-internet connected PC's, least it should be possible though, thanks for info. ;)

---

### Post by Nightstrike2009 on 2009-03-11
**Nvidia 180 Driver (Recommended for use with Ubuntu 9.04 instead of the 177 Driver) Tested on Alpha 5**

Website:[http://packages.ubuntu.com/jaunty/misc/nvidia-180-kernel-source]("http://packages.ubuntu.com/jaunty/misc/nvidia-180-kernel-source")
[I]
FILES REQUIRED BY UBUNTU 9.04:[/I]

[COLOR="SeaGreen"]dkms_2.0.21.1-0ubuntu3_all
nvidia-180-kernel-source_180.35-0ubuntu1_i386
nvidia-glx-180_180.35-0ubuntu1_i386[/COLOR]

This file is also required:

[COLOR="SeaGreen"]nvidia-180-libvdpau_180.35-0ubuntu1_i386[/COLOR]

Website:[http://packages.ubuntu.com/jaunty/misc/nvidia-180-libvdpau](http://packages.ubuntu.com/jaunty/misc/nvidia-180-libvdpau)

To install these .deb file double click on the icon and click install in the package manager that appears either install the 4 Nvidia 180 driver files mentioned above, then go to SYSTEM>ADMINISTRATION>HARDWARE DRIVERS select NVIDIA ACCELERATED GRAPHICS DRIVER VERSION 180 click enable, an arrow should appear asking you to restart your system.

After restarting your system the driver will enable, select your desktop effects from appearances
and your up and running

**Nvidia Settings (For 180 Driver)**

Website:[http://packages.ubuntu.com/jaunty/nvidia-settings]("http://packages.ubuntu.com/jaunty/nvidia-settings")

Adds System/Administration/NVIDIA X Server Settings (GUI to Ubuntu's Menu Bar)

*FILES REQUIRED BY UBUNTU 9.04:*

[COLOR="SeaGreen"]nvidia-settings_180.25-0ubuntu1_i386[/COLOR]

---

### Post by Nightstrike2009 on 2009-03-11
I haven't got compiz working yet although my 3D driver is up and running. Ive downloaded these files (including dependancies);
[COLOR="SeaGreen"]
compizconfig-settings-manager_0.8.2-0ubuntu1_all
python2.6_2.6.1-1ubuntu1_i386
python-compizconfig_0.8.2-0ubuntu1_i386
python-minimal_2.6.1-0ubuntu3_all[/COLOR]

But when I get to [COLOR="SeaGreen"]python-minimal_2.6.1-0ubuntu3_all[/COLOR] I get this error 
[COLOR="Red"]ERROR: Breaks existing package "Python" dependancy "Python-minimal (=2.5.4-0ubuntu5)[/COLOR]

I understand this is refering to a previous version of python and I could remove with Synaptic but this would remove all its dependancies to and possibly prevent my Ubuntu from working. Has anyone got any advice on this or should I just wait and see whether Ubuntu 9.04 has python 2.6 as standard on release as my version is alpha 5 (Testing Version) after all?

UPDATE: Just been elsewhere on the forum it seems Ubuntu 9.04 will be updating to Python 2.6, so all should be well then, I will provide updates & further how-to's as I prove them to work :)

---

