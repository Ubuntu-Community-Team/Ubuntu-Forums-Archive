---
title: "Not able to Install LAMP Please please help"
date: 2011-07-28
forum: Installation &amp; Upgrades
---

### Post by poornima.biradar on 2011-07-28
hi,

I am new to ubuntu. Even i am not able to install LAMP. i tried all the option posted in this forum. nothing is working :sad:. tasksel is already installed. and i tried installing from tasksel it gives me
> tasksel: aptitude failed (100)and as suggested in one of the thread to update apt-get first. so i ran 
> sudo apt-get update                      even its giving me error, following is the log... please please help 


> ubuntu@ubuntu-desktop:~$ sudo apt-get update
Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty Release.gpg
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.canonical.com]("http://archive.canonical.com/") lucid Release.gpg                                                               
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid Release.gpg                                                                  
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.canonical.com/](http://archive.canonical.com/) lucid/partner Translation-en_IN                                                
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty/multiverse Translation-en_IN  
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates Release.gpg                
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_IN         
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://archive.canonical.com]("http://archive.canonical.com/") lucid Release                             
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates/multiverse Translation-en_IN
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_IN   
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://archive.canonical.com]("http://archive.canonical.com/") lucid/partner Packages                       
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty Release                               
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_IN     
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://archive.canonical.com]("http://archive.canonical.com/") lucid/partner Packages                       
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates Release                       
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_IN   
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.canonical.com]("http://archive.canonical.com/") lucid/partner Packages                       
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/multiverse Packages                   
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-updates Release.gpg                    
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_IN
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_IN
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_IN
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/multiverse Packages
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_IN
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/multiverse Packages
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-security Release.gpg
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/multiverse Packages         
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_IN 
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/multiverse Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_IN
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_IN
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_IN
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid Release
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-updates Release
Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/multiverse Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-security Release
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid/main Packages
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid/restricted Packages
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid/main Sources
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid/restricted Sources
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid/universe Packages
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid/universe Sources
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid/multiverse Packages
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid/multiverse Sources
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-updates/main Packages
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-updates/restricted Packages
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-updates/main Sources
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-updates/restricted Sources
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-updates/universe Packages
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-updates/universe Sources
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-updates/multiverse Packages
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-updates/multiverse Sources
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-security/main Packages
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-security/restricted Packages
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-security/main Sources
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-security/restricted Sources
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-security/universe Packages
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-security/universe Sources
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-security/multiverse Packages
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-security/multiverse Sources
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid/main Packages
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid/restricted Packages
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid/main Sources
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid/restricted Sources
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid/universe Packages
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid/universe Sources
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid/multiverse Packages
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid/multiverse Sources
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-updates/main Packages
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-updates/restricted Packages
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-updates/main Sources
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-updates/restricted Sources
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-updates/universe Packages
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-updates/universe Sources
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-updates/multiverse Packages
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-updates/multiverse Sources
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-security/main Packages
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-security/restricted Packages
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-security/main Sources
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-security/restricted Sources
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-security/universe Packages
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-security/universe Sources
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-security/multiverse Packages
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-security/multiverse Sources
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid/main Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid/restricted Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid/main Sources
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid/restricted Sources
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid/universe Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid/universe Sources
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid/multiverse Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid/multiverse Sources
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-updates/main Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-updates/restricted Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-updates/main Sources
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-updates/restricted Sources
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-updates/universe Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-updates/universe Sources
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-updates/multiverse Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-updates/multiverse Sources
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-security/main Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-security/restricted Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-security/main Sources
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-security/restricted Sources
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-security/universe Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-security/universe Sources
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-security/multiverse Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-security/multiverse Sources
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...id/Release.gpg]("http://archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg")  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...tion-en_IN.bz2]("http://archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_IN.bz2")  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...tion-en_IN.bz2]("http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_IN.bz2")  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...tion-en_IN.bz2]("http://archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_IN.bz2")  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...tion-en_IN.bz2]("http://archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_IN.bz2")  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...es/Release.gpg]("http://archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg")  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...tion-en_IN.bz2]("http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_IN.bz2")  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...tion-en_IN.bz2]("http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_IN.bz2")  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...tion-en_IN.bz2]("http://archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_IN.bz2")  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...tion-en_IN.bz2]("http://archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_IN.bz2")  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...ty/Release.gpg]("http://archive.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg")  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...tion-en_IN.bz2]("http://archive.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_IN.bz2")  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...tion-en_IN.bz2]("http://archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_IN.bz2")  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...tion-en_IN.bz2]("http://archive.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_IN.bz2")  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...tion-en_IN.bz2]("http://archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_IN.bz2")  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.canonical.com/dists/lucid/Release.gpg](http://archive.canonical.com/dists/lucid/Release.gpg)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.canonical.com/dists/l...tion-en_IN.bz2]("http://archive.canonical.com/dists/lucid/partner/i18n/Translation-en_IN.bz2")  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...ty/Release.gpg]("http://us.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg")  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...tion-en_IN.bz2]("http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_IN.bz2")  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...es/Release.gpg]("http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg")  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...tion-en_IN.bz2]("http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_IN.bz2")  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.canonical.com/dists/l...64/Packages.gz]("http://archive.canonical.com/dists/lucid/partner/binary-amd64/Packages.gz")  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...64/Packages.gz]("http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-amd64/Packages.gz")  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...64/Packages.gz]("http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-amd64/Packages.gz")  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...64/Packages.gz]("http://archive.ubuntu.com/ubuntu/dists/lucid/main/binary-amd64/Packages.gz")  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...64/Packages.gz]("http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-amd64/Packages.gz")  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz]("http://archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz")  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz]("http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz")  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...64/Packages.gz]("http://archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-amd64/Packages.gz")  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz]("http://archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz")  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...64/Packages.gz]("http://archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-amd64/Packages.gz")  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz]("http://archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz")  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...64/Packages.gz]("http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-amd64/Packages.gz")  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...64/Packages.gz]("http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-amd64/Packages.gz")  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz]("http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz")  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz]("http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz")  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...64/Packages.gz]("http://archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-amd64/Packages.gz")  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz]("http://archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz")  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...64/Packages.gz]("http://archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-amd64/Packages.gz")  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz]("http://archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz")  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...64/Packages.gz]("http://archive.ubuntu.com/ubuntu/dists/lucid-security/main/binary-amd64/Packages.gz")  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...64/Packages.gz]("http://archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-amd64/Packages.gz")  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz]("http://archive.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.gz")  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz]("http://archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz")  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...64/Packages.gz]("http://archive.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-amd64/Packages.gz")  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz]("http://archive.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.gz")  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...64/Packages.gz]("http://archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-amd64/Packages.gz")  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz]("http://archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.gz")  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by tom4everitt on 2011-07-28
The apt-get update failure indicates the servers were down or that something was wrong with your Internet connection. 

This may well be why the tasksel command failed as well. 

Try again a bit later, I would say.

If that doesn't work, a sort of general remedy to these kinds of issues is to run:
```

sudo dpkg --configure -a

```
It won't hurt to try it.

---

