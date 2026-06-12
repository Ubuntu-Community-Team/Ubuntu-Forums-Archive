---
title: "update manager broken, won't update anything"
date: 2010-11-30
forum: Installation &amp; Upgrades
---

### Post by Dans564 on 2010-11-30
Hey guys, 
im on mint 10 and when I run Update Manager i get this
```
W: GPG error: http://archive.canonical.com maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://security.ubuntu.com maverick-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7889D725DA6DEEAA
W: GPG error: http://archive.ubuntu.com maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://packages.linuxmint.com julia Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3EE67F3D0FF405B2
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://archive.ubuntu.com maverick-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://dl.google.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://dl.google.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991

W: GPG error: http://packages.medibuntu.org maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/Release  

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/Release  

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick-updates/Release  

W: Failed to fetch http://dl.google.com/linux/deb/dists/stable/Release  

W: Failed to fetch http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.gz  404  Not Found

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

thats a lot of broken PPAs.  Is there a way to auto fix them all?

---

### Post by Chrisy91 on 2010-11-30
If possible can you reinstall your OS?

---

### Post by karthick87 on 2010-11-30
Run the following in terminal,

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 437D05B5
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys DA6DEEAA
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0FF405B2
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 7FAC5991
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0C5A2783
sudo apt-get update

```

---

### Post by sikander3786 on 2010-11-30
And after adding the keys, please post the output of following command if the errors are still there.

```
cat /etc/apt/sources.list
```

For Launchpad PPAs, go to Software Sources > Other Software Tab and disable them. 404 error means server not found and those PPAs might not be maintained any longer or the server might be down. Maintaining a PPA is often up to a single person so those problems seem to happen with them.

---

### Post by cknight725 on 2010-11-30
Hint from [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) :

What to do when experiencing **The following signatures were invalid: BADSIG ...** when refreshing the packages from the repository? 
```

# sudo -s -H
# apt-get clean
# rm /var/lib/apt/lists/*
# rm /var/lib/apt/lists/partial/*
# apt-get clean
# apt-get update

```

Worked for me.  I think a while back when GetDeb went down the Launchpad PPA keys changed, so unless you clear and clean the old keys it will screw up updating even if you use the new keys.

---

### Post by Dans564 on 2010-11-30
I got scared when i read this ```
If possible can you reinstall your OS?
``` but then i scrolled down and was relieved lol.

when i ran:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 437D05B5
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys DA6DEEAA
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0FF405B2
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 7FAC5991
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0C5A2783
sudo apt-get update
```

I got back this during the apt-get update phase:
```
danny@i5GTX ~ $ sudo apt-get update
Ign file: binary/ Release.gpg
Ign file:/usr/share/local-repository/ binary/ Translation-en                   
Ign file:/usr/share/local-repository/ binary/ Translation-en_US                
Ign file: binary/ Release                                                      
Ign file: binary/ Packages                                                     
Ign file: binary/ Packages                                                     
Get:1 http://dl.google.com stable Release.gpg [197B]                           
Get:2 http://packages.medibuntu.org maverick Release.gpg [197B]                
Hit http://archive.canonical.com maverick Release.gpg                          
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en       
Get:3 http://ppa.launchpad.net karmic Release.gpg [307B]                       
Ign http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/ karmic/main Translation-en
Ign http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/ karmic/main Translation-en_US
Hit http://security.ubuntu.com maverick-security Release.gpg                   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en          
Hit http://archive.ubuntu.com maverick Release.gpg                             
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en             
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_US       
Get:4 http://packages.linuxmint.com julia Release.gpg [198B]                   
Ign http://packages.linuxmint.com/ julia/import Translation-en                 
Ign http://packages.linuxmint.com/ julia/import Translation-en_US              
Ign http://packages.linuxmint.com/ julia/main Translation-en                   
Get:5 http://dl.google.com stable Release.gpg [189B]                           
Ign http://dl.google.com/linux/deb/ stable/main Translation-en                 
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US    
Hit http://archive.canonical.com maverick Release                              
Ign http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net karmic Release                                    
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://security.ubuntu.com maverick-security Release                       
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US          
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en       
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US    
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en       
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US    
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en         
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US      
Hit http://archive.ubuntu.com maverick-updates Release.gpg                     
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en     
Ign http://packages.linuxmint.com/ julia/main Translation-en_US                
Ign http://packages.linuxmint.com/ julia/upstream Translation-en               
Ign http://packages.linuxmint.com/ julia/upstream Translation-en_US            
Get:6 http://packages.linuxmint.com julia Release [7,231B]                     
Ign http://packages.medibuntu.org/ maverick/free Translation-en                
Hit http://archive.canonical.com maverick/partner amd64 Packages               
Ign http://ppa.launchpad.net maverick Release                                  
Hit http://security.ubuntu.com maverick-security/main amd64 Packages           
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US  
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en 
Hit http://ppa.launchpad.net karmic/main Sources                               
Hit http://ppa.launchpad.net karmic/main amd64 Packages                        
Hit http://security.ubuntu.com maverick-security/restricted amd64 Packages     
Hit http://security.ubuntu.com maverick-security/universe amd64 Packages       
Hit http://security.ubuntu.com maverick-security/multiverse amd64 Packages     
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://archive.ubuntu.com maverick Release                                 
Hit http://archive.ubuntu.com maverick-updates Release                         
Ign http://dl.google.com/linux/deb/ stable/main Translation-en_US              
Ign http://ppa.launchpad.net maverick/main Sources                             
Ign http://ppa.launchpad.net maverick/main amd64 Packages                      
Ign http://packages.medibuntu.org/ maverick/free Translation-en_US             
Get:7 http://dl.google.com stable Release [1,347B]                             
Ign http://packages.linuxmint.com julia/main amd64 Packages                    
Hit http://archive.ubuntu.com maverick/main amd64 Packages                     
Get:8 http://dl.google.com stable Release [2,544B]                             
Ign http://ppa.launchpad.net maverick/main Sources                             
Hit http://archive.ubuntu.com maverick/restricted amd64 Packages               
Hit http://archive.ubuntu.com maverick/universe amd64 Packages                 
Hit http://archive.ubuntu.com maverick/multiverse amd64 Packages               
Hit http://archive.ubuntu.com maverick-updates/main amd64 Packages             
Hit http://archive.ubuntu.com maverick-updates/restricted amd64 Packages       
Hit http://archive.ubuntu.com maverick-updates/universe amd64 Packages         
Ign http://packages.linuxmint.com julia/upstream amd64 Packages                
Get:9 http://dl.google.com stable/main amd64 Packages [1,098B]                 
Ign http://ppa.launchpad.net maverick/main amd64 Packages                      
Ign http://packages.medibuntu.org/ maverick/non-free Translation-en            
Hit http://archive.ubuntu.com maverick-updates/multiverse amd64 Packages       
Ign http://packages.linuxmint.com julia/import amd64 Packages                  
Err http://ppa.launchpad.net maverick/main Sources                             
  404  Not Found
Get:10 http://dl.google.com stable/main amd64 Packages [1,104B]                
Ign http://packages.linuxmint.com julia/main amd64 Packages                    
Err http://ppa.launchpad.net maverick/main amd64 Packages            
  404  Not Found
Ign http://packages.medibuntu.org/ maverick/non-free Translation-en_US
Ign http://packages.linuxmint.com julia/upstream amd64 Packages                
Ign http://packages.linuxmint.com julia/import amd64 Packages                  
Hit http://packages.medibuntu.org maverick Release                             
Hit http://packages.linuxmint.com julia/main amd64 Packages
Hit http://packages.medibuntu.org maverick/free amd64 Packages                 
Hit http://packages.linuxmint.com julia/upstream amd64 Packages                
Hit http://packages.medibuntu.org maverick/non-free amd64 Packages             
Hit http://packages.linuxmint.com julia/import amd64 Packages                  
Fetched 14.4kB in 1s (8,479B/s)                          
W: Failed to fetch http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

this is what I get when I run "cat /etc/apt/sources.list'

```
danny@i5GTX ~ $ cat /etc/apt/sources.list
deb http://packages.linuxmint.com/ julia main upstream import
deb http://archive.ubuntu.com/ubuntu/ maverick main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ maverick-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ maverick-security main restricted universe multiverse
deb http://archive.canonical.com/ubuntu/ maverick partner
deb http://packages.medibuntu.org/ maverick free non-free

# deb http://archive.getdeb.net/ubuntu maverick-getdeb apps
# deb http://archive.getdeb.net/ubuntu maverick-getdeb games
deb http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu karmic main

```

thanks in advanced

---

### Post by karthick87 on 2010-11-30
You are getting 404 error,

> **sikander3786 said:**
>  404 error means server not found and those PPAs might not be maintained any longer or the server might be down.

---

### Post by sikander3786 on 2010-11-30
No need to re-install definitely here :-)

Edit your sources.list by

```
gksudo gedit /etc/apt/sources.list
```

Comment these 2 lines with #. They are just at the end of your file.

```
deb http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu karmic main
```

So that they look like,

```
#deb http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu karmic main
#deb-src http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu karmic main
```

Save and close that file and try apt-get update again.

Good Luck!

---

### Post by Dans564 on 2010-11-30
thanks sikander3786.  I did your suggestion just instead I did i by unchecking them in the software source GUI.  Same thing I figured.  And it worked!  Thanks, I'm up and updating again.

---

### Post by sikander3786 on 2010-11-30
> **Dans564 said:**
> thanks sikander3786.  I did your suggestion just instead I did i by unchecking them in the software source GUI.  Same thing I figured.  And it worked!  Thanks, I'm up and updating again.
You are Welcome. Yes you can do it from Software Sources also. In fact I mentioned that in my above post :-)

Glad to know it is all sorted now.

You can mark this thread Solved using **[COLOR="Red"]Thread Tools[/COLOR]** near the top of this page.

Happy Ubuntu-ing!

---

### Post by Dans564 on 2010-11-30
Marked as Solved

---

### Post by mkstallings1 on 2010-11-30
This is what I get when I type the same command.  I am not sure what to edit.

Thanks

# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-security multiverse
mike@mike-Pavilion-dv8000-EP409UA-ABA:~$

---

### Post by sikander3786 on 2010-11-30
> **mkstallings1 said:**
> This is what I get when I type the same command.  I am not sure what to edit.

Thanks

..............
We need to see the output of this one as well.

```
sudo apt-get update
```

---

### Post by mkstallings1 on 2010-11-30
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                              
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release.gpg                         
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en       
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic Release.gpg                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release.gpg                          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/bisigi/ppa/ubuntu/](http://ppa.launchpad.net/bisigi/ppa/ubuntu/) maverick/main Translation-en   
Ign [http://ppa.launchpad.net/bisigi/ppa/ubuntu/](http://ppa.launchpad.net/bisigi/ppa/ubuntu/) maverick/main Translation-en_US
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                  
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US    
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
Ign [http://archive.canonical.com/](http://archive.canonical.com/) maverick/partner Translation-en              
Ign [http://archive.canonical.com/](http://archive.canonical.com/) maverick/partner Translation-en_US           
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                              
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US       
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release.gpg                  
Ign [http://deb.playonlinux.com/](http://deb.playonlinux.com/) karmic/main Translation-en                     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/) maverick/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/ferramroberto/linuxfreedomlucid/ubuntu/](http://ppa.launchpad.net/ferramroberto/linuxfreedomlucid/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/ferramroberto/linuxfreedomlucid/ubuntu/](http://ppa.launchpad.net/ferramroberto/linuxfreedomlucid/ubuntu/) maverick/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/team-xbmc-svn/ppa/ubuntu/](http://ppa.launchpad.net/team-xbmc-svn/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/team-xbmc-svn/ppa/ubuntu/](http://ppa.launchpad.net/team-xbmc-svn/ppa/ubuntu/) maverick/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                              
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/free Translation-en                
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                             
Ign [http://deb.playonlinux.com/](http://deb.playonlinux.com/) karmic/main Translation-en_US                  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-security Release.gpg                 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en 
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) maverick/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources                      
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                       
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic Release                                  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/free Translation-en_US             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-security Release                     
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic/main i386 Packages/DiffIndex             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                   
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages             
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/non-free Translation-en  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main i386 Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted i386 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe i386 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse i386 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic/main i386 Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main i386 Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/non-free Translation-en_US         
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic/main i386 Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-security/main Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-security/restricted Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-security/universe Sources            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-security/multiverse Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-security/main i386 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-security/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-security/universe i386 Packages
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                   
  404  Not Found
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-security/multiverse i386 Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
  404  Not Found
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free i386 Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free i386 Packages
W: Failed to fetch [http://ppa.launchpad.net/ferramroberto/linuxfreedomlucid/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/ferramroberto/linuxfreedomlucid/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/ferramroberto/linuxfreedomlucid/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/ferramroberto/linuxfreedomlucid/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by karthick87 on 2010-12-01
Do the following,
> **sikander3786 said:**
> No need to re-install definitely here :-)

Edit your sources.list by

```
gksudo gedit /etc/apt/sources.list
```Comment these 2 lines with #. They are just at the end of your file.

```
deb http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu karmic main
```So that they look like,

```
#deb http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu karmic main
#deb-src http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu karmic main
```Save and close that file and try apt-get update again.

Good Luck!

---

### Post by mkstallings1 on 2010-12-01
I don't have any lines that show that:

deb [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu) karmic main

---

### Post by sikander3786 on 2010-12-01
> **mkstallings1 said:**
> I don't have any lines that show that:

deb [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu) karmic main
Launchpad PPAs are not stored in sources.list, instead they are in sources.list.d. Rather than editing sources.list.d, try disabling them from Software Sources instead.

Go to Software Center > Edit > Software Sources > Other Software Tab and disable those offensive PPAs (2 of them) and try apt-get update again.

Good Luck!

---

### Post by mkstallings1 on 2010-12-01
Thanks, that seemed to do the trick in the terminal.  I was wondering, does this mean that I can't use Ubuntu Tweak for updates since now when I start it the  notice comes up that the Ubuntu Tweak repositories need to be enabled?  No big deal, I was just wondering.

---

