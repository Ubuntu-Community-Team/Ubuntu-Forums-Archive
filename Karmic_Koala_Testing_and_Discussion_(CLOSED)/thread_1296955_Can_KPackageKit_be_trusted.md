---
title: "Can KPackageKit be trusted?"
date: 2009-10-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by lovinglinux on 2009-10-21
KpackageKit has been working for a while now, but it seems it has issues with dependencies. For example, I wanted to install screenlets just because of the RingSensors widget. When I try to do that via command-line or Synaptic, there is a HUGE list of gnome dependencies:

```
alacarte capplets-data desktop-file-utils evolution-data-server     
  evolution-data-server-common gnome-about gnome-applets              
  gnome-applets-data gnome-control-center gnome-desktop-data          
  gnome-media gnome-media-common gnome-menus gnome-panel              
  gnome-panel-data gnome-session gnome-session-bin                    
  gnome-settings-daemon gnome-system-monitor gnome-user-guide         
  indicator-applet indicator-messages libatspi1.0-0 libcamel1.2-14    
  libcanberra-gtk-module libcanberra-gtk0 libdbusmenu-glib0
  libdbusmenu-gtk0 libdevkit-power-gobject1 libebackend1.2-0
  libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6
  libedataserver1.2-11 libedataserverui1.2-8 libegroupwise1.2-13
  libgdata-google1.2-1 libgdata1.2-1 libgnome-desktop-2-11
  libgnome-media0 libgnome-menu2 libgnome-window-settings1
  libgnomekbd-common libgnomekbd4 libgnomekbdui4 libgucharmap7
  libgweather-common libgweather1 libmetacity0 libnautilus-extension1
  libpanel-applet2-0 libpulse-mainloop-glib0 libtidy-0.99-0
  libunique-1.0-0 metacity metacity-common mousetweaks nautilus
  nautilus-data python-chardet python-evolution python-feedparser
  python-gmenu python-gnomeapplet python-gnomekeyring
  python-gtkmozembed python-rsvg python-utidylib python-wnck
  screen-resolution-extra screenlets ubuntu-system-service
```

But when I try to install via KPackageKit, it only install two dependencies, python-wnck and python-rsvg. So I tried it, but screenlets manager doesn't load.

I don't remember which applications I have installed with KPackageKit. Probably not many, but I'm afraid that I might have some packages with missing dependencies now.

Any idea why this happens? Is this default behavior of KPackageKit when installing gnome packages?

---

### Post by edin9 on 2009-10-21
KPackageKit is a joke ATM. It's essentially shipped broken. Don't trust it in any way! Use Terminal for everything in Kubuntu.

---

### Post by philinux on 2009-10-21
Here's what synaptic says in ubuntu.
[https://u1files.ubuntu.com/7fd0193e-5b50-4d4b-8b4a-27ff6b41f847](https://u1files.ubuntu.com/7fd0193e-5b50-4d4b-8b4a-27ff6b41f847)

---

### Post by philinux on 2009-10-21
Hey whats up with attachments. They get squished. You have to save as on your desktop to view.

---

### Post by lovinglinux on 2009-10-21
> **edin9 said:**
> KPackageKit is a joke ATM. It's essentially shipped broken. Don't trust it in any way! Use Terminal for everything in Kubuntu.

Thanks. I have exported my package selections with dpkg and then used it to install again, so the package manager asked for a couple of missing dependencies. I guess I'm good now.

> **philinux said:**
> Here's what synaptic says in ubuntu.

Thanks for the effort, but I can't read anything on such a small image. Besides, I'm running kde-minimal over Ubuntu command-line only installation, so my dependency list is completely different from someone running a vanilla Ubuntu.

---

### Post by edin9 on 2009-10-21
> **lovinglinux said:**
> Thanks. I have exported my package selections with dpkg and then used it to install again, so the package manager asked for a couple of missing dependencies. I guess I'm good now.



Thanks for the effort, but I can't read anything on such a small image. Besides, I'm running kde-minimal over Ubuntu command-line only installation, so my dependency list is completely different from someone running a vanilla Ubuntu.

Oh then maybe I was a little unfair. KPackageKit may have a lot of problems, but if you're not running the vanilla Kubuntu, then maybe it was another issue.

---

### Post by benjamimgois on 2009-10-21
Kpackagekit is so much broken that it shouldn't be included by default. You always have to use the comand-line on Kubuntu.

---

### Post by Zorael on 2009-10-21
apt is now set up by default to treat recommends as dependencies, so on non-GNOME installations you really have to use the terminal and tread carefully when installing stuff without getting a HEAP of gunk you don't need.

If you tell your package manager to only listen to real dependencies (aptitude install --without-recommends), you'll learn that sometimes dependencies aren't listed, or assumed to be already installed, or assumed tsuggestionso be installed as they're recommends/suggests. python packages have been a thorn in my side for some time now, after getting python tracebacks complaining about a missing module that wasn't a dependency of the package I installed (python-glade2, python-gnome, etc). The UPnP monitor tool that's in the repository needs gnome icons to start at all. etc.

Try installing Firefox without getting Pulseaudio, for one. I think installing the Flash installer will get you Pulse too. Unless you parse the list of what aptitude would install and explicitly tell it to leave pulse alone;
```
$ sudo aptitude install -P firefox pulseaudio_
```
Alternatively use --without-recommends and go through the list of packages that are now listed as being recommended or suggested, and see if there's anything obvious in there that you want at the same time. And if so, just add it to the line.
```
$ sudo aptitude install --without-recommends -P sun-java6-jre sun-java6-plugin
```

---

### Post by lovinglinux on 2009-10-21
> **Zorael said:**
> apt is now set up by default to treat recommends/suggestions as dependencies, so on non-GNOME installations you really have to use the terminal and tread carefully when installing stuff without getting a HEAP of gunk you don't need.

If you tell your package manager to only listen to real dependencies (aptitude install --without-recommends), you'll learn that sometimes dependencies aren't listed, or assumed to be already installed, or assumed to be installed as they're recommends/suggests. python packages have been a thorn in my side for some time now, after getting python tracebacks complaining about a missing module that wasn't a dependency of the package I installed (python-glade2, python-gnome, etc). The UPnP monitor tool that's in the repository needs gnome icons to start at all. etc.

Try installing Firefox without getting Pulseaudio, for one. I think installing the Flash installer will get you Pulse too. Unless you parse the list of what aptitude would install and explicitly tell it to leave pulse alone;
```
$ sudo aptitude install -P firefox pulseaudio_
```
Alternatively use --without-recommends and go through the list of packages that are now listed as being recommended or suggested, and see if there's anything obvious in there that you want at the same time. And if so, just add it to the line.
```
$ sudo aptitude install --without-recommends -P sun-java6-jre sun-java6-plugin
```

Thank you. Very good info. Do you know why the* --without-recommends* flag doesn't work with apt-get, just aptitude?

---

### Post by philinux on 2009-10-21
apt-get uses this flag --no-install-recommends

---

### Post by lovinglinux on 2009-10-21
> **philinux said:**
> apt-get uses this flag --no-install-recommends

Thank you. I tried something like that a couple of days ago, but it wasn't working. I guess I must have used a mistyped flag.

---

### Post by ranch hand on 2009-10-21
I have used package kit in a couple of other distros where they have used it for a while.  Doesn't work well there either.

---

### Post by NormanFLinux on 2009-10-21
In Kubuntu, I just run Synaptic. Its the best package manager. KPackagekit just don't work for me.

---

### Post by ranch hand on 2009-10-21
+1

---

### Post by inportb on 2009-10-21
> **Zorael said:**
> apt is now set up by default to treat recommends/suggestions as dependencies, so on non-GNOME installations you really have to use the terminal and tread carefully when installing stuff without getting a HEAP of gunk you don't need.

Whoa? And why is this a useful default?

---

### Post by seeker5528 on 2009-10-21
> **inportb said:**
> Whoa? And why is this a useful default?

Suggested packages are not treated as dependencies.
Recommended packages are.


In the simple view:

Commonly suggested packages would be packages that are independent of the package being installed but considered desirable and the recommended packages would be packages that enhance functionality of the package being installed.

Of course the package maintainers have their own ideas about what the relative importance of things are, so in the real world it gets a little more complicated than that, but you get the idea.

Later, Seeker

---

### Post by Seventh Reign on 2009-10-21
KPackagekit seemed to show alot of promise and potential, but it has never once lived up to the hype.

I will however say that as bad as it is, it IS quite a bit better than Portage .. or whatever Sabayon is calling their Package Manager lately.

---

### Post by ranch hand on 2009-10-21
> **Seventh Reign said:**
> KPackagekit seemed to show alot of promise and potential, but it has never once lived up to the hype.

I will however say that as bad as it is, it IS quite a bit better than Portage .. or whatever Sabayon is calling their Package Manager lately.
And about on par with Adept, that sorry thing KDE has been using.

---

### Post by Zorael on 2009-10-21
> **seeker5528 said:**
> Suggested packages are not treated as dependencies.
Recommended packages are.
I stand corrected.

"Considered desirable" is a good way of putting it. The crux arises when a package is desirable in one environment and not in another, the obvious example being Ubuntu vs Kubuntu and their environment-specific utilities and backends. I don't want pulse, nor gvfs, nor all those gconf tools and libraries. Just as I imagine you don't want Akonadi (but you get it anyway, harr).

You have to keep an active watch out for stowaways. Or use --without-recommends/--no-install-recommends and instead hunt for missing functionality.

---

### Post by ranch hand on 2009-10-21
I am not sure where apt is configured this way.  It most certainly is not in Hardy through Karmic Ubuntu, nor under the Xubuntu that I have used.

It has all acted the same.  It lists the suggested and recommended packages and then leaves it up to your lack of discretion.

Kubuntu may be different but I don't know for sure.  I have had it on my box, at times but I am not really KDE compatible.  I try to keep a KDE on here, in case someone wants to see it but it is usually Mandriva.  I find it is really hard to try apt on Mandriva.

---

### Post by Slug71 on 2009-10-21
The biggest problem with Packagekit/Kpackagekit at the moment on deb systems is with debconf at the moment. Packagekit/Kpackagekit doesnt support it at the moment but it is a work in progress. Still in the planning stages last i heard though. It does have non-interactive debconf support though but i think that is in the 0.5 series if im not mistaken.

The 0.5.0 series also has many changes/new features but is still in development. Wont make it for Karmic but will for 10.04.

KDE 4.4 is also dropping Kpackage for Kpackagekit, so expect much better integration from there on.

---

### Post by Slug71 on 2009-10-21
I just installed Kpackagekit on Mandriva because im not a big fan of Rpmdrake but it keeps crashing.

Im thinking that is an issue with Mandriva though.

---

### Post by screaminj3sus on 2009-10-22
Recently tried kubuntu 9.10, god kpackagekit is just beyond terrible. Extremely buggy to say the least.

---

### Post by Zorael on 2009-10-22
> **ranch hand said:**
> I am not sure where apt is configured this way.  It most certainly is not in Hardy through Karmic Ubuntu, nor under the Xubuntu that I have used.

It has all acted the same.  It lists the suggested and recommended packages and then leaves it up to your lack of discretion.

Is this an upgraded system? Mine is a fresh Karmic installation and it behaves this way.
```
apt (0.7.14ubuntu1) intrepid; urgency=low

  [ Michael Vogt ]
  * enable installation of recommends by default
  * debian/apt.conf.ubuntu:
    - remove APT::Install-Recommends-Sections (no longer needed)
  * merged from debian/sid, remaining changes:
    - authentication-reliable branch (to be merged into debian soon)
    - mirror:// uri branch (breaks ABI in debian, not merged yet)
    - apport failure reporting
    - show warning on apt-get source with 'Vcs-' header
    - proxy detection from gconf in apt.cron

...

 -- Michael Vogt <mvo@debian.org>  Wed, 28 May 2008 15:19:12 +0200
```

---

### Post by zekopeko on 2009-10-22
> **Slug71 said:**
> The biggest problem with Packagekit/Kpackagekit at the moment on deb systems is with debconf at the moment. Packagekit/Kpackagekit doesnt support it at the moment but it is a work in progress. Still in the planning stages last i heard though. It does have non-interactive debconf support though but i think that is in the 0.5 series if im not mistaken.

The 0.5.0 series also has many changes/new features but is still in development. Wont make it for Karmic but will for 10.04.

KDE 4.4 is also dropping Kpackage for Kpackagekit, so expect much better integration from there on.

I highly doubt that this has anything to do with what the OP posted.
I get a feeling that you don't know exactly what Package-kit is and what it does and how it's related to debconf. But you buy the hype.

---

### Post by ranch hand on 2009-10-22
> **Zorael said:**
> Is this an upgraded system? Mine is a fresh Karmic installation and it behaves this way.
```
apt (0.7.14ubuntu1) intrepid; urgency=low

  [ Michael Vogt ]
  * enable installation of recommends by default
  * debian/apt.conf.ubuntu:
    - remove APT::Install-Recommends-Sections (no longer needed)
  * merged from debian/sid, remaining changes:
    - authentication-reliable branch (to be merged into debian soon)
    - mirror:// uri branch (breaks ABI in debian, not merged yet)
    - apport failure reporting
    - show warning on apt-get source with 'Vcs-' header
    - proxy detection from gconf in apt.cron

...

 -- Michael Vogt <mvo@debian.org>  Wed, 28 May 2008 15:19:12 +0200
```

```

ker@ker-desktop:~$ apt-get -v
apt 0.7.23.1ubuntu2 for amd64 compiled on Oct 15 2009 19:26:30
Supported modules:
*Ver: Standard .deb
*Pkg:  Debian dpkg interface (Priority 30)
 S.L: 'deb' Standard Debian binary tree
 S.L: 'deb-src' Standard Debian source tree
 Idx: Debian Source Index
 Idx: Debian Package Index
 Idx: Debian Translation Index
 Idx: Debian dpkg status file
ker@ker-desktop:~$ 

```

---

### Post by Slug71 on 2009-10-22
> **zekopeko said:**
> I highly doubt that this has anything to do with what the OP posted.
I get a feeling that you don't know exactly what Package-kit is and what it does and how it's related to debconf. But you buy the hype.

Youre entitled to think what you want.

---

### Post by ranch hand on 2009-10-22
> **zekopeko said:**
> i highly doubt that this has anything to do with what the op posted.
I get a feeling that you don't know exactly what package-kit is and what it does and how it's related to debconf. But you buy the hype.
+1

---

### Post by Slug71 on 2009-10-22
[http://dantti.wordpress.com/2009/10/14/packagekit-and-the-road-to-debian/](http://dantti.wordpress.com/2009/10/14/packagekit-and-the-road-to-debian/)

---

### Post by ranch hand on 2009-10-22
> **Slug71 said:**
> [http://dantti.wordpress.com/2009/10/14/packagekit-and-the-road-to-debian/](http://dantti.wordpress.com/2009/10/14/packagekit-and-the-road-to-debian/)
And this in some way counteracts the fact that the bugger just doesn't work?

---

### Post by Slug71 on 2009-10-22
> **ranch hand said:**
> And this in some way counteracts the fact that the bugger just doesn't work?

Nope, just some intersting reading.

---

