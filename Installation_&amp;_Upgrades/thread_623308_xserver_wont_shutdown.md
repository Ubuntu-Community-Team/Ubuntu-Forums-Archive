---
title: "xserver wont shutdown"
date: 2007-11-25
forum: Installation &amp; Upgrades
---

### Post by R.E.A.D on 2007-11-25
I am a fairly new user to linux in general but i know a lil bit. i just did a fresh install of gutsy 7.10 64 bit and am trying to install nvidia driver for my geforce 7600gs but every time i try to shutdown the xserver it kinda works and then i start the install via (sh NVIDIA(blablabla) and it says the xserver is not shut down iv tried multiple ways of doing it but i cannot figure it out plz help.](*,)

---

### Post by Pumalite on 2007-11-25
Did you try:
Ctrl+Alt+F1
username
password
sudo /etc/init.d/gdm stop
sudo sh /pathtodriver/NVIDIA...
sudo /etc/init.d/gdm start
?

---

### Post by R.E.A.D on 2007-11-25
yes ,but i only got as far as sh pathtodriver/NVIDIA then it said that the xserver wasn't shutdown and rebooted:confused:

---

### Post by R.E.A.D on 2007-11-25
nvm my uncle came over and helped me fix it thx for the input though for 15 i think im doin pretty well

---

### Post by Unknowndady on 2008-01-03
> **R.E.A.D said:**
> nvm my uncle came over and helped me fix it thx for the input though for 15 i think im doin pretty well

Hehe, Im having the same problem , mind asking your uncle how he did it?

---

### Post by ~LoKe on 2008-01-03
Try...
```
sudo killall gdm
```

---

### Post by Pumalite on 2008-01-03
This, form post # 2 should have stopped it:
sudo /etc/init.d/gdm stop

---

### Post by Unknowndady on 2008-01-03
Ok installed driver, now Im getting a message saying 

"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. "

I did the "sudo nvidia-xconfig" but what is the code to restart the x server?

Oh and I love your sig. Pumalite

---

### Post by ~LoKe on 2008-01-03
> **Unknowndady said:**
> Ok installed driver, now Im getting a message saying 

"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. "

I did the "sudo nvidia-xconfig" but what is the code to restart the x server?

Oh and I love your sig. Pumalite

To restart the xserver:
```
sudo /etc/init.d/gdm restart
```
To use the nvidia driver...
```
sudo nano /etc/X11/xorg.conf
```
Search for driver and change it from nv to nvidia.

---

### Post by Unknowndady on 2008-01-03
Hmmmm, it already had nvidia there - not sure whats the problem

```

Section "Device"
        Identifier      "nVidia Corporation G80 [GeForce 8600 GT]"
        Driver          "nvidia"
        BusID           "PCI:5:0:0"
        Option          "UseFBDev"              "true"
```

---

### Post by ~LoKe on 2008-01-03
That's odd.  Try this:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Pumalite on 2008-01-03
Go to System>Administration>Restricted Drivers and enable them.

---

### Post by Unknowndady on 2008-01-03
Ok well It wont let me enable the restriced drivers I get this message

```
The software source for the package

   nvidia-glx-new

 is not enabled.
```

and when I put "sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup" into the terminal nothing happened 

but then when I put "sudo dpkg-reconfigure -phigh xserver-xorg" int the terminal It came back with 

```
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080103151220
```

---

### Post by Pumalite on 2008-01-03
If you have an Nividia 7600 or superior:
sudo apt-get install nvidia-glx-new
Then try again.

---

### Post by Unknowndady on 2008-01-03
Hmm, looks like its not there


```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx-new is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package nvidia-glx-new has no installation candidate

```

---

### Post by Pumalite on 2008-01-03
At your Terminal run:
glxgears
And tell me what you see.

---

### Post by Unknowndady on 2008-01-03
I got 

```
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual
```

also thanks for helping me guys :D

---

### Post by Pumalite on 2008-01-03
Run:
sudo apt-get install buid-essential
Install your driver again:
Accept the License
Let it configure your module into your kernel
Let it modify your xorg.conf file
sudo /etc/init.d/gdm start
Check your Restricted Drivers again.

---

### Post by Unknowndady on 2008-01-03
When doing 
"sudo apt-get install buid-essential"
I get

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package buid-essential
```

---

### Post by Pumalite on 2008-01-03
Post your /etc/apt/sources.list:
cat /etc/apt/sources.list

---

### Post by Unknowndady on 2008-01-03
This is what I got from 
"cat /etc/apt/sources.list"

```

deb http://archive.ubuntu.com/ubuntu/ gutsy main
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://archive.ubuntu.com/ubuntu/ gutsy restricted
deb http://archive.ubuntu.com/ubuntu/ gutsy universe
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
```

---

### Post by Pumalite on 2008-01-03
Comment out the 'deb-src' ones (put a # in front)
Backup you file first.
Then try again.
(you cannot have installed your driver without build-essential installed)
Change Server too.

---

### Post by Unknowndady on 2008-01-03
Ok I tried it again after Commenting out those two lines and it gave me this 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package buid-essential
```

---

### Post by ~LoKe on 2008-01-03
> **Unknowndady said:**
> Ok I tried it again after Commenting out those two lines and it gave me this 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package buid-essential
```

build-essential not buid.

---

### Post by Pumalite on 2008-01-03
Whoops, my mistake...sorry.

---

### Post by Unknowndady on 2008-01-03
Np, It worked out in the end 

Got it working , I'm very happy now
Thanks guys

Also Im using Pyrolinux
located 
[http://www.pyrolinux.com/](http://www.pyrolinux.com/)
If you want to try it out, its hardly different from Ubuntu, just more beautiful.

---

### Post by ~LoKe on 2008-01-03
> **Unknowndady said:**
> Np, It worked out in the end 

Got it working , I'm very happy now
Thanks guys

Also Im using Pyrolinux
located 
[http://www.pyrolinux.com/](http://www.pyrolinux.com/)
If you want to try it out, its hardly different from Ubuntu, just more beautiful.

The screenshots make it look like Ubuntu with an ugly GTK theme and AWN.

---

### Post by Unknowndady on 2008-01-03
Hehe the screen shot are terrible, they are suppose to put a video up soon of it.
Since a thousands words can't really be used in this case.

My Video Drivers were working until I restarted, going to try to install again and see if they work after a restart.

---

### Post by Unknowndady on 2008-01-04
Hey I'm having a problem now, everytime I restart I have to re-install the Nvidia Drivers, and I can not enable the Extra Visual/Desktop features, also Nvidia X server Settings gives me this again

"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. "

But It does say that the Nvidia accelerated graphics driver is enabled.

---

