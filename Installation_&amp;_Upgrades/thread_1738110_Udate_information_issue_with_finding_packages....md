---
title: "Udate information issue with finding packages..."
date: 2011-04-24
forum: Installation &amp; Upgrades
---

### Post by aperture123 on 2011-04-24
Hello everybody...

  I'm using lucid (10.04) and recently I went into the hosts file in /etc and edited it, adding the following lines:

```

188.165.56.119 patchpc.ipsueu.segaonline.jp
188.165.56.119 loginpc.ipsueu.segaonline.jp

188.165.56.119 patchpc.ipsu.segaonline.jp
188.165.56.119 loginpc.ipsu.segaonline.jp

```After this, a notification icon popped up saying their was an issue with updating. This happened after launching the online wine version of Phantasy Star Universe AOTI. I seriously doubt that when launching the game, it caused my issue but....eh, well here's the terminal output of that.

```

laptop:~/.wine/dosdevices/c:/SEGA/PHANTASY STAR UNIVERSE Illuminus$ fixme:win:EnumDisplayDevicesW ((null),0,0x10bf830,0x00000000), stub!
fixme:imm:ImmDisableIME (0): stub
fixme:imm:ImmReleaseContext (0x30076, 0x13cbd0): stub
fixme:imm:ImeHandleNotify WM_IME_NOTIFY:IMN_SETCOMPOSITIONWINDOW
fixme:imm:ImmGetOpenStatus (0x13cbd0): semi-stub
err:d3d:context_create wglSwapIntervalEXT failed to set swap interval 1 for context 0x151268, last error 0x591
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
err:d3d:context_create wglSwapIntervalEXT failed to set swap interval 1 for context 0x151118, last error 0x591
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats

```Anyways, I had to force quit the application, giving this:

```

XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 104 requests (104 known processed) with 0 events remaining.

```The real issue wasn't that (although it is annoying I can't connect). Instead, the issue is NOW when I go to install updates, half of which are ignored, and the error still pops up. Here's a list of all of them with hits, and also is my sources attached...

update:
```

laptop:~/.wine/dosdevices/c:/SEGA/PHANTASY STAR UNIVERSE Illuminus$ sudo apt-get update
Hit http://linux.dropbox.com lucid Release.gpg
Ign http://linux.dropbox.com/ubuntu/ lucid/main Translation-en_US                                                            
Ign http://apt.boxee.tv lucid Release.gpg                                                                                    
Hit http://linux.dropbox.com lucid Release                                                                                   
Hit http://archive.canonical.com lucid Release.gpg                                                                           
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US                                                     
Hit http://archive.canonical.com lucid Release.gpg                                                                           
Hit http://apt.wxwidgets.org lucid-wx Release.gpg                                                                            
Ign http://apt.wxwidgets.org/ lucid-wx/main Translation-en_US                                                                
Hit http://security.ubuntu.com lucid-security Release.gpg                                                                    
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US                                                 
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US                                           
Ign http://apt.boxee.tv/ lucid/main Translation-en_US                                                                        
Hit http://ppa.launchpad.net lucid Release.gpg                                                                               
Ign http://ppa.launchpad.net/c-korn/ppa/ubuntu/ lucid/main Translation-en_US                                                 
Hit http://ppa.launchpad.net lucid Release.gpg                                                                               
Hit http://linux.dropbox.com lucid/main Packages                                                                             
Hit http://us.archive.ubuntu.com lucid Release.gpg                                                                           
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US                                                        
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US                                      
Ign http://archive.canonical.com/ lucid/partner Translation-en_US                                                            
Ign http://apt.boxee.tv lucid Release                                                                                        
Hit http://archive.canonical.com lucid Release                                                                   
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US                                             
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US                                           
Hit http://apt.wxwidgets.org lucid-wx Release                                                                    
Hit http://security.ubuntu.com lucid-security Release                                                                        
Ign http://ppa.launchpad.net/gregory-hainaut/pcsx2.official.ppa/ubuntu/ lucid/main Translation-en_US                         
Ign http://ppa.launchpad.net lucid Release.gpg                                                                               
Ign http://ppa.launchpad.net/https/ppa/ubuntu/ lucid/main Translation-en_US                                                  
Hit http://ppa.launchpad.net lucid Release.gpg                                                                               
Ign http://ppa.launchpad.net/mars-core/ppa/ubuntu/ lucid/main Translation-en_US                                  
Hit http://ppa.launchpad.net lucid Release.gpg                                                                   
Ign http://ppa.launchpad.net/murrine-daily/ppa/ubuntu/ lucid/main Translation-en_US                              
Hit http://ppa.launchpad.net lucid Release.gpg                                                                               
Ign http://ppa.launchpad.net/sunab/kdenlive-release/ubuntu/ lucid/main Translation-en_US                                     
Hit http://ppa.launchpad.net lucid Release.gpg                                                                               
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US                                        
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US                                      
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg                                                       
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US                                    
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US                              
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US                                            
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US                                          
Hit http://apt.boxee.tv lucid/main Packages                                                                      
Hit http://archive.canonical.com lucid Release                                                                   
Hit http://us.archive.ubuntu.com lucid-backports Release.gpg                                                                 
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-backports/main Translation-en_US                                              
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-backports/restricted Translation-en_US                                        
Hit http://apt.wxwidgets.org lucid-wx/main Packages                                                                          
Hit http://security.ubuntu.com lucid-security/main Packages                                                      
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ lucid/main Translation-en_US          
Hit http://ppa.launchpad.net lucid Release                                                 
Hit http://ppa.launchpad.net lucid Release                                                                                   
Ign http://ppa.launchpad.net lucid Release                                                                                   
Hit http://ppa.launchpad.net lucid Release                                                                                   
Hit http://ppa.launchpad.net lucid Release                                                                                   
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-backports/universe Translation-en_US                                          
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-backports/multiverse Translation-en_US                            
Hit http://us.archive.ubuntu.com lucid Release                                             
Hit http://us.archive.ubuntu.com lucid-updates Release                                                                       
Hit http://archive.canonical.com lucid/partner Packages                                                                      
Hit http://archive.canonical.com lucid/partner Sources                                                                       
Hit http://apt.wxwidgets.org lucid-wx/main Sources                                                                           
Hit http://security.ubuntu.com lucid-security/restricted Packages                                                            
Hit http://security.ubuntu.com lucid-security/main Sources                                 
Hit http://security.ubuntu.com lucid-security/restricted Sources     
Hit http://security.ubuntu.com lucid-security/universe Packages                            
Hit http://security.ubuntu.com lucid-security/universe Sources                             
Hit http://security.ubuntu.com lucid-security/multiverse Packages                          
Hit http://ppa.launchpad.net lucid Release                                                 
Hit http://us.archive.ubuntu.com lucid-backports Release                                                         
Hit http://archive.canonical.com lucid/partner Packages                                    
Hit http://security.ubuntu.com lucid-security/multiverse Sources                           
Hit http://ppa.launchpad.net lucid Release                           
Hit http://ppa.launchpad.net lucid/main Packages                     
Ign http://ppa.launchpad.net lucid/main Packages                     
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://us.archive.ubuntu.com lucid/universe Sources
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://ppa.launchpad.net lucid/main Packages
Ign http://ppa.launchpad.net lucid/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Err http://ppa.launchpad.net lucid/main Packages
  404  Not Found
Hit http://us.archive.ubuntu.com lucid-backports/main Packages
Hit http://us.archive.ubuntu.com lucid-backports/restricted Packages
Hit http://us.archive.ubuntu.com lucid-backports/universe Packages
Hit http://us.archive.ubuntu.com lucid-backports/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-backports/main Sources
Hit http://us.archive.ubuntu.com lucid-backports/restricted Sources
Hit http://us.archive.ubuntu.com lucid-backports/universe Sources
Hit http://us.archive.ubuntu.com lucid-backports/multiverse Sources
W: Failed to fetch http://ppa.launchpad.net/https/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```sources.list
```

# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
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
deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
deb http://archive.canonical.com/ lucid partner
    # wxWidgets/wxPython repository at apt.wxwidgets.org
deb http://apt.wxwidgets.org/ lucid-wx main
deb-src http://apt.wxwidgets.org/ lucid-wx main

```
Anybody know what could be causing the issue. :( No updates doesn't seem like a good use of an operating system in terms of safety and usability....

---

