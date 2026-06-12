---
title: "XBMC .xsession cleared on reboot"
date: 2011-02-12
forum: Installation &amp; Upgrades
---

### Post by Hybridtech on 2011-02-12
Hi im having a total nightmare trying to get my OrigenAE H6 Case vfd display working under lcdproc. Iv followed the following tutorial: 
 
 
Code:
sudo apt-get install make
Code:
mkdir lcdproc-installcd lcdproc-install/
Code:
wget [http://www.irtrans.de/download/Server/Linux/lcdproc.tar.gztar](http://www.irtrans.de/download/Server/Linux/lcdproc.tar.gztar) -xvzf lcdproc.tar.gzcd lcdproc/./configure --enable-drivers=irtransmake cleansudo makesudo make install
Code:
nano LCDd.confForeground=no
Code:
sudo cp LCDd.conf /etc
Code:
cd /home/xbmc/sudo nano .xsession
Code:
/usr/local/sbin/LCDd -c /etc/LCDd.conf
 
When i run: /usr/local/sbin/LCDd -c /etc/LCDd.conf in terminal the vfd display works perfect. but i need it to autostart. as the instructions show above iv been adding this command in .xsession as so to auto start lcdproc:
 
```
#!/bin/bash
 /usr/local/sbin/LCDd -c /etc/LCDd.conf 
/usr/bin/xbmc --standalone
case "$?" in
    0 ) # Quit
        touch /tmp/noRestartXBMC
        break ;;
    64 ) # Shutdown System
        sleep 10 ;;
    65 ) # Warm Reboot
        echo Restarting XBMC ... ;;
    66 ) # Reboot System
        sleep 10 ;;
     * ) ;;
esac
```
 
 
But on reboot its changed back to this: 
 
```
#!/bin/bash
/usr/bin/xbmc --standalone
case "$?" in
    0 ) # Quit
        touch /tmp/noRestartXBMC
        break ;;
    64 ) # Shutdown System
        sleep 10 ;;
    65 ) # Warm Reboot
        echo Restarting XBMC ... ;;
    66 ) # Reboot System
        sleep 10 ;;
     * ) ;;
esac
```
 
Im really finding this frustrating as iv been on this for a week now and its the last thing i need to do to get everything up and running. Any help greatly apreciated. 
 
Sorry im using xbmc Dharma 10.0 if this helps :confused:

---

