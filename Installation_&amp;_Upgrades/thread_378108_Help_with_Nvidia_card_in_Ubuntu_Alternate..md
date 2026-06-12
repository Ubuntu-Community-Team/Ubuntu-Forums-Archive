---
title: "Help with Nvidia card in Ubuntu Alternate."
date: 2007-03-06
forum: Installation &amp; Upgrades
---

### Post by elitelinuxnoob on 2007-03-06
I finally got the Alternate to work and installed with no problems.

Except one thing I am still getting a gray bar across my screen just like I did in 6.10 desktop LiveCD and Kbuntu liveCD. I get the to the login screen and login and then I get the  bar across my screen that looks like the top part of a window. 

I tried the "chroot /root nano etc/x11/xorg.conf" but it says, "cannot change root directory to /root: Operation not permitted."

So how do I get in this etc/x11/xorg.conf the correct way and is this how I change my graphics driver to the "Vesa?" Once I get in then what do I do. Please be descriptive because im new to linux

Oh guys I can feel it, im so close to getting Ubuntu operating normally and with your help it should be very soon so please I apreciate everything guys.

---

### Post by seldenthuis on 2007-03-06
If you want to edit your Xorg configuration file you should use: ```
sudo nano /etc/X11/xorg.conf
```
Then look for the part that looks something like:
```

Section "Device"
    Identifier "Name of your graphics card"
    Driver     "nv"
    BusID     "PCI:1:0:0"
EndSection

```
To use the Vesa driver you have to change the line ```
Driver     "nv"
``` to ```
Driver     "vesa"
```

The fact that you're seeing a gray bar across your screen might just mean that Xorg is using the wrong resolution or refresh rate for your monitor. If you post the contents of your xorg.conf and give us some details about your graphics card and monitor, we might be ale to get the Nvidia driver working.

---

### Post by elitelinuxnoob on 2007-03-06
All I see in /etc/x11/xorg.conf is a blank black screen with a blinking cursor with Get Help, Write Out, Read File, Prev Page, Cut text, Cur Pos, Exit, Justify...etc. 
Im so lost, am I in the right place? I see nothing about Device Drivers.

---

### Post by skiforfun on 2007-03-06
> You have to type sudo cp /etc/**X**11/xorg.conf,otherwise your file doesn't exist.

But back to your problem,if you can boot into recovery mode and login in your console,try the next command.
Code:

sudo dpkg-reconfigure xserver-xorg

and choose the desired resolution for your monitor.

Thats from my other thread, I have another problem with my nvidia card, remember its a big X and not the small one.

---

### Post by elitelinuxnoob on 2007-03-06
> **skiforfun said:**
> Thats from my other thread, I have another problem with my nvidia card, remember its a big X and not the small one.

I tried the sudo cp /etc/X11/xorg.conf and it says "Try 'cp--help' for more info." 

Is Ctrl, Alt, F1 the only way to get into the command prompt?


But I did try sudo dpkg-reconfigure xserver-xorg and I was able to select the Vese driver. There were a lot of things it asked for me to change but I just said ok on all of them. I am happy I got Ubuntu to work now so now I can see the desktop and open progams but the VESA driver make movement of windows and scrolling up/down in webpages very slow to update. How can I make it normal again and use the regular Nvidia driver? I want to try games next so I know this Vesa wont cut it.

thank you very much

---

### Post by po0f on 2007-03-07
elitelinuxnoob,

To make a backup xorg.conf:

```
$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

To install NVIDIA drivers:

```
$ sudo apt-get update
$ sudo apt-get install nvidia-glx
```

---

### Post by elitelinuxnoob on 2007-03-07
> **po0f said:**
> elitelinuxnoob,

To make a backup xorg.conf:

```
$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

To install NVIDIA drivers:

```
$ sudo apt-get update
$ sudo apt-get install nvidia-glx
```

Ok thank you sir and how do I do sudo cp /etc/X11/xorg.conf and it says "Try 'cp--help' for more info." How come I couldn't see anything in the xorg.conf? i just want to know so next time I do it the right way to get vesa drive. just a backup way to get the vesa driver.
thankyou

---

### Post by orb9220 on 2007-03-07
> How come I couldn't see anything in the xorg.conf?

That is the copy command and is incomplete,the right way is: sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

> All I see in /etc/x11/xorg.conf is a blank black screen

That is because /x11/ shoud have Bee /**X**11/ capital X

---

