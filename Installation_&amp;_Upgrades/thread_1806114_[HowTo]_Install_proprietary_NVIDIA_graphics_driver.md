---
title: "[HowTo] Install proprietary NVIDIA graphics drivers from restricted repo"
date: 2011-07-17
forum: Installation &amp; Upgrades
---

### Post by szal on 2011-07-17
**Preliminary remarks.** As this question pops up quite often on IRC and, as a quick search told me, on this board as well, I decided to put together some directions that, with some or the other variation, also apply to other Linux distributions and have never failed me. The following is confirmed to work for Kubuntu 11.04 “Natty Narwhal” 64bit with a NVIDIA GeForce GT 240 and on Kubuntu 11.04 “Natty Narwhal” 32bit with a NVIDIA GeForce FX 5900XT graphics card.

This HowTo will describe how to install the proprietary NVIDIA graphics card drivers using exclusively the command line. _I strongly suggest you try this method for a fresh install of graphics drivers before trying any other method_, especially a GUI-driven one (I never used a GUI for package management on a Debian-ish system, but I hear that the Ubuntu Software Center supposedly has a way of installing proprietary graphics drivers).

The restricted packages repository should be enabled by default.

To the more experienced users: This HowTo uses ‘apt-get’ for demonstrating the install process. If you prefer using ‘aptitude’, feel free to replace the commands accordingly.



**First steps.** As we’ll be doing everything on the command line, first open a terminal application from your desktop environment’s menu or from a shortcut icon on your panel, if you have one. You should be greeted by a *prompt* that looks like this:
```
username@machinename:~$
```with [COLOR=Green]~[COLOR=Black] signifying your currently logged in user’s home directory ([COLOR=Green]/home/username/[COLOR=Black]) and [COLOR=Green]$[COLOR=Black] stating that you have no special privileges.

[/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR]Know your graphics card! If you’re not 100% sure what graphics card is in your machine, find out by issuing the following command:
```
username@machinename:~$ lspci -k
```This returns all devices that are connected to your machine’s PCI bus. Scroll to find the entry that describes your graphics card; it should look similar to this one:
```
02:00.0 VGA compatible controller: nVidia Corporation GT215 [GeForce GT 240] (rev a2)
        Subsystem: CardExpert Technology Device 0401
        Kernel driver in use: nvidia
        Kernel modules: nvidia-current, nouveau, nvidiafb
```In this example the proprietary NVIDIA driver is already installed (“Kernel driver in use: nvidia”). If the NVIDIA driver is not installed, it will most likely show “nouveau” as being used.

**Which driver to choose?** Ubuntu offers three different NVIDIA driver packages: [COLOR=Green]nvidia-current[/COLOR], [COLOR=Green]nvidia-173[/COLOR], and [COLOR=Green]nvidia-96[/COLOR]. These are for the following NVIDIA graphics cards:


[LIST]
[*][COLOR=Green]nvidia-current[/COLOR]: for GeForce 6 series (6xxx), GeForce 7 and GeForce Go 7 series (7xxx), GeForce 8 and 8M series (8xxx), GeForce 9 and 9M series (9xxx), GeForce 100 and 100M series (1xx), GeForce 200 and 200M series (2xx), GeForce 300 and 300M series (3xx), GeForce 400 and 400M series (4xx), GeForce 500 and 500M series (5xx). As far as I can see, this is also the driver to choose if you happen to run a Quadro graphics card (except Quadro 2 Pro and Quadro 2 MXR).
[*][COLOR=Green]nvidia-173[/COLOR]: for GeForce FX series (FX 5xxx).
[*][COLOR=Green]nvidia-96[/COLOR]: for GeForce 4 MX and Ti series, GeForce 3 series.
[/LIST]

GeForce 2, GeForce 256, TNT, TNT2 and Riva graphics cards would require an even older driver, the installation of which is outside the scope of this HowTo, and for most users of these cards, proprietary drivers should offer no tangible advantage over the free nouveau driver.

For the purpose of demonstrating the installation, I will use “nvidia-current” below. Users of cards for which this driver doesn’t apply, please replace with “nvidia-173” or “nvidia-96” accordingly.

**Install the driver.** Now comes the moment where the elephant releases its water… ;) Issue the following command on the terminal:
```
username@machinename:~$ sudo apt-get update && sudo apt-get install nvidia-current && sudo nvidia-xconfig
```This will (a) refresh your package sources cache, (b) install the NVIDIA driver and any dependencies it needs to pull in, and (c) create a new Xorg configuration file [COLOR=Green]/etc/X11/xorg.conf[/COLOR].

If the process finished with no errors, reboot and you should be set. :)


Please feel free to post any questions arising from this description here.

---

### Post by Ad@m on 2011-07-17
> **szal said:**
>  _I strongly suggest you try this method for a fresh install of graphics drivers before trying any other method_, especially a GUI-driven one (I never used a GUI for package management on a Debian-ish system, but I hear that the Ubuntu Software Center supposedly has a way of installing proprietary graphics drivers).



Unfortunately I would have to disagree.

Using the 'Hardware Drivers' application in Ubuntu is the easiest method to install display drivers and it works.

---

### Post by szal on 2011-07-17
> **Ad@m said:**
> Unfortunately I would have to disagree.

Using the 'Hardware Drivers' application in Ubuntu is the easiest method to install display drivers and it works.
YMMV. I, for one, would be a bit discouraged about a number of reports popping up where the GUI thingy states, “driver installed but not in use”—perhaps they just forgot to reboot, but what do I know…

And as for being “easy”, I don’t see anything complicated about issuing 3 shell commands (concatenated in the above example). ;)

---

### Post by realzippy on 2011-07-17
“*driver installed but not in use bug*"  does not appear
when installing manually?

---

### Post by szal on 2011-07-17
> **realzippy said:**
> “*driver installed but not in use bug*"  does not appear
when installing manually?
What do you mean by “installing manually”? If you mean pulling the installer script from nvidia.com and running that, that is not the subject of my description.

---

### Post by realzippy on 2011-07-17
manually=your "howto"= sudo apt-get install nvidia-current && sudo nvidia-xconfig
means not using jockey GUI.

---

### Post by jocko on 2011-07-17
> **realzippy said:**
> “*driver installed but not in use bug*"  does not appear
when installing manually?
The bug results in jockey ("hardware drivers") reporting that the driver is not in use even when it is, and this method of installing will not affect that fact. Jockey will still tell you that the driver is installed but not in use, irrespective of which method you used to install it.
This howto does exactly what jockey does.

---

### Post by MrTKusa on 2011-08-18
TY szal, I installed Kubuntu 11.04 with a GeForce 240 GT and I could not clearly see my screen, let alone get to the GUI.  Your solution worked great and has allowed me to use my Kubuntu again!!!  TY


MrTKusa

---

