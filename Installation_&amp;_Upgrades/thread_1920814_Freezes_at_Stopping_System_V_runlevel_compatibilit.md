---
title: "Freezes at Stopping System V runlevel compatibility [ok]"
date: 2012-02-05
forum: Installation &amp; Upgrades
---

### Post by Nick_C on 2012-02-05
I have installed Server (minimal install) with Virtualization role.  On top of this I have tried to install Ubuntu desktop:
[INDENT]
sudo apt-get update
sudo apt-get install --no-install-recommends ubuntu-desktop
[/INDENT]

Unfortunately after a reboot the machine freezes at:
[INDENT]Stopping System V runlevel compatibility [ok][/INDENT]

I can get to tty1 with ctrl-alt-F1 but where to go from here.

Thanks,

---

### Post by searchfgold6789 on 2012-02-05
Ding ding ding!!! Graphics. [http://ubuntuforums.org/showthread.php?t=1859820](http://ubuntuforums.org/showthread.php?t=1859820)

---

### Post by Nick_C on 2012-02-06
Thanks, that looks like a reasonable possibility.

Actually I have now over-written that server install with a command line installation from the alternate CD.  Unfortunately this also seems to suffer from a graphics related problem, just a bit different.

Command line only installation of 11.10 from the Alternate CD text mode install all went well but on reboot the screen is unreadable.  I can however ctrl-alt-F1 into tty1 and the screen becomes readable.

I have tried 
[INDENT]
sudo apt-get install nvidia-current
[/INDENT]
but this errors with: Unable to locate package nvidia-current

I then tried
[INDENT]
sudo apt-get install --reinstall nvidia-173
(but don't know how to tell if this is the version I have)
[/INDENT]
but same error: Unable to locate package nvidia-173

How can I find what graphics driver I have installed.

---

### Post by Nick_C on 2012-02-06
Ah just discovered that I had to insert the Alternate CD for this to work.
[INDENT]sudo apt-get install nvidia-current[/INDENT]
now worked and installed ok

Unfortunately this does not quite solve the problem.  Although a graphical mode starts it now freezes with a red flashing underscore cursor at the top left of the screen.

---

### Post by searchfgold6789 on 2012-02-06
Well, are you positive that you have a nVidia brand graphics card? you can find out your GPU with the command ```
lshw -c graphics
``` and then get the appropriate drivers...
Also, check out these two threads: [http://ubuntuforums.org/showthread.php?p=11556799](http://ubuntuforums.org/showthread.php?p=11556799) and [http://ubuntuforums.org/showthread.php?p=11638267](http://ubuntuforums.org/showthread.php?p=11638267)

---

### Post by Nick_C on 2012-02-06
> **searchfgold6789 said:**
> Well, are you positive that you have a nVidia brand graphics card? you can find out your GPU with the command ```
lshw -c graphics
``` and then get the appropriate drivers...
Also, check out these two threads: [http://ubuntuforums.org/showthread.php?p=11556799](http://ubuntuforums.org/showthread.php?p=11556799) and [http://ubuntuforums.org/showthread.php?p=11638267](http://ubuntuforums.org/showthread.php?p=11638267)
Definately sure it is an nVidia Quadro NVS 295.

Command lshw -c graphics does not return any result.

---

### Post by searchfgold6789 on 2012-02-06
Sorry, in that command I should have replaced "graphics" with "display", but no matter, as you are sure about the graphics card.
Your graphics driver version is actually 185, not 173, so try installing those instead with APT:```
sudo apt-get install nvidia-185
```Or if that doesn't work, get them from nVidia: (as long as you agree to the [license agreement]("http://www.nvidia.com/content/DriverDownload-March2009/licence.php?lang=us") they have):```
wget http://us.download.nvidia.com/XFree86/Linux-x86/185.18.36/NVIDIA-Linux-x86-185.18.36-pkg1.run
chmod a+x ./NVIDIA-Linux-x86-185.18.36-pkg1.run
sudo sh ./NVIDIA-Linux-x86-185.18.36-pkg1.run
```

---

### Post by Nick_C on 2012-02-07
Had a bit of a problem with
[INDENT]ERROR: this .run file is intended for the Linux-x86 platform, but you appear to be running on Linux-x86_64.  Aborting installation[/INDENT]

Spent a while trying to ad various repositories to get this driver but couldn't find it anywhere, is there a repository I could add to allow this to installed directly?

Eventually I tried guessing and found I could get it by just modifing the file to
[INDENT][http://us.download.nvidia.com/XFree86/Linux-x86_64/185.18.36/NVIDIA-Linux-x86_64-185.18.36-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/185.18.36/NVIDIA-Linux-x86_64-185.18.36-pkg1.run)[/INDENT]

Arggg..
Nearly worked but running it causes
[INDENT]ERROR Unable to find the system utility 'Id' please make sure you have the package 'binutils' installed[/INDENT]

Fixed that by
[INDENT]sudo apt-get install binutils[/INDENT]

Now get error
[INDENT]No precompiled kernel interface was found to match your kernel; would you like the installer to attempt to download a kernel interface for your kernel from the NVIDIA ftp site?[/INDENT]
to which I answer yes, but then get faced with
[INDENT]No precompiled kernel interface was found on the NVIDIA ftp site; this means that the installer will need to compile a kernel interface for your kernel[/INDENT]
Answer OK, but then errors with
[INDENT]ERROR: Unable to find the development tool 'cc' in your path; please make sure that you have the package 'gcc' installed[/INDENT]

So now install gcc
[INDENT]sudo apt-get install gcc[/INDENT]

And try again... now errors with
[INDENT]ERROR: Unable to find the development tool 'make' in your path; please make sure that you have the package 'make' installed[/INDENT]

So now install make
[INDENT]sudo apt-get install make[/INDENT]

And try again... this time get
[INDENT]ERROR Unable to determine the version of the kernel sources located in '/lib/modules/3.0.0-12-server/build'[/INDENT]

This is starting to get very complicated, where do I go from here?

---

### Post by searchfgold6789 on 2012-02-08
I would have tried the APT command first:```
sudo apt-get purge nvidia-173
sudo apt-get install nvidia-185
```

But anyway, in answer to your question, the answer is to install the `kernel-source` package:```
sudo apt-get install kernel-source
```

---

### Post by Nick_C on 2012-02-08
> **searchfgold6789 said:**
> I would have tried the APT command first:```
sudo apt-get purge nvidia-173
sudo apt-get install nvidia-185
```

But anyway, in answer to your question, the answer is to install the `kernel-source` package:```
sudo apt-get install kernel-source
```

Thanks for that.  Ok I will try again.

All getting a bit complicated keeping track of what I have done so far therefore starting again on a fresh install of [INDENT]Install Server - normal install, with Virtual Machine Host role selected.[/INDENT]

Desktop then installed by
[INDENT]sudo apt-get install --no-install-recomends ubuntu-desktop[/INDENT]

Now to moving on to your suggestion
[INDENT]sudo apt-get purge nvidia-173
returns: Package nvidia-173 is not installed, so not removed

sudo apt-get install nvidia-185
returns: Unable to locate package nvidia-185
[/INDENT]

Do I need to set some repository for this to be found?

---

### Post by Nick_C on 2012-02-08
I desided to install a minimal desktop with
[INDENT]sudo apt-get install --no-install-recommends ubuntu-desktop[/INDENT]

Still freezes but does let me run desktop from ctrl-alt-F1 -> startx.  However desktop is quite flaky and locks up frequently.

Not great so decided to remove desktop
[INDENT]sudo apt-get remove ubuntu-desktop[/INDENT]
However this doesn't seem to have worked properly, startx still starts up the desktop!  What have I done wrong, what do I need to do to actually remove the ubuntu-desktop and all of its files?

---

### Post by searchfgold6789 on 2012-02-09
You're crashing because you don't have graphics drivers.
If you have GUI capabilities after installing ubuntu-desktop, install 'jockey-gtk'. That will help you get your drivers set up via GUI, if you are still crashing.
Alternately, install the drivers from the website or with apt-get as I described before.


In answer to your question, tha following command should do the trick:```
sudo apt-get purge ubuntu-desktop && sudo apt-get --purge autoremove
```

---

### Post by Nick_C on 2012-02-09
Just installed jockey-gtk.  Also done an apt-get update & apt-get upgrade.

Choose the nVidia driver from the Restricted Drivers GUI.

Unfortunately still same problem, freezes at boot and need to issue startx manually to get the GUI running.

---

### Post by searchfgold6789 on 2012-02-09
This website will show you how to run a script at bootup:
[http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)
Create a file with the command 'startx' in it to use with those instructions.
Good luck,
 - Richie

---

### Post by Nick_C on 2012-02-10
Thanks Richie, decided perhaps best thing is to go with your suggestion of recompiling the kernel with the correct graphics drivers...

Well I was but had a problem with apt-get install kernel-sources
[INDENT]Package kernel-sources has no installation candidate
[/INDENT]
Then read about kernel-package so installed that but still kernel-sources has the same problem and nVidia driver won't install because of this missing kernel source.

Is there some app repository I need to add to make this source available?

Actually just cleaned up a bit and reinstalled jockey-gtx and now discover that the following driver is available which I have now installed:
[INDENT]NVIDIA binary Xorg driver, kernel module and VDPAU library[/INDENT]

Noticed an error message in the tty1 terminal after issuing startx:
[INDENT](EE) Failed to load module "nv" (module does not exist, 0)[/INDENT]
Ran sudo nvidia-xconfig
[INDENT]Validation Error: Data incomplete in file /etc/X11/xorg.conf, Device section "Default Device" must have a Driver line
[/INDENT]
that error now fixed but still not booting up automatically.

Trying manual nVidia driver install again but
[INDENT]ERROR Unable to determine the version of the kernel sources located in '/lib/modules/3.0.0-15-server/build'
[/INDENT]
and cannot install kernel source because:
[INDENT]
Package kernel-source is not available, but is referred to by another package.
Package 'kernel-source' has no installation candidate
[/INDENT]

---

### Post by searchfgold6789 on 2012-02-11
Here's what you'll need to do:

First, install the linux-source package (I guess I got the package name wrong):
```
sudo apt-get install linux-source
```
Then, try redoing the installation of the nVidia drivers.

[CENTER][B]OR
[/B][LEFT]Install the drivers using jockey-gtk.

[CENTER][B]THEN
[/B][LEFT]Create a new text file with the following contents called 'x.sh' in your home directory:```

#!/bin/sh
startx
```
Then, make the file executable, move the file to your /etc/init.d folder, and update the startup scripts:```
chmod a+x ~/x.sh
sudo mv ~/x.sh /etc/init.d
update-rc.d x.sh defaults
```
[/LEFT]
[/CENTER]
[/LEFT]
[/CENTER]

---

