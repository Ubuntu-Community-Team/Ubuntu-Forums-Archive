---
title: "Installed Ubuntu 10.10 Using Wubi - Can't Access GUI"
date: 2011-01-13
forum: Installation &amp; Upgrades
---

### Post by Flood-X on 2011-01-13
Installed Ubuntu 10.10 Using Wubi - Can't Access GUI

Hello everyone,

First, let me say that I'm new to Ubuntu and this is the first time I've tried installing it on my desktop PC. My PC specs are as follows:
Operating System:	MS Windows XP Professional 32-bit SP3
CPU:	Intel Celeron 336, 2.80 GHz, Prescott 90nm Technology
RAM:	1.0GB Single-Channel DDR @ 165MHz (2.5-4-4-7)
Motherboard:	MICRO-STAR INTL, CO.,LTD. MS-7108 (Socket 478)
Monitor:	LG-T711S @ 1024x768
Graphics Card:	128MB NVIDIA GeForce FX 5200 (XFX Pine Group)
Hard Drives:	78GB Western Digital WDC WD800JD-00MSA1 (SATA)
Optical Drives:	Samsung TSSTcorp CDDVDW SH-S223C
Audio:	Realtek AC'97 Audio

I installed using Ubuntu 10.10 LiveCD Wubi (to install and unistall Ubuntu from Windows).

I ran the Wubi install. After completing, it tells you that you need to restart your PC. I restarted and chose Ubuntu from the OS choices. I then clicked escape to access the options list and chose the Safe Graphics Mode install option. I did so because when it tries to install in the normal mode, I can't see what's going on. I get a message from my monitor saying "out of frequency range" when I use the normal mode install. Whereas in the Safe Grahpics Mode I see what's going on during the install and the progress of the installation. Upon completing the installation, the system reboots. I then chose again Ubuntu from the OS options. After that, I get a screen (GRUB) allowing to to choose generic (default) or generic restoration mode of boot. If I choose the default I don't get a GUI. I just get a text prompt asking for my username and password. When I enter them, I am logged in, but at a text prompt.

So I tried to get to the GUI using: startx

I got the following errors:
(EE) VESA: Kernel modesetting driver in use is refusing to load
(EE) No devices detected

Fatal server error: no screens found
ddxSigGiveUp: Closing log
xinit: No such file or directory (erno 2): unable to connect to X server
xinit: No such process (erno 3): Server error

If I try Ctrl-Alt-F7, I get some standard log messages, none of which indicate an error, but it never enters the Ubuntu GUI desktop.

If I try: sudo service gdm start
or: sudo start gdm

I get:
start: Job is already running: gdm

Could anyone help? Thank you a lot.

---

### Post by Rubi1200 on 2011-01-13
Hi and welcome to the forums :)

You could try this from safe mode or recovery mode:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bad

sudo dpkg-reconfigure -phigh xserver-xorg

```

---

### Post by Flood-X on 2011-01-13
After choosing recovery mode, I get a list of options of different possible ways to continue. I wasn't sure which mode to choose to enter the commands you suggested so I chose the netroot (or rootnet, I can't remember now). Then I entered the two commands on the prompt and reset the computer. It seems I was able then to access the GUI but I had the problem of the monitor being out of frequency. So I reboot and entered into recovery mode and chose the failsafe mode. This time I was able to login to the GUI and see it. Then the system gave me a recommendation to download the nvidia drivers and activate them. So I did so and reboot, and now I can login to the GUI.

Thank you so much for your help.

---

### Post by Rubi1200 on 2011-01-14
Excellent! I am glad you got it sorted out.

Enjoy and feel free to ask here anytime you need help.

---

