---
title: "Ubuntu 20.04 LTS and Lubuntu 20.04 LTS display issues"
date: 2020-09-09
forum: Installation &amp; Upgrades
---

### Post by keep-tryin on 2020-09-09
I am trying to get 20.04 LTS up and running on an older Machine. The machine ran Lubuntu 18.04 LTS without problems. First I tried booting from the Ubuntu 20.04 LTS Live DVD but the display was unreadable with the image badly distorted and mixed up. Tried the Lubuntu 20.04 LTS Live DVD it installed okay but first thing I noticed was the login box was flashing like crazy. I could log on and do things but periodically the display would become a continuous pattern of repeating lines and I would have to kill X to continue. I thought maybe changing back to lightdm would solve the problem. It does give me a nice screen for login, but continuing to have X crash randomly when doing things like opening LibreOfffice Write or viewing a webpage.  The machine uses the nouveau driver which should be the same as with 18.04 but since it is a NVIDIA GeForce 7025 display I checked to see if I had any display driver options and even tried to install the Nvidia driver NVIDIA-Linux-x86_64-304.137 but it would not compile and when I looked into it, it looks like it is not supported for the newer version of ubuntu. I still have Lubuntu 18.04 on the machine and the display information listed with lshw are identical except 18.04 uses irq 21 and 20.04 uses irq 22 so it probably is some setting for X windows that needs to be changed but I have no idea what to try next. Also on this machine ctrl-alt-F1 does not give a terminal window I had to add the shortcut to /etc/default/keyboard to have a way to terminate X windows.  Any help would be greatly appreciated. 
                Thanks

---

### Post by keep-tryin on 2020-09-24
I installed the xubuntu-desktop with synaptic. It gave a few errors installing but seems to be working much better with the graphics card so I will probably do a clean install of xubuntu to clear up any potential problems from the error messages

---

### Post by gdesilva on 2020-09-24
Have tried booting with nomodprobe switch in the grub command line? LiveDVD probably has a way of specifying this using a function key before you proceed with the boot process.

---

