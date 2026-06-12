---
title: "Graphics not working when upgraded to Gutsy"
date: 2008-01-14
forum: Installation &amp; Upgrades
---

### Post by josefs on 2008-01-14
I've finally upgraded to Ubuntu 7.10 from 7.4 but I ran into some problems with the graphics when doing so. I have a nvidia Geforce 8400 and I managed to get it working properly under 7.4. I've tried various tips that I've come across but this has left me in a pretty bad situation. After doing sudo dpkg-reconfigure xserver-org all I get now when I start Ubuntu is a blank screen. From what I've read downloading a driver from nvidia will probably solve my problem. The thing is, I cannot download the driver without having the graphics working at least to some degree since the network I'm connected to requires login via the browser. So what I would like some help with is getting things back to a state where I can actually log in and use my web brower.

Thanks,

Josef

---

### Post by chewearn on 2008-01-14
When you use  sudo dpkg-reconfigure xserver-org, choose nv driver, and set the resolution to match your display.  If nv does work, use vesa.

To install driver from nvidia website, I suggest this:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by PmDematagoda on 2008-01-14
Boot Ubuntu in Recovery Mode and follow the instructions below.

First remove the Nvidia package using:-
```
sudo apt-get purge nvidia-glx-new nvidia-glx
```
After that, remove a few files using:-
```
sudo rm /etc/init.d/nvidia-*
```
and
```
sudo rm /lib/linux-restricted-modules/.nvidia_new_installed
```
Open the modules file for editing using:-
```
sudo nano /etc/default/linux-restricted-modules-common
```
Then add this to the DISABLED_MODULES line to make it look like this:-
```
DISABLED_MODULES="nv nv_new"
```
Then download the Nvidia installer using:-
```
wget http://us.download.nvidia.com/XFree86/Linux-x86/169.07/NVIDIA-Linux-x86-169.07-pkg1.run
```
Execute:-
```
ls
```
to find the name of the downloaded file and execute it(Replace "filename" with the name of the Nvidia installer):-
```
sudo sh filename
```
After that is complete, run:-
```
sudo dpkg-reconfigure xserver-xorg
```
And try:-
```
startx
```

If you see your GUI, your problem has been solved.

---

### Post by josefs on 2008-01-14
I manage to solve the problem by running dpkg-reconfigure xserver-xorg again and selecting the vesa driver instead. From there I could then log in, download and install the new nvidia driver. Things seems to work well now.

---

