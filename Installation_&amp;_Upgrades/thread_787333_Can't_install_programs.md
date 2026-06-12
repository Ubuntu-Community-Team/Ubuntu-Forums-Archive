---
title: "Can't install programs"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by mercury_may2112 on 2008-05-08
I tried doing:

sudo apt-get install vlc

But what I got was:

The following packages have unmet dependencies:
  kmplayer-konq-plugins: Depends: konqueror but it is not going to be installed
  konq-plugins: Depends: konqueror (>= 4:3.5.8-1) but it is not going to be installed
  konqueror-nsplugins: Depends: konqueror but it is not going to be installed
  strigi-applet: Depends: konqueror but it is not going to be installed
  vlc: Depends: libiso9660-5 but it is not going to be installed
       Depends: libsdl-image1.2 (>= 1.2.5) but it is not going to be installed
       Depends: libtar but it is not going to be installed
       Depends: libvcdinfo0 (> 0.7.23) but it is not going to be installed
       Depends: libvlc0 (>= 0.8.6.release.e+x264svn20071224+faad2.6.1) but it is not going to be installed
       Depends: libwxbase2.6-0 (>= 2.6.3.2.2) but it is not going to be installed
       Depends: libwxgtk2.6-0 (>= 2.6.3.2.2) but it is not going to be installed
       Depends: libxosd2 (>= 2.2.13) but it is not going to be installed
       Depends: ttf-dejavu but it is not going to be installed
       Depends: vlc-nox (= 0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3) but it is not going to be installed
       Depends: vlc-plugin-pulse but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

I also have Kubuntu desktop installed with sudo apt-get install kubuntu-desktop and I want to get rid of it. how would I do that?

---

### Post by tamoneya on 2008-05-08
```
sudo apt-get -f install vlc
sudo apt-get remove kubuntu-desktop
```
Should solve both problems.

---

