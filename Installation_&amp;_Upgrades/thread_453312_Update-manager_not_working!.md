---
title: "Update-manager not working!"
date: 2007-05-24
forum: Installation &amp; Upgrades
---

### Post by jefh262 on 2007-05-24
I am at a college which has a wireless internet and to log onto the internet (firefox) it pops up with a box which prompts me to 'enter username and password for "" at http://serverintranet' into which i enter computing\myname as username and a password. On my internet settings i have set proxy: 'proxy2' and port '8080'. However, I am not sure how to get this for update manager as it just doesn't want to find the internet. I use ubuntu edgy and am fairly new to ubuntu.
:)

---

### Post by joriad on 2007-05-24
It doesn't appear to be an update manager issue. You would probably have to talk to the schools network administrator for the settings.

---

### Post by jefh262 on 2007-05-24
firefox works. What i need is to be able to connect on start up though.

---

### Post by joriad on 2007-05-24
Ok so you do have an internet connection but cannot get updates. Did you try sudo apt-get update in terminal, Applications > Accessories > Terminal? You can also use System > Administration > Synaptic Package Manager. If you have problems still post the results from terminal here. Also in synaptic package manager try a different server, at times there have been problems with connectivity.

---

### Post by jefh262 on 2007-05-24
jefh@jefh-desktop:~$ sudo apt-get update
Password:
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg
Ign [http://debs.michaelbiebl.de](http://debs.michaelbiebl.de) edgy Release.gpg
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US            
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy Release.gpg  
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/main Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/restricted Translation-en_US
Ign [http://debs.michaelbiebl.de](http://debs.michaelbiebl.de) edgy/main Translation-en_US                    
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg                   
Ign [http://cle.linux.org.tw](http://cle.linux.org.tw) i386/ Release.gpg                                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US        
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_US                    
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy Release.gpg                                   
Ign [http://debs.michaelbiebl.de](http://debs.michaelbiebl.de) edgy Release                                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                           
Ign [http://debs.michaelbiebl.de](http://debs.michaelbiebl.de) edgy/main Packages                             
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release                                   
Ign [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Ign [http://dl.google.com](http://dl.google.com) stable/non-free Translation-en_US                     
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Translation-en_US        
Ign [http://cle.linux.org.tw](http://cle.linux.org.tw) i386/ Translation-en_US                            
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) edgy/ Release.gpg                                    
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) edgy/ Translation-en_US                              
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy/main Translation-en_US                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_US                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Err [http://debs.michaelbiebl.de](http://debs.michaelbiebl.de) edgy/main Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages
Ign [http://dl.google.com](http://dl.google.com) stable Release
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release
Ign [http://cle.linux.org.tw](http://cle.linux.org.tw) i386/ Release
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) edgy/ Release
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources                      
Err [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages                             
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Ign [http://dl.google.com](http://dl.google.com) stable/non-free Packages                              
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages                 
Ign [http://cle.linux.org.tw](http://cle.linux.org.tw) i386/ Packages                                     
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) edgy/ Packages                                       
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy/main Packages                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US      
Err [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages                 
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://cle.linux.org.tw](http://cle.linux.org.tw) i386/ Packages                                     
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://ftp.osuosl.org](http://ftp.osuosl.org) edgy/ Packages                                       
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy/main Packages                                 
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://dl.google.com](http://dl.google.com) stable/non-free Packages                              
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Translation-en_US
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Translation-en_US
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://debs.michaelbiebl.de/dists/edgy/main/binary-i386/Packages.gz](http://debs.michaelbiebl.de/dists/edgy/main/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/Packages.gz](http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://dl.google.com/linux/deb/dists/stable/non-free/binary-i386/Packages.gz](http://dl.google.com/linux/deb/dists/stable/non-free/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.canonical.com/ubuntu/dists/edgy-commercial/main/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/edgy-commercial/main/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://cle.linux.org.tw/candyz/Ubuntu/edgy/i386/Packages.gz](http://cle.linux.org.tw/candyz/Ubuntu/edgy/i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://ftp.osuosl.org/pub/pculture.org/democracy/linux/repositories/ubuntu/edgy/Packages.gz](http://ftp.osuosl.org/pub/pculture.org/democracy/linux/repositories/ubuntu/edgy/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://wine.lowvoice.nl/apt/dists/edgy/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/edgy/main/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-backports/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/main/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
jefh@jefh-desktop:~$

---

### Post by joriad on 2007-05-24
> **joriad said:**
> Ok so you do have an internet connection but cannot get updates. Did you try sudo apt-get update in terminal, Applications > Accessories > Terminal? You can also use System > Administration > Synaptic Package Manager. If you have problems still post the results from terminal here. Also in synaptic package manager try a different server, at times there have been problems with connectivity.

Sorry just waking up, brain not functioning yet

Applications > Accessories > Terminal type in
```
sudo apt-get update
```
enter password, then if that works type in 
```
 sudo apt-get upgrade
```

if you have a problem and these don't work submit the results of terminal to this thread.

---

### Post by jefh262 on 2007-05-24
done that, results are posted above...

---

### Post by joriad on 2007-05-24
Your problem is beyond my scope of understanding, however I did find this thread that probably will give you some answers. Sorry I could not be of further help.
[http://ubuntuforums.org/showthread.php?t=96802](http://ubuntuforums.org/showthread.php?t=96802)

---

### Post by jefh262 on 2007-05-24
OK, thanks

---

### Post by jefh262 on 2007-05-24
still does not work...

---

### Post by sschaper on 2007-05-24
I am having the same problem. It is as if Ubuntu changed the authentication or pathways, and we can't update anything. It just fails to authenticate.

---

### Post by jorno on 2007-09-10
I don't know if anyone still has this problem, but I found my solution in another post.

The steps mentioned here earlier are good and all, BUT if those of  you who's got this problem is in a Windows environment with a Microsoft ISA Proxy that need authentication, this is the solution that worked for me:

You need to install NTLMAPS.

[http://packages.ubuntu.com/feisty/web/ntlmaps](http://packages.ubuntu.com/feisty/web/ntlmaps)
* Go there, and download, either from within Firefox (if you manage to get Proxy working with Firefox - I did, but not apt-get or Synaptics or anything else).
* Download the package for ntlmaps (this is for Ubuntu Feisty)
* Start a terminal, find your downloaded package, and type:
*sudo dpkg -i ntlmaps_0.9.9.0.1-6_all.deb*
This should guide you trough the installation of the package...

BUT, my problems didn't stop there!
After, I had to edit /etc/ntlmaps/server.cfg manually.
( *sudo vim /etc /ntlmaps/server.cfg* )
Then I saw that the config-file was formatted with DOS (not UNIX), so I had to tell vim to convert it to UNIX-format. Do this in vim:
*:set fileformat=unix*
*:wq*
This should convert the file, and save it.
I also had to change some of the options:
Under the [CLIENT_HEADER] section, I had to comment out the first Accept and User-Agent part (Windows 98), and then uncomment the next part (Windows 2000 emulation).
Then I filled in "NT_HOSTNAME" (remembered what PC number this workstation had in Windows), and "NT_DOMAIN").

After those changes, restart ntlmaps:
*/etc/init.d/ntlmaps restart*

And point all your proxy-settings to: [http://127.0.0.1:5865](http://127.0.0.1:5865)

Make a file: */etc/apt/apt.conf*
Acquire::http::Proxy "http://127.0.0.1:5865";

And then try "*apt-get update*".

You could also insert this into:
System -> Preferences -> Network Proxy

And in Synaptics:
System -> Administration -> Synaptics -> Settings -> Preferences -> Network:
Manual proxy configuration:

127.0.0.1 port 5865 (no authentication)


This should do the trick! It did for me.. Please ask if there is something not clear yet, or if I should correct any of this. (Sorry, English is not my native tongue).

---

