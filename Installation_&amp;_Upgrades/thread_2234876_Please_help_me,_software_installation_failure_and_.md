---
title: "Please help me, software installation failure and a few other odd behaviors."
date: 2014-07-17
forum: Installation &amp; Upgrades
---

### Post by thenh813 on 2014-07-17
Version: Xubuntu 12.04
Kernel: 3.2.0-23-generic 

  I have a problem that may cause my to grab a list of user installed packages and format my OS partition. I cant install DeVeDe or anything else I tested. Logs below.

```

root@ubuntu-pc:$ apt-get update
Get:1 http://extras.ubuntu.com precise Release.gpg [72 B]                      
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://us.archive.ubuntu.com precise Release.gpg                           
Hit http://extras.ubuntu.com precise Release                         
Hit http://us.archive.ubuntu.com precise Release                     
Get:2 http://deb.opera.com stable Release.gpg [819 B]                 
Hit http://ppa.launchpad.net precise Release                          
Get:3 http://deb.opera.com stable Release [1,721 B]                   
Hit http://us.archive.ubuntu.com precise/main Sources                          
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://us.archive.ubuntu.com precise/restricted Sources                    
Hit http://us.archive.ubuntu.com precise/universe Sources                      
Hit http://us.archive.ubuntu.com precise/multiverse Sources                    
Hit http://us.archive.ubuntu.com precise/main i386 Packages                    
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://us.archive.ubuntu.com precise/universe i386 Packages                
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex             
Get:4 http://deb.opera.com stable/non-free i386 Packages [933 B]               
Hit http://us.archive.ubuntu.com precise/main Translation-en                   
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en    
Hit http://ppa.launchpad.net precise/main i386 Packages               
Ign http://ppa.launchpad.net precise/main TranslationIndex            
Hit http://us.archive.ubuntu.com precise/restricted Translation-en             
Hit http://us.archive.ubuntu.com precise/universe Translation-en               
Ign http://deb.opera.com stable/non-free TranslationIndex                      
Ign http://extras.ubuntu.com precise/main Translation-en_US           
Ign http://extras.ubuntu.com precise/main Translation-en              
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://deb.opera.com stable/non-free Translation-en_US
Ign http://deb.opera.com stable/non-free Translation-en
Fetched 3,545 B in 3s (1,155 B/s)
Reading package lists... Done

root@ubuntu-pc:$ apt-get install libavformat-extra-53 libpostproc-extra-52 libswscale-extra-2 devede
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 devede : Depends: ffmpeg (>= 4:0.7.2) but it is not going to be installed
 libavformat-extra-53 : Depends: libavcodec-extra-53 (<= 4:0.8.1ubuntu1-99) but 4:0.8.10ubuntu0.12.04.1 is to be installed
                        Depends: libavutil-extra-51 (<= 4:0.8.1ubuntu1-99) but 4:0.8.10ubuntu0.12.04.1 is to be installed
 libpostproc-extra-52 : Depends: libavutil-extra-51 (<= 4:0.8.1ubuntu1-99) but 4:0.8.10ubuntu0.12.04.1 is to be installed
 libswscale-extra-2 : Depends: libavutil-extra-51 (<= 4:0.8.1ubuntu1-99) but 4:0.8.10ubuntu0.12.04.1 is to be installed
E: Unable to correct problems, you have held broken packages.

```

The right version is installed, the version number matches. How can a library depend on itself? And what is the mystery object depending on libavutil-extra-51? Is it easier to fix the package system or to reinstall? I have my user data on a seperate partition as well as /boot, so I will lose nothing. It will just cause me to loose a few hours of working time reinstalling the updates and user installed packages.

Please advise me what to do next.

---

### Post by grahammechanical on 2014-07-17
I do find your post offensive.

It is just a machine. Even when we choose to install software through terminal commands we are protected by the apt-get utility. It will not let us install something that will break the system. 

Computer programs are quite stupid in a way. They never reason "What's it to do with me. Just do what the user wants. What happens next is his problem."  They always follow the code. It is always best to install using the software centre and to a lesser degree through a PPA. It is one thing to use a PPA to install software but once the software is installed we should, in my opinion, disable the PPA to avoid problems with updating.

Software gets depreciated because the developer has stopped maintaining it (fixing bugs) or it is to be replaced by something better. Linux gives us the freedom to install whatever we like. It is also the freedom to break the OS.

I do find your post offensive.

It is just a machine. Even when we choose to install software through terminal commands we are protected by the apt-get utility. It will not let us install something that will break the system. 

Computer programs are quite stupid in a way. They never reason "What's it to do with me. Just do what the user wants. What happens next is his problem." They always follow the code. It is always best to install using the software centre and to a lesser degree through a PPA. It is one thing to use a PPA to install software but once the software is installed we should, in my opinion, disable the PPA to avoid problems with updating.

Software gets depreciated because the developer has stopped maintaining it (fixing bugs) or it is to be replaced by something better. Linux gives us the freedom to install whatever we like. It is also the freedom to break the OS. The libraries are not depending on themselves.

those libraries depend on a version of a library less than version  4:0.8.1 but 4:.0.8.10 is going to be installed, which I notice is a 12.04.1 library. What you are installing, is it packaged for 12.04?

---

### Post by Old_Grey_Wolf on 2014-07-17
You need to upgrade your system. The kernel for 12.04 should be 3.2.0-65-generic. You have 3.2.0-23-generic. Do the following commands:
```
sudo apt-get update
``````
sudo apt-get dist-upgrade
```
Then try installing the packages you want.

---

### Post by bapoumba on 2014-07-17
Which ppa are you using ?

---

### Post by thenh813 on 2014-07-18
@grahammechanical Sorry, I should have waited a few hours before posting. I will not post next time if in a bad mood or mad about something.
 I removed the unnecessary information and cleaned up the post. Whats odd about FFMpeg i that it is still actively maintained, unless you mean DeVeDe, which still is too. I am trying to install DeVeDe as shown in the command. I am installing it from the "official" repositories, and have no other repos besides Remastersys.



@Old_Grey_Wolf
 I held back the kernel because any update breaks the GPU drivers and it is a pain to get them working. I for how to unmark hold on a package, I no longer care about the drivers so I will update that.Running apt-get dist-upgrade does nothing. 

```

root@ubuntu-pc:~$ sudo apt-get dist-upgrade
[sudo] password for <REDACTED>: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Everything else is up to date. I did disable the update manager because I do manual updates when I have the time.



@bapoumba
I am not using any PPA for this, it is in the default repos. I usually avoid PPAs and download/compile the source myself if it is not available in the normal way.



EDIT:
 Sorry for posting 3 replies, had some trouble. Maybe I should start a new thread for this, but the keyboard is randomly alt+lefting (and other shortcuts) destroying my comments as I am about to send them. A different KB makes no difference, but a different OS does (im using Puppy Linux on my external HDD to post now). I cannot delete the other ones now, can someone who has admin privileges do that?

---

### Post by Bucky Ball on 2014-07-18
You shouldn't run the 'apt-get dist-upgrade' without running two others first:

```
sudo apt-get install update
sudo apt-get install upgrade
sudo apt-get install dist-upgrade
```

If that is not what you did, try again. Report any errors.

---

### Post by bapoumba on 2014-07-19
> **thenh813 said:**
> 
@bapoumba
I am not using any PPA for this, it is in the default repos. I usually avoid PPAs and download/compile the source myself if it is not available in the normal way.

I have removed the two posts you had empied :)

What is that for ?
```
Hit http://ppa.launchpad.net precise/main Sources
``` 
I also see the opera third party repo.

---

### Post by thenh813 on 2014-07-19
@bapoumba
Hmm... I guess you are right. I dont remember adding those repos, maybe they came with Xubuntu? I had forgotten adding the opera repo, I downloaded some .sh that automatically installs Opera and can be set to update it. I guess because it wasnt in sources.list I never knew it existed, I was assuming it pulled a deb from a ftp server. I found the "alternative" source entries in a different folder and noticed a few PPAs, I will comment them out (excluding Opera) and see what happens. I used to use DamnVid downloader and removed that as well because I have it uninstalled for a while (I use YTD2 from SourceForge). Thanks for removing the blank posts for me. I figured the buggy kerboard out, accidentally uncommented a conflicting module instead of pcspkr (I failed). Now I can hear the beeps again and use the beep command to generate tones.

@Bucky Ball
After killing a few PPAs, I will retry running those again. I did do the correct process before. I noticed some wierd PPAs that maybe came with Xubuntu that maybe override other packages. This may fix it, output here:

```

root@ubuntu-pc:~# apt-get update
Hit http://us.archive.ubuntu.com precise Release.gpg                           
Hit http://deb.opera.com stable Release.gpg                                    
Hit http://extras.ubuntu.com precise Release.gpg
Hit http://us.archive.ubuntu.com precise Release
Hit http://deb.opera.com stable Release                               
Hit http://us.archive.ubuntu.com precise/main Sources                 
Hit http://extras.ubuntu.com precise Release   
Hit http://us.archive.ubuntu.com precise/restricted Sources           
Hit http://us.archive.ubuntu.com precise/universe Sources            
Hit http://us.archive.ubuntu.com precise/multiverse Sources          
Hit http://us.archive.ubuntu.com precise/main i386 Packages          
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages    
Hit http://us.archive.ubuntu.com precise/universe i386 Packages      
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages    
Hit http://us.archive.ubuntu.com precise/main TranslationIndex       
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex 
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex 
Hit http://deb.opera.com stable/non-free i386 Packages               
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex   
Hit http://extras.ubuntu.com precise/main Sources                    
Hit http://us.archive.ubuntu.com precise/main Translation-en         
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en   
Ign http://deb.opera.com stable/non-free TranslationIndex            
Hit http://us.archive.ubuntu.com precise/restricted Translation-en   
Hit http://extras.ubuntu.com precise/main i386 Packages              
Ign http://extras.ubuntu.com precise/main TranslationIndex           
Hit http://us.archive.ubuntu.com precise/universe Translation-en     
Ign http://extras.ubuntu.com precise/main Translation-en_US
Ign http://deb.opera.com stable/non-free Translation-en_US
Ign http://extras.ubuntu.com precise/main Translation-en
Ign http://deb.opera.com stable/non-free Translation-en
Reading package lists... Done
root@ubuntu-pc:~# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ubuntu-pc:~# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Nothing? I may purge the kernel and reinstall it (and make a backup copy of vmlinuz/initrd). Its not detecting the update for the kernel.

EDIT: Ran the following:
dpkg -P --force-all linux-firmware linux-generic linux-image-generic linux-headers-3.2.0-23 linux-headers-3.2.0-23-generic linux-image-3.2.0-23-generic
apt-get update
apt-get install linux-firmware linux-generic linux-image-generic linux-headers-3.2.0-23 linux-headers-3.2.0-23-generic linux-image-3.2.0-23-generic

It did nothing, the same version is installed, but it did fix a few missing kernel headers.

 Here is sources.list, it appears to be missing the security and backport lines. I think that is where the kernel and a few other missing updates are. Can anyone tell me what a unmodified "official" version of this file looks like?

```

# deb cdrom:[Xubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.


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


```

---

### Post by bapoumba on 2014-07-19
```
ls -la /etc/apt/sources.list.d
tail -v -n +1 /etc/apt/sources.list.d/*
```
Will tell you which ppa you are using and where the repos are.

---

### Post by thenh813 on 2014-07-19
@bapoumba

 Thanks, that will be helpfull. What is the sources line for security on 12.04, it is missing on my PC. Also, I think I edited while you were posting, so sorry you missed part of the message.

---

### Post by bapoumba on 2014-07-19
> **thenh813 said:**
> @bapoumba

 Thanks, that will be helpfull. What is the sources line for security on 12.04, it is missing on my PC. Also, I think I edited while you were posting, so sorry you missed part of the message.

OK, yes, did not see the edit, thanks. You're missing updates too.

```
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse

```
You can activate them from Software Sources > Updates tab.

Once done, could you please try :
```
sudo apt-get update
sudo apt-get dist-upgrade linux-firmware linux-generic
```

---

### Post by thenh813 on 2014-07-20
```

root@ubuntu-pc:~$ apt-get update
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://deb.opera.com stable Release.gpg                                    
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://extras.ubuntu.com precise Release                                   
Hit http://deb.opera.com stable Release                                        
Hit http://archive.canonical.com precise Release                               
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://deb.opera.com stable/non-free i386 Packages                         
Hit http://archive.canonical.com precise/partner Sources                       
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Ign http://deb.opera.com stable/non-free TranslationIndex                      
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release                                   
Hit http://us.archive.ubuntu.com precise Release.gpg                           
Get:1 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Get:2 http://us.archive.ubuntu.com precise-security Release.gpg [198 B]        
Get:3 http://us.archive.ubuntu.com precise-backports Release.gpg [198 B]       
Hit http://us.archive.ubuntu.com precise Release                               
Get:4 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]           
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:5 http://us.archive.ubuntu.com precise-security Release [49.6 kB]          
Get:6 http://us.archive.ubuntu.com precise-backports Release [49.6 kB]         
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Hit http://us.archive.ubuntu.com precise/restricted Sources                    
Hit http://us.archive.ubuntu.com precise/main Sources                          
Hit http://us.archive.ubuntu.com precise/multiverse Sources                    
Hit http://us.archive.ubuntu.com precise/universe Sources                      
Hit http://us.archive.ubuntu.com precise/main i386 Packages                    
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://us.archive.ubuntu.com precise/universe i386 Packages                
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                 
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://deb.opera.com stable/non-free Translation-en_US                     
Ign http://archive.canonical.com precise/partner Translation-en_US             
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex             
Get:7 http://us.archive.ubuntu.com precise-updates/main i386 Packages [853 kB] 
Ign http://deb.opera.com stable/non-free Translation-en                        
Ign http://archive.canonical.com precise/partner Translation-en                
Ign http://ppa.launchpad.net precise/main Translation-en_US                   
Ign http://ppa.launchpad.net precise/main Translation-en
Get:8 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [13.7 kB]
Get:9 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [251 kB]
Get:10 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [15.5 kB]
Get:11 http://us.archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]
Get:12 http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]
Get:13 http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]
Get:14 http://us.archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]
Get:15 http://us.archive.ubuntu.com precise-security/main i386 Packages [440 kB]
Get:16 http://us.archive.ubuntu.com precise-security/restricted i386 Packages [4,620 B]
Get:17 http://us.archive.ubuntu.com precise-security/universe i386 Packages [99.7 kB]
Get:18 http://us.archive.ubuntu.com precise-security/multiverse i386 Packages [2,650 B]
Get:19 http://us.archive.ubuntu.com precise-security/main TranslationIndex [74 B]
Get:20 http://us.archive.ubuntu.com precise-security/multiverse TranslationIndex [72 B]
Get:21 http://us.archive.ubuntu.com precise-security/restricted TranslationIndex [72 B]
Get:22 http://us.archive.ubuntu.com precise-security/universe TranslationIndex [73 B]
Hit http://us.archive.ubuntu.com precise/main Translation-en                   
Get:23 http://us.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Get:24 http://us.archive.ubuntu.com precise-backports/main i386 Packages [6,420 B]
Get:25 http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages [5,178 B]
Get:26 http://us.archive.ubuntu.com precise-backports/universe i386 Packages [41.2 kB]
Get:27 http://us.archive.ubuntu.com precise-backports/main TranslationIndex [72 B]
Get:28 http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex [72 B]
Get:29 http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex [70 B]
Get:30 http://us.archive.ubuntu.com precise-backports/universe TranslationIndex [73 B]
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://us.archive.ubuntu.com precise/restricted Translation-en             
Hit http://us.archive.ubuntu.com precise/universe Translation-en               
Get:31 http://us.archive.ubuntu.com precise-updates/main Translation-en [360 kB]
Get:32 http://us.archive.ubuntu.com precise-updates/multiverse Translation-en [9,010 B]
Get:33 http://us.archive.ubuntu.com precise-updates/restricted Translation-en [3,027 B]
Get:34 http://us.archive.ubuntu.com precise-updates/universe Translation-en [142 kB]
Get:35 http://us.archive.ubuntu.com precise-security/main Translation-en [188 kB]
Get:36 http://us.archive.ubuntu.com precise-security/multiverse Translation-en [1,299 B]
Get:37 http://us.archive.ubuntu.com precise-security/restricted Translation-en [1,253 B]
Get:38 http://us.archive.ubuntu.com precise-security/universe Translation-en [57.8 kB]
Get:39 http://us.archive.ubuntu.com precise-backports/main Translation-en [5,882 B]
Get:40 http://us.archive.ubuntu.com precise-backports/multiverse Translation-en [4,610 B]
Get:41 http://us.archive.ubuntu.com precise-backports/restricted Translation-en [14 B]
Get:42 http://us.archive.ubuntu.com precise-backports/universe Translation-en [32.9 kB]
Fetched 2,700 kB in 18s (150 kB/s)                                             
Reading package lists... Done

root@ubuntu-pc:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-image-generic
The following packages will be upgraded:
  apt apt-transport-https apt-utils bsdutils cups cups-bsd cups-client
  cups-common cups-ppdc dbus dbus-x11 dpkg dpkg-dev ffmpeg file
  firefox-locale-en flashplugin-installer fonts-opensymbol glade gnupg gpgv
  grub-common grub-pc grub-pc-bin grub2 grub2-common iproute kdelibs-bin
  kdelibs5-data kdelibs5-plugins kdoctools libapt-inst1.4 libapt-pkg4.12
  libav-tools libavcodec-extra-53 libavdevice53 libavfilter2 libavformat53
  libavutil-extra-51 libblkid1 libcups2 libcupscgi1 libcupsdriver1
  libcupsimage2 libcupsmime1 libcupsppdc1 libdbus-1-3 libdpkg-perl
  libdrm-intel1 libdrm-nouveau1a libdrm-radeon1 libdrm2 libgladeui-2-0
  libgladeui-common libglib2.0-doc libgnutls-dev libgnutls-openssl27
  libgnutls26 libgnutlsxx27 libgtk-3-doc libgtk2.0-doc libgtksourceview-3.0-0
  libgtksourceview-3.0-common libjpeg-turbo-progs libjpeg-turbo8 libjson0
  libkcmutils4 libkde3support4 libkdeclarative5 libkdecore5 libkdesu5
  libkdeui5 libkdewebkit5 libkdnssd4 libkemoticons4 libkfile4 libkhtml5
  libkidletime4 libkio5 libkjsapi4 libkjsembed4 libkmediaplayer4
  libknewstuff3-4 libknotifyconfig4 libkntlm4 libkparts4 libkpty4
  libkrosscore4 libkrossui4 libktexteditor4 liblightdm-gobject-1-0 libmagic1
  libminiupnpc8 libmount1 libmysqlclient18 libnepomuk4 libnepomukquery4a
  libnepomukutils4 libnspr4 libnspr4-0d libpam-winbind libpango1.0-doc
  libplasma3 libpostproc52 libpurple-bin libpurple0 libqt4-dbus
  libqt4-declarative libqt4-designer libqt4-network libqt4-opengl
  libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-svg
  libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libreoffice-base-core
  libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw
  libreoffice-emailmerge libreoffice-impress libreoffice-math
  libreoffice-style-human libreoffice-writer libsmbclient libsolid4 libssl-dev
  libssl-doc libssl1.0.0 libsvn1 libswscale2 libthreadweaver4 libuuid1
  libwbclient0 libxml2 libxml2-utils lightdm linux-firmware linux-libc-dev
  mount mysql-client-core-5.5 mysql-common mysql-server-core-5.5 openssl
  pidgin pidgin-data python-libxml2 python-lxml python-uno qdbus samba-common
  samba-common-bin smbclient thunderbird thunderbird-globalmenu
  thunderbird-locale-en thunderbird-locale-en-us transmission-common
  transmission-gtk tzdata tzdata-java uno-libs3 update-manager
  update-manager-core update-notifier update-notifier-common ure util-linux
  uuid-runtime wget winbind xsltproc
178 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 251 MB of archives.
After this operation, 9,283 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y

```

 Difference much? Updates and Security still appeared checked in software-sources so I added those with Leafpad. I unchecked them and rechecked them in sources to make sure they were working. Just started apt-get upgrade, I have a *few* things to update. The two that wont be upgraded are the kernel headers and image. Will run apt-get dist-upgrade for that afterwards. The reason that DeVeDe wasn't installing was because I had a half up to date system. Surprised something didn't break yet. Here comes a half hour of downloading...

 I will post the result of the update, and see if DeVeDe installs.
All I wanted to do was add subtitles to something and burn it, and I get all of this!?!?!? LOL
Well, its probabally for the better as this would have caused MAJOR issues somewhere later on.

---

### Post by bapoumba on 2014-07-20
Well, yes, run the upgrade and let it finish. Then run it again :
```
sudo apt-get update
sudo apt-get upgrade

```
If there are no more packages to upgrade and the kernel packages are still kept back (they should be) :
```
sudo apt-get dist-upgrade linux-generic linux-image-generic
```

(linux_image_generic depends on linux-generic, so dist-upgrading linux-generic should be enough).

Edit : should something go wrong, do not reboot half finished, run the update/upgrade cycle again. If for any reason you loose the GUI, <ctrl><alt><f1> will take you to a tty, login and you can finish from there before going back to the GUI interface with <ctrl><alt><f7>.

---

### Post by thenh813 on 2014-07-20
UPGRADE SUCCESS!!! DeVeDe installed flawlessly!
The graphics drivers were successfully murdered in the process leaving me with a  black screen instead of X and no KB response. All that was required was   SYSRQ+E,I,S to to kill all non kernel processes and flush the disk buffer (incase I had to reset). I switched to TTY2 (TTY1 had the kernel log in it), logged in and ran sudo sh NVIDIA-96x*.run in my downloads folder. It said the drivers were already installed, so it was reinstalling them. The reason I originally held the kernel back was because versions higher than a certain number are incompatable. Its good to know Xubuntu 12.04 will always run the legacy kernel, they simply update and patch it to the latest version. I do have a newer GPU installed as well, but I keep the ancient (2001-2003) NV17/18 card installed to run a second CRT without loading the primary GPU (plus the AGP would be unused anyway).

This problem is resolved, thanks for all the help. I will mark the thread as solved to let others know it is fixed.
I may consider installing ppa-purge as mentioned in your signature, it never hurts to be too safe with anything. I should also use checkinstall/fakeroot+deb instead of make-install when I compile stuff. That way I can avoid similar problems (wrong package versions) in the future, if I accidentally introduce them.
 Once again thanks for the help bapoumba, and thanks to everyone else for suggestions.

---

### Post by bapoumba on 2014-07-21
Glad to see you got it to work :)
Yeah, ppa-purge comes handy when reverting packages back to their distribution versions. When the package manager is stuck, it is too late to install it..

---

