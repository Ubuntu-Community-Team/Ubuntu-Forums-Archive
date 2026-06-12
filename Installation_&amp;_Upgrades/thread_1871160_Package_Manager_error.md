---
title: "Package Manager error"
date: 2011-10-28
forum: Installation &amp; Upgrades
---

### Post by nipunreddevil on 2011-10-28
Recently a red color icon has started appearing my notification area.It says that "an error occured.Please run apt-get to see what is wrong.Error:Broken Count>0.This usually means that you have installed packages with unmet dependencies.I have pasted the output ```

nipun@nipun-Satellite-L305D:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libva-x11-1 libpurple-bin libxcb-xv0 uvcdynctrl libindicate-gtk3
  libiso9660-7 libdvbpsi7 libindicate5 libvlc5 libupnp3 libtelepathy-glib0
  indicator-messages libmatroska4 libxcb-keysyms1 libwebcam0 uvcdynctrl-data
  indicator-status-provider-pidgin app-install-data vlc-data
  indicator-status-provider-mc5 libvlccore4 python-pysqlite2 libvcdinfo0
  libebml3 libxcb-randr0 libindicator-messages-status-provider1
  desktop-file-utils:i386 libfaac0:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  desktop-file-utils:i386 libavutil-extra-51 libfaac0:i386
  libpostproc-extra-52 libswscale-extra-2 libutempter0 xbitmaps xterm
Suggested packages:
  xfonts-cyrillic
The following packages will be REMOVED:
  alsa-utils audacious audacious-plugins chromium-browser
  chromium-browser-l10n chromium-codecs-ffmpeg desktop-file-utils
  gecko-mediaplayer gnome-mplayer gstreamer0.10-ffmpeg
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-base
  gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly guvcview info libaa1
  libaudiofile0 libavcodec53 libavformat53 libavutil51 libcdparanoia0
  libdc1394-22 libdca0 libesd0 libfaad2 libgpm2 libgstfarsight0.10-0
  libopenal1 libpostproc52 libpurple0 libsdl-image1.2 libshout3 libswscale2
  libvte9 libxvidcore4 lubuntu-desktop lubuntu-software-center lxterminal
  mobilemediaconverter:i386 mozilla-plugin-vlc mplayer mtpaint nano parted
  pidgin pidgin-libnotify pidgin-microblog python-aptdaemon-gtk
  python-aptdaemon.gtkwidgets python-vte sessioninstaller synaptic
  ubuntu-standard vlc vlc-nox vlc-plugin-notify vlc-plugin-pulse
The following NEW packages will be installed:
  desktop-file-utils:i386 libavutil-extra-51 libfaac0:i386
  libpostproc-extra-52 libswscale-extra-2 libutempter0 xbitmaps xterm
0 upgraded, 8 newly installed, 58 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 913 kB of archives.
After this operation, 189 MB disk space will be freed.

```
I had recently fresh installed Lubuntu 11.10
It has also become unusually slow.I don't think that removing the mentioned packages would be a good idea as without them the system will be useless.What can be done?

---

### Post by nipunreddevil on 2011-10-28
SOlved it.Went to Synaptic.Saw Broken under custom filters.It showed a 32 bit application i had tried to install on my 64 bit system and had failed.So just removing it did the trick.

---

