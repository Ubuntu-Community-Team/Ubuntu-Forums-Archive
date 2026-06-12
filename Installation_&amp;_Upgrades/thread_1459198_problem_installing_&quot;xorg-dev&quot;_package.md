---
title: "problem installing &quot;xorg-dev&quot; package"
date: 2010-04-21
forum: Installation &amp; Upgrades
---

### Post by ravi_pawase on 2010-04-21
I need to install "xorg-dev" package as a prerequisite for one program but when I  try  

sudo apt-get install   xorg-dev it gives me the following errors 

> Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xorg-dev: Depends: libdmx-dev but it is not going to be installed
            Depends: libx11-dev but it is not going to be installed
            Depends: libxaw7-dev but it is not going to be installed
            Depends: libxcomposite-dev but it is not going to be installed
            Depends: libxcursor-dev but it is not going to be installed
            Depends: libxdamage-dev but it is not going to be installed
            Depends: libxext-dev but it is not going to be installed
            Depends: libxfixes-dev but it is not going to be installed
            Depends: libxfont-dev but it is not going to be installed
            Depends: libxft-dev but it is not going to be installed
            Depends: libxi-dev but it is not going to be installed
            Depends: libxinerama-dev but it is not going to be installed
            Depends: libxkbfile-dev but it is not going to be installed
            Depends: libxkbui-dev but it is not going to be installed
            Depends: libxmu-dev but it is not going to be installed
            Depends: libxmuu-dev but it is not going to be installed
            Depends: libxpm-dev but it is not going to be installed
            Depends: libxrandr-dev but it is not going to be installed
            Depends: libxrender-dev but it is not going to be installed
            Depends: libxres-dev but it is not going to be installed
            Depends: libxss-dev but it is not going to be installed
            Depends: libxt-dev but it is not going to be installed
            Depends: libxtrap-dev but it is not going to be installed
            Depends: libxtst-dev but it is not going to be installed
            Depends: libxv-dev but it is not going to be installed
            Depends: libxvmc-dev but it is not going to be installed
            Depends: libxxf86dga-dev but it is not going to be installed
            Depends: libxxf86misc-dev but it is not going to be installed
            Depends: libxxf86vm-dev but it is not going to be installed
            Depends: x11proto-trap-dev but it is not going to be installed
E: Broken packages


and my  /etc/apt/sources.list files looks like following 

> 
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main universe restricted multiverse #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security universe main multiverse restricted #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe main multiverse restricted #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-proposed universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-proposed universe main multiverse restricted #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-backports universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-backports universe main multiverse restricted #Added by software-properties
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) hardy main
deb [http://ppa.launchpad.net/telepathy/ubuntu](http://ppa.launchpad.net/telepathy/ubuntu) hardy main




and I have upgraded my system from ubuntu 7.? to 8.04 .
So please let me know the solution.

thanks in advance.

---

### Post by zvacet on 2010-04-21
Edit your source list with 

```
gksudo gedit /etc/apt/sources.list
```

and replace it with this one 

> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) hardy main
deb [http://ppa.launchpad.net/telepathy/ubuntu](http://ppa.launchpad.net/telepathy/ubuntu) hardy main

Save and close file.

```
sudo apt-get update
```

Now try to install your package.

---

### Post by ravi_pawase on 2010-04-22
Thanks  **zvacet** for your reply.

After editing the sources.list file and executing the command 
sudo apt-get update 
I get the following output on terminal 
>  **sudo: unable to resolve host ravi-desktop**
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_IN                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                             
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_IN               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_IN                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_IN           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_IN     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_IN                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_IN               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_IN                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_IN               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_IN
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_IN
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release.gpg                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Translation-en_IN           
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                          
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Translation-en_IN       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Translation-en_IN     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed Release.gpg                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/restricted Translation-en_IN      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/main Translation-en_IN  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/multiverse Translation-en_IN
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                                
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/universe Translation-en_IN        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed Release                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/universe Packages
Fetched 1B in 3s (0B/s)  
Reading package lists... Done

which I am guessing is fine except the first line bothers me , is it any problem?
And after this  when I try to install the  "xorg-dev" package, again it gives the same output as in the my first post.         :confused:

So still my problem is not solved........

---

