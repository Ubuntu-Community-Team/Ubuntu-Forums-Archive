---
title: "dist-upgrade want to remove packages i use"
date: 2009-08-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by terry_gardener on 2009-08-21
i have just ran sudo apt-get dist-upgrade and it want to remove loads of software/packages that i use. 

anyone know why, 

here is the terminal output. 

The following packages will be REMOVED
  devede gecko-mediaplayer gnome-mplayer gstreamer0.10-ffmpeg
  gstreamer0.10-plugins-bad-multiverse k9copy libavcodec-unstripped-52
  libavformat-unstripped-52 libk3b6-extracodecs libmjpegtools-1.9
  libquicktime1 mencoder mjpegtools mplayer mplayer-nogui vlc vlc-nox
  vlc-plugin-pulse
The following NEW packages will be installed
  akonadi-server kdebase-workspace-bin kdebase-workspace-data
  kdebase-workspace-kgreet-plugins kdebase-workspace-libs4+5 kdepim-runtime
  kdepim-runtime-data kdepim-runtime-libs4 kdepimlibs-data kdepimlibs5
  libakonadiprivate1 libboost-program-options1.38.0 libqimageblitz4
  libstrigiqtdbusclient0 mysql-server-core-5.1 plasma-dataengines-workspace
  plasma-widgets-workspace
The following packages have been kept back:
  nvidia-common
The following packages will be upgraded:
  alsa-utils computer-janitor computer-janitor-gtk k3b k3b-data
  language-pack-en language-pack-en-base language-pack-gnome-en
  language-pack-gnome-en-base libk3b6 libpulse-browse0 libpulse-mainloop-glib0
  libpulse0 libsasl2-2 libsasl2-modules modemmanager mozilla-thunderbird
  network-manager-gnome ntpdate pulseaudio pulseaudio-esound-compat
  pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-udev
  pulseaudio-module-x11 pulseaudio-module-zeroconf pulseaudio-utils
  python-fstab thunderbird
29 upgraded, 17 newly installed, 18 to remove and 1 not upgraded.
Need to get 40.2MB/43.4MB of archives.
After this operation, 7385kB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.

---

### Post by DougieFresh4U on 2009-08-21
Upgrade this morning didn't want to remove any thing here.
Some times I will copy what packages it wants to remove and I will install them afterwards. Just my thought.

---

### Post by Seventh Reign on 2009-08-21
> **terry_gardener said:**
> i have just ran sudo apt-get dist-upgrade and it want to remove loads of software/packages that i use. 

anyone know why, 

here is the terminal output. 

The following packages will be REMOVED
  devede gecko-mediaplayer gnome-mplayer gstreamer0.10-ffmpeg
  gstreamer0.10-plugins-bad-multiverse k9copy libavcodec-unstripped-52
  libavformat-unstripped-52 libk3b6-extracodecs libmjpegtools-1.9
  libquicktime1 mencoder mjpegtools mplayer mplayer-nogui vlc vlc-nox
  vlc-plugin-pulse
The following NEW packages will be installed
  akonadi-server kdebase-workspace-bin kdebase-workspace-data
  kdebase-workspace-kgreet-plugins kdebase-workspace-libs4+5 kdepim-runtime
  kdepim-runtime-data kdepim-runtime-libs4 kdepimlibs-data kdepimlibs5
  libakonadiprivate1 libboost-program-options1.38.0 libqimageblitz4
  libstrigiqtdbusclient0 mysql-server-core-5.1 plasma-dataengines-workspace
  plasma-widgets-workspace
The following packages have been kept back:
  nvidia-common
The following packages will be upgraded:
  alsa-utils computer-janitor computer-janitor-gtk k3b k3b-data
  language-pack-en language-pack-en-base language-pack-gnome-en
  language-pack-gnome-en-base libk3b6 libpulse-browse0 libpulse-mainloop-glib0
  libpulse0 libsasl2-2 libsasl2-modules modemmanager mozilla-thunderbird
  network-manager-gnome ntpdate pulseaudio pulseaudio-esound-compat
  pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-udev
  pulseaudio-module-x11 pulseaudio-module-zeroconf pulseaudio-utils
  python-fstab thunderbird
29 upgraded, 17 newly installed, 18 to remove and 1 not upgraded.
Need to get 40.2MB/43.4MB of archives.
After this operation, 7385kB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.

Most likely, the packages it wants to install through the updates dont play nice with the packages it wants to remove.  This is expected and common with an Alpha release.

This happens alot with Devede ..

---

### Post by castrojo on 2009-08-21
When new packages get uploaded that depend on new versions of stuff and those deps haven't been uploaded stuff things like this happens (which is to be expected in a development release)

Don't run dist-upgrades during dev releases, just run normal "apt-get upgrade" and when you see packages held back just wait a few hours and normally it works itself out the next time you upgrade. If a package is held back for a long time, then try "apt-get install whatever" and it'll usually be obvious why it was held back (It needed a new version of something that the upgrade doesn't catch or it wants to remove something old.) 

If you do that and it returns a long list of stuff that looks dangerous to remove then just hold off a day or two.

---

### Post by terry_gardener on 2009-08-21
i did the upgrade and copied the package names it removed over to the text editor. 

it errored on the update because of the k3d because it depends on kdebase-workspaces-bin but it errored when trying to install this dependent.  

fixed this by just removing k3b until the kdebase-workspaces-bin is fixed 

did autoclean and clean. 

then preceded to install the packages it removed back on the system.
which they seemed to install. 

i rebooted and now cant even get on the system. 

it boots normally to just before the gdm is about to appear and then lots of errors and kicks me to the terminal. 

sorry cant get errors as i am now using the main pc with jaunty.

---

### Post by terry_gardener on 2009-08-21
thanks whiprush and Seventh Reign
which i waited little longer before upgrading but these things happen on alphas.

---

### Post by fazza on 2009-08-21
Ok so I've just done the same thing (or at least I think that must have been what I typed - dist-upgrade). It then did a partial upgrade and tried to remove things... I naively decided to trust it this time around, the same as I have done for the past 4 years :S

Obviously, I needed those packages. One of the things it upgraded was the nvidia graphics driver from 180 to 185. But then the 185 module wasn't created, and X couldn't start. After tiny amounts of fiddling, I discovered I couldn't downgrade to 180, as that is now a transitional package. So I tried 173, but in the end, I still had to edit /etc/X11/xorg.conf and change the nvidia module to vesa (or whatever it actually is).

So now I have an installation in the same state as my old 8.10 - vesa graphics, no nvidia drivers working, and jockey not even detecting the card.

Don't get me wrong; I'm not ranting :P I just want to know:

Will this fix itself when more updates come or not? I want to know at this stage, because I only installed this system yesterday. It is my only running system. YES, I know I shouldn't do that, and especially shouldn't then complain that it's broken, so I'm not complaining. I just want to know if it will get fixed, or if I'm better off clean installing Jaunty again and leaving it at that.

Thanks :) Sorry for the really long, wordy and pointless post :P Mine are always like that ><

---

### Post by terry_gardener on 2009-08-21
fazza 

i have managed to get logged in and fix the problem with little help from your last post. which i thank you.
i changed the xorg.conf file to nv to get logged in and then i went to system - administration - hardware drivers and click the 185 drivers and then clicked activate. 
this redownloaded the drivers and installed them correctly.
and i rebooted and works ok now. 

hope this helps you get your 3d back.

---

### Post by fazza on 2009-08-22
Aha thank you, that worked! :D

Cheers, I'll remember next time not to do that dist-upgrade thing :P

So yours works now then?

---

### Post by terry_gardener on 2009-08-22
fazza 

yes mine is sorted now thanks
glad yours is back working also.

---

### Post by duanedesign on 2009-10-23
Here is a good post walking you through the process of determining if a package removed by a partial upgrade, should in fact be removed.

[http://ubuntuforums.org/showpost.php?p=8142730&postcount=101](http://ubuntuforums.org/showpost.php?p=8142730&postcount=101)

---

