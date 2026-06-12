---
title: "Computer softlocks after installing graphics drivers"
date: 2016-02-28
forum: Installation &amp; Upgrades
---

### Post by Ncolaprete on 2016-02-28
I've gone through the steps to install ubuntu 15.10 64 bit onto a partition on my boot ssd. I gave it a total of 101 gigs; 20 for my pagefile, 20 for my root dir, 50 for /home, 5 for /tmp, 5 for /var, 512 mb for /boot, and 512 mb for the reserved bios boot sector. I had to set all this up manually myself, since the option to automatically install alongside windows 10 did not show up. Everything seemed to be going smoothly after I got everything said and done, but as soon as I got to install my graphics drivers for my GTX 980, I ran into a huge problem. I rand the command `sudo apt-get install nvidia-current-update` and waited for it to finish, then rebooted. But my computer booted to a black screen with a flashing cursor in the corner and stayed there indefinitely. It only started working again once I booted into safe mode via grub and uninstalled the graphics drivers. How do I go about installing them properly without softlocking my system?

---

### Post by X-RED_Tech on 2016-02-29
The nvidia-current isn't current at all. You need to install the recommended driver version (or higher) for your graphics card which isn't the one you find in the 'current' package (an old 304, I guess).

---

### Post by grahammechanical on 2016-02-29
What Nvidia drivers does Additional Drivers offer? The Nvidia web site is recommending Nvidia 361.28. I have an old adapter that is obsolete by Nvidia's definition. So, Additional Drivers does not offer me the latest, by Ubuntu's standards, Nvidia drivers but I think that Nvidia 361 is available for 15.10 users.

Oh, if we want to do things by the terminal then here are the useful commands

```
ubuntu-drivers list
ubuntu-drivers devices
ubuntu-drivers autoinstall
```

Regards.

---

### Post by Ncolaprete on 2016-02-29
I tried downloading the .run file from nvidia's website, but I came across a whole host of errors trying to install it.

`ubuntu-drivers list` shows I have nvidia-352 and nvidia-352-update installed. How do i properly install version 361.28 from the command line?

The main reason I'm trying to install newer drivers is because my desktop is running extremely slow and laggy when it should be much more responsive.

---

### Post by X-RED_Tech on 2016-02-29
Don't use the file from nvidia.
Instead, add the PPA as mentioned in [http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action) (same instructions but install 361 version):

```
sudo add-apt-repository [B]ppa:graphics-drivers/ppa
[/B]sudo apt-get update && sudo apt-get install **nvidia-361**
```

---

### Post by buzzingrobot on 2016-02-29
352 is the most recent I see in the repos for 15.10, so you do need that PPA.

Follow Nvidia's guidance on deleting the files you installed from their site first, though.

---

### Post by X-RED_Tech on 2016-02-29
Even batter is to reinstall Ubuntu and do it right this time.

---

### Post by Ncolaprete on 2016-02-29
I don't understand how I could possibly "do it right this time" when these drivers were preinstalled as soon as I got into my desktop.

---

### Post by X-RED_Tech on 2016-02-29
The only preinstalled driver relevant for your graphics card is the open source nouveau which unfortunately has no support for the new GTX980. So, doing it right means reinstall Ubuntu, add the nomodeset parameter to grub if needed to have have some sort of video then follow the instructions in post #5 and nothing else. In other words, it's the same that you (apparently) did before but using the correct nvidia driver version, not an old one, not the file directly from nvidia. Shouldn't be that hard to understand.

---

### Post by deadflowr on 2016-02-29
> **Ncolaprete said:**
> I don't understand how I could possibly "do it right this time" when these drivers were preinstalled as soon as I got into my desktop.
Whether a driver is installed or not is moot if the system isn't using them.
I think nvidia needs them to be configured for use.
try
```
sudo nvidia-xconfig
```
then restart X or reboot the system, which will restart X along with everything else.

---

