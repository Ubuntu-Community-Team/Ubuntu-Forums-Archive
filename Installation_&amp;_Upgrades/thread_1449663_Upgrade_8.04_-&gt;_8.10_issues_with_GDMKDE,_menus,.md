---
title: "Upgrade 8.04 -&gt; 8.10 issues with GDM/KDE, menus, &amp; dropping to login screen."
date: 2010-04-08
forum: Installation &amp; Upgrades
---

### Post by Paulzy on 2010-04-08
I have a dual boot PC. , XP on hd0,0 and Ubuntu on hd3,4
winXP Home SP3 32bit
AMD Athlon XP 2800+, 2GB RAM
nVIDIA 7600GS 512MB

I recently upgraded from 8.04 LTS to 8.10 on my way to 9.10. Well, I want to change the theme I am using and also the keyboard shortcuts for my Logitech G11. However, whenever I select an program from the System/Preferences menu, the system drops and goes back to the login screen. So far I have only tried the Keyboard Shortcuts, Appearance, and CompizConfig items. When I submit this I'll try all the other items.

But it seems that these three items broke the upgrade.

```

E: gnome-accessibility-themes: subprocess post-installation script returned error exit status 1
E: gnome-themes: subprocess post-installation script returned error exit status 1
E: ubuntu-desktop: dependency problems - leaving unconfigured

```

 I did install kde-desktop a couple days ago, thinking I would actually get KDE4 on my system. :(, so I uninstalled the kde splash image and the kde-desktop packages, but it only remove itself and not all the 430MB of apps it came with. Hmm?

So anytime I attempt an update I will always get this popping up:
```

E: gnome-accessibility-themes: subprocess post-installation script returned error exit status 1
E: gnome-themes: subprocess post-installation script returned error exit status 1
E: ubuntu-desktop: dependency problems - leaving unconfigured

```

Whilst the update screen verbosed something about Appaort following up on a previous error. 

[URL="http://gallery.pjcii.net/albums/userpics/10001/updateError-scr1.png"][IMG]http://gallery.pjcii.net/albums/userpics/10001/normal_updateError-scr1.png[/IMG]
[/URL] Screen 1
[[IMG]http://gallery.pjcii.net/albums/userpics/10001/normal_upDateerror-scr2.png[/IMG]]("http://gallery.pjcii.net/albums/userpics/10001/upDateerror-scr2.png")
Screen 2
[[IMG]http://gallery.pjcii.net/albums/userpics/10001/normal_updateerror_scr3.png[/IMG]]("http://gallery.pjcii.net/albums/userpics/10001/updateerror_scr3.png") Screen 3 (Scr2 cont.)

Should I just continue the onto 9.04 and see if it corrects itself?  What should I do?

---

### Post by Paulzy on 2010-04-10
Most of the other options in the menus work, except the ones that modify the system, like Appearnce, Keyboard, and Sound.

I need an answer to this, please. Why are the updates failing? 

How do I repair the **gnome-accessibility-themes, gnome-themes,** and **ubuntu-desktop** packages? 

Do I uninstall them, reboot, and reinstall?

Do I just go ahead and continue to upgrade to 9.04, then onto 9.10 and hope the errors will resolve themselves?

I'm bumping this because I would like some help, please?

Thank you.

Paul

---

### Post by Paulzy on 2010-04-10
I'll buy you a beer if you help me.:popcorn:
If my Ubuntu's broken - what'll I do then? Hmm?

:confused::(

---

### Post by Paulzy on 2010-04-11
:( SIGH....
ok then...

---

### Post by Paulzy on 2010-04-15
bump

Can **anyone** see a way to resolve this?

---

### Post by kellemes on 2010-04-15
Well..
Try this from a terminal..
```
sudo dpkg --configure -a
```
What's the output?

Remove the packages having issues..
```
sudo apt-get --purge remove gnome-accessibility-themes
sudo apt-get --purge remove gnome-themes
```

Reinstall ubuntu-desktop..
```
sudo apt-get install ubuntu-desktop
```

Just guessing here.. so try at your own risk ;-)

Just wondering.. why not a fresh install of 9.10?

---

### Post by Paulzy on 2010-04-17
> **kellemes said:**
> Well..
Try this from a terminal..
```
sudo dpkg --configure -a
```
What's the output?

Remove the packages having issues..
```
sudo apt-get --purge remove gnome-accessibility-themes
sudo apt-get --purge remove gnome-themes
```

Reinstall ubuntu-desktop..
```
sudo apt-get install ubuntu-desktop
```

Just guessing here.. so try at your own risk ;-)

Just wondering.. why not a fresh install of 9.10?

Thought about that, but from what i read in the Docs it said that should upgrade by following the path: 8.04 LTS -> 8.10 -> 9.04 -> 9.10. So I was just following the upgrade docs instructions verbatim.

Also, the dpkg --configure -a verbosed nothing, as I already did a complete removal of the aforementioned "gnome*themes" from Synaptic as well as ubuntu-desktop, since I believed it was part of the problem (as much as my earlier installation of kubuntu-desktop may have also greatly contributed to this mess). So I attempt a re-install right now using apt-get instead of Synaptic.

---

### Post by Paulzy on 2010-04-17
Got a new message after attempting to re-install ubuntu-desktop:

> 
[PJCI] pauljc: sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  sharutils libcvsservice0 libavutil1d libdc1394-13 libpythonize0
  libgda3-common python-gnome2-extras icedtea6-plugin python-twisted-web
  eclipse-sdk libsilc-1.1-2 libkbluetooth0 libjack0.100.0-0 libmimelib1c2a
  libpostproc1d kdeedu-data libexiv2-2 libkcddb1 libclamav5 libnss3-dev
  libavformat1d pykdeextensions libxosd2 cryptsetup libkleopatra1 libx264-57
  libvlc0 adept-common libkonq4 cvs libfltk1.1 libksieve0 libkpimidentities1
  libswscale1d libnspr4-dev debtags networkstatus liblinebreak
  libkpimexchange1 libavcodec1d libgda3-3 libkdeedu3 update-manager-kde
  vlc-plugin-pulse xaw3dg xnest python-xlib libxerces27 libgdl-1-0 python-kde3
  libgdl-1-common
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gnome-accessibility-themes gnome-themes
Suggested packages:
  gnome-themes-extras
Recommended packages:
  pidgin pidgin-otr
The following NEW packages will be installed:
  gnome-accessibility-themes gnome-themes ubuntu-desktop
0 upgraded, 3 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/652kB of archives.
After this operation, 4702kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package gnome-accessibility-themes.
(Reading database ... 370044 files and directories currently installed.)
Unpacking gnome-accessibility-themes (from .../gnome-accessibility-themes_2.24.1-0ubuntu1_all.deb) ...
Selecting previously deselected package gnome-themes.
Unpacking gnome-themes (from .../gnome-themes_2.24.1-0ubuntu1_all.deb) ...
Selecting previously deselected package ubuntu-desktop.
Unpacking ubuntu-desktop (from .../ubuntu-desktop_1.124_i386.deb) ...
Setting up gnome-accessibility-themes (2.24.1-0ubuntu1) ...
gtk-update-icon-cache: symbol lookup error: /usr/local/lib/libpng12.so.0: undefined symbol: inflateInit_
dpkg: error processing gnome-accessibility-themes (--configure):
 subprocess post-installation script returned error exit status 127
Setting up gnome-themes (2.24.1-0ubuntu1) ...
gtk-update-icon-cache: symbol lookup error: /usr/local/lib/libpng12.so.0: undefined symbol: inflateInit_
dpkg: error processing gnome-themes (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on gnome-themes; however:
  Package gnome-themes is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 gnome-accessibility-themes
 gnome-themes
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by Paulzy on 2010-08-18
This issue has been resolved via upgrading to 9.04 over the network.
However, the gnome-accessibilty-themes package still returns these errors whenever the Synaptic Package Manager is used or run:

(Reading database ... 398558 files and directories currently installed.)
Removing amarok ...
Purging configuration files for amarok ...
Removing amarok-common ...
Purging configuration files for amarok-common ...
Removing amarok-engine-xine ...
Removing emerald ...
Purging configuration files for emerald ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for man-db ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Setting up gnome-accessibility-themes (2.26.0-0ubuntu1) ...
gtk-update-icon-cache: Failed to open file /usr/share/icons/HighContrastLargePrintInverse/.icon-theme.cache : File exists
dpkg: error processing gnome-accessibility-themes (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 gnome-accessibility-themes
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up gnome-accessibility-themes (2.26.0-0ubuntu1) ...
gtk-update-icon-cache: Failed to open file /usr/share/icons/HighContrastLargePrintInverse/.icon-theme.cache : File exists
dpkg: error processing gnome-accessibility-themes (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 gnome-accessibility-themes

E: gnome-accessibility-themes: subprocess post-installation script returned error exit status 1


Or when doing a network upgrade:

Could not install 'gnome-accessibility-themes'

The upgrade will continue but the 'gnome-accessibility-themes' package may be in a not working state. Please consider submitting a bug report about it.

subprocess post-installation script returned error exit status 127

---

