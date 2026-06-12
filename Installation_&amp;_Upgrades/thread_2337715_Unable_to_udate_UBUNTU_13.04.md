---
title: "Unable to udate UBUNTU 13.04"
date: 2016-09-20
forum: Installation &amp; Upgrades
---

### Post by irshad437 on 2016-09-20
Did sudo apt-get update. Following is the terminal output.
update-manager gives an error "Failed to download repositories. Please check your internet connetion"
I have NO problem with internet as i have posted this question from the same computer. I want to update it to latest version.
[INDENT]irshad@irshad-Inspiron-3521:~$ sudo apt-get update
[sudo] password for irshad: 
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring Release.gpg
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring-updates Release.gpg               
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring-backports Release.gpg             
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring Release                           
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring-updates Release                   
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring-backports Release                 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release.gpg                                
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security Release.gpg                 
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security Release          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release                         
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/main Sources                
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/restricted Sources
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/universe Sources 
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/multiverse Sources
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/main i386 Packages
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring/main Sources           
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring/restricted Sources     
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/restricted i386 Packages
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring/universe Sources       
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring/multiverse Sources     
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring/main i386 Packages
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring/restricted i386 Packages
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring/universe i386 Packages
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring/multiverse i386 Packages
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring/main Translation-en_IN
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring/main Translation-en
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring/multiverse Translation-en_IN
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring/multiverse Translation-en
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring/restricted Translation-en_IN
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring/restricted Translation-en
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring/universe Translation-en_IN
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring/universe Translation-en
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring-updates/main Sources
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring-updates/restricted Sources
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring-updates/universe Sources
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring-updates/multiverse Sources
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring-updates/main i386 Packages
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring-updates/restricted i386 Packages
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring-updates/universe i386 Packages
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/universe i386 Packages
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring-updates/multiverse i386 Packages  
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring-updates/main Translation-en_IN    
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring-updates/main Translation-en
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring-updates/multiverse Translation-en_IN
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring-updates/multiverse Translation-en
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring-updates/restricted Translation-en_IN
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring-updates/restricted Translation-en
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring-updates/universe Translation-en_IN
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring-updates/universe Translation-en
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring-backports/main Sources
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring-backports/restricted Sources
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring-backports/universe Sources
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring-backports/multiverse Sources
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring-backports/main i386 Packages
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring-backports/restricted i386 Packages
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring-backports/universe i386 Packages
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring-backports/multiverse i386 Packages
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring-backports/main Translation-en_IN  
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring-backports/main Translation-en     
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring-backports/multiverse Translation-en_IN
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring-backports/multiverse Translation-en
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/multiverse i386 Packages
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring-backports/restricted Translation-en_IN
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring-backports/restricted Translation-en
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring-backports/universe Translation-en_IN
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) raring-backports/universe Translation-en
  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/main Translation-en
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/multiverse Translation-en
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/restricted Translation-en
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/universe Translation-en
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Sources
  404  Not Found [IP: 91.189.92.152 80]
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main i386 Packages
  404  Not Found [IP: 91.189.92.152 80]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en_IN
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/main Translation-en_IN
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/multiverse Translation-en_IN
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/restricted Translation-en_IN
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/universe Translation-en_IN
W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring/Release.gpg](http://in.old-releases.ubuntu.com/ubuntu/dists/raring/Release.gpg)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring-updates/Release.gpg](http://in.old-releases.ubuntu.com/ubuntu/dists/raring-updates/Release.gpg)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring-backports/Release.gpg](http://in.old-releases.ubuntu.com/ubuntu/dists/raring-backports/Release.gpg)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring/main/source/Sources](http://in.old-releases.ubuntu.com/ubuntu/dists/raring/main/source/Sources)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring/restricted/source/Sources](http://in.old-releases.ubuntu.com/ubuntu/dists/raring/restricted/source/Sources)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring/universe/source/Sources](http://in.old-releases.ubuntu.com/ubuntu/dists/raring/universe/source/Sources)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring/multiverse/source/Sources](http://in.old-releases.ubuntu.com/ubuntu/dists/raring/multiverse/source/Sources)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring/restricted/binary-i386/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/raring/restricted/binary-i386/Packages)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring/universe/binary-i386/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/raring/universe/binary-i386/Packages)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring/multiverse/binary-i386/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/raring/multiverse/binary-i386/Packages)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring/main/i18n/Translation-en_IN](http://in.old-releases.ubuntu.com/ubuntu/dists/raring/main/i18n/Translation-en_IN)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring/main/i18n/Translation-en](http://in.old-releases.ubuntu.com/ubuntu/dists/raring/main/i18n/Translation-en)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring/multiverse/i18n/Translation-en_IN](http://in.old-releases.ubuntu.com/ubuntu/dists/raring/multiverse/i18n/Translation-en_IN)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring/multiverse/i18n/Translation-en](http://in.old-releases.ubuntu.com/ubuntu/dists/raring/multiverse/i18n/Translation-en)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring/restricted/i18n/Translation-en_IN](http://in.old-releases.ubuntu.com/ubuntu/dists/raring/restricted/i18n/Translation-en_IN)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring/restricted/i18n/Translation-en](http://in.old-releases.ubuntu.com/ubuntu/dists/raring/restricted/i18n/Translation-en)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring/universe/i18n/Translation-en_IN](http://in.old-releases.ubuntu.com/ubuntu/dists/raring/universe/i18n/Translation-en_IN)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring/universe/i18n/Translation-en](http://in.old-releases.ubuntu.com/ubuntu/dists/raring/universe/i18n/Translation-en)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring-updates/main/source/Sources](http://in.old-releases.ubuntu.com/ubuntu/dists/raring-updates/main/source/Sources)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring-updates/restricted/source/Sources](http://in.old-releases.ubuntu.com/ubuntu/dists/raring-updates/restricted/source/Sources)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring-updates/universe/source/Sources](http://in.old-releases.ubuntu.com/ubuntu/dists/raring-updates/universe/source/Sources)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring-updates/multiverse/source/Sources](http://in.old-releases.ubuntu.com/ubuntu/dists/raring-updates/multiverse/source/Sources)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring-updates/main/binary-i386/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/raring-updates/main/binary-i386/Packages)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring-updates/restricted/binary-i386/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/raring-updates/restricted/binary-i386/Packages)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring-updates/universe/binary-i386/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/raring-updates/universe/binary-i386/Packages)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring-updates/multiverse/binary-i386/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/raring-updates/multiverse/binary-i386/Packages)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring-updates/main/i18n/Translation-en_IN](http://in.old-releases.ubuntu.com/ubuntu/dists/raring-updates/main/i18n/Translation-en_IN)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring-updates/main/i18n/Translation-en](http://in.old-releases.ubuntu.com/ubuntu/dists/raring-updates/main/i18n/Translation-en)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring-updates/multiverse/i18n/Translation-en_IN](http://in.old-releases.ubuntu.com/ubuntu/dists/raring-updates/multiverse/i18n/Translation-en_IN)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring-updates/multiverse/i18n/Translation-en](http://in.old-releases.ubuntu.com/ubuntu/dists/raring-updates/multiverse/i18n/Translation-en)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring-updates/restricted/i18n/Translation-en_IN](http://in.old-releases.ubuntu.com/ubuntu/dists/raring-updates/restricted/i18n/Translation-en_IN)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring-updates/restricted/i18n/Translation-en](http://in.old-releases.ubuntu.com/ubuntu/dists/raring-updates/restricted/i18n/Translation-en)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring-updates/universe/i18n/Translation-en_IN](http://in.old-releases.ubuntu.com/ubuntu/dists/raring-updates/universe/i18n/Translation-en_IN)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring-updates/universe/i18n/Translation-en](http://in.old-releases.ubuntu.com/ubuntu/dists/raring-updates/universe/i18n/Translation-en)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring-backports/main/source/Sources](http://in.old-releases.ubuntu.com/ubuntu/dists/raring-backports/main/source/Sources)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring-backports/restricted/source/Sources](http://in.old-releases.ubuntu.com/ubuntu/dists/raring-backports/restricted/source/Sources)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring-backports/universe/source/Sources](http://in.old-releases.ubuntu.com/ubuntu/dists/raring-backports/universe/source/Sources)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring-backports/multiverse/source/Sources](http://in.old-releases.ubuntu.com/ubuntu/dists/raring-backports/multiverse/source/Sources)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring-backports/main/binary-i386/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/raring-backports/main/binary-i386/Packages)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring-backports/restricted/binary-i386/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/raring-backports/restricted/binary-i386/Packages)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring-backports/universe/binary-i386/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/raring-backports/universe/binary-i386/Packages)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring-backports/multiverse/binary-i386/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/raring-backports/multiverse/binary-i386/Packages)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring-backports/main/i18n/Translation-en_IN](http://in.old-releases.ubuntu.com/ubuntu/dists/raring-backports/main/i18n/Translation-en_IN)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring-backports/main/i18n/Translation-en](http://in.old-releases.ubuntu.com/ubuntu/dists/raring-backports/main/i18n/Translation-en)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring-backports/multiverse/i18n/Translation-en_IN](http://in.old-releases.ubuntu.com/ubuntu/dists/raring-backports/multiverse/i18n/Translation-en_IN)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring-backports/multiverse/i18n/Translation-en](http://in.old-releases.ubuntu.com/ubuntu/dists/raring-backports/multiverse/i18n/Translation-en)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring-backports/restricted/i18n/Translation-en_IN](http://in.old-releases.ubuntu.com/ubuntu/dists/raring-backports/restricted/i18n/Translation-en_IN)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring-backports/restricted/i18n/Translation-en](http://in.old-releases.ubuntu.com/ubuntu/dists/raring-backports/restricted/i18n/Translation-en)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring-backports/universe/i18n/Translation-en_IN](http://in.old-releases.ubuntu.com/ubuntu/dists/raring-backports/universe/i18n/Translation-en_IN)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/raring-backports/universe/i18n/Translation-en](http://in.old-releases.ubuntu.com/ubuntu/dists/raring-backports/universe/i18n/Translation-en)  Something wicked happened resolving 'in.old-releases.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/raring/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/raring/main/source/Sources)  404  Not Found [IP: 91.189.92.152 80]

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages)  404  Not Found [IP: 91.189.92.152 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
[/INDENT]

---

### Post by QIII on 2016-09-20
Hello!

13.04 is long past its End Of Life and the repositories have been moved to old-releases.  *in.old-releases* does not appear to exist.

Although there is a path to use "old-release" repositories to bring you to a supported release, each step is more likely to result in a significant emotional event than a successful update.  And you would have several of those old-release updates to do.

I would highly recommend a fresh installation of a currently supported release.

Cheers!

---

