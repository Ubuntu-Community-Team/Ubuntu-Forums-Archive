---
title: "Questions about installing and changiing the desktop environment"
date: 2013-04-06
forum: Installation &amp; Upgrades
---

### Post by rxlord on 2013-04-06
Q1. Hey everybody whenever i install any flavour of ubuntu it downloads some language packs etc.I have a slow internet and i usually have problem with ubuntu and at a point i have to re-install it.So is there any way through which i can make backup of these language packs etc so that if i have to reinstall ubuntu then i dont have to download the language packs again and again and the installer can use these backups of language packs etc instead of downloading them again.

Q2. Its my second ques.. as the prefix says im using lubuntu right now and i want to install xubuntu in it.I want to change every drop of it to xubuntu without downloading xubuntu iso and installing it over my current installation.I tried it once from other tutorial but in it loading screen did'nt changed and wifi tab didnt showed any wifi networks available for connection.I also wanna know if i choose xubuntu desktop in tasksel then will it change every drop of lubuntu to xubuntu

Q3.How can i make a reset drive or anything like it so that if i run into a serious problem (eg:-lubuntu not booting) then i could revert it back so that i dont have to reinstall the os again.

Q4. IS there any ubuntu website from where i could download ubuntu-desktop etc. packages on my windows pc because i cant run my lubuntu pc for long time and i ave a slow connection

Sorry for spelling or language mistakes if any.:D

---

### Post by rxlord on 2013-04-07
no answers for any question?

---

### Post by ibjsb4 on 2013-04-07
Q2:

Install xubuntu

```
sudo apt-get install xubuntu-desktop
```

To remove lubuntu

[http://www.psychocats.net/ubuntu/purexubuntu](http://www.psychocats.net/ubuntu/purexubuntu)

This requires internet

Will it change every drop?  It should, but I do no pass out guaranties

---

### Post by ibjsb4 on 2013-04-07
Q4:

[https://help.ubuntu.com/community/InstallingSoftware#Installing_packages_without_an_Internet_connection](https://help.ubuntu.com/community/InstallingSoftware#Installing_packages_without_an_Internet_connection)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=offline+package+installer&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=offline+package+installer&sa=Search&cof=FORID:9)

---

### Post by MAFoElffen on 2013-04-07
> **ibjsb4 said:**
> Q2:

Install xubuntu

```
sudo apt-get install xubuntu-desktop
```

To remove lubuntu

[http://www.psychocats.net/ubuntu/purexubuntu](http://www.psychocats.net/ubuntu/purexubuntu)

This requires internet

[COLOR=#ff0000]Will it change every drop?  It should, but I do no pass out guaranties[/COLOR]
Note: If you have an Ubuntu core installed, you can install any desktop package on it via the software center, synaptics... or just via apt-get to install: ubuntu-desktop, xubuntu-desktop, lubuntu-desktop, kubuntu-desktop, edubuntu-desktop, mythbuntu-desktop, etc... even gnome-shell.

All these will install and you can select what flavor to bring up from the LightDM login.

Pro's- You can install and run different flavors without having to reinstall a whole core foundation and still keep all your settings and data. You can mix and match to use what you want in the DE you prefer.

Con's- Look what I hightlighted in red, because that is incorrect. It will install the new app's from that desktop environment while retaining all the app's from previous desktop environments, resulting in app's from all installed distro's showing up in the menu's to all desktops. It does not remove the app's or DE (unless you remove them manually). This is okay as long as you understand that. Also, some KDE app's do not run right in other DE's... Lubuntu app's may not run as fast in a heavy install base or other DE. So a drawback to this method is that unless you know which app's go with which flavors, a new user doesn't get a clear picture of the pure flavor, what works together as optimally tuned to, in that distro flavor.

There is trade off's.

On the other hand, if you want to just test drive distro's... why not install Ubuntu (or any other flavor) and then install "Testdrive an Ubuntu ISO" which will install Virtualbox, with a scripted App to DL the Branch LiveCD you want to try out in VirtualBox...

---

### Post by ibjsb4 on 2013-04-07
> Con's- Look what I hightlighted in red, because that is incorrect. It will install the new app's from that desktop environment while retaining all the app's from previous desktop environments, resulting in app's from all installed distro's showing up in the menu's to all desktops.
You only highlighted the last line in red which is not a command and will not install anything :confused:  It will not result in app's from all distros being installed.  Unless you mean the "install xubuntu-desktop" command (not in red) which installs only xubuntu-desktop and not **all** distro's. If left at that then you would have a mix of xubuntu and lubuntu, but it does not stop there.

> It does not remove the app's or DE (unless you remove them manually).

That is what the link is all about.  [http://www.psychocats.net/ubuntu/purexubuntu](http://www.psychocats.net/ubuntu/purexubuntu)
Manually removing lubuntu.

> Also, some KDE app's do not run right in other DE's

KDE?  Not even a topic.  

> Lubuntu app's may not run as fast in a heavy install base or other DE.

Lubuntu is being removed

> So a drawback to this method is that unless you know which app's go with which flavors, a new user doesn't get a clear picture of the pure flavor

Again, the psychocats link removes **L**ubuntu

---

### Post by MAFoElffen on 2013-04-08
> **ibjsb4 said:**
> You only highlighted the last line in red which is not a command and will not install anything :confused:  It will not result in app's from all distros being installed.  Unless you mean the "install xubuntu-desktop" command (not in red) which installs only xubuntu-desktop and not **all** distro's. If left at that then you would have a mix of xubuntu and lubuntu, but it does not stop there.

Here's were you seem to be confused...
Lubuntu:
- Lubuntu uses lxde as the base desktop environment. The package for just that is "lxde".
- The Lubuntu core package, including all *it's* distro relevant applications above the base Ubuntu core is the meta-package named "lubuntu-desktop"

Xubuntu:
- Xubuntu uses 2 base DE's for the user to decide on, gnome-shell and "Xfce" 
- The Xubuntu core package that installs on the Ubuntu core, that includes it's desktop environment and all *it's* applications is the meta-package named "xubuntu-desktop"

So... if you wanted to install just a different top graphical layered Xubuntu desktop environment without all it's own applications being installed, you instead would install just the desktop environment- gnome-shell and/or xfce... and to remove the Lubuntu's desktop environment, you would remove lxde.

The package names do seem to confuse some people, The "...-desktop" in the meta-package names denotes the Desktop Edition, not meaning a desktop environment as you assumed. There are major differences in what those (Desktop Edition) really are... compared to what I now know what you are referring to (desktop environment)... right? Yes, referring to those other packages instead (lxde, xfce and gnome-shell), they are also interchangeable... without affecting *many* other app's. Note that some are tied to the DE, such as for example, some of the gnome specific app's and applets are removed if you remove that gnome-shell package.

I'm not really trying to step on anyone's toes... just trying to clear up any confusion. I'm here to help and share experience.

---

### Post by ibjsb4 on 2013-04-08
No confusion here, the op wants to remove lubuntu and install xubuntu.  No mention of confusion about lxde and xfce, actually no mention at all by the op.  Post #3 works; have you ever tried it?  I have :)

---

### Post by MAFoElffen on 2013-04-08
Yes I have. Both methods... Here is what "sudo apt-get install xubuntu-desktop" would install on an Ubuntu install, which the one already has gnome shell installed, not included the other other full blown utils... So on Lubuntu, it would install more packages:
```

The following extra packages will be installed:
   abiword (2.9.2+svn20120603-8)
   abiword-common (2.9.2+svn20120603-8)
   abiword-plugin-grammar (2.9.2+svn20120603-8)
   abiword-plugin-mathview (2.9.2+svn20120603-8)
   bison (2.5.dfsg-2.1build1)
   blueman (1.23-0ubuntu3)
   brltty-x11 (4.4-5ubuntu3)
   catfish (0.4.0.2-0ubuntu1)
   exo-utils (0.8.0-1)
   flex (2.5.35-10.1ubuntu1)
   fonts-lyx (2.0.3-3)
   gigolo (0.4.1-3)
   gmusicbrowser (1.1.9-2)
   gnome-time-admin (3.0.0-2ubuntu1)
   gstreamer0.10-gnomevfs (0.10.36-1ubuntu1.1)
   gthumb (3.0.2-0ubuntu2)
   gthumb-data (3.0.2-0ubuntu2)
   indicator-application-gtk2 (12.10.0.1-0ubuntu1)
   indicator-sound-gtk2 (12.10.0.1-0ubuntu1)
   leafpad (0.8.18.1-3)
   libabiword-2.9 (2.9.2+svn20120603-8)
   libbison-dev (2.5.dfsg-2.1build1)
   libdigest-crc-perl (0.18-1)
   libexo-1-0 (0.8.0-1)
   libexo-common (0.8.0-1)
   libexo-helpers (0.8.0-1)
   libfl-dev (2.5.35-10.1ubuntu1)
   libgarcon-1-0 (0.2.0-1)
   libgarcon-common (0.2.0-1)
   libgdome2-0 (0.8.1+debian-4.1build1)
   libgdome2-cpp-smart0c2a (0.2.6-6build2)
   libgsf-1-114 (1.14.24-0ubuntu1)
   libgsf-1-common (1.14.24-0ubuntu1)
   libgstreamer-perl (0.17-1)
   libgtk2-notify-perl (0.05-3build1)
   libgtk2-trayicon-perl (0.06-1build2)
   libgtkmathview0c2a (0.8.0-8)
   libido-0.1-0 (12.10.0.1-0ubuntu1)
   libintl-perl (1.20-1build2)
   libkeybinder0 (0.2.2-4)
   liblink-grammar4 (4.7.4-2)
   libloudmouth1-0 (1.4.3-8)
   libotr2 (3.2.1-1)
   libots0 (0.5.0-2.1)
   libtagc0 (1.8-0ubuntu2)
   libthunarx-2-0 (1.4.0-1ubuntu2.1)
   libtidy-0.99-0 (20091223cvs-1.2)
   libtumbler-1-0 (0.1.25-1ubuntu1)
   libunique-1.0-0 (1.1.6-4build1)
   libwv-1.2-4 (1.2.9-3)
   libxfce4ui-1-0 (4.10.0-1)
   libxfce4ui-utils (4.10.0-1)
   libxfce4util-bin (4.10.0-1)
   libxfce4util-common (4.10.0-1)
   libxfce4util6 (4.10.0-1)
   libxfcegui4-4 (4.10.0-1)
   libxfconf-0-2 (4.10.0-1)
   lightdm-gtk-greeter (1.3.1-0ubuntu1)
   link-grammar-dictionaries-en (4.7.4-2)
   m4 (1.4.16-3)
   orage (4.8.3-2)
   parole (0.3.0.3-0ubuntu1)
   pastebinit (1.3-2ubuntu3)
   pavucontrol (1.0-1)
   pidgin (2.10.6-0ubuntu2.2)
   pidgin-data (2.10.6-0ubuntu2.2)
   pidgin-libnotify (0.14-4ubuntu11)
   pidgin-microblog (0.3.0-3)
   pidgin-otr (3.2.1-3)
   plymouth-theme-xubuntu-logo (12.10.2)
   plymouth-theme-xubuntu-text (12.10.2)
   python-configobj (4.7.2+ds-4)
   ristretto (0.6.3-0ubuntu1)
   screensaver-default-images (0.2-1)
   shimmer-themes (1.5.3-0ubuntu1)
   thunar (1.4.0-1ubuntu2.1)
   thunar-archive-plugin (0.3.0-4)
   thunar-data (1.4.0-1ubuntu2.1)
   thunar-media-tags-plugin (0.2.0-1)
   thunar-volman (0.8.0-1)
   tumbler (0.1.25-1ubuntu1)
   tumbler-common (0.1.25-1ubuntu1)
   xbrlapi (4.4-5ubuntu3)
   xfburn (0.4.3-4ubuntu2)
   xfce-keyboard-shortcuts (4.10.0-1)
   xfce4-appfinder (4.10.0-1)
   xfce4-cpugraph-plugin (1.0.5-0ubuntu1)
   xfce4-dict (0.6.0-5build2)
   xfce4-indicator-plugin (0.5.0-1ubuntu2)
   xfce4-mailwatch-plugin (1.1.0-5build2)
   xfce4-netload-plugin (1.2.0-0ubuntu1)
   xfce4-notes (1.7.7-2ubuntu3)
   xfce4-notes-plugin (1.7.7-2ubuntu3)
   xfce4-notifyd (0.2.2-2ubuntu1)
   xfce4-panel (4.10.0-1ubuntu2)
   xfce4-places-plugin (1.3.0-1ubuntu1)
   xfce4-power-manager (1.2.0-1ubuntu1.1)
   xfce4-power-manager-data (1.2.0-1ubuntu1.1)
   xfce4-quicklauncher-plugin (1.9.4-9build2)
   xfce4-screenshooter (1.8.1-1)
   xfce4-session (4.10.0-1ubuntu1)
   xfce4-settings (4.10.0-1ubuntu2)
   xfce4-systemload-plugin (1.1.1-1ubuntu1)
   xfce4-taskmanager (1.0.0-2)
   xfce4-terminal (0.4.8-1ubuntu3)
   xfce4-verve-plugin (1.0.0-1build2)
   xfce4-volumed (0.1.13-2ubuntu1)
   xfce4-weather-plugin (0.8.1-0ubuntu1)
   xfce4-xkb-plugin (0.5.4.3-1ubuntu3)
   xfconf (4.10.0-1)
   xfdesktop4 (4.10.0-1ubuntu1.1)
   xfdesktop4-data (4.10.0-1ubuntu1.1)
   xfwm4 (4.10.0-2ubuntu1)
   xscreensaver (5.15-2ubuntu1)
   xubuntu-artwork (12.10.2)
   xubuntu-default-settings (12.10.7)
   xubuntu-docs (12.10.2)
   xubuntu-icon-theme (12.10.2)
   xubuntu-wallpapers (12.10.2)
Suggested packages:
   bison-doc (2.5-1)
   strigi-daemon (0.7.7-2ubuntu2)
   doodle (0.7.0-5)
   tracker (0.14.1-1ubuntu5)
   beagle ()
   libgnome2-wnck-perl (0.16-2build2)
   libgstreamer-interfaces-perl (0.06-2)
   libgtk2-mozembed-perl ()
   mpg321 (0.3.2-1.1)
   flac123 ()
   ogg123 ()
   vorbis-tools (1.4.0-1ubuntu3)
   evince-gtk (3.6.0-0ubuntu2)
   libintl-xs-perl (1.20-1build2)
   libotr2-bin (3.2.1-1)
   sox (14.4.0-3)
   shimmer-wallpapers (1.5.3-0ubuntu1)
   tumbler-plugins-extra (0.1.25-1ubuntu1)
   xfce4-power-manager-plugins (1.2.0-1ubuntu1.1)
   xfce4 (4.10.0)
   xfwm4-themes (4.10.0-1)
   xfishtank (2.2-26)
   xdaliclock (2.36+debian-1)
   fortune ()
   qcam ()
   streamer (3.102-3)
   gdm3 ()
   kdm-gdmcompat (0.13-2)
The following NEW packages will be installed:
   abiword (2.9.2+svn20120603-8)
   abiword-common (2.9.2+svn20120603-8)
   abiword-plugin-grammar (2.9.2+svn20120603-8)
   abiword-plugin-mathview (2.9.2+svn20120603-8)
   bison (2.5.dfsg-2.1build1)
   blueman (1.23-0ubuntu3)
   brltty-x11 (4.4-5ubuntu3)
   catfish (0.4.0.2-0ubuntu1)
   exo-utils (0.8.0-1)
   flex (2.5.35-10.1ubuntu1)
   fonts-lyx (2.0.3-3)
   gigolo (0.4.1-3)
   gmusicbrowser (1.1.9-2)
   gnome-time-admin (3.0.0-2ubuntu1)
   gstreamer0.10-gnomevfs (0.10.36-1ubuntu1.1)
   gthumb (3.0.2-0ubuntu2)
   gthumb-data (3.0.2-0ubuntu2)
   indicator-application-gtk2 (12.10.0.1-0ubuntu1)
   indicator-sound-gtk2 (12.10.0.1-0ubuntu1)
   leafpad (0.8.18.1-3)
   libabiword-2.9 (2.9.2+svn20120603-8)
   libbison-dev (2.5.dfsg-2.1build1)
   libdigest-crc-perl (0.18-1)
   libexo-1-0 (0.8.0-1)
   libexo-common (0.8.0-1)
   libexo-helpers (0.8.0-1)
   libfl-dev (2.5.35-10.1ubuntu1)
   libgarcon-1-0 (0.2.0-1)
   libgarcon-common (0.2.0-1)
   libgdome2-0 (0.8.1+debian-4.1build1)
   libgdome2-cpp-smart0c2a (0.2.6-6build2)
   libgsf-1-114 (1.14.24-0ubuntu1)
   libgsf-1-common (1.14.24-0ubuntu1)
   libgstreamer-perl (0.17-1)
   libgtk2-notify-perl (0.05-3build1)
   libgtk2-trayicon-perl (0.06-1build2)
   libgtkmathview0c2a (0.8.0-8)
   libido-0.1-0 (12.10.0.1-0ubuntu1)
   libintl-perl (1.20-1build2)
   libkeybinder0 (0.2.2-4)
   liblink-grammar4 (4.7.4-2)
   libloudmouth1-0 (1.4.3-8)
   libotr2 (3.2.1-1)
   libots0 (0.5.0-2.1)
   libtagc0 (1.8-0ubuntu2)
   libthunarx-2-0 (1.4.0-1ubuntu2.1)
   libtidy-0.99-0 (20091223cvs-1.2)
   libtumbler-1-0 (0.1.25-1ubuntu1)
   libunique-1.0-0 (1.1.6-4build1)
   libwv-1.2-4 (1.2.9-3)
   libxfce4ui-1-0 (4.10.0-1)
   libxfce4ui-utils (4.10.0-1)
   libxfce4util-bin (4.10.0-1)
   libxfce4util-common (4.10.0-1)
   libxfce4util6 (4.10.0-1)
   libxfcegui4-4 (4.10.0-1)
   libxfconf-0-2 (4.10.0-1)
   lightdm-gtk-greeter (1.3.1-0ubuntu1)
   link-grammar-dictionaries-en (4.7.4-2)
   m4 (1.4.16-3)
   orage (4.8.3-2)
   parole (0.3.0.3-0ubuntu1)
   pastebinit (1.3-2ubuntu3)
   pavucontrol (1.0-1)
   pidgin (2.10.6-0ubuntu2.2)
   pidgin-data (2.10.6-0ubuntu2.2)
   pidgin-libnotify (0.14-4ubuntu11)
   pidgin-microblog (0.3.0-3)
   pidgin-otr (3.2.1-3)
   plymouth-theme-xubuntu-logo (12.10.2)
   plymouth-theme-xubuntu-text (12.10.2)
   python-configobj (4.7.2+ds-4)
   ristretto (0.6.3-0ubuntu1)
   screensaver-default-images (0.2-1)
   shimmer-themes (1.5.3-0ubuntu1)
   thunar (1.4.0-1ubuntu2.1)
   thunar-archive-plugin (0.3.0-4)
   thunar-data (1.4.0-1ubuntu2.1)
   thunar-media-tags-plugin (0.2.0-1)
   thunar-volman (0.8.0-1)
   tumbler (0.1.25-1ubuntu1)
   tumbler-common (0.1.25-1ubuntu1)
   xbrlapi (4.4-5ubuntu3)
   xfburn (0.4.3-4ubuntu2)
   xfce-keyboard-shortcuts (4.10.0-1)
   xfce4-appfinder (4.10.0-1)
   xfce4-cpugraph-plugin (1.0.5-0ubuntu1)
   xfce4-dict (0.6.0-5build2)
   xfce4-indicator-plugin (0.5.0-1ubuntu2)
   xfce4-mailwatch-plugin (1.1.0-5build2)
   xfce4-netload-plugin (1.2.0-0ubuntu1)
   xfce4-notes (1.7.7-2ubuntu3)
   xfce4-notes-plugin (1.7.7-2ubuntu3)
   xfce4-notifyd (0.2.2-2ubuntu1)
   xfce4-panel (4.10.0-1ubuntu2)
   xfce4-places-plugin (1.3.0-1ubuntu1)
   xfce4-power-manager (1.2.0-1ubuntu1.1)
   xfce4-power-manager-data (1.2.0-1ubuntu1.1)
   xfce4-quicklauncher-plugin (1.9.4-9build2)
   xfce4-screenshooter (1.8.1-1)
   xfce4-session (4.10.0-1ubuntu1)
   xfce4-settings (4.10.0-1ubuntu2)
   xfce4-systemload-plugin (1.1.1-1ubuntu1)
   xfce4-taskmanager (1.0.0-2)
   xfce4-terminal (0.4.8-1ubuntu3)
   xfce4-verve-plugin (1.0.0-1build2)
   xfce4-volumed (0.1.13-2ubuntu1)
   xfce4-weather-plugin (0.8.1-0ubuntu1)
   xfce4-xkb-plugin (0.5.4.3-1ubuntu3)
   xfconf (4.10.0-1)
   xfdesktop4 (4.10.0-1ubuntu1.1)
   xfdesktop4-data (4.10.0-1ubuntu1.1)
   xfwm4 (4.10.0-2ubuntu1)
   xscreensaver (5.15-2ubuntu1)
   xubuntu-artwork (12.10.2)
   xubuntu-default-settings (12.10.7)
   xubuntu-desktop (2.162)
   xubuntu-docs (12.10.2)
   xubuntu-icon-theme (12.10.2)
   xubuntu-wallpapers (12.10.2)
0 upgraded, 120 newly installed, 0 to remove and 5 not upgraded.
Inst m4 (1.4.16-3 Ubuntu:12.10/quantal [amd64])
Inst libfl-dev (2.5.35-10.1ubuntu1 Ubuntu:12.10/quantal [amd64])
Inst flex (2.5.35-10.1ubuntu1 Ubuntu:12.10/quantal [amd64])
Inst libgsf-1-common (1.14.24-0ubuntu1 Ubuntu:12.10/quantal [all])
Inst libgsf-1-114 (1.14.24-0ubuntu1 Ubuntu:12.10/quantal [amd64])
Inst libwv-1.2-4 (1.2.9-3 Ubuntu:12.10/quantal [amd64])
Inst libabiword-2.9 (2.9.2+svn20120603-8 Ubuntu:12.10/quantal [amd64])
Inst libxfce4util-common (4.10.0-1 Ubuntu:12.10/quantal [all])
Inst libxfce4util6 (4.10.0-1 Ubuntu:12.10/quantal [amd64])
Inst xfconf (4.10.0-1 Ubuntu:12.10/quantal [amd64])
Inst libxfconf-0-2 (4.10.0-1 Ubuntu:12.10/quantal [amd64])
Inst xfce-keyboard-shortcuts (4.10.0-1 Ubuntu:12.10/quantal [all])
Inst libxfce4ui-1-0 (4.10.0-1 Ubuntu:12.10/quantal [amd64])
Inst libexo-common (0.8.0-1 Ubuntu:12.10/quantal [all])
Inst libexo-helpers (0.8.0-1 Ubuntu:12.10/quantal [amd64])
Inst libexo-1-0 (0.8.0-1 Ubuntu:12.10/quantal [amd64])
Inst libgarcon-common (0.2.0-1 Ubuntu:12.10/quantal [all])
Inst libgarcon-1-0 (0.2.0-1 Ubuntu:12.10/quantal [amd64])
Inst libido-0.1-0 (12.10.0.1-0ubuntu1 Ubuntu:12.10/quantal [amd64])
Inst libtagc0 (1.8-0ubuntu2 Ubuntu:12.10/quantal [amd64])
Inst thunar-data (1.4.0-1ubuntu2.1 Ubuntu:12.10/quantal-updates [all])
Inst libthunarx-2-0 (1.4.0-1ubuntu2.1 Ubuntu:12.10/quantal-updates [amd64])
Inst libtumbler-1-0 (0.1.25-1ubuntu1 Ubuntu:12.10/quantal [amd64])
Inst libxfcegui4-4 (4.10.0-1 Ubuntu:12.10/quantal [amd64])
Inst lightdm-gtk-greeter (1.3.1-0ubuntu1 Ubuntu:12.10/quantal [amd64])
Inst exo-utils (0.8.0-1 Ubuntu:12.10/quantal [amd64])
Inst xfce4-panel (4.10.0-1ubuntu2 Ubuntu:12.10/quantal [amd64])
Inst xfce4-settings (4.10.0-1ubuntu2 Ubuntu:12.10/quantal [amd64])
Inst xfce4-session (4.10.0-1ubuntu1 Ubuntu:12.10/quantal [amd64])
Inst shimmer-themes (1.5.3-0ubuntu1 Ubuntu:12.10/quantal [all])
Inst xubuntu-artwork (12.10.2 Ubuntu:12.10/quantal [all])
Inst xubuntu-default-settings (12.10.7 Ubuntu:12.10/quantal [all])
Inst libloudmouth1-0 (1.4.3-8 Ubuntu:12.10/quantal [amd64])
Inst libots0 (0.5.0-2.1 Ubuntu:12.10/quantal [amd64])
Inst libtidy-0.99-0 (20091223cvs-1.2 Ubuntu:12.10/quantal [amd64])
Inst abiword-common (2.9.2+svn20120603-8 Ubuntu:12.10/quantal [all])
Inst abiword (2.9.2+svn20120603-8 Ubuntu:12.10/quantal [amd64])
Inst link-grammar-dictionaries-en (4.7.4-2 Ubuntu:12.10/quantal [all])
Inst liblink-grammar4 (4.7.4-2 Ubuntu:12.10/quantal [amd64])
Inst abiword-plugin-grammar (2.9.2+svn20120603-8 Ubuntu:12.10/quantal [amd64])
Inst libgdome2-0 (0.8.1+debian-4.1build1 Ubuntu:12.10/quantal [amd64])
Inst libgdome2-cpp-smart0c2a (0.2.6-6build2 Ubuntu:12.10/quantal [amd64])
Inst libgtkmathview0c2a (0.8.0-8 Ubuntu:12.10/quantal [amd64])
Inst fonts-lyx (2.0.3-3 Ubuntu:12.10/quantal [all])
Inst abiword-plugin-mathview (2.9.2+svn20120603-8 Ubuntu:12.10/quantal [amd64])
Inst libbison-dev (1:2.5.dfsg-2.1build1 Ubuntu:12.10/quantal [amd64])
Inst bison (1:2.5.dfsg-2.1build1 Ubuntu:12.10/quantal [amd64])
Inst xfce4-notifyd (0.2.2-2ubuntu1 Ubuntu:12.10/quantal [amd64])
Inst blueman (1.23-0ubuntu3 Ubuntu:12.10/quantal [amd64])
Inst catfish (0.4.0.2-0ubuntu1 Ubuntu:12.10/quantal [all])
Inst gigolo (0.4.1-3 Ubuntu:12.10/quantal [amd64])
Inst libgstreamer-perl (0.17-1 Ubuntu:12.10/quantal [amd64])
Inst gmusicbrowser (1.1.9-2 Ubuntu:12.10/quantal [all])
Inst gnome-time-admin (3.0.0-2ubuntu1 Ubuntu:12.10/quantal [amd64])
Inst gstreamer0.10-gnomevfs (0.10.36-1ubuntu1.1 Ubuntu:12.10/quantal-updates [amd64])
Inst gthumb-data (3:3.0.2-0ubuntu2 Ubuntu:12.10/quantal [all])
Inst gthumb (3:3.0.2-0ubuntu2 Ubuntu:12.10/quantal [amd64])
Inst indicator-application-gtk2 (12.10.0.1-0ubuntu1 Ubuntu:12.10/quantal [amd64])
Inst leafpad (0.8.18.1-3 Ubuntu:12.10/quantal [amd64])
Inst libdigest-crc-perl (0.18-1 Ubuntu:12.10/quantal [amd64])
Inst libgtk2-notify-perl (0.05-3build1 Ubuntu:12.10/quantal [amd64])
Inst libgtk2-trayicon-perl (0.06-1build2 Ubuntu:12.10/quantal [amd64])
Inst libintl-perl (1.20-1build2 Ubuntu:12.10/quantal [all])
Inst libkeybinder0 (0.2.2-4 Ubuntu:12.10/quantal [amd64])
Inst libotr2 (3.2.1-1 Ubuntu:12.10/quantal [amd64])
Inst libunique-1.0-0 (1.1.6-4build1 Ubuntu:12.10/quantal [amd64])
Inst libxfce4ui-utils (4.10.0-1 Ubuntu:12.10/quantal [amd64])
Inst libxfce4util-bin (4.10.0-1 Ubuntu:12.10/quantal [amd64])
Inst orage (4.8.3-2 Ubuntu:12.10/quantal [amd64])
Inst parole (0.3.0.3-0ubuntu1 Ubuntu:12.10/quantal [amd64])
Inst python-configobj (4.7.2+ds-4 Ubuntu:12.10/quantal [all])
Inst pastebinit (1.3-2ubuntu3 Ubuntu:12.10/quantal [all])
Inst pavucontrol (1.0-1 Ubuntu:12.10/quantal [amd64])
Inst pidgin-data (1:2.10.6-0ubuntu2.2 Ubuntu:12.10/quantal-updates [all])
Inst pidgin (1:2.10.6-0ubuntu2.2 Ubuntu:12.10/quantal-updates [amd64])
Inst pidgin-libnotify (0.14-4ubuntu11 Ubuntu:12.10/quantal [amd64])
Inst pidgin-microblog (0.3.0-3 Ubuntu:12.10/quantal [amd64])
Inst pidgin-otr (3.2.1-3 Ubuntu:12.10/quantal [amd64])
Inst plymouth-theme-xubuntu-logo (12.10.2 Ubuntu:12.10/quantal [all])
Inst plymouth-theme-xubuntu-text (12.10.2 Ubuntu:12.10/quantal [all])
Inst screensaver-default-images (0.2-1 Ubuntu:12.10/quantal [all])
Inst thunar (1.4.0-1ubuntu2.1 Ubuntu:12.10/quantal-updates [amd64])
Inst thunar-archive-plugin (0.3.0-4 Ubuntu:12.10/quantal [amd64])
Inst thunar-media-tags-plugin (0.2.0-1 Ubuntu:12.10/quantal [amd64])
Inst thunar-volman (0.8.0-1 Ubuntu:12.10/quantal [amd64])
Inst tumbler-common (0.1.25-1ubuntu1 Ubuntu:12.10/quantal [all])
Inst tumbler (0.1.25-1ubuntu1 Ubuntu:12.10/quantal [amd64])
Inst xfburn (0.4.3-4ubuntu2 Ubuntu:12.10/quantal [amd64])
Inst xfce4-appfinder (4.10.0-1 Ubuntu:12.10/quantal [amd64])
Inst xfce4-cpugraph-plugin (1.0.5-0ubuntu1 Ubuntu:12.10/quantal [amd64])
Inst xfce4-dict (0.6.0-5build2 Ubuntu:12.10/quantal [amd64])
Inst xfce4-indicator-plugin (0.5.0-1ubuntu2 Ubuntu:12.10/quantal [amd64])
Inst xfce4-mailwatch-plugin (1.1.0-5build2 Ubuntu:12.10/quantal [amd64])
Inst xfce4-netload-plugin (1.2.0-0ubuntu1 Ubuntu:12.10/quantal [amd64])
Inst xfce4-notes (1.7.7-2ubuntu3 Ubuntu:12.10/quantal [amd64])
Inst xfce4-notes-plugin (1.7.7-2ubuntu3 Ubuntu:12.10/quantal [amd64])
Inst xfce4-power-manager-data (1.2.0-1ubuntu1.1 Ubuntu:12.10/quantal-updates [all])
Inst xfce4-power-manager (1.2.0-1ubuntu1.1 Ubuntu:12.10/quantal-updates [amd64])
Inst xfce4-quicklauncher-plugin (1.9.4-9build2 Ubuntu:12.10/quantal [amd64])
Inst xfce4-screenshooter (1.8.1-1 Ubuntu:12.10/quantal [amd64])
Inst xfce4-systemload-plugin (1:1.1.1-1ubuntu1 Ubuntu:12.10/quantal [amd64])
Inst xfce4-taskmanager (1.0.0-2 Ubuntu:12.10/quantal [amd64])
Inst xfce4-terminal (0.4.8-1ubuntu3 Ubuntu:12.10/quantal [amd64])
Inst xfce4-verve-plugin (1.0.0-1build2 Ubuntu:12.10/quantal [amd64])
Inst xfce4-volumed (0.1.13-2ubuntu1 Ubuntu:12.10/quantal [amd64])
Inst xfce4-weather-plugin (0.8.1-0ubuntu1 Ubuntu:12.10/quantal [amd64])
Inst xfce4-xkb-plugin (0.5.4.3-1ubuntu3 Ubuntu:12.10/quantal [amd64])
Inst xfdesktop4-data (4.10.0-1ubuntu1.1 Ubuntu:12.10/quantal-updates [all])
Inst xfdesktop4 (4.10.0-1ubuntu1.1 Ubuntu:12.10/quantal-updates [amd64])
Inst xfwm4 (4.10.0-2ubuntu1 Ubuntu:12.10/quantal [amd64])
Inst xscreensaver (5.15-2ubuntu1 Ubuntu:12.10/quantal [amd64])
Inst xubuntu-desktop (2.162 Ubuntu:12.10/quantal [amd64])
Inst xubuntu-docs (12.10.2 Ubuntu:12.10/quantal [all])
Inst xubuntu-icon-theme (12.10.2 Ubuntu:12.10/quantal [all])
Inst xubuntu-wallpapers (12.10.2 Ubuntu:12.10/quantal [all])
Inst brltty-x11 (4.4-5ubuntu3 Ubuntu:12.10/quantal [amd64])
Inst indicator-sound-gtk2 (12.10.0.1-0ubuntu1 Ubuntu:12.10/quantal [amd64])
Inst ristretto (0.6.3-0ubuntu1 Ubuntu:12.10/quantal [amd64])
Inst xbrlapi (4.4-5ubuntu3 Ubuntu:12.10/quantal [amd64])
Inst xfce4-places-plugin (1.3.0-1ubuntu1 Ubuntu:12.10/quantal [amd64])
Conf m4 (1.4.16-3 Ubuntu:12.10/quantal [amd64])
Conf libfl-dev (2.5.35-10.1ubuntu1 Ubuntu:12.10/quantal [amd64])
Conf flex (2.5.35-10.1ubuntu1 Ubuntu:12.10/quantal [amd64])
Conf libgsf-1-common (1.14.24-0ubuntu1 Ubuntu:12.10/quantal [all])
Conf libgsf-1-114 (1.14.24-0ubuntu1 Ubuntu:12.10/quantal [amd64])
Conf libwv-1.2-4 (1.2.9-3 Ubuntu:12.10/quantal [amd64])
Conf libabiword-2.9 (2.9.2+svn20120603-8 Ubuntu:12.10/quantal [amd64])
Conf libxfce4util-common (4.10.0-1 Ubuntu:12.10/quantal [all])
Conf libxfce4util6 (4.10.0-1 Ubuntu:12.10/quantal [amd64])
Conf xfconf (4.10.0-1 Ubuntu:12.10/quantal [amd64])
Conf libxfconf-0-2 (4.10.0-1 Ubuntu:12.10/quantal [amd64])
Conf xfce-keyboard-shortcuts (4.10.0-1 Ubuntu:12.10/quantal [all])
Conf libxfce4ui-1-0 (4.10.0-1 Ubuntu:12.10/quantal [amd64])
Conf libexo-common (0.8.0-1 Ubuntu:12.10/quantal [all])
Conf libexo-helpers (0.8.0-1 Ubuntu:12.10/quantal [amd64])
Conf libexo-1-0 (0.8.0-1 Ubuntu:12.10/quantal [amd64])
Conf libgarcon-common (0.2.0-1 Ubuntu:12.10/quantal [all])
Conf libgarcon-1-0 (0.2.0-1 Ubuntu:12.10/quantal [amd64])
Conf libido-0.1-0 (12.10.0.1-0ubuntu1 Ubuntu:12.10/quantal [amd64])
Conf libtagc0 (1.8-0ubuntu2 Ubuntu:12.10/quantal [amd64])
Conf thunar-data (1.4.0-1ubuntu2.1 Ubuntu:12.10/quantal-updates [all])
Conf libthunarx-2-0 (1.4.0-1ubuntu2.1 Ubuntu:12.10/quantal-updates [amd64])
Conf libtumbler-1-0 (0.1.25-1ubuntu1 Ubuntu:12.10/quantal [amd64])
Conf libxfcegui4-4 (4.10.0-1 Ubuntu:12.10/quantal [amd64])
Conf lightdm-gtk-greeter (1.3.1-0ubuntu1 Ubuntu:12.10/quantal [amd64])
Conf exo-utils (0.8.0-1 Ubuntu:12.10/quantal [amd64])
Conf xfce4-panel (4.10.0-1ubuntu2 Ubuntu:12.10/quantal [amd64])
Conf xfce4-settings (4.10.0-1ubuntu2 Ubuntu:12.10/quantal [amd64])
Conf xfce4-session (4.10.0-1ubuntu1 Ubuntu:12.10/quantal [amd64])
Conf shimmer-themes (1.5.3-0ubuntu1 Ubuntu:12.10/quantal [all])
Conf xubuntu-artwork (12.10.2 Ubuntu:12.10/quantal [all])
Conf xubuntu-default-settings (12.10.7 Ubuntu:12.10/quantal [all])
Conf libloudmouth1-0 (1.4.3-8 Ubuntu:12.10/quantal [amd64])
Conf libots0 (0.5.0-2.1 Ubuntu:12.10/quantal [amd64])
Conf libtidy-0.99-0 (20091223cvs-1.2 Ubuntu:12.10/quantal [amd64])
Conf abiword-common (2.9.2+svn20120603-8 Ubuntu:12.10/quantal [all])
Conf abiword (2.9.2+svn20120603-8 Ubuntu:12.10/quantal [amd64])
Conf link-grammar-dictionaries-en (4.7.4-2 Ubuntu:12.10/quantal [all])
Conf liblink-grammar4 (4.7.4-2 Ubuntu:12.10/quantal [amd64])
Conf abiword-plugin-grammar (2.9.2+svn20120603-8 Ubuntu:12.10/quantal [amd64])
Conf libgdome2-0 (0.8.1+debian-4.1build1 Ubuntu:12.10/quantal [amd64])
Conf libgdome2-cpp-smart0c2a (0.2.6-6build2 Ubuntu:12.10/quantal [amd64])
Conf libgtkmathview0c2a (0.8.0-8 Ubuntu:12.10/quantal [amd64])
Conf fonts-lyx (2.0.3-3 Ubuntu:12.10/quantal [all])
Conf abiword-plugin-mathview (2.9.2+svn20120603-8 Ubuntu:12.10/quantal [amd64])
Conf libbison-dev (1:2.5.dfsg-2.1build1 Ubuntu:12.10/quantal [amd64])
Conf bison (1:2.5.dfsg-2.1build1 Ubuntu:12.10/quantal [amd64])
Conf xfce4-notifyd (0.2.2-2ubuntu1 Ubuntu:12.10/quantal [amd64])
Conf blueman (1.23-0ubuntu3 Ubuntu:12.10/quantal [amd64])
Conf catfish (0.4.0.2-0ubuntu1 Ubuntu:12.10/quantal [all])
Conf gigolo (0.4.1-3 Ubuntu:12.10/quantal [amd64])
Conf libgstreamer-perl (0.17-1 Ubuntu:12.10/quantal [amd64])
Conf gmusicbrowser (1.1.9-2 Ubuntu:12.10/quantal [all])
Conf gnome-time-admin (3.0.0-2ubuntu1 Ubuntu:12.10/quantal [amd64])
Conf gstreamer0.10-gnomevfs (0.10.36-1ubuntu1.1 Ubuntu:12.10/quantal-updates [amd64])
Conf gthumb-data (3:3.0.2-0ubuntu2 Ubuntu:12.10/quantal [all])
Conf gthumb (3:3.0.2-0ubuntu2 Ubuntu:12.10/quantal [amd64])
Conf indicator-application-gtk2 (12.10.0.1-0ubuntu1 Ubuntu:12.10/quantal [amd64])
Conf leafpad (0.8.18.1-3 Ubuntu:12.10/quantal [amd64])
Conf libdigest-crc-perl (0.18-1 Ubuntu:12.10/quantal [amd64])
Conf libgtk2-notify-perl (0.05-3build1 Ubuntu:12.10/quantal [amd64])
Conf libgtk2-trayicon-perl (0.06-1build2 Ubuntu:12.10/quantal [amd64])
Conf libintl-perl (1.20-1build2 Ubuntu:12.10/quantal [all])
Conf libkeybinder0 (0.2.2-4 Ubuntu:12.10/quantal [amd64])
Conf libotr2 (3.2.1-1 Ubuntu:12.10/quantal [amd64])
Conf libunique-1.0-0 (1.1.6-4build1 Ubuntu:12.10/quantal [amd64])
Conf libxfce4ui-utils (4.10.0-1 Ubuntu:12.10/quantal [amd64])
Conf libxfce4util-bin (4.10.0-1 Ubuntu:12.10/quantal [amd64])
Conf orage (4.8.3-2 Ubuntu:12.10/quantal [amd64])
Conf parole (0.3.0.3-0ubuntu1 Ubuntu:12.10/quantal [amd64])
Conf python-configobj (4.7.2+ds-4 Ubuntu:12.10/quantal [all])
Conf pastebinit (1.3-2ubuntu3 Ubuntu:12.10/quantal [all])
Conf pavucontrol (1.0-1 Ubuntu:12.10/quantal [amd64])
Conf pidgin-data (1:2.10.6-0ubuntu2.2 Ubuntu:12.10/quantal-updates [all])
Conf pidgin (1:2.10.6-0ubuntu2.2 Ubuntu:12.10/quantal-updates [amd64])
Conf pidgin-libnotify (0.14-4ubuntu11 Ubuntu:12.10/quantal [amd64])
Conf pidgin-microblog (0.3.0-3 Ubuntu:12.10/quantal [amd64])
Conf pidgin-otr (3.2.1-3 Ubuntu:12.10/quantal [amd64])
Conf plymouth-theme-xubuntu-logo (12.10.2 Ubuntu:12.10/quantal [all])
Conf plymouth-theme-xubuntu-text (12.10.2 Ubuntu:12.10/quantal [all])
Conf screensaver-default-images (0.2-1 Ubuntu:12.10/quantal [all])
Conf thunar (1.4.0-1ubuntu2.1 Ubuntu:12.10/quantal-updates [amd64])
Conf thunar-archive-plugin (0.3.0-4 Ubuntu:12.10/quantal [amd64])
Conf thunar-media-tags-plugin (0.2.0-1 Ubuntu:12.10/quantal [amd64])
Conf thunar-volman (0.8.0-1 Ubuntu:12.10/quantal [amd64])
Conf tumbler-common (0.1.25-1ubuntu1 Ubuntu:12.10/quantal [all])
Conf tumbler (0.1.25-1ubuntu1 Ubuntu:12.10/quantal [amd64])
Conf xfburn (0.4.3-4ubuntu2 Ubuntu:12.10/quantal [amd64])
Conf xfce4-appfinder (4.10.0-1 Ubuntu:12.10/quantal [amd64])
Conf xfce4-cpugraph-plugin (1.0.5-0ubuntu1 Ubuntu:12.10/quantal [amd64])
Conf xfce4-dict (0.6.0-5build2 Ubuntu:12.10/quantal [amd64])
Conf xfce4-indicator-plugin (0.5.0-1ubuntu2 Ubuntu:12.10/quantal [amd64])
Conf xfce4-mailwatch-plugin (1.1.0-5build2 Ubuntu:12.10/quantal [amd64])
Conf xfce4-netload-plugin (1.2.0-0ubuntu1 Ubuntu:12.10/quantal [amd64])
Conf xfce4-notes (1.7.7-2ubuntu3 Ubuntu:12.10/quantal [amd64])
Conf xfce4-notes-plugin (1.7.7-2ubuntu3 Ubuntu:12.10/quantal [amd64])
Conf xfce4-power-manager-data (1.2.0-1ubuntu1.1 Ubuntu:12.10/quantal-updates [all])
Conf xfce4-power-manager (1.2.0-1ubuntu1.1 Ubuntu:12.10/quantal-updates [amd64])
Conf xfce4-quicklauncher-plugin (1.9.4-9build2 Ubuntu:12.10/quantal [amd64])
Conf xfce4-screenshooter (1.8.1-1 Ubuntu:12.10/quantal [amd64])
Conf xfce4-systemload-plugin (1:1.1.1-1ubuntu1 Ubuntu:12.10/quantal [amd64])
Conf xfce4-taskmanager (1.0.0-2 Ubuntu:12.10/quantal [amd64])
Conf xfce4-terminal (0.4.8-1ubuntu3 Ubuntu:12.10/quantal [amd64])
Conf xfce4-verve-plugin (1.0.0-1build2 Ubuntu:12.10/quantal [amd64])
Conf xfce4-volumed (0.1.13-2ubuntu1 Ubuntu:12.10/quantal [amd64])
Conf xfce4-weather-plugin (0.8.1-0ubuntu1 Ubuntu:12.10/quantal [amd64])
Conf xfce4-xkb-plugin (0.5.4.3-1ubuntu3 Ubuntu:12.10/quantal [amd64])
Conf xfdesktop4-data (4.10.0-1ubuntu1.1 Ubuntu:12.10/quantal-updates [all])
Conf xfdesktop4 (4.10.0-1ubuntu1.1 Ubuntu:12.10/quantal-updates [amd64])
Conf xfwm4 (4.10.0-2ubuntu1 Ubuntu:12.10/quantal [amd64])
Conf xscreensaver (5.15-2ubuntu1 Ubuntu:12.10/quantal [amd64])
Conf xubuntu-desktop (2.162 Ubuntu:12.10/quantal [amd64])
Conf xubuntu-docs (12.10.2 Ubuntu:12.10/quantal [all])
Conf xubuntu-icon-theme (12.10.2 Ubuntu:12.10/quantal [all])
Conf xubuntu-wallpapers (12.10.2 Ubuntu:12.10/quantal [all])
Conf brltty-x11 (4.4-5ubuntu3 Ubuntu:12.10/quantal [amd64])
Conf indicator-sound-gtk2 (12.10.0.1-0ubuntu1 Ubuntu:12.10/quantal [amd64])
Conf ristretto (0.6.3-0ubuntu1 Ubuntu:12.10/quantal [amd64])
Conf xbrlapi (4.4-5ubuntu3 Ubuntu:12.10/quantal [amd64])
Conf xfce4-places-plugin (1.3.0-1ubuntu1 Ubuntu:12.10/quantal [amd64])

```
Here is the package reference:
[http://packages.ubuntu.com/precise/xubuntu-desktop](http://packages.ubuntu.com/precise/xubuntu-desktop)

I have supported UNIX, then Linux for over 25 years... created custom LiveCD's and custom distro's. I convert RPM's to Debain packages. I've ported OS'es to handheld devices since, MSCE 1.0. (I was at the announcement of...) I get to develop app's. I've built Linux from scratch. I've played with lots of combinations of packages to create different combinations of configurations. I've created very light remote user desktops using just XServer utils... I specialize in the UNIX and Linux graphics layer... I get to play with those hands on. Not many people have 5 laptops, 10 desktops and 10 servers at home to play with. To dev test with and see what works and what doesn't, hands on. I seem to know what I am talking about. I am usually modest. If I don't know something, it inspires me to learn about it... But if I don't know something or if I am wrong, I'll be the first to admit it or apologize for a mistake..

I'm sorry that you seem to have taken the defense and misunderstood me. I mean nothing by it personally nor otherwise. I would rather have friends than have any kind of confrontation.

If you are curious about what would happen if you install or remove a package without actually installing or removing it... a dry run:
```

sudo apt-get install -sV xubuntu-desktop

```
It will print out a dry run without making any changes... Or go Synaptic and check to see what packages it marks to install and/or remove.

The OP could install the meta-package "xubuntu-desktop" which will take a while for him to download, install and will take a chunk of space from his hard disk. The OP needs to be aware of and plan for that and what will happen. That package will install any user application included in the full Xubuntu Desktop Edition distro that is not common to the Lubuntu Desktop Edition distro. Historically, when I first tried Xubuntu years ago, Xubuntu was only offered as getting this same named meta-package and installing it on an Ubuntu base core. When it first came out, there was no separate ISO images or separate distro branch. I've done this before.

Post #1. The Op mentioned he was on Lubuntu. He mentioned a slow internet connection. He mentioned going to Xubuntu. He mentioned going to "ubuntu-desktop" which includes even more applications that are not common with the other desktop editions. He wanted to know the implications of installing that meta-package instead of doing a re-install. Noted. 

He mentioned concerns about backing off changes. Backup a snap-shot before doing it (recommended) or.. Install etckeeper, which would install bazaar version control, so you back back off to any previous incremental system change.

What is a concern is 
> 
[COLOR=#000000] i cant run my lubuntu pc for long time and i ave a slow connection[/COLOR]

Which could be translated to limited system resources, such as needing a minimum install... which brings up- just downloading a minumum install cd, which if he wanted to install fresh, then he could install the Ubuntu core base... He could select the flavored "...-desktop" he wanted to try from the tasksel from that disk and only have to dl one ISO to be able to do that. (maximizing his dl time on that slow connection.) But then again, that would mean a reinstall. Or he could use the ISO's as a local apt repo by mounting it and then using "apt-cdrom --add" to use the packages on a cd image as a local repo.

Like I said, I'm here to help, not to argue or fight. Starting to feel bad that you think I have slighted you in some way. Not meant that way at all. Laterz.

---

### Post by cortman on 2013-04-08
What?

```
sudo apt-get install xubuntu-desktop
```

installs the metapackage "xubuntu-desktop" which includes (as dependencies) all the packages that come with a normal Xubuntu installation (besides, obviously, the base system).
Running the commands given in the psychocats' tutorial will remove all traces of Lubuntu.

It's as simple as that. I don't get what the point of contention is. Sure, xubuntu-desktop is a big package, but that's what it takes if you want Xubuntu.

---

### Post by rxlord on 2013-04-10
ok ok i got the answer on how to install xubuntu desktop so no more posts about that.
now plz answer my other questions

---

### Post by cortman on 2013-04-10
It looks like you're asking several different and unrelated questions. Start a new thread for each question so people can help you more effectively.

---

### Post by howefield on 2013-04-10
Your downloaded packages are saved to /var/cache/apt/archives. Copy them from there and you can paste back to the same location when needed.

Clonezilla will image your drive and allow you to reimage it back when you mess up.

Packages can be downloaded form [http://packages.ubuntu.com/](http://packages.ubuntu.com/) not sure it is the best way, but it works.

---

