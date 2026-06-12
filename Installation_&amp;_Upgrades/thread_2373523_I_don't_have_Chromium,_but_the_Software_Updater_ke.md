---
title: "I don't have Chromium, but the Software Updater keeps updating some extensions!"
date: 2017-10-07
forum: Installation &amp; Upgrades
---

### Post by New_buntu_89 on 2017-10-07
I have Ubuntu Mate 14.04, in case it matters. The Software Updater keeps giving me updates for some Chromium extensions, but I don't even have Chromium! The only browser I have currently installed is Firefox!

I checked the Synaptic Package Manager, searching for "chromium" in the quick filter. It says I have the two following packages:

Extra ffmpeg codecs for the Chromium Browser (chromium-codecs-ffmpeg-extra)
Web browser engine for Qt (codecs)  (oxideqt-codecs-extra)

Is there another application using these packages? How can I tell? Should I remove them??

Thanks in advance for the help!

---

### Post by Impavidus on 2017-10-07
chromium-codecs-ffmpeg-extra is a dependency of chromium. It may have been left on your system when you uninstalled chromium. I don't know about the other package. But if no other software depends on those packages, they should be autoremovable.```
sudo apt-get autoremove
```Make sure it doesn't list any packages you know you want to keep.

Or use synaptic, check status->autoremovable and uninstall the autoremovable packages.

---

### Post by vasa1 on 2017-10-07
I don't have chromium-browser installed and am sure I haven't ever installed it on my current system.
```
$ apt list --installed | grep -i chromium

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

chromium-codecs-ffmpeg-extra/xenial-updates,xenial-security,now 61.0.3163.100-0ubuntu0.16.04.1306 amd64 [installed,automatic]
$
```and
```
$ apt rdepends chromium-codecs-ffmpeg-extra
chromium-codecs-ffmpeg-extra
Reverse Depends:
  Depends: chromium-codecs-ffmpeg-extra-dbg (= 51.0.2704.79-0ubuntu0.16.04.1.1242)
 |Depends: chromium-browser (= 61.0.3163.100-0ubuntu0.16.04.1306)
  Replaces: chromium-codecs-ffmpeg
  Conflicts: chromium-codecs-ffmpeg
 |Depends: chromium-browser (= 49.0.2623.108-0ubuntu1.1233)
  Recommends: ubuntu-restricted-addons
  Recommends: kubuntu-restricted-addons
  Depends: chromium-codecs-ffmpeg-extra-dbg (= 49.0.2623.108-0ubuntu1.1233)
  Replaces: chromium-codecs-ffmpeg
  Conflicts: chromium-codecs-ffmpeg
$ 
```So maybe it has something to do with *ubuntu-restricted-addons* or *kubuntu-restricted-addons* unless one installs with the *--no-install-recommends* option which isn't on by default.

---

### Post by jeremy31 on 2017-10-07
I think ubuntu-restricted-addons is needed for playing DVDs

---

### Post by New_buntu_89 on 2017-10-11
So... what about the Web browser Engine for Qt?  The ffmpeg codecs are probably necessary for playing DVDs, according to jeremy31. I'll agree, since I vaguely remember having installed some random package from Chromium for something media-related. However, I do not recall ever having had Chromium on this computer. I might have though, since I've had it for close to 4 years now, and I did play around with it a little bit when I first installed Ubuntu. 

How safe is autoremove nowadays? Going by some old discussions online, it seems like it could remove necessary stuff, and people recommend doing backups.

---

### Post by Impavidus on 2017-10-11
Autoremove is quite safe, but not infallible. It will show you a list of packages it is going to remove. Look at that list and if there's anything suspicious on it, abort. Most of the time it will only show old kernels and headers (I used it for that a moment ago), maybe some dependencies of a program you recently removed. But sometimes people remove a meta-package, suddenly making much of their favourite software autoremovable.
```
sudo apt autoremove --purge
```

---

### Post by jeremy31 on 2017-10-11
The oxideqt-codecs-extra package is part of ubuntu-restricted-addons just like the chromium-codecs-ffmpeg-extra
```
apt depends ubuntu-restricted-addons
ubuntu-restricted-addons
  Recommends: gstreamer1.0-plugins-ugly
  Recommends: flashplugin-installer
    flashplugin-installer:i386
  Recommends: gstreamer1.0-plugins-bad
  Recommends: gstreamer1.0-libav
  Recommends: gstreamer1.0-fluendo-mp3
  Recommends: chromium-codecs-ffmpeg-extra
  Recommends: oxideqt-codecs-extra

```

---

