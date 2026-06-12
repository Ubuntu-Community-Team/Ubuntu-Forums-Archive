---
title: "Unable to install or reinstall certain programmes"
date: 2012-11-25
forum: Installation &amp; Upgrades
---

### Post by s0563764 on 2012-11-25
Hi,

I changed my mum's ubuntu to xubuntu awhile ago, and upgrading it to 12.10 was fine, but recently her laptop has no longer access to gnomes network tools (or really anything to control wireless etc), and jdownloader has disappeared too. In the case of network tools I can't uninstall it then install it. An error turns up. And for jdownloader, even though the PPA is in the system etc, I can't find it on software centre.

Just looking for a place to start to solve this/similar problems, or should I just do a clean install?

---

### Post by dino99 on 2012-11-25
xub is not my fav, so i dont know about the exact xub command (but as you know gnome, you'll be able to translate i suppose)

start cleaning the room:

sudo apt-get clean
sudo apt-get autoclean
sudo at-get autoremove

sudo apt-get install  gtkorphan
sudo apt-get install  bleachbit

then go to the menu, and select : 
- Apps -> System Tools -> Admin -> Remove Orphans
- Apps -> System Tools -> Bleachbit (as root) : and check the options carefully before proceeding (dont check to erase passwords for example)

And you can check /etc/apt/sources.list  & /etc/apt/sources.list.d to be sure of the activated repos (not mixing old release with actual for example) and maybe unckeck/remove some ppas. (dont forget to update again after tweaks done)

---

### Post by ibjsb4 on 2012-11-25
If dino's suggestion doesn't work, open a terminal and enter:

sudo apt-get upgrade

And please post the output.

---

### Post by s0563764 on 2012-11-27
Hey guys,

sudo apt-get install gtkorphan and sudo apt-get upgrade results in this (sorry, seems a lot, the same names of apps pop up at the bottom. Happens when I try to install stuff):

Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe deborphan i386 1.7.28.5 [102 kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe dialog i386 1.1-20111020-1 [276 kB]
Get:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe libgtk2-gladexml-perl i386 1.007-1build2 [41.4 kB]
Get:4 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe gtkorphan all 0.4.4-1 [30.7 kB]
Fetched 450 kB in 2s (152 kB/s)     
Selecting previously unselected package deborphan.
(Reading database ... 379888 files and directories currently installed.)
Unpacking deborphan (from .../deborphan_1.7.28.5_i386.deb) ...
Selecting previously unselected package dialog.
Unpacking dialog (from .../dialog_1.1-20111020-1_i386.deb) ...
Selecting previously unselected package libgtk2-gladexml-perl.
Unpacking libgtk2-gladexml-perl (from .../libgtk2-gladexml-perl_1.007-1build2_i386.deb) ...
Selecting previously unselected package gtkorphan.
Unpacking gtkorphan (from .../gtkorphan_0.4.4-1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for menu ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Setting up gconf2 (3.2.5-0ubuntu2) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 97, in <module>
    for f in os.listdir(defaults_dest):
OSError: [Errno 2] No such file or directory: '/var/lib/gconf/defaults'
dpkg: error processing gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gnome-media:
 gnome-media depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-media (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-common:
 libgnomevfs2-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing libgnomevfs2-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-0:
 libgnomevfs2-0 depends on libgnomevfs2-common (>= 1:2.24); however:
  Package libgnomevfs2-common is not configured yet.
 libgnomevfs2-0 depends on libgnomevfs2-common (<< 1:2.25); however:
  Package libgnomevfs2-common is not configured yet.
dpkg: error processing libgnomevfs2-0 (--confNo apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                         No apport report written because the error message indicates it's a follow-up error from a previous failure.
                     No apport report written because MaxReports has already been reached
         No apport report written because MaxReports has already been reached
                                                                             No apport report written because MaxReports has already been reached
                                                                 No apport report written because MaxReports has already been reached
                                                     No apport report written because MaxReports has already been reached
                                         No apport report written because MaxReports has already been reached
                             No apport report written because MaxReports has already been reached
                 No apport report written because MaxReports has already been reached
     No apport report written because MaxReports has already been reached
                                                                         igure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2-common:
 libgnome2-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing libgnome2-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2-0:
 libgnome2-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 libgnome2-0 depends on libgnome2-common (>= 2.32); however:
  Package libgnome2-common is not configured yet.
 libgnome2-0 depends on libgnome2-common (<< 2.33); however:
  Package libgnome2-common is not configured yet.
dpkg: error processing libgnome2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of aisleriot:
 aisleriot depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing aisleriot (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-extra:
 libgnomevfs2-extra depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 libgnomevfs2-extra depends on libgnomevfs2-common (>= 1:2.24); however:
  Package libgnomevfs2-common is not configured yet.
 libgnomevfs2-extra depends on libgnomevfs2-common (<< 1:2.25); however:
  Package libgnomevfs2-common is not configured yet.
dpkg: error processing libgnomevfs2-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of light-themes:
 light-themes depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing light-themes (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unity-common:
 unity-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing unity-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unity:
 unity depends on unity-common (= 5.16.0-0ubuntu1); however:
  Package unity-common is not configured yet.
dpkg: error processing unity (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on gnome-media; however:
  Package gnome-media is not configured yet.
 ubuntu-desktop depends on unity; however:
  Package unity is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Setting up deborphan (1.7.28.5) ...
Setting up dialog (1.1-20111020-1) ...
Setting up libgtk2-gladexml-perl (1.007-1build2) ...
dpkg: dependency problems prevent configuration of libgnome2-bin:
 libgnome2-bin depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
dpkg: error processing libgnome2-bin (--configure):
 dependency problems - leaving unconfigured
Processing triggers for menu ...
No apport report written because MaxReports has already been reached
                                                                    Setting up gtkorphan (0.4.4-1) ...
Errors were encountered while processing:
 gconf2
 gnome-media
 libgnomevfs2-common
 libgnomevfs2-0
 libgnome2-common
 libgnome2-0
 aisleriot
 libgnomevfs2-extra
 light-themes
 unity-common
 unity
 ubuntu-desktop
 libgnome2-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)

Its the same stuff popping up, is there a way to resolve this?

---

### Post by ibjsb4 on 2012-11-27
First, Using code tags makes your long post easier to read.  Maybe edit yours.

[http://ubuntuforums.org/showthread.php?t=890901](http://ubuntuforums.org/showthread.php?t=890901)

```
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe deborphan i386 1.7.28.5 [102 kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe dialog i386 1.1-20111020-1 [276 kB]
Get:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe libgtk2-gladexml-perl i386 1.007-1build2 [41.4 kB]
Get:4 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe gtkorphan all 0.4.4-1 [30.7 kB]
Fetched 450 kB in 2s (152 kB/s)     
Selecting previously unselected package deborphan.
(Reading database ... 379888 files and directories currently installed.)
Unpacking deborphan (from .../deborphan_1.7.28.5_i386.deb) ...
Selecting previously unselected package dialog.
Unpacking dialog (from .../dialog_1.1-20111020-1_i386.deb) ...
Selecting previously unselected package libgtk2-gladexml-perl.
Unpacking libgtk2-gladexml-perl (from .../libgtk2-gladexml-perl_1.007-1build2_i386.deb) ...
Selecting previously unselected package gtkorphan.
Unpacking gtkorphan (from .../gtkorphan_0.4.4-1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for menu ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Setting up gconf2 (3.2.5-0ubuntu2) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 97, in <module>
    for f in os.listdir(defaults_dest):
OSError: [Errno 2] No such file or directory: '/var/lib/gconf/defaults'
dpkg: error processing gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gnome-media:
 gnome-media depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-media (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-common:
 libgnomevfs2-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing libgnomevfs2-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-0:
 libgnomevfs2-0 depends on libgnomevfs2-common (>= 1:2.24); however:
  Package libgnomevfs2-common is not configured yet.
 libgnomevfs2-0 depends on libgnomevfs2-common (<< 1:2.25); however:
  Package libgnomevfs2-common is not configured yet.
dpkg: error processing libgnomevfs2-0 (--confNo apport report written  because the error message indicates it's a follow-up error from a  previous failure.
                                                                          No apport report written because the error message indicates it's a  follow-up error from a previous failure.
                     No apport report written because MaxReports has already been reached
         No apport report written because MaxReports has already been reached
                                                                              No apport report written because MaxReports has already been  reached
                                                                 No  apport report written because MaxReports has already been reached
                                                     No apport report written because MaxReports has already been reached
                                         No apport report written because MaxReports has already been reached
                             No apport report written because MaxReports has already been reached
                 No apport report written because MaxReports has already been reached
     No apport report written because MaxReports has already been reached
                                                                         igure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2-common:
 libgnome2-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing libgnome2-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2-0:
 libgnome2-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 libgnome2-0 depends on libgnome2-common (>= 2.32); however:
  Package libgnome2-common is not configured yet.
 libgnome2-0 depends on libgnome2-common (<< 2.33); however:
  Package libgnome2-common is not configured yet.
dpkg: error processing libgnome2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of aisleriot:
 aisleriot depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing aisleriot (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-extra:
 libgnomevfs2-extra depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 libgnomevfs2-extra depends on libgnomevfs2-common (>= 1:2.24); however:
  Package libgnomevfs2-common is not configured yet.
 libgnomevfs2-extra depends on libgnomevfs2-common (<< 1:2.25); however:
  Package libgnomevfs2-common is not configured yet.
dpkg: error processing libgnomevfs2-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of light-themes:
 light-themes depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing light-themes (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unity-common:
 unity-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing unity-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unity:
 unity depends on unity-common (= 5.16.0-0ubuntu1); however:
  Package unity-common is not configured yet.
dpkg: error processing unity (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on gnome-media; however:
  Package gnome-media is not configured yet.
 ubuntu-desktop depends on unity; however:
  Package unity is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Setting up deborphan (1.7.28.5) ...
Setting up dialog (1.1-20111020-1) ...
Setting up libgtk2-gladexml-perl (1.007-1build2) ...
dpkg: dependency problems prevent configuration of libgnome2-bin:
 libgnome2-bin depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
dpkg: error processing libgnome2-bin (--configure):
 dependency problems - leaving unconfigured
Processing triggers for menu ...
No apport report written because MaxReports has already been reached
                                                                    Setting up gtkorphan (0.4.4-1) ...
Errors were encountered while processing:
 gconf2
 gnome-media
 libgnomevfs2-common
 libgnomevfs2-0
 libgnome2-common
 libgnome2-0
 aisleriot
 libgnomevfs2-extra
 light-themes
 unity-common
 unity
 ubuntu-desktop
 libgnome2-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

From what I can make of this you had Ubuntu installed and then installed Xubuntu on top of it and also looks like your PPA's are carried over from Ubuntu.

What you can try if this is the case is totally removing Ubuntu.  This is also going to mess with your PPA's, but that's fixable (and there's  probably going to be other things to fix).  To remove Ubuntu:

[http://www.psychocats.net/ubuntu/purexubuntu](http://www.psychocats.net/ubuntu/purexubuntu)

If it was my  system I would just reinstall Xubuntu, I don't like patching things up.  :)

You should also backup any personal data.

---

### Post by s0563764 on 2012-12-12
> **ibjsb4 said:**
> First, Using code tags makes your long post easier to read.  Maybe edit yours.

[http://ubuntuforums.org/showthread.php?t=890901](http://ubuntuforums.org/showthread.php?t=890901)

```
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe deborphan i386 1.7.28.5 [102 kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe dialog i386 1.1-20111020-1 [276 kB]
Get:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe libgtk2-gladexml-perl i386 1.007-1build2 [41.4 kB]
Get:4 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe gtkorphan all 0.4.4-1 [30.7 kB]
Fetched 450 kB in 2s (152 kB/s)     
Selecting previously unselected package deborphan.
(Reading database ... 379888 files and directories currently installed.)
Unpacking deborphan (from .../deborphan_1.7.28.5_i386.deb) ...
Selecting previously unselected package dialog.
Unpacking dialog (from .../dialog_1.1-20111020-1_i386.deb) ...
Selecting previously unselected package libgtk2-gladexml-perl.
Unpacking libgtk2-gladexml-perl (from .../libgtk2-gladexml-perl_1.007-1build2_i386.deb) ...
Selecting previously unselected package gtkorphan.
Unpacking gtkorphan (from .../gtkorphan_0.4.4-1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for menu ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Setting up gconf2 (3.2.5-0ubuntu2) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 97, in <module>
    for f in os.listdir(defaults_dest):
OSError: [Errno 2] No such file or directory: '/var/lib/gconf/defaults'
dpkg: error processing gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gnome-media:
 gnome-media depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-media (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-common:
 libgnomevfs2-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing libgnomevfs2-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-0:
 libgnomevfs2-0 depends on libgnomevfs2-common (>= 1:2.24); however:
  Package libgnomevfs2-common is not configured yet.
 libgnomevfs2-0 depends on libgnomevfs2-common (<< 1:2.25); however:
  Package libgnomevfs2-common is not configured yet.
dpkg: error processing libgnomevfs2-0 (--confNo apport report written  because the error message indicates it's a follow-up error from a  previous failure.
                                                                          No apport report written because the error message indicates it's a  follow-up error from a previous failure.
                     No apport report written because MaxReports has already been reached
         No apport report written because MaxReports has already been reached
                                                                              No apport report written because MaxReports has already been  reached
                                                                 No  apport report written because MaxReports has already been reached
                                                     No apport report written because MaxReports has already been reached
                                         No apport report written because MaxReports has already been reached
                             No apport report written because MaxReports has already been reached
                 No apport report written because MaxReports has already been reached
     No apport report written because MaxReports has already been reached
                                                                         igure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2-common:
 libgnome2-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing libgnome2-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2-0:
 libgnome2-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 libgnome2-0 depends on libgnome2-common (>= 2.32); however:
  Package libgnome2-common is not configured yet.
 libgnome2-0 depends on libgnome2-common (<< 2.33); however:
  Package libgnome2-common is not configured yet.
dpkg: error processing libgnome2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of aisleriot:
 aisleriot depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing aisleriot (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-extra:
 libgnomevfs2-extra depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 libgnomevfs2-extra depends on libgnomevfs2-common (>= 1:2.24); however:
  Package libgnomevfs2-common is not configured yet.
 libgnomevfs2-extra depends on libgnomevfs2-common (<< 1:2.25); however:
  Package libgnomevfs2-common is not configured yet.
dpkg: error processing libgnomevfs2-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of light-themes:
 light-themes depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing light-themes (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unity-common:
 unity-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing unity-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unity:
 unity depends on unity-common (= 5.16.0-0ubuntu1); however:
  Package unity-common is not configured yet.
dpkg: error processing unity (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on gnome-media; however:
  Package gnome-media is not configured yet.
 ubuntu-desktop depends on unity; however:
  Package unity is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Setting up deborphan (1.7.28.5) ...
Setting up dialog (1.1-20111020-1) ...
Setting up libgtk2-gladexml-perl (1.007-1build2) ...
dpkg: dependency problems prevent configuration of libgnome2-bin:
 libgnome2-bin depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
dpkg: error processing libgnome2-bin (--configure):
 dependency problems - leaving unconfigured
Processing triggers for menu ...
No apport report written because MaxReports has already been reached
                                                                    Setting up gtkorphan (0.4.4-1) ...
Errors were encountered while processing:
 gconf2
 gnome-media
 libgnomevfs2-common
 libgnomevfs2-0
 libgnome2-common
 libgnome2-0
 aisleriot
 libgnomevfs2-extra
 light-themes
 unity-common
 unity
 ubuntu-desktop
 libgnome2-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)
```From what I can make of this you had Ubuntu installed and then installed Xubuntu on top of it and also looks like your PPA's are carried over from Ubuntu.

What you can try if this is the case is totally removing Ubuntu.  This is also going to mess with your PPA's, but that's fixable (and there's  probably going to be other things to fix).  To remove Ubuntu:

[http://www.psychocats.net/ubuntu/purexubuntu](http://www.psychocats.net/ubuntu/purexubuntu)

If it was my  system I would just reinstall Xubuntu, I don't like patching things up.  :)

You should also backup any personal data.

Cheers, just haven't learned the format here yet.

I resolved this with a CD upgrade, its a bit patchwork, but I regretfully backed up all the data already

---

