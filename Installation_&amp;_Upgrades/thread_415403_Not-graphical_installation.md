---
title: "Not-graphical installation"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by Martje_001 on 2007-04-20
Hi,
How do I perform a not-graphical installation using ubuntu 7.04? I want to install ubuntu, and then install nvidia drivers because the video-cart doesn't work by default.

Thanx!

---

### Post by bwitherell on 2007-04-20
Try installing the Ubuntu 7.04 server distro instead of using the Desktop distro. The Server distro does not come with a GUI. Also keep in mind that if you install without a GUI it might be more difficult to install the GUI later on. Instead you might try looking into installing Ubuntu with the GUI but then start it in a differnt run level.

---

### Post by madmetal on 2007-04-20
download the alternate cd and install ubuntu from this..
its non graphical installation and when its installed you got gnome..
its the best for avoiding problems..

---

### Post by tanari on 2007-04-20
I can't install from alternate cd, after choosing install I just see black screen and "_" :(

---

### Post by zvacet on 2007-04-20
Install Ubuntu with GUI,and when you are finish 

```
sudo /etc/nint.d/gdm stop
```

After that 

```
 sudo dpkg-reconfigure xserver-xorg
```

Set your video card(maybe choose **nv** instead of **nvidia**)

and if you want GUI back 

```
sudo /etc/init.d/gdm start
``` 

or

```
sudo /etc/init.d/gdm restart
```

---

### Post by tanari on 2007-04-22
i can't install it with any cd (desktop or alternate), 
I have installed edgy and upgraded to feisty, but after grub i see only black screen

---

