---
title: "Media codecs installation and installation of vlc media player"
date: 2011-09-26
forum: Installation &amp; Upgrades
---

### Post by cyberpunky2j on 2011-09-26
hi,i have been using ubuntu 11.04 for the past few days.but unfortunately my pc does not have an internet connection.can anyone suggest how can i install the codecs required to play media files or install vlc media player on my ubuntu offline?thanks in advance for your answers.

---

### Post by LepeKaname on 2011-09-26
I think it is just faster if you can connect even for few minutes your computer to internet. But if that is not possible, then you can try this:

Option 1) If you have "apt-rdepends" installed, you can issue this command:

```
apt-rdepends vlc vlc-data vlc-plugin-pulse | grep ^[a-z] | sort > vlc_packages
```

Get your installed packages:

```
dpkg --get-selections | awk '{ print $1 '} > installed
```

Get only those you need:

```
diff vlc_packages installed | grep "^<" > vlc_required
```

Save the vlc_required file into a USB drive.

For each of those files, check on "aptitude" or "synaptics" which is the  current version. And keep that info as well.

NOTE: For previous steps you don't need internet connection. 

Go to a place with internet and in google, search like this:

```
site:archive.ubuntu.com PACKAGE_NAME
```

Download the *.deb files you need which match the version you got before.
Be sure the files you are downloading match your CPU.

Take them home and put them in one directory (e.g. vlc_downloaded) and issue:

```
cd vlc_downloaded; dpkg -i ./*
```

Option 2) You can use [AptOnCD]("http://aptoncd.sourceforge.net/")
I haven't t tried it but it may be faster than option 1. I'm not sure what you need to install it.

Option 3) You can buy the universe repository from: [http://thelinuxstore.ca](http://thelinuxstore.ca)

I hope it helps.

---

