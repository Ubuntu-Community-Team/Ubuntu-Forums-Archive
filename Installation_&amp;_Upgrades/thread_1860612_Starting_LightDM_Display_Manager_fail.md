---
title: "Starting LightDM Display Manager fail"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by iniwidi on 2011-10-14
I just upgrade my laptop DeLL Vostro 3300 from ubuntu 11.04 to 11.10, but after finish and reboot the desktop cannot run well like hanging.

I try to look at the text line there is some error, here's the error

* Starting LightDM Display Manager [fail]

And there isnt any other information message for the error.

Note:

regarding the error I've attached a file in jpg form


Please Help me, thx.

---

### Post by collisionystm on 2011-10-14
its not AMD is it? If it is... you may as well throw in the towel now.

---

### Post by iniwidi on 2011-10-14
> **collisionystm said:**
> its not AMD is it? If it is... you may as well throw in the towel now.

my laptop is not amd but intel, thx for your reply

---

### Post by 23dornot23d on 2011-10-14
You could try 

sudo apt-get update
sudo apt-get install aptitude
sudo aptitude reinstall lightdm

if that fails try gdm

sudo aptitude install gdm

---

### Post by iniwidi on 2011-10-15
> **23dornot23d said:**
> You could try 

sudo apt-get update
sudo apt-get install aptitude
sudo aptitude reinstall lightdm

if that fails try gdm

sudo aptitude install gdm

Great!, lightDM start normaly, but i have other error, here's the error :

[B]* Starting automatic crash report generation [failed]
[/B]

I try to do the same thing as above but still error, the error follows:

## start here ##
root@widi-Vostro-3300:~# aptitude reinstall apport
The following packages will be REINSTALLED:
  apport
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 2 not upg                                                                                                                                                             raded.
Need to get 0 B/82.5 kB of archives. After unpacking 0 B will be used.
(Reading database ... 336621 files and directories currently installed.)
Preparing to replace apport 1.23-0ubuntu3 (using .../apport_1.23-0ubuntu3_all.de                                                                                                                                                             b) ...
Unpacking replacement apport ...
Processing triggers for ureadahead ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'interface/x-winamp-skin'
Processing triggers for man-db ...
Setting up apport (1.23-0ubuntu3) ...
start: Job failed to start
invoke-rc.d: initscript apport, action "start" failed.

## Eof ##

thx for ure help.

---

### Post by iniwidi on 2011-10-15
> **23dornot23d said:**
> You could try 

sudo apt-get update
sudo apt-get install aptitude
sudo aptitude reinstall lightdm

if that fails try gdm

sudo aptitude install gdm

I think this has nothing to do with the error above, because I try to remove lightdm and GDM status remains the same, I try to look for another error, I do not find other errors.

Is there another way to fix it? or to delete all associated with the gui, and tried to install from scratch, please give me advice.

---

### Post by iniwidi on 2011-10-15
> **iniwidi said:**
> I think this has nothing to do with the error above, because I try to remove lightdm and GDM status remains the same, I try to look for another error, I do not find other errors.

Is there another way to fix it? or to delete all associated with the gui, and tried to install from scratch, please give me advice.

I think here's the error why my desktop cannot load :

##start here##


[    19.216] (II) LoadModule: "nvidia"
[    19.216] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    19.216] (II) Module nvidia: vendor="NVIDIA Corporation"
[    19.216]    compiled for 4.0.2, module version = 1.0.0
[    19.216]    Module class: X.Org Video Driver
[    19.218] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[    19.218] (EE) NVIDIA:     system's kernel log for additional error messages.
[    19.218] (II) UnloadModule: "nvidia"
[    19.218] (II) Unloading nvidia
[    19.218] (EE) Failed to load module "nvidia" (module-specific error, 0)
[    19.218] (EE) No drivers available.
[    19.218]
Fatal server error:
[    19.218] no screens found
[    19.218]
Please consult the The X.Org Foundation support
         at [http://wiki.x.org](http://wiki.x.org)
 for help.

##EOF

where i find drivers for nvidia?

---

### Post by Sofa_King_Cool79 on 2011-12-08
> **23dornot23d said:**
> You could try 

sudo apt-get update
sudo apt-get install aptitude
sudo aptitude reinstall lightdm

if that fails try gdm

sudo aptitude install gdm

I too upgraded from 11.04 to 11.10 and got this lightDM fail error along with SP5100 TCO Timer: mmio address 0xfec000f0 already in use. 

I tried the above and no luck, I still get the mmio address error. 

uname -r shows I have 

3.0.0-13-generic-pae

any other suggestions. 

running a home built box with a GeForce 9400 series video card
4GB RAM DDR3
Dual Core AMD 3.6ghz

---

### Post by MAFoElffen on 2011-12-08
> **iniwidi said:**
> my laptop is not amd but intel, thx for your reply
What is your latop and what does it have for graphics.

You are focusing on the wrong error. I have been ignoring that apport error on 3 of my boxes since natty alpha2 and have not had a problem with apoort at all. BUT, if you look at your error, it really says that /etc/rc2.d/xxxxxx Can't read the filename, line 6 of that file.

If you could post that file (and the syslog), it may tell us exactly where that problem is. You could do that from a LiveCD.

"rc2" is the defualt init runlevel for the desktop.  This could be a graphics problem with either xorg or your graphics driver. Lightdm is falling out because theres a problem with the graphics elsewhere... At least from what I see in these previous posts.

---

### Post by MAFoElffen on 2011-12-08
Thinking about this one- Might be less work and frustration to just reinstall this one.

---

### Post by ghaniba on 2011-12-12
Grab the latest nvidia drivers for your card and run it.  Worked for me this am!

Dave

---

### Post by LakeHMM on 2012-10-03
Easier said than done.  I had a really hard time tracking down the right driver, since it seemed to have disappeared from repositories.  Here's what worked for me.  Depending on your nVidia card, you might need to download a different file, but they're all listed at [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html).  I needed the legacy 96xx driver for my GeForce 2 MX 400.  So, after weeks of trying to fix this, I just ran these commands and it finally worked!

```
wget http://us.download.nvidia.com/XFree86/Linux-x86/96.43.23/NVIDIA-Linux-x86-96.43.23-pkg1.run
sudo sh NVIDIA-Linux-x86-96.43.23-pkg1.run
sudo reboot
```

---

### Post by QwUo173Hy on 2013-01-16
> **LakeHMM said:**
> Easier said than done.  I had a really hard time tracking down the right driver, since it seemed to have disappeared from repositories.  Here's what worked for me.  Depending on your nVidia card, you might need to download a different file, but they're all listed at [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html).  I needed the legacy 96xx driver for my GeForce 2 MX 400.  So, after weeks of trying to fix this, I just ran these commands and it finally worked!

```
wget http://us.download.nvidia.com/XFree86/Linux-x86/96.43.23/NVIDIA-Linux-x86-96.43.23-pkg1.run
sudo sh NVIDIA-Linux-x86-96.43.23-pkg1.run
sudo reboot
```

Thank you so much LakeHMM, you just saved me lots of time and a reinstall!

---

