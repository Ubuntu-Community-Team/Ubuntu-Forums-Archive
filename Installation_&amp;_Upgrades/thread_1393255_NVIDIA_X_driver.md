---
title: "NVIDIA X driver"
date: 2010-01-29
forum: Installation &amp; Upgrades
---

### Post by Mr Food 101 on 2010-01-29
well just upgraded to 9.10 from hardy and screen doesn't work. Specifically says "not supported" on my tv. So I hooked up to old monitor and thats even off. Cant get into x driver and when I try it says "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server." 
   So I tried nvidia-xconfig and nothing at all. Its like i hit enter. I just want my computer to work with my tv again.

---

### Post by llawwehttam on 2010-01-29
You probably ran it as your user not root.
 
try
```
sudo nvidia-xconfig
```
 
then to restart the x server.
 
```
sudo service gdm restart
```
 
or if its not running
 
```
sudo service gdm start
```

---

### Post by Mr Food 101 on 2010-01-29
derek@CheeseNCrackers:~$ sudo nvidia-xconfig
derek@CheeseNCrackers:~$ 

thats what it does now. In hardy I remember a text thing coming up.

---

### Post by Grenage on 2010-01-29
Make a backup of your old config, reboot, then activate the driver via system/administration/hardware drivers (then reboot):

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.old
```

Then run nvidia-settings as root:

```
gksu nvidia-settings
```

Make your changes, save the config and give it a go.

---

### Post by Mr Food 101 on 2010-01-29
Video works but now sound stopped.


:edit   haha somehow muted it ! Thanx a million

---

