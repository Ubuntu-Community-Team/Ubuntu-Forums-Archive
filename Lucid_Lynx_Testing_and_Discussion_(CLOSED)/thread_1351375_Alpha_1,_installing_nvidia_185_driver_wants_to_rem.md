---
title: "Alpha 1, installing nvidia 185 driver wants to remove xorg and ubuntu-desktop"
date: 2009-12-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-12-10
Fully up to date as of now. Is this a case of just waiting. 
```

sudo apt-get install nvidia-glx-185
[sudo] password for philinux: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dkms fakeroot nvidia-185-kernel-source nvidia-185-libvdpau nvidia-settings patch
Suggested packages:
  diff-doc
The following packages will be REMOVED
  ubuntu-desktop xorg xserver-xorg xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse xserver-xorg-video-all xserver-xorg-video-apm xserver-xorg-video-ark
  xserver-xorg-video-ati xserver-xorg-video-chips xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-i128
  xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga xserver-xorg-video-neomagic xserver-xorg-video-nv
  xserver-xorg-video-openchrome xserver-xorg-video-r128 xserver-xorg-video-radeon xserver-xorg-video-rendition
  xserver-xorg-video-s3 xserver-xorg-video-s3virge xserver-xorg-video-savage xserver-xorg-video-siliconmotion
  xserver-xorg-video-sis xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident xserver-xorg-video-tseng
  xserver-xorg-video-v4l xserver-xorg-video-vesa xserver-xorg-video-vmware xserver-xorg-video-voodoo
The following NEW packages will be installed
  dkms fakeroot nvidia-185-kernel-source nvidia-185-libvdpau nvidia-glx-185 nvidia-settings patch
0 upgraded, 7 newly installed, 39 to remove and 0 not upgraded.
Need to get 22.1MB of archives.
After this operation, 55.4MB of additional disk space will be used.
Do you want to continue [Y/n]? n

```

---

### Post by rtalcott on 2009-12-10
Same issue here!  Hopefully this gets resolved soon!
rt

---

### Post by jppr on 2009-12-10
> **rtalcott said:**
> Same issue here!  Hopefully this gets resolved soon!
rt


The nv driver used by default for nvidia video chipsets on the LiveCD is reported to lead to X server crashes. Investigation of this issue is ongoing and should be resolved for Lucid Alpha 2. As a workaround, users can boot with safe graphics mode" to use the vesa driver. (494627)

---

### Post by kevpan815 on 2009-12-10
It's A Problem On The Alternate CD As Well, Just FYI. I Installed The NVIDIA 185 Series Device Driver, Rebooted, All Of A Sudden No More GUI Interface, All I Had Was A Command Line Interface, Just FYI!

---

### Post by BobCFC on 2009-12-10
I got dropped to the console courtesy of the proprietary package too

The way I fixed it for now was 
```

sudo apt-get remove nvidia*
sudo apt-get install xserver-xorg-core
``` 

which reinstalled about 30 packages and gave me X back.

Then reboot and choose low graphics for one session so I could browse to nvidia.com and manually download the latest 195.22 beta driver. 

Installed this by hand and now have hires/compiz

(Crtl-Alt-F1, sudo stop gdm, sudo sh NVIDIA1234.run, sudo start gdm)


From past experience it is not fun to use the manual driver during the alphas because there are so many new kernels.  But it will do for now until the package deps are fixed.

---

### Post by Darkshade on 2009-12-10
Yup, same here. Installed 195.22 from the sevenmachines ppa and everything's working again.

---

### Post by kingborel on 2009-12-10
Same problem, installing nvidia-glx-185 wants to remove the rest of xserver-xorg. Using the vesa driver at the moment, but hopefully its a simple fix :)

---

### Post by Robin Nixon on 2009-12-11
```
sudo apt-get remove nvidia*
sudo apt-get install xserver-xorg-core
```That did the job for me, thanks.

---

### Post by philinux on 2009-12-11
I think I'll sit back and wait for the fix.

---

### Post by Gina on 2009-12-11
> **philinux said:**
> I think I'll sit back and wait for the fix.Good thinking - think I'll do the same :D

---

### Post by kevpan815 on 2009-12-11
> **BobCFC said:**
> I got dropped to the console courtesy of the proprietary package too

The way I fixed it for now was 
```

sudo apt-get remove nvidia*
sudo apt-get install xserver-xorg-core
``` 

which reinstalled about 30 packages and gave me X back.

Then reboot and choose low graphics for one session so I could browse to nvidia.com and manually download the latest 195.22 beta driver. 

Installed this by hand and now have hires/compiz

(Crtl-Alt-F1, sudo stop gdm, sudo sh NVIDIA1234.run, sudo start gdm)


From past experience it is not fun to use the manual driver during the alphas because there are so many new kernels.  But it will do for now until the package deps are fixed.

Your Right, The 195.22 Beta Device Driver Worked Just Fine Here 2!

---

### Post by brm on 2009-12-11
I have had a similar experience with the Kubuntu flavour of Lucid.

I first tried using the "Hardware Drivers" application (which appears not have changed over several releases). Interestingly, it did not even list the 180 or 185 series drivers, only the 173 and 96 series. It recommended the 173 series. I selected that and clicked the "Activate" button. Nothing happened.

Interestingly, I had the same experience a couple of days ago when I realized that the Jaunty (9.04) installation on this (multi-boot) machine had not enabled the proprietary driver. But under jaunty, the command-line method (next paragraph) actually worked.

I then tried installing the packages through the command line. The next step after that is to run sudo nvidia-xconfig. But, as others have reported, the system threatened to uninstall all of X.

Such is the pain of running the first alpha.

---

### Post by clivejo on 2009-12-12
I've been having same problem, but downloaded the beta driver as suggested and it works brilliantly!

---

### Post by Bumper44 on 2009-12-12
I get a error whenever I try to install the beta driver! Help please. Thanks :D

---

### Post by Regenweald on 2009-12-12
> **Bumper44 said:**
> I get a error whenever I try to install the beta driver! Help please. Thanks :D

The post is pretty ambiguous ;) What is the error ? how are you trying to install the driver ?

---

### Post by Bumper44 on 2009-12-12
I'm kinda of noob to Ubuntu, but I just downloaded the file and double clicked it, lol. Anything I should have done?

---

### Post by dino99 on 2009-12-12
have had too this problem on Lucid, the same happened with Karmic & nvidia 195.

So, this come up after installing the last kernel on Karmic: during installation, i remember the warning saying that it found too many dkms & it can't choose one & abort. Of course, i only have 1 dkms package.

As said above, i first removed / purged all nvidia packages and reinstalled them, then xserver worked fine.

As i understand, the 195 package is recognized as a 190 in synaptic: maybe the reason of conflict.

---

### Post by Bumper44 on 2009-12-12
I tried what you said but when installing 190 in also wants to install 185 which removes xserver-xorg. I'm am trying to install the beta driver from their website, but I get a error.

---

### Post by Gina on 2009-12-12
Still lots of problems with nvidia and the X server which the devs are working on.  Seems to be quite a problem.  Meanwhile, I've stopped testing on nvidia graphics until bug fixes come along.  Good luck to those still persevering :)  I'm switching test machines to my P4 - only 32 bit but ATI graphics and it's working :)

---

### Post by Bumper44 on 2009-12-12
How long do you think til we have fix?

---

### Post by jppr on 2009-12-12
> **Bumper44 said:**
> How long do you think til we have fix?
The nv driver used by default for nvidia video chipsets on the LiveCD is reported to lead to X server crashes. Investigation of this issue is ongoing and should be resolved for Lucid Alpha 2. As a workaround, users can boot with safe graphics mode" to use the vesa driver. (494627)

---

### Post by Jordanwb on 2009-12-12
^ Having the above problem, will try vesa driver.

*Edit*

Vesa driver works.

---

### Post by paul_in_london on 2009-12-12
I'm using this ppa:

[https://launchpad.net/~sevenmachines/+archive/nvidia?field.series_filter=lucid](https://launchpad.net/~sevenmachines/+archive/nvidia?field.series_filter=lucid)

and was able to install the 195.22 nvidia driver without conflicts :-)

---

### Post by jppr on 2009-12-13
> **Jordanwb said:**
> ^ Having the above problem, will try vesa driver.

*Edit*

Vesa driver works.


How can i install vesa driver when i have do fresh alternate installation? i mean... how install vesa driver in recovery mode? sudo aptitude install... ? or... how can i change /etc/x11/xorg.conf that (install) vesa driver in recovery mode? after alternate installation, system boot black and empty screen and i can´t do anything.
Now i have back pre alpha installation with 185 driver and i can´t update new X

---

### Post by dino99 on 2009-12-13
run the command you find inside xorg.conf (sudo dpkg -reconfigure ...)

---

### Post by philinux on 2009-12-15
Anyone know when this will get fixed. Trying to install 185 still wants to remove all of X.

I want to stick with the stock install for testing.

---

### Post by brm on 2009-12-15
I agree wholeheartedly with the comments of philinux.

If I need the full functionality of a proprietary video driver, I will use a released (and supported) version of Kubuntu (that is, my particular flavour).

My view is that the point of testing a development version is to stick with the released version, not to tweak it with files from outside the repositories to add missing functionality.

---

### Post by cariboo on 2009-12-15
Right now I'd prefer just getting Lucid running using whatever works. I'm running Nvidia's 190.42 beta driver. Once a proper driver is ready, I'll switch back to it.

---

### Post by SevenMachines on 2009-12-15
> **cariboo907 said:**
> Right now I'd prefer just getting Lucid running using whatever works. I'm running Nvidia's 190.42 beta driver. Once a proper driver is ready, I'll switch back to it.
ditto, i'm ok to use nvidia/fglrx stuff from outside the repository when it keeps things working while using lucid, makes it easier to test if you can use it usefully.
i prefer to keep the development versions running all main repository packages though. bugs are hard enough to spot without throwing in lots of different repositories too :)

---

### Post by Robin Nixon on 2009-12-16
I see that the temporary solution appears to be the removal of all nvidia drivers from *System > Administration > Hardware Drivers*, so you can't try to install them that way. I presume that when they return the problem will have been rectified.

---

### Post by philinux on 2009-12-16
> **Robin Nixon said:**
> I see that the temporary solution appears to be the removal of all nvidia drivers from *System > Administration > Hardware Drivers*, so you can't try to install them that way. I presume that when they return the problem will have been rectified.

I removed my 185 driver to let the xorg upgrade through. With hindsight I should have waited. 

Ok so now I've got full res with the vesa driver so no real problem. I'll wait till the 185 or later driver is rebuilt. 

However using Hardware Drivers does not warn you it will remove all of X. I test using apt-get install nvidia-glx-185 and see what it wants to do. and checking the updates of course.

---

