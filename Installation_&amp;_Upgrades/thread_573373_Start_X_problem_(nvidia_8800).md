---
title: "Start X problem (nvidia 8800)"
date: 2007-10-11
forum: Installation &amp; Upgrades
---

### Post by orrie on 2007-10-11
I have a XFX Geforce 8800 Ultra 768 MB and I', trying to install the drivers to this card.
I have tried much (envy, manual installation etc.) and nothing works.
When I trying to boot my Ubuntu then the screen just goes black and I can't press ALT+CTRL+F2, CTRL+ALT+DEL to get out of the "black screen".
But in recovery mode does it work; there I can access X without any problems.

One of the steps I have tried is:
# apt-get install build-essential
# apt-get install xserver-xorg-dev
# nano /etc/default/linux-restricted-modules*
DISABLED_MODULES="" changed to DISABLED_MODULES="nv"
Rebooted.
/etc/init.d/gdm stop
sh NV*
Been running through the NVIDIA-installer and the NVidia-settings I can access in recovery mode without any problems at all..

How to fix this?

---

### Post by reckless2k2 on 2007-10-11
are you trying to install this from binary or through the restricted drivers menu?

---

### Post by orrie on 2007-10-11
I have downloaded the drivers and installed it through NVIDIA-*.run.
And, I actually tried to install it from restricted manager for a couple of minutes ago, but then the same problem accourd..


-- My specs --
8800 Ultra
AMD Athlon 64 6000+
2g Corsair DDR

---

### Post by schwiz on 2007-10-11
I am having this same problem, I am a first time linux user so I don't have any idea what I am doing.  I put in the live CD and when I try to boot after it loads I get a blank screen.  here are my specs

Q6600 @ 3Ghz
EVGA 680i
8800 Ultra
3 250g WD Caviar in RAID 0
4g Corsair DDR2 800
X-fi fatal1ty professional 
3DAurora Chassis

---

### Post by Ub1476 on 2007-10-11
> I am having this same problem, I am a first time linux user so I don't have any idea what I am doing. I put in the live CD and when I try to boot after it loads I get a blank screen. here are my specs

First enter the terminal by pressing Alt+Ctrl+F1, then edit xorg.conf:

```
sudo gedit nano /etc/X11/xorg.conf
```

Go t the "advice" section (above the monitor section) and change the driver to Vesa.
Press Alt+F2, save and exit.

Now start GDM

```
sudo killall gdm
sudo gdm
```

Install Ubuntu and apply the restricted drivers for your graphic card (System>Administration>Restriced Driver Manager).

This works for most nvidia cards:)

> I have a XFX Geforce 8800 Ultra 768 MB and I', trying to install the drivers to this card.
I have tried much (envy, manual installation etc.) and nothing works.
When I trying to boot my Ubuntu then the screen just goes black and I can't press ALT+CTRL+F2, CTRL+ALT+DEL to get out of the "black screen".
But in recovery mode does it work; there I can access X without any problems.

One of the steps I have tried is:
# apt-get install build-essential
# apt-get install xserver-xorg-dev
# nano /etc/default/linux-restricted-modules*
DISABLED_MODULES="" changed to DISABLED_MODULES="nv"
Rebooted.
/etc/init.d/gdm stop
sh NV*
Been running through the NVIDIA-installer and the NVidia-settings I can access in recovery mode without any problems at all..

How to fix this?

RDM should work (do a apt-get update/grade before installing drivers). If it doesn't you can post your xorg.conf here.

---

### Post by orrie on 2007-10-11
I have just fixed the problem by using [this guide]("https://help.ubuntu.com/community/NvidiaManual") :D

---

### Post by schwiz on 2007-10-11
> 
First enter the terminal by pressing Alt+Ctrl+F1, then edit xorg.conf:

Code:

sudo gedit nano /etc/X11/xorg.conf

Go t the "advice" section (above the monitor section) and change the driver to Vesa.
Press Alt+F2, save and exit.

Now start GDM

Code:

sudo killall gdm
sudo gdm

Install Ubuntu and apply the restricted drivers for your graphic card (System>Administration>Restriced Driver Manager).

This works for most nvidia cards


When I press ctrl+alt+f1 it doesn't do anything still a blank screen...

---

### Post by overlord.gaurav on 2007-10-11
I have nVidia 8800 GTS. 
I have the same problem as you guys.

Basically, the kernel isn't compiled properly.
What I noticed was: Difference in the actual version of the driver and the version stated in the kernel.
I tried installing the drivers using the official nvidia drivers from the nvidia site,  twice.
And I got the same problem both the times.

Both of these times, I used [Envy]("http://albertomilone.com/nvidia_scripts1.html") to install my drivers and it worked like a wonder for me.

---

### Post by nzadLithium on 2007-10-11
schiwz wen grub comes up select the second ubuntu option.

When its finished you should now have a terminal.

login

run sudo passwd

setup your 'root' password

now run 

sudo apt-get install nvidia-glx-new

sudo nvidia-xconfig

sudo shutdown -r now

Then use the normal option to boot ubuntu.

Hopefully you'll have an xserver

---

### Post by overlord.gaurav on 2007-10-12
> 
sudo apt-get install nvidia-glx-new
I had even tried this, it didn't work me.

---

### Post by nzadLithium on 2007-10-13
did you do every single thing that i wrote?

and what do you mean it didnt work? do you mean the command failed?

---

### Post by orrie on 2007-10-15
When you get the bootscreen, try to press the [E] button and edit the line where it stands kernel .... ro quiet splash

The problem with the blank/black screen is that the OS is trying to boot and load the splash, and it is there it's failing..
Just remove the splash by doing what I said above and it should work smoothly :)

---

### Post by nzadLithium on 2007-10-15
I'm glad someone on these forums has got the newest nvidia card to go :) The newest card I have setup is the 8600 and that didn't need any fiddling with boot options :D

---

