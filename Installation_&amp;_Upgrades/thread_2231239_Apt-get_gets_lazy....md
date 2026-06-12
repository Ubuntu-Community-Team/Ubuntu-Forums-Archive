---
title: "Apt-get gets lazy... :/"
date: 2014-06-24
forum: Installation &amp; Upgrades
---

### Post by checoimg on 2014-06-24
I did :

```


sudo apt-get install gimp gmic-gimp wget audacity gcc make inkscape cheese flac vlc alsa-tools wireshark ntfsprogs gdb rsync inkscape* xchat exiftool nautilus* git transmission-gtk gimp* totem* lynx ufraw ffmpeg gthumb mono* tasque wavpack docky mkvtoolnix midori epiphany udisks csound fliudsynth icecast yafray* gwget guitarix dvgrab freqtweak csync openexr irssi* goobox gnome-blog unison-gtk zsync povray kdenlive rosegraden recordmydesktop gccmakedep cd-paranoia leechcraft* openLP bluefish avidemux-gtk gnome-clocks ffmpeg2theora ffmpegthumbnailer avidemux* ladspa*


```

And nothing.... this girl won't kiss me :(

Maybe a Auto-repair can get her to reason...

TY for your attention :)

---

### Post by checoimg on 2014-06-24
```
carlosjcheco@frogui:~$ sudo apt-get install -f
[sudo] password for carlosjcheco: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  kde-l10n-engb
Use 'apt-get autoremove' to remove it.
The following extra packages will be installed:
  oxygen-icon-theme
The following NEW packages will be installed:
  oxygen-icon-theme
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0 B/28.9 MB of archives.
After this operation, 31.1 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 235199 files and directories currently installed.)
Preparing to unpack .../oxygen-icon-theme_4%3a4.13.0-0ubuntu1_all.deb ...
Unpacking oxygen-icon-theme (4:4.13.0-0ubuntu1) ...
dpkg-deb (subprocess): decompressing archive member: lzma error: compressed data is corrupt
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing archive /var/cache/apt/archives/oxygen-icon-theme_4%3a4.13.0-0ubuntu1_all.deb (--unpack):
 cannot copy extracted data for './usr/share/icons/oxygen/256x256/apps/qelectrotech.png' to '/usr/share/icons/oxygen/256x256/apps/qelectrotech.png.dpkg-new': unexpected end of file or stream
Processing triggers for hicolor-icon-theme (0.13-1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/oxygen-icon-theme_4%3a4.13.0-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
carlosjcheco@frogui:~$
```

---

### Post by checoimg on 2014-06-24
Thisn is obvously a "Loop-Hole" PAckge won't install because Package system is broken... How can I break this loop ? The Packge manager should let me Purge the broken packges Duh...

---

### Post by ian-weisser on 2014-06-24
Well, the error message seems pretty specific. You are trying to install a corrupt package.

> **checoimg said:**
> 
Preparing to unpack .../oxygen-icon-theme_4%3a4.13.0-0ubuntu1_all.deb ...
Unpacking oxygen-icon-theme (4:4.13.0-0ubuntu1) ...
dpkg-deb (subprocess): decompressing archive member: **[COLOR=#ff0000]lzma error: compressed data is corrupt[/COLOR]**
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing archive /var/cache/apt/archives/oxygen-icon-theme_4%3a4.13.0-0ubuntu1_all.deb (--unpack):
 cannot copy extracted data for './usr/share/icons/oxygen/256x256/apps/qelectrotech.png' to '/usr/share/icons/oxygen/256x256/apps/qelectrotech.png.dpkg-new': **[COLOR=#ff0000]unexpected end of file or stream[/COLOR]**


You're right that the package manager does not easily delete corrupt packages.

One easy way to fix the problem is to simply delete /var/cache/apt/archives/oxygen-icon-theme_4%3a4.13.0-0ubuntu1_all.deb so apt-get will download a fresh (non-corrupt) copy.

---

### Post by checoimg on 2014-06-24
> **ian-weisser said:**
> Well, the error message seems pretty specific. You are trying to install a corrupt package.



You're right that the package manager does not easily delete corrupt packages.

One easy way to fix the problem is to simply delete /var/cache/apt/archives/oxygen-icon-theme_4%3a4.13.0-0ubuntu1_all.deb so apt-get will download a fresh (non-corrupt) copy.

Thanks for the tip :) , I just decided to make a clean install of 14.04 since I don't want more problems.

---

