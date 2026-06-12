---
title: "Kernel 2.6.30-10 not offered"
date: 2009-06-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by celticbhoy on 2009-06-25
I read a post saying that a few folk having updated to Kernel 2.6.30-10, when I run update manager this is not offered as an update to me. Am I missing something?

---

### Post by taavikko on 2009-06-25
> **celticbhoy said:**
> I read a post saying that a few folk having updated to Kernel 2.6.30-10, when I run update manager this is not offered as an update to me. Am I missing something?

Check the sources.list, make sure you use "main server" as sometimes the localized mirrors are out of sync.

Also might be wortwhile to check via CLI if it works better.
```
sudo aptitude update && sudo aptitude full-upgrade
``` 

If in doubt, paste the output.

---

### Post by celticbhoy on 2009-06-25
Just tried changing servers to main - no dif.
Using the CLI commands it wants to update a load of open office stuff that been sitting in update manager for a few days shouting for a partial upgrade - is that wise?

---

### Post by taavikko on 2009-06-25
> **celticbhoy said:**
> 
Using the CLI commands it wants to update a load of open office stuff that been sitting in update manager for a few days shouting for a partial upgrade - is that wise?

As I replied,

> **taavikko said:**
> 
If in doubt, paste the output.

---

### Post by nyarnon on 2009-06-25
> **celticbhoy said:**
> Just tried changing servers to main - no dif.
Using the CLI commands it wants to update a load of open office stuff that been sitting in update manager for a few days shouting for a partial upgrade - is that wise?

Why dont you *test* that?

---

### Post by celticbhoy on 2009-06-25
The only concerns are those regarding partial upgrades. Get this output :-

Writing extended state information... Done
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_GB                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_GB                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_GB                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_GB                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Translation-en_GB                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Translation-en_GB               
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                             
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_GB               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Translation-en_GB                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Translation-en_GB               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release.gpg                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Translation-en_GB             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Translation-en_GB       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Translation-en_GB         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Translation-en_GB       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports Release.gpg                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/main Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/restricted Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/universe Translation-en_GB       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/multiverse Translation-en_GB     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release.gpg           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Translation-en_GB
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed Release.gpg                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/restricted Translation-en_GB      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/main Translation-en_GB            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/multiverse Translation-en_GB      
Ign [http://apt.boxee.tv](http://apt.boxee.tv) jaunty Release.gpg                                      
Ign [http://apt.boxee.tv](http://apt.boxee.tv) jaunty/main Translation-en_GB                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/universe Translation-en_GB        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed Release                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Sources                                
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                        
Ign [http://apt.boxee.tv](http://apt.boxee.tv) jaunty Release                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                    
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Sources             
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages                              
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Sources             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Packages            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Sources             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Packages
Ign [http://apt.boxee.tv](http://apt.boxee.tv) jaunty/main Packages  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/main Packages        
Hit [http://apt.boxee.tv](http://apt.boxee.tv) jaunty/main Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/universe Sources
Reading package lists... Done             

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
The following NEW packages will be installed:
  gconf-defaults-service{a} geoip-database{a} install-info{a} 
  libcolamd2.7.1{a} libempathy-gtk24{a} libempathy26{a} libevent-1.4-2{a} 
  libgeoip1{a} libmono-i18n-west2.0-cil{a} libntfs-3g54{a} libsgutils2{a} 
  libtag1-vanilla{a} libtorrent-rasterbar4{a} linux-headers-2.6.30-10{a} 
  linux-headers-2.6.30-10-generic{a} linux-image-2.6.30-10-generic 
The following packages will be REMOVED:
  hotkey-setup{a} libempathy-gtk23{u} libempathy25{u} 
  libtorrent-rasterbar3{u} linux-headers-2.6.30-7{u} 
  linux-headers-2.6.30-7-generic{u} mono-2.0-runtime{a} mono-common{a} 
  mono-jit{a} python-nautilus{u} 
The following packages will be upgraded:
  bind9-host ca-certificates deluge deluge-common deluge-core dnsutils 
  empathy gconf-editor info libbind9-50 libdns50 libempathy-common 
  libempathy-gtk-common libisc50 libisccc50 libisccfg50 liblwres50 
  libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-data2.0-cil 
  libmono-getoptions2.0-cil libmono-i18n2.0-cil libmono-posix2.0-cil 
  libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil 
  libmono-system-data2.0-cil libmono-system-web2.0-cil 
  libmono-system2.0-cil libmono2.0-cil libtag1c2a libx86-1 libxapian15 
  linux-generic linux-headers-generic linux-image-generic lp-solve 
  mono-2.0-gac mono-gac mono-runtime ntfs-3g openoffice.org 
  openoffice.org-base openoffice.org-base-core openoffice.org-calc 
  openoffice.org-core openoffice.org-draw openoffice.org-evolution 
  openoffice.org-filter-binfilter openoffice.org-impress 
  openoffice.org-math openoffice.org-officebean openoffice.org-writer 
  python-libtorrent sg3-utils telepathy-gabble transmission-common 
  transmission-gtk udev-extras whois xserver-xorg-video-geode 
The following packages are RECOMMENDED but will NOT be installed:
  openoffice.org-emailmerge 
61 packages upgraded, 16 newly installed, 10 to remove and 0 not upgraded.
Need to get 106MB of archives. After unpacking 88.8MB will be used.
Do you want to continue? [Y/n/?] n
Abort.

---

### Post by taavikko on 2009-06-25
Whups, misread...

There's no point of using "proposed & backports" in karmic at this point,

And for the updates, it's ok to say "yes"

The update output states that there is the *-10 kernel available...

---

### Post by celticbhoy on 2009-06-25
The only Jaunty refs are for third party apps with no Karmic options.

Thanx for the help will upgrade now.

---

