---
title: "Installing a printer SUCKS!"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by shultzjr on 2007-05-03
In Windows the procedure is 1. load software, 2. connect usb printer and it all just works.  In Kubuntu704 I took the brand new printer out of the box and plugged in the power and connected it to the usb port.  No plug-and-play routine pops up and says there is a new device connected to my computer.  The printer is a new hp d1420 and it is a deskjet so it should "just work" and it doesn't.  I have been through the CUPS printing manager for hours.  The usb option is not even listed when I get to that screen.  A dozen other choices but no usb option.  When I do it manually is says that "no hp device connected". when it scans the usb bus.  I have other usb devices plugged in and they work fine.  The chipset is an AMD-756 Viper USB rev 06 and it is on the motherboard.  I even tried a pci usb card with an OPTI chipset.  It comes up in the lspci list but will not work with the printer D1420.  When I go into the HPLIB Toolbox it says to install the printer.  When I go to install the printer, whatever installation routine doesn't find it.  I even found a driver that is pretty close off the Internet, D1400 so it should work.  I have tried installing it with the CUPS installer (failed) and the HP-SETUP routine (failed) so what's next?

later......

---

### Post by SishGupta on 2007-05-03
I haven't heard someone complaining about linux printing in ages.

My printer is parallel but i just plug it in and hit "next ->" as fast as i can until the end of the add printer wizard.

I am curious about the USB thing though, I'm gonna try one in an hour and report back.

Good luck

---

### Post by Teamgeist on 2007-05-03
The Printer is supported by HPLIP 1.7.4!
Ubuntu comes with HPLIP 1.7.3!
You can download 1.7.4 here: [http://hplip.sourceforge.net/downloads.html](http://hplip.sourceforge.net/downloads.html)

It seems to have an installer that works on Ubuntu.

Good Luck.

And calm down a little, dude. It's HP fault that they didn't put the Linux drivers on the CD that came with the printer.
At least they're having excellent drivers for most of their machines that can be downloaded and installed.

/edit: here are instructions on how to use the installer: [http://hplip.sourceforge.net/install/install/index.html](http://hplip.sourceforge.net/install/install/index.html)

/edit2: you might wanna install the package build-essential before running the HPLIP installer:
```
sudo apt-get install build-essential
```

---

### Post by ubuntu27 on 2007-05-03
@shultzjr: It's alright. Your printer is not support with the version that *ubuntu Feisty Fawn provides. 
Download and install the latest HPLIP from 

[http://hplip.sourceforge.net/install/install/index.html](http://hplip.sourceforge.net/install/install/index.html)


[Here is the list]("http://hplip.sourceforge.net/supported_devices/combined.html") of HP Printer supported by HPLIP. It says that your printer needs at least HPLIP version 1.7.4 minimum to function.

Good Luck!

---

### Post by kelvin spratt on 2007-05-03
exuse me windows does not supply printer drivers by magic it supplies a driver to fit all printers sort of it also tells you the software might not work witch is usually the case a printer usb or not plugs into printer port usb printer thats under windows thats what that shiny disc is for the windows drivers  as well if you press printers tab add printer linux will look for drivers just like windows and u have more chance of finding drivers installed in linux than the 1 msoft printer driver in windows please don't slag linux of when you are talking about things that should be common sense after all linux supplies more drivers for all hardware free than anybody else does
and they charge you money at the end of the day if you need help you can get it here but don't offend the people that contribute in these forums by insulting their choice of distro then expect them to help you

---

