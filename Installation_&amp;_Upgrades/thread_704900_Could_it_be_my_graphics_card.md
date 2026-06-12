---
title: "Could it be my graphics card?"
date: 2008-02-22
forum: Installation &amp; Upgrades
---

### Post by kcdude on 2008-02-22
I've been trying to find a way to install Ubuntu 7.10 on this system for a very long time now but have had no luck because once the load screen is finished, all that is left is a black screen. I was thinking it is because I have a graphics card that Ubuntu may not support, it's an older NVIDIA GeForce 5500 FX. After having that trouble, I tried installing in "Safe Graphics Mode" but all that happens is a few lines pop up and then it freezes up and does not continue. I know it is not a bad installation disk because I have downloaded Ubuntu several times and have tried several disks, I even used this disk to install it on a separate machine, it is just this computer that is having the trouble. The computer itself is old as well (HP, Pentium 3, 256 ram, 40GB hard drive.) Any help getting this thing to boot/install is appreciated!

UPDATE-Just so you all know, the screen is blank BEFORE the "X" appears, but after the loading screen.

---

### Post by taurus on 2008-02-22
Try using the alternate CD instead.  I have a GeForce 5600 and didn't have any problem with the alternate CD and the nvidia driver in System -> Administration -> Restricted Drivers Manager (after you've installed it on your harddrive).

---

### Post by djhnsmn on 2008-02-22
I had a simalar problem with a new everex machine. Try loading a earlier version of ubuntu, if that works then simply upgrade

---

### Post by kcdude on 2008-02-23
> **taurus said:**
> Try using the alternate CD instead.  I have a GeForce 5600 and didn't have any problem with the alternate CD and the nvidia driver in System -> Administration -> Restricted Drivers Manager (after you've installed it on your harddrive).
I got it installed on the computer using the alternate CD, although now it boots and I'm getting the same problem after the load screen...a blank black screen. I don't know how I'm supposed to enable the NVIDIA drivers when I can't see anything. Is there a way to boot Ubuntu in safe graphics mode? Thanks again.

---

### Post by ShodanjoDM on 2008-02-23
This is where the CLI comes handy.

If you can't see the gdm login screen, reboot the pc. Then during the GRUB loading, press esc. There should be a recovery (non graphical) mode.

Choose it and let it runs, enter username and login password, then you'll see a command prompt.

type:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.bak
```

to make a backup of the xorg.conf file.

Then this is the 1st option you can do:

```
sudo dpkg-reconfigure xserver-xorg
```

When you get to Video driver configuration screen, choose Vesa. It is the standard, non accelerated video driver. Restart & if you can login via gdm, then you can install the nvidia driver to get 3D acceleration.

OR the 2nd option (to install nvidia driver directly if that PC is connected to the internet). At the command prompt, type:

```
sudo aptitude install nvidia-glx
```

Hope that helps.

---

