---
title: "Nvidia driver files will not update"
date: 2022-01-21
forum: Installation &amp; Upgrades
---

### Post by watchpocket on 2022-01-21
I get Nvidia-driver updates from the "Graphics Drivers" PPA.  

A couple of weeks ago I updated 25 of these driver files. On reboot, I was stuck at a login-screen loop.

I have since kept them held back.
 
Yesterday I un-held them and tried again to do this update, with the same result.  
(I rolled back the system to an earlier snapshot with Timeshift to recover.)

When I look at any one of these files in Synaptic, they show (one, or more, of) the others as dependencies. 
I would think that the dependencies should be met by updating them all simultaneously.

I'm currently at a loss as to how to do this update successfully.
  
All ideas welcome.

My graphics card is an ** *NVIDIA Gigabyte GeForce RTX 3060 ***(as shown in my sig).

inxi tells me that the OpenGL renderer is:  ***"NVIDIA GeForce RTX 3060/PCIe/SSE2,  v: 4.6.0 NVIDIA 495.44,** direct render: Yes"*

I'm using the Nvidia driver version ***495.44***, and I'm trying to update it to v.** *495.46***.  
Almost all of the 25 files in the update are version 495.44, and the update is to move them to 495.46.

For what it's worth, [here's a current boot-info script]("https://paste.ubuntu.com/p/TZcckjWMqP/").

And these are the 25 files that won't update:

--------------------------------------------
libnss-systemd   (installed: 245.4-4ubuntu3.14; latest: 245.4-4ubuntu3.15)   
libnvidia-cfg1-495    (.44 > .46, same update for next 8 libs below)
libnvidia-compute-495    
libnvidia-compute-495:i386     
libnvidia-decode-495:i386        
libnvidia-encode-495:i386     
libnvidia-extra-495        
libnvidia-fbc1-495    
libnvidia-gl-495 
libnvidia-gl-495:i386 
    
libpam-systemd  (245.4-4ubuntu3.14  >  245.4-4ubuntu3.15)   
libsystemd-dev  (same version as above)    
libsystemd0  (same as above)    
libudev1  (same as above)
    
lightdm  (1.30.0-0ubuntu4-20.04.1 >  1.30.0-0ubuntu4-20.04.2) 
   
nvidia-compute-utils-495    (.44 > .46)
nvidia-dkms-495     
nvidia-kernel-common-495 
nvidia-kernel-source-495  
nvidia-utils-495 

systemd  (245.4-4ubuntu3.14 > 245.4-4ubuntu3.15)    
systemd-sysv   (same version as above)    
systemd-timesyncd  (same as above)    
udev  (same as above) 
   
xserver-xorg-video-nvidia-495 (.44 > .46)
----------------------------------------------------------------

---

### Post by CatKiller on 2022-01-21
> **watchpocket said:**
> I'm currently at a loss as to how to do this update successfully.
  
All ideas welcome.
I suspect that you've got bigger issues than simply the driver, since you're apparently struggling to update the kernel and systemd - neither of which rely on the Nvidia driver.

But for getting the driver installed properly, you may well find it easiest to purge all the nvidia and libnvidia packages, and then install the new ones.

(if you purge the drivers and reboot, and find yourself at a black screen with a blinking cursor, you can add *nomodeset* to your kernel line, just like you might on a fresh install of the OS)

---

### Post by watchpocket on 2022-01-21
Thanks for the response.

But I realized my problem was that I was using the wrong driver for my GPU.  I was -- mistakenly -- using driver 495.  

The Nvidia site recommends -- for my card -- to use driver 470.  So I changed to driver 470, and there are now no more problems with any Nvidia updates.

And I've already solved my kernel-update problems.  

I've marked the thread as solved.

---

