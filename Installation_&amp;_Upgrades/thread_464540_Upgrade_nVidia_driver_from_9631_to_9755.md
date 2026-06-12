---
title: "Upgrade nVidia driver from 9631 to 9755"
date: 2007-06-04
forum: Installation &amp; Upgrades
---

### Post by steveneddy on 2007-06-04
I was wondering the correct way to upgrade my nVidia driver from Synaptic. I noticed that there is an entry:

nvidia-glx-new

but I have nvidia-glx installed.

AND - I believe that I will have to install the new kernel headers also? and remove the old kernel headers?

Can this all be done in Synaptic or do I have to utilize the CLI?

What exactly would I do? Uninstall everything nvidia-glx including headers and then reinstall, without a reboot, the new kernel headers and nvidia-glx-new?

-SE

EDIT:

I don't want to frag my next kernel update by running a newer driver without the correct kernel headers that will update simultaneously. So many people have the problem of reinstalling a new video driver when there is a kernel update and I can't go through that all the time anymore.

---

### Post by Pumalite on 2007-06-04
> **steveneddy said:**
> I was wondering the correct way to upgrade my nVidia driver from Synaptic. I noticed that there is an entry:

nvidia-glx-new

but I have nvidia-glx installed.

AND - I believe that I will have to install the new kernel headers also? and remove the old kernel headers?

Can this all be done in Synaptic or do I have to utilize the CLI?

What exactly would I do? Uninstall everything nvidia-glx including headers and then reinstall, without a reboot, the new kernel headers and nvidia-glx-new?

-SE

EDIT:

I don't want to frag my next kernel update by running a newer driver without the correct kernel headers that will update simultaneously. So many people have the problem of reinstalling a new video driver when there is a kernel update and I can't go through that all the time anymore.

Running the Nvidia driver from synaptic is not the same as installing a new driver from Nvidia. I f you have an  NVIDIA card, I would recommend downloading 9755 from Nvidia and put it in your /home folder, then make sure you have: make, autocong, kernel-headers matching your kernel,  gcc++. Then reboot in 'Recovery mode', as root then cd /path/to/driver and then run your NVIDIA driver .run file. BTW, is obligatory to reinstall your graphics drivers after each kernel update. Is better to uninstall previous drivers first, but if you don't do it, the .run file does it for you, as well as reconfiguring your xorg file.

Good luck.

---

### Post by steveneddy on 2007-06-04
But this makes my X prone to crashing when a new kernel update happens. 

I just would like a newer nVidia driver without the pain of reinstalling the driver after a kernel update.

So.....would the Synaptic method work for this if I installed the new kernel headers for this driver also?

---

### Post by dfreer on 2007-06-04
I'm thinking if you use the driver provided in the repositories, as long as you watch carefully whenever there is a new kernel released to make sure the corresponding linux-restricted-modules is updated as well, you should never experience X crashing because the driver needs reinstalled. Most of the time the ubuntu guys release both at the same time so you should be ok anyways. And the kernel doesn't update THAT often unless you are running gutsy :) 

However, the official driver from nvidia WILL need recompiled on every kernel update regardless, that's the problem with it. stick with nvidia-glx or nvidia-glx-new. You shouldn't need to mess with kernel headers, although I'm not quite sure on the proper way to uninstall an nvidia driver, the correct way of installing one is by using the restricted drivers manager OR sudo apt-get install nvidia-glx-new, and then editing xorg.conf (backup first!!!)

---

### Post by steveneddy on 2007-06-04
I already use the 9631 nVidia driver. I just want to upgrade to the newer 9755 version from Synaptic and not have to recompile when updating kernel comes in an update.

---

### Post by steveneddy on 2007-06-05
OK - here's what i did.

I went to Synaptic and uninstalled
```
   
nvidia-glx 
```

nVidia driver and installed the 
```
 
nvidia-glx-new 
```

video driver.

I then restarted X and came to a command line and logged in, did a 

```
sudo dpkg-reconfigure xserver-xorg
```

and then did a 

```
sudo /etc/init.d/gdm restart
```

to restart the log in manager. If you don't restart gdm, then all you get is raw X and that is ugly. Try it, you will see. If you DO only the startx command, after you log off you will come back to a CLI screen and you will have to start gdm anyway, so do it now.

I then looked at my xorg.conf file & determined that it wasn't quite right, so i copied my main backup xorg.conf file to the current xorg.conf file by

```
sudo cp /etc/X11/xorg.conf.masterbu /etc/X11/xorg.conf
```

where "xorg.conf.masterbu" is the name of MY backup file. Yours may be different.

I restarted X again by Ctrl + Alt + Backspace and GDM was running and I loggen in as normal.

I then went to 

```
gksudo nvidia-settings
```

and checked that the correct driver was being used, and since I had put in my xorg.conf file the command for   Coolbits, it now showed up in my nvidiaa-settings window. Now I can overclock my video card if I want to.

WARNING!!!

Before you start doing stuff like this, especially if you are new to editing files, please back up your xorg.conf file by doing a

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

This will save you if you hose something.

I do not recommend this for the faint of heart because if you get lost, you can really frag you system.

OK - one more thing. If you are stuck in a command line and can't get a GUI, just do this

```
nano /etc/X11/xorg.conf
``` and change the driver to "nv" instead of "nvidia" and you should be set.

This will give you a GUI but still give you time to sort things if you have probs.

The "nv" driver is a safe video driver for nVidia cards and will at least get you to a desktop.

After you get things running, go back and change the driver to "nvidia" to use the new driver.

Just remember to

```
sudo /etc/init.d/gdm restart
```

Good luck - we're all counting on you.

-SE

---

### Post by steveneddy on 2007-06-09
By using this newer version of the nVidia driver from the repositories, I avoided the dreaded kernel re ompile for the video driver.

After the last kernel update I was worried that I would have to go through all of that nonsense again, but not so is the case. The update went off without a hitch and the lappie booted up afterwards into a GUI perfectly.

The 9755 nVidia driver is a great video driver that works well with my hardware. The options are are greater than the 9631 driver and the picture is fabulous compared to the other driver. I have tweaked it a little to get some great vibrance and color correction from my monitor and I must say that, especially when viewing HD movie trailers from Apple full screen, it really comes into it's own.

I have a System76 Serval Performance with the nVidia GeForce GO 7600 with 256MB VRAM and a Cre 2 Duo processor. I use 

```
gksudo nvidia-settings
```

to adjust the card.

---

