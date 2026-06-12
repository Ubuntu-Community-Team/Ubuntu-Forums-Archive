---
title: "How to rollback nvidia changes from update"
date: 2021-12-26
forum: Installation &amp; Upgrades
---

### Post by agrayray on 2021-12-26
It seems there was some big changes with nvidia drivers in the update I just did this morning to Ubuntu (gnome) 20 system running on a Dell p5550. Immediately after the update my fan has been running non stop and my computer and keyboard get pretty hot.
I have been running this system fine with no fan or over heating problems (for over a year) prior to the update so i am assuming its the new nvdia software that was put on my system.  I was also prompted if I wanted to remove lots of obsolete packages which were mostly all nvidia ones.

So..question 1: 

I would like to rollback my system to what it was prior (using the nvidia packages that worked fine before upgrade).  Is there an easy to do this (say with 1-2 hours of work)?  It doesn't appear that easy to do based on the searching I have done.

If not, I would think I want to do a wipe and re-install Ubuntu 20.04.03.  I can do that in about two hours, but I am not sure if I should update my system.  I am guessing that if I do, I will get the latest nvidia packages which just screwed everything up and I do don't want them.

Question 2 - Is there a way to do updates to just one rev back from the current updates, or a way I can update without putting back these new problematic nvidia drivers back on my system?
Question 3 - Can I/should I install updates when installing ubuntu?

Basically I just want to update my system to where it was before these nvdia updates that wrecked my system.  I would opt to go base 20.04.3 install with no updates if I had to, but of course I would prefer updates minus these nvidia updates.

Here's some screenshots of the packages that were removed and a copy of apt update log (/var/log/apt/history.log), although FYI the update was not done through the command line but was done with the graphical software updater on Ubuntu.

Question 4 - If there is another recommendation to stop this overheating and constant fan issue (which is too loud to do my work/mtgs regardless of overheating), please advise!

THANKS VERY MUCH TO ALL FOR YOUR TIME AND HELP IN ADVANCE!

---

### Post by oldfred on 2021-12-27
How did you install nVidia driver?
You always want to install from Ubuntu repository, not a driver directly from nVidia.
The direct download has to be reinstalled with every kernel update.

This says you should be using 390.xx?
Updated driver search by nVidia model, do not download, just check correct driver version
[https://www.nvidia.com/Download/index.aspx](https://www.nvidia.com/Download/index.aspx)

If changing drivers, you must totally purge old one, as new does not remove old & then you get conflicts.
If you downloaded from nVidia, you must use its process to remove it.

#What is installed
dkms status
lsmod | grep nvidia

If you have installed any version, you must purge first, old will conflict with new as new install does not overwrite old version.
sudo apt-get remove --purge nvidia-*
sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms
This xorg file may not exist, so if error that would be ok
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

sudo ubuntu-drivers devices
If you just want default version - recommended one
sudo ubuntu-drivers autoinstall
Or you can manually choose any in list.
sudo apt-get install nvidia-XXX 

Some after a purge need this:
sudo apt update
sudo apt install linux-generic
sudo apt full-upgrade

[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351)

---

### Post by agrayray on 2021-12-27
**How did you install nVidia driver?**
- Just from doing the Ubuntu update prompt I got when logged into my system.
- From looking at the apt history log (apt-history-log-2.txt from my previous attachment), it appears the update did the following "nvidia" changes:
```

Upgrade: xserver-xorg-video-nvidia-470:amd64 (470.82.00-0ubuntu0.20.04.1, 470.86-0ubuntu0.20.04.1), libnvidia-cfg1-470:amd64 (470.82.00-0ubuntu0.20.04.1, 470.86-0ubuntu0.20.04.1)
Upgrade: libnvidia-compute-470:amd64 (470.82.00-0ubuntu0.20.04.1, 470.86-0ubuntu0.20.04.1), libnvidia-decode-470:amd64 (470.82.00-0ubuntu0.20.04.1, 470.86-0ubuntu0.20.04.1)
Upgrade: libnvidia-fbc1-470:amd64 (470.82.00-0ubuntu0.20.04.1, 470.86-0ubuntu0.20.04.1)
Upgrade: libnvidia-common-470:amd64 (470.82.00-0ubuntu0.20.04.1, 470.86-0ubuntu0.20.04.1)
Upgrade: libnvidia-extra-470:amd64 (470.82.00-0ubuntu0.20.04.1, 470.86-0ubuntu0.20.04.1)
Upgrade: libnvidia-gl-470:amd64 (470.82.00-0ubuntu0.20.04.1, 470.86-0ubuntu0.20.04.1)
Upgrade: libnvidia-encode-470:amd64 (470.82.00-0ubuntu0.20.04.1, 470.86-0ubuntu0.20.04.1)
Upgrade: nvidia-compute-utils-470:amd64 (470.82.00-0ubuntu0.20.04.1, 470.86-0ubuntu0.20.04.1)
Upgrade: nvidia-kernel-source-470:amd64 (470.82.00-0ubuntu0.20.04.1, 470.86-0ubuntu0.20.04.1)
Upgrade: nvidia-utils-470:amd64 (470.82.00-0ubuntu0.20.04.1, 470.86-0ubuntu0.20.04.1)
Upgrade: libnvidia-ifr1-470:amd64 (470.82.00-0ubuntu0.20.04.1, 470.86-0ubuntu0.20.04.1)

```

```

Upgrade:  ...
nvidia-settings:amd64

```

```

Remove: nvidia-kernel-source-470:amd64 (470.86-0ubuntu0.20.04.1)

```

[B]#What is installed
[/B]```

$ dkms status

$ lsmod | grep nvidia
nvidia_uvm           1036288  0
nvidia_drm             61440  2
nvidia_modeset       1200128  1 nvidia_drm
nvidia              35315712  2 nvidia_uvm,nvidia_modeset
drm_kms_helper        237568  2 nvidia_drm,i915
drm                   548864  20 drm_kms_helper,nvidia,nvidia_drm,i915

$ ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
modalias : pci:v000010DEd00001FB9sv00001028sd0000097Ebc03sc02i00
vendor   : NVIDIA Corporation
model    : TU117GLM [Quadro T1000 Mobile]
manual_install: True
driver   : nvidia-driver-495 - distro non-free
driver   : nvidia-driver-450-server - distro non-free
driver   : nvidia-driver-418-server - distro non-free
driver   : nvidia-driver-470-server - distro non-free
driver   : nvidia-driver-460-server - distro non-free
driver   : nvidia-driver-460 - distro non-free
driver   : nvidia-driver-470 - distro non-free recommended
driver   : xserver-xorg-video-nouveau - distro free builtin

== /sys/devices/pci0000:00/0000:00:1f.4 ==
modalias : pci:v00008086d000006A3sv00001028sd0000097Ebc0Csc05i00
vendor   : Intel Corporation
driver   : oem-somerville-varys-meta - distro free

```
Not sure why it says *manual_install= true* as I have never installed any drivers explicitly and yes, I just have and want to use the default install and updates from Ubuntu.  I was trying to convey that it was just the standard Ubuntu updates that caused these issues with my specific computer.

If I manually purged the drivers and installed the old versions, wouldn't this simply re-surface again if I did an Ubuntu update to my system?  That is more my question.  I would like to take my computer back to the state with the updates prior to last the update I did that broke things.

Not even sure how I would recover from the other packages I choose to remove based upon the update recommendations either.

?

Thanks again for all your help!

---

### Post by oldfred on 2021-12-27
Did dkms status not show anything?
That would mean you have downloaded drivers, but not added them to kernel.

Does this update?
sudo update-initramfs -u 
or
sudo update-initramfs -k all -c

dkms status

---

### Post by agrayray on 2021-12-28
Yes, dkms status returned nothing.

Are these normally added to the kernel?  Again, all I did was do a normal update, but the first time I ran the update I did get an error that said only partial update was possible, please check your internet connection.  It looked like the cause of this was my docker entry and after commenting that out from sources I proceeded to do the update again....which seemingly went fine .that was the update that changed my nvidia software..???

I will do update-initramfs -u shortly..(backing up my system first)

---

### Post by ubfan1 on 2021-12-28
The Ubuntu Nvidia driver updates (Software & Updates/Addiional drivers) include the script/glue code to gin up a new driver when the kernel updates occur -- other non-Ubuntu Nvidia driver sources don't.  Maybe just switch to the nouveau driver, clean out all the *nvidia* packages, and reinstall from the Software & Updates /Additional Drivers tab.  the 470 is the "tested" one, but I've been using the 495 without any issues.

---

### Post by agrayray on 2021-12-30
I think I would prefer to roll my system back rather than install yet another different driver etc...

I would rather go with a system that worked well such as either a system updated to the point it was before my last update which broke things or just do a base install of Ubuntu 20 and turn off updates.  Updates to my base OS aren't that big of deal to me, because I do most things in virtual machines and docker containers anyway. 

Is it possible to do a new install and update the computer not to latest updates but update it only to a point in time or basically one version back the previous update..or just easily rollback the previous update?

---

### Post by ubfan1 on 2021-12-30
You should always be able to select the "Advanced options" from the grub menu, and then select the previous kernel, which has the same (working) Nvidia driver it always did.  Booting in "Save" mode should also automatically use the nouveau driver, if you decide to clean out the old nvidia packages, and install from the standard repos.

---

