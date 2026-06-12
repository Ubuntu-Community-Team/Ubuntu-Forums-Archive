---
title: "problem with flash"
date: 2010-01-13
forum: Installation &amp; Upgrades
---

### Post by jokernomore on 2010-01-13
okay so i ttired toi upgrade to adobe flash player 10 and well it isnt working im  a newb to ubuntu 8.04 so idk how to enable it in firefox any help would be awsome 

ps i use the 32 bit version

---

### Post by marcozs on 2010-01-13
> **jokernomore said:**
> okay so i ttired toi upgrade to adobe flash player 10 and well it isnt working im  a newb to ubuntu 8.04 so idk how to enable it in firefox any help would be awsome 

ps i use the 32 bit version

Have you tried to install flash from the adobe website or how?
Here there is the deb from the adobe website
[http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb) 
which should be working for all Ubuntu < 9.04

Remember to remove the old version if you have any installed...

---

### Post by jokernomore on 2010-01-13
i have tried this and the terminal install and i have remvoed previous flash the terminal install says that the file or directory does not exist

---

### Post by marcozs on 2010-01-13
> **jokernomore said:**
> i have tried this and the terminal install and i have remvoed previous flash the terminal install says that the file or directory does not exist

Post terminal log and commands?

You should be giving first something like
```
sudo apt-get remove flashplugin-nonfree
sudo dpkg -i install_flash_player_10_linux.deb
```

---

### Post by jokernomore on 2010-01-13
chris@ubuntu:~$  sudo dpkg -i install_flash_player_10_linux.deb
[sudo] password for chris: 
dpkg: error processing install_flash_player_10_linux.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 install_flash_player_10_linux.deb
chris@ubuntu:~$

---

### Post by marcozs on 2010-01-13
> **jokernomore said:**
> dpkg: error processing install_flash_player_10_linux.deb (--install):
 cannot access archive: No such file or directory

It looks like you might have something else already installed, have you removed all the other flash packages?

Try to clean up:
```
sudo apt-get remove -y --purge flashplugin-nonfree libflashsupport
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
```

---

### Post by jokernomore on 2010-01-13
i ttried that b4 and this came up 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not installed, so not removed
Package libflashsupport is not installed, so not removed
The following packages were automatically installed and are no longer required:
  oem-config-gtk xserver-xorg-video-amd localechooser-data oem-config
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
chris@ubuntu:~$

---

### Post by marcozs on 2010-01-13
Strange that the deb doesn't work... tried to double click on it to see if all the dependencies are satisfied? (even though I don't think there are special dependencies)

You could also try the adobe installer:
```
wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz
tar -zxvf install_flash_player_10_linux.tar.gz
cd install_flash_player_10_linux
./flashplayer-installer
```

---

### Post by jokernomore on 2010-01-13
chris@ubuntu:~$ wget [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz)
--04:15:31--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz)
           => `install_flash_player_10_linux.tar.gz.1'
Resolving fpdownload.macromedia.com... 72.247.82.70
Connecting to fpdownload.macromedia.com|72.247.82.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4,050,308 (3.9M) [application/x-gzip]

100%[====================================>] 4,050,308      2.48M/s             

04:15:33 (2.47 MB/s) - `install_flash_player_10_linux.tar.gz.1' saved [4050308/4050308]

chris@ubuntu:~$ tar -zxvf install_flash_player_10_linux.tar.gz
libflashplayer.so
chris@ubuntu:~$ cd install_flash_player_10_linux
bash: cd: install_flash_player_10_linux: No such file or directory
chris@ubuntu:~$ ./flashplayer-installer


this came up XD

---

### Post by marcozs on 2010-01-13
> **jokernomore said:**
> chris@ubuntu:~$ tar -zxvf install_flash_player_10_linux.tar.gz
libflashplayer.so
this came up XD

Oh there's only the library in the gz...
Probably you can just copy it in

```
sudo mv libflashplayer.so /usr/lib/mozilla/plugins/
```

And then start firefox and check if that works...

---

### Post by marcozs on 2010-01-13
Just out of curiosity: why do you use ubuntu 8.04 and not the latest 9.10 which has flash10 already out-of-the-box?

---

### Post by jokernomore on 2010-01-13
libary? well when my compture was given to me this is what it had on it XD

---

### Post by jokernomore on 2010-01-13
sudo mv libflashplayer.so /usr/lib/mozilla/plugins/
mv: cannot stat `libflashplayer.so': No such file or directory


this came up >< lol

---

### Post by marcozs on 2010-01-13
> **jokernomore said:**
> sudo mv libflashplayer.so /usr/lib/mozilla/plugins/
mv: cannot stat `libflashplayer.so': No such file or directory

Check if the folder exists?

---

### Post by jokernomore on 2010-01-13
yeah i creatied a file named plugins in .mozilla

---

### Post by slakkie on 2010-01-13
Hi,

please have a look at the upgrade flash link in my signature. In there you can find instructions to install the latest available flash player from Adobe from an official repository. It is the same version as Karmic is using.

See also: [http://ubuntuforums.org/showthread.php?p=8657657#post8657657](http://ubuntuforums.org/showthread.php?p=8657657#post8657657)

---

### Post by jokernomore on 2010-01-13
> **slakkie said:**
> Hi,

please have a look at the upgrade flash link in my signature. In there you can find instructions to install the latest available flash player from Adobe from an official repository. It is the same version as Karmic is using.

See also: [http://ubuntuforums.org/showthread.php?p=8657657#post8657657](http://ubuntuforums.org/showthread.php?p=8657657#post8657657)

i tried that and it just made me more confused im a compleat newbie to linux XD

---

### Post by slakkie on 2010-01-13
> **jokernomore said:**
> i tried that and it just made me more confused im a compleat newbie to linux XD

What was the problem then? 


* Open your sources.list file:

gksudo gedit /etc/apt/sources.list

Make sure it contains (only) these lines:

```

### Hardy 8.04
# Required    
deb http://archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ hardy-security main restricted universe multiverse
#deb-src http://security.ubuntu.com/ubuntu/ hardy-security main restricted universe multiverse
# Recommended
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse
# Optional
#deb http://packages.medibuntu.org/ hardy free non-free
#deb-src http://packages.medibuntu.org/ hardy free non-free
deb http://archive.canonical.com/ubuntu/ hardy partner
#deb-src http://archive.canonical.com/ubuntu/ hardy partner
#deb http://archive.ubuntu.com/ubuntu/ hardy-proposed main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ hardy-proposed main restricted universe multiverse
#deb http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

```

* Update the package list:

sudo aptitude update

* Install flash:

sudo aptitude install adobe-flashplugin

* Done.

---

### Post by jokernomore on 2010-01-13
# 
deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/ hardy main restricted

deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

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

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) hardy main #WineHQ - Ubuntu 8.04 "Hardy Heron"







this is what came up XD

---

### Post by jokernomore on 2010-01-14
up would realy like to fix this be4 i say that linux is more bs then windows and just reformat cause this is makeing me really ******* mad lol and frustraited

---

### Post by night dash on 2010-01-26
Thanks all friends trying to help.
I am a Ubuntu 8.04 user too. When installing flash, i had the same problems as jokernomore had lived.
I did what slakkie had suggested, after doing this 
```
sudo aptitude update 
```i did 
```

sudo apt-get install flashplugin-nonfree

```instead of

```

sudo aptitude install adobe-flashplugin

```It worked for me, try this.

---

