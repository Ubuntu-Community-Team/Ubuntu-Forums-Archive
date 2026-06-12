---
title: "Lenovo ideapad s205 - install of xubuntu"
date: 2013-09-24
forum: Installation &amp; Upgrades
---

### Post by Jimmy_Page on 2013-09-24
HI guys,
I've got a common problem with installation x/ubuntu on this netbook. After installation lates version of xubuntu I cannot boot it. I have to reinstall/replace grub but thats a bit problem for me. I've found some guides on the internet but none of them works so far. Now I'm trying to solve it via this guide: 

[http://helms-deep.cable.nu/~rwh/blog/?p=177](http://helms-deep.cable.nu/~rwh/blog/?p=177)

but an erros has occured:

after -  chroot .
command apt-get update says this:

```
root@xubuntu:/# apt-get update
Err http://cz.archive.ubuntu.com raring Release.gpg
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://security.ubuntu.com raring-security Release.gpg              
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err http://extras.ubuntu.com raring Release.gpg                         
  Something wicked happened resolving 'extras.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring-updates Release.gpg             
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring-backports Release.gpg
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Ign http://security.ubuntu.com raring-security Release
Ign http://cz.archive.ubuntu.com raring Release
Ign http://cz.archive.ubuntu.com raring-updates Release
Ign http://extras.ubuntu.com raring Release
Ign http://security.ubuntu.com raring-security/main Sources/DiffIndex
Ign http://cz.archive.ubuntu.com raring-backports Release
Ign http://extras.ubuntu.com raring/main Sources/DiffIndex
Ign http://cz.archive.ubuntu.com raring/main Sources/DiffIndex
Ign http://cz.archive.ubuntu.com raring/restricted Sources/DiffIndex
Ign http://cz.archive.ubuntu.com raring/universe Sources/DiffIndex
Ign http://cz.archive.ubuntu.com raring/multiverse Sources/DiffIndex
Ign http://cz.archive.ubuntu.com raring/main amd64 Packages/DiffIndex
Ign http://cz.archive.ubuntu.com raring/restricted amd64 Packages/DiffIndex
Ign http://cz.archive.ubuntu.com raring/universe amd64 Packages/DiffIndex
Ign http://cz.archive.ubuntu.com raring/multiverse amd64 Packages/DiffIndex
Ign http://security.ubuntu.com raring-security/restricted Sources/DiffIndex
Ign http://security.ubuntu.com raring-security/universe Sources/DiffIndex
Ign http://security.ubuntu.com raring-security/multiverse Sources/DiffIndex
Ign http://security.ubuntu.com raring-security/main amd64 Packages/DiffIndex
Ign http://security.ubuntu.com raring-security/restricted amd64 Packages/DiffIndex
Ign http://security.ubuntu.com raring-security/universe amd64 Packages/DiffIndex
Ign http://security.ubuntu.com raring-security/multiverse amd64 Packages/DiffIndex
Ign http://security.ubuntu.com raring-security/main i386 Packages/DiffIndex
Ign http://security.ubuntu.com raring-security/restricted i386 Packages/DiffIndex
Ign http://cz.archive.ubuntu.com raring/main i386 Packages/DiffIndex         
Ign http://cz.archive.ubuntu.com raring/restricted i386 Packages/DiffIndex   
Ign http://cz.archive.ubuntu.com raring/universe i386 Packages/DiffIndex     
Ign http://cz.archive.ubuntu.com raring/multiverse i386 Packages/DiffIndex   
Ign http://security.ubuntu.com raring-security/universe i386 Packages/DiffIndex
Ign http://extras.ubuntu.com raring/main amd64 Packages/DiffIndex            
Ign http://extras.ubuntu.com raring/main i386 Packages/DiffIndex             
Ign http://security.ubuntu.com raring-security/multiverse i386 Packages/DiffIndex
Ign http://cz.archive.ubuntu.com raring-updates/main Sources/DiffIndex
Ign http://cz.archive.ubuntu.com raring-updates/restricted Sources/DiffIndex
Ign http://cz.archive.ubuntu.com raring-updates/universe Sources/DiffIndex
Ign http://cz.archive.ubuntu.com raring-updates/multiverse Sources/DiffIndex
Ign http://cz.archive.ubuntu.com raring-updates/main amd64 Packages/DiffIndex
Ign http://cz.archive.ubuntu.com raring-updates/restricted amd64 Packages/DiffIndex
Ign http://cz.archive.ubuntu.com raring-updates/universe amd64 Packages/DiffIndex
Ign http://cz.archive.ubuntu.com raring-updates/multiverse amd64 Packages/DiffIndex
Err http://extras.ubuntu.com raring/main Translation-en_US
  Something wicked happened resolving 'extras.ubuntu.com:http' (-11 - System error)
Ign http://cz.archive.ubuntu.com raring-updates/main i386 Packages/DiffIndex   
Ign http://cz.archive.ubuntu.com raring-updates/restricted i386 Packages/DiffIndex
Ign http://cz.archive.ubuntu.com raring-updates/universe i386 Packages/DiffIndex
Ign http://cz.archive.ubuntu.com raring-updates/multiverse i386 Packages/DiffIndex
Err http://extras.ubuntu.com raring/main Translation-en                        
  Something wicked happened resolving 'extras.ubuntu.com:http' (-11 - System error)
Err http://extras.ubuntu.com raring/main Sources                               
  Something wicked happened resolving 'extras.ubuntu.com:http' (-11 - System error)
Err http://extras.ubuntu.com raring/main amd64 Packages                        
  Something wicked happened resolving 'extras.ubuntu.com:http' (-11 - System error)
Err http://extras.ubuntu.com raring/main i386 Packages                         
  Something wicked happened resolving 'extras.ubuntu.com:http' (-11 - System error)
Ign http://cz.archive.ubuntu.com raring-backports/main Sources/DiffIndex       
Ign http://cz.archive.ubuntu.com raring-backports/restricted Sources/DiffIndex
Ign http://cz.archive.ubuntu.com raring-backports/universe Sources/DiffIndex
Ign http://cz.archive.ubuntu.com raring-backports/multiverse Sources/DiffIndex
Ign http://cz.archive.ubuntu.com raring-backports/main amd64 Packages/DiffIndex
Ign http://cz.archive.ubuntu.com raring-backports/restricted amd64 Packages/DiffIndex
Ign http://cz.archive.ubuntu.com raring-backports/universe amd64 Packages/DiffIndex
Ign http://cz.archive.ubuntu.com raring-backports/multiverse amd64 Packages/DiffIndex
Ign http://cz.archive.ubuntu.com raring-backports/main i386 Packages/DiffIndex
Err http://security.ubuntu.com raring-security/main Translation-en_US
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Ign http://cz.archive.ubuntu.com raring-backports/restricted i386 Packages/DiffIndex
Err http://security.ubuntu.com raring-security/main Translation-en
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Ign http://cz.archive.ubuntu.com raring-backports/universe i386 Packages/DiffIndex
Err http://security.ubuntu.com raring-security/multiverse Translation-en_US
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Ign http://cz.archive.ubuntu.com raring-backports/multiverse i386 Packages/DiffIndex
Err http://security.ubuntu.com raring-security/multiverse Translation-en
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err http://security.ubuntu.com raring-security/restricted Translation-en_US
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err http://security.ubuntu.com raring-security/restricted Translation-en
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err http://security.ubuntu.com raring-security/universe Translation-en_US
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err http://security.ubuntu.com raring-security/universe Translation-en
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err http://security.ubuntu.com raring-security/main Sources
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err http://security.ubuntu.com raring-security/restricted Sources            
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err http://security.ubuntu.com raring-security/universe Sources              
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err http://security.ubuntu.com raring-security/multiverse Sources            
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err http://security.ubuntu.com raring-security/main amd64 Packages           
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err http://security.ubuntu.com raring-security/restricted amd64 Packages     
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err http://security.ubuntu.com raring-security/universe amd64 Packages       
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err http://security.ubuntu.com raring-security/multiverse amd64 Packages     
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err http://security.ubuntu.com raring-security/main i386 Packages            
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err http://security.ubuntu.com raring-security/restricted i386 Packages      
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err http://security.ubuntu.com raring-security/universe i386 Packages        
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err http://security.ubuntu.com raring-security/multiverse i386 Packages      
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring/main Translation-en_US               
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring/main Translation-en
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring/multiverse Translation-en_US
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring/multiverse Translation-en
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring/restricted Translation-en_US
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring/restricted Translation-en
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring/universe Translation-en_US
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring/universe Translation-en
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring-updates/main Translation-en_US
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring-updates/main Translation-en
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring-updates/multiverse Translation-en_US
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring-updates/multiverse Translation-en
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring-updates/restricted Translation-en_US
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring-updates/restricted Translation-en
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring-updates/universe Translation-en_US
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring-updates/universe Translation-en
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring-backports/main Translation-en_US
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring-backports/main Translation-en
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring-backports/multiverse Translation-en_US
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring-backports/multiverse Translation-en
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring-backports/restricted Translation-en_US
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring-backports/restricted Translation-en
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring-backports/universe Translation-en_US
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring-backports/universe Translation-en
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring/main Sources
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring/restricted Sources
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring/universe Sources
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring/multiverse Sources
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring/main amd64 Packages
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring/restricted amd64 Packages
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring/universe amd64 Packages
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring/multiverse amd64 Packages
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring/main i386 Packages
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring/restricted i386 Packages
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring/universe i386 Packages
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring/multiverse i386 Packages
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring-updates/main Sources
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring-updates/restricted Sources
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring-updates/universe Sources
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring-updates/multiverse Sources
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring-updates/main amd64 Packages
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring-updates/restricted amd64 Packages
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring-updates/universe amd64 Packages
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring-updates/multiverse amd64 Packages
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring-updates/main i386 Packages
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring-updates/restricted i386 Packages
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring-updates/universe i386 Packages
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring-updates/multiverse i386 Packages
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring-backports/main Sources
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring-backports/restricted Sources
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring-backports/universe Sources
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring-backports/multiverse Sources
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring-backports/main amd64 Packages
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring-backports/restricted amd64 Packages
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring-backports/universe amd64 Packages
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring-backports/multiverse amd64 Packages
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring-backports/main i386 Packages
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring-backports/restricted i386 Packages
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring-backports/universe i386 Packages
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
Err http://cz.archive.ubuntu.com raring-backports/multiverse i386 Packages
  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)
W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring/Release.gpg  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring-updates/Release.gpg  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring-backports/Release.gpg  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/raring-security/Release.gpg  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/raring/Release.gpg  Something wicked happened resolving 'extras.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/raring-security/main/i18n/Translation-en_US  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/raring-security/main/i18n/Translation-en  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/raring-security/multiverse/i18n/Translation-en_US  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/raring-security/multiverse/i18n/Translation-en  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/raring-security/restricted/i18n/Translation-en_US  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/raring-security/restricted/i18n/Translation-en  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/raring-security/universe/i18n/Translation-en_US  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/raring-security/universe/i18n/Translation-en  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring/main/i18n/Translation-en_US  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring/main/i18n/Translation-en  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring/multiverse/i18n/Translation-en_US  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring/multiverse/i18n/Translation-en  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring/restricted/i18n/Translation-en_US  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring/restricted/i18n/Translation-en  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring/universe/i18n/Translation-en_US  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring/universe/i18n/Translation-en  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring-updates/main/i18n/Translation-en_US  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring-updates/main/i18n/Translation-en  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/i18n/Translation-en_US  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/i18n/Translation-en  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/i18n/Translation-en_US  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/i18n/Translation-en  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring-updates/universe/i18n/Translation-en_US  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring-updates/universe/i18n/Translation-en  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/raring/main/i18n/Translation-en_US  Something wicked happened resolving 'extras.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/raring/main/i18n/Translation-en  Something wicked happened resolving 'extras.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/raring-security/main/source/Sources  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring-backports/main/i18n/Translation-en_US  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring-backports/main/i18n/Translation-en  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/i18n/Translation-en_US  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/i18n/Translation-en  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/i18n/Translation-en_US  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/i18n/Translation-en  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring-backports/universe/i18n/Translation-en_US  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring-backports/universe/i18n/Translation-en  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/raring/main/source/Sources  Something wicked happened resolving 'extras.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring/main/source/Sources  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring/restricted/source/Sources  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring/universe/source/Sources  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring/multiverse/source/Sources  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring/main/binary-amd64/Packages  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring/restricted/binary-amd64/Packages  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring/universe/binary-amd64/Packages  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring/multiverse/binary-amd64/Packages  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/raring-security/restricted/source/Sources  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/raring-security/universe/source/Sources  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/raring-security/multiverse/source/Sources  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/raring-security/main/binary-amd64/Packages  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/raring-security/restricted/binary-amd64/Packages  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/raring-security/universe/binary-amd64/Packages  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/raring-security/multiverse/binary-amd64/Packages  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/raring-security/main/binary-i386/Packages  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/raring-security/restricted/binary-i386/Packages  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring/restricted/binary-i386/Packages  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring/universe/binary-i386/Packages  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring/multiverse/binary-i386/Packages  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/raring-security/universe/binary-i386/Packages  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/raring/main/binary-amd64/Packages  Something wicked happened resolving 'extras.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages  Something wicked happened resolving 'extras.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/raring-security/multiverse/binary-i386/Packages  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring-updates/main/source/Sources  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/source/Sources  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring-updates/universe/source/Sources  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/source/Sources  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring-updates/main/binary-amd64/Packages  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/binary-amd64/Packages  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring-updates/universe/binary-amd64/Packages  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/binary-amd64/Packages  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring-updates/main/binary-i386/Packages  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/binary-i386/Packages  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring-updates/universe/binary-i386/Packages  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/binary-i386/Packages  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring-backports/main/source/Sources  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/source/Sources  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring-backports/universe/source/Sources  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/source/Sources  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring-backports/main/binary-amd64/Packages  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/binary-amd64/Packages  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring-backports/universe/binary-amd64/Packages  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/binary-amd64/Packages  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring-backports/main/binary-i386/Packages  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/binary-i386/Packages  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring-backports/universe/binary-i386/Packages  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/binary-i386/Packages  Something wicked happened resolving 'cz.archive.ubuntu.com:http' (-11 - System error)

E: Some index files failed to download. They have been ignored, or old ones used instead.
root@xubuntu:/# 

```

I tried to google it but I didnt find anything that would help me....

thanks for ideas!

---

### Post by Jimmy_Page on 2013-09-24
nobody knows?

---

### Post by oldfred on 2013-09-24
Those instructions still mention grub legacy. Ubuntu has not used that since 9.04 as default boot loader. Since 9.10 it has used grub2.
Also its chroot does not include a network, this command may be necessary.
 sudo cp /etc/resolv.conf /mnt/etc/resolv.conf #(may or may not be necessary to establish an internet connection)

Better to use Boot-Repair as it does all that automatically. If still issues post link to bootinfo report.
      
 
Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by Jimmy_Page on 2013-09-26
thanks man! you are my hero! I wish I had known it so F.. simple! damn it! im gonna build a statue in your honour! you have no idea what Ive been through because of that

---

