---
title: "MythTv Multi-seat"
date: 2007-09-22
forum: Installation &amp; Upgrades
---

### Post by dwf_starband on 2007-09-22
I have purchased a Hauppauge-WinTV-PVR-150 with a remote which should be here sometime this week.

Will my wife be able to control the tv (s-video out of my video card) while I'm doing stuff on my computer?  Or will things i do on the computer affect Mythtv on the other screen and what she does with the remote affect what happens on my computer screen?

If they do affect each other it seems like i need to set up a multi-seat setup with my computer monitor and my TV as separate seats.

What is the best way to do this?  There are plenty of tutorials around but they are all missing small pieces of information assuming the reader already knows what they are talking about.

I have tried the Userful Desktop Multiplier which works great when using two computer monitors but doesn't work with the s-video output on my video card.

Any advice or insight would be appreciated,

Dennis

---

### Post by madrivereric on 2007-11-03
I've successfully got a multi-seat myth box running.  I'm feeding the video/audio out of the PVR-350 card into a video modulator and then using a cable amplifier to feed the cable wiring throughout the house.  A filter on the cable input prevents my myth channel from going back to the cable co.  To control the box remotely, I'm using a universal remote and RF remote extender (google next generation home products -- looks questionable, but it really works!).   The PVR-350 remote didn't work with the RF extender, but a cheap RS one set to the default settings does.  I've then connected the extender's output to an opto-coupler to the serial port as a quasi home-brew LIRC receiver.  

After getting everything working, I tried upgrading OpenOffice and hosed my system big time (tricking the package manager to install packages across ubuntu releases is a very bad idea).  Reinstalling the system, I took notes on what I did and here they are.

Hard learned lessons: 
* need to install device void for xorg to box to work with only one keyboard/mouse
* place myth recordings on separate partition (like user directories) so you can reload system w.o losing data/shows!!!
* install latest version of nvidia driver from company or mulitple x servers won't work...
* compiz fusion hosed the nvidia drivers -- just say no!


Hardware: ASUS M2NBP-VM CSM (onboard Nvidia graphics), 2 GB ECC memory,  PVR-150, PVR-350, AMD64 x2 4600+

Ubuntu 7.04 're-install'.

Standard options,

Disk partion map:
/hda1 -- root partition (17GB)
/hda4 -- /home -- user partition (13GB) -- likely will want to migrate to new disk someday
/hda2 -- swap (6GB)
/hda3 -- /myth (144GB) -- DVR programs and database

/var/* gets formatted with fresh install.  Myth default locates database and recordings in /var/lib.  To resolve this, place these directories in own partition (/myth) and put in links to allow Myth's default installtion to find them:

Do the installation.  Reboot, login and run the update manager.  While its downloading the updates, do some housekeeping to save time.  Provided games also help pass the time.

make links from Myth volume to /var/lib...

sudo ln -s /myth/mysql mysql
sudo ln -s /myth/mysql-cluster/ mysql-cluster
sudo ln -s /myth/mythtv mythtv

Re-add additional users / groups.  (myth install will create the mysql group).

make sure that the mythtv directory's (and files) are owned by mythtv  
The mysql should be owned by mysql
mysql-cluster is owned by mythtv (admin group) -- odd, but seems to work, so...



Video setup:

Additions to get multi-seat X working:

DO NOT INSTALL Video Driver via Restricted drivers manager (as of 7.04 -- later versions might work ok, but I was seriously burned:  Ubuntu version was out of date and didn't fully work.  It wasn't fully and completely removed which prevented the newer version from the website to fully and properly load!  Lots of manual effort was requried to track down the remaining cruft which prevented the factory driver from loading.  Just don't go there!)

Furthermore, DO NOT RUN "Desktop Effects" -- they are interesting eyecandy but hosed the NVIDA driver files causing poor desktop response and low stability...  Just say NO and demove COMPIZ and related packages.  Fast and stable is much better than cool, slow and buggy...


First install libc6-dev (and libc6-dev-i386)

NVIDA driver downloaded from NVIDA website.

Run from text console (no X-server running)
(ctrl-alt-F6 for text console, sudo /etc/init.d/gdm stop to stop x)

sudo sh NVIDIA-Linux-x86_64-100.14.19-pkg2.run

installes latest video drivers

Run nvidia-xconfig afterwards and copy xorg.conf to /etc/X11 if not already done...

sudo /etc/init.d/gdm start to resume x & get login screen


Need to add void input device to Xorg install.  (Ubuntu installs numerous other devices, but not void -- go figure)  Void input device will let us not have a keyboard or mouse for the Myth seat.

see xorg.conf example


add Following packages (multiple dependencies will be added too):
openssh-server 

setserial
lirc
lirc-x
lirc-modules-source
module-assistant

libmyth-0.20
mytharchive
mytharchive-data
mythtv
mythtv-backend
mythtv-backend-master
mythtv-common
mythtv-database
mythtv-doc
mythtv-frontend
mythtv-themes

xserver-xorg-input-void



Configuring LIRC
(see [https://help.ubuntu.com/community/Install_Lirc_Feisty](https://help.ubuntu.com/community/Install_Lirc_Feisty) for ref)

/etc/init.d/lirc add 
setserial /dev/ttyS0 uart none
above load_modules ()


PVR tv out:
[https://help.ubuntu.com/community/MythTV_Feisty_hardware_pvr-350_TV-out](https://help.ubuntu.com/community/MythTV_Feisty_hardware_pvr-350_TV-out)

edit /etc/modprobe.d/aliases
to add: line "options ivtv-fb osd_compat=1" to /etc/modprobe.d/aliases

add ivtvdev_drv to X:

[http://packages.debian.org/etch/xserver-xorg-video-ivtv](http://packages.debian.org/etch/xserver-xorg-video-ivtv)

download the driver and open with GDebi Package Installer (default)

To allow the dvr user to access the PVR-350's sound output,
edit /etc/group to add dvr user to group video


edit /etc/gdm/gdm.conf-custom to select console only and disable auto login.  
(skip above step if feeling lucky)

(see attached version -- presently set as described)

make backup of /etc/X11/xorg.conf
mv multi user xorg.conf to /etc/X11

Reboot and test.

---

