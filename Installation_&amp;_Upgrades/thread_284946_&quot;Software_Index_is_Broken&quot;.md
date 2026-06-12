---
title: "&quot;Software Index is Broken&quot;"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by Snow Dogg on 2006-10-26
Hey, I have tried to upgrade to Edgy from Dapper but i am getting errors. Basically it says the Software Index is Broken and i need to do: "sudo apt-get install -f" in terminal. When i do this i get an error:

> /var/cache/apt/archives/x11-common_1%3a7.1.1ubuntu6_i386.deb (--unpack):
trying to overwrite `/usr/X11R6/bin', which is also in package opera
Errors were encountered while processing:
/var/cache/apt/archives/x11-common_1%3a7.1.1ubuntu6_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I cant fix it, im going mad, please help!

---

### Post by trvmyr on 2006-10-26
I'm getting sort of the same error:

> Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  x11-common
The following packages will be upgraded:
  x11-common
1 upgraded, 0 newly installed, 0 to remove and 884 not upgraded.
46 not fully installed or removed.
Need to get 0B/291kB of archives.
After unpacking 418kB of additional disk space will be used.
Do you want to continue [Y/n]? y
debconf: unable to initialize frontend: Kde
debconf: (Unable to load Qt -- is libqt-perl installed?)
debconf: falling back to frontend: Dialog
Preconfiguring packages ...
(Reading database ... 114826 files and directories currently installed.)
Preparing to replace x11-common 7.0.0-0ubuntu45 (using .../x11-common_1%3a7.1.1ubuntu6_i386.deb) ...
debconf: unable to initialize frontend: Kde
debconf: (Unable to load Qt -- is libqt-perl installed?)
debconf: falling back to frontend: Dialog
Unpacking replacement x11-common ...
dpkg: error processing /var/cache/apt/archives/x11-common_1%3a7.1.1ubuntu6_i386.deb (--unpack):
 trying to overwrite `/usr/X11R6/bin', which is also in package xfcom-i810
debconf: unable to initialize frontend: Kde
debconf: (Unable to load Qt -- is libqt-perl installed?)
debconf: falling back to frontend: Dialog
Errors were encountered while processing:
 /var/cache/apt/archives/x11-common_1%3a7.1.1ubuntu6_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


When I use Synaptic to Fix the broken dep. I get this error
> E: /var/cache/apt/archives/x11-common_1%3a7.1.1ubuntu6_i386.deb: trying to overwrite `/usr/X11R6/bin', which is also in package xfcom-i810


Happend when trying to upgrade from Dapper to Edgy using the gksudo command.  Why it's looking for KDE frontend I have no idea unless it looks for both Gnome (what I'm using) and KDE...???  Tried to use sudo apt-get install -f  and using Synaptic to install the Broken Packages and both fail.  Help!!! ](*,)

---

### Post by itsterry on 2006-10-26
I'm getting this error, too.

Have tried chmod 777 /usr/X11R6/bin in case it was a permission thing, but that's not helping

---

### Post by P_Badger on 2006-10-26
I'm having the same issue, and it's happened before for me on another computer. I had to do a clean install on that one, I'd like not to do the same with this machine. : P

---

### Post by OniAnubis on 2006-10-27
I'm getting the same error about the X11R6/bin folder...](*,)

---

### Post by itsterry on 2006-10-27
Anyone figure out a way round this yet?

I'm leaving my main dev machine switched on in case I can't get back from this without a re-install. Can't afford the hours to reconfigure all my programs again !

---

### Post by orsula on 2006-10-27
Just another guy with the same thing. I also tried to upgrade to Edgy with the ```
gksu "update-manager -c"
``` and things went smooth. I downloaded about 800MB and got an error message about /usr/X11R6/bin being 'not-empty'. I removed the contents and ran the ```
sudo apt-get install -f
``` with no success. Also got the following:

```
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libcairo2 libcairo2-dev libglib2.0-0 libglib2.0-data libglib2.0-dev
  libpango1.0-0 libpango1.0-0-dbg libpango1.0-common libpango1.0-dev
  libxft-dev libxft2 x11-common xkb-data xserver-xorg-core xutils-dev
Suggested packages:
  libcairo2-doc libglib2.0-doc ttf-thryomanes libpango1.0-doc
The following NEW packages will be installed:
  libxft-dev xkb-data xutils-dev
The following packages will be upgraded:
  libcairo2 libcairo2-dev libglib2.0-0 libglib2.0-data libglib2.0-dev
  libpango1.0-0 libpango1.0-0-dbg libpango1.0-common libpango1.0-dev libxft2
  x11-common xserver-xorg-core
12 upgraded, 3 newly installed, 0 to remove and 1022 not upgraded.
44 not fully installed or removed.
Need to get 0B/7708kB of archives.
After unpacking 6009kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 102952 files and directories currently installed.)
Preparing to replace x11-common 7.0.0-0ubuntu45 (using .../x11-common_1%3a7.1.1ubuntu6_i386.deb) ...
Unpacking replacement x11-common ...
Replacing files in old package xinit ...
dpkg: error processing /var/cache/apt/archives/x11-common_1%3a7.1.1ubuntu6_i386.deb (--unpack):
 trying to overwrite `/usr/X11R6/bin', which is also in package fvwm-shell
Errors were encountered while processing:
 /var/cache/apt/archives/x11-common_1%3a7.1.1ubuntu6_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I have no idea what to do with this....but it seems like a a recurring theme.
Gideon

---

### Post by itsterry on 2006-10-28
Looks like the solution to this one is at
[http://www.ubuntuforums.org/showthread.php?t=286351](http://www.ubuntuforums.org/showthread.php?t=286351)

Many thanks to that poster !!

---

### Post by chstamat on 2006-10-30
Hi 
i have the following problem :
When i try to install or remove something i get ,for example, the following error 

(update-desktop-database:8230): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing bittornado-gui (--remove):
 subprocess post-removal script returned error exit status 139

i have tried apt-get install -f, apt-get remove --purge package, aptitude remove --purge and everything it crossed my mind except from pray :). Also when i tried to run the update manager i got "software index is broken ,type apt-get install -f to fix......." 
Any ideas ??

Thanks in advance.
Haris

---

### Post by pingveno on 2006-11-02
I'm getting the same error. From tinkering around with the system, I found out that the install for the x11-common package fails.
```

# apt-get install x11-common
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  x11-common
1 upgraded, 0 newly installed, 0 to remove and 1208 not upgraded.
56 not fully installed or removed.
....more output...
Errors were encountered while processing:
 /var/cache/apt/archives/x11-common_1%3a7.1.1ubuntu6_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

The error message *exactly* duplicates the one that I got in the intial dist-upgrade. So apparently something about the x11-common package is causing an error.

---

