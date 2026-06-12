---
title: "New Install of v7.10 - System does nothing after logging in"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by mskadu on 2007-10-28
Hi,

I've done a fresh install of Ubuntu v7.10. The installer goes through fine and reboots. After the reboot, nothing happens after I login (note that I do hear the startup music playing). I can move my mouse, but cannot switch to console 1 (Ctrl+Alt+F1). If I wait for a while, I can see my hdd lights flickering (maybe somethings on).

I've tried booting into recovery mode, but /var/log/messages doesn't show any problems.  Any hint's on what I should be doing next? :confused:

---

### Post by jenhsun on 2007-10-28
X windows crash, I think.
do
sudo /etc/init.d/gdm stop
dpkg-reconfigure xserver-xorg
......do the configure
/etc/init.d/gdm restart

---

### Post by mskadu on 2007-10-28
Ok .. I've tried that and it doesn't work. On GDM restart the same thing happens again (except this time I saw the top bar appear and disappear in a flash!). It froze for a few seconds and fell back to prompt.

What next?

---

### Post by jenhsun on 2007-10-28
Go to this site
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

You can install it under your text mode.
I think your driver is not correct.

---

### Post by mskadu on 2007-10-28
Ok, doing a "sudo dpkg-reconfigure gdm" a second time did the trick. I can get to the desktop. But that's it. I can see the desktop, I see a "Software updates avaialable" tooltip and I can't do anything else (note that my mouse is still moving around). Can't switch to console (C+A+F1) either. Do we still think this is a driver problem?

Oh, and yes, after re-configuring my X I ran unto the Usplash (the bootup logo and orange progress bar) not showing problem. But [this thread]("http://ubuntuforums.org/showthread.php?t=583876") here helped me sort it out.

---

### Post by mskadu on 2007-10-28
Oh and yes, I cant do this as my network interfaces aren't up when I start GDM from recovery mode. 

> **jenhsun said:**
> Go to this site
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

You can install it under your text mode.
I think your driver is not correct.

---

### Post by jenhsun on 2007-10-28
> **mskadu said:**
> Oh and yes, I cant do this as my network interfaces aren't up when I start GDM from recovery mode.

You don't need to connect to the internet use gdm, just use terminal
Try to setup your network interface in

```
sudo gedit /etc/network/interfaces
```

then

```
sudo apt-get update
```

if you can link to the net, you will see what happened.

Then try to do

```
wget http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.8-0ubuntu8_all.deb
sudo dpkg -i envy_0.9.8-0ubuntu8_all.deb

```

To Uninstall
```
sudo dpkg -r package_name
```
so you can download the file
please follow the setting for your graphic card.

---

### Post by mskadu on 2007-10-28
Umm.. didn't get to doing that. I restart the machine and I am now able to login to the new installation. I am not sure what happened?? :confused:

Anyway, the problem seems sorted for the moment. The systems running very slow though (even after disabling effects).

Update - new thread for slow running [started here]("http://ubuntuforums.org/showthread.php?t=595006").

---

