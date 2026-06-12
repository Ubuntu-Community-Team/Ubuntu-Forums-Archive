---
title: "Can't Install a LOT of Various Packages"
date: 2012-07-13
forum: Installation &amp; Upgrades
---

### Post by clappboard on 2012-07-13
Lately, I can't install any of a variety of packages either via cli or ubuntu software center (I'm interested namely in playonlinux).  I always get a spiralling dependancy tree, none of the packages able to be installed.
These are the errors I get:
_Terminal:_
```
username@hostname:~$ sudo apt-get install playonlinux
[sudo] password for username: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 playonlinux : Depends: wine or
                        wine-unstable but it is not installable
E: Unable to correct problems, you have held broken packages.
```_Software Centre_
```
The following packages have unmet dependencies:

playonlinux: Depends: x-terminal-emulator but it is a virtual package
```I suspect that the problem is architecture related, as I'm running 64-bit precise.
Any help is appreciated.

---

### Post by cortman on 2012-07-13
Have you tried running

```
sudo apt-get -f install
```

?

---

### Post by clappboard on 2012-07-13
Same error when using the -f flag.

---

### Post by cortman on 2012-07-13
> **clappboard said:**
> Same error when using the -f flag.

Try running

```
sudo apt-get install gnome-terminal --reinstall
```

Then try installing playonlinux.

---

### Post by clappboard on 2012-07-13
I tried that to no avail.  Like I said, I think is has something to do with the 64-bit architecture.  It affects not just playonlinux but also other, seemingly _random_ packages.

---

### Post by clappboard on 2012-07-13
Here's what I mean about the impossible dependancy situation:
```

username@hostname:~$ sudo apt-get install playonlinux
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 playonlinux : Depends: wine or
                        wine-unstable but it is not installable
E: Unable to correct problems, you have held broken packages.
username@hostname:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine1.5 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
username@hostname:~$ sudo apt-get install wine1.5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 wine1.5 : Depends: wine1.5-amd64 (= 1.5.8-0ubuntu2~pulse18) but it is not going to be installed
           Depends: wine1.5-i386 (= 1.5.8-0ubuntu2~pulse18)
           Recommends: winbind
E: Unable to correct problems, you have held broken packages.
username@hostname:~$ sudo apt-get install wine1.5-amd64
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 wine1.5-amd64 : Depends: wine1.5:any (= 1.5.8-0ubuntu2~pulse18)
                 Recommends: gettext but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
username@hostname:~$ sudo apt-get install wine1.5:any
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 wine1.5 : Depends: wine1.5-amd64 (= 1.5.8-0ubuntu2~pulse18) but it is not going to be installed
           Depends: wine1.5-i386 (= 1.5.8-0ubuntu2~pulse18)
           Recommends: winbind
E: Unable to correct problems, you have held broken packages.
```

---

### Post by cortman on 2012-07-13
Hm, I kind of doubt it has much to do with processor architecture, but I won't say for certain.
Here's a couple more commands to run:

```
sudo rm -r /var/cache/apt/archives/*.deb
sudo apt-get autoclean
sudo apt-get update

```

---

### Post by clappboard on 2012-07-14
I tried running those commands then installing, and still no luck.  I'm wondering if there's a decrepid or 'broken' package somewhere in my system that wine depends on...?

---

### Post by oldos2er on 2012-07-14
Have you run ```
sudo apt-get update
``` lately?

Would you mind posting your sources.list? ```
cat /etc/apt/sources.list && ls /etc/apt/sources.list.d/
```

---

### Post by clappboard on 2012-07-14
> **oldos2er said:**
> Have you run ```
sudo apt-get update
``` lately?

Would you mind posting your sources.list? ```
cat /etc/apt/sources.list && ls /etc/apt/sources.list.d/
```

Here it is:
```
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ precise universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ precise multiverse

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

#user added
atareao-lenses-precise.list
atareao-lenses-precise.list.save
diesch-testing-precise.list
diesch-testing-precise.list.save
google-chrome.list
google-chrome.list.save
indicator-multiload-stable-daily-precise.list
indicator-multiload-stable-daily-precise.list.save
jsevi83-unity-precise.list
jsevi83-unity-precise.list.save
markjtully-ppa-precise.list
markjtully-ppa-precise.list.save
otto-kesselgulasch-gimp-precise.list
otto-kesselgulasch-gimp-precise.list.save
private-ppa.launchpad.net_commercial-ppa-uploaders_blocks-on-ice_ubuntu.list
private-ppa.launchpad.net_commercial-ppa-uploaders_blocks-on-ice_ubuntu.list.save
private-ppa.launchpad.net_commercial-ppa-uploaders_intellij-idea-ce_ubuntu.list
scopes-packagers-ppa-precise.list
scopes-packagers-ppa-precise.list.save
tiheum-equinox-precise.list
ubuntu-wine-ppa-precise.list
ubuntu-wine-ppa-precise.list.save
webupd8team-jupiter-precise.list
webupd8team-jupiter-precise.list.save
```

---

### Post by cortman on 2012-07-14
Whoa- what's with all the "user added" stuff- did you add that manually?

---

### Post by clappboard on 2012-07-15
> **cortman said:**
> Whoa- what's with all the "user added" stuff- did you add that manually?
Yeah.  Well, i used "sudo apt-add-repository [ppa-repository]" for a lot of them...  I'm not sure if that counts as "manually."  I like to keep them all separated from the ones Ubuntu ships with in case I run into problems, in which case it's easier to find and remove them.  This is only a new install, too.  Give it a few months and I'll have a lot more in there ;)

---

### Post by oldos2er on 2012-07-15
Could you run ```
sudo apt-get update && sudo apt-get install playonlinux
``` and post the output here?

---

### Post by clappboard on 2012-07-15
> **oldos2er said:**
> Could you run ```
sudo apt-get update && sudo apt-get install playonlinux
``` and post the output here?
```
username@hostname:~$ sudo apt-get update && sudo apt-get install playonlinux
[sudo] password for username: 
Ign http://ca.archive.ubuntu.com precise InRelease                                                                                            
Ign http://extras.ubuntu.com precise InRelease                                                                                                
Ign http://ppa.launchpad.net precise InRelease                      
Ign http://ppa.launchpad.net precise InRelease                      
Ign http://ppa.launchpad.net precise InRelease                                             
Ign http://dl.google.com stable InRelease                                                  
Hit http://ca.archive.ubuntu.com precise Release.gpg                                       
Hit http://extras.ubuntu.com precise Release.gpg                     
Get:1 http://dl.google.com stable Release.gpg [198 B]                
Hit http://ca.archive.ubuntu.com precise Release                                                      
Get:2 http://dl.google.com stable Release [1,347 B]                                         
Hit http://ca.archive.ubuntu.com precise/main Sources                                           
Hit http://extras.ubuntu.com precise Release                         
Ign http://ppa.launchpad.net precise InRelease                        
Ign http://ppa.launchpad.net precise InRelease                       
Ign http://ppa.launchpad.net precise InRelease                       
Get:3 http://dl.google.com stable/main amd64 Packages [1,233 B]      
Hit http://ca.archive.ubuntu.com precise/restricted Sources                
Hit http://ca.archive.ubuntu.com precise/universe Sources
Hit http://ca.archive.ubuntu.com precise/multiverse Sources
Hit http://ca.archive.ubuntu.com precise/main amd64 Packages
Hit http://ca.archive.ubuntu.com precise/restricted amd64 Packages
Hit http://ca.archive.ubuntu.com precise/universe amd64 Packages
Hit http://ca.archive.ubuntu.com precise/multiverse amd64 Packages
Hit http://ca.archive.ubuntu.com precise/main i386 Packages
Hit http://ca.archive.ubuntu.com precise/restricted i386 Packages
Hit http://ca.archive.ubuntu.com precise/universe i386 Packages
Hit http://extras.ubuntu.com precise/main Sources                     
Get:4 http://dl.google.com stable/main i386 Packages [1,224 B]       
Hit http://ca.archive.ubuntu.com precise/multiverse i386 Packages                           
Hit http://ca.archive.ubuntu.com precise/main TranslationIndex        
Ign http://dl.google.com stable/main TranslationIndex                 
Hit http://extras.ubuntu.com precise/main amd64 Packages              
Hit http://extras.ubuntu.com precise/main i386 Packages
Hit http://ca.archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://ca.archive.ubuntu.com precise/restricted TranslationIndex
Hit http://ca.archive.ubuntu.com precise/universe TranslationIndex
Ign http://ppa.launchpad.net precise InRelease  
Ign http://ppa.launchpad.net precise InRelease                                              
Hit http://ca.archive.ubuntu.com precise/main Translation-en_CA                             
Hit http://ca.archive.ubuntu.com precise/main Translation-en                                
Hit http://ca.archive.ubuntu.com precise/multiverse Translation-en    
Hit http://ca.archive.ubuntu.com precise/restricted Translation-en    
Hit http://ca.archive.ubuntu.com precise/universe Translation-en_CA                         
Hit http://ca.archive.ubuntu.com precise/universe Translation-en                            
Ign http://ppa.launchpad.net precise InRelease                        
Hit http://ppa.launchpad.net precise Release.gpg                      
Hit http://ppa.launchpad.net precise Release.gpg
Hit http://ppa.launchpad.net precise Release.gpg
Hit http://ppa.launchpad.net precise Release.gpg
Hit http://ppa.launchpad.net precise Release.gpg
Hit http://ppa.launchpad.net precise Release.gpg                      
Hit http://ppa.launchpad.net precise Release.gpg                      
Ign http://extras.ubuntu.com precise/main TranslationIndex            
Hit http://ppa.launchpad.net precise Release.gpg                      
Hit http://ppa.launchpad.net precise Release.gpg
Ign http://dl.google.com stable/main Translation-en_CA
Hit http://ppa.launchpad.net precise Release    
Hit http://ppa.launchpad.net precise Release    
Hit http://ppa.launchpad.net precise Release    
Hit http://ppa.launchpad.net precise Release    
Hit http://ppa.launchpad.net precise Release    
Ign http://dl.google.com stable/main Translation-en                                          
Hit http://ppa.launchpad.net precise Release                         
Hit http://ppa.launchpad.net precise Release   
Hit http://ppa.launchpad.net precise Release                          
Hit http://ppa.launchpad.net precise Release   
Hit http://ppa.launchpad.net precise/main Sources                     
Hit http://ppa.launchpad.net precise/main amd64 Packages
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main amd64 Packages
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main amd64 Packages
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Ign http://extras.ubuntu.com precise/main Translation-en_CA
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main amd64 Packages
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main amd64 Packages
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main amd64 Packages
Ign http://extras.ubuntu.com precise/main Translation-en
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Ign https://private-ppa.launchpad.net precise InRelease
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main amd64 Packages
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main amd64 Packages
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main amd64 Packages
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Ign https://private-ppa.launchpad.net precise InRelease
Hit https://private-ppa.launchpad.net precise Release.gpg
Hit https://private-ppa.launchpad.net precise Release.gpg
Hit https://private-ppa.launchpad.net precise Release                                                                                         
Hit https://private-ppa.launchpad.net precise Release                                                                                         
Hit https://private-ppa.launchpad.net precise/main amd64 Packages                                                                             
Hit https://private-ppa.launchpad.net precise/main i386 Packages                                                                              
Ign https://private-ppa.launchpad.net precise/main TranslationIndex                                                                           
Ign http://ppa.launchpad.net precise/main Translation-en_CA                                                                                   
Ign http://ppa.launchpad.net precise/main Translation-en                                                                                      
Ign http://ppa.launchpad.net precise/main Translation-en_CA                                                                                   
Ign http://ppa.launchpad.net precise/main Translation-en                                                                                      
Ign http://ppa.launchpad.net precise/main Translation-en_CA                                                                                   
Ign http://ppa.launchpad.net precise/main Translation-en                                                                                      
Ign http://ppa.launchpad.net precise/main Translation-en_CA                                                                                   
Ign http://ppa.launchpad.net precise/main Translation-en                                                                                      
Ign http://ppa.launchpad.net precise/main Translation-en_CA                                                                                   
Ign http://ppa.launchpad.net precise/main Translation-en                                                                                      
Ign http://ppa.launchpad.net precise/main Translation-en_CA                                                                                   
Ign http://ppa.launchpad.net precise/main Translation-en                                                                                      
Ign http://ppa.launchpad.net precise/main Translation-en_CA                                                                                   
Ign http://ppa.launchpad.net precise/main Translation-en                                                                                      
Hit https://private-ppa.launchpad.net precise/main amd64 Packages                                                                             
Ign http://ppa.launchpad.net precise/main Translation-en_CA                                                                                   
Ign http://ppa.launchpad.net precise/main Translation-en                                                                                      
Ign http://ppa.launchpad.net precise/main Translation-en_CA                                                                                   
Ign http://ppa.launchpad.net precise/main Translation-en                                                                                      
Hit https://private-ppa.launchpad.net precise/main i386 Packages                                                                              
Ign https://private-ppa.launchpad.net precise/main TranslationIndex                                                                           
Ign https://private-ppa.launchpad.net precise/main Translation-en_CA                                                                          
Ign https://private-ppa.launchpad.net precise/main Translation-en
Ign https://private-ppa.launchpad.net precise/main Translation-en_CA
Ign https://private-ppa.launchpad.net precise/main Translation-en
Fetched 4,002 B in 26s (149 B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 playonlinux : Depends: wine or
                        wine-unstable but it is not installable
E: Unable to correct problems, you have held broken packages.
```

---

### Post by clappboard on 2012-07-16
Okay so I've fiddled around a bit, and now when I try to mark playonlinux for installation in synaptic, it wants to remove all the currently installed packages and install a handful of new ones, and if I say yes it fails to mark for install.  I'm not sure what to do...

---

### Post by cortman on 2012-07-16
> **clappboard said:**
> Okay so I've fiddled around a bit, and now when I try to mark playonlinux for installation in synaptic, it wants to remove all the currently installed packages and install a handful of new ones, and if I say yes it fails to mark for install.  I'm not sure what to do...

Wants to remove all installed Wine related packages? Could you post a list of what it wants to remove?

---

### Post by clappboard on 2012-07-16
> **cortman said:**
> Wants to remove all installed Wine related packages? Could you post a list of what it wants to remove?
No, all as in ALL packages.  The list won't let me copy and paste, but it spans a to z.

---

### Post by cortman on 2012-07-17
I'd want oldos2er's input here; but it looks like a borked package system to me (one of a Linux user's worst nightmares). Before you proceed any further, I'd recommend backing up all your personal files or anything that you don't want to lose.
Depending what Ann suggests, I'd almost just say let Synaptic do what it wants to.

---

### Post by clappboard on 2012-07-17
> **cortman said:**
> I'd want oldos2er's input here; but it looks like a borked package system to me (one of a Linux user's worst nightmares). Before you proceed any further, I'd recommend backing up all your personal files or anything that you don't want to lose.
Depending what Ann suggests, I'd almost just say let Synaptic do what it wants to.
I back up multiple times a day, so that's not a problem ;)  And as far as letting synaptic do what it wants, the operation fails every time with this error message: ```
playonlinux:
 Depends: wine or
     wine-unstable  but it is not installable
 Depends: python-wxgtk2.8 but it is not going to be installed
 Depends: imagemagick
 Depends: gettext-base but it is not going to be installed
 Depends: icoutils

```

---

### Post by oldos2er on 2012-07-17
> **cortman said:**
> Depending what Ann suggests, 

Ann is out of suggestions here, which is why I haven't posted back. The only other thing I'd try would be to change servers to the main server and retry sudo apt-get update etc.

```
gksu software-properties-gtk
``` Download from:, Main server.

---

### Post by cortman on 2012-07-17
> **clappboard said:**
> I back up multiple times a day, so that's not a problem ;)  And as far as letting synaptic do what it wants, the operation fails every time with this error message: ```
playonlinux:
 Depends: wine or
     wine-unstable  but it is not installable
 Depends: python-wxgtk2.8 but it is not going to be installed
 Depends: imagemagick
 Depends: gettext-base but it is not going to be installed
 Depends: icoutils

```

This error almost always means you just need to re-update the lists (sudo apt-get update) but you've obviously done that. Perhaps you should try commenting out each of your added repositories in sources.list, run apt-get update, then try. If it goes through, uncomment them one at a time until you find a culprit (if indeed that is the problem).
Otherwise, I'm also out of suggestions, other than... reinstall Ubuntu? :? Not fun, I know.

---

### Post by clappboard on 2012-07-17
No luck with the main server either...  I think I'll try a clean install and go from there.  I'll post my results in a few hours.  Thanks for all the help guys (and girls)!

---

### Post by clappboard on 2012-07-17
So I did a clean 64-bit install, and it's working now!  I updated and upgraded everything, then install playonlinux, and it installed no problem.  Marking as...solved...?  It's not really a solution, but it's close.  Thanks for all the help and support everyone! :)

---

### Post by cortman on 2012-07-17
> **clappboard said:**
> So I did a clean 64-bit install, and it's working now!  I updated and upgraded everything, then install playonlinux, and it installed no problem.  Marking as...solved...?  It's not really a solution, but it's close.  Thanks for all the help and support everyone! :)

I'm sorry we couldn't be more helpful, but all's well that end's well, as they say. Glad to hear it's working! Good luck! :)

---

