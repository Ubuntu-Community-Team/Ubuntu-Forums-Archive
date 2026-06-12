---
title: "Network Manager Install Help"
date: 2006-08-29
forum: Installation &amp; Upgrades
---

### Post by cac007 on 2006-08-29
I've tried installing nm through apt-get but it doesn't ever seem to work right so i'm installing through tar.gz.  I've extracted it and now i'm trying to ./configure.  Then i come across this message:

checking for intltool >= 0.27.2... 0.34.1 found
checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool

What do i need to fix this?

I have perl, perl-base, and perl-modules installed??/

---

### Post by ciscosurfer on 2006-08-29
You should try to stick with the packages in the repos and only use the source as a last resort.  What problems are you having exactly with the package version downloaded through apt?  A quick, handy fix that has always worked for me is to issue the following in a terminal after you install nm-applet```
gtk-update-icon-cache -f /usr/share/icons/hicolor/
```
Hope that helps.  Let me know.

---

### Post by cac007 on 2006-08-29
in the terminal i do nm-applet and nothing happens it just sits there

---

### Post by ciscosurfer on 2006-08-29
If you're running Gnome, then (re)install network-manager; if you're running KDE, then (re)install knetworkmanager.  Then throw nm-applet into your startup sessions tab.  

1) If you don't currently have the packages installed, then run these commands for Gnome and/or KDE, respectively```
sudo aptitude install network-manager
```OR```
sudo aptitude install knetworkmanager
``` 2) If you do have them installed already (the packages, not the source), then issue these in a terminal for Gnome or KDE, respectively```
sudo aptitude reinstall network-manager
```OR```
sudo aptitude reinstall knetworkmanager
``` Remember to add this line to your startup sessions tab (System > Preferences > Sessions | Startup Programs | Add)```
nm-applet --sm-disable
```Then issue the following to update the icon cache```
gtk-update-icon-cache -f /usr/share/icons/hicolor/
```Logout, then log back in to see your network manager applet in the upper-right corner (if you're using Gnome); lower-right if you're using KDE. :D

---

