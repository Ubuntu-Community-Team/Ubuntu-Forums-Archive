---
title: "Problem installing 12.04LTS  and forward"
date: 2012-10-21
forum: Installation &amp; Upgrades
---

### Post by commbba on 2012-10-21
Hello there.The problem I'm facing is a bit strange.I have an Acer F3000 laptop and I'm using Ubuntu for about 3 years with great success except a few problems at the beggining.Now the problem is that I cannot install 12.04 and forward because the installer copy files to the HHD but when starts installing,a dialog box appears and says that an error occured and must stops.I searched .iso file and cd for erros,via md5sum and internal disk analyser and all are 100% OK.What is the error that is sawing up ?
I'm always do clean install because I found that from upgrades some issues appears such I'm facing now after upgrading from 11.10 to 12.04.I also upgrade to 12.10 despite the dialog box of the OS that informed me not to do the upgrade because of the old architecure of the system.After upgrade the system freezed and I had to do all the way down.Install 11.10 and after upgrade 12.04LTS.I also tried to install Xubuntu & Lubuntu,as they are lighter releases of Ubuntu but the same problem happens.What is the problem that the 11.10 cd does not has ?Why 11.10 installs great,more than 6 times at the last 2 days because I did a lot of experiments,and the later releases can't install,even the lighter ?
Thank you in advance for your answers.

---

### Post by commbba on 2012-10-22
Problem solved and to be honest double solved.What I mean ?First of all the problem with the installation was that the system didn't allowed to create the folder root/cache/dconf and the solution is:in live cd desktop open the terminal first and type "sudo apt-get remove ubiquity-slideshow-xubuntu" and where "xubuntu" your type of OS.
The second solution is about recognizing usb flash disks in bios.
Now I have a little problem with the language layout.
Thank you for your help.

---

