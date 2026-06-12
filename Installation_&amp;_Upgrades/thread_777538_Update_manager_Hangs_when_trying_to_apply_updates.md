---
title: "Update manager Hangs when trying to apply updates"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by bronxbomberz41 on 2008-05-01
My Girlfriend has an ACER lappy with very little ram so even Xubuntu runs a little slowly on it.  We just got our Hardy upgrades (i use Ubuntu) and I have solved any bugs for mine, but I can't for the life of me figure out why her Update Manager just hangs when she tries to apply the new updates.  Its never done that before Hardy. She has like 32 updates now to download and install and i imagine its only going to get bigger

If there is not an immediate fix what is a good workaround through the terminal?

Thank you!!

---

### Post by Pumalite on 2008-05-01
Check her connection and if OK.; then try changing Server (USA to Main as an example)

---

### Post by bronxbomberz41 on 2008-05-13
Hi again...the workaround to change the server worked temporarily but now that can't even opened now at this point and it is still hanging on the update manager.  Is there any other thing i could try??  please help!

---

### Post by Pumalite on 2008-05-13
Tell me in detail what happened.

---

### Post by bronxbomberz41 on 2008-05-13
When i go to "Software Sources" under the System menu and click on it, it does not open.  The mouse pointer acts like it is going to open it but it never opens.

The Red Arrow is on the top panel, indicating that there are updates for Xubuntu and whatever other programs are on the computer.  Upon clicking this the update manager populates the list (there are currently about 45 updates)  When I click on the "Apply" button the computer "thinks" for a minute but it does not ask for a password and it does not download or apply the updates.  You have to open up the System Monitor to kill the app.

That is what happens.  I appreciate your help so far, thank you!

---

### Post by Pumalite on 2008-05-13
Post:
cat /etc/apt/sources.list

---

### Post by bronxbomberz41 on 2008-05-15
Unfortunately thats not working either....I went to open sources.list and it did the same thing.  We are up to 67 updates that we can't install now.

---

### Post by Pumalite on 2008-05-15
Time to save data and do a clean install.

---

### Post by giancast on 2008-05-17
I am having the same exact problem. Update manager just hangs in there. I have internet connection since I am using the same laptop to post this reply.

Here is the output of my sources.list
giancarlo@giancarlo:~$ cat /etc/apt/sources.list
# 
# deb cdrom:[Xubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.1)]/ hardy main multiverse restricted universe

# deb cdrom:[Xubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.1)]/ hardy main multiverse restricted universe
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ubuntu.mirror.frontiernet.net/ubuntu/](http://ubuntu.mirror.frontiernet.net/ubuntu/) hardy main restricted
deb-src [http://ubuntu.mirror.frontiernet.net/ubuntu/](http://ubuntu.mirror.frontiernet.net/ubuntu/) hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntu.mirror.frontiernet.net/ubuntu/](http://ubuntu.mirror.frontiernet.net/ubuntu/) hardy-updates main restricted
deb-src [http://ubuntu.mirror.frontiernet.net/ubuntu/](http://ubuntu.mirror.frontiernet.net/ubuntu/) hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ubuntu.mirror.frontiernet.net/ubuntu/](http://ubuntu.mirror.frontiernet.net/ubuntu/) hardy universe
deb [http://ubuntu.mirror.frontiernet.net/ubuntu/](http://ubuntu.mirror.frontiernet.net/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ubuntu.mirror.frontiernet.net/ubuntu/](http://ubuntu.mirror.frontiernet.net/ubuntu/) hardy multiverse
deb [http://ubuntu.mirror.frontiernet.net/ubuntu/](http://ubuntu.mirror.frontiernet.net/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://ubuntu.mirror.frontiernet.net/ubuntu/](http://ubuntu.mirror.frontiernet.net/ubuntu/) hardy-security main restricted
deb-src [http://ubuntu.mirror.frontiernet.net/ubuntu/](http://ubuntu.mirror.frontiernet.net/ubuntu/) hardy-security restricted main multiverse universe #Added by software-properties
deb [http://ubuntu.mirror.frontiernet.net/ubuntu/](http://ubuntu.mirror.frontiernet.net/ubuntu/) hardy-security universe
deb [http://ubuntu.mirror.frontiernet.net/ubuntu/](http://ubuntu.mirror.frontiernet.net/ubuntu/) hardy-security multiverse
giancarlo@giancarlo:~$ 

Any help will be appreciated.

Thanks

---

### Post by Pumalite on 2008-05-17
Post the output of:
sudo apt-get update
sudo apt-get upgrade

---

### Post by giancast on 2008-05-17
giancarlo@giancarlo:~$ sudo apt-get update
[sudo] password for giancarlo: 
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy Release.gpg
Ign [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy/main Translation-en_US
Ign [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy/restricted Translation-en_US
Ign [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy/universe Translation-en_US
Ign [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy/multiverse Translation-en_US
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-updates Release.gpg
Ign [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-updates/main Translation-en_US
Ign [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-updates/restricted Translation-en_US
Ign [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-updates/universe Translation-en_US
Ign [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-updates/multiverse Translation-en_US
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-security Release.gpg
Ign [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-security/main Translation-en_US
Ign [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-security/restricted Translation-en_US
Ign [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-security/universe Translation-en_US
Ign [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-security/multiverse Translation-en_US
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy Release
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-updates Release
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-security Release
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy/main Packages
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy/restricted Packages
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy/restricted Sources
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy/main Sources
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy/multiverse Sources
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy/universe Sources
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy/universe Packages
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy/multiverse Packages
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-updates/main Packages
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-updates/restricted Packages
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-updates/restricted Sources
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-updates/main Sources
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-updates/multiverse Sources
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-updates/universe Sources
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-updates/universe Packages
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-updates/multiverse Packages
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-security/main Packages
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-security/restricted Packages
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-security/restricted Sources
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-security/main Sources
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-security/multiverse Sources
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-security/universe Sources
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-security/universe Packages
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-security/multiverse Packages
Reading package lists... Done

giancarlo@giancarlo:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  ssl-cert
The following packages will be upgraded:
  apparmor apparmor-utils apport apport-gtk bsdutils foomatic-filters friendly-recovery gdm gksu
  gnome-system-monitor gstreamer0.10-plugins-good gtk2-engines-pixbuf hal jockey-common
  jockey-gtk libcamel1.2-11 libebook1.2-9 libecal1.2-7 libedataserver1.2-9 libglib2.0-0
  libglib2.0-data libgnome-desktop-2 libgphoto2-2 libgphoto2-port0 libgtk2.0-0 libgtk2.0-bin
  libgtk2.0-common libhal-storage1 libhal1 libldap-2.4-2 libnautilus-extension1
  libpanel-applet2-0 libspeex1 libssl0.9.8 libtotem-plparser10 lshw mount mozilla-thunderbird
  openssh-client openssl python-apport python-problem-report python-virtkey sudo thunderbird
  transmission-common transmission-gtk update-manager update-manager-core util-linux
  util-linux-locales xserver-xorg-video-intel xulrunner-1.9
53 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 36.8MB of archives.
After this operation, 111kB of additional disk space will be used.
Do you want to continue [Y/n]? 

After I entered y then it proceeded to download packages (53) in my case, here are the last lines of the download:

Get:50 [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-updates/main transmission-gtk 1.06-0ubuntu5 [240kB]
Get:51 [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-updates/main transmission-common 1.06-0ubuntu5 [14.0kB]
Get:52 [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-updates/main xserver-xorg-video-intel 2:2.2.1-1ubuntu13 [336kB]
Get:53 [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-updates/main xulrunner-1.9 1.9~b5+nobinonly-0ubuntu4~8.04.0mt1 [7659kB]
Fetched 36.8MB in 2min11s (280kB/s)                                                              
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... Get:50 [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-updates/main transmission-gtk 1.06-0ubuntu5 [240kB]
Get:51 [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-updates/main transmission-common 1.06-0ubuntu5 [14.0kB]
Get:52 [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-updates/main xserver-xorg-video-intel 2:2.2.1-1ubuntu13 [336kB]
Get:53 [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-updates/main xulrunner-1.9 1.9~b5+nobinonly-0ubuntu4~8.04.0mt1 [7659kB]
Fetched 36.8MB in 2min11s (280kB/s)                                                              
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 


Now it is reading packages and unpacking packages, hopefully it will continue to install all the packages. I will double check and see if my download mirror in the update manager is pointing to the one the apt-get upgrade is downloading from.

Message is getting too big. 

Thanks for your help. It is installing right now.

---

### Post by Pumalite on 2008-05-17
You are welcome. Good luck.

---

