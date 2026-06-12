---
title: "apt-get install from usb or Live CD?"
date: 2008-04-18
forum: Installation &amp; Upgrades
---

### Post by Grogknot on 2008-04-18
I've recently reinstalled ubuntu on my laptop because I want to have my /home folder on a separate partition. Unfortunately I have an ati mobility x1400 which just makes installation a pain because xserver fails all the time. I've followed the instructions from this guide: [http://www.blindedbytech.com/2007/10/20/gutsy-gibbon-radeon-mobility-x1400/](http://www.blindedbytech.com/2007/10/20/gutsy-gibbon-radeon-mobility-x1400/)

which has worked for me before, but not this time. I've managed to boot up the Live CD, partition the drives, and install ubuntu. However when I boot from my hard drive i cannot use ctrl+alt+f2 to get to the command line. If I boot up in recovery mode, I don't seem to have a network connection because apt-get update does not work.

Is there a way I can download xorg-driver-fglrx on to a USB drive and install from there? I only really need this driver to get going, I should be able to figure it out from there.

Or is there a way to install the driver through the live CD on to the hard drive installation. I imagine that is not possible because of permissions, but I'm still a big noob with linux.

If there is any other way to get to a command line when I boot in the generic mode I could try that. ctrl alt backspace doesn't seem to work either. 

Any ideas why I don't have a network connection now, but I do when I use the Live CD?

Also just to note, this is setup for a dual boot with windows xp. 

thank you very much for any help

---

### Post by warp99 on 2008-04-18
Boot into recovery mode and at the root command prompt issue the following:
```
dpkg-reconfigure -phigh xserver-xorg
```
change the driver from 'ati' to 'vesa'. Then issue a 'sudo reboot'. Boot the computer into your normal session. Connect to the internet, open a terminal and at the command line issue the following:
```
sudo apt-get install --reinstall linux-restricted-modules-$(uname -r) xorg-driver-fglrx
```
then run the following:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and change the driver from 'vesa' to 'fglrx', then issue a 'sudo reboot'.

if you have some additional problems please visit the ATI wiki:

[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

Edit:

If you installed Hardy then you have to edit your xorg.conf manually. So instead of running 'dpkg-reconfigure -phigh xserver-xorg' do the following:
```
sudo nano /etc/X11/xorg.conf
```
and in the device section add the following line:
```
Driver "vesa'
```
press Crtl-o to save and Crtl-x to exit, then 'sudo reboot'. After you install the 'xorg-driver-fglrx' driver issue the following:
```
sudo nano /etc/X11/xorg.conf
```
and in the device section change "vesa" to "fglrx". Save the file then issue a 'sudo reboot'

---

### Post by Grogknot on 2008-04-19
Thank you. This worked flawlessly.

---

