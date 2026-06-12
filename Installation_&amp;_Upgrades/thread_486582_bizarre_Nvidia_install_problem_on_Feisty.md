---
title: "bizarre Nvidia install problem on Feisty"
date: 2007-06-28
forum: Installation &amp; Upgrades
---

### Post by kachun on 2007-06-28
Hi,

I have a rather old SGI 330 workstation running dual Pentium IIIs, with an NVIDIA Quadro2 Pro card.  I had installed Edgy without any problems.  But when I tried to upgrade to Feisty, my long rough journey began ...

First I tried to do a fresh install from the LiveCD.  I was unable to even completely log in with that.  When I got to the login screen, the sound cue that normally plays once kept repeating.  After entering the password, another sound cue started repeating on top of the first.  The screen would stay blank (except for the creamy orange background and the mouse cursor which could still be moved around).  The machine was effectively hung and I would have to reboot.

I thought I had a corrupt copy of the CD so I didn't give it much thought.  I eventually did the upgrade through the System->Upgrade Manager.  After rebooting, I discovered the CD wasn't the problem: it was Feisty's interaction with whatever my hardware setup was.  (I also have an Ensoniq ES1371 [AudioPCI-97] soundcard which may also be confusing things, considering the weird sound issue.)

If I let the now 7.04 OS-enabled machine reboot normally (to the 2.6.20-16 kernel), I get the behavior described above when I first inserted the Feisty CD.  I can reboot to the 2.6.17-10-generic kernel, and get X working.  However I've been trying to get the Nvidia drivers properly installed, after googling and finding similar Nvidia problems with Feisty, but finding no one else with the unique problems that I've encountered.

According to [http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html) I need the legacy drivers.  So I've used apt-get to install nvidia-glx-legacy and nvidia-glx-config. Running the latter and dpkg-reconfigure xserver-xorg seems to set up xorg.conf without any problems, but I can't restart X without it failing and getting messages about the inability to load the Nvidia kernel modules.  I can re-edit xorg.conf to switch "nvidia" to "vesa", and can get a minuscule screen resolution of 1024x768, but I really want my full resolution of at least 1600x1200!  Even after configuring xserver-xorg and toggling on the higher resolutions, I keep getting downgraded to 1024x768 in vesa mode.

One other thing I've tried is run Administration->Restricted Drivers Manager.  However now I get a pop-up with the message:

   You need to install the package
   linux-restricted-modules-2.6.17-10-generic
   for this program to work.

Doing a search for 2.6.17-10 package doesn't turn up anything useful.  So it doesn't look like I can win.  I can't run in the 2.6.20-16 kernel, and the 2.6.17-10 kernel lets me start up X but I can't seem to get anywhere with it!

(There was one other kernel option in the startup: 2.6.17-11.  This turned out to be even less useful than 2.6.20-16 since the machine froze right after the orange startup progress bar against the black background showed up, and before it had grown to more than a few pixels in length.)

--kachun

---

### Post by renzokuken on 2007-06-28
enable the universe and multiverse repos (can be done in synaptic, "sources" or something like that. update/reload synaptic then search for "restricted".

then match your kernel to the right restricted modules package, install

and try again. you may have to reinstall the nvidia driver again too

---

### Post by kachun on 2007-06-28
Hi,

> **renzokuken said:**
> enable the universe and multiverse repos (can be done in synaptic, "sources" or something like that. update/reload synaptic then search for "restricted".

then match your kernel to the right restricted modules package, install

and try again. you may have to reinstall the nvidia driver again too

Okay I have universe and multiverse on (basically all possible repositories loaded), and linux-restricted-modules-2.6.17.-10-generic does show up with a search for restricted.  However now I get the message:

> 
  **Could not mark all packages for installation or upgrade**

  The following packages have unresolvable dependencies.  Make sure that all required repositories are added and enabled in the preferences.

  linux-restricted-modules-2.6.17-10-generic:

  Package linux-restricted-modules-2.6.17-10-generic has no available version, but exists in the database.

  This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list


Switching servers doesn't help, presumably because all of the servers are the same.

--kachun

---

### Post by kachun on 2007-06-28
Okay it looked like most of the repositories were down for updates just until now.  I did a fresh re-install of nvidia-glx-legacy, nvidia-xconfig, and nvidia-settings from synaptic.  The new xorg.conf finally got me into a much higher resolution display and out of the 1024x768 ghetto.  However I had to switch the Driver from "nvidia" to "nv" to get it to work.  So this mean I am still not using my Nvidia card?  ("lsmod | grep nv" doesn't show anything, suggesting that this is so.)

Also I am still running the 2.6.17-10 kernel with no way to use the 2.6.20-16/15 one without the machine freezing after logging in.  And I can't seem to download linux-restricted-modules-2.6.17-10 (see the previous message) and therefore can't run restricted-manager.

--kachun

---

### Post by bluknight on 2007-06-28
> **kachun said:**
> 
Also I am still running the 2.6.17-10 kernel with no way to use the 2.6.20-16/15 one without the machine freezing after logging in.  And I can't seem to download linux-restricted-modules-2.6.17-10 (see the previous message) and therefore can't run restricted-manager.


I am also running Feisty with 2.6.17-11 kernel. The kernel 2.6.20-16 that came with 7.04 doesnt even boot up on my Dell system. I do not have the freezing problem with the Edgy kernel. But I had to manually copy /lib/modules/2.6.17-11 (and the firmware folder) from Edgy to the Fiesty partition. That solved my restricted modules and I'm happy to be running Feisty.

HTH

---

