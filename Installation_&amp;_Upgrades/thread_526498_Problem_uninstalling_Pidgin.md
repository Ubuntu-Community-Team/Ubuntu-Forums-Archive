---
title: "Problem uninstalling Pidgin"
date: 2007-08-15
forum: Installation &amp; Upgrades
---

### Post by Baresi on 2007-08-15
Hello, I'm new to the forums and linux. I recently started using Ubuntu Feisty and haven't had any problems with it. In fact, I'm extremely happy I switched. But today I tried installing Pidgin's deb and all hell broke loose. :mad:

First, it did appear as installed in the Synaptic Package Manager, but didn't showed up in the Internet menu. Then I tried to uninstall it and re-install GAIM and it gave me this error:
```
E: /var/cache/apt/archives/gaim_1%3a2.0.0+beta6-1ubuntu4_i386.deb: trying to overwrite `/usr/share/dbus-1/services/gaim.service', which is also in package pidgin

```

Then it told me I had a broken dependency, nautilus-sendto, but when I try to re-install it, it gives me the same error.

The update manager isn't working either. It tells me this:
```
Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.
```

I input the command in the terminal and it ends up showing me the same error that gave me while un-installing Pidgin.

Sorry for what probably si a dumb, simple problem, but I can admit that I'm a complete noob. :)

Thanks in advance for any help.

---

### Post by Gremlinzzz on 2007-08-15
did ya try 
sudo apt-get install -f

---

### Post by Gremlinzzz on 2007-08-15
or
sudo dpkg --configure -a
or

Open synaptic, click edit, click Fix broken packages, click reload, click mark all upgrades

---

### Post by Baresi on 2007-08-15
Pidgin is working fine now, but the update manager is not.

> **Gremlinzzz said:**
> did ya try 
sudo apt-get install -f

This is what I get when I input the command:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libsm-dev libice-dev x11proto-xext-dev libaudiofile-dev libaudio-dev
  libsdl1.2-dev x11proto-kb-dev libglib2.0-dev libkexif1 mesa-common-dev
  libxdmcp-dev libdirectfb-extra libwavpack0 libpng12-dev libdirectfb-dev
  xtrans-dev setserial x11proto-core-dev libexif-dev libgphoto2-2-dev
  libusb-dev libglu1-mesa-dev libxt-dev libxext-dev libjpeg62-dev libntfs8
  zlib1g-dev x11proto-input-dev libfreetype6-dev libesd0-dev libxau-dev
  libasound2-dev libgl1-mesa-dev libslang2-dev libncurses5-dev libx11-dev
  libartsc0-dev libaa1-dev x-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gaim
Suggested packages:
  libzephyr3 tcl8.4 tk8.4
The following NEW packages will be installed:
  gaim
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/1741kB of archives.
After unpacking 4923kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 186869 files and directories currently installed.)
Unpacking gaim (from .../gaim_1%3a2.0.0+beta6-1ubuntu4_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/gaim_1%3a2.0.0+beta6-1ubuntu4_i386.deb (--unpack):
 trying to overwrite `/usr/share/dbus-1/services/gaim.service', which is also in package pidgin
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/gaim_1%3a2.0.0+beta6-1ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


> **Gremlinzzz said:**
> or
sudo dpkg --configure -a

This is what I get when I input this other command:
> dpkg: dependency problems prevent configuration of nautilus-sendto:
 nautilus-sendto depends on gaim (>= 1:2.0.0+beta6); however:
  Package gaim is not installed.
dpkg: error processing nautilus-sendto (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on nautilus-sendto; however:
  Package nautilus-sendto is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nautilus-sendto
 ubuntu-desktop

> Open synaptic, click edit, click Fix broken packages, click reload, click mark all upgrades

And doing this marks Gaim as the only upgrade, but it  still won't let me install it. 

From reading all that I guess I messed something up with Nautilus and Ubuntu Desktop, but what?

---

### Post by jdong on 2007-08-15
This is why you should not install packages from non-official Ubuntu sources.

Try **dpkg --remove pidgin**, then **apt-get -f install** and see if that corrects it.

---

### Post by Baresi on 2007-08-15
jdong, this is what I get:

> Password:
(Reading database ... 187130 files and directories currently installed.)
Removing pidgin ...
dpkg - warning: while removing pidgin, directory `/usr/local/share/applications' not empty so not removed.
dpkg - warning: while removing pidgin, directory `/usr/local/share' not empty so not removed.
dpkg - warning: while removing pidgin, directory `/usr/local/lib' not empty so not removed.
dpkg - warning: while removing pidgin, directory `/usr/local' not empty so not removed.


---

### Post by jdong on 2007-08-15
That still looked like it succeeded though; those messages are somewhat normal (as in, non-fatal, but properly packaged software shouldn't generate them).

---

### Post by Baresi on 2007-08-15
It did work. THank you, very much, jdong and Gremlinzzz for all your help.

---

### Post by jdong on 2007-08-15
Sure thing -- that's what we're here for. Now, be careful messing with unofficial packages from now on!

---

