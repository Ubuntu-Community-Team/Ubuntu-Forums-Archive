---
title: "Upgrade from 13.10 to 14.04 Hangs"
date: 2014-10-05
forum: Installation &amp; Upgrades
---

### Post by MidnightJava on 2014-10-05
After reading the release notes and the instructions for upgrading to 14.04, I did```
 sudo update-manager
```, and then clicked the "Upgrade" button. On the dialog with introductory information I clicked "Upgrade" at the bottom. A window came up with the various steps in the upgrade process listed, to show progress as it proceeded.

Within 30 secs or so it tried to launch a dialog of some sort. But the dialog is just empty, and the parent window is empty now as well. So apparently it hug as it was trying to tell me something, and I have no idea what it was trying to tell me.

It was fairly early in the upgrade process, so maybe if I kill the Distribution Upgrade window everything will be fine. But I know from experience that interrupting an upgrade can be disastrous, so I don;t want to do that.

Is there some way I can find out what it's hung on, or how far along it is? My system is very vanilla, nothing out of the ordinary. I started with Ubuntu 11.10 IIRC and have been able to upgrade each time all the way to 13.10. Now suddenly it just hangs.

Edit: top shows process trusty with cpu utilization around 190%, fluctuating a few points up and down. I have two cores.

---

### Post by Vladlenin5000 on 2014-10-05
You should have done it earlier...
13.10 is EoL and I'm not sure its repositories are still online.

---

### Post by MidnightJava on 2014-10-05
Thanks for the reply. I did notice that 13.10 updates were no longer available; but I didn't realize that that meant I wouldn't be able to upgrade from 13.10 to 14.04. Nor that the attempt would fail so ungracefully.

So I guess my only option now is to do a fresh install of Ubuntu? Does that mean I have to backup and restore all my data and re-install all my apps?

Edit: Also this official Ubuntu page gives instructions for [upgrading from 13.10 to 14.04]("https://help.ubuntu.com/community/TrustyUpgrades"). Doesn't that mean it's still supported? It was following the instructions on that link hat led to the hung installation. And this page on[ general upgrade instructions]("https://help.ubuntu.com/community/UpgradeNotes#From_13.10_to_14.04") lists the 13.10 to 14.04 upgrade under the heading "current and supported".

---

### Post by Vladlenin5000 on 2014-10-05
You're right about that and the failure might have nothing to do with the EoL status. It could be a problem with one or more PPAs, perhaps?!?

@oldfred is the expert, not me.

---

### Post by grahammechanical on 2014-10-05
Ubuntu 13.10 is not still supported and the wiki page was written 2014-18-04 or just before Ubuntu 14.04 was released. It is not applicable now that we are 3 months beyond the End of Life date of 13.10.

This information is more applicable 

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

I would have thought that if End of Life was the problem then the upgrade would not have even started. You would have got an error message about not finding the repositories.

Can you move that dialog out of the way? Is the whole system frozen? Pressing enter might get things moving. We sometimes get asked to approve some action. I have known the upgrade process to ask for confirmation to over-write an existing Grub configuration file or to accept something or other regarding DBus. 

Regards.

---

### Post by MidnightJava on 2014-10-05
I killed the Distribution Upgrade window (didn't think about just hitting Return), and re-ran sudo update-manager. Based on VladLennin5000's comment I checked the Software Update tab and saw that all the sources were un-checked. So I checked them and proceeded with the upgrade. It downloaded all the packages and then exited. So I ran ```
sudo apt-get dist-upgrade
```, and it seemed to be upgrading, but ultimately failed.

Now that I see grahammechanical's response, I realize that was probably a mistake, and I think I've really messed things up. I can give the particulars of how it failed, but maybe that's not important. For the most part it seemed to be succeeding, and ran for quite a while installing packages. I saw an error message scroll by saying that a file was missing, and I might need to run

  ```
gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
``` to work around it. (But when I run that, even with sudo, I get permission denied.

Then the installation suddenly quit with the following on the command line:

```
Unpacking libgphoto2-dev (2.5.3.1-1ubuntu2.2) ...
dpkg: error processing archive /var/cache/apt/archives/libgphoto2-dev_2.5.3.1-1ubuntu2.2_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libgphoto2.a', which is also in package libgphoto2-6-dev 2.5.2-0ubuntu5
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to unpack .../libieee1284-3-dev_0.2.11-12_amd64.deb ...
Unpacking libieee1284-3-dev (0.2.11-12) over (0.2.11-11) ...
Preparing to unpack .../libieee1284-3_0.2.11-12_amd64.deb ...
De-configuring libieee1284-3:i386 (0.2.11-11) ...
Unpacking libieee1284-3:amd64 (0.2.11-12) over (0.2.11-11) ...
Preparing to unpack .../libieee1284-3_0.2.11-12_i386.deb ...
Unpacking libieee1284-3:i386 (0.2.11-12) over (0.2.11-11) ...
Preparing to unpack .../libsane-dev_1.0.23-3ubuntu3.1_amd64.deb ...
Unpacking libsane-dev (1.0.23-3ubuntu3.1) over (1.0.23-0ubuntu3) ...
Processing triggers for man-db (2.6.5-2) ...
Processing triggers for gnome-menus (3.8.1-0ubuntu2~saucy1) ...
Processing triggers for bamfdaemon (0.5.1+13.10.20131011-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1) ...
Processing triggers for doc-base (0.10.5) ...
Processing 2 changed doc-base files, 1 added doc-base file...
Processing triggers for install-info (5.2.0.dfsg.1-2) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libgphoto2-dev_2.5.3.1-1ubuntu2.2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


If I try to run sudo apt-get dist-upgrade again I get 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 gvfs-backends : Depends: libsmbclient (>= 2:4.0.3+dfsg1) but 2:3.6.18-1ubuntu3.3 is installed
 libgtk-3-0 : Depends: libcairo2 (>= 1.13.0~20140204) but 1.12.16-0ubuntu2 is installed
 libharfbuzz-icu0 : Depends: libharfbuzz0b (>= 0.6.0) but it is not installed
 libpangoft2-1.0-0 : Depends: libharfbuzz0b (>= 0.9.9) but it is not installed
 libreoffice-core : Depends: libboost-date-time1.54.0 but it is not installed
                    Depends: libcmis-0.4-4 (>= 0.4.0) but it is not installed
                    Depends: libharfbuzz0b (>= 0.9.18) but it is not installed
                    Depends: librdf0 (>= 1.0.17) but 1.0.16-1 is installed
 libsane-dev : Depends: libgphoto2-dev but it is not installed
               Depends: libsane (= 1.0.23-3ubuntu3.1) but 1.0.23-0ubuntu3 is installed
 libwebkitgtk-3.0-0 : Depends: libharfbuzz0b (>= 0.9.18) but it is not installed
E: Unmet dependencies. Try using -f.
```


So I'm exactly where I didn't want to be, in the midst of a failed upgrade. I took at the link that grahammechanical posted, and it doesn't address the transition from 13.10 to 14.04 (the highest it goes is 11.10 to 12.04). Since it's mostly a list of specific packages to install depending on which upgrade you're trying to do, it doesn't seem there's anything there I should try.

I think I'm pretty screwed up here, but at least I haven't rebooted. Any ideas how I can get out of this mess?

---

### Post by MidnightJava on 2014-10-06
The link with instructions for upgrading from EOL distributions says to put the following in /etc/apt/sources.list

```
[COLOR=#333333][FONT=UbuntuMono]deb http://old-releases.ubuntu.com/ubuntu/ saucy main restricted universe multiverse
[/FONT][/COLOR]deb http://old-releases.ubuntu.com/ubuntu/ saucy-updates main restricted universe multiverse
[COLOR=#333333][FONT=UbuntuMono]deb http://old-releases.ubuntu.com/ubuntu/ saucy-security main restricted universe multiverse[/FONT][/COLOR]  
```

I tried that but when I run sudo apt-get update, I get 404 errors for the URL [COLOR=#333333][FONT=UbuntuMono]http://old-releases.ubuntu.com/ubuntu/. If I point my browser at that URL I see a dists folder that has almost every release from breezy to raring, but no saucy

I ran
[/FONT][/COLOR]```
[COLOR=#000000]sudo dpkg --configure -a[/COLOR]
[COLOR=#000000]sudo apt-get -f install[/COLOR]
```

And seemed to get normal results. But then running [COLOR=#000000]sudo apt-get dist-upgrade[/COLOR] fails and I I end up in upgrade Hell.

sudo apt-get -f install now results in

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  argyll browser-plugin-gnash caribou caribou-antler cheese fonts-cantarell
  gdebi gdebi-core geoclue-2.0 gir1.2-gtop-2.0 gir1.2-rest-0.7
  gir1.2-tracker-0.16 gir1.2-zpj-0.0 gnash gnash-common gnome-backgrounds
  gnome-color-manager gnome-dictionary gnome-documents gnome-games
  gnome-icon-theme-extras gnome-nettool gnome-online-miners gnome-packagekit
  gnome-packagekit-data gnome-packagekit-session gnome-shell-extensions
  gnome-tweak-tool gnome-video-effects gstreamer1.0-nice hamster-applet
  hamster-indicator inkscape libbonoboui2-0 libbonoboui2-common
  libboost-date-time1.53.0 libboost-program-options1.53.0
  libboost-thread1.53.0 libcaribou-gtk-module libcaribou-gtk3-module
  libcmis-0.3-3 libdb5.1:i386 libebackend-1.2-6 libedata-book-1.2-17
  libedata-cal-1.2-20 libfarstream-0.2-2 libgdict-1.0-6 libgdict-common
  libgnomecanvas2-0 libgnomecanvas2-common libgnomeui-0 libgnomeui-common
  libgrilo-0.2-1 libgsl0ldbl libgupnp-av-1.0-2 libgupnp-dlna-2.0-3
  libgweather-3-3 libhud-client2 libicc2 libimdi0 libjson0:i386
  libkadm5clnt-mit8 libkadm5srv-mit8 libkdb5-6 libllvm3.3 libllvm3.3:i386
  libmagick++5 libmozjs-17.0-0 libpthread-stubs0 libqt53d5 libqt5location5
  libqt5v8-5 librhythmbox-core7 librygel-core-2.0-1 librygel-renderer-2.0-1
  librygel-renderer-gst-2.0-1 librygel-server-2.0-1 libsasl2-modules:i386
  libsofia-sip-ua-glib3 libsofia-sip-ua0 libtasn1-3:i386 libtasn1-3-dev
  libtelepathy-farstream3 libxcb-sync0 libzapojit-0.0-0
  linux-image-3.11.0-15-generic linux-image-extra-3.11.0-15-generic
  oneconf-common perlmagick python-gnome2 python-oneconf python-pyatspi
  python-pyorbit python-uniconvertor python-wnck python3-dirspec
  python3-oneconf python3-piston-mini-client re2c rygel rygel-playbin
  rygel-preferences seahorse sound-juicer telepathy-rakia
  ubuntuone-client-data xfce-keyboard-shortcuts
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  cheese cheese-common gir1.2-totem-1.0 gnome-settings-daemon-schemas
  gstreamer1.0-clutter libcheese-gtk23 libcheese7 libclutter-gst-1.0-0
  libgjs0e libmozjs-24-0 libmx-1.0-2 libmx-common totem totem-common
  totem-mozilla totem-plugins webaccounts-extension-common
Suggested packages:
  gnome-video-effects-frei0r gnome-video-effects-extra gromit
The following packages will be REMOVED:
  gnome-core libgjs0d
The following NEW packages will be installed:
  gnome-settings-daemon-schemas libgjs0e libmozjs-24-0
The following packages will be upgraded:
  cheese cheese-common gir1.2-totem-1.0 gstreamer1.0-clutter libcheese-gtk23
  libcheese7 libclutter-gst-1.0-0 libmx-1.0-2 libmx-common totem totem-common
  totem-mozilla totem-plugins webaccounts-extension-common
14 upgraded, 3 newly installed, 2 to remove and 1145 not upgraded.
10 not fully installed or removed.
Need to get 0 B/5,571 kB of archives.
After this operation, 3,031 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 285829 files and directories currently installed.)
Preparing to unpack .../gnome-settings-daemon-schemas_3.8.6.1-0ubuntu11.2_all.deb ...
Unpacking gnome-settings-daemon-schemas (3.8.6.1-0ubuntu11.2) ...
dpkg: error processing archive /var/cache/apt/archives/gnome-settings-daemon-schemas_3.8.6.1-0ubuntu11.2_all.deb (--unpack):
 trying to overwrite '/usr/share/GConf/gsettings/gnome-settings-daemon.convert', which is also in package gnome-settings-daemon 3.10.2-0ubuntu1~saucy6
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-settings-daemon-schemas_3.8.6.1-0ubuntu11.2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

And [COLOR=#000000]sudo dpkg --configure -a[/COLOR][COLOR=#000000] returns

[/COLOR]```
dpkg: dependency problems prevent configuration of unity-settings-daemon:
 unity-settings-daemon depends on gnome-settings-daemon-schemas (>= 3.8); however:
  Package gnome-settings-daemon-schemas is not installed.
 unity-settings-daemon depends on gnome-settings-daemon-schemas (<< 3.10); however:
  Package gnome-settings-daemon-schemas is not installed.


dpkg: error processing package unity-settings-daemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gjs:
 gjs depends on libgjs0-libmozjs-24-0; however:
  Package libgjs0-libmozjs-24-0 is not installed.
 gjs depends on libgjs0e (>= 1.40.1); however:
  Package libgjs0e is not installed.


dpkg: error processing package gjs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-session-flashback:
 gnome-session-flashback depends on unity-settings-daemon; however:
  Package unity-settings-daemon is not configured yet.


dpkg: error processing package gnome-session-flashback (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-sushi:
 gnome-sushi depends on libgjs0-libmozjs-24-0; however:
  Package libgjs0-libmozjs-24-0 is not installed.
 gnome-sushi depends on libgjs0e (>= 1.39.90); however:
  Package libgjs0e is not installed.


dpkg: error processing package gnome-sushi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xul-ext-webaccounts:
 xul-ext-webaccounts depends on webaccounts-extension-common (= 0.5-0ubuntu2); however:
  Version of webaccounts-extension-common on system is 0.5-0ubuntu1.


dpkg: error processing package xul-ext-webaccounts (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compiz-gnome:
 compiz-gnome depends on gnome-settings-daemon-schemas (>= 3.4.2-0ubuntu9); however:
  Package gnome-settings-daemon-schemas is not installed.


dpkg: error processing package compiz-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-shell:
 gnome-shell depends on libgjs0-libmozjs-24-0; however:
  Package libgjs0-libmozjs-24-0 is not installed.
 gnome-shell depends on libgjs0e (>= 1.40.1); however:
  Package libgjs0e is not installed.
 gnome-shell depends on libmozjs-24-0; however:
  Package libmozjs-24-0 is not installed.
 gnome-shell depends on gjs (>= 1.37.4); however:
  Package gjs is not configured yet.


dpkg: error processing package gnome-shell (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gdm:
 gdm depends on gnome-shell; however:
  Package gnome-shell is not configured yet.


dpkg: error processing package gdm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compiz:
 compiz depends on compiz-gnome; however:
  Package compiz-gnome is not configured yet.


dpkg: error processing package compiz (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unity:
 unity depends on compiz; however:
  Package compiz is not configured yet.


dpkg: error processing package unity (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 unity-settings-daemon
 gjs
 gnome-session-flashback
 gnome-sushi
 xul-ext-webaccounts
 compiz-gnome
 gnome-shell
 gdm
 compiz
 unity

```

It seems like the issue is I have no way to point to the EOL saucy sources. As I mentioned, they're missing from [COLOR=#333333][FONT=UbuntuMono]http://old-releases.ubuntu.com/ubuntu/. I do see them in the dists folder at [/FONT][/COLOR]http://ubuntu.mirror.constant.com/, but apt-get update is not picking them up.

---

### Post by MidnightJava on 2014-10-07
So I have a lot of information posted here, but the problem boils down to this:

The Ubuntu page on [EOL upgrades]("https://help.ubuntu.com/community/EOLUpgrades") says to put the following in my sources.list file in order to access the packages for an EOL release:

```
## EOL upgrade sources.list
# Required
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) CODENAME main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) CODENAME-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) CODENAME-security main restricted universe multiverse
```

But when I do that, substituting saucy for CODENAME, I get http 404 errors when I run sudo apt-get update, shown below. So the saucy packages seem to have been removed from the usual location, but not copied to the advertised EOL archive location. I can find raring packages this way, and most of the other releases down to breezy, but not saucy.

Am I doing something wrong, or are the saucy packages just not available for some reason?

```

Ign http://ppa.launchpad.net saucy/main Translation-en_US                      
Ign http://ppa.launchpad.net saucy/main Translation-en
Ign http://ppa.launchpad.net saucy/main Translation-en_US
Ign http://ppa.launchpad.net saucy/main Translation-en
Ign http://ppa.launchpad.net saucy/main Translation-en_US
Ign http://ppa.launchpad.net saucy/main Translation-en
Err http://old-releases.ubuntu.com saucy/main amd64 Packages                   
  404  Not Found
Err http://old-releases.ubuntu.com saucy/restricted amd64 Packages
  404  Not Found
Err http://old-releases.ubuntu.com saucy/universe amd64 Packages
  404  Not Found
Err http://old-releases.ubuntu.com saucy/multiverse amd64 Packages
  404  Not Found
Err http://old-releases.ubuntu.com saucy/main i386 Packages
  404  Not Found
Err http://old-releases.ubuntu.com saucy/restricted i386 Packages
  404  Not Found
Err http://old-releases.ubuntu.com saucy/universe i386 Packages
  404  Not Found
Err http://old-releases.ubuntu.com saucy/multiverse i386 Packages
  404  Not Found
Ign http://old-releases.ubuntu.com saucy/main Translation-en_US
Ign http://old-releases.ubuntu.com saucy/main Translation-en
Ign http://old-releases.ubuntu.com saucy/multiverse Translation-en_US
Ign http://old-releases.ubuntu.com saucy/multiverse Translation-en
Ign http://old-releases.ubuntu.com saucy/restricted Translation-en_US
Ign http://old-releases.ubuntu.com saucy/restricted Translation-en
Ign http://old-releases.ubuntu.com saucy/universe Translation-en_US
Ign http://old-releases.ubuntu.com saucy/universe Translation-en
Err http://old-releases.ubuntu.com saucy-updates/main amd64 Packages
  404  Not Found
Err http://old-releases.ubuntu.com saucy-updates/restricted amd64 Packages
  404  Not Found
Err http://old-releases.ubuntu.com saucy-updates/universe amd64 Packages
  404  Not Found
Err http://old-releases.ubuntu.com saucy-updates/multiverse amd64 Packages
  404  Not Found
Err http://old-releases.ubuntu.com saucy-updates/main i386 Packages
  404  Not Found
Err http://old-releases.ubuntu.com saucy-updates/restricted i386 Packages
  404  Not Found
Err http://old-releases.ubuntu.com saucy-updates/universe i386 Packages
  404  Not Found
Err http://old-releases.ubuntu.com saucy-updates/multiverse i386 Packages
  404  Not Found
Ign http://old-releases.ubuntu.com saucy-updates/main Translation-en_US
Ign http://old-releases.ubuntu.com saucy-updates/main Translation-en
Ign http://old-releases.ubuntu.com saucy-updates/multiverse Translation-en_US
Ign http://old-releases.ubuntu.com saucy-updates/multiverse Translation-en
Ign http://old-releases.ubuntu.com saucy-updates/restricted Translation-en_US
Ign http://old-releases.ubuntu.com saucy-updates/restricted Translation-en
Ign http://old-releases.ubuntu.com saucy-updates/universe Translation-en_US
Ign http://old-releases.ubuntu.com saucy-updates/universe Translation-en
Err http://old-releases.ubuntu.com saucy-security/main amd64 Packages
  404  Not Found
Err http://old-releases.ubuntu.com saucy-security/restricted amd64 Packages
  404  Not Found
Err http://old-releases.ubuntu.com saucy-security/universe amd64 Packages
  404  Not Found
Err http://old-releases.ubuntu.com saucy-security/multiverse amd64 Packages
  404  Not Found
Err http://old-releases.ubuntu.com saucy-security/main i386 Packages
  404  Not Found
Err http://old-releases.ubuntu.com saucy-security/restricted i386 Packages
  404  Not Found
Err http://old-releases.ubuntu.com saucy-security/universe i386 Packages
  404  Not Found
Err http://old-releases.ubuntu.com saucy-security/multiverse i386 Packages
  404  Not Found
Ign http://old-releases.ubuntu.com saucy-security/main Translation-en_US
Ign http://old-releases.ubuntu.com saucy-security/main Translation-en
Ign http://old-releases.ubuntu.com saucy-security/multiverse Translation-en_US
Ign http://old-releases.ubuntu.com saucy-security/multiverse Translation-en
Ign http://old-releases.ubuntu.com saucy-security/restricted Translation-en_US
Ign http://old-releases.ubuntu.com saucy-security/restricted Translation-en
Ign http://old-releases.ubuntu.com saucy-security/universe Translation-en_US
Ign http://old-releases.ubuntu.com saucy-security/universe Translation-en
Fetched 1,625 kB in 23s (68.0 kB/s)
W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy/main/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy/restricted/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy/universe/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy/multiverse/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy/main/binary-i386/Packages  404  Not Found


W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy/restricted/binary-i386/Packages  404  Not Found


W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy/universe/binary-i386/Packages  404  Not Found


W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy/multiverse/binary-i386/Packages  404  Not Found


W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-updates/main/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-updates/restricted/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-updates/universe/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-updates/multiverse/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-updates/main/binary-i386/Packages  404  Not Found


W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-updates/restricted/binary-i386/Packages  404  Not Found


W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-updates/universe/binary-i386/Packages  404  Not Found


W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-updates/multiverse/binary-i386/Packages  404  Not Found


W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-security/main/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-security/restricted/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-security/universe/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-security/multiverse/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-security/main/binary-i386/Packages  404  Not Found


W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-security/restricted/binary-i386/Packages  404  Not Found


W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-security/universe/binary-i386/Packages  404  Not Found


W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/saucy-security/multiverse/binary-i386/Packages  404  Not Found

```

---

