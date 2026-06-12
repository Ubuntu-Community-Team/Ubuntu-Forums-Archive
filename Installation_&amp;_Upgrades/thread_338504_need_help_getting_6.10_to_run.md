---
title: "need help getting 6.10 to run"
date: 2007-01-14
forum: Installation &amp; Upgrades
---

### Post by LilRayRay on 2007-01-14
I have the Nvidia 8800 GTS, and get (what seems to be somewhat common) error when running the 6.10 live cd.  I have tryed both reg. and safe graphics modes, and received An xserver error "No screens found".  I then tryed the alternate cd.  It isntalled, but i can only boot into safe mode.  I have read that it is possible to download and install the latest Nvidia driver from the command prompt.  Unfortunately, (in dapper at least), in order to use my network card, I had to go administrative > Networking, and then choose my network inorder to get access to internet.  

My questions:
1) How do I configure my network card from the command line???
2) What steps do I follow in order to download and install the nvidia drivers???

I have receive little to no support on this topic.  If anyone could perhaps help, I would be extremely greatful.

---

### Post by tommcd on 2007-01-14
You will need the driver from nvidia for such a new card. See this:
[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)
I assume you are using edgy 6.10 (you mentioned the edgy live CD). The driver from nividia can be installed using method 2 in the guide. You will need to completely remove the driver from the repos first (if you already installed it) before you install the driver from nvidia.
See this thread also:
[http://ubuntuforums.org/showthread.php?t=329635&highlight=nvidia+8800](http://ubuntuforums.org/showthread.php?t=329635&highlight=nvidia+8800)
If you can not boot to the GUI at all, then from recovery mode you can edit your xorg.conf file and change the driver to "vesa" under Section "Device" . This will get you a basic GUI until the nvidia driver is installed.
First backup xorg.conf
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
Then to edit the file
sudo nano -w /etc/X11/xorg.conf
scroll down to the device section, change to vesa, then do ctrl+x, y, to save.
Hope this helps.

---

### Post by LilRayRay on 2007-01-15
thanks for the help, but I have already tried changing my xorg.conf to vesa, and instead of getting "no screens found, I got a nice black screen on standby.

---

### Post by tommcd on 2007-01-16
Your eth0 should be enabled on bootup. If it is not you could do
sudo ifdown eth0
sudo ifup eth0
sudo dhclient
This should get your internet up.
I suppose you could download the nvidia driver on another PC, burn it to a cdrom and then do " sudo apt-cdrom add" and try to install the driver that way.

---

### Post by LilRayRay on 2007-01-16
if only I used my ethernet card. Im actually using a Netgear wireless USB WG111v2 for internet.  But I think I ll download the driver onto a flash drive and see if I can figure out how to mount it and then copy the driver from there.  If anyone could help with this, I would be greatful.

---

### Post by tommcd on 2007-01-17
Well, I think you should probably try to get online with a wired connection first. Then get your video card up and running. Then try to get wireless to work.
It can be a problem running linux with cutting edge hardware. Often, extra configuration or compiling drivers is needed to get it to work.

---

### Post by LilRayRay on 2007-01-18
well, a wired connection might be a bit tricky, but I think I will be just as easily able to  download the drivers to a flash drive and then do the offline installation.

---

