---
title: "Install VLC Player From Local  Directory"
date: 2008-07-24
forum: Installation &amp; Upgrades
---

### Post by RealG187 on 2008-07-24
Okay before I installed VLC player and then I copied all the DEBs out of /var/cache/apt/arcives

This was before my hard drive failed.

I am on my new system and when I click the package it says something about a dependency. I install that and it just keeps going.

Is there a simple way I can install VLC player (or any program) and it's dependencies from a local folder.

I am going insane trying to install this one program.

[http://www.newlinuxuser.com/howto-use-dpkg-to-install-deb-files/](http://www.newlinuxuser.com/howto-use-dpkg-to-install-deb-files/)

> mpg@MIKED5:/var/cache/apt/archives$ sudo dpkg -i vlc_0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3_i386.deb
(Reading database ... 97030 files and directories currently installed.)
Preparing to replace vlc 0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3 (using vlc_0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3_i386.deb) ...
Unpacking replacement vlc ...
dpkg: dependency problems prevent configuration of vlc:
 vlc depends on libiso9660-5; however:
  Package libiso9660-5 is not installed.
 vlc depends on libsdl-image1.2 (>= 1.2.5); however:
  Package libsdl-image1.2 is not installed.
 vlc depends on libtar; however:
  Package libtar is not installed.
 vlc depends on libvcdinfo0 (>> 0.7.23); however:
  Package libvcdinfo0 is not installed.
 vlc depends on libvlc0 (>= 0.8.6.release.e+x264svn20071224+faad2.6.1); however:
  Package libvlc0 is not installed.
 vlc depends on libwxbase2.6-0 (>= 2.6.3.2.2); however:
  Package libwxbase2.6-0 is not installed.
 vlc depends on libwxgtk2.6-0 (>= 2.6.3.2.2); however:
  Package libwxgtk2.6-0 is not installed.
 vlc depends on libxosd2 (>= 2.2.13); however:
  Package libxosd2 is not installed.
 vlc depends on ttf-dejavu; however:
  Package ttf-dejavu is not installed.
 vlc depends on vlc-nox (= 0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3); however:
  Package vlc-nox is not installed.
 vlc depends on vlc-plugin-pulse; however:
  Package vlc-plugin-pulse is not configured yet.
dpkg: error processing vlc (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 vlc
mpg@MIKED5:/var/cache/apt/archives$ 

It says all sorts of packages are not installed, but they are in the directory, it shold just install them and them install VLC

---

### Post by Frak on 2008-07-27
sudo apt-get install -f

---

### Post by RealG187 on 2008-07-28
I think this might do it:
[http://kubuntuforums.net/forums/index.php?topic=3087550.0](http://kubuntuforums.net/forums/index.php?topic=3087550.0)

I have the files ready and will try the next time I need to install it...

but what would the -f option do?

---

