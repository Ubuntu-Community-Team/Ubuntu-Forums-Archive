---
title: "uninstalling and upgrading glib"
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by Diabolis on 2007-05-28
I tried to install **bit torrent** but I failed becaused I needed to install **wxwidgets** first. When  I tried to install wxwidgets, it showed this error:

[COLOR="DarkSlateGray"]checking for GTK+ - version >= 2.0.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
configure: error:
The development files for GTK+ were not found. For GTK+ 2, please
ensure that pkg-config is in the path and that gtk+-2.0.pc is
installed. For GTK+ 1.2 please check that gtk-config is in the path,
and that the version is 1.2.3 or above. Also check that the
libraries returned by 'pkg-config gtk+-2.0 --libs' or 'gtk-config
--libs' are in the LD_LIBRARY_PATH or equivalent.[/COLOR]

then I tried to install **GTK+**, it needed **glib** so I downloaded a recent version and installed it and now I got this error:

[COLOR="DarkSlateGray"]checking for GLIB - version >= 2.12.0...
*** 'pkg-config --modversion glib-2.0' returned 2.13.2, but GLIB (2.10.3)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** GLIB 2.12.0 or better is required. The latest version of
*** GLIB is always available from [ftp://ftp.gtk.org/pub/gtk/](ftp://ftp.gtk.org/pub/gtk/).[/COLOR]

I know what the error means, but not how to fix it because I don know anything about enviroment variables or the place where this packages are installed.

I tried to fix it by downloading the old version of glib (2.10.3) and doing the following in the terminal:
[COLOR="DarkSlateGray"]extract files from glib 2.10.3 (the one I downloaded)
cd to the glib 2.10.3 directory
./configure
make
make uninstall[/COLOR]

everything ran smootheley but when I tried to install GTK again, I got the same error I posted above.

I have read that some other torrent clients are easier to install but the thing is that I like bit  torrent.

---

### Post by yabbadabbadont on 2007-05-28
Run System->Administration->Synaptic Package Manager and then use the search button to search for torrent.  You will find several differnt clients already available for easy installation in the repositories.

---

### Post by Diabolis on 2007-05-28
I tried that before and the description of the package contains the following:

[COLOR="DarkSlateGray"]This package contains the tools which are used for console-only
downloading.  If you want the GUI interface, install the
bittorrent-gui package.

 Homepage: [http://bitconjurer.org/BitTorrent/](http://bitconjurer.org/BitTorrent/)[/COLOR]

I downloaded the bittorrent-gui from the bit torrent site and thats what I've been trying to install for so long, but thanks for the interest.

---

### Post by yabbadabbadont on 2007-05-28
The gui version of bittorrent is installed by default with the standard Gnome Ubuntu desktop.  There just isn't a menu entry for it.  However, it is already associated with torrent files and will launch any time you click on one.

---

### Post by Diabolis on 2007-05-28
I opened Synaptic and installed bittorrent, I tried to download a torrent file by just clicking on it and it didn't work, but then I checked Synaptic again and below the bittorrent there was a package called **gnome-btdownload**. I installed this package and after that I was able to run and download my torrent file :p. thankyou for your help.

the only thing is that all I got as a GUI is a small window that shows the download process, but not any preferences or settings menu. I wonder if I can install the same GUI that bit torrent uses in windows. And I still have the **double glib** installation problem, that I would like to fix.

---

### Post by Diabolis on 2007-05-31
Recently I tried to remove the old version of glib through synaptic, but that messed my whole system and I had to reinstall ubuntu. Is not that bad, because I had a back up of my files in my usb. So, _how do I upgrade glib????_

---

### Post by midtown on 2007-07-04
I would also appreciate an answer to this, as I am having the same error while trying to do something as well. This thread comes up high on google searching for upgrading glib so it would probably be useful for other users as well :p.

---

### Post by foxmuldr on 2007-07-10
> **midtown said:**
> I would also appreciate an answer to this, as I am having the same error while trying to do something as well. This thread comes up high on google searching for upgrading glib so it would probably be useful for other users as well :p.

I am having the same problem when trying to install GTK+-2.10.13:

-----[ Begin message ]-----
checking for GLIB - version >= 2.12.0... 
*** 'pkg-config --modversion glib-2.0' returned 2.13.6, but GLIB (2.12.11)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** GLIB 2.12.0 or better is required. The latest version of
*** GLIB is always available from [ftp://ftp.gtk.org/pub/gtk/](ftp://ftp.gtk.org/pub/gtk/).
-----[ End message ]-----

I've tried installing glib-2.13.6.  It seemed to work.  Now this.  Where is 2.12.11 installed?  How can I update it to 2.13.6?  Or how can I downgrade 2.13.6 to 2.12.11?  This seems like it's a fairly large error.  I haven't been able to find a FAQ anywhere.

Any help is appreciated.

---

### Post by Diabolis on 2007-07-10
The message is already telling you what to do, change your path by adding the new glib installation. You have to add it in this order:

path = new glib + path

because the system will recognize only the first ocurrence of glib in the path.

Probably after that you can uninstall the old glib without trouble through synaptic.

---

### Post by rcatman on 2007-08-02
Did you ever get the error message to go away? Its weird. I've been trying to install the latest release of gimp and I get the same message.

---

