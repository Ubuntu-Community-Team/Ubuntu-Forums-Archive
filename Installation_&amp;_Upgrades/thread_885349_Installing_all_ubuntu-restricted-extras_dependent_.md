---
title: "Installing all ubuntu-restricted-extras dependent packages without internet"
date: 2008-08-10
forum: Installation &amp; Upgrades
---

### Post by Vyoma on 2008-08-10
I need to install the restricted codes/libraries/packages in a Ubuntu 8 installed PC which does not have an internet connection.

So, I wanted to get all the .deb files required for simple MP3 and video/dvd play back.

I wrote a download script (using the Synaptic Package Manager) based on the following package description on my Ubuntu installation.

```
$ sudo apt-cache depends ubuntu-restricted-extras
ubuntu-restricted-extras
  Recommends: flashplugin-nonfree
  Recommends: gstreamer0.10-ffmpeg
  Recommends: gstreamer0.10-pitfdll
  Recommends: gstreamer0.10-plugins-bad
  Recommends: gstreamer0.10-plugins-bad-multiverse
  Recommends: gstreamer0.10-plugins-ugly
  Recommends: gstreamer0.10-plugins-ugly-multiverse
  Recommends: libdvdread3
  Recommends: liblame0
  Recommends: msttcorefonts
    ttf-liberation
  Recommends: sun-java6-plugin
  Recommends: unrar
```

Since I had already had them all installed in my system, it took a while switching between 'apt-cache depends' and the Synaptic Package Manager's download script generator to get the following script:

```
#!/bin/sh
wget -c http://archive.ubuntu.com/ubuntu/pool/universe/c/cabextract/cabextract_1.2-2_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.124.0ubuntu2_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/g/gst-plugins-ugly-multiverse0.10/gstreamer0.10-plugins-ugly-multiverse_0.10.7-1_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/m/msttcorefonts/msttcorefonts_2.4_all.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/u/ubuntu-restricted-extras/ubuntu-restricted-extras_15.2_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/u/unrar-nonfree/unrar_3.7.8-1_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-plugin_6-06-0ubuntu1_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/libe/liberation-fonts/ttf-liberation_1.0-0ubuntu1_all.deb

wget -c http://archive.ubuntu.com/ubuntu/pool/universe/g/gstreamer0.10-ffmpeg/gstreamer0.10-ffmpeg_0.10.3-6_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/universe/g/gstreamer0.10-pitfdll/gstreamer0.10-pitfdll_0.9.1.1+cvs20080215-1_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins-bad0.10/gstreamer0.10-plugins-bad_0.10.6-5_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/g/gst-plugins-bad-multiverse0.10/gstreamer0.10-plugins-bad-multiverse_0.10.6-1_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins-ugly0.10/gstreamer0.10-plugins-ugly_0.10.7-3_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/g/gst-plugins-ugly-multiverse0.10/gstreamer0.10-plugins-ugly-multiverse_0.10.7-1_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/universe/libd/libdvdread/libdvdread3_0.9.7-8ubuntu1_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/l/lame/liblame0_3.97-0.0_i386.deb
```

Am I missing something?  Would the above cover all the basic packages required to play multimedia files? I just want to be sure, because once I get to that place, an internet connection is not possible (third world country) and I want to take all required .debs written on a CD and install myself.

Is there a list I can refer to that gives me all the dependencies for ubuntu-restricted-extras package that I can refer to, to create a download script, and use it to create the CD?

---

### Post by SF007 on 2008-09-10
At least for the flash package it will not work :( since that .deb file is just a "metapackage" that downloads the real binary file of Flash from adobe.com
So it will not work without internet, I tried it myself...

---

### Post by Vyoma on 2008-09-10
Oh - so when I try to install the flash DEB file on the PC without internet connection, it would fail because the installer actually in turn downloads a binary from Adobe.com ?

Is there a way I can get this binary and place it myself?

---

### Post by elbrun on 2008-12-04
I think there is more packages in **Ubuntu Restricted Extras**.To know this I freshly installed ubuntu 8.10  and checked.List is here.For intrepid there are 56 packages.I think number is the same for Hardy too.

List for 8.10 is here:
[http://userend.blogspot.com/2008/12/download-ubuntu-restricted-extras-for.html]("http://userend.blogspot.com/2008/12/download-ubuntu-restricted-extras-for.html")

I made this coz i'm an offline user!:p

---

### Post by sankz on 2009-01-06
> **elbrun said:**
> I think there is more packages in **Ubuntu Restricted Extras**.To know this I freshly installed ubuntu 8.10  and checked.List is here.For intrepid there are 56 packages.I think number is the same for Hardy too.

List for 8.10 is here:
[http://userend.blogspot.com/2008/12/download-ubuntu-restricted-extras-for.html]("http://userend.blogspot.com/2008/12/download-ubuntu-restricted-extras-for.html")

I made this coz i'm an offline user!:p

This might help you:
Chk out these ideaz here…

Installing packages without an internet connection:
[http://fasterthanlight.wordpress.com/2009/01/05/packgs-without-internet/](http://fasterthanlight.wordpress.com/2009/01/05/packgs-without-internet/)

And installing packages using Live CD:
[http://fasterthanlight.wordpress.com/2008/07/02/install-applications-from-live-cd/](http://fasterthanlight.wordpress.com/2008/07/02/install-applications-from-live-cd/)

---

