---
title: "Unmet Dependancies"
date: 2012-02-11
forum: Installation &amp; Upgrades
---

### Post by TedinOz on 2012-02-11
I made the error of running Partial Upgrade through software updates. This was the first time that I had ever seen it and assumed that it was something I was required to do to allow all updates to be installed. As it was running it showed that 2 packages would be removed...Gimp and Xscreensaver. I have since successfully re-installed screensaver but am having a problem with Gimp.From all that I have now read since it is unwise to run Partial Upgrade. The overall system seems to be fine but I can't re-install Gimp.
```
 sudo apt-get install gimp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gimp : Depends: libglib2.0-0 (>= 2.31.2) but 2.30.0-0ubuntu4 is to be installed
E: Unable to correct problems, you have held broken packages.
```

I also tried to install with Synaptic Package manager but got error message saying fix broken packages. Trying to do that I got this message.[IMG][[IMG]http://img692.imageshack.us/img692/4508/brokenpackages.png[/IMG]](http://img692.imageshack.us/i/brokenpackages.png/)[/IMG]
In the software Center I had the same problems producing these results...
[IMG][[IMG]http://img96.imageshack.us/img96/7320/screenshotkrd.png[/IMG]](http://img96.imageshack.us/i/screenshotkrd.png/)[/IMG]

And these are the details...

```
The following packages have unmet dependencies:

gimp: Depends: python-gtk2 (>= 2.8.0) but 2.24.0-2 is to be installed
      Depends: libc6 (>= 2.11) but 2.13-20ubuntu5 is to be installed
      Depends: libfontconfig1 (>= 2.8.0) but 2.8.0-3ubuntu2 is to be installed
      Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but 2.24.0-1ubuntu1 is to be installed
      Depends: libglib2.0-0 (>= 2.31.2) but 2.30.0-0ubuntu4 is to be installed
      Depends: libgs9 (>= 8.61.dfsg.1) but 9.04~dfsg-0ubuntu11.5 is to be installed
      Depends: libgtk2.0-0 (>= 2.24.0) but 2.24.6-0ubuntu5 is to be installed
      Depends: libgudev-1.0-0 (>= 147) but 1:173-0ubuntu4.1 is to be installed
      Depends: libjpeg62 (>= 6b1) but 6b1-1ubuntu2 is to be installed
      Depends: librsvg2-2 (>= 2.14.4) but 2.34.1-2 is to be installed
      Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4.dfsg-3ubuntu3 is to be installed

```

Can anyone offer some help here? At worst I know I can run a fresh install and start again but would like to avoid that if possible. From all that I have read I have tried running the commands suggested every where...

sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install

...all with no reports of any errors.

Thanks in advance.

---

### Post by jerrrys on 2012-02-11
Got anything weird going on in your software sources?

In terminal enter:

gedit /etc/apt/sources.list

---

### Post by jerrrys on 2012-02-11
Another double post removed

---

### Post by TedinOz on 2012-02-11
> **jerrrys said:**
> Got anything weird going on in your software sources?

In terminal enter:

gedit /etc/apt/sources.list

I'm not sure if its weird or not. File out put below..

```
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://mirror.optus.net/ubuntu/ oneiric main restricted
deb-src http://mirror.optus.net/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.optus.net/ubuntu/ oneiric-updates main restricted
deb-src http://mirror.optus.net/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror.optus.net/ubuntu/ oneiric universe
deb-src http://mirror.optus.net/ubuntu/ oneiric universe
deb http://mirror.optus.net/ubuntu/ oneiric-updates universe
deb-src http://mirror.optus.net/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.optus.net/ubuntu/ oneiric multiverse
deb-src http://mirror.optus.net/ubuntu/ oneiric multiverse
deb http://mirror.optus.net/ubuntu/ oneiric-updates multiverse
deb-src http://mirror.optus.net/ubuntu/ oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://mirror.optus.net/ubuntu/ oneiric-backports main restricted universe multiverse
deb-src http://mirror.optus.net/ubuntu/ oneiric-backports main restricted universe multiverse

deb http://mirror.optus.net/ubuntu/ oneiric-security main restricted
deb-src http://mirror.optus.net/ubuntu/ oneiric-security main restricted
deb http://mirror.optus.net/ubuntu/ oneiric-security universe
deb-src http://mirror.optus.net/ubuntu/ oneiric-security universe
deb http://mirror.optus.net/ubuntu/ oneiric-security multiverse
deb-src http://mirror.optus.net/ubuntu/ oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu oneiric partner
deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main
```

Thanks for your input.

---

### Post by jerrrys on 2012-02-12
sudo apt-get purge --remove gimp

try that

and your sources looks ok

also

[https://answers.launchpad.net/ubuntu/+source/gimp/+question/130374](https://answers.launchpad.net/ubuntu/+source/gimp/+question/130374)

---

### Post by TedinOz on 2012-02-12
> **jerrrys said:**
> sudo apt-get purge --remove gimp

try that

and your sources looks ok

also

[https://answers.launchpad.net/ubuntu/+source/gimp/+question/130374](https://answers.launchpad.net/ubuntu/+source/gimp/+question/130374)

I ran all of these commands again, including those suggested in your link here but unfortunately no changes and still unable to install Gimp. The error seems to be very much related to running the Partial Upgrade as it removed Gimp which was working perfectly before that but now is no longer installed.

Here are outputs...

```
ted@ted-Satellite:~$ sudo apt-get purge --remove gimp
[sudo] password for ted: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gimp is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ted@ted-Satellite:~$ sudo apt-get remove gimp*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gimp-help-2
ted@ted-Satellite:~$ sudo apt-get clean
ted@ted-Satellite:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ted@ted-Satellite:~$ sudo apt-get update
Ign http://mirror.optus.net oneiric InRelease
Ign http://mirror.optus.net oneiric-updates InRelease                          
Ign http://mirror.optus.net oneiric-backports InRelease                        
Ign http://mirror.optus.net oneiric-security InRelease                         
Hit http://mirror.optus.net oneiric Release.gpg                                
Hit http://mirror.optus.net oneiric-updates Release.gpg                        
Hit http://mirror.optus.net oneiric-backports Release.gpg                      
Hit http://mirror.optus.net oneiric-security Release.gpg                       
Hit http://mirror.optus.net oneiric Release                                    
Hit http://mirror.optus.net oneiric-updates Release                            
Hit http://mirror.optus.net oneiric-backports Release                          
Hit http://mirror.optus.net oneiric-security Release                           
Hit http://mirror.optus.net oneiric/main Sources                               
Hit http://mirror.optus.net oneiric/restricted Sources                         
Hit http://mirror.optus.net oneiric/universe Sources                           
Hit http://mirror.optus.net oneiric/multiverse Sources                         
Hit http://mirror.optus.net oneiric/main i386 Packages                         
Hit http://mirror.optus.net oneiric/restricted i386 Packages                   
Hit http://mirror.optus.net oneiric/universe i386 Packages                     
Hit http://mirror.optus.net oneiric/multiverse i386 Packages                   
Hit http://mirror.optus.net oneiric/main TranslationIndex                      
Hit http://mirror.optus.net oneiric/multiverse TranslationIndex                
Hit http://mirror.optus.net oneiric/restricted TranslationIndex                
Hit http://mirror.optus.net oneiric/universe TranslationIndex                  
Hit http://mirror.optus.net oneiric-updates/main Sources                       
Hit http://mirror.optus.net oneiric-updates/restricted Sources                 
Hit http://mirror.optus.net oneiric-updates/universe Sources                   
Hit http://mirror.optus.net oneiric-updates/multiverse Sources                 
Hit http://mirror.optus.net oneiric-updates/main i386 Packages                 
Hit http://mirror.optus.net oneiric-updates/restricted i386 Packages           
Hit http://mirror.optus.net oneiric-updates/universe i386 Packages             
Hit http://mirror.optus.net oneiric-updates/multiverse i386 Packages           
Hit http://mirror.optus.net oneiric-updates/main TranslationIndex              
Hit http://mirror.optus.net oneiric-updates/multiverse TranslationIndex        
Hit http://mirror.optus.net oneiric-updates/restricted TranslationIndex        
Hit http://mirror.optus.net oneiric-updates/universe TranslationIndex          
Hit http://mirror.optus.net oneiric-backports/main Sources                     
Hit http://mirror.optus.net oneiric-backports/restricted Sources               
Hit http://mirror.optus.net oneiric-backports/universe Sources                 
Hit http://mirror.optus.net oneiric-backports/multiverse Sources               
Hit http://mirror.optus.net oneiric-backports/main i386 Packages               
Hit http://mirror.optus.net oneiric-backports/restricted i386 Packages         
Hit http://mirror.optus.net oneiric-backports/universe i386 Packages           
Hit http://mirror.optus.net oneiric-backports/multiverse i386 Packages         
Hit http://mirror.optus.net oneiric-backports/main TranslationIndex            
Hit http://mirror.optus.net oneiric-backports/multiverse TranslationIndex      
Hit http://mirror.optus.net oneiric-backports/restricted TranslationIndex      
Hit http://mirror.optus.net oneiric-backports/universe TranslationIndex        
Hit http://mirror.optus.net oneiric-security/main Sources                      
Hit http://mirror.optus.net oneiric-security/restricted Sources                
Hit http://mirror.optus.net oneiric-security/universe Sources                  
Hit http://mirror.optus.net oneiric-security/multiverse Sources                
Hit http://mirror.optus.net oneiric-security/main i386 Packages                
Hit http://mirror.optus.net oneiric-security/restricted i386 Packages          
Hit http://mirror.optus.net oneiric-security/universe i386 Packages            
Hit http://mirror.optus.net oneiric-security/multiverse i386 Packages          
Hit http://mirror.optus.net oneiric-security/main TranslationIndex             
Hit http://mirror.optus.net oneiric-security/multiverse TranslationIndex       
Hit http://mirror.optus.net oneiric-security/restricted TranslationIndex       
Hit http://mirror.optus.net oneiric-security/universe TranslationIndex         
Hit http://mirror.optus.net oneiric/main Translation-en_AU                     
Hit http://mirror.optus.net oneiric/main Translation-en                        
Hit http://packages.medibuntu.org oneiric InRelease                            
Ign http://archive.canonical.com oneiric InRelease                             
Hit http://mirror.optus.net oneiric/multiverse Translation-en_AU               
Hit http://mirror.optus.net oneiric/multiverse Translation-en                  
Hit http://mirror.optus.net oneiric/restricted Translation-en_AU               
Hit http://mirror.optus.net oneiric/restricted Translation-en                  
Hit http://mirror.optus.net oneiric/universe Translation-en                    
Hit http://mirror.optus.net oneiric-updates/main Translation-en                
Hit http://mirror.optus.net oneiric-updates/multiverse Translation-en          
Hit http://mirror.optus.net oneiric-updates/restricted Translation-en          
Hit http://mirror.optus.net oneiric-updates/universe Translation-en            
Hit http://mirror.optus.net oneiric-backports/main Translation-en              
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Hit http://mirror.optus.net oneiric-backports/multiverse Translation-en        
Hit http://mirror.optus.net oneiric-backports/restricted Translation-en        
Hit http://mirror.optus.net oneiric-backports/universe Translation-en          
Hit http://mirror.optus.net oneiric-security/main Translation-en               
Hit http://mirror.optus.net oneiric-security/multiverse Translation-en         
Hit http://mirror.optus.net oneiric-security/restricted Translation-en         
Hit http://mirror.optus.net oneiric-security/universe Translation-en           
Hit http://repository.spotify.com stable InRelease                             
Ign http://extras.ubuntu.com oneiric InRelease                                 
Hit http://archive.canonical.com oneiric Release.gpg                           
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Hit http://repository.spotify.com stable/non-free i386 Packages                
Hit http://extras.ubuntu.com oneiric Release.gpg                               
Hit http://packages.medibuntu.org oneiric/free i386 Packages                   
Hit http://archive.canonical.com oneiric Release                               
Ign http://repository.spotify.com stable/non-free TranslationIndex             
Hit http://extras.ubuntu.com oneiric Release                                   
Hit http://archive.canonical.com oneiric/partner Sources                       
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Hit http://packages.medibuntu.org oneiric/non-free i386 Packages               
Hit http://extras.ubuntu.com oneiric/main Sources                              
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Ign http://packages.medibuntu.org oneiric/free TranslationIndex                
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Ign http://packages.medibuntu.org oneiric/non-free TranslationIndex            
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release                                   
Ign http://repository.spotify.com stable/non-free Translation-en_AU            
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Ign http://repository.spotify.com stable/non-free Translation-en               
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Ign http://archive.canonical.com oneiric/partner Translation-en_AU             
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Ign http://extras.ubuntu.com oneiric/main Translation-en_AU                    
Hit http://ppa.launchpad.net oneiric Release                                   
Ign http://archive.canonical.com oneiric/partner Translation-en                
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Ign http://extras.ubuntu.com oneiric/main Translation-en                       
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources
Hit http://ppa.launchpad.net oneiric/main i386 Packages              
Ign http://ppa.launchpad.net oneiric/main TranslationIndex           
Hit http://ppa.launchpad.net oneiric/main Sources
Hit http://ppa.launchpad.net oneiric/main i386 Packages              
Ign http://ppa.launchpad.net oneiric/main TranslationIndex           
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources
Hit http://ppa.launchpad.net oneiric/main i386 Packages
Ign http://ppa.launchpad.net oneiric/main TranslationIndex
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex           
Hit http://ppa.launchpad.net oneiric/main Sources                    
Hit http://ppa.launchpad.net oneiric/main i386 Packages              
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                    
Hit http://ppa.launchpad.net oneiric/main i386 Packages              
Ign http://ppa.launchpad.net oneiric/main TranslationIndex           
Hit http://ppa.launchpad.net oneiric/main Sources                    
Hit http://ppa.launchpad.net oneiric/main i386 Packages
Ign http://ppa.launchpad.net oneiric/main TranslationIndex
Hit http://ppa.launchpad.net oneiric/main Sources
Hit http://ppa.launchpad.net oneiric/main i386 Packages              
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages              
Ign http://ppa.launchpad.net oneiric/main TranslationIndex           
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex           
Hit http://ppa.launchpad.net oneiric/main Sources                    
Hit http://ppa.launchpad.net oneiric/main i386 Packages              
Ign http://ppa.launchpad.net oneiric/main TranslationIndex           
Hit http://ppa.launchpad.net oneiric/main Sources                    
Hit http://ppa.launchpad.net oneiric/main i386 Packages              
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                    
Hit http://ppa.launchpad.net oneiric/main i386 Packages              
Ign http://ppa.launchpad.net oneiric/main TranslationIndex           
Hit http://ppa.launchpad.net oneiric/main Sources                    
Hit http://ppa.launchpad.net oneiric/main i386 Packages              
Ign http://ppa.launchpad.net oneiric/main TranslationIndex           
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Ign http://packages.medibuntu.org oneiric/free Translation-en_AU               
Ign http://dl.google.com stable InRelease                                      
Ign http://dl.google.com stable InRelease                                      
Ign http://packages.medibuntu.org oneiric/free Translation-en                  
Ign http://packages.medibuntu.org oneiric/non-free Translation-en_AU 
Ign http://packages.medibuntu.org oneiric/non-free Translation-en    
Ign http://dl.google.com stable InRelease                            
Get:1 http://dl.google.com stable Release.gpg [198 B]
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Get:2 http://dl.google.com stable Release.gpg [198 B]
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Get:3 http://dl.google.com stable Release.gpg [198 B]                          
Get:4 http://dl.google.com stable Release [1,347 B]                            
Get:5 http://dl.google.com stable Release [1,338 B]                            
Get:6 http://dl.google.com stable Release [1,347 B]                            
Get:7 http://dl.google.com stable/main i386 Packages [1,242 B]                 
Ign http://dl.google.com stable/main TranslationIndex                          
Get:8 http://dl.google.com stable/main i386 Packages [464 B]                   
Ign http://dl.google.com stable/main TranslationIndex                          
Get:9 http://dl.google.com stable/main i386 Packages [759 B]                   
Ign http://dl.google.com stable/main TranslationIndex                          
Ign http://dl.google.com stable/main Translation-en_AU                         
Ign http://dl.google.com stable/main Translation-en
Ign http://dl.google.com stable/main Translation-en_AU
Ign http://dl.google.com stable/main Translation-en
Ign http://dl.google.com stable/main Translation-en_AU
Ign http://dl.google.com stable/main Translation-en
Fetched 7,091 B in 3min 32s (33 B/s)
Reading package lists... Done
ted@ted-Satellite:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ted@ted-Satellite:~$ sudo apt-get install gimp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gimp : Depends: libglib2.0-0 (>= 2.31.2) but 2.30.0-0ubuntu4 is to be installed
E: Unable to correct problems, you have held broken packages.
ted@ted-Satellite:~$ 

```

Maybe I should think about a re-install of 11.10 and get back to before the Partial Upgrade went through?

---

### Post by jerrrys on 2012-02-12
<> **TedinOz said:**
> I ran all of these commands again, including those suggested in your link here but unfortunately no changes and still unable to install Gimp. The error seems to be very much related to running the Partial Upgrade as it removed Gimp which was working perfectly before that but now is no longer installed.

Here are outputs...

```
ted@ted-Satellite:~$ sudo apt-get purge --remove gimp
[sudo] password for ted: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gimp is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ted@ted-Satellite:~$ sudo apt-get remove gimp*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gimp-help-2
ted@ted-Satellite:~$ sudo apt-get clean
ted@ted-Satellite:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ted@ted-Satellite:~$ sudo apt-get update
Ign http://mirror.optus.net oneiric InRelease
Ign http://mirror.optus.net oneiric-updates InRelease                          
Ign http://mirror.optus.net oneiric-backports InRelease                        
Ign http://mirror.optus.net oneiric-security InRelease                         
Hit http://mirror.optus.net oneiric Release.gpg                                
Hit http://mirror.optus.net oneiric-updates Release.gpg                        
Hit http://mirror.optus.net oneiric-backports Release.gpg                      
Hit http://mirror.optus.net oneiric-security Release.gpg                       
Hit http://mirror.optus.net oneiric Release                                    
Hit http://mirror.optus.net oneiric-updates Release                            
Hit http://mirror.optus.net oneiric-backports Release                          
Hit http://mirror.optus.net oneiric-security Release                           
Hit http://mirror.optus.net oneiric/main Sources                               
Hit http://mirror.optus.net oneiric/restricted Sources                         
Hit http://mirror.optus.net oneiric/universe Sources                           
Hit http://mirror.optus.net oneiric/multiverse Sources                         
Hit http://mirror.optus.net oneiric/main i386 Packages                         
Hit http://mirror.optus.net oneiric/restricted i386 Packages                   
Hit http://mirror.optus.net oneiric/universe i386 Packages                     
Hit http://mirror.optus.net oneiric/multiverse i386 Packages                   
Hit http://mirror.optus.net oneiric/main TranslationIndex                      
Hit http://mirror.optus.net oneiric/multiverse TranslationIndex                
Hit http://mirror.optus.net oneiric/restricted TranslationIndex                
Hit http://mirror.optus.net oneiric/universe TranslationIndex                  
Hit http://mirror.optus.net oneiric-updates/main Sources                       
Hit http://mirror.optus.net oneiric-updates/restricted Sources                 
Hit http://mirror.optus.net oneiric-updates/universe Sources                   
Hit http://mirror.optus.net oneiric-updates/multiverse Sources                 
Hit http://mirror.optus.net oneiric-updates/main i386 Packages                 
Hit http://mirror.optus.net oneiric-updates/restricted i386 Packages           
Hit http://mirror.optus.net oneiric-updates/universe i386 Packages             
Hit http://mirror.optus.net oneiric-updates/multiverse i386 Packages           
Hit http://mirror.optus.net oneiric-updates/main TranslationIndex              
Hit http://mirror.optus.net oneiric-updates/multiverse TranslationIndex        
Hit http://mirror.optus.net oneiric-updates/restricted TranslationIndex        
Hit http://mirror.optus.net oneiric-updates/universe TranslationIndex          
Hit http://mirror.optus.net oneiric-backports/main Sources                     
Hit http://mirror.optus.net oneiric-backports/restricted Sources               
Hit http://mirror.optus.net oneiric-backports/universe Sources                 
Hit http://mirror.optus.net oneiric-backports/multiverse Sources               
Hit http://mirror.optus.net oneiric-backports/main i386 Packages               
Hit http://mirror.optus.net oneiric-backports/restricted i386 Packages         
Hit http://mirror.optus.net oneiric-backports/universe i386 Packages           
Hit http://mirror.optus.net oneiric-backports/multiverse i386 Packages         
Hit http://mirror.optus.net oneiric-backports/main TranslationIndex            
Hit http://mirror.optus.net oneiric-backports/multiverse TranslationIndex      
Hit http://mirror.optus.net oneiric-backports/restricted TranslationIndex      
Hit http://mirror.optus.net oneiric-backports/universe TranslationIndex        
Hit http://mirror.optus.net oneiric-security/main Sources                      
Hit http://mirror.optus.net oneiric-security/restricted Sources                
Hit http://mirror.optus.net oneiric-security/universe Sources                  
Hit http://mirror.optus.net oneiric-security/multiverse Sources                
Hit http://mirror.optus.net oneiric-security/main i386 Packages                
Hit http://mirror.optus.net oneiric-security/restricted i386 Packages          
Hit http://mirror.optus.net oneiric-security/universe i386 Packages            
Hit http://mirror.optus.net oneiric-security/multiverse i386 Packages          
Hit http://mirror.optus.net oneiric-security/main TranslationIndex             
Hit http://mirror.optus.net oneiric-security/multiverse TranslationIndex       
Hit http://mirror.optus.net oneiric-security/restricted TranslationIndex       
Hit http://mirror.optus.net oneiric-security/universe TranslationIndex         
Hit http://mirror.optus.net oneiric/main Translation-en_AU                     
Hit http://mirror.optus.net oneiric/main Translation-en                        
Hit http://packages.medibuntu.org oneiric InRelease                            
Ign http://archive.canonical.com oneiric InRelease                             
Hit http://mirror.optus.net oneiric/multiverse Translation-en_AU               
Hit http://mirror.optus.net oneiric/multiverse Translation-en                  
Hit http://mirror.optus.net oneiric/restricted Translation-en_AU               
Hit http://mirror.optus.net oneiric/restricted Translation-en                  
Hit http://mirror.optus.net oneiric/universe Translation-en                    
Hit http://mirror.optus.net oneiric-updates/main Translation-en                
Hit http://mirror.optus.net oneiric-updates/multiverse Translation-en          
Hit http://mirror.optus.net oneiric-updates/restricted Translation-en          
Hit http://mirror.optus.net oneiric-updates/universe Translation-en            
Hit http://mirror.optus.net oneiric-backports/main Translation-en              
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Hit http://mirror.optus.net oneiric-backports/multiverse Translation-en        
Hit http://mirror.optus.net oneiric-backports/restricted Translation-en        
Hit http://mirror.optus.net oneiric-backports/universe Translation-en          
Hit http://mirror.optus.net oneiric-security/main Translation-en               
Hit http://mirror.optus.net oneiric-security/multiverse Translation-en         
Hit http://mirror.optus.net oneiric-security/restricted Translation-en         
Hit http://mirror.optus.net oneiric-security/universe Translation-en           
Hit http://repository.spotify.com stable InRelease                             
Ign http://extras.ubuntu.com oneiric InRelease                                 
Hit http://archive.canonical.com oneiric Release.gpg                           
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Hit http://repository.spotify.com stable/non-free i386 Packages                
Hit http://extras.ubuntu.com oneiric Release.gpg                               
Hit http://packages.medibuntu.org oneiric/free i386 Packages                   
Hit http://archive.canonical.com oneiric Release                               
Ign http://repository.spotify.com stable/non-free TranslationIndex             
Hit http://extras.ubuntu.com oneiric Release                                   
Hit http://archive.canonical.com oneiric/partner Sources                       
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Hit http://packages.medibuntu.org oneiric/non-free i386 Packages               
Hit http://extras.ubuntu.com oneiric/main Sources                              
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Ign http://packages.medibuntu.org oneiric/free TranslationIndex                
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Ign http://packages.medibuntu.org oneiric/non-free TranslationIndex            
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release                                   
Ign http://repository.spotify.com stable/non-free Translation-en_AU            
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Ign http://repository.spotify.com stable/non-free Translation-en               
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Ign http://archive.canonical.com oneiric/partner Translation-en_AU             
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Ign http://extras.ubuntu.com oneiric/main Translation-en_AU                    
Hit http://ppa.launchpad.net oneiric Release                                   
Ign http://archive.canonical.com oneiric/partner Translation-en                
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Ign http://extras.ubuntu.com oneiric/main Translation-en                       
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources
Hit http://ppa.launchpad.net oneiric/main i386 Packages              
Ign http://ppa.launchpad.net oneiric/main TranslationIndex           
Hit http://ppa.launchpad.net oneiric/main Sources
Hit http://ppa.launchpad.net oneiric/main i386 Packages              
Ign http://ppa.launchpad.net oneiric/main TranslationIndex           
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources
Hit http://ppa.launchpad.net oneiric/main i386 Packages
Ign http://ppa.launchpad.net oneiric/main TranslationIndex
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex           
Hit http://ppa.launchpad.net oneiric/main Sources                    
Hit http://ppa.launchpad.net oneiric/main i386 Packages              
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                    
Hit http://ppa.launchpad.net oneiric/main i386 Packages              
Ign http://ppa.launchpad.net oneiric/main TranslationIndex           
Hit http://ppa.launchpad.net oneiric/main Sources                    
Hit http://ppa.launchpad.net oneiric/main i386 Packages
Ign http://ppa.launchpad.net oneiric/main TranslationIndex
Hit http://ppa.launchpad.net oneiric/main Sources
Hit http://ppa.launchpad.net oneiric/main i386 Packages              
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages              
Ign http://ppa.launchpad.net oneiric/main TranslationIndex           
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex           
Hit http://ppa.launchpad.net oneiric/main Sources                    
Hit http://ppa.launchpad.net oneiric/main i386 Packages              
Ign http://ppa.launchpad.net oneiric/main TranslationIndex           
Hit http://ppa.launchpad.net oneiric/main Sources                    
Hit http://ppa.launchpad.net oneiric/main i386 Packages              
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                    
Hit http://ppa.launchpad.net oneiric/main i386 Packages              
Ign http://ppa.launchpad.net oneiric/main TranslationIndex           
Hit http://ppa.launchpad.net oneiric/main Sources                    
Hit http://ppa.launchpad.net oneiric/main i386 Packages              
Ign http://ppa.launchpad.net oneiric/main TranslationIndex           
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Ign http://packages.medibuntu.org oneiric/free Translation-en_AU               
Ign http://dl.google.com stable InRelease                                      
Ign http://dl.google.com stable InRelease                                      
Ign http://packages.medibuntu.org oneiric/free Translation-en                  
Ign http://packages.medibuntu.org oneiric/non-free Translation-en_AU 
Ign http://packages.medibuntu.org oneiric/non-free Translation-en    
Ign http://dl.google.com stable InRelease                            
Get:1 http://dl.google.com stable Release.gpg [198 B]
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Get:2 http://dl.google.com stable Release.gpg [198 B]
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_AU                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Get:3 http://dl.google.com stable Release.gpg [198 B]                          
Get:4 http://dl.google.com stable Release [1,347 B]                            
Get:5 http://dl.google.com stable Release [1,338 B]                            
Get:6 http://dl.google.com stable Release [1,347 B]                            
Get:7 http://dl.google.com stable/main i386 Packages [1,242 B]                 
Ign http://dl.google.com stable/main TranslationIndex                          
Get:8 http://dl.google.com stable/main i386 Packages [464 B]                   
Ign http://dl.google.com stable/main TranslationIndex                          
Get:9 http://dl.google.com stable/main i386 Packages [759 B]                   
Ign http://dl.google.com stable/main TranslationIndex                          
Ign http://dl.google.com stable/main Translation-en_AU                         
Ign http://dl.google.com stable/main Translation-en
Ign http://dl.google.com stable/main Translation-en_AU
Ign http://dl.google.com stable/main Translation-en
Ign http://dl.google.com stable/main Translation-en_AU
Ign http://dl.google.com stable/main Translation-en
Fetched 7,091 B in 3min 32s (33 B/s)
Reading package lists... Done
ted@ted-Satellite:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ted@ted-Satellite:~$ sudo apt-get install gimp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gimp : Depends: libglib2.0-0 (>= 2.31.2) but 2.30.0-0ubuntu4 is to be installed
E: Unable to correct problems, you have held broken packages.
ted@ted-Satellite:~$ 

```Maybe I should think about a re-install of 11.10 and get back to before the Partial Upgrade went through?>

I don't understand all the PPA's in this.  If this is a fairly fresh install you may be better off just doing that (reinstall Ubuntu).

GIMP seems to be stuck in partial limbo.  One last suggestion for tonight.

In terminal enter:

gksudo nautilus

Go to "File System" and do a search on GIMP and manually remove all gimp files and folders.

Good Luck

---

### Post by ottosykora on 2012-02-12
hmmm, but so far I know, there is no gimp for 11.10 and it can not be installed and is not compatible with 11.10.

One of many reasons I still did not upgrade to 11.10.

---

### Post by jerrrys on 2012-02-12
> **ottosykora said:**
> hmmm, but so far I know, there is no gimp for 11.10 and it can not be installed and is not compatible with 11.10.

One of many reasons I still did not upgrade to 11.10.

Gimp works in 11.10; Im running it.  It has a few glitches, but no show stoppers.

---

### Post by ottosykora on 2012-02-12
>Gimp works in 11.10; Im running it. It has a few glitches, but no show stoppers.<

but how did you install it? From someppa?

As in general gimp is removed by the installation of 11.10 because dependencies can be met.

---

### Post by jerrrys on 2012-02-12
I installed from the software center (synaptic really).

As for PPA's; check this out:

[http://ubuntuforums.org/showthread.php?p=11682384#post11682384](http://ubuntuforums.org/showthread.php?p=11682384#post11682384)

---

### Post by TedinOz on 2012-02-12
> **jerrrys said:**
> I installed from the software center (synaptic really).

As for PPA's; check this out:

[http://ubuntuforums.org/showthread.php?p=11682384#post11682384](http://ubuntuforums.org/showthread.php?p=11682384#post11682384)

Thanks for the link. Ultimately that solved it for me although not without some extra work which I will describe here for others if they have the same problems. 
Firstly after adding the PPA's and running update I was given the error message W: GPG error:The following signatures couldn't be verified because the public key is not available: NO_PUBKEY..........
I used this solution to fix that [http://en.kioskea.net/faq/809-debian-apt-get-no-pubkey-gpg-error#solution](http://en.kioskea.net/faq/809-debian-apt-get-no-pubkey-gpg-error#solution) then rebooted ans was able to install Gimp.

Then when I tried to run Gimp I got this new error....



[IMG][[IMG]http://img853.imageshack.us/img853/6572/gimpmessage.png[/IMG]](http://img853.imageshack.us/i/gimpmessage.png/)[/IMG]



Using Synaptic I was able to locate GTK+version 2.24.6 and was able to force an upgrade to 2.24.8. This worked as far as gimp is concerned which now works but has created a new problem in that it has somehow disabled Nautilus and I can't open files from dash and get this new error message.


[IMG][[IMG]http://img269.imageshack.us/img269/7086/filemanagerk.png[/IMG]](http://img269.imageshack.us/i/filemanagerk.png/)[/IMG]

 I have only just discovered this when trying to open screenshots to upload here. I can still access the files using Imageshack but to try to open Home from dash does nothing and to try to open a file from within unity gives me the message above.

After I have finished this posting I will reboot to see if that fixes it and report back. Complicated huh?

Thanks again for ongoing input.

---

### Post by TedinOz on 2012-02-12
Update...

A reboot fixed the Nautilus problem even though it played havoc with my themes settings. I have been able to re-set those through Ubuntu Tweak. And Gimp is still working :)

@ jerrrys..Thanks for preventing me from doing a fresh install. This exercise was certainly quicker than that and has contributed greatly to my learning experience as this forum always does :)

Thanks also to others who got involved.

I will mark this solved.

---

