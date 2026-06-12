---
title: "Upgrade from 12.04 to 14.04 using Package Manager failed."
date: 2014-08-12
forum: Installation &amp; Upgrades
---

### Post by Panawe on 2014-08-12
I expect this is hardly news but I had the upgrade fail during the "setting software channels" step. I get the following error messages:

   >Third party sources disabled 

  
  Some third party entries in your sources.list were disabled. You can re-enable them after the upgrade with the 'software-properties' tool or your package manager.
>> This is simply accepted and the upgrade continues

>Could not determine the upgrade 

  
 An unresolvable problem occurred while calculating the upgrade. 
  
  This can be caused by: 
  * Upgrading to a pre-release version of Ubuntu 
  * Running the current pre-release version of Ubuntu 
  * Unofficial software packages not provided by Ubuntu 
  
 If none of this applies, then please report this bug using the command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal.


>>Upgrade stops and restores 12.04

So I'm going to wait until the upgrade is fixed and install via Package Manager, unless someone can offer any suggestions to act otherwise/

---

### Post by Bashing-om on 2014-08-12
Panawe; Hi !

Let's make sure the system is fully updated, and look at the graphic driver situation and check for 3rd party software sources.
Post back the outputs of terminal commands:
```

sudo apt-get update
sudo apt-get upgrade
sudo lshw -C display
cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
Then we take another poke at the release upgrade process.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by Panawe on 2014-08-12
Here goes...
phil@panawe:~$ sudo apt-get update 
[sudo] password for phil:  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                                
Get:1 [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg [198 B]                  
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                           
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise Release.gpg                        
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise-updates Release.gpg                
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise-security Release.gpg               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                    
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                     
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                     
Get:2 [http://archive.canonical.com](http://archive.canonical.com) precise Release [7,078 B]                    
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise Release                            
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise-updates Release                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                    
Hit [http://dl.google.com](http://dl.google.com) stable Release                                         
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise-security Release                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                               
Hit [http://dl.google.com](http://dl.google.com) stable Release                                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                               
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise/main Sources                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                      
Get:3 [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages [7,909 B]     
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise/restricted Sources                 
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise/universe Sources                   
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise/multiverse Sources                 
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise/main amd64 Packages                
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise/restricted amd64 Packages          
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise/universe amd64 Packages            
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise/multiverse amd64 Packages          
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise/main i386 Packages                 
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                      
Get:4 [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages [8,933 B]      
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex               
Hit [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb Release.gpg                        
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise/restricted i386 Packages           
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise/universe i386 Packages             
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise/multiverse i386 Packages           
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise/main TranslationIndex              
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise/multiverse TranslationIndex        
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise/restricted TranslationIndex        
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise/universe TranslationIndex          
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                              
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                           
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                             
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                              
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                           
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources                       
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise-updates/main Sources               
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise-updates/restricted Sources         
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise-updates/universe Sources           
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise-updates/multiverse Sources         
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise-updates/main amd64 Packages        
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise-updates/restricted amd64 Packages  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                      
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise-updates/universe amd64 Packages    
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise-updates/multiverse amd64 Packages  
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise-updates/main i386 Packages         
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise-updates/restricted i386 Packages   
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise-updates/universe i386 Packages     
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise-updates/multiverse i386 Packages   
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise-updates/main TranslationIndex      
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise-updates/multiverse TranslationIndex 
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise-updates/restricted TranslationIndex 
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise-updates/universe TranslationIndex  
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise-security/main Sources              
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise-security/restricted Sources        
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise-security/universe Sources          
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise-security/multiverse Sources        
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise-security/main amd64 Packages       
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise-security/restricted amd64 Packages 
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise-security/universe amd64 Packages   
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise-security/multiverse amd64 Packages 
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise-security/main i386 Packages        
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise-security/restricted i386 Packages  
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise-security/universe i386 Packages    
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise-security/multiverse i386 Packages  
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise-security/main TranslationIndex     
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise-security/multiverse TranslationIndex 
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise-security/restricted TranslationIndex 
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise-security/universe TranslationIndex 
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise/main Translation-en_GB             
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise/main Translation-en                
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise/multiverse Translation-en_GB       
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise/multiverse Translation-en          
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise/restricted Translation-en_GB       
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise/restricted Translation-en          
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise/universe Translation-en_GB         
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise/universe Translation-en            
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise-updates/main Translation-en_GB     
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise-updates/main Translation-en        
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise-updates/multiverse Translation-en_GB 
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise-updates/multiverse Translation-en  
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise-updates/restricted Translation-en_GB 
Hit [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb Release                            
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise-updates/restricted Translation-en  
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise-updates/universe Translation-en_GB 
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise-updates/universe Translation-en    
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise-security/main Translation-en       
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise-security/multiverse Translation-en 
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise-security/restricted Translation-en 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_GB                     
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) precise-security/universe Translation-en   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                        
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_GB              
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                        
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_GB                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB                     
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                             
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_GB 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en 
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en 
Hit [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb/apps Sources 
Hit [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb/apps amd64 Packages 
Hit [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb/apps i386 Packages 
Ign [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb/apps TranslationIndex 
Ign [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb/apps Translation-en_GB             
Ign [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb/apps Translation-en                
Fetched 24.1 kB in 7s (3,435 B/s)                                               
Reading package lists... Done 
phil@panawe:~$ sudo apt-get upgrade 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
The following packages have been kept back: 
  libav-tools libavdevice53 libavfilter2 nvidia-304 
The following packages will be upgraded: 
  adobe-flash-properties-gtk adobe-flashplugin 
2 to upgrade, 0 to newly install, 0 to remove and 4 not to upgrade. 
Need to get 7,029 kB of archives. 
After this operation, 0 B of additional disk space will be used. 
Do you want to continue [Y/n]? y 
Get:1 [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner adobe-flash-properties-gtk amd64 11.2.202.400-0precise1 [134 kB] 
Get:2 [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner adobe-flashplugin amd64 11.2.202.400-0precise1 [6,895 kB] 
Fetched 7,029 kB in 7s (890 kB/s)                                               
(Reading database ... 1273653 files and directories currently installed.) 
Preparing to replace adobe-flash-properties-gtk 11.2.202.394-0precise1 (using .../adobe-flash-properties-gtk_11.2.202.400-0precise1_amd64.deb) ... 
Unpacking replacement adobe-flash-properties-gtk ... 
Preparing to replace adobe-flashplugin 11.2.202.394-0precise1 (using .../adobe-flashplugin_11.2.202.400-0precise1_amd64.deb) ... 
Unpacking replacement adobe-flashplugin ... 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index... 
Processing triggers for desktop-file-utils ... 
Processing triggers for gnome-menus ... 
Processing triggers for hicolor-icon-theme ... 
Setting up adobe-flashplugin (11.2.202.400-0precise1) ... 
update-alternatives: using /usr/lib/adobe-flashplugin/libflashplayer.so to provide /usr/lib/mozilla/plugins/flashplugin-alternative.so (mozilla-flashplugin) in auto mode. 
Setting up adobe-flash-properties-gtk (11.2.202.400-0precise1) ... 
phil@panawe:~$ sudo lshw -C display 
  *-display                
       description: VGA compatible controller 
       product: G98 [GeForce 8400 GS Rev. 2] 
       vendor: NVIDIA Corporation 
       physical id: 0 
       bus info: pci@0000:01:00.0 
       version: a1 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom 
       configuration: driver=nvidia latency=0 
       resources: irq:18 memory:fa000000-faffffff memory:d0000000-dfffffff memory:f8000000-f9ffffff ioport:ef00(size=128) memory:fb000000-fb01ffff 
phil@panawe:~$ cat -n /etc/apt/sources.list 
     1    # deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted 
     2    # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to 
     3    # newer versions of the distribution. 
     4     
     5    deb [http://mirror.sov.uk.goscomb.net/ubuntu/](http://mirror.sov.uk.goscomb.net/ubuntu/) precise main restricted 
     6    deb-src [http://mirror.sov.uk.goscomb.net/ubuntu/](http://mirror.sov.uk.goscomb.net/ubuntu/) precise main restricted 
     7     
     8    ## Major bug fix updates produced after the final release of the 
     9    ## distribution. 
    10    deb [http://mirror.sov.uk.goscomb.net/ubuntu/](http://mirror.sov.uk.goscomb.net/ubuntu/) precise-updates main restricted 
    11    deb-src [http://mirror.sov.uk.goscomb.net/ubuntu/](http://mirror.sov.uk.goscomb.net/ubuntu/) precise-updates main restricted 
    12     
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    14    ## team. Also, please note that software in universe WILL NOT receive any 
    15    ## review or updates from the Ubuntu security team. 
    16    deb [http://mirror.sov.uk.goscomb.net/ubuntu/](http://mirror.sov.uk.goscomb.net/ubuntu/) precise universe 
    17    deb-src [http://mirror.sov.uk.goscomb.net/ubuntu/](http://mirror.sov.uk.goscomb.net/ubuntu/) precise universe 
    18    deb [http://mirror.sov.uk.goscomb.net/ubuntu/](http://mirror.sov.uk.goscomb.net/ubuntu/) precise-updates universe 
    19    deb-src [http://mirror.sov.uk.goscomb.net/ubuntu/](http://mirror.sov.uk.goscomb.net/ubuntu/) precise-updates universe 
    20     
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu  
    22    ## team, and may not be under a free licence. Please satisfy yourself as to  
    23    ## your rights to use the software. Also, please note that software in  
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu 
    25    ## security team. 
    26    deb [http://mirror.sov.uk.goscomb.net/ubuntu/](http://mirror.sov.uk.goscomb.net/ubuntu/) precise multiverse 
    27    deb-src [http://mirror.sov.uk.goscomb.net/ubuntu/](http://mirror.sov.uk.goscomb.net/ubuntu/) precise multiverse 
    28    deb [http://mirror.sov.uk.goscomb.net/ubuntu/](http://mirror.sov.uk.goscomb.net/ubuntu/) precise-updates multiverse 
    29    deb-src [http://mirror.sov.uk.goscomb.net/ubuntu/](http://mirror.sov.uk.goscomb.net/ubuntu/) precise-updates multiverse 
    30     
    31    ## Uncomment the following two lines to add software from the 'backports' 
    32    ## repository. 
    33    ## N.B. software from this repository may not have been tested as 
    34    ## extensively as that contained in the main release, although it includes 
    35    ## newer versions of some applications which may provide useful features. 
    36    ## Also, please note that software in backports WILL NOT receive any review 
    37    ## or updates from the Ubuntu security team. 
    38    # deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse 
    39    # deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse 
    40     
    41    ## Uncomment the following two lines to add software from Canonical's 
    42    ## 'partner' repository. 
    43    ## This software is not part of Ubuntu, but is offered by Canonical and the 
    44    ## respective vendors as a service to Ubuntu users. 
    45    deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner 
    46    deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner 
    47     
    48    ## This software is not part of Ubuntu, but is offered by third-party 
    49    ## developers who want to ship their latest software. 
    50    deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main 
    51    deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main 
    52     
    53    deb [http://mirror.sov.uk.goscomb.net/ubuntu/](http://mirror.sov.uk.goscomb.net/ubuntu/) precise-security main restricted 
    54    deb-src [http://mirror.sov.uk.goscomb.net/ubuntu/](http://mirror.sov.uk.goscomb.net/ubuntu/) precise-security main restricted 
    55    deb [http://mirror.sov.uk.goscomb.net/ubuntu/](http://mirror.sov.uk.goscomb.net/ubuntu/) precise-security universe 
    56    deb-src [http://mirror.sov.uk.goscomb.net/ubuntu/](http://mirror.sov.uk.goscomb.net/ubuntu/) precise-security universe 
    57    deb [http://mirror.sov.uk.goscomb.net/ubuntu/](http://mirror.sov.uk.goscomb.net/ubuntu/) precise-security multiverse 
    58    deb-src [http://mirror.sov.uk.goscomb.net/ubuntu/](http://mirror.sov.uk.goscomb.net/ubuntu/) precise-security multiverse 
    59    deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) precise-getdeb apps 
    60    deb-src [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) precise-getdeb apps 
phil@panawe:~$ tail -v -n +1 /etc/apt/sources.list.d/* 
==> /etc/apt/sources.list.d/gencfsm-ppa-precise.list <== 
deb [http://ppa.launchpad.net/gencfsm/ppa/ubuntu](http://ppa.launchpad.net/gencfsm/ppa/ubuntu) precise main 
deb-src [http://ppa.launchpad.net/gencfsm/ppa/ubuntu](http://ppa.launchpad.net/gencfsm/ppa/ubuntu) precise main 
 
==> /etc/apt/sources.list.d/gencfsm-ppa-precise.list.distUpgrade <== 
deb [http://ppa.launchpad.net/gencfsm/ppa/ubuntu](http://ppa.launchpad.net/gencfsm/ppa/ubuntu) precise main 
deb-src [http://ppa.launchpad.net/gencfsm/ppa/ubuntu](http://ppa.launchpad.net/gencfsm/ppa/ubuntu) precise main 
 
==> /etc/apt/sources.list.d/gencfsm-ppa-precise.list.save <== 
deb [http://ppa.launchpad.net/gencfsm/ppa/ubuntu](http://ppa.launchpad.net/gencfsm/ppa/ubuntu) precise main 
deb-src [http://ppa.launchpad.net/gencfsm/ppa/ubuntu](http://ppa.launchpad.net/gencfsm/ppa/ubuntu) precise main 
 
==> /etc/apt/sources.list.d/google-chrome.list <== 
### THIS FILE IS AUTOMATICALLY CONFIGURED ### 
# You may comment out this entry, but any other modifications may be lost. 
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main 
 
==> /etc/apt/sources.list.d/google-chrome.list.distUpgrade <== 
### THIS FILE IS AUTOMATICALLY CONFIGURED ### 
# You may comment out this entry, but any other modifications may be lost. 
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main 
 
==> /etc/apt/sources.list.d/google-chrome.list.save <== 
### THIS FILE IS AUTOMATICALLY CONFIGURED ### 
# You may comment out this entry, but any other modifications may be lost. 
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main 
 
==> /etc/apt/sources.list.d/google-earth.list <== 
### THIS FILE IS AUTOMATICALLY CONFIGURED ### 
# You may comment out this entry, but any other modifications may be lost. 
deb [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable main 
 
==> /etc/apt/sources.list.d/google-earth.list.distUpgrade <== 
### THIS FILE IS AUTOMATICALLY CONFIGURED ### 
# You may comment out this entry, but any other modifications may be lost. 
deb [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable main 
 
==> /etc/apt/sources.list.d/google-earth.list.save <== 
### THIS FILE IS AUTOMATICALLY CONFIGURED ### 
# You may comment out this entry, but any other modifications may be lost. 
deb [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable main 
 
==> /etc/apt/sources.list.d/medibuntu.list <== 
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/) 
# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) precise free non-free #Medibuntu - Ubuntu 12.04 "precise pangolin" 
# deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) precise free non-free #Medibuntu (source) - Ubuntu 12.04 "precise pangolin" 
 
==> /etc/apt/sources.list.d/medibuntu.list.distUpgrade <== 
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/) 
# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) precise free non-free #Medibuntu - Ubuntu 12.04 "precise pangolin" 
# deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) precise free non-free #Medibuntu (source) - Ubuntu 12.04 "precise pangolin" 
 
==> /etc/apt/sources.list.d/medibuntu.list.save <== 
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/) 
# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) precise free non-free #Medibuntu - Ubuntu 12.04 "precise pangolin" 
# deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) precise free non-free #Medibuntu (source) - Ubuntu 12.04 "precise pangolin" 
 
==> /etc/apt/sources.list.d/openshot_developers-ppa-maverick.list <== 
# deb [http://ppa.launchpad.net/openshot.developers/ppa/ubuntu](http://ppa.launchpad.net/openshot.developers/ppa/ubuntu) maverick main 
# deb-src [http://ppa.launchpad.net/openshot.developers/ppa/ubuntu](http://ppa.launchpad.net/openshot.developers/ppa/ubuntu) maverick main 
 
==> /etc/apt/sources.list.d/openshot_developers-ppa-maverick.list.distUpgrade <== 
# deb [http://ppa.launchpad.net/openshot.developers/ppa/ubuntu](http://ppa.launchpad.net/openshot.developers/ppa/ubuntu) maverick main 
# deb-src [http://ppa.launchpad.net/openshot.developers/ppa/ubuntu](http://ppa.launchpad.net/openshot.developers/ppa/ubuntu) maverick main 
 
==> /etc/apt/sources.list.d/openshot_developers-ppa-maverick.list.save <== 
# deb [http://ppa.launchpad.net/openshot.developers/ppa/ubuntu](http://ppa.launchpad.net/openshot.developers/ppa/ubuntu) maverick main 
# deb-src [http://ppa.launchpad.net/openshot.developers/ppa/ubuntu](http://ppa.launchpad.net/openshot.developers/ppa/ubuntu) maverick main 
 
==> /etc/apt/sources.list.d/tikhonov-misc-precise.list <== 
deb [http://ppa.launchpad.net/tikhonov/misc/ubuntu](http://ppa.launchpad.net/tikhonov/misc/ubuntu) precise main 
deb-src [http://ppa.launchpad.net/tikhonov/misc/ubuntu](http://ppa.launchpad.net/tikhonov/misc/ubuntu) precise main 
 
==> /etc/apt/sources.list.d/tikhonov-misc-precise.list.distUpgrade <== 
deb [http://ppa.launchpad.net/tikhonov/misc/ubuntu](http://ppa.launchpad.net/tikhonov/misc/ubuntu) precise main 
deb-src [http://ppa.launchpad.net/tikhonov/misc/ubuntu](http://ppa.launchpad.net/tikhonov/misc/ubuntu) precise main 
 
==> /etc/apt/sources.list.d/tikhonov-misc-precise.list.save <== 
deb [http://ppa.launchpad.net/tikhonov/misc/ubuntu](http://ppa.launchpad.net/tikhonov/misc/ubuntu) precise main 
deb-src [http://ppa.launchpad.net/tikhonov/misc/ubuntu](http://ppa.launchpad.net/tikhonov/misc/ubuntu) precise main 
 
==> /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-precise.list <== 
deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) precise main 
deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) precise main 
 
==> /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-precise.list.distUpgrade <== 
deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) precise main 
deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) precise main 
 
==> /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-precise.list.save <== 
deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) precise main 
deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) precise main 
 
==> /etc/apt/sources.list.d/user-phil-maverick.list <== 
# deb [http://ppa.launchpad.net/user/phil/ubuntu](http://ppa.launchpad.net/user/phil/ubuntu) maverick main 
# deb-src [http://ppa.launchpad.net/user/phil/ubuntu](http://ppa.launchpad.net/user/phil/ubuntu) maverick main 
 
==> /etc/apt/sources.list.d/user-phil-maverick.list.distUpgrade <== 
# deb [http://ppa.launchpad.net/user/phil/ubuntu](http://ppa.launchpad.net/user/phil/ubuntu) maverick main 
# deb-src [http://ppa.launchpad.net/user/phil/ubuntu](http://ppa.launchpad.net/user/phil/ubuntu) maverick main 
 
==> /etc/apt/sources.list.d/user-phil-maverick.list.save <== 
# deb [http://ppa.launchpad.net/user/phil/ubuntu](http://ppa.launchpad.net/user/phil/ubuntu) maverick main 
# deb-src [http://ppa.launchpad.net/user/phil/ubuntu](http://ppa.launchpad.net/user/phil/ubuntu) maverick main 
phil@panawe:~$

Thanks for your help - I hope all this means something!

---

### Post by Bashing-om on 2014-08-12
Panawe; so far so good ;

Are you comfortable with a text editor (?); there are a couple of issues with the "/etc/apt/sources.list" file.
> 
46 deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner 
 
Maverick no longer exist, comment that line out.
> 
59 deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) precise-getdeb apps 
60 deb-src [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) precise-getdeb apps

Unknown if these are supported in trusty, disable in attempting to get 12.04 as close to default as possible to aid in the release upgrade process .
-------------------------
Graphics driver: 
> 
The following packages have been kept back: 
libav-tools libavdevice53 libavfilter2 [color=red]nvidia-304[/color]

We will take care of that in a moment for the CURRENT install, MUST be reverted to open source when making the release upgrade. 
--------------------------------
OK done the edit(s) in the sources.list file, now let's update/upgrade the installed 12.04 packages to latest ( including the 304 driver);
Again, post back the outputs of Terminal commands:
And please employ code tags, makes it so much easier for us to read.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
```

sudo apt-get update
sudo apt-get updrade
sudo apt-get dist-upgrade

```
where "dist-upgrade" will pull in those held packages.
---------------------------
Once the 12.04 install is stable and fully updated, 3rd party PPAs disabled (Software Sources tool), THEN we can do the release upgrade.


[INDENT][INDENT][INDENT]ain't nothing but some things
[/INDENT][/INDENT][/INDENT]

---

### Post by Panawe on 2014-08-12
I'm not sure here what to do when you say "Maverick no longer exist, comment that line out." And similarly when you say "disable" lines 59 & 60 and the business with the graphics driver.
Can you help me here?

---

### Post by Old_Grey_Wolf on 2014-08-12
The "comment out" and "disable" refer to putting the # symbol at the beginning of the line. You will see it on a few lines in the sources.list file.

---

### Post by Bashing-om on 2014-08-12
Panawe; Sure,

Glad to oblige;
1st make a backup of the file you are going to edit - just standard operating procedure:
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list-12aug2014

```
Now fire up the text editor ( my reference is gedit of that editor), with admin privileges opening that file:
```

gksudo gedit /etc/apt/sources.list

```
OK our target file is loaded and available to be edited.
Arrow down to the line "  deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner " and type the character '#' at the start of the line. Any line starting with # is considered to be a comment by the system and that line will not be parsed - hence the term "commented out".

Arrow on down to the next item "deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) precise-getdeb apps ". and also place a # at the start of that line:
repeat for line " deb-src [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) precise-getdeb apps " If these are supported in 14.04, they may be placed back in service when the release upgrade is completed.

Save the file and exit out, back to the terminal.

The graphics driver: There is an update available for it and we will do so as it is a part of the other held updates. However, it is a 3rd party driver and is not a part of the ubuntu install, In the release upgrade process, as this software is not a part of ubuntu that driver will break. So to make the transition to 14.04 one reverts the proprietary back to the open source ( nouveau ) driver - that is a part of ubuntu. Once release upgraded, if you so desire you may (RE-)install a proprietary graphics driver.

Required also for safety's sake; one disables all 3rd party repositories. The easiest way is from the GUI "Software Sources" -> other software and uncheck the check boxes . And again, when verified that they support 14.04 they may be enabled when 14.04 upgrade is complete.

OK, with me so far ? ..

All done up to this point then let's see what the status is prior to making the release upgrade:
post the outputs - Between code tags, please - of terminal commands: 
```

sudo apt-get update
sudo apt-get updrade
sudo apt-get dist-upgrade

```
So we see that you are ready to do the release upgrade to 14.04.

[INDENT][INDENT][INDENT]can do
[INDENT][INDENT][INDENT][INDENT]gets it done
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Panawe on 2014-08-12
Okay, I haven't gone to the last step of dist-upgrade but here it is so far...
```

phil@panawe:~$ sudo apt-get update
[sudo] password for phil: 
Hit http://mirror.sov.uk.goscomb.net precise Release.gpg
Hit http://mirror.sov.uk.goscomb.net precise-updates Release.gpg
Hit http://mirror.sov.uk.goscomb.net precise-security Release.gpg
Hit http://mirror.sov.uk.goscomb.net precise Release
Hit http://mirror.sov.uk.goscomb.net precise-updates Release
Hit http://mirror.sov.uk.goscomb.net precise-security Release
Hit http://mirror.sov.uk.goscomb.net precise/main Sources
Hit http://mirror.sov.uk.goscomb.net precise/restricted Sources
Hit http://mirror.sov.uk.goscomb.net precise/universe Sources
Hit http://mirror.sov.uk.goscomb.net precise/multiverse Sources
Hit http://mirror.sov.uk.goscomb.net precise/main amd64 Packages
Hit http://mirror.sov.uk.goscomb.net precise/restricted amd64 Packages
Hit http://mirror.sov.uk.goscomb.net precise/universe amd64 Packages
Hit http://mirror.sov.uk.goscomb.net precise/multiverse amd64 Packages
Hit http://mirror.sov.uk.goscomb.net precise/main i386 Packages
Hit http://mirror.sov.uk.goscomb.net precise/restricted i386 Packages
Hit http://mirror.sov.uk.goscomb.net precise/universe i386 Packages
Hit http://mirror.sov.uk.goscomb.net precise/multiverse i386 Packages
Hit http://mirror.sov.uk.goscomb.net precise/main TranslationIndex
Hit http://mirror.sov.uk.goscomb.net precise/multiverse TranslationIndex
Hit http://mirror.sov.uk.goscomb.net precise/restricted TranslationIndex
Hit http://mirror.sov.uk.goscomb.net precise/universe TranslationIndex
Hit http://mirror.sov.uk.goscomb.net precise-updates/main Sources
Hit http://mirror.sov.uk.goscomb.net precise-updates/restricted Sources
Hit http://mirror.sov.uk.goscomb.net precise-updates/universe Sources
Hit http://mirror.sov.uk.goscomb.net precise-updates/multiverse Sources
Hit http://mirror.sov.uk.goscomb.net precise-updates/main amd64 Packages
Hit http://mirror.sov.uk.goscomb.net precise-updates/restricted amd64 Packages
Hit http://mirror.sov.uk.goscomb.net precise-updates/universe amd64 Packages
Hit http://mirror.sov.uk.goscomb.net precise-updates/multiverse amd64 Packages
Hit http://mirror.sov.uk.goscomb.net precise-updates/main i386 Packages
Hit http://mirror.sov.uk.goscomb.net precise-updates/restricted i386 Packages
Hit http://mirror.sov.uk.goscomb.net precise-updates/universe i386 Packages
Hit http://mirror.sov.uk.goscomb.net precise-updates/multiverse i386 Packages
Hit http://mirror.sov.uk.goscomb.net precise-updates/main TranslationIndex
Hit http://mirror.sov.uk.goscomb.net precise-updates/multiverse TranslationIndex
Hit http://mirror.sov.uk.goscomb.net precise-updates/restricted TranslationIndex
Hit http://mirror.sov.uk.goscomb.net precise-updates/universe TranslationIndex
Hit http://mirror.sov.uk.goscomb.net precise-security/main Sources
Hit http://mirror.sov.uk.goscomb.net precise-security/restricted Sources
Hit http://mirror.sov.uk.goscomb.net precise-security/universe Sources
Hit http://mirror.sov.uk.goscomb.net precise-security/multiverse Sources
Hit http://mirror.sov.uk.goscomb.net precise-security/main amd64 Packages
Hit http://mirror.sov.uk.goscomb.net precise-security/restricted amd64 Packages
Hit http://mirror.sov.uk.goscomb.net precise-security/universe amd64 Packages
Hit http://mirror.sov.uk.goscomb.net precise-security/multiverse amd64 Packages
Hit http://mirror.sov.uk.goscomb.net precise-security/main i386 Packages
Hit http://mirror.sov.uk.goscomb.net precise-security/restricted i386 Packages
Hit http://mirror.sov.uk.goscomb.net precise-security/universe i386 Packages
Hit http://mirror.sov.uk.goscomb.net precise-security/multiverse i386 Packages
Hit http://mirror.sov.uk.goscomb.net precise-security/main TranslationIndex
Hit http://mirror.sov.uk.goscomb.net precise-security/multiverse TranslationIndex
Hit http://mirror.sov.uk.goscomb.net precise-security/restricted TranslationIndex
Hit http://mirror.sov.uk.goscomb.net precise-security/universe TranslationIndex
Get:1 http://mirror.sov.uk.goscomb.net precise/main Translation-en_GB [96.4 kB]
Hit http://mirror.sov.uk.goscomb.net precise/main Translation-en
Get:2 http://mirror.sov.uk.goscomb.net precise/multiverse Translation-en_GB [79.8 kB]
Hit http://mirror.sov.uk.goscomb.net precise/multiverse Translation-en       
Get:3 http://mirror.sov.uk.goscomb.net precise/restricted Translation-en_GB [2,406 B]
Hit http://mirror.sov.uk.goscomb.net precise/restricted Translation-en       
Get:4 http://mirror.sov.uk.goscomb.net precise/universe Translation-en_GB [5,492 B]
Hit http://mirror.sov.uk.goscomb.net precise/universe Translation-en       
Get:5 http://mirror.sov.uk.goscomb.net precise-updates/main Translation-en_GB [96.4 kB]
Hit http://mirror.sov.uk.goscomb.net precise-updates/main Translation-en     
Get:6 http://mirror.sov.uk.goscomb.net precise-updates/multiverse Translation-en_GB [79.8 kB]
Hit http://mirror.sov.uk.goscomb.net precise-updates/multiverse Translation-en
Get:7 http://mirror.sov.uk.goscomb.net precise-updates/restricted Translation-en_GB [2,406 B]
Hit http://mirror.sov.uk.goscomb.net precise-updates/restricted Translation-en
Get:8 http://mirror.sov.uk.goscomb.net precise-updates/universe Translation-en_GB [5,492 B]
Hit http://mirror.sov.uk.goscomb.net precise-updates/universe Translation-en
Hit http://mirror.sov.uk.goscomb.net precise-security/main Translation-en
Hit http://mirror.sov.uk.goscomb.net precise-security/multiverse Translation-en
Hit http://mirror.sov.uk.goscomb.net precise-security/restricted Translation-en
Hit http://mirror.sov.uk.goscomb.net precise-security/universe Translation-en
Fetched 368 kB in 1s (345 kB/s)                           
Reading package lists... Done
phil@panawe:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libav-tools libavcodec-extra-53 libavdevice53 libavfilter2
  libavformat-extra-53 libavutil-extra-51 libpostproc-extra-52
  libswscale-extra-2 nvidia-304
9 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
Need to get 72.6 MB of archives.
After this operation, 593 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://mirror.sov.uk.goscomb.net/ubuntu/ precise-updates/main libav-tools amd64 4:0.8.15-0ubuntu0.12.04.1 [613 kB]
Get:2 http://mirror.sov.uk.goscomb.net/ubuntu/ precise-updates/universe libpostproc-extra-52 amd64 4:0.8.15ubuntu0.12.04.1 [63.4 kB]
Get:3 http://mirror.sov.uk.goscomb.net/ubuntu/ precise-updates/main libavfilter2 amd64 4:0.8.15-0ubuntu0.12.04.1 [80.6 kB]
Get:4 http://mirror.sov.uk.goscomb.net/ubuntu/ precise-updates/universe libswscale-extra-2 amd64 4:0.8.15ubuntu0.12.04.1 [92.1 kB]
Get:5 http://mirror.sov.uk.goscomb.net/ubuntu/ precise-updates/main libavdevice53 amd64 4:0.8.15-0ubuntu0.12.04.1 [29.1 kB]
Get:6 http://mirror.sov.uk.goscomb.net/ubuntu/ precise-updates/universe libavformat-extra-53 amd64 4:0.8.15ubuntu0.12.04.1 [490 kB]
Get:7 http://mirror.sov.uk.goscomb.net/ubuntu/ precise-updates/universe libavcodec-extra-53 amd64 4:0.8.15ubuntu0.12.04.1 [2,937 kB]
Get:8 http://mirror.sov.uk.goscomb.net/ubuntu/ precise-updates/universe libavutil-extra-51 amd64 4:0.8.15ubuntu0.12.04.1 [66.8 kB]
Get:9 http://mirror.sov.uk.goscomb.net/ubuntu/ precise-updates/restricted nvidia-304 amd64 304.116-0ubuntu0.0.1 [68.3 MB]
Fetched 72.6 MB in 1min 11s (1,013 kB/s)                                       
(Reading database ... 1273653 files and directories currently installed.)
Preparing to replace libav-tools 4:0.8.13-0ubuntu0.12.04.1 (using .../libav-tools_4%3a0.8.15-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement libav-tools ...
Preparing to replace libpostproc-extra-52 4:0.8.13ubuntu0.12.04.1 (using .../libpostproc-extra-52_4%3a0.8.15ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement libpostproc-extra-52 ...
Preparing to replace libavfilter2 4:0.8.13-0ubuntu0.12.04.1 (using .../libavfilter2_4%3a0.8.15-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement libavfilter2 ...
Preparing to replace libswscale-extra-2 4:0.8.13ubuntu0.12.04.1 (using .../libswscale-extra-2_4%3a0.8.15ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement libswscale-extra-2 ...
Preparing to replace libavdevice53 4:0.8.13-0ubuntu0.12.04.1 (using .../libavdevice53_4%3a0.8.15-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement libavdevice53 ...
Preparing to replace libavformat-extra-53 4:0.8.13ubuntu0.12.04.1 (using .../libavformat-extra-53_4%3a0.8.15ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement libavformat-extra-53 ...
Preparing to replace libavcodec-extra-53 4:0.8.13ubuntu0.12.04.1 (using .../libavcodec-extra-53_4%3a0.8.15ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement libavcodec-extra-53 ...
Preparing to replace libavutil-extra-51 4:0.8.13ubuntu0.12.04.1 (using .../libavutil-extra-51_4%3a0.8.15ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement libavutil-extra-51 ...
Preparing to replace nvidia-304 304.88-0ubuntu0.0.3 (using .../nvidia-304_304.116-0ubuntu0.0.1_amd64.deb) ...
Removing all DKMS Modules


```

Terminal seems to be hanging after "removing all DKMS modules".

Thanks for your help.

---

### Post by Panawe on 2014-08-12
Turns out the Terminal wasn't hanging, I was being impatient. here's the last bit...

```

Removing all DKMS Modules
Done.
Unpacking replacement nvidia-304 ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Setting up libavutil-extra-51 (4:0.8.15ubuntu0.12.04.1) ...
Setting up libavcodec-extra-53 (4:0.8.15ubuntu0.12.04.1) ...
Setting up libavformat-extra-53 (4:0.8.15ubuntu0.12.04.1) ...
Setting up libavdevice53 (4:0.8.15-0ubuntu0.12.04.1) ...
Setting up libswscale-extra-2 (4:0.8.15ubuntu0.12.04.1) ...
Setting up libavfilter2 (4:0.8.15-0ubuntu0.12.04.1) ...
Setting up libpostproc-extra-52 (4:0.8.15ubuntu0.12.04.1) ...
Setting up libav-tools (4:0.8.15-0ubuntu0.12.04.1) ...
Setting up nvidia-304 (304.116-0ubuntu0.0.1) ...
INFO:Enable nvidia-304
DEBUG:Parsing /usr/share/nvidia-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/nvidia-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/nvidia-common/quirks/dell_latitude
Loading new nvidia-304-304.116 DKMS files...
Building only for 3.2.0-67-generic
Building for architecture x86_64
Building initial module for 3.2.0-67-generic
Done.

nvidia_304:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-67-generic/updates/dkms/

depmod....

DKMS: install completed.
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
phil@panawe:~$ 


```

---

### Post by Bashing-om on 2014-08-12
Panawe; Now That looks good !

Cooking with Crisco now.

OK now go ahead and complete the 12.04 update:
```

sudo apt-get dist-upgrade

``` which DOES NOT do a release upgrade, it is apt-get's smart mode to deal with packing requirements. It only updates installed packages. In this case to install those held packages.
That command may now not produce anything as I now see:
> 
9 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.


But run it anyway, just for cheap insurance.

[INDENT][INDENT][INDENT]getting ready to jump
[/INDENT][/INDENT][/INDENT]

---

### Post by grahammechanical on 2014-08-12
I am concerned about this
> 
[COLOR=#000000]==> /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-precise.list <== [/COLOR]
[COLOR=#000000]deb [/COLOR][http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu)[COLOR=#000000] precise main [/COLOR]
[COLOR=#000000]deb-src [/COLOR][http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu)[COLOR=#000000] precise main [/COLOR]

[https://launchpad.net/~ubuntu-x-swat/+archive/ubuntu/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/ubuntu/x-updates)

Is this why upgrade manager is unable to calculate the upgrade?

> [COLOR=#000000]An unresolvable problem occurred while calculating the upgrade. [/COLOR]

[COLOR=#000000]This can be caused by: [/COLOR]
[COLOR=#000000]* Upgrading to a pre-release version of Ubuntu [/COLOR]
[COLOR=#000000]* Running the current pre-release version of Ubuntu [/COLOR]
[COLOR=#000000]* _Unofficial software packages not provided by Ubuntu_ [/COLOR]

You have X.Org components that the upgrade scripts are not expecting and they may even be different from what is in 14.04. Perhaps a fresh install of 14.04 would be the easy option from here on. Or try this and start again.

> [COLOR=#333333][FONT=monospace]If you are upgrading from one release to another with this PPA activated, please install the ppa-purge package and use it to downgrade everything in here beforehand. sudo ppa-purge ppa:ubuntu-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]x-swat/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]x-updates will do it.[/FONT][/COLOR]

Regards.

---

### Post by Panawe on 2014-08-13
Hi Bashing-om, and thanks for your help.
I've done the last step (sudo apt-get dist-upgrade) and got the following response...
```

phil@panawe:~$ sudo apt-get dist-upgrade
[sudo] password for phil: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
phil@panawe:~$ 

```

Thanks for the post grahammechanical. I did as you suggested but got the message "ppa-purge: command not found". I did uncheck all the ppa boxes in the Other Software menu of the Sources List.

Thanks again to you both.

---

### Post by Panawe on 2014-08-13
Just for the hell of it I tried upgrading via package manager but it fell over again at the "setting new software channels" stage with the following...

```

   An unresolvable problem occurred while calculating the upgrade.
 

This can be caused by: 

  * Upgrading to a pre-release version of Ubuntu
 

  * Running the current pre-release version of Ubuntu
 

  * Unofficial software packages not provided by Ubuntu
 

 If none of this applies, then please report this bug using the command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal.

```

---

### Post by Bashing-om on 2014-08-13
@ grahammechanical; Wow,

Great catch - makes me question why I did not also see that one - must have a real bad case of tunnel vision.

@ Panawe; The risk is increased; if you decide to proceed with the release upgrade have good backups of your data.
On your word we go onto the next steps in preperation.
---------------------------------

I somehow failed to post the ups last night .
OK as Graham advises, we must revert the x-org PPA back to what is available in the ubuntu's software repository.
To do that one has to install the ppa-purge tool.
To install ppa-purge enter:
```

sudo apt-get install ppa-purge

```

I do hope that the last attempt did put all things back to 12.04 and now we can try the release upgrade once more.
No PPAs enabled
No proprietary drivers in use
No screen saver active
system fully updated

==>>> ready set GO

[INDENT][INDENT][INDENT]it takes a village
[/INDENT][/INDENT][/INDENT]

---

### Post by Panawe on 2014-08-13
Okay, installed "ppa-purge". Do I now go ahead with "[COLOR=#333333][FONT=monospace]sudo ppa-purge ppa:ubuntu-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]x-swat/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]x-updates"?

Off to bed now so I'll think over whether to go ahead with the upgrade. I've been reading about the way 14.04 blanks the hard drive while upgrading!!!
[/FONT][/COLOR]

---

### Post by Bashing-om on 2014-08-13
Panawe; Yepper !

Then make sure the PPA is "commented out" in /etc/apt/sources.list.d, and I expect you are ready to go for it.
Keep in mind good backups are good insurance.
Remember to also disable any screen saver that you may have.

[INDENT][INDENT]3rd time is the charm
[/INDENT][/INDENT]

---

### Post by Panawe on 2014-08-14
What do you make of this?

```

[COLOR=#333333][FONT=monospace][/FONT][/COLOR][COLOR=#333333][FONT=monospace][/FONT][/COLOR][COLOR=#333333][FONT=monospace][/FONT][/COLOR]phil@panawe:~$ sudo ppa-purge ppa:ubuntu-x-swat/x-updates
[sudo] password for phil: 
Updating packages lists
PPA to be removed: ubuntu-x-swat x-updates
Warning:  Could not find package list for PPA: ubuntu-x-swat x-updates
phil@panawe:~$ 


```

---

### Post by Panawe on 2014-08-14
Okay, I've got this far but not sure how to comment out PPA entries.
```

phil@panawe:~$ ls
Anyrail                      Map Overlays  Podcasts
Desktop                      Map.png       Public
doc 120121 Freud v Jung.mp3  Maps          Radio
Documents                    Modelling     SillyHat2010.JPG
Downloads                    Money         Templates
DSC_4820.JPG                 Music         Thunderbird Attachments
ebooks                       My Garmin     Tunes
Encfs                        News          Ubuntu One
Films                        NYD2010q.JPG  Videos
Firefox_wallpaper.png        P1000628.JPG  Webcam_Pictures
JavaMorph                    Photography   Yellowstone
JOSM                         Pictures
phil@panawe:~$ cd .
phil@panawe:~$ ls
Anyrail                      Map Overlays  Podcasts
Desktop                      Map.png       Public
doc 120121 Freud v Jung.mp3  Maps          Radio
Documents                    Modelling     SillyHat2010.JPG
Downloads                    Money         Templates
DSC_4820.JPG                 Music         Thunderbird Attachments
ebooks                       My Garmin     Tunes
Encfs                        News          Ubuntu One
Films                        NYD2010q.JPG  Videos
Firefox_wallpaper.png        P1000628.JPG  Webcam_Pictures
JavaMorph                    Photography   Yellowstone
JOSM                         Pictures
phil@panawe:~$ cd ..
phil@panawe:/home$ ls
deleteme  phil
phil@panawe:/home$ cd ..
phil@panawe:/$ ls
bin    etc             lib         lost+found  proc  selinux  usr
boot   home            lib32       media       root  srv      var
cdrom  initrd.img      lib64       mnt         run   sys      vmlinuz
dev    initrd.img.old  libnss3.so  opt         sbin  tmp      vmlinuz.old
phil@panawe:/$ cd /etc
phil@panawe:/etc$ ls
acpi                           gshadow              passwd-
adduser.conf                   gshadow-             pcmcia
akonadi                        gtk-2.0              perl
alternatives                   gtk-3.0              pkcs11
anacrontab                     hal                  pm
apache2                        hdparm.conf          pmount.allow
apg.conf                       hellanzb.conf        pnm2ppa.conf
apm                            host.conf            polkit-1
apparmor                       hostname             popularity-contest.conf
apparmor.d                     hosts                ppp
apport                         hosts.allow          printcap
apt                            hosts.deny           profile
ardour2                        hp                   profile.d
at.deny                        icedtea-web          protocols
at-spi2                        ifplugd              pulse
avahi                          ImageMagick          purple
avserver.conf                  init                 python
bash.bashrc                    init.d               python2.6
bash_completion                initramfs-tools      python2.7
bash_completion.d              inputrc              qt3
bindresvport.blacklist         insserv              rarfiles.lst
blkid.conf                     insserv.conf         rc0.d
blkid.tab                      insserv.conf.d       rc1.d
bluetooth                      iproute2             rc2.d
bogofilter.cf                  issue                rc3.d
bonobo-activation              issue.net            rc4.d
brlapi.key                     java-6-openjdk       rc5.d
brltty                         java-6-sun           rc6.d
brltty.conf                    javascript-common    rc.local
byobu                          kbd                  rcS.d
ca-certificates                kde3                 request-key.conf
ca-certificates.conf           kernel               resolvconf
ca-certificates.conf.dpkg-old  kernel-img.conf      resolv.conf
calendar                       kerneloops.conf      rmt
chatscripts                    ldap                 rpc
checkbox.d                     ld.so.cache          rsyslog.conf
clamav                         ld.so.conf           rsyslog.d
clutter-imcontext              ld.so.conf.d         samba
colord.conf                    legal                sane.d
compizconfig                   lftp.conf            sbackup.conf
computer-janitor.d             libao.conf           screenrc
ConsoleKit                     libnl-3              securetty
console-setup                  libpaper.d           security
couchdb                        libreoffice          sensors3.conf
cracklib                       lightdm              sensors.d
cron.d                         lighttpd             services
cron.daily                     lintianrc            sgml
cron.hourly                    locale.alias         shadow
cron.monthly                   localtime            shadow-
crontab                        logcheck             shells
cron.weekly                    login.defs           skel
crypttab                       logrotate.conf       snmp
cups                           logrotate.d          sound
cupshelpers                    lsb-base             spamassassin
dbus-1                         lsb-base-logging.sh  speech-dispatcher
dconf                          lsb-release          ssh
debconf.conf                   ltrace.conf          ssl
debian_version                 magic                sudoers
default                        magic.mime           sudoers.d
defoma                         mail                 su-to-rootrc
deluser.conf                   mailcap              sysctl.conf
depmod.d                       mailcap.order        sysctl.d
dhcp                           mail.rc              systemd
dhcp3                          manpath.config       terminfo
dictionaries-common            menu                 texmf
dkms                           menu-methods         thunderbird
doc-base                       mime.types           timezone
dpkg                           mke2fs.conf          timidity
emacs                          modprobe.d           tor
environment                    modules              torsocks.conf
esound                         mono                 ts.conf
ffserver.conf                  motd                 ucf.conf
firefox                        mplayer              udev
fonts                          mtab                 ufw
foomatic                       mtab.fuselock        updatedb.conf
fstab                          mtools.conf          update-manager
fstab_backup                   mysql                update-motd.d
fstab.d                        nanorc               update-notifier
fuse.conf                      nero                 UPower
gai.conf                       netscsid.conf        usb_modeswitch.conf
gamin                          network              usb_modeswitch.d
gconf                          NetworkManager       vdpau_wrapper.cfg
gdb                            networks             vga
gdm                            newt                 vim
ghostscript                    nsswitch.conf        vlc
gimp                           obex-data-server     vtrgb
ginn                           ODBCDataSources      w3m
gnome                          odbc.ini             wgetrc
gnome-app-install              odbcinst.ini         wildmidi
gnome-settings-daemon          openal               wodim.conf
gnome-system-tools             openbve              wpa_supplicant
gnome-vfs-2.0                  OpenCL               X11
gnome-vfs-mime-magic           opt                  xdg
gnucash                        os-release           xml
gre.d                          pam.conf             xpdf
groff                          pam.d                xul-ext
group                          pango                xulrunner-1.9.2
group-                         papersize            zsh_command_not_found
grub.d                         passwd
phil@panawe:/etc$ cd /apt
bash: cd: /apt: No such file or directory
phil@panawe:/etc$ sudo gedit /etc/apt/sources.list.d
[sudo] password for phil: 
phil@panawe:/etc$ cd /etc/apt/sources.list.d
phil@panawe:/etc/apt/sources.list.d$ ls
gencfsm-ppa-precise.list
gencfsm-ppa-precise.list.distUpgrade
gencfsm-ppa-precise.list.save
google-chrome.list
google-chrome.list.distUpgrade
google-chrome.list.save
google-earth.list
google-earth.list.distUpgrade
google-earth.list.save
medibuntu.list
medibuntu.list.distUpgrade
medibuntu.list.save
openshot_developers-ppa-maverick.list
openshot_developers-ppa-maverick.list.distUpgrade
openshot_developers-ppa-maverick.list.save
tikhonov-misc-precise.list
tikhonov-misc-precise.list.distUpgrade
tikhonov-misc-precise.list.save
ubuntu-x-swat-x-updates-precise.list
ubuntu-x-swat-x-updates-precise.list.distUpgrade
ubuntu-x-swat-x-updates-precise.list.save
user-phil-maverick.list
user-phil-maverick.list.distUpgrade
user-phil-maverick.list.save
phil@panawe:/etc/apt/sources.list.d$ 


```

Cheers in advance.

---

### Post by Bashing-om on 2014-08-14
Panawe; Well,

Maybe take the package manager at it's word here, and see if what "I Think" is so:
```

ls -al /var/lib/dpkg/info/*nvidia*

```
Which may lead to a number of conclusions.

Let's see what the result is before
[INDENT][INDENT][INDENT]jumping to any conclusion
[/INDENT][/INDENT][/INDENT]

---

### Post by Panawe on 2014-08-14
here's the result.
```

phil@panawe:~$ ls -al /var/lib/dpkg/info/*nvidia*
-rw-r--r-- 1 root root  4014 Feb  4  2014 /var/lib/dpkg/info/nvidia-173.list
-rw-r--r-- 1 root root  4525 Dec 18  2013 /var/lib/dpkg/info/nvidia-173.md5sums
-rwxr-xr-x 1 root root  6353 Dec 18  2013 /var/lib/dpkg/info/nvidia-173.postinst
-rwxr-xr-x 1 root root  1063 Dec 18  2013 /var/lib/dpkg/info/nvidia-173.postrm
-rwxr-xr-x 1 root root 10651 Dec 18  2013 /var/lib/dpkg/info/nvidia-173.preinst
-rwxr-xr-x 1 root root   932 Dec 18  2013 /var/lib/dpkg/info/nvidia-173.prerm
-rw-r--r-- 1 root root   131 Dec 18  2013 /var/lib/dpkg/info/nvidia-173.shlibs
-rw-r--r-- 1 root root    39 Dec 18  2013 /var/lib/dpkg/info/nvidia-304.conffiles
-rw-r--r-- 1 root root  9159 Aug 12 22:35 /var/lib/dpkg/info/nvidia-304.list
-rw-r--r-- 1 root root 11664 Dec 18  2013 /var/lib/dpkg/info/nvidia-304.md5sums
-rwxr-xr-x 1 root root  9245 Dec 18  2013 /var/lib/dpkg/info/nvidia-304.postinst
-rwxr-xr-x 1 root root  1487 Dec 18  2013 /var/lib/dpkg/info/nvidia-304.postrm
-rwxr-xr-x 1 root root 10841 Dec 18  2013 /var/lib/dpkg/info/nvidia-304.preinst
-rwxr-xr-x 1 root root  1140 Dec 18  2013 /var/lib/dpkg/info/nvidia-304.prerm
-rw-r--r-- 1 root root    51 Dec 18  2013 /var/lib/dpkg/info/nvidia-304.shlibs
-rw-r--r-- 1 root root    47 Dec 18  2013 /var/lib/dpkg/info/nvidia-304-updates.conffiles
-rw-r--r-- 1 root root 10886 Feb  4  2014 /var/lib/dpkg/info/nvidia-304-updates.list
-rw-r--r-- 1 root root 12976 Dec 18  2013 /var/lib/dpkg/info/nvidia-304-updates.md5sums
-rwxr-xr-x 1 root root  9453 Dec 18  2013 /var/lib/dpkg/info/nvidia-304-updates.postinst
-rwxr-xr-x 1 root root  1535 Dec 18  2013 /var/lib/dpkg/info/nvidia-304-updates.postrm
-rwxr-xr-x 1 root root 10849 Dec 18  2013 /var/lib/dpkg/info/nvidia-304-updates.preinst
-rwxr-xr-x 1 root root  1180 Dec 18  2013 /var/lib/dpkg/info/nvidia-304-updates.prerm
-rw-r--r-- 1 root root    51 Dec 18  2013 /var/lib/dpkg/info/nvidia-304-updates.shlibs
-rw-r--r-- 1 root root   258 Jan 25  2011 /var/lib/dpkg/info/nvidia-96-modaliases.list
-rw-r--r-- 1 root root   240 Nov 22  2010 /var/lib/dpkg/info/nvidia-96-modaliases.md5sums
-rw-r--r-- 1 root root    26 Oct  2  2012 /var/lib/dpkg/info/nvidia-common.conffiles
-rwxr-xr-x 1 root root   197 Oct  2  2012 /var/lib/dpkg/info/nvidia-common.config
-rw-r--r-- 1 root root  1728 Oct  5  2012 /var/lib/dpkg/info/nvidia-common.list
-rw-r--r-- 1 root root  1466 Oct  2  2012 /var/lib/dpkg/info/nvidia-common.md5sums
-rwxr-xr-x 1 root root   163 Oct  2  2012 /var/lib/dpkg/info/nvidia-common.postinst
-rwxr-xr-x 1 root root   206 Oct  2  2012 /var/lib/dpkg/info/nvidia-common.postrm
-rwxr-xr-x 1 root root   827 Oct  2  2012 /var/lib/dpkg/info/nvidia-common.preinst
-rwxr-xr-x 1 root root   263 Oct  2  2012 /var/lib/dpkg/info/nvidia-common.prerm
-rw-r--r-- 1 root root   361 Oct  2  2012 /var/lib/dpkg/info/nvidia-common.templates
-rw-r--r-- 1 root root   228 Dec  6  2013 /var/lib/dpkg/info/nvidia-current.list
-rw-r--r-- 1 root root   156 Dec  4  2013 /var/lib/dpkg/info/nvidia-current.md5sums
-rw-r--r-- 1 root root   229 Feb  4  2014 /var/lib/dpkg/info/nvidia-current-updates.list
-rw-r--r-- 1 root root    81 Dec 18  2013 /var/lib/dpkg/info/nvidia-current-updates.md5sums
-rw-r--r-- 1 root root   169 Feb  4  2014 /var/lib/dpkg/info/nvidia-settings-304.list
-rw-r--r-- 1 root root    78 Dec 18  2013 /var/lib/dpkg/info/nvidia-settings-304.md5sums
-rw-r--r-- 1 root root   193 Feb  4  2014 /var/lib/dpkg/info/nvidia-settings-304-updates.list
-rw-r--r-- 1 root root    86 Dec 18  2013 /var/lib/dpkg/info/nvidia-settings-304-updates.md5sums
-rw-r--r-- 1 root root    53 Dec 18  2013 /var/lib/dpkg/info/nvidia-settings.conffiles
-rw-r--r-- 1 root root  1778 Feb  4  2014 /var/lib/dpkg/info/nvidia-settings.list
-rw-r--r-- 1 root root  2268 Dec 18  2013 /var/lib/dpkg/info/nvidia-settings.md5sums
-rwxr-xr-x 1 root root   844 Dec 18  2013 /var/lib/dpkg/info/nvidia-settings.preinst
-rw-r--r-- 1 root root   181 Feb  4  2014 /var/lib/dpkg/info/nvidia-settings-updates.list
-rw-r--r-- 1 root root    82 Dec 18  2013 /var/lib/dpkg/info/nvidia-settings-updates.md5sums
phil@panawe:~$ 


```

---

### Post by Bashing-om on 2014-08-14
Panawe;; Great !

You are trying to work this out:

> 
[color=red]sudo[/color] gedit /etc/apt/sources.list.d

The use of "sudo" for ANY graphical application is a NO-NO ! It's use in such a instance/manner can have serious side effects. Use the term gksudo for activating a GUI application with those elevated privileges  .

With your above outputs, let's see what the "ubuntu-x-swat-x-updates-precise.list" directory contains for the source locator;
```

ls -al /etc/apt/sources.list.d ## where the modifiers 'al' mean give us 'A'll the listings in the directory, and 'L'ong, all the info available .

```
In that output is "ubuntu-x-swat-x-updates-precise.list" - the listing of interest. Look and see:
```

cat /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-precise.list

``` and from that output one can direct the action of the ppa-purge for this application.

Make sense ? can do ? what results ?

We need all PPA's packaging reverted back to ubuntu's repository, and in particular the Nvidia graphics, as the upgrade will in deed break the operating system. It is no fault to ubuntu, as ubuntu has no control over what Nvidia - or other 3rd party software vendors - does or what you choose to install. The upgrade process belongs solely to ubuntu, and ubuntu works with ubuntu files.

[INDENT][INDENT]the care and feeding of your ubuntu
[/INDENT][/INDENT]

---

### Post by Panawe on 2014-08-14
Here are the results.
```

phil@panawe:~$ ls -al /etc/apt/sources.list.d
total 104
drwxr-xr-x 2 root root 4096 Aug 12 11:27 .
drwxr-xr-x 6 root root 4096 Aug 14 19:20 ..
-rw-r--r-- 1 root root  130 Aug 13 11:22 gencfsm-ppa-precise.list
-rw-r--r-- 1 root root  130 Aug 13 11:21 gencfsm-ppa-precise.list.distUpgrade
-rw-r--r-- 1 root root  130 Aug 12 22:25 gencfsm-ppa-precise.list.save
-rw-r--r-- 1 root root  178 Aug 13 11:22 google-chrome.list
-rw-r--r-- 1 root root  178 Aug 13 11:21 google-chrome.list.distUpgrade
-rw-r--r-- 1 root root  178 Aug 12 22:25 google-chrome.list.save
-rw-r--r-- 1 root root  177 Aug 13 11:22 google-earth.list
-rw-r--r-- 1 root root  177 Aug 13 11:21 google-earth.list.distUpgrade
-rw-r--r-- 1 root root  177 Aug 12 22:25 google-earth.list.save
-rw-r--r-- 1 root root  287 Aug 13 11:22 medibuntu.list
-rw-r--r-- 1 root root  287 Aug 13 11:21 medibuntu.list.distUpgrade
-rw-r--r-- 1 root root  287 Aug 12 22:25 medibuntu.list.save
-rw-r--r-- 1 root root  156 Aug 13 11:22 openshot_developers-ppa-maverick.list
-rw-r--r-- 1 root root  156 Aug 13 11:21 openshot_developers-ppa-maverick.list.distUpgrade
-rw-r--r-- 1 root root  156 Aug 12 22:25 openshot_developers-ppa-maverick.list.save
-rw-r--r-- 1 root root  134 Aug 13 11:22 tikhonov-misc-precise.list
-rw-r--r-- 1 root root  134 Aug 13 11:21 tikhonov-misc-precise.list.distUpgrade
-rw-r--r-- 1 root root  134 Aug 12 22:25 tikhonov-misc-precise.list.save
-rw-r--r-- 1 root root  154 Aug 13 11:22 ubuntu-x-swat-x-updates-precise.list
-rw-r--r-- 1 root root  154 Aug 13 11:21 ubuntu-x-swat-x-updates-precise.list.distUpgrade
-rw-r--r-- 1 root root  154 Aug 12 22:25 ubuntu-x-swat-x-updates-precise.list.save
-rw-r--r-- 1 root root  128 Aug 13 11:22 user-phil-maverick.list
-rw-r--r-- 1 root root  128 Aug 13 11:21 user-phil-maverick.list.distUpgrade
-rw-r--r-- 1 root root  128 Aug 12 22:25 user-phil-maverick.list.save
phil@panawe:~$ cat /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-precise.list
# deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu precise main
# deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu precise main
phil@panawe:~$ 


```

Meaningless to me.

---

### Post by Bashing-om on 2014-08-14
Panawe; We are making progress.

How can I more enlighten you, we want you to know and learn:
> 
Meaningless to me.


Presently working on getting the proprietary drivers reverted.
To do so in this instance with proprietary Nvidia grphics drivers installed will use the "ppa-purge" tool to do so:
I think , now,in order for the tool to run the PPA must be enabled:
Let's do this in small steps - if you do not mind, for my little minds sake.
enable the repository:
fire up the text editor once more;
```

gksudo gedit /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-precise.list

```
where you see:
"# deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) precise main
remove the comment (#) character at the start of the line and save the file, exit back to the terminal.
Now let's do the graphics driver reversion.
The syntax is " sudo ppa-purge ppa:<repository-name>/<subdirectory>"
So try as terminal command:
```

sudo ppa-purge ppa:launchpad.net/ubuntu-x-swat

```
Try this and see what results.

[INDENT]-> maybe yes
[INDENT][INDENT][INDENT][INDENT]but maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Panawe on 2014-08-14
Okay, here it is.
```

phil@panawe:~$ gksudo gedit /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-precise.list
phil@panawe:~$ sudo ppa-purge ppa:launchpad.net/ubuntu-x-swat
Updating packages lists
PPA to be removed: launchpad.net ubuntu-x-swat
Warning:  Could not find package list for PPA: launchpad.net ubuntu-x-swat
phil@panawe:~$ 


```

Sorry, don't mean to be obstructive and I understand generally what we are trying to, do it's just the detail that confounds me.

---

### Post by Bashing-om on 2014-08-14
Panawe; Hummpppff !

Don't feel bad about that " it's just the detail that confounds me." as that last output confounds me too !
Let's take a pause and await and see if Graham pops back in here and sheds some light on our confusion.
Likely my construct is in error. But maybe not and there other problems farther up. As I do not run Nvidia graphics I hve no direct experience to draw on.

One thing for sure, the proprietary graphics driver has to be reverted. 'till that is done we are dead in the water.

[INDENT][INDENT]patience is  virtue
[/INDENT][/INDENT]

---

### Post by Panawe on 2014-08-14
Okay, hanging fire at this end.

---

### Post by Bashing-om on 2014-08-16
Panawe; Hello,

Not my entent to leave you hanging or stranded.
I am in the process of research and see what I can find to purge the PPA drivers.

As soon as I know ->

[INDENT][INDENT][INDENT]I'll Be Baccckkk
[/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-08-16
Panawe; I am Bacckk !

My scratch pad:
/ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu <- the source;
[https://launchpad.net/~ubuntu-x-swat/+archive/ubuntu/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/ubuntu/x-updates) <- the web site !
And the directive from the authors to revert the PPA to the repository versions:
(as Graham has already advised)
> 
If you are upgrading from one release to another with this PPA activated, please install the ppa-purge package and use it to downgrade everything in here beforehand. sudo ppa-purge ppa:ubuntu-x-swat/x-updates will do it.


My conclusion:
So with that source list enabled ( uncommented ); try again:
Terminal command:
```

sudo ppa-purge ppa:ubuntu-x-swat/x-update

```

And let's see what happens ( yeah again !) and then look at manually intervening and taking matters into our own hands.

[INDENT][INDENT][INDENT]away we go again
[/INDENT][/INDENT][/INDENT]

---

### Post by Panawe on 2014-08-17
Ah, sorry, lost the thread for a while and toyed with the idea of loading from DVD.

Here's the output...#
```

phil@panawe:~$ sudo ppa-purge ppa:ubuntu-x-swat/x-update
[sudo] password for phil: 
Updating packages lists
W: Duplicate sources.list entry cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2)/ trusty/main i386 Packages (/var/lib/apt/lists/Ubuntu%2014.04.1%20LTS%20%5fTrusty%20Tahr%5f%20-%20Release%20amd64%20(20140722.2)_dists_trusty_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2)/ trusty/restricted i386 Packages (/var/lib/apt/lists/Ubuntu%2014.04.1%20LTS%20%5fTrusty%20Tahr%5f%20-%20Release%20amd64%20(20140722.2)_dists_trusty_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
PPA to be removed: ubuntu-x-swat x-update
Warning:  Could not find package list for PPA: ubuntu-x-swat x-update
phil@panawe:~$ 


```

And if installing 14.04 from a disk is best here's two snapshots from Gparted...

---

### Post by Bashing-om on 2014-08-17
Panawe; Hey;

Hanging in here with you.

Presently we must repair the source.list file:
> 
W: Duplicate sources.list entry cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2)/ trusty/main i386 Packages (/var/lib/apt/lists/Ubuntu%2014.04.1%20LTS%20%5fTrusty%20Tahr%5f%20-%20Release%20amd64%20(20140722.2)_dists_trusty_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2)/ trusty/restricted i386 Packages (/var/lib/apt/lists/Ubuntu%2014.04.1%20LTS%20%5fTrusty%20Tahr%5f%20-%20Release%20amd64%20(20140722.2)_dists_trusty_restricted_binary-i386_Packages)
W:


Uncheck the CD box in "Software Sources" ;
Then clean out the cache and get new index files:
```

sudo apt-get clean
sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update

```

Reboot the system and verify the system integrity:
```

sudo apt-get update
sudo apt-get upgrade

```

 If all is good at this point and only if good - we do not need to compound the problems - proceed onto ->

Now let's return to the issue of reverting the Nvidia drivers:
As the x-swat PPA does not seen to be fully installed let's shotgun remove Nvidia, restore the Desktop, and install the open source driver (nouveau):
I am - assuming - you are running ubuntu with the standard desk top environment - unity- ! ELSE, stop and advise.
```

sudo nvidia-installer --uninstall ##just in the event the installer is still around ##
sudo nvidia-settings --uninstall ##same same as above, that tool may or may not exist##
apt-get purge nvidia-*
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf-old

sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall ubuntu-desktop
sudo apt-get install xserver-xorg-video-nouveau

```

Once more reboot for the changes to take effect.

------------------------------------
Now, if all looks good we can proceed with the release upgrade.

---

### Post by Panawe on 2014-08-17
Hi, thanks for your patience.
All doesn't look so good though...
```

phil@panawe:~$ sudo apt-get update
[sudo] password for phil: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
phil@panawe:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
phil@panawe:~$ sudo apt-get upgrade


```

Nothing critical I hope?

---

### Post by Bashing-om on 2014-08-17
Panawe; no cause for sweat yet:

This one:
> 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)

most generally is another instance of a package manager running. Can only have 1 active at any given time .

Mke sure all instance are closed out, then to make sure, reboot the system,
Then open a terminal and try once more:
```

sudo apt-get update
sudo apt-get upgrade

```
-when- that runs clean, pick up where you left off, as we try to purge Nvidia and install nouveau .

[INDENT][INDENT][INDENT]making progress
[INDENT][INDENT][INDENT][INDENT]slowly
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Panawe on 2014-08-17
This is straight after reboot.
```

phil@panawe:~$ sudo apt-get update
[sudo] password for phil: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
phil@panawe:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
phil@panawe:~$ 


```

Good to go?

---

### Post by Bashing-om on 2014-08-17
Panawe; Well then !

Make sure there is no other instance running:
```

ps -e | grep apt

```
Depending on that output, we 'unlock' dpkg. (nothing is great !)

[INDENT][INDENT]no step for a stepper
[/INDENT][/INDENT]

---

### Post by Panawe on 2014-08-17
This look okay?
```

phil@panawe:~$ ps -e | grep apt
phil@panawe:~$ sudo apt-get update
[sudo] password for phil: 
Hit http://ppa.launchpad.net precise Release.gpg
Hit http://mirror.sov.uk.goscomb.net precise Release.gpg
Hit http://mirror.sov.uk.goscomb.net precise-updates Release.gpg
Hit http://mirror.sov.uk.goscomb.net precise-security Release.gpg
Hit http://ppa.launchpad.net precise Release
Hit http://mirror.sov.uk.goscomb.net precise Release
Hit http://mirror.sov.uk.goscomb.net precise-updates Release
Hit http://mirror.sov.uk.goscomb.net precise-security Release
Hit http://ppa.launchpad.net precise/main Sources                     
Hit http://mirror.sov.uk.goscomb.net precise/main Sources
Hit http://mirror.sov.uk.goscomb.net precise/restricted Sources
Hit http://mirror.sov.uk.goscomb.net precise/universe Sources
Hit http://mirror.sov.uk.goscomb.net precise/multiverse Sources
Hit http://mirror.sov.uk.goscomb.net precise/main amd64 Packages
Hit http://mirror.sov.uk.goscomb.net precise/restricted amd64 Packages
Hit http://mirror.sov.uk.goscomb.net precise/universe amd64 Packages
Hit http://mirror.sov.uk.goscomb.net precise/multiverse amd64 Packages
Hit http://mirror.sov.uk.goscomb.net precise/main i386 Packages
Hit http://mirror.sov.uk.goscomb.net precise/restricted i386 Packages
Hit http://mirror.sov.uk.goscomb.net precise/universe i386 Packages
Hit http://mirror.sov.uk.goscomb.net precise/multiverse i386 Packages
Hit http://mirror.sov.uk.goscomb.net precise/main TranslationIndex
Hit http://mirror.sov.uk.goscomb.net precise/multiverse TranslationIndex
Hit http://mirror.sov.uk.goscomb.net precise/restricted TranslationIndex
Hit http://mirror.sov.uk.goscomb.net precise/universe TranslationIndex
Hit http://mirror.sov.uk.goscomb.net precise-updates/main Sources
Hit http://mirror.sov.uk.goscomb.net precise-updates/restricted Sources
Hit http://mirror.sov.uk.goscomb.net precise-updates/universe Sources
Hit http://mirror.sov.uk.goscomb.net precise-updates/multiverse Sources
Hit http://mirror.sov.uk.goscomb.net precise-updates/main amd64 Packages
Hit http://mirror.sov.uk.goscomb.net precise-updates/restricted amd64 Packages
Hit http://mirror.sov.uk.goscomb.net precise-updates/universe amd64 Packages
Hit http://mirror.sov.uk.goscomb.net precise-updates/multiverse amd64 Packages
Hit http://mirror.sov.uk.goscomb.net precise-updates/main i386 Packages
Hit http://mirror.sov.uk.goscomb.net precise-updates/restricted i386 Packages
Hit http://mirror.sov.uk.goscomb.net precise-updates/universe i386 Packages
Hit http://mirror.sov.uk.goscomb.net precise-updates/multiverse i386 Packages
Hit http://mirror.sov.uk.goscomb.net precise-updates/main TranslationIndex
Hit http://mirror.sov.uk.goscomb.net precise-updates/multiverse TranslationIndex
Hit http://mirror.sov.uk.goscomb.net precise-updates/restricted TranslationIndex
Hit http://mirror.sov.uk.goscomb.net precise-updates/universe TranslationIndex
Hit http://mirror.sov.uk.goscomb.net precise-security/main Sources
Hit http://mirror.sov.uk.goscomb.net precise-security/restricted Sources
Hit http://mirror.sov.uk.goscomb.net precise-security/universe Sources
Hit http://mirror.sov.uk.goscomb.net precise-security/multiverse Sources
Hit http://mirror.sov.uk.goscomb.net precise-security/main amd64 Packages
Hit http://mirror.sov.uk.goscomb.net precise-security/restricted amd64 Packages
Hit http://mirror.sov.uk.goscomb.net precise-security/universe amd64 Packages
Hit http://mirror.sov.uk.goscomb.net precise-security/multiverse amd64 Packages
Hit http://mirror.sov.uk.goscomb.net precise-security/main i386 Packages
Hit http://mirror.sov.uk.goscomb.net precise-security/restricted i386 Packages
Hit http://mirror.sov.uk.goscomb.net precise-security/universe i386 Packages
Hit http://mirror.sov.uk.goscomb.net precise-security/multiverse i386 Packages
Hit http://mirror.sov.uk.goscomb.net precise-security/main TranslationIndex
Hit http://mirror.sov.uk.goscomb.net precise-security/multiverse TranslationIndex
Hit http://mirror.sov.uk.goscomb.net precise-security/restricted TranslationIndex
Hit http://mirror.sov.uk.goscomb.net precise-security/universe TranslationIndex
Hit http://mirror.sov.uk.goscomb.net precise/main Translation-en_GB
Hit http://mirror.sov.uk.goscomb.net precise/main Translation-en
Hit http://mirror.sov.uk.goscomb.net precise/multiverse Translation-en_GB
Hit http://mirror.sov.uk.goscomb.net precise/multiverse Translation-en
Hit http://mirror.sov.uk.goscomb.net precise/restricted Translation-en_GB
Hit http://mirror.sov.uk.goscomb.net precise/restricted Translation-en
Hit http://mirror.sov.uk.goscomb.net precise/universe Translation-en_GB
Hit http://mirror.sov.uk.goscomb.net precise/universe Translation-en
Hit http://mirror.sov.uk.goscomb.net precise-updates/main Translation-en_GB
Hit http://mirror.sov.uk.goscomb.net precise-updates/main Translation-en
Hit http://mirror.sov.uk.goscomb.net precise-updates/multiverse Translation-en_GB
Hit http://mirror.sov.uk.goscomb.net precise-updates/multiverse Translation-en
Hit http://mirror.sov.uk.goscomb.net precise-updates/restricted Translation-en_GB
Hit http://mirror.sov.uk.goscomb.net precise-updates/restricted Translation-en
Hit http://mirror.sov.uk.goscomb.net precise-updates/universe Translation-en_GB
Hit http://mirror.sov.uk.goscomb.net precise-updates/universe Translation-en
Hit http://mirror.sov.uk.goscomb.net precise-security/main Translation-en
Hit http://mirror.sov.uk.goscomb.net precise-security/multiverse Translation-en
Hit http://mirror.sov.uk.goscomb.net precise-security/restricted Translation-en
Hit http://mirror.sov.uk.goscomb.net precise-security/universe Translation-en
Reading package lists... Done
phil@panawe:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
phil@panawe:~$ 


```

Did i say thank you?

---

### Post by Bashing-om on 2014-08-17
Panawe; Yepper;

'dpkg' is unlocked, continue on !

[INDENT][INDENT]meanwhile, back at the ranch
[/INDENT][/INDENT]

---

### Post by Panawe on 2014-08-17
There was a heart-stopping moment on reboot when the screen went crazy but I seem to back amongst the land of the living.

When I go for the upgrade I don't want anything changed on the second (storage) drive - I wondered about opening the case and physically disconnecting it?

---

### Post by Bashing-om on 2014-08-17
Panawe; Yeah;

Takes a bit for the kernel to 'reconfigure'.

OK, let's take a gander before leaping, as to what we have for a graphics driver ( after the release upgrade ya can try a proprietary driver if ya need/want )
for now what returns :
```

sudo lshw -C display

```

If that is good, ALL PPAs are disabled, no other proprietary software in effect, and screen saver turned off -> we go for it !

[INDENT][INDENT]look before we leap
[/INDENT][/INDENT]

---

### Post by Panawe on 2014-08-17
Here it is...
```

phil@panawe:~$ sudo lshw -C display
[sudo] password for phil: 
  *-display               
       description: VGA compatible controller
       product: G98 [GeForce 8400 GS Rev. 2]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:18 memory:fa000000-faffffff memory:d0000000-dfffffff memory:f8000000-f9ffffff ioport:ef00(size=128) memory:fb000000-fb01ffff
phil@panawe:~$ 


```

diver=nouveau - that's good isn't it?

---

### Post by Bashing-om on 2014-08-17
Panawe; Yeah !

That is good !
Go for it !
```

sudo do-release-upgrade

```

And I see you on the other side !

[INDENT][INDENT][INDENT]no step for a stepper
[/INDENT][/INDENT][/INDENT]

---

### Post by Panawe on 2014-08-17
I'm going to take a little time to make sure everything's backed-up so there may be a delay before I respond.

See you, as you say, on the other side!

---

### Post by Panawe on 2014-08-17
Hi, nope, it's falling over again at the "calculating changes" stage. Also, system seems a bit unstable and screen goes bizarre during boot up.

---

### Post by Bashing-om on 2014-08-17
Panawe; Strange, real strange .

What have you now got installed onto the system that is non-standard ?

I guess you will have to go through each and every PPA and either revert back to what is available in the ubuntu repository OR maybe go so far as to remove from the system those with no candidate ?

As the system is stable, and the package manager is in a consistent state, about all it can be. Something going on that the package manager has no handle on.

[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT]

---

### Post by Panawe on 2014-08-18
Hi,
I have GoogleEarth, which I think was loaded outside of Software Centre. I also have three Windows programs running under Wine. 
Most everything else, I think, I installed via Software Centre.

Ah, but hold on, I found one PPA box checked in Software Sources - have unchecked and going to have another go. Hold on!

---

### Post by Panawe on 2014-08-18
Fell over again when calculating the upgrade although I didn't get the "*Some third party entries in your sources.list were disabled. You can  re-enable them after the upgrade with the 'software-properties' tool or  your package manage*r" warning box before that.

Will it have to be a disk installation?

---

### Post by Ronald_Bagwell on 2014-08-18
> **Panawe said:**
> I expect this is hardly news but I had the upgrade fail during the "setting software channels" step. I get the following error messages:

   >Third party sources disabled 

  
  Some third party entries in your sources.list were disabled. You can re-enable them after the upgrade with the 'software-properties' tool or your package manager.
>> This is simply accepted and the upgrade continues

>Could not determine the upgrade 

  
 An unresolvable problem occurred while calculating the upgrade. 
  
  This can be caused by: 
  * Upgrading to a pre-release version of Ubuntu 
  * Running the current pre-release version of Ubuntu 
  * Unofficial software packages not provided by Ubuntu 
  
 If none of this applies, then please report this bug using the command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal.


>>Upgrade stops and restores 12.04

So I'm going to wait until the upgrade is fixed and install via Package Manager, unless someone can offer any suggestions to act otherwise/

:confused: I had a simlar problem. I resorted to installing Ubuntu 14.04 rather that perform an upgrade. This resulted in the loss of all files on the Ubuntu partition. I was very careful to follow the correct option which should have left all files intact. If you have any idea how I might recover the files please let me know.

Ron

---

### Post by Panawe on 2014-08-18
Sorry, I don't know enough about this business to help you.

But I'm interested in installing 14.04 into the partition currently occupied by 12.04 (sda5). I don't mind if it wipes everything in that partition but I'd rather keep Windows 7 alive for the moment (although I have the disk if need be).

Sorry I'm no use to you, I hope somebody can help you fix your problem.

---

### Post by kansasnoob on 2014-08-18
> **Ronald_Bagwell said:**
> :confused: I had a simlar problem. I resorted to installing Ubuntu 14.04 rather that perform an upgrade. This resulted in the loss of all files on the Ubuntu partition. I was very careful to follow the correct option which should have left all files intact. If you have any idea how I might recover the files please let me know.

Ron

You should start a new thread because it's a different issue, but that's probably due to this bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

You should stop using the newly installed OS immediately and only boot that machine using the live media you used to install. Then we can investigate and see if TestDisk or PhotoRec might be able to recover some data.

---

### Post by kansasnoob on 2014-08-18
> **Panawe said:**
> Sorry, I don't know enough about this business to help you.

But I'm interested in installing 14.04 into the partition currently occupied by 12.04 (sda5). I don't mind if it wipes everything in that partition but I'd rather keep Windows 7 alive for the moment (although I have the disk if need be).

Sorry I'm no use to you, I hope somebody can help you fix your problem.

You could potentially also be effected by this bug if reinstalling:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

So start by posting the output of:

```
sudo parted -l
```

That will provide some basic drive structure info so we can try to help you perform a safe reinstallation.

---

### Post by Panawe on 2014-08-18
Here it is...
```

phil@panawe:~$ sudo parted -l
[sudo] password for phil: 
Model: ATA WDC WD10EARS-22Y (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  106MB   105MB   primary   ntfs            boot
 2      106MB   467GB   467GB   primary   ntfs
 3      467GB   1000GB  533GB   extended
 5      467GB   988GB   521GB   logical   ext4
 6      988GB   1000GB  12.2GB  logical   linux-swap(v1)


Model: ATA WDC WD10EARS-22Y (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size   Type     File system  Flags
 1      1049kB  500GB   500GB  primary  ext4
 2      500GB   1000GB  500GB  primary  ntfs         boot


phil@panawe:~$ 


```

---

### Post by kansasnoob on 2014-08-18
If your 12.04 still boots also post the output of:

```
df -H
```

```
cat /etc/fstab
```

BTW the capital H is not a typo ;)

---

### Post by Panawe on 2014-08-18
Although the screen goes doolally during boot (between selecting Ubuntu and the Login screen) 12.04 seems to be working fine.
```

phil@panawe:~$ phil@panawe:~$ sudo parted -l
phil@panawe:~$: command not found
phil@panawe:~$ [sudo] password for phil: 
[sudo]: command not found
phil@panawe:~$ Model: ATA WDC WD10EARS-22Y (scsi)
bash: syntax error near unexpected token `('
phil@panawe:~$ Disk /dev/sda: 1000GB
No command 'Disk' found, did you mean:
 Command 'risk' from package 'xfrisk' (universe)
Disk: command not found
phil@panawe:~$ Sector size (logical/physical): 512B/4096B
bash: syntax error near unexpected token `('
phil@panawe:~$ Partition Table: msdos
Partition: command not found
phil@panawe:~$ 
phil@panawe:~$ Number  Start   End     Size    Type      File system     Flags
No command 'Number' found, did you mean:
 Command 'number' from package 'bsdgames' (universe)
Number: command not found
phil@panawe:~$  1      1049kB  106MB   105MB   primary   ntfs            boot
1: command not found
phil@panawe:~$  2      106MB   467GB   467GB   primary   ntfs
2: command not found
phil@panawe:~$  3      467GB   1000GB  533GB   extended
3: command not found
phil@panawe:~$  5      467GB   988GB   521GB   logical   ext4
5: command not found
phil@panawe:~$  6      988GB   1000GB  12.2GB  logical   linux-swap(v1)
bash: syntax error near unexpected token `('
phil@panawe:~$ 
phil@panawe:~$ 
phil@panawe:~$ Model: ATA WDC WD10EARS-22Y (scsi)
bash: syntax error near unexpected token `('
phil@panawe:~$ Disk /dev/sdb: 1000GB
No command 'Disk' found, did you mean:
 Command 'risk' from package 'xfrisk' (universe)
Disk: command not found
phil@panawe:~$ Sector size (logical/physical): 512B/4096B
bash: syntax error near unexpected token `('
phil@panawe:~$ Partition Table: msdos
Partition: command not found
phil@panawe:~$ 
phil@panawe:~$ Number  Start   End     Size   Type     File system  Flags
No command 'Number' found, did you mean:
 Command 'number' from package 'bsdgames' (universe)
Number: command not found
phil@panawe:~$  1      1049kB  500GB   500GB  primary  ext4
1: command not found
phil@panawe:~$  2      500GB   1000GB  500GB  primary  ntfs         boot
2: command not found
phil@panawe:~$ 
phil@panawe:~$ 
phil@panawe:~$ phil@panawe:~$ 
phil@panawe:~$: command not found
phil@panawe:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=0dc6003c-74d4-4382-9c6f-002877b280d6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=fbcadba6-5823-4484-876f-1c8df1bb7d3f none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
phil@panawe:~$ 


```

---

### Post by kansasnoob on 2014-08-18
> **Panawe said:**
> Although the screen goes doolally during boot (between selecting Ubuntu and the Login screen) 12.04 seems to be working fine.
```

phil@panawe:~$ phil@panawe:~$ sudo parted -l
phil@panawe:~$: command not found
phil@panawe:~$ [sudo] password for phil: 
[sudo]: command not found
phil@panawe:~$ **[COLOR="#FF0000"]Model: ATA WDC WD10EARS-22Y (scsi)[/COLOR]**
bash: syntax error near unexpected token `('
phil@panawe:~$ **[COLOR="#FF0000"]Disk /dev/sda: 1000GB[/COLOR]**
No command 'Disk' found, did you mean:
 Command 'risk' from package 'xfrisk' (universe)
Disk: command not found
phil@panawe:~$ **[COLOR="#FF0000"]Sector size (logical/physical): 512B/4096B[/COLOR]**
bash: syntax error near unexpected token `('
phil@panawe:~$ [COLOR="#FF0000"]Partition Table: msdos[/COLOR]
Partition: command not found
phil@panawe:~$ 
phil@panawe:~$ **[COLOR="#FF0000"]Number  Start   End     Size    Type      File system     Flags[/COLOR]**
No command 'Number' found, did you mean:
 Command 'number' from package 'bsdgames' (universe)
Number: command not found
phil@panawe:~$  1      1049kB  106MB   105MB   primary   ntfs            boot
1: command not found
phil@panawe:~$  2      106MB   467GB   467GB   primary   ntfs
2: command not found
phil@panawe:~$  3      467GB   1000GB  533GB   extended
3: command not found
phil@panawe:~$  5      467GB   988GB   521GB   logical   ext4
5: command not found
phil@panawe:~$  6      988GB   1000GB  12.2GB  logical   linux-swap(v1)
bash: syntax error near unexpected token `('
phil@panawe:~$ 
phil@panawe:~$ 
phil@panawe:~$ **[COLOR="#FF0000"]Model: ATA WDC WD10EARS-22Y (scsi)[/COLOR]**
bash: syntax error near unexpected token `('
phil@panawe:~$ Disk /dev/sdb: 1000GB
No command 'Disk' found, did you mean:
 Command 'risk' from package 'xfrisk' (universe)
Disk: command not found
phil@panawe:~$ Sector size (logical/physical): 512B/4096B
bash: syntax error near unexpected token `('
phil@panawe:~$ Partition Table: msdos
Partition: command not found
phil@panawe:~$ 
phil@panawe:~$ Number  Start   End     Size   Type     File system  Flags
No command 'Number' found, did you mean:
 Command 'number' from package 'bsdgames' (universe)
Number: command not found
phil@panawe:~$  1      1049kB  500GB   500GB  primary  ext4
1: command not found
phil@panawe:~$  2      500GB   1000GB  500GB  primary  ntfs         boot
2: command not found
phil@panawe:~$ 
phil@panawe:~$ 
phil@panawe:~$ phil@panawe:~$ 
phil@panawe:~$: command not found
phil@panawe:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=0dc6003c-74d4-4382-9c6f-002877b280d6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=fbcadba6-5823-4484-876f-1c8df1bb7d3f none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
phil@panawe:~$ 


```

Why are you running commands like those I highlighted? Are you trying to blow things up?

---

### Post by kansasnoob on 2014-08-18
You did not post the output of:

```
df -H
```

I don't need it incredibly badly but I was curious how much space is used in the Ubuntu partition. Are you sure there is nothing in the Ubuntu partition that you'd like to back up? Firefox or Thunderbird profiles? Nothing?

---

### Post by Panawe on 2014-08-18
Hi, I didn't run those commands, don't know how they got there.
```

phil@panawe:~$ df -H
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5       513G  102G  385G  21% /
udev            4.2G  4.1k  4.2G   1% /dev
tmpfs           838M  1.0M  837M   1% /run
none            5.3M     0  5.3M   0% /run/lock
none            4.2G  652k  4.2G   1% /run/shm
/dev/sdb1       493G   68G  400G  15% /media/UbuntuStore
/dev/sdb2       501G  180G  322G  36% /media/StoreWin
phil@panawe:~$ 


```

---

### Post by Panawe on 2014-08-18
All very strange, I hadn't cleared the screen from the previous command, is that it?
```

phil@panawe:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=0dc6003c-74d4-4382-9c6f-002877b280d6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=fbcadba6-5823-4484-876f-1c8df1bb7d3f none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
phil@panawe:~$ 


```

I blame copy/paste!

---

### Post by kansasnoob on 2014-08-18
> **Panawe said:**
> **[COLOR="#FF0000"]All very strange, I hadn't cleared the screen from the previous command, is that it?[/COLOR]**
```

phil@panawe:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=0dc6003c-74d4-4382-9c6f-002877b280d6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=fbcadba6-5823-4484-876f-1c8df1bb7d3f none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
phil@panawe:~$ 


```

I blame copy/paste!

Maybe because you're using a partially borked OS :confused:

It shouldn't have done any harm - just freaked me out. I'm taking some new screenshots of the installation process so the info I provide is up-to-date, but I'll be back directly.

Give some serious thought to whatever you might want to backup from that old installation. Better to take your time to think about it now instead of wishing you had afterwards.

---

### Post by Panawe on 2014-08-18
I've backed up all the stuff I want onto the second HDD (sdb) and also an external HDD. 

I'd very much prefer the installation to leave sdb alone!

---

### Post by kansasnoob on 2014-08-18
> **Panawe said:**
> I've backed up all the stuff I want onto the second HDD (sdb) and also an external HDD. 

I'd very much prefer the installation to leave sdb alone!

OK, excuse me for being anal but a common mistake I've seen made when people create a backup is backing up .mozilla (the Firefox profile) and/or .thunderbird while those apps are running. Then when those old profiles are restored they fail to work, instead just telling you they're already running ;)

Anyway you will leave everything undisturbed unless you select to do otherwise. You already seem to be fairly aware of how Ubuntu designates drives and partitions. From the output of parted -l I can see you have two identical 1TB drives. The first is shown as /dev/sda with two NTFS partitions for Win 7 and also the root and SWAP partitions for Ubuntu. The second is shown as /dev/sdb and has two data partitions, one NTFS and the other ext4.

A long time ago there was a bug around that would sometimes cause the live media to recognize the drives out of order. I think that bug was fixed long ago but I'm still always very cautious to be sure that the drives are in fact recognized as expected. When you're performing the installation if things don't look right don't proceed without asking more questions.

In your case it should be almost impossible to mistakenly choose the wrong partition to reuse because **you want to reuse only /dev/sda5** and there is no /dev/sdb5 to confuse it with. SWAP will automatically be reused with no action by you during the installation process.

But first things first. Since you're using new installation media, whether it's a live USB or live DVD, when you boot it the first time enter the [advanced boot options]("https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options") and choose Check disc for defects. That takes several minutes to complete but there's no point in proceeding with bad installation media. 

It's then probably best to try the live desktop to be sure it's going to run with your hardware, but that choice is up to you. After selecting Install Ubuntu when you get to the Installation type screen select Something else > Continue:

[ATTACH=CONFIG]255586[/ATTACH]

Note: those screenshots are taken using Lubuntu but Ubuntu is the same other than color.

After clicking on Continue it may take a few minutes for the next screen to appear:

[ATTACH=CONFIG]255587[/ATTACH]

You can see there that it displays a list of all devices - both drives and partitions - remember **[COLOR="#FF0000"]you only want to select /dev/sda5[/COLOR]**. In my screenshot I chose sda6 but **[COLOR="#FF0000"]you want sda5[/COLOR]**! With /dev/sda5 highlighted click on Change and another window will appear:

[ATTACH=CONFIG]255588[/ATTACH]

There you will want to leave the Size as it is, set Use as to Ext4, do click on Format, and set Mount point to / which indicates root. Then just click on OK and that window will close. You may be asked to confirm that change.

You can see that you could also select a different location to install grub to but the default is the MBR of /dev/sda and I think we should assume that's correct. If not then /dev/sdb must be set to boot first in BIOS so I assume you'd know how to change that if presented with a "no device found" error on first boot?

That is basically it other than answering questions/entering user info as they're presented to you after clicking on Continue. Is this clear as mud?

I recommend using the same username and password you're now using just to avoid potential permission problems with external storage devices when the installation completes.

---

### Post by Panawe on 2014-08-18
Many thanks, I understand this. Between yourself and Bashing-Om I have been the recipient of the most helpful advice. Is there any way I can buy you guys a beer?

I'll recheck that everything is backed up as it should be (note taken of what you said about Thunderbird & Firefox) and jump in the deep deep tomorrow morning, GMT.

---

### Post by Panawe on 2014-08-18
Installed 14.04 successfully! Surprisingly painless so far but no doubt there'll be all kinds of glitches over the weeks to come.

I owe you guys a great debt.;)

Somewhere here there's a button I press to mark this as solved.

---

### Post by Bashing-om on 2014-08-18
Panawe; Hey ;

I see you found the solved button !

For clarification; the solution is the nuclear one ?
A clean fresh install of release 14.04 ?

[INDENT][INDENT]there is always that one
[/INDENT][/INDENT]

---

### Post by Panawe on 2014-08-19
Yes, Bashing-Om, I followed the instructions of kansasnoob to the letter, including the advice about closing Thunderbird & Mozilla before backing them up. Then I just did as he said, installed into the partition occupied by 12.04. Went like a dream.

I owe you a beer :)

PS While reinstalling my old stuff I came across a problem trying to reinstall Gnome Encfs Manager and I noticed while reading the bumph that it uses a PPA repository. That programme was always running while we were trying to clear out the PPA repositories in 12.04!

---

### Post by kansasnoob on 2014-08-19
> **Bashing-om said:**
> Panawe; Hey ;

I see you found the solved button !

For clarification; the solution is the nuclear one ?
A clean fresh install of release 14.04 ?

[INDENT][INDENT]there is always that one
[/INDENT][/INDENT]

In the real world I almost always use the nuclear option :lolflag:

I currently maintain about 60 individual PC's spread out over a 40 mile radius and I've found that I no more than get one little thing fixed, then a day or two later I get a call that something else went haywire. So now I almost always just have people drop their PC off, give them a loaner, and then give their PC the "full meal deal" :biggrin:

---

