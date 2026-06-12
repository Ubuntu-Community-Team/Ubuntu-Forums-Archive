---
title: "Upgrade to Ubuntu 11.10 deleted Lotus Notes"
date: 2011-10-19
forum: Installation &amp; Upgrades
---

### Post by lads on 2011-10-19
Dear all,

I upgraded to Oneiric yesterday and one of the applications I use the most was deleted: Lotus Notes 8.5.3.

Today I tried to re-install Lotus Notes and things got a bit tricky, running the deb package I get this error:

```
Errors were encountered while processing:
 ibm-lotus-notes:i386

```

Not much information so I tried to install this package:

```
$ sudo apt-get install ibm-lotus-notes:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ibm-lotus-notes:i386 is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 ibm-lotus-notes:i386 : Depends: gdb:i386 but it is not going to be installed
                        Depends: coreutils:i386 but it is not going to be installed
                        Depends: unzip:i386 but it is not going to be installed
                        Depends: bash:i386 but it is not going to be installed
                        Depends: procps:i386 but it is not going to be installed
                        Depends: grep:i386 but it is not going to be installed
                        Depends: sed:i386 but it is not going to be installed
                        Depends: libart-2.0-2:i386 but it is not going to be installed
                        Depends: libbonobo2-0:i386 but it is not going to be installed
                        Depends: libbonoboui2-0:i386 but it is not going to be installed
                        Depends: libgconf2-4:i386 but it is not going to be installed
                        Depends: libgnome2-0:i386 but it is not going to be installed
                        Depends: libgnomecanvas2-0:i386 but it is not going to be installed
                        Depends: libgnome-desktop-2:i386 but it is not installable or
                                 libgnome-desktop-2-7:i386 but it is not installable or
                                 libgnome-desktop-2-11:i386 but it is not installable or
                                 libgnome-desktop-2-17:i386 but it is not going to be installed
                        Depends: libgnomeprint2.2-0:i386 but it is not going to be installed
                        Depends: libgnomeprintui2.2-0:i386 but it is not going to be installed
                        Depends: libgnomeui-0:i386 but it is not going to be installed
                        Depends: libgnomevfs2-0:i386 but it is not going to be installed
                        Depends: liborbit2:i386 but it is not going to be installed
                        Depends: libpopt0:i386 but it is not going to be installed
                        Depends: libxkbfile1:i386 but it is not going to be installed
                        Depends: libxml2:i386 but it is not going to be installed
                        Depends: libxp6:i386 but it is not going to be installed
                        Depends: libxtst6:i386 but it is not going to be installed
                        Recommends: ttf-xfree86-nonfree:i386 but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

When I run 'apt-get -f install' I'm asked to remove a boatload of packages, including things like Java or LibreOffice.

So the main question is how to install Lotus Notes on Ubuntu 11.10. And second question would be why did the upgrade deleted an application, something that had never happened to me before.

Thank you.

---

### Post by Tom43 on 2011-10-20
Notes did not get uninstalled. The console sais: ibm-lotus-notes:i386 is already the newest version. You can verify this by opening the folders, where you installed Notes. Standard folder is /opt/ibm/lotus/notes. But is has now many unmet dependencies, since Ubuntu 11.10 is no more based on gnome 2 but on gnome 3. You have to try to install the packages mentioned, then maybe Notes will run again. But is is very likely that you do not see an icon to start Notes, because Ubuntu 11.10 uses the Unity desktop and I think Notes installation does not create a start icon for it. In that case, you need to create your own. Hope this helps somehow.

---

### Post by kah00na on 2011-10-20
I upgraded too and the /opt/IBM/lotus/notes directory was still there and populated, but it wouldn't start.  I created soft links to all the *.so files in opt/IBM/lotus/notes to /usr/lib like this.
```
cd /opt/ibm/lotus/notes
for file in $(ls *.so); do
   sudo ln -s /opt/ibm/lotus/notes/${file} /usr/lib/${file}
done
```
I then re-downloaded and re-installed the "getlibs-all.deb" from [http://frozenfox.freehostia.com/cappy](http://frozenfox.freehostia.com/cappy).

Then rebooted.  After it came back up, I opened a terminal window and did this and Lotus Notes started!
```
cd /opt/ibm/lotus/notes
./lnotes
```
There are a bunch of errors in the command line window, but it seems to be running fine.

I have to figure out some way to make a new short cut in my menus.  This new Ubuntu interface is still confusing to me.

---

### Post by kah00na on 2011-10-20
Well, it looks like the reboot also made the Lotus Notes icons now show up in the search results (Clicking the Ubuntu logo button, then typing "lotus" in the search box).  I just had to drag it to the bar on the left side of my screen.  That was easy.

---

### Post by lads on 2011-10-21
Folks, when I say "deleted" I really mean deleted.

```
$ ls -la /opt/ibm/lotus/notes
total 5372
drwxr-xr-x 3 root    root      36864 2011-10-19 12:14 .
drwxr-xr-x 3 root    root       4096 2011-07-22 13:13 ..
drwxr-xr-x 3 root    root       4096 2011-10-19 12:14 jvm
-rw-rw-r-- 1 desousa desousa  116732 2010-01-15 21:30 libgdk_pixbuf-2.0.so.0
-rw-rw-r-- 1 desousa desousa   67240 2010-01-15 21:30 libgdk_pixbuf_xlib-2.0.so.0
-rw-rw-r-- 1 desousa desousa  679940 2010-01-15 21:30 libgdk-x11-2.0.so.0
-rw-rw-r-- 1 desousa desousa 4579940 2010-01-15 21:30 libgtk-x11-2.0.so.0
```

Those .so.0 got there already after the upgrade in one of the failed attempts to re-install. The *ibm-lotus-notes:i386* package was there also because of these attempts. I had to remove it because with it installed I wasn't able to either update or upgrade.

By the way there are [ other reports of the upgrade doing this to Lotes Notes and further applications]("http://askubuntu.com/questions/66525/upgrade-removed-lotus-notes-and-some-other-applications"). I perfectly understand that some software may not work after an  upgrade, but removing it is bit too much, IMHO.

The indications by kah00na are a good start but I need to get the software installed first...

Thanks,

Luís

---

### Post by lads on 2011-10-21
To experiment with kah00na's suggestion I tried once again the installation following the [IBM guide]("http://www-10.lotus.com/ldd/nd85forum.nsf/0/69b50f2db7bb7b0b85257659005ab79e?OpenDocument"). Though it ends up also with the error on the *ibm-lotus-notes:i386* the /ibm/lotus/notes directory got populated, which allowed me to run  kah00na's instructions.

After rebooting I tried it and got this error:

```
$ ./lnotes
./lnotes: error while loading shared libraries: libgconf-2.so.4: wrong ELF class: ELFCLASS64

```

If anyone has any other suggestion please let me know. Thank you,

Luís

---

### Post by ondrokm on 2011-10-21
> **lads said:**
> 
After rebooting I tried it and got this error:
```
$ ./lnotes
./lnotes: error while loading shared libraries: libgconf-2.so.4: wrong ELF class: ELFCLASS64

```

I have the same problem, don't know how to solve it :(

---

### Post by lads on 2011-10-24
This Ubuntu release is up for a fight. These being early days after the release I run the upgrade everyday. This morning aptitude reported hundreds of conflicting packages that had to be removed, among these where unity, compiz, virtualbox, tex-live, texmaker and more, rendering the system useless. I'm re-installing these packages from the CD right now to see if I can save this install. Pretty neat.

---

### Post by Niise on 2011-10-25
This is work for me. ubuntu 11.10 x64 with ibm lotus notes 8.5.3
[LIST=1]
[*]you should use getlib ([https://launchpad.net/~jcollins/+archive/jaminppa/+build/1482994/+files/getlibs_2.06-0ubuntu1%7Eppa2_all.deb](https://launchpad.net/~jcollins/+archive/jaminppa/+build/1482994/+files/getlibs_2.06-0ubuntu1%7Eppa2_all.deb)) to get all needed ia32 library.
```

sudo apt-get install libgnomeprintui2.2-0 ia32-libs ttf-xfree86-nonfree t1-xfree86-nonfree

sudo getlibs -p libgnomeprintui2.2-0 libgnomeprint2.2-0 libgnomevfs2-0 libgnomeui-0 libxkbfile1 libstartup-notification0 libsepol1 libselinux1 libgsf-1-114 libgsf-1-dev librsvg2-2 librsvg2-common libavahi-client3 libavahi-common3 libavahi-glib1 libbonoboui2-0 libcroco3 libdbus-1-3 libdbus-glib-1-2  libgnome2-0 libgnomecanvas2-0 libgnome-keyring0 libgnome-menu2 libesd0 gtk2-engines libgnome-desktop-2-17 libmotif4 libmotif3 libgnome-desktop-3-0 libavahi-glib1 gtk2-engines-oxygen gtk2-engines-aurora gtk2-engines-qtcurve  gtk2-engines-murrine gtk2-engines-equinox  alsa-base alsa-utils iproute gnome-desktop-3-2 liborbit2 libbonobo2-0 libgconf2-4
```
[*]unpack the deb (ibm-lotus-notes-8.5.3.i586.deb) to remove the dependence in file UNPACK/DEBIAN/control, let it be blank, if you need sametime feature, do the same thing in ibm-lotus-sametime-8.5.3.i586.deb
```
Pre-Depends:
Depends:
Recommends:
Conflicts:



```
[*]rename original deb to avoid override the origin package.
```
sudo dpkg-deb -b ibm-lotus-notes-8.5.3.i586
```
install the deb of lotus notes
```
sudo dpkg -i &#8211;force-all ibm-lotus-notes-8.5.3.i586.deb
```
[*]you need do a gtk hack of notes, you can get the source code from [https://github.com/sgh/lotus-notes_gtk2.23.3/](https://github.com/sgh/lotus-notes_gtk2.23.3/)
maybe you should change the permission of the libnotesgtkfix.so.
```
make
chmod +x notes-wrapper
sudo cp notes-wrapper libnotesgtkfix.so /opt/ibm/lotus/notes/
```
[*]modify the LotusNotes8.5.desktop file(PATH /usr/share/applications)
```
[Desktop Entry]
Encoding=UTF-8
Name=Lotus Notes 8.5
Type=Application
Exec=env LD_LIBRARY_PATH=/opt/ibm/lotus/notes/:/usr/lib32/:/usr/lib32/i386-linux-gnu/ /opt/ibm/lotus/notes/framework/../notes-wrapper %F
Icon=/opt/ibm/lotus/notes/framework/shared/eclipse/features/com.ibm.notes.links.feature_8.5.3.20110916-0921/icons/notes.ico
Terminal=false
Categories=Application;Office;
```
[*]enjoy your notes.
[*]some tips, you can ldd your notes to check what library leak.
[/LIST]

reference guide
[http://usablesoftware.wordpress.com/2011/10/10/install-lotus-notes-8-5-3-en-on-ubuntu-11-04-64bit/](http://usablesoftware.wordpress.com/2011/10/10/install-lotus-notes-8-5-3-en-on-ubuntu-11-04-64bit/)

PS. i dont suggest you do symbol link like as kah00na. I strongly suggest you use LD_LIBRARY_PATH to fix the search order of libraries which notes need. The simply way is my list point 5

---

### Post by lads on 2011-10-26
Hello Niise, thank you for your reply.

I installed getlibs and then proceeded with libraries. Three of them failed: *libmotif3*, *libgnome-desktop-3-0* and *gnome-desktop-3-2*. Even after adding the Gnome3 PPA getlibs can't find them and browsing the Ubuntu repo pages it seems they've been deleted.

I have no idea what you mean with point 2. Which deb should I unpack? And then what file should I edit to set the blanks?

Anyways, trying to install the lotus notes deb package after installing the libraries with getlibs yields exactly the same result I reported in the opening of this thread.

Thank you,

Luís

---

### Post by Niise on 2011-10-27
I have do some edit in the last post. hope that will help you.
and if the message complain the so not found. 
```
apt-cache search <LIBRARY_NAME_WITHOUT_VERSION>
```
try apt-get install the truly package name and version.

---

### Post by lads on 2011-10-28
Hi Niise, thank you for the update. I managed to get Notes installed, it doesn't run yet but I feel we are getting close. Could you please take a look at log? Thank you.

```

**~$ sudo apt-get install libgnomeprintui2.2-0 ia32-libs ttf-xfree86-nonfree t1-xfree86-nonfree**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
libgnomeprintui2.2-0 is already the newest version.
ttf-xfree86-nonfree is already the newest version.
Suggested packages:
  xfs xserver
The following NEW packages will be installed:
  t1-xfree86-nonfree
0 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
Need to get 939 kB of archives.
After this operation, 2,327 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://de.archive.ubuntu.com/ubuntu/ oneiric/multiverse t1-xfree86-nonfree all 4.2.1-3 [939 kB]
Fetched 939 kB in 0s (1,917 kB/s)          
Selecting previously deselected package t1-xfree86-nonfree.
(Reading database ... 218570 files and directories currently installed.)
Unpacking t1-xfree86-nonfree (from .../t1-xfree86-nonfree_4.2.1-3_all.deb) ...
Processing triggers for fontconfig ...
Setting up t1-xfree86-nonfree (4.2.1-3) ...
Updating fontconfig cache for /usr/share/fonts/type1/t1-xfree86-nonfree
Updating fontconfig cache for /usr/share/fonts/type1/t1-xfree86-nonfree
**~$ sudo getlibs -p libgnomeprintui2.2-0 libgnomeprint2.2-0 libgnomevfs2-0 libgnomeui-0 libxkbfile1 libstartup-notification0 libsepol1 libselinux1 libgsf-1-114 libgsf-1-dev librsvg2-2 librsvg2-common libavahi-client3 libavahi-common3 libavahi-glib1 libbonoboui2-0 libcroco3 libdbus-1-3 libdbus-glib-1-2  libgnome2-0 libgnomecanvas2-0 libgnome-keyring0 libgnome-menu2 libesd0 gtk2-engines libgnome-desktop-2-17 libmotif4 libmotif3 libgnome-desktop-3-0 libavahi-glib1 gtk2-engines-oxygen gtk2-engines-aurora gtk2-engines-qtcurve  gtk2-engines-murrine gtk2-engines-equinox  alsa-base alsa-utils iproute gnome-desktop-3-2 liborbit2 libbonobo2-0 libgconf2-4**
The following i386 packages will be installed: libgnomeprintui2.2-0 libgnomeprint2.2-0 libgnomevfs2-0 libgnomeui-0 libxkbfile1 libstartup-notification0 libsepol1 libselinux1 libgsf-1-114 libgsf-1-dev librsvg2-2 librsvg2-common libavahi-client3 libavahi-common3 libavahi-glib1 libbonoboui2-0 libcroco3 libdbus-1-3 libdbus-glib-1-2 libgnome2-0 libgnomecanvas2-0 libgnome-keyring0 libgnome-menu2 libesd0 gtk2-engines libgnome-desktop-2-17 libmotif4 libmotif3 libgnome-desktop-3-0 libavahi-glib1 gtk2-engines-oxygen gtk2-engines-aurora gtk2-engines-qtcurve gtk2-engines-murrine gtk2-engines-equinox alsa-base alsa-utils iproute gnome-desktop-3-2 liborbit2 libbonobo2-0 libgconf2-4
Continue [Y/n]? Y
libmotif3 was not found in your repositories
Make sure you have all repositories enabled and updated
E: No packages found
libgnome-desktop-3-0 was not found in your repositories
Make sure you have all repositories enabled and updated
E: No packages found
gnome-desktop-3-2 was not found in your repositories
Make sure you have all repositories enabled and updated
Downloading ...
Installing libraries ...
**~$ sudo apt-cache search libmotif**
libmotif-dev - Open Motif - development files
libmotif4 - Open Motif - shared libraries
libmotif4-dbg - Open Motif - shared libraries
**~$ sudo getlibs -p libmotif4**
The following i386 packages will be installed: libmotif4
Continue [Y/n]? Y
Downloading ...
Installing libraries ...
**~$ sudo apt-cache search libgnome-desktop**
libgnome-desktop-2-17 - Utility library for loading .desktop files - runtime files
libgnome-desktop-dev - Utility library for loading .desktop files - development files
libgnome-desktop-3-2 - Utility library for loading .desktop files - runtime files
libgnome-desktop-3-dev - Utility library for loading .desktop files - development files
**~$ sudo getlibs -p libgnome-desktop-3-2**
The following i386 packages will be installed: libgnome-desktop-3-2
Continue [Y/n]? Y
Downloading ...
Installing libraries ...
**~$ sudo apt-cache search gnome-desktop**
gnome-desktop-data - Common files for GNOME desktop apps
libgnome-desktop-2-17 - Utility library for loading .desktop files - runtime files
libgnome-desktop-dev - Utility library for loading .desktop files - development files
gnome-desktop-environment - The GNOME Desktop Environment - transitional package
gnome-desktop-sharp2 - GNOME Desktop# 2.24 suite, CLI bindings for GNOME
libgnomedesktop2.0-cil-dev - CLI binding for GNOME Desktop 2.24
libgnomedesktop2.20-cil - CLI binding for GNOME Desktop 2.24
pychess - chess graphical user interface for several chess engines
gnome-desktop3-data - Common files for GNOME desktop apps
libgnome-desktop-3-2 - Utility library for loading .desktop files - runtime files
libgnome-desktop-3-dev - Utility library for loading .desktop files - development files
**~$ sudo getlibs -p gnome-desktop3-data**
The following i386 packages will be installed: gnome-desktop3-data
Continue [Y/n]? Y
Downloading ...
Installing libraries ...
**~$ cd temp**
**~/temp$ dpkg -x ibm-lotus-notes-8.5.2.i586.deb notes**
**~/temp$ ls -la notes**
total 16
drwxr-xr-x 4 desousa desousa 4096 2010-08-12 00:11 .
drwxr-xr-x 6 desousa desousa 4096 2011-10-28 09:50 ..
drwxr-xr-x 3 desousa desousa 4096 2010-08-12 00:08 opt
drwxr-xr-x 3 desousa desousa 4096 2010-08-12 00:09 usr

[Since this didn't work I unpacked with Nautilus into ibm-lotus-notes-8.5.2.i586]

**~/temp$ cp ibm-lotus-notes-8.5.2.i586/DEBIAN/control ibm-lotus-notes-8.5.2.i586/DEBIAN/control.old**
**~/temp$ pico ibm-lotus-notes-8.5.2.i586/DEBIAN/control**
**~/temp$ cat ibm-lotus-notes-8.5.2.i586/DEBIAN/control**
Package: ibm-lotus-notes
Version: 8.5.2-20100811.1131
Section: IBM
Priority: extra
Architecture: i386
Pre-Depends:
Depends: 
Recommends: 
Conflicts:
Installed-Size: 633888
Maintainer: IBM Lotus Product <sw_support@us.ibm.com>
Description: IBM Lotus Notes
 IBM Lotus Notes software provides a robust and productive user experience with a single point of access to email, calendars, contacts, activities, instant messaging, feeds, office documents, collaboration tools, and business applications. Loaded with new features to help you work smarter, the new user interface presents the tools you need, when and where you need them. Plus, you get quick access to your business information in one integrated view, in the context of the work you're doing. That means you get your job done faster, and easier. You can also install the following optional features once you have installed IBM Lotus Notes: IBM Lotus Sametime, IBM Lotus Composite Application Editor, IBM Lotus Connections, IBM Lotus Symphony.
**~/temp$ sudo dpkg -i –force-all ibm-lotus-notes-8.5.2.i586.deb**
dpkg: error processing –force-all (--install):
 cannot access archive: No such file or directory
(Reading database ... 218648 files and directories currently installed.)
Preparing to replace ibm-lotus-notes:i386 8.5.2-20100811.1131 (using ibm-lotus-notes-8.5.2.i586.deb) ...
cat: /opt/ibm/lotus/notes/framework/rcp/rcplauncher.properties: No such file or directory
Unpacking replacement ibm-lotus-notes:i386 ...

Setting up ibm-lotus-notes:i386 (8.5.2-20100811.1131) ...
mv: cannot stat `/opt/ibm/lotus/notes/framework/rcp/rcplauncher.old': No such file or directory
mv: cannot stat `/opt/ibm/lotus/notes/framework/rcp/rcplauncher.properties.old': No such file or directory
mv: cannot stat `/opt/ibm/lotus/notes/framework/rcp/deploy/install.xml.old': No such file or directory
cat: /opt/ibm/lotus/notes/framework/rcp/deploy/install.xml: No such file or directory
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Errors were encountered while processing:
 –force-all
**~/temp$ git clone git://github.com/sgh/lotus-notes_gtk2.23.3.git**
Cloning into lotus-notes_gtk2.23.3...
remote: Counting objects: 22, done.
remote: Compressing objects: 100% (22/22), done.
remote: Total 22 (delta 8), reused 0 (delta 0)
Receiving objects: 100% (22/22), done.
Resolving deltas: 100% (8/8), done.
**~/temp$ cd lotus-notes_gtk2.23.3/**
**~/temp/lotus-notes_gtk2.23.3$ make**
gcc -Wall -Wextra `pkg-config --cflags gtk+-2.0`-m32 -shared libnotesgtkfix.c -o libnotesgtkfix.so -ldl
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
In file included from /usr/include/stdio.h:28:0,
                 from libnotesgtkfix.c:1:
/usr/include/features.h:323:26: fatal error: bits/predefs.h: No such file or directory
compilation terminated.
make: *** [all] Error 1
**~/temp/lotus-notes_gtk2.23.3$ sudo apt-get install libgtk2.0-dev**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libatk1.0-dev libcairo-script-interpreter2 libcairo2-dev libexpat1-dev libfontconfig1-dev libfreetype6-dev libgdk-pixbuf2.0-dev
  libglib2.0-dev libice-dev libpango1.0-dev libpixman-1-dev libpng12-dev libpthread-stubs0 libpthread-stubs0-dev libsm-dev libx11-dev
  libxau-dev libxcb-render0-dev libxcb-shm0-dev libxcb1-dev libxcomposite-dev libxcursor-dev libxdamage-dev libxdmcp-dev libxext-dev
  libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxrandr-dev libxrender-dev x11proto-composite-dev x11proto-core-dev
  x11proto-damage-dev x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-render-dev x11proto-xext-dev
  x11proto-xinerama-dev xorg-sgml-doctools xtrans-dev
Suggested packages:
  libcairo2-doc libglib2.0-doc python-subunit libgtk2.0-doc libpango1.0-doc
The following NEW packages will be installed:
  libatk1.0-dev libcairo-script-interpreter2 libcairo2-dev libexpat1-dev libfontconfig1-dev libfreetype6-dev libgdk-pixbuf2.0-dev
  libglib2.0-dev libgtk2.0-dev libice-dev libpango1.0-dev libpixman-1-dev libpng12-dev libpthread-stubs0 libpthread-stubs0-dev libsm-dev
  libx11-dev libxau-dev libxcb-render0-dev libxcb-shm0-dev libxcb1-dev libxcomposite-dev libxcursor-dev libxdamage-dev libxdmcp-dev
  libxext-dev libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxrandr-dev libxrender-dev x11proto-composite-dev x11proto-core-dev
  x11proto-damage-dev x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-render-dev x11proto-xext-dev
  x11proto-xinerama-dev xorg-sgml-doctools xtrans-dev
0 upgraded, 44 newly installed, 0 to remove and 6 not upgraded.
Need to get 14.7 MB of archives.
After this operation, 66.0 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/ oneiric/main libglib2.0-dev amd64 2.31.0-0ubuntu1~oneiric1 [2,428 kB]
Get:2 http://de.archive.ubuntu.com/ubuntu/ oneiric/main libcairo-script-interpreter2 amd64 1.10.2-6ubuntu3 [62.1 kB]
Get:3 http://de.archive.ubuntu.com/ubuntu/ oneiric/main libatk1.0-dev amd64 2.2.0-0ubuntu1 [129 kB]
Get:4 http://de.archive.ubuntu.com/ubuntu/ oneiric/main libexpat1-dev amd64 2.0.1-7ubuntu3 [217 kB]
Get:5 http://de.archive.ubuntu.com/ubuntu/ oneiric/main libfreetype6-dev amd64 2.4.4-2ubuntu1 [769 kB]
Get:6 http://de.archive.ubuntu.com/ubuntu/ oneiric/main libfontconfig1-dev amd64 2.8.0-3ubuntu2 [660 kB]
Get:7 http://de.archive.ubuntu.com/ubuntu/ oneiric/main xorg-sgml-doctools amd64 1:1.8-2 [10.9 kB]
Get:8 http://de.archive.ubuntu.com/ubuntu/ oneiric/main x11proto-core-dev amd64 7.0.22-1 [299 kB]
Get:9 http://de.archive.ubuntu.com/ubuntu/ oneiric/main libxau-dev amd64 1:1.0.6-3 [10.5 kB]
Get:10 http://de.archive.ubuntu.com/ubuntu/ oneiric/main libxdmcp-dev amd64 1:1.1.0-3 [45.4 kB]
Get:11 http://de.archive.ubuntu.com/ubuntu/ oneiric/main x11proto-input-dev amd64 2.0.2-2ubuntu1 [69.0 kB]
Get:12 http://de.archive.ubuntu.com/ubuntu/ oneiric/main x11proto-kb-dev amd64 1.0.5-2 [27.6 kB]
Get:13 http://de.archive.ubuntu.com/ubuntu/ oneiric/main xtrans-dev amd64 1.2.6-2 [82.9 kB]
Get:14 http://de.archive.ubuntu.com/ubuntu/ oneiric/main libpthread-stubs0 amd64 0.3-2.1 [3,264 B]
Get:15 http://de.archive.ubuntu.com/ubuntu/ oneiric/main libpthread-stubs0-dev amd64 0.3-2.1 [2,486 B]
Get:16 http://de.archive.ubuntu.com/ubuntu/ oneiric/main libxcb1-dev amd64 1.7-3 [78.0 kB]  
Get:17 http://de.archive.ubuntu.com/ubuntu/ oneiric/main libx11-dev amd64 2:1.4.4-2ubuntu1 [3,263 kB]
Get:18 http://de.archive.ubuntu.com/ubuntu/ oneiric/main x11proto-render-dev amd64 2:0.11.1-2 [20.1 kB]
Get:19 http://de.archive.ubuntu.com/ubuntu/ oneiric/main libxrender-dev amd64 1:0.9.6-2 [28.3 kB]
Get:20 http://de.archive.ubuntu.com/ubuntu/ oneiric/main libpng12-dev amd64 1.2.46-3ubuntu1 [207 kB]
Get:21 http://de.archive.ubuntu.com/ubuntu/ oneiric/main libice-dev amd64 2:1.0.7-2 [132 kB]
Get:22 http://de.archive.ubuntu.com/ubuntu/ oneiric/main libsm-dev amd64 2:1.2.0-2 [87.6 kB]
Get:23 http://de.archive.ubuntu.com/ubuntu/ oneiric/main libpixman-1-dev amd64 0.22.2-1 [226 kB]
Get:24 http://de.archive.ubuntu.com/ubuntu/ oneiric/main libxcb-render0-dev amd64 1.7-3 [21.1 kB]
Get:25 http://de.archive.ubuntu.com/ubuntu/ oneiric/main libxcb-shm0-dev amd64 1.7-3 [8,492 B]
Get:26 http://de.archive.ubuntu.com/ubuntu/ oneiric/main libcairo2-dev amd64 1.10.2-6ubuntu3 [586 kB]
Get:27 http://de.archive.ubuntu.com/ubuntu/ oneiric/main libgdk-pixbuf2.0-dev amd64 2.24.0-1ubuntu1 [49.1 kB]
Get:28 http://de.archive.ubuntu.com/ubuntu/ oneiric/main libxft-dev amd64 2.2.0-3ubuntu1 [55.0 kB]
Get:29 http://de.archive.ubuntu.com/ubuntu/ oneiric/main libpango1.0-dev amd64 1.29.3+git20110916-0ubuntu1 [499 kB]
Get:30 http://de.archive.ubuntu.com/ubuntu/ oneiric/main x11proto-xext-dev amd64 7.2.0-3 [253 kB]
Get:31 http://de.archive.ubuntu.com/ubuntu/ oneiric/main libxext-dev amd64 2:1.3.0-3 [144 kB]
Get:32 http://de.archive.ubuntu.com/ubuntu/ oneiric/main x11proto-xinerama-dev amd64 1.2.1-2 [4,966 B]
Get:33 http://de.archive.ubuntu.com/ubuntu/ oneiric/main libxinerama-dev amd64 2:1.1.1-3 [8,490 B]
Get:34 http://de.archive.ubuntu.com/ubuntu/ oneiric/main libxi-dev amd64 2:1.4.3-3ubuntu1 [218 kB]
Get:35 http://de.archive.ubuntu.com/ubuntu/ oneiric/main x11proto-randr-dev all 1.4.0+git20101207.0d32bb07-0ubuntu1 [32.0 kB]
Get:36 http://de.archive.ubuntu.com/ubuntu/ oneiric/main libxrandr-dev amd64 2:1.3.2-2 [24.9 kB]
Get:37 http://de.archive.ubuntu.com/ubuntu/ oneiric/main x11proto-fixes-dev amd64 1:5.0-2 [14.4 kB]
Get:38 http://de.archive.ubuntu.com/ubuntu/ oneiric/main libxfixes-dev amd64 1:5.0-4 [13.1 kB]
Get:39 http://de.archive.ubuntu.com/ubuntu/ oneiric/main libxcursor-dev amd64 1:1.1.12-1 [29.9 kB]
Get:40 http://de.archive.ubuntu.com/ubuntu/ oneiric/main x11proto-composite-dev amd64 1:0.4.2-2 [10.5 kB]
Get:41 http://de.archive.ubuntu.com/ubuntu/ oneiric/main libxcomposite-dev amd64 1:0.4.3-2 [9,754 B]
Get:42 http://de.archive.ubuntu.com/ubuntu/ oneiric/main x11proto-damage-dev amd64 1:1.2.1-2 [8,286 B]
Get:43 http://de.archive.ubuntu.com/ubuntu/ oneiric/main libxdamage-dev amd64 1:1.1.3-2 [5,700 B]
Get:44 http://de.archive.ubuntu.com/ubuntu/ oneiric/main libgtk2.0-dev amd64 2.24.6-0ubuntu5 [3,862 kB]
Fetched 14.7 MB in 3s (4,179 kB/s)          
Extracting templates from packages: 100%
Selecting previously deselected package libcairo-script-interpreter2.
(Reading database ... 237688 files and directories currently installed.)
Unpacking libcairo-script-interpreter2 (from .../libcairo-script-interpreter2_1.10.2-6ubuntu3_amd64.deb) ...
Selecting previously deselected package libglib2.0-dev.
Unpacking libglib2.0-dev (from .../libglib2.0-dev_2.31.0-0ubuntu1~oneiric1_amd64.deb) ...
Selecting previously deselected package libatk1.0-dev.
Unpacking libatk1.0-dev (from .../libatk1.0-dev_2.2.0-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libexpat1-dev.
Unpacking libexpat1-dev (from .../libexpat1-dev_2.0.1-7ubuntu3_amd64.deb) ...
Selecting previously deselected package libfreetype6-dev.
Unpacking libfreetype6-dev (from .../libfreetype6-dev_2.4.4-2ubuntu1_amd64.deb) ...
Selecting previously deselected package libfontconfig1-dev.
Unpacking libfontconfig1-dev (from .../libfontconfig1-dev_2.8.0-3ubuntu2_amd64.deb) ...
Selecting previously deselected package xorg-sgml-doctools.
Unpacking xorg-sgml-doctools (from .../xorg-sgml-doctools_1%3a1.8-2_amd64.deb) ...
Selecting previously deselected package x11proto-core-dev.
Unpacking x11proto-core-dev (from .../x11proto-core-dev_7.0.22-1_amd64.deb) ...
Selecting previously deselected package libxau-dev.
Unpacking libxau-dev (from .../libxau-dev_1%3a1.0.6-3_amd64.deb) ...
Selecting previously deselected package libxdmcp-dev.
Unpacking libxdmcp-dev (from .../libxdmcp-dev_1%3a1.1.0-3_amd64.deb) ...
Selecting previously deselected package x11proto-input-dev.
Unpacking x11proto-input-dev (from .../x11proto-input-dev_2.0.2-2ubuntu1_amd64.deb) ...
Selecting previously deselected package x11proto-kb-dev.
Unpacking x11proto-kb-dev (from .../x11proto-kb-dev_1.0.5-2_amd64.deb) ...
Selecting previously deselected package xtrans-dev.
Unpacking xtrans-dev (from .../xtrans-dev_1.2.6-2_amd64.deb) ...
Selecting previously deselected package libpthread-stubs0.
Unpacking libpthread-stubs0 (from .../libpthread-stubs0_0.3-2.1_amd64.deb) ...
Selecting previously deselected package libpthread-stubs0-dev.
Unpacking libpthread-stubs0-dev (from .../libpthread-stubs0-dev_0.3-2.1_amd64.deb) ...
Selecting previously deselected package libxcb1-dev.
Unpacking libxcb1-dev (from .../libxcb1-dev_1.7-3_amd64.deb) ...
Selecting previously deselected package libx11-dev.
Unpacking libx11-dev (from .../libx11-dev_2%3a1.4.4-2ubuntu1_amd64.deb) ...
Selecting previously deselected package x11proto-render-dev.
Unpacking x11proto-render-dev (from .../x11proto-render-dev_2%3a0.11.1-2_amd64.deb) ...
Selecting previously deselected package libxrender-dev.
Unpacking libxrender-dev (from .../libxrender-dev_1%3a0.9.6-2_amd64.deb) ...
Selecting previously deselected package libpng12-dev.
Unpacking libpng12-dev (from .../libpng12-dev_1.2.46-3ubuntu1_amd64.deb) ...
Selecting previously deselected package libice-dev.
Unpacking libice-dev (from .../libice-dev_2%3a1.0.7-2_amd64.deb) ...
Selecting previously deselected package libsm-dev.
Unpacking libsm-dev (from .../libsm-dev_2%3a1.2.0-2_amd64.deb) ...
Selecting previously deselected package libpixman-1-dev.
Unpacking libpixman-1-dev (from .../libpixman-1-dev_0.22.2-1_amd64.deb) ...
Selecting previously deselected package libxcb-render0-dev.
Unpacking libxcb-render0-dev (from .../libxcb-render0-dev_1.7-3_amd64.deb) ...
Selecting previously deselected package libxcb-shm0-dev.
Unpacking libxcb-shm0-dev (from .../libxcb-shm0-dev_1.7-3_amd64.deb) ...
Selecting previously deselected package libcairo2-dev.
Unpacking libcairo2-dev (from .../libcairo2-dev_1.10.2-6ubuntu3_amd64.deb) ...
Selecting previously deselected package libgdk-pixbuf2.0-dev.
Unpacking libgdk-pixbuf2.0-dev (from .../libgdk-pixbuf2.0-dev_2.24.0-1ubuntu1_amd64.deb) ...
Selecting previously deselected package libxft-dev.
Unpacking libxft-dev (from .../libxft-dev_2.2.0-3ubuntu1_amd64.deb) ...
Selecting previously deselected package libpango1.0-dev.
Unpacking libpango1.0-dev (from .../libpango1.0-dev_1.29.3+git20110916-0ubuntu1_amd64.deb) ...
Selecting previously deselected package x11proto-xext-dev.
Unpacking x11proto-xext-dev (from .../x11proto-xext-dev_7.2.0-3_amd64.deb) ...
Selecting previously deselected package libxext-dev.
Unpacking libxext-dev (from .../libxext-dev_2%3a1.3.0-3_amd64.deb) ...
Selecting previously deselected package x11proto-xinerama-dev.
Unpacking x11proto-xinerama-dev (from .../x11proto-xinerama-dev_1.2.1-2_amd64.deb) ...
Selecting previously deselected package libxinerama-dev.
Unpacking libxinerama-dev (from .../libxinerama-dev_2%3a1.1.1-3_amd64.deb) ...
Selecting previously deselected package libxi-dev.
Unpacking libxi-dev (from .../libxi-dev_2%3a1.4.3-3ubuntu1_amd64.deb) ...
Selecting previously deselected package x11proto-randr-dev.
Unpacking x11proto-randr-dev (from .../x11proto-randr-dev_1.4.0+git20101207.0d32bb07-0ubuntu1_all.deb) ...
Selecting previously deselected package libxrandr-dev.
Unpacking libxrandr-dev (from .../libxrandr-dev_2%3a1.3.2-2_amd64.deb) ...
Selecting previously deselected package x11proto-fixes-dev.
Unpacking x11proto-fixes-dev (from .../x11proto-fixes-dev_1%3a5.0-2_amd64.deb) ...
Selecting previously deselected package libxfixes-dev.
Unpacking libxfixes-dev (from .../libxfixes-dev_1%3a5.0-4_amd64.deb) ...
Selecting previously deselected package libxcursor-dev.
Unpacking libxcursor-dev (from .../libxcursor-dev_1%3a1.1.12-1_amd64.deb) ...
Selecting previously deselected package x11proto-composite-dev.
Unpacking x11proto-composite-dev (from .../x11proto-composite-dev_1%3a0.4.2-2_amd64.deb) ...
Selecting previously deselected package libxcomposite-dev.
Unpacking libxcomposite-dev (from .../libxcomposite-dev_1%3a0.4.3-2_amd64.deb) ...
Selecting previously deselected package x11proto-damage-dev.
Unpacking x11proto-damage-dev (from .../x11proto-damage-dev_1%3a1.2.1-2_amd64.deb) ...
Selecting previously deselected package libxdamage-dev.
Unpacking libxdamage-dev (from .../libxdamage-dev_1%3a1.1.3-2_amd64.deb) ...
Selecting previously deselected package libgtk2.0-dev.
Unpacking libgtk2.0-dev (from .../libgtk2.0-dev_2.24.6-0ubuntu5_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for libglib2.0-0:i386 ...
Processing triggers for libglib2.0-0 ...
Processing triggers for doc-base ...
Processing 3 added doc-base files...
Registering documents with scrollkeeper...
Setting up libcairo-script-interpreter2 (1.10.2-6ubuntu3) ...
Setting up libglib2.0-dev (2.31.0-0ubuntu1~oneiric1) ...
Setting up libatk1.0-dev (2.2.0-0ubuntu1) ...
Setting up libexpat1-dev (2.0.1-7ubuntu3) ...
Setting up libfreetype6-dev (2.4.4-2ubuntu1) ...
Setting up libfontconfig1-dev (2.8.0-3ubuntu2) ...
Setting up xorg-sgml-doctools (1:1.8-2) ...
Setting up x11proto-core-dev (7.0.22-1) ...
Setting up libxau-dev (1:1.0.6-3) ...
Setting up libxdmcp-dev (1:1.1.0-3) ...
Setting up x11proto-input-dev (2.0.2-2ubuntu1) ...
Setting up x11proto-kb-dev (1.0.5-2) ...
Setting up xtrans-dev (1.2.6-2) ...
Setting up libpthread-stubs0 (0.3-2.1) ...
Setting up libpthread-stubs0-dev (0.3-2.1) ...
Setting up libxcb1-dev (1.7-3) ...
Setting up libx11-dev (2:1.4.4-2ubuntu1) ...
Setting up x11proto-render-dev (2:0.11.1-2) ...
Setting up libxrender-dev (1:0.9.6-2) ...
Setting up libpng12-dev (1.2.46-3ubuntu1) ...
Setting up libice-dev (2:1.0.7-2) ...
Setting up libsm-dev (2:1.2.0-2) ...
Setting up libpixman-1-dev (0.22.2-1) ...
Setting up libxcb-render0-dev (1.7-3) ...
Setting up libxcb-shm0-dev (1.7-3) ...
Setting up libcairo2-dev (1.10.2-6ubuntu3) ...
Setting up libgdk-pixbuf2.0-dev (2.24.0-1ubuntu1) ...
Setting up libxft-dev (2.2.0-3ubuntu1) ...
Setting up libpango1.0-dev (1.29.3+git20110916-0ubuntu1) ...
Setting up x11proto-xext-dev (7.2.0-3) ...
Setting up libxext-dev (2:1.3.0-3) ...
Setting up x11proto-xinerama-dev (1.2.1-2) ...
Setting up libxinerama-dev (2:1.1.1-3) ...
Setting up libxi-dev (2:1.4.3-3ubuntu1) ...
Setting up x11proto-randr-dev (1.4.0+git20101207.0d32bb07-0ubuntu1) ...
Setting up libxrandr-dev (2:1.3.2-2) ...
Setting up x11proto-fixes-dev (1:5.0-2) ...
Setting up libxfixes-dev (1:5.0-4) ...
Setting up libxcursor-dev (1:1.1.12-1) ...
Setting up x11proto-composite-dev (1:0.4.2-2) ...
Setting up libxcomposite-dev (1:0.4.3-2) ...
Setting up x11proto-damage-dev (1:1.2.1-2) ...
Setting up libxdamage-dev (1:1.1.3-2) ...
Setting up libgtk2.0-dev (2.24.6-0ubuntu5) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
**~/temp/lotus-notes_gtk2.23.3$ sudo apt-get install g++-multilib**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  g++ g++-4.6 g++-4.6-multilib gcc-4.6-multilib gcc-multilib lib32gomp1 lib32quadmath0 libc6-dev-i386 libstdc++6-4.6-dev
Suggested packages:
  gcc-4.6-doc libstdc++6-4.6-dbg lib32stdc++6-4.6-dbg lib32mudflap0 libstdc++6-4.6-doc
The following NEW packages will be installed:
  g++ g++-4.6 g++-4.6-multilib g++-multilib gcc-4.6-multilib gcc-multilib lib32gomp1 lib32quadmath0 libc6-dev-i386 libstdc++6-4.6-dev
0 upgraded, 10 newly installed, 0 to remove and 6 not upgraded.
Need to get 13.9 MB of archives.
After this operation, 42.4 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y 
Get:1 http://de.archive.ubuntu.com/ubuntu/ oneiric/main libc6-dev-i386 amd64 2.13-20ubuntu5 [1,517 kB]
Get:2 http://de.archive.ubuntu.com/ubuntu/ oneiric/main lib32gomp1 amd64 4.6.1-9ubuntu3 [28.2 kB]
Get:3 http://de.archive.ubuntu.com/ubuntu/ oneiric/main lib32quadmath0 amd64 4.6.1-9ubuntu3 [195 kB]
Get:4 http://de.archive.ubuntu.com/ubuntu/ oneiric/main gcc-4.6-multilib amd64 4.6.1-9ubuntu3 [2,534 kB]
Get:5 http://de.archive.ubuntu.com/ubuntu/ oneiric/main gcc-multilib amd64 4:4.6.1-2ubuntu5 [962 B]
Get:6 http://de.archive.ubuntu.com/ubuntu/ oneiric/main libstdc++6-4.6-dev amd64 4.6.1-9ubuntu3 [1,644 kB]
Get:7 http://de.archive.ubuntu.com/ubuntu/ oneiric/main g++-4.6 amd64 4.6.1-9ubuntu3 [6,970 kB]
Get:8 http://de.archive.ubuntu.com/ubuntu/ oneiric/main g++ amd64 4:4.6.1-2ubuntu5 [1,444 B]
Get:9 http://de.archive.ubuntu.com/ubuntu/ oneiric/main g++-4.6-multilib amd64 4.6.1-9ubuntu3 [1,015 kB]
Get:10 http://de.archive.ubuntu.com/ubuntu/ oneiric/main g++-multilib amd64 4:4.6.1-2ubuntu5 [872 B]
Fetched 13.9 MB in 4s (3,407 kB/s)    
Selecting previously deselected package libc6-dev-i386.
(Reading database ... 240673 files and directories currently installed.)
Unpacking libc6-dev-i386 (from .../libc6-dev-i386_2.13-20ubuntu5_amd64.deb) ...
Selecting previously deselected package lib32gomp1.
Unpacking lib32gomp1 (from .../lib32gomp1_4.6.1-9ubuntu3_amd64.deb) ...
Selecting previously deselected package lib32quadmath0.
Unpacking lib32quadmath0 (from .../lib32quadmath0_4.6.1-9ubuntu3_amd64.deb) ...
Selecting previously deselected package gcc-4.6-multilib.
Unpacking gcc-4.6-multilib (from .../gcc-4.6-multilib_4.6.1-9ubuntu3_amd64.deb) ...
Selecting previously deselected package gcc-multilib.
Unpacking gcc-multilib (from .../gcc-multilib_4%3a4.6.1-2ubuntu5_amd64.deb) ...
Selecting previously deselected package libstdc++6-4.6-dev.
Unpacking libstdc++6-4.6-dev (from .../libstdc++6-4.6-dev_4.6.1-9ubuntu3_amd64.deb) ...
Selecting previously deselected package g++-4.6.
Unpacking g++-4.6 (from .../g++-4.6_4.6.1-9ubuntu3_amd64.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.6.1-2ubuntu5_amd64.deb) ...
Selecting previously deselected package g++-4.6-multilib.
Unpacking g++-4.6-multilib (from .../g++-4.6-multilib_4.6.1-9ubuntu3_amd64.deb) ...
Selecting previously deselected package g++-multilib.
Unpacking g++-multilib (from .../g++-multilib_4%3a4.6.1-2ubuntu5_amd64.deb) ...
Processing triggers for man-db ...
Setting up libc6-dev-i386 (2.13-20ubuntu5) ...
Setting up lib32gomp1 (4.6.1-9ubuntu3) ...
Setting up lib32quadmath0 (4.6.1-9ubuntu3) ...
Setting up gcc-4.6-multilib (4.6.1-9ubuntu3) ...
Setting up gcc-multilib (4:4.6.1-2ubuntu5) ...
Setting up g++-4.6 (4.6.1-9ubuntu3) ...
Setting up libstdc++6-4.6-dev (4.6.1-9ubuntu3) ...
Setting up g++ (4:4.6.1-2ubuntu5) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode.
Setting up g++-4.6-multilib (4.6.1-9ubuntu3) ...
Setting up g++-multilib (4:4.6.1-2ubuntu5) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
**~/temp/lotus-notes_gtk2.23.3$ make**
gcc -Wall -Wextra `pkg-config --cflags gtk+-2.0`-m32 -shared libnotesgtkfix.c -o libnotesgtkfix.so -ldl
**~/temp/lotus-notes_gtk2.23.3$ chmod +x notes-wrapper**
**~/temp/lotus-notes_gtk2.23.3$ sudo cp notes-wrapper libnotesgtkfix.so /opt/ibm/lotus/notes/**
**~/temp/lotus-notes_gtk2.23.3$ sudo cp /usr/share/applications/LotusNotes8.5.desktop /usr/share/applications/LotusNotes8.5.desktop.old**
**~/temp/lotus-notes_gtk2.23.3$ sudo pico /usr/share/applications/LotusNotes8.5.desktop**
**~/temp/lotus-notes_gtk2.23.3$ cat /usr/share/applications/LotusNotes8.5.desktop**
[Desktop Entry]
Encoding=UTF-8
Name=Lotus Notes 8.5
Type=Application
Exec=env LD_LIBRARY_PATH=/opt/ibm/lotus/notes/:/usr/lib32/:/usr/lib32/i386-linux-gnu/ /opt/ibm/lotus/notes/framework/../notes-wrapper %F
Icon=/opt/ibm/lotus/notes/framework/shared/eclipse/features/com.ibm.notes.links.feature_8.5.2.20100811-1131/icons/notes.ico
Terminal=false
Categories=Application;Office;
**~/temp/lotus-notes_gtk2.23.3$ env LD_LIBRARY_PATH=/opt/ibm/lotus/notes/:/usr/lib32/:/usr/lib32/i386-linux-gnu/ /opt/ibm/lotus/notes/framework/../notes-wrapper %F**
JVMJ9VM039I -Xscmx is ignored if -Xshareclasses is not specified
JVMJ9VM067W -Xshareclasses not enabled, -Xzero:sharezip option ignored

Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64

(notes2:14597): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(notes2:14597): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(notes2:14597): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(notes2:14597): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(notes2:14597): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(notes2:14597): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(notes2:14597): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(notes2:14597): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(notes2:14597): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(notes2:14597): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(notes2:14597): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(notes2:14597): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(notes2:14597): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(notes2:14597): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(notes2:14597): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(notes2:14597): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(notes2:14597): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(notes2:14597): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(notes2:14597): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(notes2:14597): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(notes2:14597): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(notes2:14597): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(notes2:14597): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(notes2:14597): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(notes2:14597): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(notes2:14597): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(notes2:14597): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(notes2:14597): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(notes2:14597): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(notes2:14597): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(notes2:14597): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(notes2:14597): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(notes2:14597): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(notes2:14597): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(notes2:14597): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(notes2:14597): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(notes2:14597): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(notes2:14597): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(notes2:14597): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(notes2:14597): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(notes2:14597): GdkPixbuf-WARNING **: Cannot open pixbuf loader module file '/etc/gtk-2.0/gdk-pixbuf.loaders': No such file or directory

(notes2:14597): GdkPixbuf-CRITICAL **: IA__gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(notes2:14597): GdkPixbuf-CRITICAL **: IA__gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(notes2:14597): Gtk-CRITICAL **: IA__gtk_window_resize: assertion `width > 0' failed


```

---

### Post by ondrokm on 2011-10-29
The instruction from Niise didn't work for me :(
I finally get Lotus notes 8.5.3 working using wine:
[LIST]
[*]Install Lotus notes on windows machine (e.g. C:/Program Files/Lotus Notes)
[*]Copy the folder with files (C:/Program Files/Lotus Notes) to your linux pc
[*]Do not try to use your Data directory from previous linux version of Lotus notes, it would cause problems
[*]Edit Lotus Notes/notes.ini (e.g. ~/.wine/drive_c/Program Files/Lotus Notes/notes.ini) and after the "[Notes]" put the line: "UseBasicNotus=1" - now it will be the second line. Found here: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=23604](http://appdb.winehq.org/objectManager.php?sClass=version&iId=23604)
[*]Run Lotus notes ($ wine notes.exe)
[/LIST]

I don't like using wine but it's working :(

---

### Post by Niise on 2011-10-30
Could you try to type following ldd command? 
```

LD_LIBRARY_PATH=/opt/ibm/lotus/notes/:/usr/lib32/:/usr/lib32/i386-linux-gnu/ LANGUAGE=zh_TW.UTF-8 ldd /opt/ibm/lotus/notes/framework/../lnotes

```

the log can help to check the library dependence.
please check all *.so come from /usr/lib32 or /lib32 or lotus notes install directory.
```
 LD_LIBRARY_PATH=/opt/ibm/lotus/notes/:/usr/lib32/:/usr/lib32/i386-linux-gnu/ LANGUAGE=zh_TW.UTF-8 ldd /opt/ibm/lotus/notes/framework/../lnotes
	linux-gate.so.1 =>  (0xf7726000)
	libnotes.so => /opt/ibm/lotus/notes/libnotes.so (0xf5243000)
	libXt.so.6 => /usr/lib32/libXt.so.6 (0xf51e7000)
	libX11.so.6 => /usr/lib32/libX11.so.6 (0xf50b0000)
	libdl.so.2 => /lib32/libdl.so.2 (0xf5089000)
	libemulator.so => /opt/ibm/lotus/notes/libemulator.so (0xf4eca000)
	libpthread.so.0 => /lib32/libpthread.so.0 (0xf4eaf000)
	libresolv.so.2 => /lib32/libresolv.so.2 (0xf4e98000)
	libdxlo.so => /opt/ibm/lotus/notes/libdxlo.so (0xf4dfe000)
	libxpm.so => /opt/ibm/lotus/notes/libxpm.so (0xf4df8000)
	libxmlproc.so => /opt/ibm/lotus/notes/libxmlproc.so (0xf49f8000)
	libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf490d000)
	libm.so.6 => /lib32/libm.so.6 (0xf48e3000)
	libc.so.6 => /lib32/libc.so.6 (0xf4769000)
	libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf474a000)
	libndgts.so => /opt/ibm/lotus/notes/libndgts.so (0xf4748000)
	libglib-2.0.so.0 => /lib32/libglib-2.0.so.0 (0xf464f000)
	libxmlcommon.so => /opt/ibm/lotus/notes/libxmlcommon.so (0xf4630000)
	librt.so.1 => /lib32/librt.so.1 (0xf4627000)
	libSM.so.6 => /usr/lib32/libSM.so.6 (0xf461d000)
	libICE.so.6 => /usr/lib32/libICE.so.6 (0xf4603000)
	libxcb.so.1 => /usr/lib32/libxcb.so.1 (0xf45e4000)
	/lib/ld-linux.so.2 (0xf7727000)
	libgtk-x11-2.0.so.0 => /usr/lib32/libgtk-x11-2.0.so.0 (0xf417b000)
	libgdk-x11-2.0.so.0 => /usr/lib32/libgdk-x11-2.0.so.0 (0xf40cd000)
	libgdk_pixbuf-2.0.so.0 => /usr/lib32/libgdk_pixbuf-2.0.so.0 (0xf40ac000)
	libpango-1.0.so.0 => /usr/lib32/libpango-1.0.so.0 (0xf4063000)
	libpangoxft-1.0.so.0 => /usr/lib32/libpangoxft-1.0.so.0 (0xf405a000)
	libpangoft2-1.0.so.0 => /usr/lib32/libpangoft2-1.0.so.0 (0xf402d000)
	libgobject-2.0.so.0 => /usr/lib32/libgobject-2.0.so.0 (0xf3fde000)
	libgnomeprint-2-2.so.0 => /usr/lib32/libgnomeprint-2-2.so.0 (0xf3f69000)
	libgnomeprintui-2-2.so.0 => /usr/lib32/libgnomeprintui-2-2.so.0 (0xf3f24000)
	libgthread-2.0.so.0 => /usr/lib32/libgthread-2.0.so.0 (0xf3f1e000)
	libgnomevfs-2.so.0 => /usr/lib32/libgnomevfs-2.so.0 (0xf3eb5000)
	libgnome-2.so.0 => /usr/lib32/libgnome-2.so.0 (0xf3ea1000)
	libfreetype.so.6 => /usr/lib32/libfreetype.so.6 (0xf3e09000)
	libfontconfig.so.1 => /usr/lib32/libfontconfig.so.1 (0xf3dd4000)
	libgconf-2.so.4 => /usr/lib32/libgconf-2.so.4 (0xf3da6000)
	libcups.so.2 => /usr/lib32/libcups.so.2 (0xf3d54000)
	libXcursor.so.1 => /usr/lib32/libXcursor.so.1 (0xf3d49000)
	libgnomeui-2.so.0 => /usr/lib32/libgnomeui-2.so.0 (0xf3cb0000)
	libxml2.so.2 => /usr/lib32/libxml2.so.2 (0xf3b63000)
	libpcre.so.3 => /lib32/libpcre.so.3 (0xf3b24000)
	libuuid.so.1 => /lib32/libuuid.so.1 (0xf3b1e000)
	libXau.so.6 => /usr/lib32/libXau.so.6 (0xf3b19000)
	libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf3b12000)
	libpangocairo-1.0.so.0 => /usr/lib32/libpangocairo-1.0.so.0 (0xf3b05000)
	libXfixes.so.3 => /usr/lib32/libXfixes.so.3 (0xf3aff000)
	libatk-1.0.so.0 => /usr/lib32/libatk-1.0.so.0 (0xf3adf000)
	libcairo.so.2 => /usr/lib32/libcairo.so.2 (0xf3a13000)
	libgio-2.0.so.0 => /usr/lib32/libgio-2.0.so.0 (0xf38cd000)
	libgmodule-2.0.so.0 => /usr/lib32/libgmodule-2.0.so.0 (0xf38c8000)
	libXext.so.6 => /usr/lib32/libXext.so.6 (0xf38b5000)
	libXrender.so.1 => /usr/lib32/libXrender.so.1 (0xf38aa000)
	libXinerama.so.1 => /usr/lib32/libXinerama.so.1 (0xf38a5000)
	libXi.so.6 => /usr/lib32/libXi.so.6 (0xf3895000)
	libXrandr.so.2 => /usr/lib32/libXrandr.so.2 (0xf388c000)
	libXcomposite.so.1 => /usr/lib32/libXcomposite.so.1 (0xf3888000)
	libXdamage.so.1 => /usr/lib32/libXdamage.so.1 (0xf3884000)
	libXft.so.2 => /usr/lib32/libXft.so.2 (0xf386d000)
	libffi.so.6 => /usr/lib32/libffi.so.6 (0xf3866000)
	libart_lgpl_2.so.2 => /usr/lib32/libart_lgpl_2.so.2 (0xf384f000)
	libz.so.1 => /usr/lib32/libz.so.1 (0xf383a000)
	libgnomecanvas-2.so.0 => /usr/lib32/libgnomecanvas-2.so.0 (0xf3804000)
	libdbus-glib-1.so.2 => /usr/lib32/libdbus-glib-1.so.2 (0xf37de000)
	libdbus-1.so.3 => /lib32/libdbus-1.so.3 (0xf3795000)
	libgnutls.so.26 => /usr/lib32/libgnutls.so.26 (0xf36e5000)
	libavahi-glib.so.1 => /usr/lib32/i386-linux-gnu/libavahi-glib.so.1 (0xf36e0000)
	libavahi-common.so.3 => /usr/lib32/libavahi-common.so.3 (0xf36d2000)
	libavahi-client.so.3 => /usr/lib32/libavahi-client.so.3 (0xf36be000)
	libutil.so.1 => /lib32/libutil.so.1 (0xf36ba000)
	libbonobo-2.so.0 => /usr/lib32/libbonobo-2.so.0 (0xf365f000)
	libbonobo-activation.so.4 => /usr/lib32/libbonobo-activation.so.4 (0xf364a000)
	libORBit-2.so.0 => /usr/lib32/libORBit-2.so.0 (0xf35ef000)
	libcanberra.so.0 => /usr/lib32/libcanberra.so.0 (0xf35dd000)
	libpopt.so.0 => /lib32/libpopt.so.0 (0xf35d1000)
	libexpat.so.1 => /lib32/libexpat.so.1 (0xf35a7000)
	libgssapi_krb5.so.2 => /usr/lib32/libgssapi_krb5.so.2 (0xf3569000)
	libbonoboui-2.so.0 => /usr/lib32/libbonoboui-2.so.0 (0xf350e000)
	libgnome-keyring.so.0 => /usr/lib32/libgnome-keyring.so.0 (0xf34eb000)
	libpixman-1.so.0 => /usr/lib32/libpixman-1.so.0 (0xf3468000)
	libpng12.so.0 => /usr/lib32/libpng12.so.0 (0xf343e000)
	libxcb-shm.so.0 => /usr/lib32/libxcb-shm.so.0 (0xf343a000)
	libxcb-render.so.0 => /usr/lib32/libxcb-render.so.0 (0xf3430000)
	libselinux.so.1 => /lib32/libselinux.so.1 (0xf3411000)
	libgailutil.so.18 => /usr/lib32/libgailutil.so.18 (0xf3409000)
	libtasn1.so.3 => /usr/lib/i386-linux-gnu/libtasn1.so.3 (0xf33f7000)
	libgcrypt.so.11 => /lib32/libgcrypt.so.11 (0xf3372000)
	libORBitCosNaming-2.so.0 => /usr/lib32/libORBitCosNaming-2.so.0 (0xf336b000)
	libvorbisfile.so.3 => /usr/lib32/libvorbisfile.so.3 (0xf3361000)
	libtdb.so.1 => /usr/lib32/libtdb.so.1 (0xf334e000)
	libltdl.so.7 => /usr/lib32/libltdl.so.7 (0xf3344000)
	libkrb5.so.3 => /usr/lib32/libkrb5.so.3 (0xf327b000)
	libk5crypto.so.3 => /usr/lib32/libk5crypto.so.3 (0xf3251000)
	libcom_err.so.2 => /lib32/libcom_err.so.2 (0xf324d000)
	libkrb5support.so.0 => /usr/lib32/libkrb5support.so.0 (0xf3244000)
	libgpg-error.so.0 => /lib32/libgpg-error.so.0 (0xf323f000)
	libvorbis.so.0 => /usr/lib32/libvorbis.so.0 (0xf3213000)
	libogg.so.0 => /usr/lib32/libogg.so.0 (0xf320b000)
	libkeyutils.so.1 => /lib32/libkeyutils.so.1 (0xf3207000)

```


besides, form your log, the error should not occur. Files could not been found in install script, that mean some configure tool execute fail in installer.
could you try to reboot after install all lib32?
Install lotus-notes after reboot, to ensure no error in sudo dpkg -i &#8211;force-all ibm-lotus-notes-8.5.2.i586.deb.

```
~/temp$ sudo dpkg -i &#8211;force-all ibm-lotus-notes-8.5.2.i586.deb
dpkg: error processing &#8211;force-all (--install):
 cannot access archive: No such file or directory
(Reading database ... 218648 files and directories currently installed.)
Preparing to replace ibm-lotus-notes:i386 8.5.2-20100811.1131 (using ibm-lotus-notes-8.5.2.i586.deb) ...
cat: /opt/ibm/lotus/notes/framework/rcp/rcplauncher.properties: No such file or directory
Unpacking replacement ibm-lotus-notes:i386 ...

Setting up ibm-lotus-notes:i386 (8.5.2-20100811.1131) ...
mv: cannot stat `/opt/ibm/lotus/notes/framework/rcp/rcplauncher.old': No such file or directory
mv: cannot stat `/opt/ibm/lotus/notes/framework/rcp/rcplauncher.properties.old': No such file or directory
mv: cannot stat `/opt/ibm/lotus/notes/framework/rcp/deploy/install.xml.old': No such file or directory
cat: /opt/ibm/lotus/notes/framework/rcp/deploy/install.xml: No such file or directory
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Errors were encountered while processing:

```

---

### Post by linctus on 2011-10-31
Hi there,

I followed the steps exactly what lads done except that:
1) I have to change permission of libnotesgtkfix.so and notes-wrapper to -rwxr-xr-x. (sorry I'm not familiar with the numerical code)
2) My package is not the newer 8.5.2 or 8.5.3, just 8.5 and seems it was released in 2008, quite a bit old.
3) I didn't need to modify the .deb archive (actually because I don't know how to) and seems it's just fine. 

btw, my configuration is:
Thankpad T420 i5-2520, Ubuntu 11.10 64 bit, Gnome-shell.

for the output message in lads's last post, seems that it's the problem of libgdk-pixbuf. So I'm thinking that maybe libnotesgtkfix.so doesn't work in lads's case. you sure libnotesgtkfix.so and notes-wrapper is -rwxr-xr-x?

And now my own problems:
First, I can't make input method work in notes for me. Ctrl+Space doesn't evoke the input method. I use ibus + ibus-pinyin + ibus-anthy. Seems that Niise is using some kind of input method for traditional Chinese. So could you please give me a hand on this issue?
The second, when I am offline, I can't open a local application (.nsf) stored in my laptop's hard disk. That's a replication of my mails and I don't understand why it require to connect to the Domino server. I have no such a problem in notes in windows, or in wine + notes in Ubuntu. I know maybe it's not a Linux-related problem but it will be appreciated if any advice is available.

Thanks in advance.

---

### Post by gdesanti on 2011-10-31
Hi everyboy,

I just installed Lotus Notes 8.5.3 on my Kubuntu 11.10 32 bits installation and the installer works fine, the problem is that when I run Lotus for the first time, it ask me for the license agreement and when I accepted, just nothing happens, no error windows or messages at all, anything happens, just doesn't continue with the setup process.

Any Ideas?

Thank you

---

### Post by linctus on 2011-10-31
Hi gdesanti,

Maybe you can check out if any library is missed as Niise mentioned in post #14.

---

### Post by linctus on 2011-10-31
OK, I got a new problem. When I open a mail, the content isn't displayed at all. Some gdk or gtk library problem I think, but have no idea how to solve.
[IMG]http://www2.6sq.net/data/attachment/album/201111/01/100014btodlyjh4qykfjtj.png[/IMG]

---

### Post by Niise on 2011-10-31
> **ondrokm said:**
> The instruction from Niise didn't work for me :(
I finally get Lotus notes 8.5.3 working using wine:
[LIST]
[*]Install Lotus notes on windows machine (e.g. C:/Program Files/Lotus Notes)
[*]Copy the folder with files (C:/Program Files/Lotus Notes) to your linux pc
[*]Do not try to use your Data directory from previous linux version of Lotus notes, it would cause problems
[*]Edit Lotus Notes/notes.ini (e.g. ~/.wine/drive_c/Program Files/Lotus Notes/notes.ini) and after the "[Notes]" put the line: "UseBasicNotus=1" - now it will be the second line. Found here: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=23604](http://appdb.winehq.org/objectManager.php?sClass=version&iId=23604)
[*]Run Lotus notes ($ wine notes.exe)
[/LIST]

I don't like using wine but it's working :(

hi, if you use wine, i remember onething need to do. The oleacc.dll should be replace to windows original one, otherwise you may not modify the preference.

---

### Post by gdesanti on 2011-11-01
> **linctus said:**
> Hi gdesanti,

Maybe you can check out if any library is missed as Niise mentioned in post #14.

Thank you linctus

Yes some missing libraries, problem was solved, and now I have lotus and sametime running, but, now the problem is that I can't see the mails, specifically internal mails, external mails don't have problems.  When I try to open a company mail, it open a gray screen, the same thing with lotus notes applications.

I think it's the same problem reported by Linctus

Any Idea?

Thanks in advance for your help

---

### Post by Niise on 2011-11-02
> **gdesanti said:**
> Thank you linctus

Yes some missing libraries, problem was solved, and now I have lotus and sametime running, but, now the problem is that I can't see the mails, specifically internal mails, external mails don't have problems.  When I try to open a company mail, it open a gray screen, the same thing with lotus notes applications.

I think it's the same problem reported by Linctus

Any Idea?

Thanks in advance for your help


I dont have this issue. what lotus server version in your company? Our server version should be 7.0.x. because your problem only occur in internal mail, i think it should be setting of policy (imo, you should check windows 8.5.3 version in your comapny).

---

### Post by lads on 2011-11-03
Hello everyone,

Below goes the output of LD_LIBRARY_PATH, as Niise requested. The only .so that is not coming from either */usr/lib32* or */opt/ibm/lotus* is *libtasn1.so.3*, coming from */usr/lib/i386-linux-gnu*. Could this be the cause of my problems? How can I change it?

Also, I verified that the permissions to *libnotesgtkfix.so* are set as linctus indicated.

Thanks.

```

$ LD_LIBRARY_PATH=/opt/ibm/lotus/notes/:/usr/lib32/:/usr/lib32/i386-linux-gnu/ LANGUAGE=zh_TW.UTF-8 ldd /opt/ibm/lotus/notes/framework/../lnotes/lib32/ilinux-gate.so.1 =>  (0xf77bc000)F-8 ldd /opt/ibm/lotus/notes/framework/.	libnotes.so => /opt/ibm/lotus/notes/libnotes.so (0xf5508000)
	libXt.so.6 => /usr/lib32/libXt.so.6 (0xf54ac000)
	libX11.so.6 => /usr/lib32/libX11.so.6 (0xf5375000)
	libdl.so.2 => /lib32/libdl.so.2 (0xf534c000)
	libemulator.so => /opt/ibm/lotus/notes/libemulator.so (0xf518f000)
	libpthread.so.0 => /lib32/libpthread.so.0 (0xf5174000)
	libresolv.so.2 => /lib32/libresolv.so.2 (0xf515d000)
	libdxlo.so => /opt/ibm/lotus/notes/libdxlo.so (0xf50c5000)
	libxpm.so => /opt/ibm/lotus/notes/libxpm.so (0xf50bf000)
	libxmlproc.so => /opt/ibm/lotus/notes/libxmlproc.so (0xf4cbf000)
	libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf4bd4000)
	libm.so.6 => /lib32/libm.so.6 (0xf4baa000)
	libc.so.6 => /lib32/libc.so.6 (0xf4a30000)
	libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf4a11000)
	libndgts.so => /opt/ibm/lotus/notes/libndgts.so (0xf4a0f000)
	libglib-2.0.so.0 => /lib32/libglib-2.0.so.0 (0xf4916000)
	libxmlcommon.so => /opt/ibm/lotus/notes/libxmlcommon.so (0xf48f7000)
	librt.so.1 => /lib32/librt.so.1 (0xf48ee000)
	libSM.so.6 => /usr/lib32/libSM.so.6 (0xf48e4000)
	libICE.so.6 => /usr/lib32/libICE.so.6 (0xf48ca000)
	libxcb.so.1 => /usr/lib32/libxcb.so.1 (0xf48ab000)
	/lib/ld-linux.so.2 (0xf77bd000)
	libgtk-x11-2.0.so.0 => /opt/ibm/lotus/notes/libgtk-x11-2.0.so.0 (0xf444b000)
	libgdk-x11-2.0.so.0 => /opt/ibm/lotus/notes/libgdk-x11-2.0.so.0 (0xf43a4000)
	libgdk_pixbuf-2.0.so.0 => /opt/ibm/lotus/notes/libgdk_pixbuf-2.0.so.0 (0xf4386000)
	libpango-1.0.so.0 => /usr/lib32/libpango-1.0.so.0 (0xf433d000)
	libpangoxft-1.0.so.0 => /usr/lib32/libpangoxft-1.0.so.0 (0xf4334000)
	libpangoft2-1.0.so.0 => /usr/lib32/libpangoft2-1.0.so.0 (0xf4307000)
	libgobject-2.0.so.0 => /usr/lib32/libgobject-2.0.so.0 (0xf42b8000)
	libgnomeprint-2-2.so.0 => /usr/lib32/libgnomeprint-2-2.so.0 (0xf4243000)
	libgnomeprintui-2-2.so.0 => /usr/lib32/libgnomeprintui-2-2.so.0 (0xf41fe000)
	libgthread-2.0.so.0 => /usr/lib32/libgthread-2.0.so.0 (0xf41f8000)
	libgnomevfs-2.so.0 => /usr/lib32/libgnomevfs-2.so.0 (0xf418f000)
	libgnome-2.so.0 => /usr/lib32/libgnome-2.so.0 (0xf417b000)
	libfreetype.so.6 => /usr/lib32/libfreetype.so.6 (0xf40e3000)
	libfontconfig.so.1 => /usr/lib32/libfontconfig.so.1 (0xf40ae000)
	libgconf-2.so.4 => /usr/lib32/libgconf-2.so.4 (0xf4080000)
	libcups.so.2 => /usr/lib32/libcups.so.2 (0xf402e000)
	libXcursor.so.1 => /usr/lib32/libXcursor.so.1 (0xf4023000)
	libgnomeui-2.so.0 => /usr/lib32/libgnomeui-2.so.0 (0xf3f8a000)
	libxml2.so.2 => /usr/lib32/libxml2.so.2 (0xf3e3d000)
	libpcre.so.3 => /lib32/libpcre.so.3 (0xf3dfe000)
	libuuid.so.1 => /lib32/libuuid.so.1 (0xf3df8000)
	libXau.so.6 => /usr/lib32/libXau.so.6 (0xf3df3000)
	libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf3dec000)
	libXext.so.6 => /usr/lib32/libXext.so.6 (0xf3dd9000)
	libXrender.so.1 => /usr/lib32/libXrender.so.1 (0xf3dce000)
	libXinerama.so.1 => /usr/lib32/libXinerama.so.1 (0xf3dca000)
	libXi.so.6 => /usr/lib32/libXi.so.6 (0xf3db9000)
	libXrandr.so.2 => /usr/lib32/libXrandr.so.2 (0xf3db0000)
	libpangocairo-1.0.so.0 => /usr/lib32/libpangocairo-1.0.so.0 (0xf3da3000)
	libXcomposite.so.1 => /usr/lib32/libXcomposite.so.1 (0xf3d9f000)
	libXdamage.so.1 => /usr/lib32/libXdamage.so.1 (0xf3d9b000)
	libXfixes.so.3 => /usr/lib32/libXfixes.so.3 (0xf3d94000)
	libatk-1.0.so.0 => /usr/lib32/libatk-1.0.so.0 (0xf3d74000)
	libcairo.so.2 => /usr/lib32/libcairo.so.2 (0xf3ca9000)
	libgio-2.0.so.0 => /usr/lib32/libgio-2.0.so.0 (0xf3b63000)
	libz.so.1 => /usr/lib32/libz.so.1 (0xf3b4e000)
	libgmodule-2.0.so.0 => /usr/lib32/libgmodule-2.0.so.0 (0xf3b48000)
	libXft.so.2 => /usr/lib32/libXft.so.2 (0xf3b32000)
	libffi.so.6 => /usr/lib32/libffi.so.6 (0xf3b2b000)
	libart_lgpl_2.so.2 => /usr/lib32/libart_lgpl_2.so.2 (0xf3b14000)
	libgnomecanvas-2.so.0 => /usr/lib32/libgnomecanvas-2.so.0 (0xf3add000)
	libdbus-glib-1.so.2 => /usr/lib32/libdbus-glib-1.so.2 (0xf3ab8000)
	libdbus-1.so.3 => /lib32/libdbus-1.so.3 (0xf3a6f000)
	libgnutls.so.26 => /usr/lib32/libgnutls.so.26 (0xf39bf000)
	libavahi-glib.so.1 => /usr/lib32/libavahi-glib.so.1 (0xf39bb000)
	libavahi-common.so.3 => /usr/lib32/libavahi-common.so.3 (0xf39ac000)
	libavahi-client.so.3 => /usr/lib32/libavahi-client.so.3 (0xf3999000)
	libutil.so.1 => /lib32/libutil.so.1 (0xf3995000)
	libbonobo-2.so.0 => /usr/lib32/libbonobo-2.so.0 (0xf393a000)
	libbonobo-activation.so.4 => /usr/lib32/libbonobo-activation.so.4 (0xf3925000)
	libORBit-2.so.0 => /usr/lib32/libORBit-2.so.0 (0xf38c9000)
	libcanberra.so.0 => /usr/lib32/libcanberra.so.0 (0xf38b8000)
	libpopt.so.0 => /lib32/libpopt.so.0 (0xf38ac000)
	libexpat.so.1 => /lib32/libexpat.so.1 (0xf3882000)
	libgssapi_krb5.so.2 => /usr/lib32/libgssapi_krb5.so.2 (0xf3844000)
	libbonoboui-2.so.0 => /usr/lib32/libbonoboui-2.so.0 (0xf37e8000)
	libgnome-keyring.so.0 => /usr/lib32/libgnome-keyring.so.0 (0xf37c6000)
	libpixman-1.so.0 => /usr/lib32/libpixman-1.so.0 (0xf3743000)
	libpng12.so.0 => /usr/lib32/libpng12.so.0 (0xf3719000)
	libxcb-shm.so.0 => /usr/lib32/libxcb-shm.so.0 (0xf3714000)
	libxcb-render.so.0 => /usr/lib32/libxcb-render.so.0 (0xf370a000)
	libselinux.so.1 => /lib32/libselinux.so.1 (0xf36ec000)
	libgailutil.so.18 => /usr/lib32/libgailutil.so.18 (0xf36e4000)
	libtasn1.so.3 => /usr/lib/i386-linux-gnu/libtasn1.so.3 (0xf36d2000)
	libgcrypt.so.11 => /lib32/libgcrypt.so.11 (0xf364c000)
	libORBitCosNaming-2.so.0 => /usr/lib32/libORBitCosNaming-2.so.0 (0xf3646000)
	libvorbisfile.so.3 => /usr/lib32/libvorbisfile.so.3 (0xf363c000)
	libtdb.so.1 => /usr/lib32/libtdb.so.1 (0xf3629000)
	libltdl.so.7 => /usr/lib32/libltdl.so.7 (0xf361f000)
	libkrb5.so.3 => /usr/lib32/libkrb5.so.3 (0xf3555000)
	libk5crypto.so.3 => /usr/lib32/libk5crypto.so.3 (0xf352c000)
	libcom_err.so.2 => /lib32/libcom_err.so.2 (0xf3528000)
	libkrb5support.so.0 => /usr/lib32/libkrb5support.so.0 (0xf351f000)
	libgpg-error.so.0 => /lib32/libgpg-error.so.0 (0xf3519000)
	libvorbis.so.0 => /usr/lib32/libvorbis.so.0 (0xf34ee000)
	libogg.so.0 => /usr/lib32/libogg.so.0 (0xf34e6000)
	libkeyutils.so.1 => /lib32/libkeyutils.so.1 (0xf34e2000)

```

---

### Post by Niise on 2011-11-03
Hi Lads
/usr/lib/i386-linux-gnu is fine, according to it's name, it should be i386 arch too.

I care about your another error message when you run notes-wrapper, maybe like as 

```
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64
```
try
```
$ sudo apt-file search libappmenu.so
appmenu-gtk: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so
appmenu-gtk3: /usr/lib/gtk-3.0/3.0.0/menuproxies/libappmenu.so
indicator-appmenu: /usr/lib/indicators3/6/libappmenu.so
indicator-appmenu-gtk2: /usr/lib/indicators/6/libappmenu.so

```
in this case you should choose appmenu-gtk, because it fit the fullpath.
```
$ getlibs -p appmenu-gtk

```

This message should come from some binary invoke by lnotes that dynamically load other libraries, so you cant trace it from "ldd lnote"
This step maybe need do a lot times, recursive it until you dont see any[COLOR="Red"] wrong ELF class: ELFCLASS64[/COLOR]

---

### Post by lads on 2011-11-03
Hi Niise,

I tried your last suggestion, but for *libcanberra-gtk-module.so* and *libmurrine.so* there was no effect.

Niise I appreciate very much your efforts to help me, but I'm reaching a point where I really don't know what I'm doing and using plenty of time in the process. I'll just stick to Winblows for the time being.

Best.

---

### Post by gdesanti on 2011-11-03
> **Niise said:**
> I dont have this issue. what lotus server version in your company? Our server version should be 7.0.x. because your problem only occur in internal mail, i think it should be setting of policy (imo, you should check windows 8.5.3 version in your comapny).

We have 8.5.x domino server version. 

My Linux is a 32 bits installation, but, at this point I think I I have the same problem reported by linctus.  

Thank you for your help

---

### Post by linctus on 2011-11-05
Hi guys,

So sad to know that your problems are not solved, mine, neither. 
I just wine it and it works fine here, and faster than the linux native.
Any way, I'll keep on finding a workaround.

Good luck.

---

### Post by linctus on 2011-11-29
Hi there,

from [here]("http://www-10.lotus.com/ldd/dominowiki.nsf/dx/Notes_8.5.3_on_Ubuntu_11.10") I think it doesn't work on 11.10 64bit yet. I transfer to 11.10 32bit with PAE kernel (I want to use my 6g memory) and it works. There's still a little bit flaw, but it works.

for your reference.

---

### Post by Niise on 2011-12-09
I must say that this combination work fine on my desktop.

---

