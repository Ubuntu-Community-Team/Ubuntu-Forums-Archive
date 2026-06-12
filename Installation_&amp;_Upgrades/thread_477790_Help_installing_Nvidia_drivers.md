---
title: "Help installing Nvidia drivers"
date: 2007-06-18
forum: Installation &amp; Upgrades
---

### Post by ChopperX on 2007-06-18
Ok i am trying to update my drivers for nvidia and i cant seem to get it to work. i downloaded the installer for linux off the website, ran it in terminal like it asked then i got this error

eric@eric-desktop:~$ sh NVIDIA-Linux-x86-1.0-9755-pkg1.run
Verifying archive integrity... OK
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86 1.0-9755........................................................................................................................................................................................................................................................................................
nvidia-installer: Error opening log file '/var/log/nvidia-installer.log' for writing (Permission denied); disabling logging.
eric@eric-desktop:~$

---

### Post by Medieval_Creations on 2007-06-18
Try running it with sudo.  That should take care of the permissions issue.

---

### Post by ChopperX on 2007-06-18
Ok i tried it and i got this error. The installer is located in my home folder. Is that an issue?

eric@eric-desktop:~$ sudo NVIDIA-Linux-x86-1.0-9755-pkg1.run
sudo: NVIDIA-Linux-x86-1.0-9755-pkg1.run: command not found
eric@eric-desktop:~$

---

### Post by stchman on 2007-06-18
> **ChopperX said:**
> Ok i am trying to update my drivers for nvidia and i cant seem to get it to work. i downloaded the installer for linux off the website, ran it in terminal like it asked then i got this error

eric@eric-desktop:~$ sh NVIDIA-Linux-x86-1.0-9755-pkg1.run
Verifying archive integrity... OK
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86 1.0-9755........................................................................................................................................................................................................................................................................................
nvidia-installer: Error opening log file '/var/log/nvidia-installer.log' for writing (Permission denied); disabling logging.
eric@eric-desktop:~$

Just enable the restricted drivers under System--->Administration--->Restricted drivers

---

### Post by Medieval_Creations on 2007-06-18
Sorry, should have been clearer...

Try:
 sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1.run

Alternatively, I just used the nvidia driver in the repositories nvidia-glx and have had no problems with it, once I reconfigured x-server.

sudo apt-get install nvidia-glx
sudo dpkg -reconfigure x-server-xorg

---

### Post by crxvfr on 2007-06-18
When I turned on Desktop Effects on my dell, ubuntu automatically downloaded and configured the driver for my nvidia. Tried that?

---

### Post by ChopperX on 2007-06-18
Well i ran the Restricted Drivers and it says NVidia accelerated graphics drivers. Its enabled and its inuse.

---

### Post by Medieval_Creations on 2007-06-18
> **ChopperX said:**
> Well i ran the Restricted Drivers and it says NVidia accelerated graphics drivers. Its enabled and its inuse.

Then you should be all set.  I've never the Driver Manager, but if you aren't experiencing any problems, you should be good to go.

---

### Post by ChopperX on 2007-06-18
yea but i cant install the update.

---

### Post by Medieval_Creations on 2007-06-18
What update?  do you mean the newest nVidia Driver off the nVidia web site?  Because I haven't had any problems with  the driver from the ubuntu repositories and haven't tried the nividia ones, so I'm not going to be much more help...

---

### Post by nutz on 2007-06-18
I recommend you stick with the driver from the repositories. Unless that driver doesn't support your card.

---

### Post by Pumalite on 2007-06-18
> **nutz said:**
> I recommend you stick with the driver from the repositories. Unless that driver doesn't support your card.

I use NVIDIA driver 9755 and it runs great. All you have to do is keep it in /home/<username> and reinstall it every time you update your kernel. BTW, during installation, the driver itself removes old drivers and reconfigure your xorg file. You have to make sure you have: 'make', 'automake', latest gcc, and 'autoconf' as well as kernel-headers matching your kernel. (the latter come with the kernel update ).

---

### Post by ChopperX on 2007-06-18
Well the one from the website. But am i all updated from ubuntu?

---

### Post by Tynach on 2007-06-18
The repositories are the updated ones, as far as I know.

---

