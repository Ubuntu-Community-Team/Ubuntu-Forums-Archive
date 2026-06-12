---
title: "[SOLVED] Brand New 8.04 Install.... Nvidia drivers HELP"
date: 2008-07-09
forum: Installation &amp; Upgrades
---

### Post by sanike on 2008-07-09
Hi all, first off I know this has been touched on before but none of the articles are up to date for 8.04 or its just not working.

I have the installed drivers from Ubuntu already done, as it was in the install but the screen is fuzzy (its like every second line is deleted).  I noticed that the Linux drivers on the nvidia site are as of June 11/08 so I figured they must be of a higher quality.

I have followed their Linux readme file to the letter and gotten nowhere (because I have no idea what I'm doing).

I first downloaded the file from the nvidia site.

I've gotten in the terminal as root, I've attempted to change the runlevel to 'init 3' and the terminal line doesn't give a confirmation of init 3, nothing changes.  I cannot seem to 'rmmod nvidia' as it says its still in use.

If someone can give me a step by step of how to do this it'd be helpful, or point out whrere I'm going wrong.

[http://us.download.nvidia.com/XFree86/Linux-x86/173.14.09/README/index.html](http://us.download.nvidia.com/XFree86/Linux-x86/173.14.09/README/index.html) is the readme guide

Thanks for everyone's help
:)

Also, I was using this guide as well [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+NVidia&back=HOWTO+INDEX+Hardware](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+NVidia&back=HOWTO+INDEX+Hardware)

---

### Post by jbrackett on 2008-07-09
This is how I always install Nvidia drivers

1.  Ctrl-Alt-F3
2.  sign in and run sudo /etc/init.d/gdm stop  (stop X)
3.  sudo sh <<driver>>
4.  follow on screen directions
5.  sudo /etc/init.d/gdm start (get back into X)

---

### Post by sanike on 2008-07-09
It says

No precompiled kernal interface was found to match your kernel; would you like the installer to attempt to downlaod a kernel interface for your kernel from the NVIDIA ftp site (ftp...)

I selected no

Then ok to creating a new interface

ERROR: you do not appear to have libc header files installed on your sister
PLEASE install your distro's libc dev package

Error: install failed please see log file etc..

I can post the logfile if you like... but its fairly long


Should I just download the interface? and if so should I enabled DSL prior to installation? or what....

---

### Post by jbrackett on 2008-07-09
Do:
sudo apt-get install build-essential

then try again

---

### Post by sanike on 2008-07-09
Got it to install, restarted X using /etc/init.d/gdm start as posted above

I got a weird window asking to set display opts, I wasn't allowed over 800x600, and when I went to drivers, it had some VEGA driver set up

When I changed it to nvidia, it wasn't accepting
I changed it to my specific card type nvidia > geforce fx

and now I post in 800x600, with no hardware accel, when I put hardware accel on, I'm back in the same place I was before... options?

---

### Post by jbrackett on 2008-07-09
At the end of the driver install it should have asked you if you wanted to set up your resolution.  I'm not certain of the exact wording, and I'm at work now so I can't check.

Also, on restart did the Nvidia logo appear before the log in screen?

---

### Post by sanike on 2008-07-09
It didn't ask and no it did not

---

### Post by jbrackett on 2008-07-09
I'm thinking it would ask to update your xorg config file... wish I was at home so I could check.

My guess is that is your problem now.  Could you post the contents of your xorg.conf (/etc/X11/xorg.conf)

If its using the nvidia driver it will have a section similar to:

```
Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTS"
EndSection
```
If not, the "Driver" parameter will be "nv"

---

### Post by sanike on 2008-07-09
```
Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"NVIDIA GeForce FX (generic)"
	Busid		"PCI:3:0:0"
	Driver		"nv"
	Screen	0
	Vendorname	"NVIDIA"
EndSection

```

its an AGP card... would the busid be causing a problem?

And if I haven't made it clear yet, I really appreciate everything your doing to help me :)

---

### Post by sanike on 2008-07-09
I just rebooted the system (went for lunch), and now the screen is in 1024x768 running at 81hz (which seems high for this monitor).  nvidia 3d accel is off (as per sys>admin>hardware drvs) and the output on xorg.conf is the same as before


Also the startup screen was huge, to the point where I could barely see the login bar as it was in the lower right hand of my screen....

---

### Post by jbrackett on 2008-07-09
Its not using the Nvidia drivers because the xorg.conf is still pointing at the 'nv' driver and not the 'nvidia' driver.

First try: sudo nvidia-xconfig then restart X (ctrl-alt-backspace)

You can try going to Applications->System Tools->Nvidia xserver settings.  Then choose Display Configuration and make any changes and press the "Save to X Configuration File" button.  It may complain about it not being active or something and ask you if you want to enable it and choose yes if so.

You probably need to restart X after that

If that still doesn't work you could try installing the drivers again and be sure to look for it asking you to set up a configuration file after it installs.

If none of this works look at this post: [http://ubuntuforums.org/showpost.php?p=5086971&postcount=6](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6)

---

### Post by sanike on 2008-07-10
> **jbrackett said:**
> Its not using the Nvidia drivers because the xorg.conf is still pointing at the 'nv' driver and not the 'nvidia' driver.

First try: sudo nvidia-xconfig then restart X (ctrl-alt-backspace)

I did this and it worked as it was supposed to
> 
You can try going to Applications->System Tools->Nvidia xserver settings.

However this came up with "you do not appear to be using the NIVIDA X driver. Pleas edit your X config file (jut run 'nividia-xconfig as root) and restart the X server

> 
Then choose Display Configuration and make any changes and press the "Save to X Configuration File" button.  It may complain about it not being active or something and ask you if you want to enable it and choose yes if so. 

Only options available:
enable tooltips, display status bar, slider text entries, include x display names in the config file, and Show Really quit? Dialog.

> 

You probably need to restart X after that

If that still doesn't work you could try installing the drivers again and be sure to look for it asking you to set up a configuration file after it installs.

If none of this works look at this post: [http://ubuntuforums.org/showpost.php?p=5086971&postcount=6](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6)

How can I wipe the drivers clean so it'll install itself, right now its runnin in high graphics mode using propetiary drivers so I'm going to test this out

---

### Post by sanike on 2008-07-10
Trying a newer card, 7300GT
still nothing

---

### Post by sanike on 2008-07-10
Still messing with this, it keeps resetting my card to VESA Compliant crap after everytime I force the card settings to change... and I can't get any higher than either 640 or 800x600 @ 61hz, my screen resolution is locked.

This is really pissing me off, how do I delete the drivers so it goes backto the one installed when I booted?

---

### Post by jbrackett on 2008-07-10
```
sudo nvidia-installer --uninstall
```

to uninstall the binary drivers

I'm not sure what the state of your xorg.conf if that is changed you will need to roll that back to a previous version.

Personally I would uninstall the drivers and reinstall them making sure you let it write your xorg.conf at the end.

Did you take a look at: [http://ubuntuforums.org/showpost.php...71&postcount=6](http://ubuntuforums.org/showpost.php...71&postcount=6)

Its essentially what I've said but with a lot more detail.

---

### Post by sanike on 2008-07-10
I'm going to try that posting you gave me

I'll update here on what happens

---

### Post by sanike on 2008-07-11
Seems to have worked, However my lag problems are still in my game

so therefore it wasn't the videocard (irony)

Thank you so much for your help :)

---

### Post by vistauser on 2008-07-11
> **jbrackett said:**
> This is how I always install Nvidia drivers

1.  Ctrl-Alt-F3
2.  sign in and run sudo /etc/init.d/gdm stop  (stop X)
3.  sudo sh <<driver>>
4.  follow on screen directions
5.  sudo /etc/init.d/gdm start (get back into X)

when I hit Ctrl-Alt-F3 my screen goes blank until I reboot.

---

### Post by jbrackett on 2008-07-11
> **sanike said:**
> Seems to have worked, However my lag problems are still in my game

so therefore it wasn't the videocard (irony)

Thank you so much for your help :)

Great, I'm glad it worked.  Too bad it didn't help with your problem but at least you've gained some knowledge :)


> when I hit Ctrl-Alt-F3 my screen goes blank until I reboot. 

You can try ctrl-alt-F1/F2/F4/F5/F6 its just different tty sessions.

If you are using Gutsy you might find a solution here - [https://answers.launchpad.net/ubuntu/+question/15560](https://answers.launchpad.net/ubuntu/+question/15560)

---

### Post by oldos2er on 2008-07-11
"No precompiled kernal interface was found to match your kernel; would you like the installer to attempt to downlaod a kernel interface for your kernel from the NVIDIA ftp site (ftp...)

I selected no"

 I think this is your problem right here. If you can , re-run the install and select 'yes.'

---

### Post by vistauser on 2008-07-11
> **oldos2er said:**
> "No precompiled kernal interface was found to match your kernel; would you like the installer to attempt to downlaod a kernel interface for your kernel from the NVIDIA ftp site (ftp...)

I selected no"

 I think this is your problem right here. If you can , re-run the install and select 'yes.'

I'm having the same problem as this guy, except it's a bit worse.  I have never gotten the driver to install and I've tried about a hundred suggestions.  It always says it doesn't detect the video card.  I put yes on that part and it says it doesn't have anything for my kernel and it will need to build one.  Then it builds one and says that it's the wrong kernel.  This has got to be the most difficult driver install of any OS I have ever seen.

---

### Post by upchucky on 2008-07-11
look here, 



[http://ubuntuforums.org/showpost.php?p=5086971&postcount=6](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6)

---

### Post by oldos2er on 2008-07-12
> **vistauser said:**
> I'm having the same problem as this guy, except it's a bit worse.  I have never gotten the driver to install and I've tried about a hundred suggestions.  It always says it doesn't detect the video card.  I put yes on that part and it says it doesn't have anything for my kernel and it will need to build one.  Then it builds one and says that it's the wrong kernel.  This has got to be the most difficult driver install of any OS I have ever seen.

 Sorry my suggestion didn't work for you. The next thing to try would be EnvyNG; see [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by sanike on 2008-07-13
ALSO just FYI prior to running the nvidia installer outside x

MAKE SURE YOUR CONNECTED TO THE INTERNE

I didn't realize I wasn't connected so therefore the ftp site never got reached...

---

### Post by vistauser on 2008-07-13
> **oldos2er said:**
> Sorry my suggestion didn't work for you. The next thing to try would be EnvyNG; see [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

I get "Exception: EnvyNG Error: Nvidia card not found."

I pretty much give up.

---

### Post by Pumalite on 2008-07-13
What card do you have? If Desktop; go inside and make sure card is well pressed on the slot. Make sure you have the right headers for the kernel.

---

