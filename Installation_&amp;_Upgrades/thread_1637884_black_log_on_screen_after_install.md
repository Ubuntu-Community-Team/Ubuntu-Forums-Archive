---
title: "black log on screen after install"
date: 2010-12-05
forum: Installation &amp; Upgrades
---

### Post by inspace2035 on 2010-12-05
im need help like many others . after install i tried to install my video .witch happens to be nvidia. and of course after reboot i now get a black screen showing login and password but it will not work i can only get in through recovery.  i have a nvidia ge force 9500gt please help i tried to look for solution but just need help? thanks

---

### Post by sikander3786 on 2010-12-05
Welcome to the forums :-)

Try restarting GDM.

```
sudo service gdm stop
```

```
sudo service gdm start
```

If that doesn't bring up the graphical stuff, try reconfiguring your graphics.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

It might throw an error like "No such file or directory" or "File not found", no problem. Proceed to the next one.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Reboot.

```
sudo shutdown -r now
```

See if it takes you to the desktop now.

If not, you might need to remove, purge and reinstall the Nvidia drivers.

```
sudo apt-get remove --purge nvidia-current nvidia-common nvidia-settings
```

Reboot and if it takes you to the desktop, re-install the drivers from System > Administration > Additional Drivers/Hardware Drivers.

Good Luck!

---

### Post by inspace2035 on 2010-12-05
tried step #6 said it worked saying it removed it .  then i did a reboot still can not get in reboot takes me to black screen asking username and password      then welcome to ubuntu all in black.  other that recovery mode should i just remove then reinstall and not intall  nvidia. or is there a fix ????? all was fine till that install????  thank you !!!!

---

### Post by wannacme16 on 2010-12-05
I've had similar problems with NVIDIA and ATI as well. I don't use the factory installed NVIDIA card but use an ATI card without installing any drivers, if I install any drivers black screen at reboot. Similar with NVIDIA card. With NVIDIA card I cant use 3d desktop but can login into desktop. With ATI card I can login and experience full 3d desktop without the need of any drivers. Don't figure but my experience, might be an issue, don't know. All I know is if I install any drivers NVIDIA or ATI I get a black screen at reboot. Hope this might help.

---

### Post by sikander3786 on 2010-12-06
> **inspace2035 said:**
> tried step #6 said it worked saying it removed it .  then i did a reboot still can not get in reboot takes me to black screen asking username and password      then welcome to ubuntu all in black.  other that recovery mode should i just remove then reinstall and not intall  nvidia. or is there a fix ????? all was fine till that install????  thank you !!!!
Please post the output of,

```
cat /etc/X11/xorg.conf
```

```
sudo service gdm start
```

---

### Post by inspace2035 on 2010-12-06
cat: /ext/XLL/xorg.conf: No such file or directory

---

### Post by inspace2035 on 2010-12-06
start: Job is already running: gdm     after second code. thanks

---

