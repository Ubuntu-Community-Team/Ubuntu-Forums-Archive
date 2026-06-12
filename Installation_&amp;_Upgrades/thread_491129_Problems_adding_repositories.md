---
title: "Problems adding repositories"
date: 2007-07-03
forum: Installation &amp; Upgrades
---

### Post by danie.thom on 2007-07-03
Hi 

I am having trouble with my feisty installation.  I get error messages when I try to install tools like mplayer.  (The error states that dependency packages cannot be downloaded.  I have updated the /etc/apt/sources.list file to allow universe and multiverse repositories, and I tried enabling the repositories using synaptic.  When i reload the repositories, I get the following error messages:

pt-get  -o=dir::etc=/usr/lib/easyubuntu/conf -o=dir::etc::sourcelist=sources.list update
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_US
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_US
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_US
Get:2 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release.gpg [189B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/free Translation-en_US
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/non-free Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_US
Get:5 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release [2182B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_US
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/non-free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages
Get:7 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/free Packages [1867B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Sources
Get:8 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/non-free Packages [1597B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Sources
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages [193kB]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
  Sub-process gzip returned an error code (1)
error: 
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages [193kB]
error: 
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
  Sub-process gzip returned an error code (1)
error: 
Fetched 5841B in 6s (852B/s)
Reading package lists...

error: 
gzip: stdin: not in gzip format
Executing: 
apt-get  -o=dir::etc=/usr/lib/easyubuntu/conf -o=dir::etc::sourcelist=sources.list --yes --allow-unauthenticated  install gstreamer0.10-pitfdll w32codecs
Reading package lists...

Can anyone please help?

---

### Post by Gremlinzzz on 2007-07-03
I'm not sure but if your desperate you can try deleting  everything in the source list click save  then reinstall it.
this is what i use medibuntu
[https://help.ubuntu.com/community/RestrictedFormats/NonNativeCodecs?highlight=%28codecs%29](https://help.ubuntu.com/community/RestrictedFormats/NonNativeCodecs?highlight=%28codecs%29)

---

### Post by Gremlinzzz on 2007-07-03
Don't forget too
sudo apt-get update
sudo apt-get upgrade

---

### Post by danie.thom on 2007-07-04
Hi

I was able to fix the problem.  I cleared the /etc/apt/sources.list file, and used Synaptic to rescan all the repositories.  

Thanks for the help.:D

---

