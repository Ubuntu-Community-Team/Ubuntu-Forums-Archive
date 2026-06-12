---
title: "A Huge Problem!"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by white_eagle-mk on 2008-04-30
Ok, I am very tired from this but I'll start from the beggining:

I had Gutsy 7.10 going on perfectly and I decided to upgrade to Hardy yesterday, so every package (except bittorent_*****.deb, my ISP's firewall constantly threwed it out, or there was some error in the ubuntu servers -- I don't know) was downloaded, so I deselected that bittorent package and went to installing and when the packages were configuring (around 20%) an error came out (I was upgrading with the update-manager) it was complaining that a package which was configuring in the update (I really don't remember the name) was trying to overwrite  a file which was already installed by another package earlier (that another package was gnome-screensaver) and it only offered a close button...
**Thats when the real problems began:**
I saw a button in the notification area which asked for me to restart (I could still to administrative things going from my account whiteeagle ) and I went to IRC and asked there what should I do. 
LjL i think told me to type a few commands in the terminal and I discovered that I had 2 kernels installed (hardy was half installed as I mentioned above) and he also told me to reboot to recovery mode and login as root and do apt-get -f install and  then dpkg --configure -a till the messages stop appearing. This messages appeared:
```
root@whiteeagle-laptop:~# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libclan2c2a-sound vnc-common libclanlib2c2a classpath-gtkpeer
  libzipios++0c2a classpath-common cacao classpath hermes1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  emesene enigma-data glipper
0 upgraded, 0 newly installed, 3 to remove and 907 not upgraded.
6 not fully installed or removed.
Need to get 0B of archives.
After unpacking 23.2MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ...   203996 files and directories currently installed.)
Removing emesene ...
The generated cache was invalid.
dpkg: error processing emesene (--remove):
 subprocess post-removal script returned error exit status 1
Removing enigma-data ...
The generated cache was invalid.
dpkg: error processing enigma-data (--remove):
 subprocess post-removal script returned error exit status 1
Removing glipper ...
The generated cache was invalid.
dpkg: error processing glipper (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 emesene
 enigma-data
 glipper
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@whiteeagle-laptop:~# dpkg --configure -a
Setting up alacarte (0.11.5-0ubuntu1) ...
The generated cache was invalid.
dpkg: error processing alacarte (--configure):
 subprocess post-installation script returned error exit status 1
Setting up apport (0.108) ...
The generated cache was invalid.
dpkg: error processing apport (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.
dpkg: error processing apport-gtk (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 alacarte
 apport
 apport-gtk

``` 
I tried that bunch of times, it didn't help. So I rebooted into the GUI luckily, but from the whiteeagle account I couldn't do anything administrative because sudo (and gksudo) complained that they couldn't find the whiteeagle-laptop host, and I also couldn't connect to the internet because I connect to it via ath0 and a keyring manager must be unlocked so it could have access to the network key, but it couldn't because of the reasons above. So, I rebooted the x session and logged in as root, I was very happy to find out that I could connect to the internet from there (I am writing from my root account now) and asked in #ubuntu what should I do. They recommended to me to do a fresh install, but my cd-rom doesn't work so I could try out [some other]("https://help.ubuntu.com/community/Installation/FromLinux") way of reinstalling Hardy. Some other guy told me to look in my /etc/hosts file to correct the problems with the unknown host when in my account, my hosts file looked like this: ```
 # The following lines are desirable for IPv6 capable hosts

::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts 
```
 
and he told me to make it look like this: ```
127.0.0.1	whiteeagle
127.0.1.1	whiteeagle.home.gateway	whiteeagle
# The following lines are desirable for IPv6 capable hosts

::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts 
```
and then to log back into my primary account and see what happens... The same happened, and I logged back in into root (because I don't have internet access with that account anymore).... :( :( :( ](*,) ](*,) ]

What do you recommend me to do, can I fix the dependency problems and the sudo problem and then continue with the upgrade, or I must do a fresh install [like that link above]("https://help.ubuntu.com/community/Installation/FromLinux") (which is very, very complicated for me to do), so I would like a step-by-step clearer instruction so I don't mess up anything anymore....

Thank you.

---

