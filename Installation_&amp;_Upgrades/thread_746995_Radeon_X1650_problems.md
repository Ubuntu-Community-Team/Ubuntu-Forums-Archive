---
title: "Radeon X1650 problems"
date: 2008-04-06
forum: Installation &amp; Upgrades
---

### Post by alberson on 2008-04-06
Hey, I'm having some problems while trying to install Ubuntu to my machine. When I choose install, the screen flashes and sometimes I get a message saying the display had crashed "X" times in 90 seconds and it tells me to try again in 2 minutes. I've installed Kurumin Linux before and I had some issues with my Video card too, but I got it solved with the command line:
```
sudo dpkg-reconfigurexserver-xorg
```
But I can't find where to type it (if this is the correct solution). I've searched the forums and all I got was how to install drivers BEFORE install Ubuntu, but I can't even install it. My machine:

Athon XP 1500MHz
1,5GB RAM
ATI RADEON X1650 (AGP)

Thanks in advance.

---

### Post by Partyboi2 on 2008-04-08
[FONT=monospace]You can type [/FONT]```
sudo dpkg-reconfigure xserver-xorg
```[FONT=monospace]in a terminal at the prompt. To get to a  terminal try Ctrl+Alt+F2 when you start getting that message. If that does not work, then maybe try the [alternate cd]("http://releases.ubuntu.com/7.10/") which is a textbase installer.
[/FONT]

---

### Post by alberson on 2008-04-27
I did it, it worked and I've instaled Ubuntu. But there is 2 new problems now:
1. Everytime I start with Ubuntu I have to reconfigure xserver. There is a way to save this configuration?
2. When I click the power-off button, in desktop, top right of the screen, all got frozen and I have to reboot manually. It's because the bad configuration of xserver?

Thanks again.

---

### Post by Partyboi2 on 2008-04-27
download envy and install the drivers for your graphics card. Envy is a very simple program that will download and install the  drivers for your graphics card.
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
download the deb package to your desktop and double click on it to start installing it.

---

### Post by alberson on 2008-05-22
Man, I have another problem. I dont have ADSL or cable internet, I have 3G internet, that i didn't find the right drivers to connect in ubuntu... that makes thinks alot harder, since the package you recomended to me need an internet connection. Any idea? I've found a how to learning how to install the internet with Gnome-PPP, but where to download the debian package? From debian website? I have to download all the packages thats marked with "depends" tag?
Here's the link I've found. Thanks in advance AGAIN.
[http://packages.debian.org/unstable/net/gnome-ppp]("http://packages.debian.org/unstable/net/gnome-ppp")

---

### Post by Partyboi2 on 2008-05-24
You can get gnome-ppp from [[COLOR=Blue]here[/COLOR]]("http://packages.ubuntu.com/hardy/gnome-ppp") if you are using hardy or [[COLOR=Blue]here[/COLOR]]("http://packages.ubuntu.com/") if using another release version. You could try something like [[COLOR=Blue]nonetdebs[/COLOR]]("http://nonetdebs.unixpod.com/") to download the gnome-ppp package..

---

