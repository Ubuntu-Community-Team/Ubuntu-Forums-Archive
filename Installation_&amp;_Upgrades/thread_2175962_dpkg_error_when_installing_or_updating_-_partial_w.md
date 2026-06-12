---
title: "dpkg error when installing or updating - partial workaround at least"
date: 2013-09-22
forum: Installation &amp; Upgrades
---

### Post by Theshank on 2013-09-22
I've seen posts of similar troubles, but none of the solutions there have worked for me, But if you read down to the bottom I did find a somewhat workaround while typing this.

Whenever i try to install new software or use the update manager. I get the following: (truncated by me)

  	 	 	 	   (Reading database ... 75%% 
 (Reading database ... 80%% 
 (Reading database ... 85%%dpkg: unrecoverable fatal error, aborting: 
  reading files list for package 'gnome-panel': Input/output error 
 Error in function:  
 SystemError: E:Sub-process /usr/bin/dpkg returned an error code (2) 

Tried putting an old /var/lib/dpkg/status from /var/backups. Even the oldest made no difference. Seems that's not the problem, so I put the original back.

  	 	 	 	   

tried:
 

 h@h-System-Product-Name:/var/backups$ sudo dpkg --configure -a 
 [sudo] password for h:  
 

 no output at all from that. Just a new prompt.
 So I tried renaming the package file, to at least get a -different- error.
 This on the assumption the “files list” is in there. Wrong.

 

 

 h@h-System-Product-Name:/var/cache/apt/archives$ sudo mv gnome-panel_1%3a3.4.1-0ubuntu1.2_amd64.deb gpaneltemp 
 [sudo] password for h:  
 

 Then tried this one:
 

 h@h-System-Product-Name:/var/cache/apt/archives$ sudo apt-get update 
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg 
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                                    
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                                       
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg                
 Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg [198 B]    
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                                                   
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release                    
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources                                                             
 Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release [49.6 kB] 
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources            
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources              
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources 
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages 
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages       
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages         
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages       
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages              
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages        
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages          
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages        
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex           
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex     
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex     
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex       
 Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                       
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en       
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en 
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main amd64 Packages 
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en 
 Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                           
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted amd64 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe amd64 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse amd64 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources 
 Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main amd64 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted amd64 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe amd64 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse amd64 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex 
 Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources [3,452 B] 
 Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources [14 B] 
 Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources [35.5 kB] 
 Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages 
 Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages 
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex 
 Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources [5,311 B] 
 Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main amd64 Packages [2,818 B] 
 Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted amd64 Packages [14 B] 
 Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe amd64 Packages [36.5 kB] 
 Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse amd64 Packages [5,206 B] 
 Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages [2,825 B] 
 Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages [14 B] 
 Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages [36.3 kB] 
 Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages [5,178 B] 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex          
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex    
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex    
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex      
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                      
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en       
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en       
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en         
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en     
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en 
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US 
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en 
 Fetched 183 kB in 1s (95.1 kB/s) 
 Reading package lists... Done 
 

 -I- don't see anything abnormal there.
 Tried:
 

 h@h-System-Product-Name:/var/cache/apt/archives$ sudo apt-get upgrade 
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 The following packages will be upgraded: 
   apt apt-transport-https apt-utils apt-xapian-index firefox firefox-globalmenu firefox-locale-en flashplugin-installer gir1.2-polkit-1.0 hplip hplip-data 
   isc-dhcp-client isc-dhcp-common jockey-common jockey-gtk language-selector-common language-selector-gnome libapt-inst1.4 libapt-pkg4.12 libcurl3 
   libcurl3-gnutls libcurl3-nss libhpmud0 libpolkit-agent-1-0 libpolkit-backend-1-0 libpolkit-gobject-1-0 libsane-hpaio libsmbclient libsyncdaemon-1.0-1 
   libwbclient0 libx11-6 libx11-data libx11-xcb1 policykit-1 printer-driver-hpcups printer-driver-hpijs printer-driver-postscript-hp python-httplib2 
   python-software-properties python-ubuntuone-client rtkit samba-common samba-common-bin sessioninstaller smbclient software-properties-common 
   software-properties-gtk tzdata tzdata-java ubuntu-system-service ubuntuone-client usb-creator-common usb-creator-gtk 
 53 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
 Need to get 0 B/66.8 MB of archives. 
 After this operation, 1,674 kB of additional disk space will be used. 
 Do you want to continue [Y/n]? y 
 Extracting templates from packages: 100% 
 Preconfiguring packages ... 
 (Reading database ... 85%dpkg: unrecoverable fatal error, aborting: 
  reading files list for package 'gnome-panel': Input/output error 
 E: Sub-process /usr/bin/dpkg returned an error code (2) 
 

 Gee, the above is familiar.
 

 h@h-System-Product-Name:/var/cache/apt/archives$ sudo apt-get install 
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 The following packages were automatically installed and are no longer required: 
   linux-headers-3.2.0-29 linux-headers-3.2.0-29-generic nvidia-settings 
 Use 'apt-get autoremove' to remove them. 
 0 upgraded, 0 newly installed, 0 to remove and 53 not upgraded. 
 h@h-System-Product-Name:/var/cache/apt/archives$ sudo apt-get -f install 
 Reading package lists... Done 
 Building dependency tree         
 Reading state information... Done 
 The following packages were automatically installed and are no longer required: 
   linux-headers-3.2.0-29 linux-headers-3.2.0-29-generic nvidia-settings 
 Use 'apt-get autoremove' to remove them. 
 0 upgraded, 0 newly installed, 0 to remove and 53 not upgraded. 
 

 tried what it suggested just for kicks.
 

 h@h-System-Product-Name:/var/cache/apt/archives$ sudo apt-get autoremove 
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 The following packages will be REMOVED: 
   linux-headers-3.2.0-29 linux-headers-3.2.0-29-generic nvidia-settings 
 0 upgraded, 0 newly installed, 3 to remove and 53 not upgraded. 
 After this operation, 67.5 MB disk space will be freed. 
 Do you want to continue [Y/n]? y 
 (Reading database ... 85%dpkg: unrecoverable fatal error, aborting: 
  reading files list for package 'gnome-panel': Input/output error 
 E: Sub-process /usr/bin/dpkg returned an error code (2) 
 

 I think I could type that error message from memory by now.

I found the list file for gnome-panel and renamed it, so dpkg or apt can't find it.

h@h-System-Product-Name:/var/lib/dpkg/info$ sudo mv gnome-panel.list gplisttemp

Now software installs and updates at least work. dpkg warns about the missing list file, but goes on.
Any suggestions to get it to update gnome-panel and quit complaining?

---

### Post by TheFu on 2013-09-22
Seems the gnome-panel was corrupted somehow - could be anything - download, out of storage, cable error, bad disk sector .. anything.  The package could have been being updated when you happened to download it. Different update methods can cause that.
I'd do a 
**sudo apt-get --reinstall install gnome-panel** to see if that helps.  

Sometimes with APT, I find that waiting a few days and trying again solves the problem as dependent packages are corrected.

---

