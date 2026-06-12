---
title: "Nvidia's Installer"
date: 2010-08-15
forum: Installation &amp; Upgrades
---

### Post by darkenvy6 on 2010-08-15
I have never in my life got this to install correctly. No the recommended drivers dont seem tow work well for me so I want to install the drivers properly from the website. Something that people have said solvs many problems. I keep getting "The distribution-provided pre-install script failed!  Continue installation 
   anyway?" Anyways here is my log.

> nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sun Aug 15 15:34:52 2010
installer version: 256.44

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  no cc version check     : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  compat32 install chroot : (not specified)
  compat32 install prefix : (not specified)
  compat32 install libdir : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 256.44.
-> Running distribution scripts
   executing: '/usr/lib/nvidia/pre-install'...
-> done.
-> The distribution-provided pre-install script failed!  Continue installation 
   anyway? (Answer: No)
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com]("http://www.nvidia.com").

---

### Post by realzippy on 2010-08-15
have a look at the drivers [README]("http://us.download.nvidia.com/XFree86/Linux-x86_64/256.44/README/index.html") file,there is a section about [removing the existing nouveau driver]("http://us.download.nvidia.com/XFree86/Linux-x86_64/256.44/README/commonproblems.html#nouveau") before installing;
also here in the forums some threads exists about removing nouveau,but
everything you need to know is there in the README.Feel free to ask...

---

### Post by darkenvy6 on 2010-08-15
You think this is it? Can I get a little bit of help with this? I have a feeling ill screw up my display driver irreversibly unless I do a complete reinstall :\

What I got from this is that Nouveau, the generic display driver, must be interfering with the nvidia-installer.

---

### Post by MAFoElffen on 2010-08-15
Just curious- What model is your NVidia Card and what version of Ubuntu?

EDIT/ADD: I have NVidia's drivers installed in all the OS'es in my sig except Ubuntu Server Edition. I use a work-around for that.

---

### Post by darkenvy6 on 2010-08-15
I have a 9800GTX and I'm running 10.04 ubuntu gnome

---

### Post by realzippy on 2010-08-16
Also running 10.04/GTX 9800...

There is **no** advantage in installing the NVIDIA driver from there website compared to *jockey* (GUI Tool Administration/Hardware drivers) since
it is the same driver (at least if you include some Xorg PPA in your sources and install the "current" driver).Disadvantage is that you have
to reinstall every kernel update...so only install manually if jockey does not work.

---

### Post by darkenvy6 on 2010-08-16
Wow I would have responded waaay sooner but the login system wouldn't let me log in! Meh whatever....

Anyways the jockey drivers I do not like. I cannot use visual effects on any level but basic without returning some error, my monitor's settings are locked on full brightness (yes on the monitor I am NOT able to change contrast. Ubuntu locks my monitor.) I think it has something to do with Nvidia's 3D Vision but I have not done anything with that. Thirdly I have had MANY issues with 3 monitors and the mouse locking up and restarting the X Display. I am very upset with these driver. Crash course in X display modding? Help me get the Monitor brightness hacked off and I'll be happy for the most part.

Note: I use xinerama Desktoping

---

### Post by realzippy on 2010-08-18
*"Crash course in X display modding?"*

[here]("http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/index.html")

As formerly said,if your driver installed fine with Hardware drivers tool,there will be no advantages to a manually installed driver,your problems will
persist.BTW,lots of problems....3 monitors!
contrast/brightness can be adjusted in nvidia-settings;would suggest to start with 1 monitor,then eliminate problems,then plug in 2nd monitor,eliminate problems,aso...

---

### Post by darkenvy6 on 2010-08-18
> **realzippy said:**
> *"Crash course in X display modding?"*

[here]("http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/index.html")

As formerly said,if your driver installed fine with Hardware drivers tool,there will be no advantages to a manually installed driver,your problems will
persist.BTW,lots of problems....3 monitors!
contrast/brightness can be adjusted in nvidia-settings;would suggest to start with 1 monitor,then eliminate problems,then plug in 2nd monitor,eliminate problems,aso...

The contrast/brightness only works for one monitor (whichever one is plugged in the first DVI slot apparently) so I naturally put that on the samsung 3D monitor which is stuck in full brightness/contrast ("Magicbright locked"). So no other monitor can be adjusted from the nvidia-settings. Also its not like the settings of brightness/contrast stay after reboot anyways. Is it supposed to? I suppose it should but idk.

---

### Post by realzippy on 2010-08-19
...you have to save your configuration so it persists a reboot..

---

### Post by ratcheer on 2010-08-19
I had similar problems installing the Ubuntu nVidia driver. There were no problems doing this through release 9.10, but since 10.04 it has been a real pain.

Here is how I solved it on my system:

1) If any nVidia proprietary driver is showing as installed in jockey (the System Hardware Devices gui), remove it and reboot.

2) Go to this website and follow the instructions to add the ppa to your system. [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

3) Update your package manager, e.g., "sudo apt-get update" or aptitude or whatever you usually use.

4) Go back to jockey and install nvidia-current (recommended). When the installation completes, you will be instructed to reboot.

You should come up with a working nVidia 256.44 driver installed. I cannot be sure it will work for you, but as I said, it worked for me (on both Lucid and Maverick). Good luck!

Tim

---

### Post by Cavsfan on 2010-08-19
Wow! I have a nVidia Geforce 9800 GT 512MB and the recommended driver has always worked for me. 
I don't understand why it doesn't for you.

---

### Post by realzippy on 2010-08-19
Both read post #7 ?

Problem is not to *install* the nvidia driver...3 monitor setup corrupted and OP
hopes that driver from NVIDIA website is better than jockey's...

---

### Post by Cavsfan on 2010-08-19
I wonder if this might help: this is in my **/etc/default/grub** file:

**gksu gedit /etc/default/grub**

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1920x1200-32,mtrr=3,scroll=ywrap"
```Compare that to yours. My monitor's native resolution is 1920x1200, but I thought that maybe the "**video=uvesafb**" part 
might help you since you have the same kind of card as I do and mine works superbly.

Or maybe something in there will help I hope!

---

### Post by darkenvy6 on 2010-08-19
ah of course! now any way to disable this magicbright? or what causes it? I want to find the cause and f*** sh** up. I'm flat out tired of it :mad:  ( <--- look at the seriousness of that face)

---

### Post by darkenvy6 on 2010-08-19
Okay I applied the nvidia drivers again and now I have no sound at all. To further the problem I can no longer mount any other drives than root!!! HELP

---

### Post by darkenvy6 on 2010-08-19
Update: I decided to just screw it and reinstall ubuntu. I had a worst issue to follow....

Anyways I am now using Nvidia drivers version 173 over the newer drivers. So far this proves to be a much etter driver and does not have the magicbright monitor settings locked on "3D ready" monitors. I will post more as my issues of adding monitors continues. Because I will have problems with this :P.

---

