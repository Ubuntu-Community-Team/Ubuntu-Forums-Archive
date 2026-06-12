---
title: "Can't Install Nemo;  Depends: libxapp1 (has no installation candidate)"
date: 2017-11-23
forum: Installation &amp; Upgrades
---

### Post by ThePowerpuffGirls on 2017-11-23
I did an update and it said nemo will be held back if I remember correctly, now it is removed from my computer.

I did sudo apt install nemo and got this:
sudo apt install nemo
[sudo] password for office2: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 nemo : Depends: libxapp1 but it is not installable
        Recommends: nemo-fileroller but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


So I try to install libxapp1 and got this:
sudo apt install libxapp1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libxapp1 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libxapp1' has no installation candidate

I also tried:
sudo aptitude install nemo
[sudo] password for office2: 
The following NEW packages will be installed:
  cinnamon-l10n{a} libnemo-extension1{a} nemo{b} nemo-data{a} 
  nemo-fileroller{a} 
0 packages upgraded, 5 newly installed, 0 to remove and 0 not to upgrade.
Need to get 3,787 kB of archives. After unpacking 24.9 MB will be used.
The following packages have unmet dependencies:
 nemo : Depends: libxapp1 which is a virtual package and is not provided by any available package.

The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     nemo [Not Installed]                               
2)     nemo-fileroller [Not Installed]                    



Accept this solution? [Y/n/q/?] 1
Action "1": Removing nemo

Package: nemo
State: not installed; will be installed automatically
Version: 3.6.4-1~webupd8~xenial02
Priority: optional
Section: gnome
Maintainer: Jacob Zimmermann <ppa@jzimm.net>
Architecture: amd64
Uncompressed Size: 4,598 k
Depends: libatk1.0-0 (>= 1.32.0), libc6 (>= 2.14), libcairo-gobject2 (>=
         1.10.0), libcairo2 (>= 1.10.0), libdbusmenu-glib4 (>= 0.4.2),
         libexempi3 (>= 2.2.0), libexif12 (>= 0.6.21-1~), libgail-3-0 (>=
         3.0.0), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.41.1),
         libgnome-desktop-3-12 (>= 3.18.1), libgtk-3-0 (>= 3.9.12),
         libnemo-extension1, libnotify4 (>= 0.7.0), libpango-1.0-0 (>= 1.20.0),
         libpangocairo-1.0-0 (>= 1.14.0), libunity9 (>= 3.8.4), libx11-6,
         libxapp1, libxml2 (>= 2.7.4), libzeitgeist-1.0-1 (>= 0.3.14),
         dconf-gsettings-backend | gsettings-backend, nemo-data (=
         3.6.4-1~webupd8~xenial02), shared-mime-info (>= 0.50),
         desktop-file-utils (>= 0.7), gvfs (>= 1.3.2), libglib2.0-data,
         gsettings-desktop-schemas, cinnamon-l10n
Recommends: eject, librsvg2-common, gvfs-backends, nemo-fileroller
Suggests: eog, evince | pdf-viewer, totem | mp3-decoder, xdg-user-dirs
Conflicts: nemo-data (< 2.2.4-2~), nemo-data:i386 (< 2.2.4-2~), nemo:i386
Breaks: gnome-bluetooth (< 3.0), gnome-bluetooth:i386 (< 3.0), gnome-session (<
        2.28), gnome-session:i386 (< 2.28), gnome-volume-manager (< 2.24),
        rhythmbox (< 0.12), rhythmbox:i386 (< 0.12)
Description: File manager and graphical shell for Unity
 Nemo is the official file manager for the Cinnamon desktop. This Nemo package
 includes Unity-specific patches (should also work with GNOME, Xfce). It allows
 to browse directories, preview files and launch applications associated with
 them. It is also responsible for handling the icons on the Cinnamon desktop. It
 works on local and remote filesystems. 
 
 Several icon themes and components for viewing different kinds of files are
 available in separate packages.


This action was selected because nemo depends upon libxapp1.

Enter "r 1" to prevent this action from appearing in new solutions.
Enter "a 1" to require that new solutions include this action if possible.

Accept this solution? [Y/n/q/?] a 1
Requiring the removal of nemo
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1) A   nemo [Not Installed]                               
2)     nemo-fileroller [Not Installed]                    



Accept this solution? [Y/n/q/?] Y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not to upgrade.
Need to get 0 B of archives. After unpacking 0 B will be used.
                                    

I also tried to do the second one and both, but I can only do one at a time.

---

### Post by vasa1 on 2017-11-23
Related to [https://ubuntuforums.org/showthread.php?t=2378280](https://ubuntuforums.org/showthread.php?t=2378280)

---

### Post by ThePowerpuffGirls on 2017-11-23
I tried that solution already but for some reason, it doesn't work for me.

---

### Post by seanos on 2017-11-24
You shouldn&#8217;t have chosen to remove it. An update being held back is not such a big deal.

I&#8217;m in the same situation. I have version 3.4.7 (3.4.7-1~webupd8~xenial04) installed from the WebUpd8 PPA and Software Updater offered me 3.6.4 (3.6.4-1~webupd8~xenial02) but didn&#8217;t install it. The new version seems to add a dependency to a new suite of helper apps through *libxapps1* but that isn&#8217;t in the WebUpd8 PPA or in standard repos for 16.04.

The file does exist in PPAs that include the Cinnamon dependencies required by *vanilla* Nemo, but the point of the WebUpd8 PPA is to *avoid* any Cinnamon dependencies so I&#8217;d wouldn&#8217;t rush into adding Cinnamon or X-Apps PPAs if you&#8217;re running Ubuntu Unity.

Probably best to give Andrew at WebUpd8 some time to sort this out. In the meantime you could probably reinstall 3.4.7 using Synaptic, or maybe aptitude, but I&#8217;m not sure I&#8217;ve ever used aptitude, so someone would need to help you there.

---

