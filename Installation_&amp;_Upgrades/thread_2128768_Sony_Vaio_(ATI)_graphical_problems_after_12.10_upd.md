---
title: "Sony Vaio (ATI) graphical problems after 12.10 updates"
date: 2013-03-24
forum: Installation &amp; Upgrades
---

### Post by lxx on 2013-03-24
Hi all,

i tried to install ubuntu 12.10 on my Sony Vaio Notebook about 4 times.
This time i made some fotos to show what problems occur.

[IMG]http://i.imgur.com/hRYL5g0.jpg[/IMG]
I installed Ubuntu 12.10 from an USB stick
In the installation I also checked "Install this third-party software"

[IMG]http://i.imgur.com/rnPaG7W.jpg[/IMG]
The installation is completed without any problems.
Because of problems with the WLAN in previous installs, i disabled WLAN, then restarted 
the notebook.

[IMG]http://i.imgur.com/KNAFl3S.jpg[/IMG]
After a restart these are my graphics settings 

[IMG]http://i.imgur.com/KL6MtNt.jpg[/IMG]
At that point Ubuntu is working fine. 
So my next step is of course to load all available updates.

[IMG]http://i.imgur.com/fVgVQbT.jpg[/IMG]
But after installing all updates and restarting the computer, i only get a graphical problem,
pink vertical stripes (no good photo)


So i start **Ubuntu, with Linux 3.5.0-26-generic (recovery mode)** trying to install the
amd fglrx driver, like descibed here: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

lspci -vvnn | grep vga
-> ... ATI Thames [Radeon 7500M/7600M Series]

At that point the is no /etc/X11/xorg.conf , so i dont need to make sure i have a backup of this file.

Then i run:

sudo apt-get install linux-headers-generic
sudo apt-get install fglrx fglrx-amdcccle
sudo aticonfig --initial

[IMG]http://i.imgur.com/tGoMWcE.jpg[/IMG]
This xorg.conf gets created
[IMG]http://i.imgur.com/1EZfMQI.jpg[/IMG]
After restarting the computer, the boot process stops here.

When i start in recovery mode again, **fglrxinfo** returns
**Error: unable to open display (null)**

---

### Post by lxx on 2013-03-27
I still think that the graphic driver is the problem.
Maybe someone can give me some tips which driver i have to install (and how).
Here is a dump of hwinfo.
[http://paste.ubuntu.com/5653515/](http://paste.ubuntu.com/5653515/)

thanks

---

### Post by lxx on 2013-03-29
Finally I was able to get the correct graphic driver running.

This instruction worked for me: [http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx/129200#129200](http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx/129200#129200)

But only the 13.3 beta driver worked.

My graphic chip is a radeon 7650M.

---

