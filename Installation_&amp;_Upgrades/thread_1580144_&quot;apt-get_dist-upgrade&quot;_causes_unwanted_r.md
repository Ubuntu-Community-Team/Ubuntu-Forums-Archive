---
title: "&quot;apt-get dist-upgrade&quot; causes unwanted removal of installed packages"
date: 2010-09-22
forum: Installation &amp; Upgrades
---

### Post by FlameReaper on 2010-09-22
Just like the title said, I'm actually pretty curious as to why is this happening.

I attempted to do this yesterday but unfortunately it broke my X Server somehow. Attempted a recovery by reinstalling them and only today I realized why was that... looking below...

```
assassin@assassin:~$ sudo apt-get dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  acpi-support acpid alsa-base alsa-utils apparmor apport apport-gtk avahi-daemon bluez bluez-cups brltty brltty-x11 checkbox checkbox-gtk console-setup couchdb-bin cups
  cups-driver-gutenprint desktopcouch erlang-base erlang-crypto erlang-inets erlang-mnesia erlang-public-key erlang-runtime-tools erlang-ssl erlang-syntax-tools erlang-xmerl
  evolution-couchdb foo2zjs foomatic-db foomatic-db-engine gdm gdm-guest-session ghostscript-cups gnome-bluetooth gnome-power-manager gnome-system-tools gnome-user-share gwibber
  gwibber-service hplip indicator-session kbd kdm knm-runtime lftp lib32nss-mdns libnet-dbus-perl libnss-mdns liboobs-1-4 libwww-perl libxml-parser-perl libxml-twig-perl
  libxml-xpath-perl linux-sound-base media-player-info netbase network-manager network-manager-gnome network-manager-kde network-manager-pptp network-manager-pptp-gnome ntfs-3g
  openprinting-ppds pcmciautils plymouth-label plymouth-theme-ubuntu-logo plymouth-x11 pm-utils pm-utils-powersave-policy powermgmt-base ppp pptp-linux pxljr python-desktopcouch
  python-desktopcouch-records splix system-tools-backends ubuntu-desktop upower usb-creator-common usb-creator-gtk wine wine1.2 wireless-crda xorg xserver-xorg xserver-xorg-core
  xserver-xorg-input-all xserver-xorg-input-evdev xserver-xorg-input-mouse xserver-xorg-input-synaptics xserver-xorg-input-vmmouse xserver-xorg-input-wacom

```

I was shocked when I found this out. Why does my base applications need to be removed? The worst of it all is that it attempts to remove even the X server. Why is this?

This feels weird because I'm running the **dist-upgrade** option via apt-get. Removal of key applications as an upgrade? Hmm, that's something new for me.

Oh by the way, I'm using Lucid desktop.

---

### Post by tommcd on 2010-09-23
Do you have any 3rd party repos in your */etc/apt/sources.list*? This includes those all too problematic ppa repos.
Please post your */etc/apt/sources.list* file. Also include anything in your */etc/apt/sources.list.d/* directory.
Also, that is apparently not the entire output of:```
sudo apt-get ditst-upgrade
```
Can you post the entire output of that command?

---

### Post by FlameReaper on 2010-09-24
> **tommcd said:**
> Do you have any 3rd party repos in your */etc/apt/sources.list*? This includes those all too problematic ppa repos.
Please post your */etc/apt/sources.list* file. Also include anything in your */etc/apt/sources.list.d/* directory.
Also, that is apparently not the entire output of:```
sudo apt-get ditst-upgrade
```
Can you post the entire output of that command?

Output of /etc/apt/sources.list

```
assassin@assassin:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://us.archive.ubuntu.com/ubuntu/ lucid-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-security main restricted
deb http://us.archive.ubuntu.com/ubuntu/ lucid-security universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-security universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-security multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-security multiverse

# deb http://apt.last.fm/ debian stable
# deb http://deb.torproject.org/torproject.org lucid main
deb ftp://ftp.au.debian.org/debian stable main contrib non-free
deb-src ftp://ftp.au.debian.org/debian stable main contrib non-free

deb http://ppa.launchpad.net/conkyhardcore/ppa/ubuntu lucid main
deb-src http://ppa.launchpad.net/conkyhardcore/ppa/ubuntu lucid main

deb http://ppa.launchpad.net/ubuntu-desktop/ppa/ubuntu lucid main
deb-src http://ppa.launchpad.net/ubuntu-desktop/ppa/ubuntu lucid main

```

/etc/apt/sources.list.d

```
assassin@assassin:~$ cat /etc/apt/sources.list.d/*.list
deb http://ppa.launchpad.net/bisigi/ppa/ubuntu lucid main
deb http://ppa.launchpad.net/doctormo/wacom-plus/ubuntu lucid main
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu lucid main
deb http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu lucid main #Firefox Stable Channel Packages
# This file makes sure that Opera Browser is kept up-to-date
# as part of regular system upgrades

deb http://deb.opera.com/opera/ stable non-free #Opera Browser (final releases)

# The line above will make sure you get all final public releases.
# Uncomment the following line if you want to get alpha and beta
# releases, too.

# deb http://deb.opera.com/opera-beta/ stable non-free #Opera Browser (beta releases)
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu lucid main #Ubuntu Tweak Stable Source
deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu lucid main

```

Output of the apt-get dist-upgrade command:

```
assassin@assassin:~$ sudo apt-get dist-upgrade 
[sudo] password for assassin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  acpi-support acpid alsa-base alsa-utils apparmor apport apport-gtk
  avahi-daemon bluez bluez-cups brltty brltty-x11 checkbox checkbox-gtk
  console-setup couchdb-bin cups cups-driver-gutenprint desktopcouch dkms
  erlang-base erlang-crypto erlang-inets erlang-mnesia erlang-public-key
  erlang-runtime-tools erlang-ssl erlang-syntax-tools erlang-xmerl
  evolution-couchdb foo2zjs foomatic-db foomatic-db-engine gdm
  gdm-guest-session ghostscript-cups gnome-bluetooth gnome-power-manager
  gnome-system-tools gnome-user-share gwibber gwibber-service hplip
  indicator-session kbd kdm knm-runtime lftp lib32nss-mdns libnet-dbus-perl
  libnss-mdns liboobs-1-4 libwww-perl libxml-parser-perl libxml-twig-perl
  libxml-xpath-perl linux-sound-base media-player-info netbase network-manager
  network-manager-gnome network-manager-kde network-manager-pptp
  network-manager-pptp-gnome ntfs-3g openprinting-ppds pcmciautils
  plymouth-label plymouth-theme-ubuntu-logo plymouth-x11 pm-utils
  pm-utils-powersave-policy powermgmt-base ppp pptp-linux pxljr
  python-desktopcouch python-desktopcouch-records splix system-tools-backends
  ubuntu-desktop upower usb-creator-common usb-creator-gtk wine wine1.2
  wireless-crda xorg xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom
The following packages have been kept back:
  python-notify
0 upgraded, 0 newly installed, 96 to remove and 1 not upgraded.
After this operation, 232MB disk space will be freed.
Do you want to continue [Y/n]? 
```

Hmm, problematic PPAs eh? Let's see, from what I can remember, there were errors whenever I run apt-get update. Here's the output of it:

```
assassin@assassin:~$ sudo apt-get update
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)/ lucid/main Translation-en_US
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)/ lucid/restricted Translation-en_US
Hit http://archive.canonical.com lucid Release.gpg                             
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US       
Hit http://archive.canonical.com lucid Release                                 
Hit http://archive.canonical.com lucid/partner Packages                        
Get:1 http://ppa.launchpad.net lucid Release.gpg [307B]                        
Hit http://archive.canonical.com lucid/partner Sources                         
Ign http://ppa.launchpad.net/conkyhardcore/ppa/ubuntu/ lucid/main Translation-en_US
Get:2 http://ppa.launchpad.net lucid Release.gpg [307B]                        
Ign http://ppa.launchpad.net/ubuntu-desktop/ppa/ubuntu/ lucid/main Translation-en_US
Get:3 http://ppa.launchpad.net lucid Release.gpg [307B]                        
Ign http://ppa.launchpad.net/bisigi/ppa/ubuntu/ lucid/main Translation-en_US   
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/doctormo/wacom-plus/ubuntu/ lucid/main Translation-en_US
Get:4 http://ppa.launchpad.net lucid Release.gpg [316B]                        
Ign http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ lucid/main Translation-en_US
Get:5 http://ppa.launchpad.net lucid Release.gpg [307B]                        
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ lucid/main Translation-en_US
Get:6 http://ppa.launchpad.net lucid Release.gpg [316B]                        
Ign http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ lucid/main Translation-en_US
Get:7 http://ppa.launchpad.net lucid Release [57.3kB]                          
Get:8 http://ppa.launchpad.net lucid Release [57.3kB]                          
Ign http://ppa.launchpad.net lucid Release                                     
Ign http://ppa.launchpad.net lucid Release                                     
Get:9 http://ppa.launchpad.net lucid Release [57.3kB]                          
Ign http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net lucid Release                                     
Get:10 http://ppa.launchpad.net lucid Release [57.3kB]                         
Hit http://deb.opera.com stable Release.gpg                                    
Ign http://deb.opera.com/opera/ stable/non-free Translation-en_US              
Get:11 http://dl.google.com stable Release.gpg [189B]                          
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_US       
Get:12 http://dl.google.com stable Release [2,544B]                            
Hit http://deb.opera.com stable Release                                        
Get:13 http://dl.google.com stable/main Packages [1,050B]                      
Hit http://us.archive.ubuntu.com lucid Release.gpg                             
Ign http://deb.opera.com stable/non-free Packages                              
Ign http://deb.opera.com stable/non-free Packages                              
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Get:14 http://us.archive.ubuntu.com lucid-updates Release.gpg [198B] 
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Get:15 http://us.archive.ubuntu.com lucid-security Release.gpg [198B]          
Hit http://deb.opera.com stable/non-free Packages                              
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US 
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release                                 
Get:16 http://us.archive.ubuntu.com lucid-updates Release [44.7kB]             
Hit http://ppa.launchpad.net lucid Release                                     
Get:17 http://ppa.launchpad.net lucid Release [57.3kB]                         
Get:18 http://ppa.launchpad.net lucid Release [57.3kB]                         
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://ppa.launchpad.net lucid/main Sources                                
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://ppa.launchpad.net lucid/main Sources                                
Hit http://ppa.launchpad.net lucid/main Packages                               
Ign http://ppa.launchpad.net lucid Release                                     
Ign http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net lucid/main Packages                               
Get:19 http://ppa.launchpad.net lucid/main Packages [105kB]          
Get:20 ftp://ftp.au.debian.org stable Release.gpg [1,033B]                    
Get:21 http://us.archive.ubuntu.com lucid-security Release [38.5kB]            
Get:22 ftp://ftp.au.debian.org/debian/ stable/main Translation-en_US           
Ign ftp://ftp.au.debian.org/debian/ stable/main Translation-en_US              
Get:23 ftp://ftp.au.debian.org/debian/ stable/contrib Translation-en_US        
Ign ftp://ftp.au.debian.org/debian/ stable/contrib Translation-en_US           
Get:24 ftp://ftp.au.debian.org/debian/ stable/non-free Translation-en_US       
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://ppa.launchpad.net lucid/main Packages                               
Ign ftp://ftp.au.debian.org/debian/ stable/non-free Translation-en_US          
Hit http://us.archive.ubuntu.com lucid/main Packages                           
Hit http://us.archive.ubuntu.com lucid/restricted Packages                     
Hit http://us.archive.ubuntu.com lucid/main Sources                            
Hit http://us.archive.ubuntu.com lucid/restricted Sources                      
Hit http://us.archive.ubuntu.com lucid/universe Packages                       
Hit http://us.archive.ubuntu.com lucid/universe Sources                        
Hit http://us.archive.ubuntu.com lucid/multiverse Packages                     
Hit http://us.archive.ubuntu.com lucid/multiverse Sources                      
Ign ftp://ftp.au.debian.org stable Release                                     
Hit ftp://ftp.au.debian.org stable/main Packages                               
Get:25 http://us.archive.ubuntu.com lucid-updates/main Packages [309kB]        
Hit ftp://ftp.au.debian.org stable/contrib Packages                            
Hit ftp://ftp.au.debian.org stable/non-free Packages                           
Hit ftp://ftp.au.debian.org stable/main Sources                                
Hit ftp://ftp.au.debian.org stable/contrib Sources                             
Hit ftp://ftp.au.debian.org stable/non-free Sources                            
Get:26 http://us.archive.ubuntu.com lucid-updates/restricted Packages [3,267B] 
Get:27 http://us.archive.ubuntu.com lucid-updates/main Sources [122kB]         
Get:28 http://us.archive.ubuntu.com lucid-updates/restricted Sources [1,443B]  
Get:29 http://us.archive.ubuntu.com lucid-updates/universe Packages [122kB]    
Get:30 http://us.archive.ubuntu.com lucid-updates/universe Sources [48.2kB]    
Get:31 http://us.archive.ubuntu.com lucid-updates/multiverse Packages [3,651B] 
Get:32 http://us.archive.ubuntu.com lucid-updates/multiverse Sources [1,739B]  
Get:33 http://us.archive.ubuntu.com lucid-security/main Packages [82.1kB]      
Get:34 http://us.archive.ubuntu.com lucid-security/restricted Packages [14B]   
Get:35 http://us.archive.ubuntu.com lucid-security/main Sources [29.7kB]       
Get:36 http://us.archive.ubuntu.com lucid-security/restricted Sources [14B]    
Get:37 http://us.archive.ubuntu.com lucid-security/universe Packages [40.7kB]  
Get:38 http://us.archive.ubuntu.com lucid-security/universe Sources [9,810B]   
Get:39 http://us.archive.ubuntu.com lucid-security/multiverse Packages [1,869B]
Get:40 http://us.archive.ubuntu.com lucid-security/multiverse Sources [656B]   
Fetched 1,029kB in 2min 14s (7,626B/s)                                         
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1E5D5E8D66AE0775
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2CC98497A1231595
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6E871C4A881574DE
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures were invalid: BADSIG 6AF0E1940624A220 Launchpad PPA for TualatriX
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B22AB97AF1CDFA9
W: GPG error: ftp://ftp.au.debian.org stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9AA38DCD55BE302B NO_PUBKEY 4D270D06F42584E6

```

---

### Post by tommcd on 2010-09-25
This is almost certainly your problem. From your */etc/apt/sources.list*:
```

deb ftp://ftp.au.debian.org/debian stable main contrib non-free
deb-src ftp://ftp.au.debian.org/debian stable main contrib non-free

```
You should *never* mix Debian and Ubuntu repos. Although Ubuntu is based on Debian, the Ubuntu packages are modified by the Ubuntu devs. The Debian and Ubuntu repos are *not* compatible.  If you upgrade your system with those Debian repos you will most likely break it.
Remove those Debian repos from your *sources.list* and run:
```

sudo apt-get update
sudo apt-get dist-upgrade

```
and see if the problem goes away.

Regarding the errors on the ppa repos, you need to import the GPG key for those ppa repos. The key is usually on the ppa repo page that you got the repo from.
See this:
[https://help.ubuntu.com/9.10/add-applications/C/adding-repos.html](https://help.ubuntu.com/9.10/add-applications/C/adding-repos.html)
And see these examples from Ubuntu Geek:
[http://www.ubuntugeek.com/ubuntu-tip-simplified-way-to-add-ppa-repositories-in-karmic.html](http://www.ubuntugeek.com/ubuntu-tip-simplified-way-to-add-ppa-repositories-in-karmic.html)
[http://www.ubuntugeek.com/how-to-install-chromium-google-chrome-in-ubuntu-using-deb-package.html](http://www.ubuntugeek.com/how-to-install-chromium-google-chrome-in-ubuntu-using-deb-package.html)

---

### Post by FlameReaper on 2010-09-25
Thanks, that solved the problem... for good I guess? Haha.

I can't remember for what I had that Debian repository, but I was certain I was trying to install something which required that repo. But now that I can't remember what was it anymore, might as well I get rid of it.

About the GPG keys, well I guess I'll hold back from fixing it for now. Right now the problem it's causing me is just needing me to manually authenticate its installations via --yes --force-yes option.

---

### Post by mailc on 2012-09-27
Please have a look at my* /etc/apt/sources.list *and tell me what needs removal or what else I should do. I see some duplicates and at least one 'debian'.
Thanks

```
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Alpha i386 (20120122)]/ precise main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise main restricted multiverse
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise main restricted multiverse
## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise-updates main restricted multiverse
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise-updates main restricted multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise universe
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise-updates universe
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise universe
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise-backports main universe restricted multiverse
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise-backports main universe restricted multiverse

deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise-security main restricted multiverse
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise-security main restricted multiverse
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise-security universe
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise-security universe

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
deb http://debian.anonymous-proxy-servers.net precise main
deb http://www.duinsoft.nl/pkg debs all
deb http://apt.bitcoins.sk/ precise main
```

---

### Post by QIII on 2012-09-27
mailc -

Please start your own new thread.

This one will soon be closed by the staff for necromancy.

---

### Post by nothingspecial on 2012-09-27
> **QIII said:**
> mailc -

Please start your own new thread.

This one will soon be closed by the staff for necromancy.

Yep.

---

