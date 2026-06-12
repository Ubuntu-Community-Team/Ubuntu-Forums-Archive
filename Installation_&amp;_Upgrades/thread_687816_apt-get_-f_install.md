---
title: "apt-get -f install"
date: 2008-02-04
forum: Installation &amp; Upgrades
---

### Post by reZo on 2008-02-04
Today I was attempting to install global-menu on my Ubuntu Gusty machine. However, Since it's Gusty, it looks like it has newer packages then are required for global-menu.

Without realizing this, I attempted to `dpkg -install *.deb` in which, * represents all deb's from the tar.gz for global-menu.

This displayed errors of cause, and didn't install the packages. Now, whenever I use apt, it asks me to "-f install", fix my installation. The problem is with this, when I'm fixing the installation, packages are being removed.

```
# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  gnome-accessibility-themes gnome-themes gnome-themes-extras gtk2-engines-pixbuf gtk2.0-examples gucharmap libgtk-directfb-2.0-0 libgtk-directfb-2.0-dev
  libgtk2.0-0-dbg libgtk2.0-bin ubuntu-desktop
0 upgraded, 0 newly installed, 11 to remove and 0 not upgraded.
6 not fully installed or removed.
Need to get 0B of archives.
After unpacking 48.7MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

```

And of cause, I don't want to remove ubuntu-desktop and such, I want my themes / setup left as is.

How can I remove the need to apt-get -f install without doing it?

```
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  gnome-themes: Depends: gtk2-engines-pixbuf but it is not going to be installed
  gnome-themes-extras: Depends: gtk2-engines-pixbuf but it is not going to be installed
  gtk2.0-examples: Depends: libgtk2.0-0 (= 2.12.0-1ubuntu3.1) but 2.12.0-1ubuntu3 is to be installed
  libgtk-directfb-2.0-0: Depends: libgtk2.0-0 (= 2.12.0-1ubuntu3.1) but 2.12.0-1ubuntu3 is to be installed
  libgtk-directfb-2.0-dev: Depends: libgtk2.0-dev (= 2.12.0-1ubuntu3.1) but 2.12.0-1ubuntu3 is to be installed
  libgtk2.0-0-dbg: Depends: libgtk2.0-0 (= 2.12.0-1ubuntu3.1) but 2.12.0-1ubuntu3 is to be installed
  libgtk2.0-bin: Depends: libgtk2.0-0 (>= 2.12.0-1ubuntu3.1) but 2.12.0-1ubuntu3 is to be installed
  ubuntu-desktop: Depends: gtk2-engines-pixbuf but it is not going to be installed
                  Recommends: ekiga but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

Hopefully you understand what I'm trying to say, I have a weakness for not being able to explain things very well.

If you need any more information to help resolve my problem, I'm happy to give it.

Thanks in advanced!

**Links**

[https://wiki.ubuntu.com/global_menu](https://wiki.ubuntu.com/global_menu)

The deb's are in the following archives (which I attempted to install):

[http://gnome2-globalmenu.googlecode.com/files/patched-gtk-ubuntu-gutsy-i386-part1.tar.gz](http://gnome2-globalmenu.googlecode.com/files/patched-gtk-ubuntu-gutsy-i386-part1.tar.gz) [http://gnome2-globalmenu.googlecode.com/files/globalmenu-applet-v3.172.tar.bz2](http://gnome2-globalmenu.googlecode.com/files/globalmenu-applet-v3.172.tar.bz2)

---

