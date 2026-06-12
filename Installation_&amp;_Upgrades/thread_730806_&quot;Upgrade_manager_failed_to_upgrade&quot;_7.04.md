---
title: "&quot;Upgrade manager failed to upgrade&quot; 7.04 to 7.10?"
date: 2008-03-21
forum: Installation &amp; Upgrades
---

### Post by dirky on 2008-03-21
Hi,
recently I upgraded from 6.10 to 7.04 on my AMD 64 3000 PC. Everything seemed to go to plan.
Last night I decided to move from 7.04 to 7.10.

All went as expected apart from a couple of failed upgrades for Open office I think it was,
then near the end I got the following error:-

[I]Upgrade manager failed to upgrade - send info
Could not install Upgrades.
The upgrade aborts now. Your system could be in an unstable state. A recovery will run now.
(dpkg --configure -a)
[/I]

A recovery did not seem to run from what I could tell. So I took a deep breath and rebooted.
Surprisingly it seems to run and MythTV works mostly (which was one of the reasons I upgraded)

So my question is, how can I tell what failed?
How can I check that it is running ok and that all packages are ok?

Should I wipe the system and do a clean install from CD? Obviously I'd rather not do this.

Many thanks
Mike

---

### Post by Pumalite on 2008-03-21
Post output of:
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade

---

### Post by dirky on 2008-03-21
> **Pumalite said:**
> Post output of:
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade



mike@myth1:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libmpich1.0c2 libopenexr2c2a mythmusic libarts1c2a libxmlsec1 libzzip-0-12 kdelibs4c2a libgsf-gnome-1-114 apache2-utils openoffice.org-style-default libneon25
  libmyth-0.20 mythphone mytharchive mythbrowser feisty-wallpapers libstlport5.1 libxmlsec1-openssl mytharchive-data python-mysqldb fftw2 kdelibs-data
  libjack0.100.0-0 libstlport4.6c2 mythdvd libxmlsec1-nss liblualib50 libpostproc0d libcarp-clan-perl mythgallery gcc-3.4-base mythgame libavformat0d libavformat1d
  dvdauthor mythflix linux-headers-2.6.20-16-generic python-imaging libcurl3 libavahi-qt3-1 libxine-main1 libswscale1d mythcontrols ffmpeg libflac7
  linux-headers-2.6.20-16 feisty-session-splashes libcdaudio1 libxml-simple-perl libjasper-1.701-1 libimage-size-perl libavcodec0d mythweather mythvideo libgs-esp8
  liblua50 libg2c0 mythnews libquicktime0 gstreamer0.10-gnomevfs libmyth-python perlmagick x-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
mike@myth1:~$ 



mike@myth1:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Translation-en_US
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Sources
Fetched 5B in 0s (6B/s)  
Reading package lists... Done
mike@myth1:~$ 





mike@myth1:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  mythvideo
The following packages will be upgraded:
  openoffice.org-help-en-us unzip
2 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 154kB/11.1MB of archives.
After unpacking 3391kB of additional disk space will be used.
Do you want to continue [Y/n]? 




Thanks for your reply,

Mike

---

### Post by Pumalite on 2008-03-21
You are welcome. I assume you auto remove?

---

### Post by dirky on 2008-03-21
> **Pumalite said:**
> You are welcome. I assume you auto remove?

You mean on the upgrade stage? I didn't do anything, I just replied 'n' for now.
Do you think the system looks ok? I'm wondering if the upgrade had in fact finished and the error I received was false?

thanks

Mike

---

### Post by Pumalite on 2008-03-21
Run:
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade

---

### Post by dirky on 2008-03-21
> **Pumalite said:**
> Run:
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade

Ok, all done.
Can I assume I have a good upgrade to 7.10?
Anything else I should check?

thanks again,

Mike

---

### Post by Pumalite on 2008-03-21
You are A-OK.

---

### Post by Gadgetman on 2008-03-22
I had a similar problem, where mythvideo "was held back" even after issuing the following:-
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade

However the following final solved the issue:-
apt-get --reinstall install mythvideo

---

