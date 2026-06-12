---
title: "OpenOffice segmentation fault after upgrade to hoary"
date: 2005-04-11
forum: Installation &amp; Upgrades
---

### Post by almarag on 2005-04-11
Hi Folks:

I'm really very happy with Ubuntu, now it's my favorite distro, many thanks to developers!!!.

Now with my case. I have experienced some troubles with the upgrade from Warty to Hoary. Some of this problems I have been fixed already, but I still have troubles with OpenOffice.org.

My upgrade was fine: apt-get update, apt-get dist-upgrade and so on, but now every time I launch OpenOffice.org (oowriter for example) I have the "Segmentation fault" error with no traces. I tried to reinstall, (apt-get remove bla bla bla, apt-get install openoffice bla bla bla, of course before that I deleted the previuously downloades packages, and no results) but I'm out of luck. ¿Somebody has experimented the same sympthoms?... thanks in advance. In Warty, OpenOffice works with no problems.

I forgot: mi PC is a Pentium IV 2.2 GHZ, 512MB RAM, 20GB Hard disk for my Linux partition, upgraded from warty to hoary. My video card is a NVIDIA-GeForce 2 MX400 PCI, with compiled drivers from the nvidia website (the hoary packages doesn't work for me).

Alejandro Martínez.

---

### Post by almarag on 2005-04-12
Ok, now I have working this stuff. For reference, the problem was the nvidia driver. After uninstalling/reinstalling nvidia driver from the website of nvidia, OO start working normally. Weird stuff, you know...

Greets.

Alex.

---

### Post by Pyxidis on 2005-04-20
I have a similar problem with OpenOffice on Hoary on one of my machines.   I tried upgrading from Warty first, which worked apart from really bad graphics card detection which wasn't a problem in Warty.  I had to dpkg-reconfigure the xorg package and turn the horizontal refresh rates down to make the system usable, but I couldn't get OpenOffice to run at all.  Running it from the command line revealed the segmentation fault error.

I tried doing a fresh install instead, which worked a little better (same carry on with the graphics card).  Sometimes I get the segmentation fault, but if I log out and back in again it goes away (for a while at least)

I don't have an Nvidia card on this box (Intel 82865G integrated graphics) so it's not nvidia drivers for me, though it could be Xorg.  Other system spec details: Celeron 2.2 with 256MB RAM, intel chipset.

The frustrating thing is that Warty installs perfectly on every box I have tried it on.



Curiously, I have another box with an Nvidia Geforce FX5200, which works very well with Hoary, but it's an AMD Sempron 2.4 with 512MB RAM

---

### Post by ElvisThePelvis on 2005-04-22
I had a very similar issue that I resolved by modifying my /etc/X11/xorg.conf file a bit.

Keep in mind that I did not use the Nvidia modules from the repos, but I instead installed from the nvidia site. I simply commented out the BusID line and all of my problems with segfaults in OpenOffice, XMMS, glxgears were resolved.

sudo vi /etc/X11/xorg.conf

```
Section "Device"
        Identifier      "NVIDIA Corporation NV40 [GeForce 6800]"
        Driver          "nvidia"
#       BusID           "PCI:1:0:0"
EndSection
```

---

### Post by yippy on 2005-05-17
[QUOTE=almarag]Ok, now I have working this stuff. For reference, the problem was the nvidia driver. After uninstalling/reinstalling nvidia driver from the website of nvidia, OO start working normally. Weird stuff, you know...

Greets.

Alex.[/QUOTE]
 I had the same problem, also fixed by removing the Ubuntu Nvidia driver and installing the one from Nvidia's website.  What kind of sense does that make?  Well it worked, and it was a simple five-minute transition.

For reference, I have version 1.0.7174 of the Nvidia driver.

---

### Post by yippy on 2005-05-24
Unfortunately it's not perfect.  Every time I reboot my machine it can't launch X, recompiling the NVIDIA driver fixes the problem on the next reboot.

What a pain.

---

### Post by yippy on 2005-10-28
I've been tolerating this since May because I didn't reboot very often and haven't had time to really look at it.  So this week I finally decided to dig in and figure out what's going on.

If you install the ubuntu nVidia packages, it installs a script in /etc/init.d that deletes your TLS symlinks.  In some cases it will try to recreate them, but fails anyway if you don't have the Ubuntu package.  If you remove that script, you won't have to recompile the nVidia driver after every reboot, and OpenOffice doesn't segfault, so everyone is happy!

Yay! :mrgreen:

---

### Post by Gezzer on 2005-10-29
have u installed nvidia-glx via synaptic
once installed open a terminal & write
sudo nvidia-glx-config enable

then C+A+Backspace to restart X

---

