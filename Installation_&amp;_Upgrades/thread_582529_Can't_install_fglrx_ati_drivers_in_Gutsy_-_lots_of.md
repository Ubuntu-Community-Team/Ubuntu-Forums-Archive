---
title: "Can't install fglrx ati drivers in Gutsy - lots of info"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by marcushe on 2007-10-19
Hey Guys,

Can't get my ATI drivers installed from the restricted drivers manager or command line on my Compaq Presario V2000 with an ATI Mobility 200M.

It was upgraded from a Fiesty install, which didnt have a working Compiz - it got the "No Composite device" error when trying to turn on desktop effects.  So I was hoping Gutsy would fix this.

I tried installing Compiz Fusion on Fiesty a while ago, but it didn't work.  So this is the upgraded install of that.  This is the output of trying to install the fglrx drivers in Gutsy:

chris@chrisman:~$ sudo apt-get install -f xorg-driver-fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  xorg-driver-fglrx
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/8558kB of archives.
After unpacking 23.0MB of additional disk space will be used.
(Reading database ... 127316 files and directories currently installed.)
Unpacking xorg-driver-fglrx (from .../xorg-driver-fglrx_7.1.0-8.37.6+2.6.22.4-14.9_i386.deb) ...
dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/fglrx/libGL.so.1.xlibmesa by xorg-driver-fglrx' clashes with `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-new'
dpkg: error processing /var/cache/apt/archives/xorg-driver-fglrx_7.1.0-8.37.6+2.6.22.4-14.9_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/xorg-driver-fglrx_7.1.0-8.37.6+2.6.22.4-14.9_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

What to do?

Thanks!

---

### Post by marcushe on 2007-10-20
Resolved this myself:

The install error noted something about the contents /usr/lib/nvidia folder, when I don't even have a nvidia graphics card.

So i moved the contents of '/usr/lib/nvidia/' to 'usr/lib/fglrx/' using sudo mv.  I tried the fglrx install again and got the same error.

Since the install error said something about fglrx clashing with nvidia, I knew something concerning nvidia was on my machine that shouldn't be, so I tried installing the nvidia drivers (nvidia-glx-new) hoping that it would set my machine to "nvidia mode".  They installed successfully.

After that, I tried installing the fglrx drivers again - it worked!  The fglrx drivers were scripted to remove nvidia drivers from the system if there were any.  I now have a working compiz fusion!

(I don't know if moving the contents of '/usr/lib/nvidia/' to 'usr/lib/fglrx/' had anything to do with this)

Resolved.

---

