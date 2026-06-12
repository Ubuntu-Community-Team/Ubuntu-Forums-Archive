---
title: "Ubuntu black screen after upgrade from 12.04 to 14.04"
date: 2014-08-25
forum: Installation &amp; Upgrades
---

### Post by sebi2 on 2014-08-25
I've upgraded from ubuntu 12.04 to 14.04. There were display  driver issues and I could only work in a terminal. I have installed the  nvidia drivers from:

[http://www.nvidia.com/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86_64/340.32/NVIDIA-Linux-x86_64-340.32.run&lang=us&type=geforcem](http://www.nvidia.com/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86_64/340.32/NVIDIA-Linux-x86_64-340.32.run&lang=us&type=geforcem)

 During the installation there seemed to be some conflicts with the  existing installations nvidia-304* and was prompted to remove them and  install the new drivers instead. Now, when I reboot the nvidia logo  flashes a few times then nothing happens;  there is a cursor on the top  left of the display.

  Typing:
  ```
Ctrl + Alt + F1

```  does not produce any result. I have dropped into the recovery mode root console and have  tried to remove all nvidia installations by running:
  ```
sudo apt-get autoremove nvidia-304*
sudo apt-get --purge remove nvidia-304*

```  The following is displayed:
  ```
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt
E: The package lists or status file could not be parsed or opened.

```  Also, networking is disabled. 
Running:

```
dpkg -l | grep nvidia 
```

shows that **nvidia-common**, **nvidia-settings **and **nvidia-settings-304** are installed.

Running:

```
grep -i "x driver" /var/log/Xorg.0.log
```

outputs:

```
[  9.224] (II) NVIDIA dllloader X Driver 340.32
``` 

How is it possible to reinstall the drivers in order to get the display back?

---

### Post by kansasnoob on 2014-08-25
In recovery mode you need to enable networking first to get read/write privileges before selecting to use the root terminal. Hope that helps a little.

---

### Post by sebi2 on 2014-08-25
If I boot from an older kernel version I can get into the console by starting in recovery mode and there enabling networking. 

GRUB displays the following on boot:

```

*Ubuntu
  Advanced options for Ubuntu
  Memory test (memtest86+)
  Memory test (memtest86+, serial console 115200)

```

I'm assuming that the first entry boots the latest version of the  kernel. When selecting the "Advanced options for Ubuntu" the following  entries are displayed:

```

Ubuntu, with Linux 3.13.0-34-generic
Ubuntu, with Linux 3.13.0-34-generic (recovery mode)
Ubuntu, with Linux 3.5.0-54-generic
Ubuntu, with Linux 3.5.0-54-generic (recovery mode)
Ubuntu, with Linux 3.5.0-47-generic
Ubuntu, with Linux 3.5.0-47-generic (recovery mode)
Ubuntu, with Linux 3.5.0-46-generic
Ubuntu, with Linux 3.5.0-46-generic (recovery mode)
Ubuntu, with Linux 3.5.0-44-generic
Ubuntu, with Linux 3.5.0-44-generic (recovery mode)
Ubuntu, with Linux 3.5.0-42-generic
Ubuntu, with Linux 3.5.0-42-generic (recovery mode)
Ubuntu, with Linux 3.5.0-41-generic
Ubuntu, with Linux 3.5.0-41-generic (recovery mode)
Ubuntu, with Linux 3.5.0-40-generic
Ubuntu, with Linux 3.5.0-40-generic (recovery mode)
Ubuntu, with Linux 3.5.0-23-generic
Ubuntu, with Linux 3.5.0-23-generic (recovery mode)

```

When trying to boot from the first option the screen freezes; Ctrl + Alt  + F1 no longer work. When I launch the first option in recovery mode I  can only drop to the root shell. Trying to enable networking freezes up  the box. 
When booting from the last option "Ubuntu, with Linux 3.5.0-23-generic  (recovery mode)" I can get networking to work. However, when I type Ctrl  + Alt + F7 the GUI  does not show. However, input is recognized and I  can revert to console mode. I have managed to uninstall all Nvidia  drivers. Even without these shouldn't I be able to launch the GUI?

---

### Post by sebi2 on 2014-08-25
If I boot from an older kernel version I can get into the console by starting in recovery mode and there enabling networking. 

GRUB displays the following on boot:

```

*Ubuntu
  Advanced options for Ubuntu
  Memory test (memtest86+)
  Memory test (memtest86+, serial console 115200)
[CODE]

I'm assuming that the first entry boots the latest version of the  kernel. When selecting the "Advanced options for Ubuntu" the following  entries are displayed:

[CODE]
Ubuntu, with Linux 3.13.0-34-generic
Ubuntu, with Linux 3.13.0-34-generic (recovery mode)
Ubuntu, with Linux 3.5.0-54-generic
Ubuntu, with Linux 3.5.0-54-generic (recovery mode)
Ubuntu, with Linux 3.5.0-47-generic
Ubuntu, with Linux 3.5.0-47-generic (recovery mode)
Ubuntu, with Linux 3.5.0-46-generic
Ubuntu, with Linux 3.5.0-46-generic (recovery mode)
Ubuntu, with Linux 3.5.0-44-generic
Ubuntu, with Linux 3.5.0-44-generic (recovery mode)
Ubuntu, with Linux 3.5.0-42-generic
Ubuntu, with Linux 3.5.0-42-generic (recovery mode)
Ubuntu, with Linux 3.5.0-41-generic
Ubuntu, with Linux 3.5.0-41-generic (recovery mode)
Ubuntu, with Linux 3.5.0-40-generic
Ubuntu, with Linux 3.5.0-40-generic (recovery mode)
Ubuntu, with Linux 3.5.0-23-generic
Ubuntu, with Linux 3.5.0-23-generic (recovery mode)

```

When trying to boot from the first option the screen freezes; Ctrl + Alt  + F1 no longer work. When I launch the first option in recovery mode I  can only drop to the root shell. Trying to enable networking freezes up  the box. 
When booting from the last option "Ubuntu, with Linux 3.5.0-23-generic  (recovery mode)" I can get networking to work. However, when I type Ctrl  + Alt + F7 the GUI  does not show. However, input is recognized and I  can revert to console mode. I have managed to uninstall all Nvidia  drivers. Even without these shouldn't I be able to launch the GUI? 

EDIT:

Apparently I can access the bash window only when the nvidia drivers are unistalled. I wonder why.

---

