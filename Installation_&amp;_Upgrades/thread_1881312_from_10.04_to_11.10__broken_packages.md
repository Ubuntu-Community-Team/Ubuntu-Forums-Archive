---
title: "from 10.04 to 11.10  broken packages"
date: 2011-11-15
forum: Installation &amp; Upgrades
---

### Post by tock on 2011-11-15
Before I upgraded I tried to remove as many packages from 3rd party repos as I could find.  I have 11.10 up and running but with some broken package problems.  I've seen a few of these problems on the many searches I've done but with no fix.  I've tried the apt-get cleans and updates to on avail.  The first package is synaptic.  It installs ok but immediately upon opening, it shuts down with the "terminate called after throwing an instance of 'std::out_of_range'
  what():  vector::_M_range_check"  error.


The other package I'm trying to get going is the latest and greatest ffmpeg using FakeOutdoorsman's procedure shown on this site.  
   I'm trying to install :
libfaac-dev libjack-jackd2-dev \
  libmp3lame-dev libopencore-amrnb-dev libopencore-amrwb-dev libsdl1.2-dev libtheora-dev \
  libva-dev libvdpau-dev libvorbis-dev libx11-dev libxfixes-dev texi2html yasm zlib1g-dev


libsdl1.2-dev gives the error "The following packages have unmet dependencies:
 libsdl1.2-dev : Depends: libglu1-mesa-dev but it is not going to be installed"


I've been playing with ubuntu for quite awhile and would like to advance my knowledge by discovering how to fix problems like this..  I've searched and found similar problems but no solutions. 

Thanks for your time.

---

### Post by FakeOutdoorsman on 2011-11-15
I'll attempt to venture into territory that I'm not very familiar with only because I heard the word "FFmpeg". As for the synaptic issue, according to bug [#607605](https://bugs.launchpad.net/synaptic/+bug/607605), running in a terminal the following command apparently worked for some people:
```
gsettings set org.gnome.desktop.interface toolkit-accessibility false
```

Now for your sdl issue. Let's see what version of Ubuntu your machine thinks it has:
```
$ lsb_release -cs
oneiric
```
Show your repository information:
```
cat /etc/apt/sources.list
```
Additionally, there might be some files in:
```
ls /etc/apt/sources.list.d/
```
If there are, cat those too and show the contents. Make sure to use the *code* tag on this forum so it gets formatted nicely.

The issue might be as simple as outdated/screwy package index files. If everything looks normal go ahead and update the repository index:
```
sudo apt-get update
```
and then try installing *libsdl1.2-dev* again:
```
sudo apt-get install libsdl1.2-dev
```
As you can tell I don't really have a simple, straightforward answer for you since I'm not an apt expert, but this will probably be a good start until someone more knowledgeable comes by.

---

### Post by tock on 2011-11-17
Now for your sdl issue. Let's see what version of Ubuntu your machine thinks it has:

```
lsb_release -cs
oneiric
```



```
cat /etc/apt/sources.list:

#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted universe multiverse

###### Ubuntu Update Repos
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-security main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-proposed main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-security main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-proposed main restricted universe multiverse

###### Ubuntu Partner Repo
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################

###### 3rd Party Binary Repos

#### GetDeb - http://www.getdeb.net
## Run this command: wget -q -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -

#### HandBrake - http://handbrake.fr/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 62D38753

#### Medibuntu - http://www.medibuntu.org/ 
## Run this command: sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update 

#### OpenShot - http://www.openshotvideo.com
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys B9BA26FA

#### SMPlayer - http://smplayer.sourceforge.net/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E4A4F4F4

#### VirtualBox - http://www.virtualbox.org
## Run this command: wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -

#### VLC Media Player  - http://www.videolan.org/vlc/
## Run this command: sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 40130828


####### 3rd Party Source Repos

#### HandBrake (Source) - http://handbrake.fr/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 62D38753

#### Medibuntu (Source) - http://www.medibuntu.org/ 
## Run this command: sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update 

#### OpenShot (Source) - http://www.openshotvideo.com
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys B9BA26FA

#### SMPlayer (Source) - http://smplayer.sourceforge.net/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E4A4F4F4
# deb-src http://ppa.launchpad.net/rvm/smplayer/ubuntu lucid main

#### VLC Media Player  (Source) - http://www.videolan.org/vlc/
## Run this command: sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 40130828



deb http://us.archive.ubuntu.com/ubuntu/ oneiric-backports restricted main multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-backports restricted main multiverse universe
deb http://extras.ubuntu.com/ubuntu oneiric main #Third party developers repository
deb http://ppa.launchpad.net/motumedia/mplayer-daily/ubuntu oneiric main
deb-src http://ppa.launchpad.net/motumedia/mplayer-daily/ubuntu oneiric main
bryan@bryan-desktop:/media$ 
```


```
ls /etc/apt/sources.list.d/

cheleb-blender-svn-lucid.list
cheleb-blender-svn-lucid.list.distUpgrade
cheleb-blender-svn-lucid.list.save
cinelerra-ppa-ppa-lucid.list
cinelerra-ppa-ppa-lucid.list.distUpgrade
cinelerra-ppa-ppa-lucid.list.save
gezakovacs-ppa-lucid.list
gezakovacs-ppa-lucid.list.distUpgrade
gezakovacs-ppa-lucid.list.save
google-chrome.list.distUpgrade
google-chrome.list.save
google-talkplugin.list.distUpgrade
google-talkplugin.list.save
jonoomph-openshot-edge-lucid.list
jonoomph-openshot-edge-lucid.list.distUpgrade
jonoomph-openshot-edge-lucid.list.save
lucid-bleed-lucidbleed-exp-lucid.list
lucid-bleed-lucidbleed-exp-lucid.list.distUpgrade
lucid-bleed-lucidbleed-exp-lucid.list.save
lucid-bleed-ppa-lucid.list
lucid-bleed-ppa-lucid.list.distUpgrade
lucid-bleed-ppa-lucid.list.save
medibuntu.list
medibuntu.list.distUpgrade
medibuntu.list.save
motumedia-mplayer-daily-lucid.list
motumedia-mplayer-daily-lucid.list.distUpgrade
motumedia-mplayer-daily-lucid.list.save
n-muench-vlc2-lucid.list
n-muench-vlc2-lucid.list.distUpgrade
n-muench-vlc2-lucid.list.save
nvidia-vdpau-ppa-lucid.list
nvidia-vdpau-ppa-lucid.list.distUpgrade
nvidia-vdpau-ppa-lucid.list.save
opera.list
pitti-ppa-lucid.list
pitti-ppa-lucid.list.distUpgrade
pitti-ppa-lucid.list.save
pkgcrosswire-ppa-lucid.list
pkgcrosswire-ppa-lucid.list.distUpgrade
pkgcrosswire-ppa-lucid.list.save
rvm-smplayer-lucid.list
rvm-smplayer-lucid.list.distUpgrade
rvm-smplayer-lucid.list.save
stebbins-handbrake-snapshots-lucid.list
stebbins-handbrake-snapshots-lucid.list.distUpgrade
stebbins-handbrake-snapshots-lucid.list.save
sunab-kdenlive-oneiric-oneiric.list
sunab-kdenlive-oneiric-oneiric.list.save
sunab-kdenlive-release-lucid.list
sunab-kdenlive-release-lucid.list.distUpgrade
sunab-kdenlive-release-lucid.list.save
sunab-kdenlive-release-oneiric.list



```

---

### Post by tock on 2011-11-17
```
sudo apt-get remove ffmpeg x264 libx264-dev
[sudo] password for bryan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package x264 is not installed, so not removed
Package libx264-dev is not installed, so not removed
The following packages were automatically installed and are no longer required:
  dvgrab libxine1-x kdenlive-data libxine1-misc-plugins libxcb-xv0
  libxine1-bin libqjson0 libxine1-ffmpeg xine-ui libxine1-console libxine1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  ffmpeg kdenlive
0 upgraded, 0 newly installed, 2 to remove and 2 not upgraded.
After this operation, 5,607 kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: warning: ignoring option --foreign-architecture=i386: this architecture cannot be foreign
(Reading database ... 264142 files and directories currently installed.)
Removing kdenlive ...
Removing ffmpeg ...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for menu ...
Processing triggers for man-db ...
bryan@bryan-desktop:/media$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  dvgrab kdenlive-data libavfilter2 libqjson0 libxcb-xv0 libxine1 libxine1-bin
  libxine1-console libxine1-ffmpeg libxine1-misc-plugins libxine1-x xine-ui
0 upgraded, 0 newly installed, 12 to remove and 2 not upgraded.
After this operation, 23.6 MB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: warning: ignoring option --foreign-architecture=i386: this architecture cannot be foreign
(Reading database ... 264068 files and directories currently installed.)
Removing dvgrab ...
Removing kdenlive-data ...
Removing libavfilter2 ...
dpkg: warning: ignoring option --foreign-architecture=i386: this architecture cannot be foreign
dpkg: warning: ignoring option --foreign-architecture=i386: this architecture cannot be foreign
Removing libqjson0 ...
dpkg: warning: ignoring option --foreign-architecture=i386: this architecture cannot be foreign
Removing xine-ui ...
Removing libxine1 ...
Removing libxine1-x ...
Removing libxcb-xv0 ...
dpkg: warning: ignoring option --foreign-architecture=i386: this architecture cannot be foreign
Removing libxine1-misc-plugins ...
Removing libxine1-ffmpeg ...
Removing libxine1-console ...
Removing libxine1-bin ...
dpkg: warning: ignoring option --foreign-architecture=i386: this architecture cannot be foreign
Processing triggers for man-db ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'interface/x-winamp-skin'
Processing triggers for hicolor-icon-theme ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for menu ...
```


```
sudo apt-get update
Ign http://extras.ubuntu.com oneiric InRelease
Ign http://us.archive.ubuntu.com oneiric InRelease                             
Ign http://us.archive.ubuntu.com oneiric-security InRelease                    
Ign http://us.archive.ubuntu.com oneiric-updates InRelease                     
Ign http://deb.opera.com stable InRelease                                      
Hit http://extras.ubuntu.com oneiric Release.gpg                               
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://us.archive.ubuntu.com oneiric-proposed InRelease                    
Ign http://us.archive.ubuntu.com oneiric-backports InRelease                   
Hit http://us.archive.ubuntu.com oneiric Release.gpg                           
Hit http://packages.medibuntu.org oneiric InRelease                            
Hit http://deb.opera.com stable Release.gpg                                    
Hit http://extras.ubuntu.com oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://us.archive.ubuntu.com oneiric-security Release.gpg                  
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://deb.opera.com stable Release                                        
Hit http://us.archive.ubuntu.com oneiric-updates Release.gpg                   
Hit http://us.archive.ubuntu.com oneiric-proposed Release.gpg                  
Hit http://us.archive.ubuntu.com oneiric-backports Release.gpg                 
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://us.archive.ubuntu.com oneiric Release                               
Hit http://deb.opera.com stable/non-free i386 Packages                         
Hit http://packages.medibuntu.org oneiric/free i386 Packages                   
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://us.archive.ubuntu.com oneiric-security Release                      
Hit http://us.archive.ubuntu.com oneiric-updates Release                       
Hit http://us.archive.ubuntu.com oneiric-proposed Release                      
Ign http://deb.opera.com stable/non-free TranslationIndex                      
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://us.archive.ubuntu.com oneiric-backports Release                     
Hit http://us.archive.ubuntu.com oneiric/main Sources                          
Hit http://us.archive.ubuntu.com oneiric/restricted Sources                    
Hit http://us.archive.ubuntu.com oneiric/universe Sources                      
Hit http://us.archive.ubuntu.com oneiric/multiverse Sources                    
Hit http://us.archive.ubuntu.com oneiric/main i386 Packages                    
Hit http://packages.medibuntu.org oneiric/non-free i386 Packages               
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://us.archive.ubuntu.com oneiric/restricted i386 Packages              
Hit http://us.archive.ubuntu.com oneiric/universe i386 Packages                
Hit http://us.archive.ubuntu.com oneiric/multiverse i386 Packages              
Hit http://us.archive.ubuntu.com oneiric/main TranslationIndex                 
Hit http://us.archive.ubuntu.com oneiric/multiverse TranslationIndex           
Hit http://us.archive.ubuntu.com oneiric/restricted TranslationIndex           
Hit http://us.archive.ubuntu.com oneiric/universe TranslationIndex             
Hit http://us.archive.ubuntu.com oneiric-security/main Sources                 
Hit http://us.archive.ubuntu.com oneiric-security/restricted Sources           
Hit http://us.archive.ubuntu.com oneiric-security/universe Sources             
Hit http://us.archive.ubuntu.com oneiric-security/multiverse Sources           
Hit http://us.archive.ubuntu.com oneiric-security/main i386 Packages           
Hit http://us.archive.ubuntu.com oneiric-security/restricted i386 Packages     
Hit http://us.archive.ubuntu.com oneiric-security/universe i386 Packages       
Hit http://us.archive.ubuntu.com oneiric-security/multiverse i386 Packages     
Ign http://packages.medibuntu.org oneiric/free TranslationIndex                
Hit http://us.archive.ubuntu.com oneiric-security/main TranslationIndex        
Hit http://us.archive.ubuntu.com oneiric-security/multiverse TranslationIndex  
Hit http://us.archive.ubuntu.com oneiric-security/restricted TranslationIndex  
Hit http://us.archive.ubuntu.com oneiric-security/universe TranslationIndex    
Hit http://us.archive.ubuntu.com oneiric-updates/main Sources                  
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Sources            
Hit http://us.archive.ubuntu.com oneiric-updates/universe Sources              
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Sources            
Hit http://us.archive.ubuntu.com oneiric-updates/main i386 Packages            
Hit http://us.archive.ubuntu.com oneiric-updates/restricted i386 Packages      
Hit http://us.archive.ubuntu.com oneiric-updates/universe i386 Packages        
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse i386 Packages      
Hit http://us.archive.ubuntu.com oneiric-updates/main TranslationIndex         
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex   
Hit http://us.archive.ubuntu.com oneiric-updates/restricted TranslationIndex   
Ign http://packages.medibuntu.org oneiric/non-free TranslationIndex            
Hit http://us.archive.ubuntu.com oneiric-updates/universe TranslationIndex     
Hit http://us.archive.ubuntu.com oneiric-proposed/main Sources                 
Hit http://us.archive.ubuntu.com oneiric-proposed/restricted Sources           
Hit http://us.archive.ubuntu.com oneiric-proposed/universe Sources             
Hit http://us.archive.ubuntu.com oneiric-proposed/multiverse Sources           
Hit http://us.archive.ubuntu.com oneiric-proposed/main i386 Packages           
Hit http://us.archive.ubuntu.com oneiric-proposed/restricted i386 Packages     
Hit http://us.archive.ubuntu.com oneiric-proposed/universe i386 Packages       
Hit http://us.archive.ubuntu.com oneiric-proposed/multiverse i386 Packages     
Hit http://us.archive.ubuntu.com oneiric-proposed/main TranslationIndex        
Hit http://us.archive.ubuntu.com oneiric-proposed/multiverse TranslationIndex  
Hit http://us.archive.ubuntu.com oneiric-proposed/restricted TranslationIndex  
Hit http://us.archive.ubuntu.com oneiric-proposed/universe TranslationIndex    
Hit http://us.archive.ubuntu.com oneiric-backports/restricted Sources          
Hit http://us.archive.ubuntu.com oneiric-backports/main Sources                
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse Sources          
Hit http://us.archive.ubuntu.com oneiric-backports/universe Sources            
Hit http://us.archive.ubuntu.com oneiric-backports/restricted i386 Packages    
Hit http://us.archive.ubuntu.com oneiric-backports/main i386 Packages          
Ign http://extras.ubuntu.com oneiric/main Translation-en_US                    
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse i386 Packages    
Hit http://us.archive.ubuntu.com oneiric-backports/universe i386 Packages      
Hit http://us.archive.ubuntu.com oneiric-backports/main TranslationIndex       
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex 
Hit http://us.archive.ubuntu.com oneiric-backports/restricted TranslationIndex 
Hit http://us.archive.ubuntu.com oneiric-backports/universe TranslationIndex   
Ign http://extras.ubuntu.com oneiric/main Translation-en                       
Hit http://us.archive.ubuntu.com oneiric/main Translation-en                   
Hit http://us.archive.ubuntu.com oneiric/multiverse Translation-en             
Hit http://us.archive.ubuntu.com oneiric/restricted Translation-en             
Hit http://us.archive.ubuntu.com oneiric/universe Translation-en               
Hit http://us.archive.ubuntu.com oneiric-security/main Translation-en          
Hit http://us.archive.ubuntu.com oneiric-security/multiverse Translation-en    
Hit http://us.archive.ubuntu.com oneiric-security/restricted Translation-en    
Hit http://us.archive.ubuntu.com oneiric-security/universe Translation-en      
Hit http://us.archive.ubuntu.com oneiric-updates/main Translation-en           
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Translation-en     
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Translation-en     
Hit http://us.archive.ubuntu.com oneiric-updates/universe Translation-en       
Hit http://us.archive.ubuntu.com oneiric-proposed/main Translation-en          
Hit http://us.archive.ubuntu.com oneiric-proposed/multiverse Translation-en    
Hit http://us.archive.ubuntu.com oneiric-proposed/restricted Translation-en    
Hit http://us.archive.ubuntu.com oneiric-proposed/universe Translation-en      
Hit http://us.archive.ubuntu.com oneiric-backports/main Translation-en         
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse Translation-en   
Hit http://us.archive.ubuntu.com oneiric-backports/restricted Translation-en   
Hit http://us.archive.ubuntu.com oneiric-backports/universe Translation-en     
Ign http://deb.opera.com stable/non-free Translation-en_US                     
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://deb.opera.com stable/non-free Translation-en                        
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_US
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://packages.medibuntu.org oneiric/free Translation-en_US
Ign http://packages.medibuntu.org oneiric/free Translation-en
Ign http://packages.medibuntu.org oneiric/non-free Translation-en_US
Ign http://packages.medibuntu.org oneiric/non-free Translation-en
Reading package lists... Done        
```


 ```
sudo apt-get install build-essential checkinstall git libfaac-dev libjack-jackd2-dev \
>   libmp3lame-dev libopencore-amrnb-dev libopencore-amrwb-dev libsdl1.2-dev libtheora-dev \
>   libva-dev libvdpau-dev libvorbis-dev libx11-dev libxfixes-dev texi2html yasm zlib1g-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
git is already the newest version.
git set to manually installed.
libtheora-dev is already the newest version.
libvorbis-dev is already the newest version.
libx11-dev is already the newest version.
libxfixes-dev is already the newest version.
texi2html is already the newest version.
zlib1g-dev is already the newest version.
checkinstall is already the newest version.
libmp3lame-dev is already the newest version.
libopencore-amrnb-dev is already the newest version.
libopencore-amrwb-dev is already the newest version.
libfaac-dev is already the newest version.
yasm is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libsdl1.2-dev : Depends: libglu1-mesa-dev but it is not going to be installed
E: Unable to correct problems, you have held broken packages
```

---

### Post by raja.genupula on 2011-11-17
yeah now try to do 
```
sudo apt-get install -f
```

it will fix the problem of broken pkg's. 

all the best.

---

### Post by tock on 2011-11-17
No luck using the -f option.  Still getting the same error.

---

