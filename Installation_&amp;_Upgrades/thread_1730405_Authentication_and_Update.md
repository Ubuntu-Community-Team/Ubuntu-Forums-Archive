---
title: "Authentication and Update"
date: 2011-04-16
forum: Installation &amp; Upgrades
---

### Post by divinenibru on 2011-04-16
Hey Ubuntuforums,

I can't install any new programs on my laptop because I keep having trouble with authentication and sudo apt-get update isn't working either ... so I'm confused as to what I should do or what the problem is.

Any ideas or suggestions?

Thanks in advance

---

### Post by divinenibru on 2011-04-16
nibru@TheAltar:~$ sudo apt-get update
[sudo] password for nibru: 
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                                                                                                                                                                                                     
  Could not connect to 196.41.132.28:8080 (196.41.132.28). - connect (110: Connection timed out)
Err [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release.gpg                                                                                                                                                                                                                
  Could not connect to 196.41.132.28:8080 (196.41.132.28). - connect (110: Connection timed out)
Err [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) lucid/main Translation-en_US                                                                                                                                                                                             
  Unable to connect to 196.41.132.28:8080:
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                                                                                                                                                                                                            
  Could not connect to 196.41.132.28:8080 (196.41.132.28). - connect (110: Connection timed out)
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US                                                                                                                                                                   
  Unable to connect to 196.41.132.28:8080:
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US                                                                                                                                                             
  Unable to connect to 196.41.132.28:8080:
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US                                                                                                                                                               
  Unable to connect to 196.41.132.28:8080:
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US                                                                                                                                                             
  Unable to connect to 196.41.132.28:8080:
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports Release.gpg                                                                                                                                                                            
  Unable to connect to 196.41.132.28:8080:
Err [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                                                                                                                                                                                      
  Could not connect to 196.41.132.28:8080 (196.41.132.28). - connect (110: Connection timed out)
Err [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US                                                                                                                                                                
  Unable to connect to 196.41.132.28:8080:
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US                                                                                                                                                            
  Unable to connect to 196.41.132.28:8080:
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US                                                                                                                                                      
  Unable to connect to 196.41.132.28:8080:
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US                                                                                                                                                        
  Unable to connect to 196.41.132.28:8080:
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US                                                                                                                                                      
  Unable to connect to 196.41.132.28:8080:
Err [http://download.virtualbox.org](http://download.virtualbox.org) lucid Release.gpg                                                                                                                                                                                    
  Could not connect to 196.41.132.28:8080 (196.41.132.28). - connect (110: Connection timed out)
Err [http://download.virtualbox.org/virtualbox/debian/](http://download.virtualbox.org/virtualbox/debian/) lucid/contrib Translation-en_US                                                                                                                                                   
  Unable to connect to 196.41.132.28:8080:
Err [http://dl.google.com](http://dl.google.com) stable Release.gpg                                                                                                                                                                                             
  Could not connect to 196.41.132.28:8080 (196.41.132.28). - connect (110: Connection timed out)
Err [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_US                                                                                                                                                                
  Unable to connect to 196.41.132.28:8080:
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/main Translation-en_US                                                                                                                                                         
  Unable to connect to 196.41.132.28:8080:
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/restricted Translation-en_US
  Unable to connect to 196.41.132.28:8080:
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/universe Translation-en_US
  Unable to connect to 196.41.132.28:8080:
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/multiverse Translation-en_US
  Unable to connect to 196.41.132.28:8080:
Ign [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release  
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid Release  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg  
  Could not connect to 196.41.132.28:8080 (196.41.132.28). - connect (110: Connection timed out)
Err [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Translation-en_US
  Unable to connect to 196.41.132.28:8080:
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports Release
Ign [http://download.virtualbox.org](http://download.virtualbox.org) lucid Release
Ign [http://linux.dropbox.com](http://linux.dropbox.com) lucid/main Packages
Ign [http://dl.google.com](http://dl.google.com) stable Release
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Ign [http://download.virtualbox.org](http://download.virtualbox.org) lucid/contrib Packages
Ign [http://linux.dropbox.com](http://linux.dropbox.com) lucid/main Packages
Ign [http://dl.google.com](http://dl.google.com) stable/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Ign [http://download.virtualbox.org](http://download.virtualbox.org) lucid/contrib Packages
Err [http://linux.dropbox.com](http://linux.dropbox.com) lucid/main Packages
  Unable to connect to 196.41.132.28:8080:
Ign [http://dl.google.com](http://dl.google.com) stable/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/restricted Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/multiverse Packages
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages
  Unable to connect to 196.41.132.28:8080:
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
  Unable to connect to 196.41.132.28:8080:
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
  Unable to connect to 196.41.132.28:8080:
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
  Unable to connect to 196.41.132.28:8080:
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources
Err [http://download.virtualbox.org](http://download.virtualbox.org) lucid/contrib Packages
  Unable to connect to 196.41.132.28:8080:
Err [http://dl.google.com](http://dl.google.com) stable/main Packages
  Unable to connect to 196.41.132.28:8080:
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
  Unable to connect to 196.41.132.28:8080:
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
  Unable to connect to 196.41.132.28:8080:
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
  Unable to connect to 196.41.132.28:8080:
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
  Unable to connect to 196.41.132.28:8080:
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
  Unable to connect to 196.41.132.28:8080:
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
  Unable to connect to 196.41.132.28:8080:
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
  Unable to connect to 196.41.132.28:8080:
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
  Unable to connect to 196.41.132.28:8080:
Err [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages
  Unable to connect to 196.41.132.28:8080:
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
  Unable to connect to 196.41.132.28:8080:
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
  Unable to connect to 196.41.132.28:8080:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages 
  Unable to connect to 196.41.132.28:8080:
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/main Packages
  Unable to connect to 196.41.132.28:8080:
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/restricted Packages
  Unable to connect to 196.41.132.28:8080:
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/universe Packages
  Unable to connect to 196.41.132.28:8080:
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/multiverse Packages
  Unable to connect to 196.41.132.28:8080:
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
  Unable to connect to 196.41.132.28:8080:
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
  Unable to connect to 196.41.132.28:8080:
Err [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources
  Unable to connect to 196.41.132.28:8080:
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Could not connect to 196.41.132.28:8080 (196.41.132.28). - connect (110: Connection timed out)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2)  Unable to connect to 196.41.132.28:8080:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2)  Unable to connect to 196.41.132.28:8080:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2)  Unable to connect to 196.41.132.28:8080:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to 196.41.132.28:8080:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/Release.gpg)  Unable to connect to 196.41.132.28:8080:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/main/i18n/Translation-en_US.bz2)  Unable to connect to 196.41.132.28:8080:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/restricted/i18n/Translation-en_US.bz2)  Unable to connect to 196.41.132.28:8080:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/universe/i18n/Translation-en_US.bz2)  Unable to connect to 196.41.132.28:8080:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to 196.41.132.28:8080:

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg](http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg)  Could not connect to 196.41.132.28:8080 (196.41.132.28). - connect (110: Connection timed out)

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/lucid/partner/i18n/Translation-en_US.bz2)  Unable to connect to 196.41.132.28:8080:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg)  Could not connect to 196.41.132.28:8080 (196.41.132.28). - connect (110: Connection timed out)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2)  Unable to connect to 196.41.132.28:8080:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2)  Unable to connect to 196.41.132.28:8080:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2)  Unable to connect to 196.41.132.28:8080:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to 196.41.132.28:8080:

W: Failed to fetch [http://download.virtualbox.org/virtualbox/debian/dists/lucid/Release.gpg](http://download.virtualbox.org/virtualbox/debian/dists/lucid/Release.gpg)  Could not connect to 196.41.132.28:8080 (196.41.132.28). - connect (110: Connection timed out)

W: Failed to fetch [http://download.virtualbox.org/virtualbox/debian/dists/lucid/contrib/i18n/Translation-en_US.bz2](http://download.virtualbox.org/virtualbox/debian/dists/lucid/contrib/i18n/Translation-en_US.bz2)  Unable to connect to 196.41.132.28:8080:

W: Failed to fetch [http://linux.dropbox.com/ubuntu/dists/lucid/Release.gpg](http://linux.dropbox.com/ubuntu/dists/lucid/Release.gpg)  Could not connect to 196.41.132.28:8080 (196.41.132.28). - connect (110: Connection timed out)

W: Failed to fetch [http://linux.dropbox.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2](http://linux.dropbox.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2)  Unable to connect to 196.41.132.28:8080:

W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg](http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg)  Could not connect to 196.41.132.28:8080 (196.41.132.28). - connect (110: Connection timed out)

W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/main/i18n/Translation-en_US.bz2](http://dl.google.com/linux/chrome/deb/dists/stable/main/i18n/Translation-en_US.bz2)  Unable to connect to 196.41.132.28:8080:

W: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/lucid/Release.gpg](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/lucid/Release.gpg)  Could not connect to 196.41.132.28:8080 (196.41.132.28). - connect (110: Connection timed out)

W: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2)  Unable to connect to 196.41.132.28:8080:

W: Failed to fetch [http://linux.dropbox.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://linux.dropbox.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  Unable to connect to 196.41.132.28:8080:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  Unable to connect to 196.41.132.28:8080:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz)  Unable to connect to 196.41.132.28:8080:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz)  Unable to connect to 196.41.132.28:8080:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz)  Unable to connect to 196.41.132.28:8080:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz)  Unable to connect to 196.41.132.28:8080:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz)  Unable to connect to 196.41.132.28:8080:

W: Failed to fetch [http://download.virtualbox.org/virtualbox/debian/dists/lucid/contrib/binary-i386/Packages.gz](http://download.virtualbox.org/virtualbox/debian/dists/lucid/contrib/binary-i386/Packages.gz)  Unable to connect to 196.41.132.28:8080:

W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/main/binary-i386/Packages.gz](http://dl.google.com/linux/chrome/deb/dists/stable/main/binary-i386/Packages.gz)  Unable to connect to 196.41.132.28:8080:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz)  Unable to connect to 196.41.132.28:8080:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz)  Unable to connect to 196.41.132.28:8080:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/main/binary-i386/Packages.gz)  Unable to connect to 196.41.132.28:8080:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/restricted/binary-i386/Packages.gz)  Unable to connect to 196.41.132.28:8080:

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-i386/Packages.gz)  Unable to connect to 196.41.132.28:8080:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.gz)  Unable to connect to 196.41.132.28:8080:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.gz)  Unable to connect to 196.41.132.28:8080:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.gz)  Unable to connect to 196.41.132.28:8080:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz)  Unable to connect to 196.41.132.28:8080:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-i386/Packages.gz)  Unable to connect to 196.41.132.28:8080:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.gz)  Unable to connect to 196.41.132.28:8080:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.gz)  Unable to connect to 196.41.132.28:8080:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/universe/binary-i386/Packages.gz)  Unable to connect to 196.41.132.28:8080:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/multiverse/binary-i386/Packages.gz)  Unable to connect to 196.41.132.28:8080:

W: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  Unable to connect to 196.41.132.28:8080:

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/partner/source/Sources.gz](http://archive.canonical.com/ubuntu/dists/lucid/partner/source/Sources.gz)  Unable to connect to 196.41.132.28:8080:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.gz)  Unable to connect to 196.41.132.28:8080:

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by varunendra on 2011-04-16
Clearly, you are unable to connect to repository servers (Unable to connect to 196.41.132.28:8080)

Are you connected to Internet at all? If yes, are you able to browse to the failing links manually? For example, I am able to open [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) page (associated with the "Err" lines in your above stated output) from here at my place.

My first guess is that either you are not connected to Internet, or there is some DNS resolution problem.

If you are sure you are connected, try changing the Download server in the repositories.
(System > Administration > Synaptic Package Manager > Settings > Repositories > Ubunt Software tab (first default tab) > Download server)

---

### Post by divinenibru on 2011-04-16
I have normal internet connection, and I can access the failed links through my browser. It downloads a sources.tz file

I tried changing the Download server using the Download Server -> Select Best server, but that didn't seem to fix the problem. The apt-get update is still having trouble connecting to the repositories and I can't seem to install any new programs.

---

### Post by varunendra on 2011-04-18
> **divinenibru said:**
> I have normal internet connection, and I can access the failed links through my browser. It downloads a sources.tz file

I tried changing the Download server using the Download Server -> Select Best server, but that didn't seem to fix the problem. The apt-get update is still having trouble connecting to the repositories and I can't seem to install any new programs.

The connection timeout message suggests a slow connection or DNS problem. This also happens to me sometimes when my internet connection is slow or network is too busy, but retrying a couple of times solves the problem for me.

Did you try updating via GUI (Synaptic > Reload) and/or selecting a local server for your location? For example, I've to switch many times between the main server and 'Server for India' when having trouble with some particular package.

But anyway, failing of all the packages at once while being able to browse to them manually doesn't make any sense to me. I'm clueless on this at the moment.

---

