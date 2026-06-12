---
title: "ImageMagik Installation"
date: 2008-04-05
forum: Installation &amp; Upgrades
---

### Post by terence.termak on 2008-04-05
Hi

i'm  having problems installing imagemagick on my vps. It is running on ubuntu-he-6.06-x86, with Plesk control panel. i have downloaded ImageMagick.tar.gz and tried to install. The information i got was


root@lvps212-241-217-30:~/ImageMagick-6.4.0# ./configure
configuring ImageMagick 6.4.0
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking whether build environment is sane... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
[B]checking for gcc... no
checking for cc... no
checking for cl.exe... no
configure: error: no acceptable C compiler found in $PATH[/B]
See `config.log' for more details.
root@lvps212-241-217-30:~/ImageMagick-6.4.0#

I don't know how to install gcc, cc or cl.exe. basically i'm a newbie. any help would be appreiciated. Thanx.

---

### Post by scragar on 2008-04-05
there is a copy ofimagemagick in the repo's, why not use that?```
sudo apt-get install imagemagick
```

as for installing gcc etc try:```
sudo apt-get install build-essential
```

---

### Post by terence.termak on 2008-04-05
thanks, but thi is what i get

root@lvps212-241-217-30:~# sudo apt-get install imagemagick
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package imagemagick
root@lvps212-241-217-30:~# sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package build-essential
root@lvps212-241-217-30:~#

---

### Post by scragar on 2008-04-05
just download the i836 .deb installer from:
[http://packages.ubuntu.com/dapper/imagemagick](http://packages.ubuntu.com/dapper/imagemagick)

and install(from command line run:```
dpkg -i **filename/path**
```you may need to run ```
sudo apt-get install -f
```to fix any dependencies that remain unmatched.

---

