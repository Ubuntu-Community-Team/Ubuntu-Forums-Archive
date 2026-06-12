---
title: "enable mp3 support"
date: 2008-06-15
forum: Installation &amp; Upgrades
---

### Post by Balvinder25 on 2008-06-15
Hi all,

I am a quite a new user to ubuntu and im just learning the trade of the game.;)
The issue that i have is i want to enable mp3 support in ubuntu but the i dont have access to internet at home., some isp problems ;(
I use ubuntu 7.10 by the way.
now is **there any way that i could download some codec installation files from out side and then take that home and install it.**
any help would be highly appreciated.
balvinder

---

### Post by 505 on 2008-06-15
Yes, there is, but it is not very nice. On the [RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats#head-6c1adf157cf1aaf47a391922036b3ecc98f01796) page you can find how to install MP3 support. It's the package "ubuntu-restricted-extras". You need to download the .deb for this package at [http://packages.ubuntu.com/gutsy/ubuntu-restricted-extras](http://packages.ubuntu.com/gutsy/ubuntu-restricted-extras) (click the i386 link at the bottom). However, this is just a meta-package, so you also need to download all .deb's listed under "recommends". Once done, double-click ubuntu-restricted-extras.deb and install. If it complains about missing packages you also need to download those.

---

### Post by Balvinder25 on 2008-06-15
thanks for that ..
would try to get that working..:confused:

---

### Post by oldos2er on 2008-06-15
Have a look at [http://nonetdebs.unixpod.com/](http://nonetdebs.unixpod.com/)

---

### Post by Eclipse. on 2008-06-15
> **505 said:**
> Yes, there is, but it is not very nice. On the [RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats#head-6c1adf157cf1aaf47a391922036b3ecc98f01796") page you can find how to install MP3 support. It's the package "ubuntu-restricted-extras". You need to download the .deb for this package at [http://packages.ubuntu.com/gutsy/ubuntu-restricted-extras](http://packages.ubuntu.com/gutsy/ubuntu-restricted-extras) (click the i386 link at the bottom). However, this is just a meta-package, so you also need to download all .deb's listed under "recommends". Once done, double-click ubuntu-restricted-extras.deb and install. If it complains about missing packages you also need to download those.

Thats an extremly long and complicated method, especially for beginners.

Easy method:-


Simply type this from the terminal:

sudo apt-get install ubuntu-restricted-extras

Or search for it in synaptic package manager.

That will install mp3 support, microsoft fonts, flash and a few other things.

---

### Post by gfg on 2008-06-15
> **Eclipse. said:**
> Thats an extremly long and complicated method, especially for beginners.

Easy method:-


Simply type this from the terminal:

sudo apt-get install ubuntu-restricted-extras

Or search for it in synaptic package manager.

That will install mp3 support, microsoft fonts, flash and a few other things.
Well it's hard to do that seeing as he has no working internet connection. He asked for a way to do it offline, and that is sort of complicated.

---

### Post by sundar_ima on 2009-04-13
> **gfg said:**
> Well it's hard to do that seeing as he has no working internet connection. He asked for a way to do it offline, and that is sort of complicated.
i thik following link will help you to solve the problem. [http://hacktolive.org/wiki/Ubuntu-restricted-extras_offline_installer]("http://hacktolive.org/wiki/Ubuntu-restricted-extras_offline_installer")

---

### Post by sundar_ima on 2009-04-21
you can also download the ubuntu restricted extra offline installer from here [http://rapidshare.com/files/222192270/ubuntu-restricted-extras_offline_installer.tar.gz]("http://rapidshare.com/files/222192270/ubuntu-restricted-extras_offline_installer.tar.gz") and if you want VLC to be installed with out internet connection then download VLC offline installer from here [http://rapidshare.com/files/222292699/VLC_offline_installer.tar.gz]("http://rapidshare.com/files/222292699/VLC_offline_installer.tar.gz")

---

### Post by apparle on 2009-04-21
See this

[http://ubuntuforums.org/showthread.php?t=310020](http://ubuntuforums.org/showthread.php?t=310020)

See my last entry for making an offline repository.
Then use the script to generate package list.
Use wget on a box with net connection.(wget is available for Windows as well)
bring the downloaded .deb packages on the ubuntu computer.
Goto the directory in konsole/terminal and install using command 
sudo dpkg -i *.deb

---

### Post by mac9416 on 2009-04-21
It might be best to use Keryx. It is an internetless package manager for Ubuntu.

---

