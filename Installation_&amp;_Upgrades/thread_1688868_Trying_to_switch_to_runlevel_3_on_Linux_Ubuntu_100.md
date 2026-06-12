---
title: "Trying to switch to runlevel 3 on Linux Ubuntu 10:04"
date: 2011-02-15
forum: Installation &amp; Upgrades
---

### Post by Wakanda on 2011-02-15
Hello.

I'm trying to switch to runlevel 3 on Ubuntu but after I press  ctrl-alt-F3, login and type init 3 it says "need to be root", it says  the same thing when I type init 3 on the terminal.

What do I do? I need to switch to runlevel 3 so I can stop the x server,  unless theres another way to stop the X server without  switching to  runlevel 3?


 I'm trying to temporarily stop the X server so I can  install my Nvidia  Graphics Card drivers, because when I try to install the drivers using  "Hardware Drivers"  it comes up with a system error that says  "SystemError: Failed to fetch cdrom:[Ubuntu 10.10 _Maverick Meerkat_ -  Release i386 (20101007)]/pool/main/d/dkms/dkms_2.1.1.… Disk not found."

So I installed the drivers to my home folder from the Nvidia website but  when I try to "run" the drivers nothing happens so I tried to run the  drivers using the terminal, and it comes up with a error that says    "ERROR: nvidia-installer must be run as root"

Then I tried to install the drivers by pressing ctrl-alt-F3, then I  login and type "sudo ./Nvidia.run" (I believe that's what I type, I  don't 100% remember) and it said that I have to exit/stop the x server.



I'm new to Linux and any help would be much appreciated, thanks.

---

### Post by tommcd on 2011-02-15
First, I prefer using the nvidia drivers from the Ubuntu repos since they are better integrated into the system than the drivers from nvidia.com.
Rather than using the hardware drivers manager, which I have never used, have you tried installing the nvidia driver from synaptic or the terminal?
If you have a gforce 6 or newer card, just install the **nvidia-current** driver from the Ubuntu repos. Then run 
**sudo nvidia-xconfig** to enable the driver. then reboot.

Otherwise, to stop the X server in Ubuntu 9.10 or newer:
```
sudo service gdm stop
```
To restart the X server:
```
sudo service gdm start
```
See this for installing the nvidia driver from nvidia.com on Ubuntu 10.04 or newer:
[http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html)
Hope this helps.
And welcome to the Ubuntu forums!

---

### Post by lisati on 2011-02-15
Thread closed, duplicate of [http://ubuntuforums.org/showthread.php?t=1688882](http://ubuntuforums.org/showthread.php?t=1688882)

---

