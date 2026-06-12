---
title: "Not upgrading Ubuntu 13.10 to 14.04"
date: 2014-04-29
forum: Installation &amp; Upgrades
---

### Post by susicox143 on 2014-04-29
HI All, 

I have followed all the below link steps to update from 13.10 to 14.04 but no success. After update manager it says your system is upto date. I have also changed Mirror but no luck. Please what i can do to upgrade ubuntu. I have read other solutions on this forum and ubuntu ask but non of them solve my problems. 

[http://www.tecmint.com/upgrade-ubuntu-to-14-04/](http://www.tecmint.com/upgrade-ubuntu-to-14-04/)

---

### Post by slickymaster on 2014-04-29
Do you have any added extra PPAs on your Software-Sources? If so, disable them and then run```
sudo apt-get update && sudo apt-get dist-upgrade
sudo do-release-upgrade
```

---

### Post by grahammechanical on 2014-04-29
How do you know that the upgrade has not been successful? What are you expecting to see that you are not seeing?

---

### Post by susicox143 on 2014-05-02
> **slickymaster said:**
> Do you have any added extra PPAs on your Software-Sources? If so, disable them and then run```
sudo apt-get update && sudo apt-get dist-upgrade
sudo do-release-upgrade
```

Here is the result of this command:    sudo apt-get update && sudo apt-get dist-upgrade

```
Ign http://ppa.launchpad.net saucy Release.gpg                                 Ign http://archive.ubuntu.com saucy Release                                    
Ign http://ppa.launchpad.net saucy Release                                     
Ign http://archive.ubuntu.com saucy-updates Release                            
Ign http://ppa.launchpad.net saucy Release                                     
Ign http://archive.ubuntu.com saucy-backports Release                          
Ign http://ppa.launchpad.net saucy Release                                     
Ign http://archive.ubuntu.com saucy-security Release                           
Ign http://ppa.launchpad.net saucy Release                                     
Ign http://archive.ubuntu.com saucy-proposed Release                           
Ign http://ppa.launchpad.net saucy Release                                     
Ign http://ppa.launchpad.net saucy Release                                     
Ign http://ppa.launchpad.net saucy Release                                     
Err http://download.mendeley.com stable/main amd64 Packages                    
  403  Forbidden
Ign http://ppa.launchpad.net saucy Release                                     
Err http://deb.opera.com stable/non-free amd64 Packages                        
  403  Forbidden
Err http://dl.google.com stable/main amd64 Packages                            
  403  Forbidden
Err http://deb.opera.com stable/non-free i386 Packages                         
  403  Forbidden
Err http://dl.google.com stable/main i386 Packages                             
  403  Forbidden
Err http://download.mendeley.com stable/main i386 Packages                     
  403  Forbidden
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://download.mendeley.com stable/main Translation-en_US                 
Ign http://deb.opera.com stable/non-free Translation-en_US                     
Ign http://dl.google.com stable/main Translation-en                            
Ign http://download.mendeley.com stable/main Translation-en                    
Err http://extras.ubuntu.com saucy/main Sources                                
  403  Forbidden
Err http://archive.canonical.com saucy/partner Sources                         
  403  Forbidden
Err http://extras.ubuntu.com saucy/main amd64 Packages                         
  403  Forbidden
Err http://archive.canonical.com saucy/partner amd64 Packages                  
  403  Forbidden
Ign http://deb.opera.com stable/non-free Translation-en                        
Err http://extras.ubuntu.com saucy/main i386 Packages                          
  403  Forbidden
Err http://archive.canonical.com saucy/partner i386 Packages                   
  403  Forbidden
Ign http://extras.ubuntu.com saucy/main Translation-en_US                      
Ign http://archive.canonical.com saucy/partner Translation-en_US               
Ign http://extras.ubuntu.com saucy/main Translation-en                         
Ign http://archive.canonical.com saucy/partner Translation-en                  
Err http://ppa.launchpad.net saucy/main amd64 Packages               
  403  Forbidden
Err http://ppa.launchpad.net saucy/main i386 Packages
  403  Forbidden
Ign http://ppa.launchpad.net saucy/main Translation-en_US
Ign http://ppa.launchpad.net saucy/main Translation-en
Err http://ppa.launchpad.net saucy/main amd64 Packages
  403  Forbidden
Err http://ppa.launchpad.net saucy/main i386 Packages
  403  Forbidden
Ign http://ppa.launchpad.net saucy/main Translation-en_US
Ign http://ppa.launchpad.net saucy/main Translation-en
Err http://ppa.launchpad.net saucy/main amd64 Packages
  403  Forbidden
Err http://ppa.launchpad.net saucy/main i386 Packages
  403  Forbidden
Ign http://ppa.launchpad.net saucy/main Translation-en_US
Ign http://ppa.launchpad.net saucy/main Translation-en
Err http://ppa.launchpad.net saucy/main amd64 Packages
  403  Forbidden
Err http://ppa.launchpad.net saucy/main i386 Packages
  403  Forbidden
Ign http://ppa.launchpad.net saucy/main Translation-en_US
Ign http://ppa.launchpad.net saucy/main Translation-en
Err http://ppa.launchpad.net saucy/main amd64 Packages
  403  Forbidden
Err http://ppa.launchpad.net saucy/main i386 Packages
  403  Forbidden
Ign http://ppa.launchpad.net saucy/main Translation-en_US
Ign http://ppa.launchpad.net saucy/main Translation-en
Err http://ppa.launchpad.net saucy/main amd64 Packages
  403  Forbidden
Err http://ppa.launchpad.net saucy/main i386 Packages
  403  Forbidden
Ign http://ppa.launchpad.net saucy/main Translation-en_US
Ign http://ppa.launchpad.net saucy/main Translation-en
Err http://ppa.launchpad.net saucy/main Sources
  403  Forbidden
Err http://ppa.launchpad.net saucy/main amd64 Packages
  403  Forbidden
Err http://ppa.launchpad.net saucy/main i386 Packages
  403  Forbidden
Ign http://ppa.launchpad.net saucy/main Translation-en_US
Ign http://ppa.launchpad.net saucy/main Translation-en
Err http://ppa.launchpad.net saucy/main amd64 Packages
  403  Forbidden
Err http://ppa.launchpad.net saucy/main i386 Packages
  403  Forbidden
Ign http://ppa.launchpad.net saucy/main Translation-en_US
Ign http://ppa.launchpad.net saucy/main Translation-en
Err http://archive.ubuntu.com saucy/main Sources
  403  Forbidden
Err http://archive.ubuntu.com saucy/restricted Sources
  403  Forbidden
Err http://archive.ubuntu.com saucy/universe Sources
  403  Forbidden
Err http://archive.ubuntu.com saucy/multiverse Sources
  403  Forbidden
Err http://archive.ubuntu.com saucy/main amd64 Packages
  403  Forbidden
Err http://archive.ubuntu.com saucy/restricted amd64 Packages
  403  Forbidden
Err http://archive.ubuntu.com saucy/universe amd64 Packages
  403  Forbidden
Err http://archive.ubuntu.com saucy/multiverse amd64 Packages
  403  Forbidden
Err http://archive.ubuntu.com saucy/main i386 Packages
  403  Forbidden
Err http://archive.ubuntu.com saucy/restricted i386 Packages
  403  Forbidden
Err http://archive.ubuntu.com saucy/universe i386 Packages
  403  Forbidden
Err http://archive.ubuntu.com saucy/multiverse i386 Packages
  403  Forbidden
Ign http://archive.ubuntu.com saucy/main Translation-en_US
Ign http://archive.ubuntu.com saucy/main Translation-en
Ign http://archive.ubuntu.com saucy/multiverse Translation-en_US
Ign http://archive.ubuntu.com saucy/multiverse Translation-en
Ign http://archive.ubuntu.com saucy/restricted Translation-en_US
Ign http://archive.ubuntu.com saucy/restricted Translation-en
Ign http://archive.ubuntu.com saucy/universe Translation-en_US
Ign http://archive.ubuntu.com saucy/universe Translation-en
Err http://archive.ubuntu.com saucy-updates/main Sources
  403  Forbidden
Err http://archive.ubuntu.com saucy-updates/restricted Sources
  403  Forbidden
Err http://archive.ubuntu.com saucy-updates/universe Sources
  403  Forbidden
Err http://archive.ubuntu.com saucy-updates/multiverse Sources
  403  Forbidden
Err http://archive.ubuntu.com saucy-updates/main amd64 Packages
  403  Forbidden
Err http://archive.ubuntu.com saucy-updates/restricted amd64 Packages
  403  Forbidden
Err http://archive.ubuntu.com saucy-updates/universe amd64 Packages
  403  Forbidden
Err http://archive.ubuntu.com saucy-updates/multiverse amd64 Packages
  403  Forbidden
Err http://archive.ubuntu.com saucy-updates/main i386 Packages
  403  Forbidden
Err http://archive.ubuntu.com saucy-updates/restricted i386 Packages
  403  Forbidden
Err http://archive.ubuntu.com saucy-updates/universe i386 Packages
  403  Forbidden
Err http://archive.ubuntu.com saucy-updates/multiverse i386 Packages
  403  Forbidden
Ign http://archive.ubuntu.com saucy-updates/main Translation-en_US
Ign http://archive.ubuntu.com saucy-updates/main Translation-en
Ign http://archive.ubuntu.com saucy-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com saucy-updates/multiverse Translation-en
Ign http://archive.ubuntu.com saucy-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com saucy-updates/restricted Translation-en
Ign http://archive.ubuntu.com saucy-updates/universe Translation-en_US
Ign http://archive.ubuntu.com saucy-updates/universe Translation-en
Err http://archive.ubuntu.com saucy-backports/main Sources
  403  Forbidden
Err http://archive.ubuntu.com saucy-backports/restricted Sources
  403  Forbidden
Err http://archive.ubuntu.com saucy-backports/universe Sources
  403  Forbidden
Err http://archive.ubuntu.com saucy-backports/multiverse Sources
  403  Forbidden
Err http://archive.ubuntu.com saucy-backports/main amd64 Packages
  403  Forbidden
Err http://archive.ubuntu.com saucy-backports/restricted amd64 Packages
  403  Forbidden
Err http://archive.ubuntu.com saucy-backports/universe amd64 Packages
  403  Forbidden
Err http://archive.ubuntu.com saucy-backports/multiverse amd64 Packages
  403  Forbidden
Err http://archive.ubuntu.com saucy-backports/main i386 Packages
  403  Forbidden
Err http://archive.ubuntu.com saucy-backports/restricted i386 Packages
  403  Forbidden
Err http://archive.ubuntu.com saucy-backports/universe i386 Packages
  403  Forbidden
Err http://archive.ubuntu.com saucy-backports/multiverse i386 Packages
  403  Forbidden
Ign http://archive.ubuntu.com saucy-backports/main Translation-en_US
Ign http://archive.ubuntu.com saucy-backports/main Translation-en
Ign http://archive.ubuntu.com saucy-backports/multiverse Translation-en_US
Ign http://archive.ubuntu.com saucy-backports/multiverse Translation-en
Ign http://archive.ubuntu.com saucy-backports/restricted Translation-en_US
Ign http://archive.ubuntu.com saucy-backports/restricted Translation-en
Ign http://archive.ubuntu.com saucy-backports/universe Translation-en_US
Ign http://archive.ubuntu.com saucy-backports/universe Translation-en
Err http://archive.ubuntu.com saucy-security/main Sources
  403  Forbidden
Err http://archive.ubuntu.com saucy-security/restricted Sources
  403  Forbidden
Err http://archive.ubuntu.com saucy-security/universe Sources
  403  Forbidden
Err http://archive.ubuntu.com saucy-security/multiverse Sources
  403  Forbidden
Err http://archive.ubuntu.com saucy-security/main amd64 Packages
  403  Forbidden
Err http://archive.ubuntu.com saucy-security/restricted amd64 Packages
  403  Forbidden
Err http://archive.ubuntu.com saucy-security/universe amd64 Packages
  403  Forbidden
Err http://archive.ubuntu.com saucy-security/multiverse amd64 Packages
  403  Forbidden
Err http://archive.ubuntu.com saucy-security/main i386 Packages
  403  Forbidden
Err http://archive.ubuntu.com saucy-security/restricted i386 Packages
  403  Forbidden
Err http://archive.ubuntu.com saucy-security/universe i386 Packages
  403  Forbidden
Err http://archive.ubuntu.com saucy-security/multiverse i386 Packages
  403  Forbidden
Ign http://archive.ubuntu.com saucy-security/main Translation-en_US
Ign http://archive.ubuntu.com saucy-security/main Translation-en
Ign http://archive.ubuntu.com saucy-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com saucy-security/multiverse Translation-en
Ign http://archive.ubuntu.com saucy-security/restricted Translation-en_US
Ign http://archive.ubuntu.com saucy-security/restricted Translation-en
Ign http://archive.ubuntu.com saucy-security/universe Translation-en_US
Ign http://archive.ubuntu.com saucy-security/universe Translation-en
Err http://archive.ubuntu.com saucy-proposed/universe amd64 Packages
  403  Forbidden
Err http://archive.ubuntu.com saucy-proposed/multiverse amd64 Packages
  403  Forbidden
Err http://archive.ubuntu.com saucy-proposed/restricted amd64 Packages
  403  Forbidden
Err http://archive.ubuntu.com saucy-proposed/main amd64 Packages
  403  Forbidden
Err http://archive.ubuntu.com saucy-proposed/universe i386 Packages
  403  Forbidden
Err http://archive.ubuntu.com saucy-proposed/multiverse i386 Packages
  403  Forbidden
Err http://archive.ubuntu.com saucy-proposed/restricted i386 Packages
  403  Forbidden
Err http://archive.ubuntu.com saucy-proposed/main i386 Packages
  403  Forbidden
Ign http://archive.ubuntu.com saucy-proposed/main Translation-en_US
Ign http://archive.ubuntu.com saucy-proposed/main Translation-en
Ign http://archive.ubuntu.com saucy-proposed/multiverse Translation-en_US
Ign http://archive.ubuntu.com saucy-proposed/multiverse Translation-en
Ign http://archive.ubuntu.com saucy-proposed/restricted Translation-en_US
Ign http://archive.ubuntu.com saucy-proposed/restricted Translation-en
Ign http://archive.ubuntu.com saucy-proposed/universe Translation-en_US
Ign http://archive.ubuntu.com saucy-proposed/universe Translation-en
W: Failed to fetch http://download.mendeley.com/apt/dists/stable/main/binary-amd64/Packages  403  Forbidden


W: Failed to fetch http://download.mendeley.com/apt/dists/stable/main/binary-i386/Packages  403  Forbidden


W: Failed to fetch http://deb.opera.com/opera/dists/stable/non-free/binary-amd64/Packages  403  Forbidden


W: Failed to fetch http://deb.opera.com/opera/dists/stable/non-free/binary-i386/Packages  403  Forbidden


W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/saucy/main/source/Sources  403  Forbidden


W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/saucy/main/binary-amd64/Packages  403  Forbidden


W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/saucy/main/binary-i386/Packages  403  Forbidden


W: Failed to fetch http://archive.canonical.com/ubuntu/dists/saucy/partner/source/Sources  403  Forbidden


W: Failed to fetch http://archive.canonical.com/ubuntu/dists/saucy/partner/binary-amd64/Packages  403  Forbidden


W: Failed to fetch http://archive.canonical.com/ubuntu/dists/saucy/partner/binary-i386/Packages  403  Forbidden


W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/main/binary-amd64/Packages  403  Forbidden


W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/main/binary-i386/Packages  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy/main/source/Sources  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy/restricted/source/Sources  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy/universe/source/Sources  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy/multiverse/source/Sources  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy/main/binary-amd64/Packages  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy/restricted/binary-amd64/Packages  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy/universe/binary-amd64/Packages  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy/multiverse/binary-amd64/Packages  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy/main/binary-i386/Packages  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy/restricted/binary-i386/Packages  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy/universe/binary-i386/Packages  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy/multiverse/binary-i386/Packages  403  Forbidden


W: Failed to fetch http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/saucy/main/binary-amd64/Packages  403  Forbidden


W: Failed to fetch http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/saucy/main/binary-i386/Packages  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-updates/main/source/Sources  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-updates/restricted/source/Sources  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-updates/universe/source/Sources  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-updates/multiverse/source/Sources  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-updates/main/binary-amd64/Packages  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-updates/restricted/binary-amd64/Packages  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-updates/universe/binary-amd64/Packages  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-updates/multiverse/binary-amd64/Packages  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-updates/main/binary-i386/Packages  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-updates/restricted/binary-i386/Packages  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-updates/universe/binary-i386/Packages  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-updates/multiverse/binary-i386/Packages  403  Forbidden


W: Failed to fetch http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/dists/saucy/main/binary-amd64/Packages  403  Forbidden


W: Failed to fetch http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/dists/saucy/main/binary-i386/Packages  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-backports/main/source/Sources  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-backports/restricted/source/Sources  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-backports/universe/source/Sources  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-backports/multiverse/source/Sources  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-backports/main/binary-amd64/Packages  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-backports/restricted/binary-amd64/Packages  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-backports/universe/binary-amd64/Packages  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-backports/multiverse/binary-amd64/Packages  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-backports/main/binary-i386/Packages  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-backports/restricted/binary-i386/Packages  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-backports/universe/binary-i386/Packages  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-backports/multiverse/binary-i386/Packages  403  Forbidden


W: Failed to fetch http://ppa.launchpad.net/keks9n/skypetab/ubuntu/dists/saucy/main/binary-amd64/Packages  403  Forbidden


W: Failed to fetch http://ppa.launchpad.net/keks9n/skypetab/ubuntu/dists/saucy/main/binary-i386/Packages  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-security/main/source/Sources  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-security/restricted/source/Sources  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-security/universe/source/Sources  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-security/multiverse/source/Sources  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-security/main/binary-amd64/Packages  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-security/restricted/binary-amd64/Packages  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-security/universe/binary-amd64/Packages  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-security/multiverse/binary-amd64/Packages  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-security/main/binary-i386/Packages  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-security/restricted/binary-i386/Packages  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-security/universe/binary-i386/Packages  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-security/multiverse/binary-i386/Packages  403  Forbidden


W: Failed to fetch http://ppa.launchpad.net/libreoffice/ppa/ubuntu/dists/saucy/main/binary-amd64/Packages  403  Forbidden


W: Failed to fetch http://ppa.launchpad.net/libreoffice/ppa/ubuntu/dists/saucy/main/binary-i386/Packages  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-proposed/universe/binary-amd64/Packages  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-proposed/multiverse/binary-amd64/Packages  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-proposed/restricted/binary-amd64/Packages  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-proposed/main/binary-amd64/Packages  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-proposed/universe/binary-i386/Packages  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-proposed/multiverse/binary-i386/Packages  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-proposed/restricted/binary-i386/Packages  403  Forbidden


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-proposed/main/binary-i386/Packages  403  Forbidden


W: Failed to fetch http://ppa.launchpad.net/linrunner/tlp/ubuntu/dists/saucy/main/binary-amd64/Packages  403  Forbidden


W: Failed to fetch http://ppa.launchpad.net/linrunner/tlp/ubuntu/dists/saucy/main/binary-i386/Packages  403  Forbidden


W: Failed to fetch http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/dists/saucy/main/binary-amd64/Packages  403  Forbidden


W: Failed to fetch http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/dists/saucy/main/binary-i386/Packages  403  Forbidden


W: Failed to fetch http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/saucy/main/source/Sources  403  Forbidden


W: Failed to fetch http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/saucy/main/binary-amd64/Packages  403  Forbidden


W: Failed to fetch http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/saucy/main/binary-i386/Packages  403  Forbidden


W: Failed to fetch http://ppa.launchpad.net/snwh/moka-gtk-theme-daily/ubuntu/dists/saucy/main/binary-amd64/Packages  403  Forbidden


W: Failed to fetch http://ppa.launchpad.net/snwh/moka-gtk-theme-daily/ubuntu/dists/saucy/main/binary-i386/Packages  403  Forbidden


E: Some index files failed to download. They have been ignored, or old ones used instead.



```

And here is the result of second command..... 

sudo do-release-upgrade
Checking for a new Ubuntu release
No new release found

---

### Post by susicox143 on 2014-05-02
> **grahammechanical said:**
> How do you know that the upgrade has not been successful? What are you expecting to see that you are not seeing?

Because i don't see running of any upgrade or update process. After running few seconds update manager says your computer is up to date. But actually it is not...

---

### Post by ibjsb4 on 2014-05-02
> **slickymaster said:**
> Do you have any added extra PPAs on your Software-Sources? If so, disable them

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

---

### Post by aysiu on 2014-05-02
Can you paste this command in? ```
sudo apt-get update && sudo do-release-upgrade -d
```

---

### Post by susicox143 on 2014-05-02
> **aysiu said:**
> Can you paste this command in? ```
sudo apt-get update && sudo do-release-upgrade -d
```

Here is the result for your command.....

```
Err http://archive.ubuntu.com saucy InRelease                                    
Err http://archive.ubuntu.com saucy-updates InRelease                          
  
Err http://archive.ubuntu.com saucy-backports InRelease                        
  
Err http://archive.ubuntu.com saucy-security InRelease                         
  
Err http://archive.ubuntu.com saucy-proposed InRelease                         
  
Err http://archive.ubuntu.com saucy Release.gpg                                
  Unable to connect to 93.118.78.204:8800:
Err http://archive.ubuntu.com saucy-updates Release.gpg                        
  Unable to connect to 93.118.78.204:8800:
Err http://archive.ubuntu.com saucy-backports Release.gpg                      
  Unable to connect to 93.118.78.204:8800:
Err http://archive.ubuntu.com saucy-security Release.gpg                       
  Unable to connect to 93.118.78.204:8800:
Err http://archive.ubuntu.com saucy-proposed Release.gpg                       
  Unable to connect to 93.118.78.204:8800:
Err http://archive.canonical.com saucy InRelease                               
  
Err http://ppa.launchpad.net saucy InRelease                                   
  
Err http://ppa.launchpad.net saucy InRelease                                   
  
Err http://ppa.launchpad.net saucy InRelease                                   
  
Err http://ppa.launchpad.net saucy InRelease                                   
  
Err http://ppa.launchpad.net saucy InRelease                                   
  
Err http://ppa.launchpad.net saucy InRelease                                   
  
Err http://ppa.launchpad.net saucy InRelease                                   
  
Err http://ppa.launchpad.net saucy InRelease                                   
  
Err http://archive.canonical.com saucy Release.gpg                             
  Unable to connect to 93.118.78.204:8800:
Err http://ppa.launchpad.net saucy Release.gpg                                 
  Unable to connect to 93.118.78.204:8800:
Err http://ppa.launchpad.net saucy Release.gpg                                 
  Unable to connect to 93.118.78.204:8800:
Err http://ppa.launchpad.net saucy Release.gpg                                 
  Unable to connect to 93.118.78.204:8800:
Err http://ppa.launchpad.net saucy Release.gpg                                 
  Unable to connect to 93.118.78.204:8800:
Err http://ppa.launchpad.net saucy Release.gpg                                 
  Unable to connect to 93.118.78.204:8800:
Err http://ppa.launchpad.net saucy Release.gpg                                 
  Unable to connect to 93.118.78.204:8800:
Err http://ppa.launchpad.net saucy Release.gpg                                 
  Unable to connect to 93.118.78.204:8800:
Err http://ppa.launchpad.net saucy Release.gpg                                 
  Unable to connect to 93.118.78.204:8800:
Err http://extras.ubuntu.com saucy InRelease                                   
  
Err http://deb.opera.com stable InRelease                                      
  
Err http://deb.opera.com stable Release.gpg                                    
  Unable to connect to 93.118.78.204:8800:
Err http://extras.ubuntu.com saucy Release.gpg                                 
  Unable to connect to 93.118.78.204:8800:
Err http://dl.google.com stable InRelease                                      
  
Err http://dl.google.com stable Release.gpg                                    
  Unable to connect to 93.118.78.204:8800:
Err http://download.mendeley.com stable InRelease
  
Err http://download.mendeley.com stable Release.gpg
  Unable to connect to 93.118.78.204:8800:
Reading package lists... Done
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy/InRelease  


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-updates/InRelease  


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-backports/InRelease  


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-security/InRelease  


W: Failed to fetch http://archive.canonical.com/ubuntu/dists/saucy/InRelease  


W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/saucy/InRelease  


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-proposed/InRelease  


W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/InRelease  


W: Failed to fetch http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/saucy/InRelease  


W: Failed to fetch http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/dists/saucy/InRelease  


W: Failed to fetch http://ppa.launchpad.net/keks9n/skypetab/ubuntu/dists/saucy/InRelease  


W: Failed to fetch http://ppa.launchpad.net/libreoffice/ppa/ubuntu/dists/saucy/InRelease  


W: Failed to fetch http://ppa.launchpad.net/linrunner/tlp/ubuntu/dists/saucy/InRelease  


W: Failed to fetch http://download.mendeley.com/apt/dists/stable/InRelease  


W: Failed to fetch http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/dists/saucy/InRelease  


W: Failed to fetch http://deb.opera.com/opera/dists/stable/InRelease  


W: Failed to fetch http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/saucy/InRelease  


W: Failed to fetch http://ppa.launchpad.net/snwh/moka-gtk-theme-daily/ubuntu/dists/saucy/InRelease  


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-updates/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-backports/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-security/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-proposed/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://archive.canonical.com/ubuntu/dists/saucy/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/saucy/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/dists/saucy/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://ppa.launchpad.net/keks9n/skypetab/ubuntu/dists/saucy/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://ppa.launchpad.net/libreoffice/ppa/ubuntu/dists/saucy/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://ppa.launchpad.net/linrunner/tlp/ubuntu/dists/saucy/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/dists/saucy/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/saucy/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://ppa.launchpad.net/snwh/moka-gtk-theme-daily/ubuntu/dists/saucy/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/saucy/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://deb.opera.com/opera/dists/stable/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://download.mendeley.com/apt/dists/stable/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Some index files failed to download. They have been ignored, or old ones used instead.
Checking for a new Ubuntu release
No new release found



```

---

### Post by aysiu on 2014-05-02
Looks as if your internet connection is failing.

---

### Post by enzideout on 2014-05-02
Yeah, it looks like you are connected through a proxy. It isn't letting you get out to check for updates. Is there any way you can bypass it?

---

### Post by susicox143 on 2014-05-14
> **slickymaster said:**
> Do you have any added extra PPAs on your Software-Sources? If so, disable them and then run```
sudo apt-get update && sudo apt-get dist-upgrade
sudo do-release-upgrade
```

Hi Slicky, i tried your lines and got this result.... I am really worried why i can't update to latest Ubuntu.. I connected with LAN and there is no proxy or any thing. I don't know what is the problem.... 
```


atif@age-ubuntu:~$ sudo apt-get update && sudo apt-get dist-upgrade
[sudo] password for atif: 
Err http://archive.canonical.com saucy InRelease                               
  
Err http://dl.google.com stable InRelease                                      
  
Err http://archive.canonical.com saucy Release.gpg                             
  Unable to connect to 93.118.78.204:8800:
Err http://dl.google.com stable Release.gpg                                    
  Unable to connect to 93.118.78.204:8800:
Err http://deb.opera.com stable InRelease                                      
  
Err http://deb.opera.com stable Release.gpg                                    
  Unable to connect to 93.118.78.204:8800:
Err http://mirror-cybernet.lums.edu.pk saucy InRelease                         
  
Err http://ppa.launchpad.net saucy InRelease                                   
  
Err http://ppa.launchpad.net saucy InRelease                                   
  
Err http://ppa.launchpad.net saucy InRelease                                   
  
Err http://ppa.launchpad.net saucy InRelease                                   
  
Err http://mirror-cybernet.lums.edu.pk saucy-updates InRelease                 
  
Err http://mirror-cybernet.lums.edu.pk saucy-backports InRelease               
  
Err http://mirror-cybernet.lums.edu.pk saucy-security InRelease                
  
Err http://ppa.launchpad.net saucy InRelease                                   
  
Err http://ppa.launchpad.net saucy InRelease                                   
  
Err http://ppa.launchpad.net saucy InRelease                                   
  
Err http://ppa.launchpad.net saucy InRelease                                   
  
Err http://mirror-cybernet.lums.edu.pk saucy Release.gpg                       
  Unable to connect to 93.118.78.204:8800:
Err http://mirror-cybernet.lums.edu.pk saucy-updates Release.gpg               
  Unable to connect to 93.118.78.204:8800:
Err http://mirror-cybernet.lums.edu.pk saucy-backports Release.gpg             
  Unable to connect to 93.118.78.204:8800:
Err http://ppa.launchpad.net saucy Release.gpg                                 
  Unable to connect to 93.118.78.204:8800:
Err http://ppa.launchpad.net saucy Release.gpg                                 
  Unable to connect to 93.118.78.204:8800:
Err http://ppa.launchpad.net saucy Release.gpg                                 
  Unable to connect to 93.118.78.204:8800:
Err http://ppa.launchpad.net saucy Release.gpg                                 
  Unable to connect to 93.118.78.204:8800:
Err http://ppa.launchpad.net saucy Release.gpg                                 
  Unable to connect to 93.118.78.204:8800:
Err http://ppa.launchpad.net saucy Release.gpg                                 
  Unable to connect to 93.118.78.204:8800:
Err http://ppa.launchpad.net saucy Release.gpg                                 
  Unable to connect to 93.118.78.204:8800:
Err http://mirror-cybernet.lums.edu.pk saucy-security Release.gpg              
  Unable to connect to 93.118.78.204:8800:
Err http://ppa.launchpad.net saucy Release.gpg                                 
  Unable to connect to 93.118.78.204:8800:
Err http://extras.ubuntu.com saucy InRelease                                   
  
Err http://download.mendeley.com stable InRelease                              
  
Err http://extras.ubuntu.com saucy Release.gpg  
  Unable to connect to 93.118.78.204:8800:
Err http://download.mendeley.com stable Release.gpg
  Unable to connect to 93.118.78.204:8800:
Reading package lists... Done
W: Failed to fetch http://mirror-cybernet.lums.edu.pk/pub/ubuntu/dists/saucy/InRelease  


W: Failed to fetch http://mirror-cybernet.lums.edu.pk/pub/ubuntu/dists/saucy-updates/InRelease  


W: Failed to fetch http://mirror-cybernet.lums.edu.pk/pub/ubuntu/dists/saucy-backports/InRelease  


W: Failed to fetch http://mirror-cybernet.lums.edu.pk/pub/ubuntu/dists/saucy-security/InRelease  


W: Failed to fetch http://archive.canonical.com/ubuntu/dists/saucy/InRelease  


W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/saucy/InRelease  


W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/InRelease  


W: Failed to fetch http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/saucy/InRelease  


W: Failed to fetch http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/dists/saucy/InRelease  


W: Failed to fetch http://ppa.launchpad.net/keks9n/skypetab/ubuntu/dists/saucy/InRelease  


W: Failed to fetch http://ppa.launchpad.net/libreoffice/ppa/ubuntu/dists/saucy/InRelease  


W: Failed to fetch http://ppa.launchpad.net/linrunner/tlp/ubuntu/dists/saucy/InRelease  


W: Failed to fetch http://download.mendeley.com/apt/dists/stable/InRelease  


W: Failed to fetch http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/dists/saucy/InRelease  


W: Failed to fetch http://deb.opera.com/opera/dists/stable/InRelease  


W: Failed to fetch http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/saucy/InRelease  


W: Failed to fetch http://ppa.launchpad.net/snwh/moka-gtk-theme-daily/ubuntu/dists/saucy/InRelease  


W: Failed to fetch http://archive.canonical.com/ubuntu/dists/saucy/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://deb.opera.com/opera/dists/stable/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://mirror-cybernet.lums.edu.pk/pub/ubuntu/dists/saucy/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/saucy/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/dists/saucy/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://ppa.launchpad.net/keks9n/skypetab/ubuntu/dists/saucy/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://ppa.launchpad.net/libreoffice/ppa/ubuntu/dists/saucy/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://mirror-cybernet.lums.edu.pk/pub/ubuntu/dists/saucy-updates/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://mirror-cybernet.lums.edu.pk/pub/ubuntu/dists/saucy-backports/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://mirror-cybernet.lums.edu.pk/pub/ubuntu/dists/saucy-security/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://ppa.launchpad.net/linrunner/tlp/ubuntu/dists/saucy/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/dists/saucy/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/saucy/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://ppa.launchpad.net/snwh/moka-gtk-theme-daily/ubuntu/dists/saucy/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/saucy/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://download.mendeley.com/apt/dists/stable/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Some index files failed to download. They have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
atif@age-ubuntu:~$ ^C
atif@age-ubuntu:~$ sudo do-release-upgrade
Checking for a new Ubuntu release
No new release found
atif@age-ubuntu:~$ sudo do-release-upgrade
Checking for a new Ubuntu release
No new release found
atif@age-ubuntu:~$ 



```

---

### Post by aysiu on 2014-05-14
It's not really an issue or upgrading or not. The issue here is you are not able to reach the software repositories.

See this earlier post:
[http://ubuntuforums.org/showthread.php?t=2220720&p=13010852&viewfull=1#post13010852](http://ubuntuforums.org/showthread.php?t=2220720&p=13010852&viewfull=1#post13010852)

---

### Post by slickymaster on 2014-05-14
> **susicox143 said:**
> <...snip...>```

atif@age-ubuntu:~$ sudo apt-get update && sudo apt-get dist-upgrade
[sudo] password for atif: 
Err [http://archive.canonical.com](http://archive.canonical.com) saucy InRelease                               
  
Err [http://dl.google.com](http://dl.google.com) stable InRelease                                      
  
Err [http://archive.canonical.com](http://archive.canonical.com) saucy Release.gpg                             
  Unable to connect to 93.118.78.204:8800:
Err [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
  Unable to connect to 93.118.78.204:8800:
Err [http://deb.opera.com](http://deb.opera.com) stable InRelease                                      
  
Err [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                    
  Unable to connect to 93.118.78.204:8800:
Err [http://mirror-cybernet.lums.edu.pk](http://mirror-cybernet.lums.edu.pk) saucy InRelease                         
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy InRelease                                   
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy InRelease                                   
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy InRelease                                   
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy InRelease                                   
  
Err [http://mirror-cybernet.lums.edu.pk](http://mirror-cybernet.lums.edu.pk) saucy-updates InRelease                 
  
Err [http://mirror-cybernet.lums.edu.pk](http://mirror-cybernet.lums.edu.pk) saucy-backports InRelease               
  
Err [http://mirror-cybernet.lums.edu.pk](http://mirror-cybernet.lums.edu.pk) saucy-security InRelease                
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy InRelease                                   
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy InRelease                                   
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy InRelease                                   
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy InRelease                                   
  
Err [http://mirror-cybernet.lums.edu.pk](http://mirror-cybernet.lums.edu.pk) saucy Release.gpg                       
  Unable to connect to 93.118.78.204:8800:
Err [http://mirror-cybernet.lums.edu.pk](http://mirror-cybernet.lums.edu.pk) saucy-updates Release.gpg               
  Unable to connect to 93.118.78.204:8800:
Err [http://mirror-cybernet.lums.edu.pk](http://mirror-cybernet.lums.edu.pk) saucy-backports Release.gpg             
  Unable to connect to 93.118.78.204:8800:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg                                 
  Unable to connect to 93.118.78.204:8800:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg                                 
  Unable to connect to 93.118.78.204:8800:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg                                 
  Unable to connect to 93.118.78.204:8800:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg                                 
  Unable to connect to 93.118.78.204:8800:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg                                 
  Unable to connect to 93.118.78.204:8800:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg                                 
  Unable to connect to 93.118.78.204:8800:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg                                 
  Unable to connect to 93.118.78.204:8800:
Err [http://mirror-cybernet.lums.edu.pk](http://mirror-cybernet.lums.edu.pk) saucy-security Release.gpg              
  Unable to connect to 93.118.78.204:8800:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg                                 
  Unable to connect to 93.118.78.204:8800:
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy InRelease                                   
  
Err [http://download.mendeley.com](http://download.mendeley.com) stable InRelease                              
  
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release.gpg  
  Unable to connect to 93.118.78.204:8800:
Err [http://download.mendeley.com](http://download.mendeley.com) stable Release.gpg
  Unable to connect to 93.118.78.204:8800:
Reading package lists... Done
W: Failed to fetch [http://mirror-cybernet.lums.edu.pk/pub/ubuntu/dists/saucy/InRelease](http://mirror-cybernet.lums.edu.pk/pub/ubuntu/dists/saucy/InRelease)  


W: Failed to fetch [http://mirror-cybernet.lums.edu.pk/pub/ubuntu/dists/saucy-updates/InRelease](http://mirror-cybernet.lums.edu.pk/pub/ubuntu/dists/saucy-updates/InRelease)  


W: Failed to fetch [http://mirror-cybernet.lums.edu.pk/pub/ubuntu/dists/saucy-backports/InRelease](http://mirror-cybernet.lums.edu.pk/pub/ubuntu/dists/saucy-backports/InRelease)  


W: Failed to fetch [http://mirror-cybernet.lums.edu.pk/pub/ubuntu/dists/saucy-security/InRelease](http://mirror-cybernet.lums.edu.pk/pub/ubuntu/dists/saucy-security/InRelease)  


W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/saucy/InRelease](http://archive.canonical.com/ubuntu/dists/saucy/InRelease)  


W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/saucy/InRelease](http://extras.ubuntu.com/ubuntu/dists/saucy/InRelease)  


W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/InRelease](http://dl.google.com/linux/chrome/deb/dists/stable/InRelease)  


W: Failed to fetch [http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/saucy/InRelease](http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/saucy/InRelease)  


W: Failed to fetch [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/dists/saucy/InRelease](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/dists/saucy/InRelease)  


W: Failed to fetch [http://ppa.launchpad.net/keks9n/skypetab/ubuntu/dists/saucy/InRelease](http://ppa.launchpad.net/keks9n/skypetab/ubuntu/dists/saucy/InRelease)  


W: Failed to fetch [http://ppa.launchpad.net/libreoffice/ppa/ubuntu/dists/saucy/InRelease](http://ppa.launchpad.net/libreoffice/ppa/ubuntu/dists/saucy/InRelease)  


W: Failed to fetch [http://ppa.launchpad.net/linrunner/tlp/ubuntu/dists/saucy/InRelease](http://ppa.launchpad.net/linrunner/tlp/ubuntu/dists/saucy/InRelease)  


W: Failed to fetch [http://download.mendeley.com/apt/dists/stable/InRelease](http://download.mendeley.com/apt/dists/stable/InRelease)  


W: Failed to fetch [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/dists/saucy/InRelease](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/dists/saucy/InRelease)  


W: Failed to fetch [http://deb.opera.com/opera/dists/stable/InRelease](http://deb.opera.com/opera/dists/stable/InRelease)  


W: Failed to fetch [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/saucy/InRelease](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/saucy/InRelease)  


W: Failed to fetch [http://ppa.launchpad.net/snwh/moka-gtk-theme-daily/ubuntu/dists/saucy/InRelease](http://ppa.launchpad.net/snwh/moka-gtk-theme-daily/ubuntu/dists/saucy/InRelease)  


W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/saucy/Release.gpg](http://archive.canonical.com/ubuntu/dists/saucy/Release.gpg)  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg](http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg)  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch [http://deb.opera.com/opera/dists/stable/Release.gpg](http://deb.opera.com/opera/dists/stable/Release.gpg)  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch [http://mirror-cybernet.lums.edu.pk/pub/ubuntu/dists/saucy/Release.gpg](http://mirror-cybernet.lums.edu.pk/pub/ubuntu/dists/saucy/Release.gpg)  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch [http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/saucy/Release.gpg](http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/saucy/Release.gpg)  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/dists/saucy/Release.gpg](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/dists/saucy/Release.gpg)  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch [http://ppa.launchpad.net/keks9n/skypetab/ubuntu/dists/saucy/Release.gpg](http://ppa.launchpad.net/keks9n/skypetab/ubuntu/dists/saucy/Release.gpg)  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch [http://ppa.launchpad.net/libreoffice/ppa/ubuntu/dists/saucy/Release.gpg](http://ppa.launchpad.net/libreoffice/ppa/ubuntu/dists/saucy/Release.gpg)  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch [http://mirror-cybernet.lums.edu.pk/pub/ubuntu/dists/saucy-updates/Release.gpg](http://mirror-cybernet.lums.edu.pk/pub/ubuntu/dists/saucy-updates/Release.gpg)  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch [http://mirror-cybernet.lums.edu.pk/pub/ubuntu/dists/saucy-backports/Release.gpg](http://mirror-cybernet.lums.edu.pk/pub/ubuntu/dists/saucy-backports/Release.gpg)  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch [http://mirror-cybernet.lums.edu.pk/pub/ubuntu/dists/saucy-security/Release.gpg](http://mirror-cybernet.lums.edu.pk/pub/ubuntu/dists/saucy-security/Release.gpg)  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch [http://ppa.launchpad.net/linrunner/tlp/ubuntu/dists/saucy/Release.gpg](http://ppa.launchpad.net/linrunner/tlp/ubuntu/dists/saucy/Release.gpg)  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/dists/saucy/Release.gpg](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/dists/saucy/Release.gpg)  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/saucy/Release.gpg](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/saucy/Release.gpg)  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch [http://ppa.launchpad.net/snwh/moka-gtk-theme-daily/ubuntu/dists/saucy/Release.gpg](http://ppa.launchpad.net/snwh/moka-gtk-theme-daily/ubuntu/dists/saucy/Release.gpg)  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/saucy/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/saucy/Release.gpg)  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch [http://download.mendeley.com/apt/dists/stable/Release.gpg](http://download.mendeley.com/apt/dists/stable/Release.gpg)  Unable to connect to 93.118.78.204:8800:


W: Some index files failed to download. They have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
atif@age-ubuntu:~$ ^C
atif@age-ubuntu:~$ sudo do-release-upgrade
Checking for a new Ubuntu release
No new release found
atif@age-ubuntu:~$ sudo do-release-upgrade
Checking for a new Ubuntu release
No new release found
atif@age-ubuntu:~$

```


aysiu is absolutely right. Your problem isn't with the upgrade *per si*, but with your connectivity. Looking at your code everything show us that you're behind a proxy which isn't allow you to reach the software repositories.

---

### Post by susicox143 on 2014-05-14
> **aysiu said:**
> Can you paste this command in? ```
sudo apt-get update && sudo do-release-upgrade -d
```


Hi Aysiu.... Here is the response of your command... It also does not work. I am very much worried about it. What to do know.. Because i connected to LAN and i made sure that i am connected to internet. I did pinging of yahoo..... 

```
atif@age-ubuntu:~$ sudo apt-get update && sudo do-release-upgrade -d[sudo] password for atif: 
Err http://ppa.launchpad.net saucy InRelease                                   
  
Err http://ppa.launchpad.net saucy InRelease                                   
  
Err http://ppa.launchpad.net saucy InRelease                                   
  
Err http://ppa.launchpad.net saucy InRelease                                   
  
Err http://ppa.launchpad.net saucy InRelease                                   
  
Err http://ppa.launchpad.net saucy InRelease                                   
  
Err http://ppa.launchpad.net saucy InRelease                                   
  
Err http://ppa.launchpad.net saucy InRelease                                   
  
Err http://ppa.launchpad.net saucy Release.gpg                                 
  Unable to connect to 93.118.78.204:8800:
Err http://ppa.launchpad.net saucy Release.gpg                                 
  Unable to connect to 93.118.78.204:8800:
Err http://ppa.launchpad.net saucy Release.gpg                                 
  Unable to connect to 93.118.78.204:8800:
Err http://ppa.launchpad.net saucy Release.gpg                                 
  Unable to connect to 93.118.78.204:8800:
Err http://ppa.launchpad.net saucy Release.gpg                                 
  Unable to connect to 93.118.78.204:8800:
Err http://ppa.launchpad.net saucy Release.gpg                                 
  Unable to connect to 93.118.78.204:8800:
Err http://ppa.launchpad.net saucy Release.gpg                                 
  Unable to connect to 93.118.78.204:8800:
Err http://ppa.launchpad.net saucy Release.gpg                                 
  Unable to connect to 93.118.78.204:8800:
Err http://deb.opera.com stable InRelease                                      
  
Err http://mirror-cybernet.lums.edu.pk saucy InRelease                         
  
Err http://mirror-cybernet.lums.edu.pk saucy-updates InRelease                 
  
Err http://mirror-cybernet.lums.edu.pk saucy-backports InRelease               
  
Err http://mirror-cybernet.lums.edu.pk saucy-security InRelease                
  
Err http://mirror-cybernet.lums.edu.pk saucy Release.gpg                       
  Unable to connect to 93.118.78.204:8800:
Err http://mirror-cybernet.lums.edu.pk saucy-updates Release.gpg               
  Unable to connect to 93.118.78.204:8800:
Err http://mirror-cybernet.lums.edu.pk saucy-backports Release.gpg             
  Unable to connect to 93.118.78.204:8800:
Err http://deb.opera.com stable Release.gpg                                    
  Unable to connect to 93.118.78.204:8800:
Err http://mirror-cybernet.lums.edu.pk saucy-security Release.gpg              
  Unable to connect to 93.118.78.204:8800:
Err http://dl.google.com stable InRelease                                      
  
Err http://download.mendeley.com stable InRelease                              
  
Err http://download.mendeley.com stable Release.gpg                            
  Unable to connect to 93.118.78.204:8800:
Err http://dl.google.com stable Release.gpg                                    
  Unable to connect to 93.118.78.204:8800:
Err http://archive.canonical.com saucy InRelease                               
  
Err http://extras.ubuntu.com saucy InRelease                                   
  
Err http://archive.canonical.com saucy Release.gpg                             
  Unable to connect to 93.118.78.204:8800:
Err http://extras.ubuntu.com saucy Release.gpg
  Unable to connect to 93.118.78.204:8800:
Reading package lists... Done
W: Failed to fetch http://mirror-cybernet.lums.edu.pk/pub/ubuntu/dists/saucy/InRelease  


W: Failed to fetch http://mirror-cybernet.lums.edu.pk/pub/ubuntu/dists/saucy-updates/InRelease  


W: Failed to fetch http://mirror-cybernet.lums.edu.pk/pub/ubuntu/dists/saucy-backports/InRelease  


W: Failed to fetch http://mirror-cybernet.lums.edu.pk/pub/ubuntu/dists/saucy-security/InRelease  


W: Failed to fetch http://archive.canonical.com/ubuntu/dists/saucy/InRelease  


W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/saucy/InRelease  


W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/InRelease  


W: Failed to fetch http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/saucy/InRelease  


W: Failed to fetch http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/dists/saucy/InRelease  


W: Failed to fetch http://ppa.launchpad.net/keks9n/skypetab/ubuntu/dists/saucy/InRelease  


W: Failed to fetch http://ppa.launchpad.net/libreoffice/ppa/ubuntu/dists/saucy/InRelease  


W: Failed to fetch http://ppa.launchpad.net/linrunner/tlp/ubuntu/dists/saucy/InRelease  


W: Failed to fetch http://download.mendeley.com/apt/dists/stable/InRelease  


W: Failed to fetch http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/dists/saucy/InRelease  


W: Failed to fetch http://deb.opera.com/opera/dists/stable/InRelease  


W: Failed to fetch http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/saucy/InRelease  


W: Failed to fetch http://ppa.launchpad.net/snwh/moka-gtk-theme-daily/ubuntu/dists/saucy/InRelease  


W: Failed to fetch http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/saucy/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/dists/saucy/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://ppa.launchpad.net/keks9n/skypetab/ubuntu/dists/saucy/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://ppa.launchpad.net/libreoffice/ppa/ubuntu/dists/saucy/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://ppa.launchpad.net/linrunner/tlp/ubuntu/dists/saucy/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/dists/saucy/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/saucy/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://ppa.launchpad.net/snwh/moka-gtk-theme-daily/ubuntu/dists/saucy/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://deb.opera.com/opera/dists/stable/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://mirror-cybernet.lums.edu.pk/pub/ubuntu/dists/saucy/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://mirror-cybernet.lums.edu.pk/pub/ubuntu/dists/saucy-updates/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://mirror-cybernet.lums.edu.pk/pub/ubuntu/dists/saucy-backports/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://mirror-cybernet.lums.edu.pk/pub/ubuntu/dists/saucy-security/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://download.mendeley.com/apt/dists/stable/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://archive.canonical.com/ubuntu/dists/saucy/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/saucy/Release.gpg  Unable to connect to 93.118.78.204:8800:


W: Some index files failed to download. They have been ignored, or old ones used instead.
Checking for a new Ubuntu release
No new release found
atif@age-ubuntu:~$ 



```

---

### Post by susicox143 on 2014-05-14
But i tried ping yahoo.com and it seems it is working... ping yahoo.com is giving me response.... And i just figured out that in ubuntu software center when i try to download something is see this "use this source" instead of install.... So you guys are right that is some problem with software repositories. Now you can you guide me what can i do... i don't see any proxies. It is just direct internet connection without any proxies......

---

### Post by susicox143 on 2014-05-14
I see ping command hang if i ping this ip   93.118.78.204 ... i think it is software repository ip....

---

### Post by slickymaster on 2014-05-14
> **susicox143 said:**
> I see ping command hang if i ping this ip   93.118.78.204 ... i think it is software repository ip....

No that's not. That's the proxy IP.

---

### Post by susicox143 on 2014-05-14
****.... how to i trace it where is it hidden.... [COLOR=#000000]*93.118.78.20  Because i don't see it anywhere in my network setting....*[/COLOR]

---

### Post by susicox143 on 2014-05-14
Thanks guys. i think it begin to work but i don't know where that proxy was hidden.... I shall be greatfull if can tell me the pin points where proxies setuped...

---

### Post by slickymaster on 2014-05-14
The proxy settings are saved into the **/etc/apt/apt.conf** file.

---

### Post by susicox143 on 2014-05-17
Now i am getting this error on update manager...................    [h=3][**Could not determine the upgrade**]("http://askubuntu.com/questions/449374/could-not-determine-the-upgrade")[/h]
I don't understand why is it... I have tried all the solution on google search but not a single solve my problem... Now what can i do......????????????????????

---

### Post by slickymaster on 2014-05-18
Can you please run the following commands in a terminal and copy/past here the entire output you get when you run them.

```
sudo apt-get update && sudo apt-get upgrade && sudo do-release-upgrade
```
```
cat /var/log/dist-upgrade/main.log | grep Obsolete
```

---

### Post by susicox143 on 2014-05-18
```
sudo apt-get update && sudo apt-get upgrade && sudo do-release-upgrade
```

Here is the output of above command.... 

```
Err http://archive.ubuntu.com saucy/multiverse Translation-en_US                                                                                              
Err http://archive.ubuntu.com saucy/restricted Translation-en_US               
                                                                               
Err http://archive.ubuntu.com saucy/universe Translation-en_US                 
                                                                               
Err http://archive.ubuntu.com saucy-updates/main Translation-en_US             
                                                                               
Err http://archive.ubuntu.com saucy-updates/multiverse Translation-en_US       
                                                                               
Err http://archive.ubuntu.com saucy-updates/restricted Translation-en_US       
                                                                               
Err http://archive.ubuntu.com saucy-updates/universe Translation-en_US         
                                                                               
Err http://archive.ubuntu.com saucy-backports/main Translation-en_US           
                                                                               
Err http://archive.ubuntu.com saucy-backports/multiverse Translation-en_US     
                                                                               
Err http://archive.ubuntu.com saucy-backports/restricted Translation-en_US     
                                                                               
Err http://archive.ubuntu.com saucy-backports/universe Translation-en_US       
                                                                               
Err http://archive.ubuntu.com saucy-security/main Translation-en_US            
                                                                               
Err http://archive.ubuntu.com saucy-security/multiverse Translation-en_US      
                                                                               
Err http://archive.ubuntu.com saucy-security/restricted Translation-en_US      
                                                                               
Err http://archive.ubuntu.com saucy-security/universe Translation-en_US        
                                                                               
Err http://archive.ubuntu.com saucy-proposed/main Translation-en_US            
                                                                               
Err http://archive.ubuntu.com saucy-proposed/multiverse Translation-en_US      
                                                                               
Err http://archive.ubuntu.com saucy-proposed/restricted Translation-en_US      
                                                                               
Err http://archive.ubuntu.com saucy-proposed/universe Translation-en_US        
                                                                               
Err http://archive.ubuntu.com saucy/main Translation-en_US                     
                                                                               
Err http://archive.ubuntu.com saucy/multiverse Translation-en_US               
                                                                               
Err http://archive.ubuntu.com saucy/restricted Translation-en_US               
                                                                               
Err http://archive.ubuntu.com saucy/universe Translation-en_US                 
                                                                               
Err http://archive.ubuntu.com saucy-updates/main Translation-en_US             
                                                                               
Err http://archive.ubuntu.com saucy-updates/multiverse Translation-en_US       
                                                                               
Err http://archive.ubuntu.com saucy-updates/restricted Translation-en_US       
                                                                               
Err http://archive.ubuntu.com saucy-updates/universe Translation-en_US         
                                                                               
Err http://archive.ubuntu.com saucy-backports/main Translation-en_US           
                                                                               
Err http://archive.ubuntu.com saucy-backports/multiverse Translation-en_US     
                                                                               
Err http://archive.ubuntu.com saucy-backports/restricted Translation-en_US     
                                                                               
Err http://archive.ubuntu.com saucy-backports/universe Translation-en_US       
                                                                               
Err http://archive.ubuntu.com saucy-security/main Translation-en_US            
                                                                               
Err http://archive.ubuntu.com saucy-security/multiverse Translation-en_US      
                                                                               
Err http://archive.ubuntu.com saucy-security/restricted Translation-en_US      
                                                                               
Err http://archive.ubuntu.com saucy-security/universe Translation-en_US        
                                                                               
Err http://archive.ubuntu.com saucy-proposed/main Translation-en_US            
                                                                               
Err http://archive.ubuntu.com saucy-proposed/multiverse Translation-en_US      
                                                                               
Err http://archive.ubuntu.com saucy-proposed/restricted Translation-en_US      
                                                                               
Err http://archive.ubuntu.com saucy-proposed/universe Translation-en_US        
                                                                               
Err http://archive.ubuntu.com saucy/main Translation-en_US                     
                                                                               
Err http://archive.ubuntu.com saucy/multiverse Translation-en_US               
                                                                               
Err http://archive.ubuntu.com saucy/restricted Translation-en_US               
                                                                               
Err http://archive.ubuntu.com saucy/universe Translation-en_US                 
                                                                               
Err http://archive.ubuntu.com saucy-updates/main Translation-en_US             
                                                                               
Err http://archive.ubuntu.com saucy-updates/multiverse Translation-en_US       
                                                                               
Err http://archive.ubuntu.com saucy-updates/restricted Translation-en_US       
                                                                               
Err http://archive.ubuntu.com saucy-updates/universe Translation-en_US         
                                                                               
Err http://archive.ubuntu.com saucy-backports/main Translation-en_US           
                                                                               
Err http://archive.ubuntu.com saucy-backports/multiverse Translation-en_US     
                                                                               
Err http://archive.ubuntu.com saucy-backports/restricted Translation-en_US     
                                                                               
Err http://archive.ubuntu.com saucy-backports/universe Translation-en_US       
                                                                               
Err http://archive.ubuntu.com saucy-security/main Translation-en_US            
                                                                               
Err http://archive.ubuntu.com saucy-security/multiverse Translation-en_US      
                                                                               
Err http://archive.ubuntu.com saucy-security/restricted Translation-en_US      
                                                                               
Err http://archive.ubuntu.com saucy-security/universe Translation-en_US        
                                                                               
Err http://archive.ubuntu.com saucy-proposed/main Translation-en_US            
                                                                               
Err http://archive.ubuntu.com saucy-proposed/multiverse Translation-en_US      
                                                                               
Err http://archive.ubuntu.com saucy-proposed/restricted Translation-en_US      
                                                                               
Err http://archive.ubuntu.com saucy-proposed/universe Translation-en_US        
                                                                               
Ign http://archive.ubuntu.com saucy/main Translation-en_US                     
Ign http://archive.ubuntu.com saucy/multiverse Translation-en_US               
Ign http://archive.ubuntu.com saucy/restricted Translation-en_US               
Ign http://archive.ubuntu.com saucy/universe Translation-en_US                 
Ign http://archive.ubuntu.com saucy-updates/main Translation-en_US             
Ign http://archive.ubuntu.com saucy-updates/multiverse Translation-en_US       
Ign http://archive.ubuntu.com saucy-updates/restricted Translation-en_US       
Ign http://archive.ubuntu.com saucy-updates/universe Translation-en_US         
Ign http://archive.ubuntu.com saucy-backports/main Translation-en_US           
Ign http://archive.ubuntu.com saucy-backports/multiverse Translation-en_US     
Ign http://archive.ubuntu.com saucy-backports/restricted Translation-en_US     
Ign http://archive.ubuntu.com saucy-backports/universe Translation-en_US       
Ign http://archive.ubuntu.com saucy-security/main Translation-en_US            
Ign http://archive.ubuntu.com saucy-security/multiverse Translation-en_US      
Ign http://archive.ubuntu.com saucy-security/restricted Translation-en_US      
Ign http://archive.ubuntu.com saucy-security/universe Translation-en_US        
Ign http://archive.ubuntu.com saucy-proposed/main Translation-en_US            
Ign http://archive.ubuntu.com saucy-proposed/multiverse Translation-en_US      
Ign http://archive.ubuntu.com saucy-proposed/restricted Translation-en_US      
Ign http://archive.ubuntu.com saucy-proposed/universe Translation-en_US        
Fetched 0 B in 6s (0 B/s)                                                      
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 


Updating repository information


Third party sources disabled 


Some third party entries in your sources.list were disabled. You can 
re-enable them after the upgrade with the 'software-properties' tool 
or your package manager. 


To continue please press [ENTER]


Ign http://archive.canonical.com trusty InRelease                              
Ign http://archive.ubuntu.com trusty InRelease                                 
Get:1 http://archive.canonical.com trusty Release.gpg [933 B]                  
Ign http://archive.ubuntu.com trusty-updates InRelease                         
Get:2 http://archive.canonical.com trusty Release [8,257 B]                    
Ign http://archive.ubuntu.com trusty-backports InRelease                       
Ign http://archive.ubuntu.com trusty-security InRelease                        
Get:3 http://archive.canonical.com trusty/partner Sources [1,888 B]            
Ign http://archive.ubuntu.com trusty-proposed InRelease                        
Get:4 http://archive.canonical.com trusty/partner amd64 Packages [2,199 B]     
Get:5 http://archive.ubuntu.com trusty Release.gpg [933 B]                     
Get:6 http://archive.ubuntu.com trusty-updates Release.gpg [933 B]             
Get:7 http://archive.canonical.com trusty/partner i386 Packages [3,159 B]      
Get:8 http://archive.ubuntu.com trusty-backports Release.gpg [933 B]           
Err http://archive.canonical.com trusty/partner Translation-en_US              
                                                                               
Get:9 http://archive.ubuntu.com trusty-security Release.gpg [933 B]            
Err http://archive.canonical.com trusty/partner Translation-en                 
                                                                               
Get:10 http://archive.ubuntu.com trusty-proposed Release.gpg [933 B]           
Err http://archive.canonical.com trusty/partner Translation-en_US              
                                                                               
Err http://archive.canonical.com trusty/partner Translation-en                 
                                                                               
Get:11 http://archive.ubuntu.com trusty Release [58.5 kB]                      
Err http://archive.canonical.com trusty/partner Translation-en_US              
                                                                               
Err http://archive.canonical.com trusty/partner Translation-en                 
                                                                               
Err http://archive.canonical.com trusty/partner Translation-en_US              
                                                                               
Err http://archive.canonical.com trusty/partner Translation-en                 
                                                                               
Ign http://archive.canonical.com trusty/partner Translation-en_US              
Ign http://archive.canonical.com trusty/partner Translation-en                 
Get:12 http://archive.ubuntu.com trusty-updates Release [58.5 kB]              
Get:13 http://archive.ubuntu.com trusty-backports Release [58.6 kB]            
Get:14 http://archive.ubuntu.com trusty-security Release [58.5 kB]             
Get:15 http://archive.ubuntu.com trusty-proposed Release [58.5 kB]             
Get:16 http://archive.ubuntu.com trusty/main Sources [1,064 kB]                
Get:17 http://archive.ubuntu.com trusty/restricted Sources [5,433 B]           
Get:18 http://archive.ubuntu.com trusty/universe Sources [6,399 kB]            
Get:19 http://archive.ubuntu.com trusty/multiverse Sources [174 kB]            
Get:20 http://archive.ubuntu.com trusty/main amd64 Packages [1,350 kB]         
Get:21 http://archive.ubuntu.com trusty/restricted amd64 Packages [13.0 kB]    
Get:22 http://archive.ubuntu.com trusty/universe amd64 Packages [5,859 kB]     
Get:23 http://archive.ubuntu.com trusty/multiverse amd64 Packages [132 kB]     
Get:24 http://archive.ubuntu.com trusty/main i386 Packages [1,348 kB]          
Get:25 http://archive.ubuntu.com trusty/restricted i386 Packages [13.4 kB]     
Get:26 http://archive.ubuntu.com trusty/universe i386 Packages [5,866 kB]      
Get:27 http://archive.ubuntu.com trusty/multiverse i386 Packages [134 kB]      
Err http://archive.ubuntu.com trusty/main Translation-en_US                    
                                                                               
Get:28 http://archive.ubuntu.com trusty/main Translation-en [762 kB]           
Err http://archive.ubuntu.com trusty/multiverse Translation-en_US              
                                                                               
Get:29 http://archive.ubuntu.com trusty/multiverse Translation-en [102 kB]     
Err http://archive.ubuntu.com trusty/restricted Translation-en_US              
                                                                               
Get:30 http://archive.ubuntu.com trusty/restricted Translation-en [3,457 B]    
Err http://archive.ubuntu.com trusty/universe Translation-en_US                
                                                                               
Get:31 http://archive.ubuntu.com trusty/universe Translation-en [4,089 kB]     
Get:32 http://archive.ubuntu.com trusty-updates/main Sources [34.1 kB]         
Get:33 http://archive.ubuntu.com trusty-updates/restricted Sources [14 B]      
Get:34 http://archive.ubuntu.com trusty-updates/universe Sources [20.0 kB]     
Get:35 http://archive.ubuntu.com trusty-updates/multiverse Sources [2,234 B]   
Get:36 http://archive.ubuntu.com trusty-updates/main amd64 Packages [82.3 kB]  
Get:37 http://archive.ubuntu.com trusty-updates/restricted amd64 Packages [14 B]
Get:38 http://archive.ubuntu.com trusty-updates/universe amd64 Packages [50.1 kB]
Get:39 http://archive.ubuntu.com trusty-updates/multiverse amd64 Packages [7,089 B]
Get:40 http://archive.ubuntu.com trusty-updates/main i386 Packages [80.6 kB]   
Get:41 http://archive.ubuntu.com trusty-updates/restricted i386 Packages [14 B]
Get:42 http://archive.ubuntu.com trusty-updates/universe i386 Packages [50.1 kB]
Get:43 http://archive.ubuntu.com trusty-updates/multiverse i386 Packages [7,273 B]
Err http://archive.ubuntu.com trusty-updates/main Translation-en_US            
                                                                               
Get:44 http://archive.ubuntu.com trusty-updates/main Translation-en [39.4 kB]  
Err http://archive.ubuntu.com trusty-updates/multiverse Translation-en_US      
                                                                               
Get:45 http://archive.ubuntu.com trusty-updates/multiverse Translation-en [3,811 B]
Err http://archive.ubuntu.com trusty-updates/restricted Translation-en_US      
                                                                               
Get:46 http://archive.ubuntu.com trusty-updates/restricted Translation-en [14 B]
Err http://archive.ubuntu.com trusty-updates/universe Translation-en_US        
                                                                               
Get:47 http://archive.ubuntu.com trusty-updates/universe Translation-en [24.5 kB]
Get:48 http://archive.ubuntu.com trusty-backports/main Sources [14 B]          
Get:49 http://archive.ubuntu.com trusty-backports/restricted Sources [14 B]    
Get:50 http://archive.ubuntu.com trusty-backports/multiverse Sources [14 B]    
Get:51 http://archive.ubuntu.com trusty-backports/universe Sources [1,295 B]   
Get:52 http://archive.ubuntu.com trusty-backports/main amd64 Packages [14 B]   
Get:53 http://archive.ubuntu.com trusty-backports/restricted amd64 Packages [14 B]
Get:54 http://archive.ubuntu.com trusty-backports/multiverse amd64 Packages [14 B]
Get:55 http://archive.ubuntu.com trusty-backports/universe amd64 Packages [1,134 B]
Get:56 http://archive.ubuntu.com trusty-backports/main i386 Packages [14 B]    
Get:57 http://archive.ubuntu.com trusty-backports/restricted i386 Packages [14 B]
Get:58 http://archive.ubuntu.com trusty-backports/multiverse i386 Packages [14 B]
Get:59 http://archive.ubuntu.com trusty-backports/universe i386 Packages [1,146 B]
Err http://archive.ubuntu.com trusty-backports/main Translation-en_US          
                                                                               
Get:60 http://archive.ubuntu.com trusty-backports/main Translation-en [14 B]   
Err http://archive.ubuntu.com trusty-backports/multiverse Translation-en_US    
                                                                               
Get:61 http://archive.ubuntu.com trusty-backports/multiverse Translation-en [14 B]
Err http://archive.ubuntu.com trusty-backports/restricted Translation-en_US    
                                                                               
Get:62 http://archive.ubuntu.com trusty-backports/restricted Translation-en [14 B]
Err http://archive.ubuntu.com trusty-backports/universe Translation-en_US      
                                                                               
Get:63 http://archive.ubuntu.com trusty-backports/universe Translation-en [677 B]
Get:64 http://archive.ubuntu.com trusty-security/main Sources [14.7 kB]        
Get:65 http://archive.ubuntu.com trusty-security/restricted Sources [14 B]     
Get:66 http://archive.ubuntu.com trusty-security/universe Sources [2,873 B]    
Get:67 http://archive.ubuntu.com trusty-security/multiverse Sources [687 B]    
Get:68 http://archive.ubuntu.com trusty-security/main amd64 Packages [47.0 kB] 
Get:69 http://archive.ubuntu.com trusty-security/restricted amd64 Packages [14 B]
Get:70 http://archive.ubuntu.com trusty-security/universe amd64 Packages [14.6 kB]
Get:71 http://archive.ubuntu.com trusty-security/multiverse amd64 Packages [1,154 B]
Get:72 http://archive.ubuntu.com trusty-security/main i386 Packages [45.1 kB]  
Get:73 http://archive.ubuntu.com trusty-security/restricted i386 Packages [14 B]
Get:74 http://archive.ubuntu.com trusty-security/universe i386 Packages [14.6 kB]
Get:75 http://archive.ubuntu.com trusty-security/multiverse i386 Packages [1,404 B]
Err http://archive.ubuntu.com trusty-security/main Translation-en_US           
                                                                               
Get:76 http://archive.ubuntu.com trusty-security/main Translation-en [21.6 kB] 
Err http://archive.ubuntu.com trusty-security/multiverse Translation-en_US     
                                                                               
Get:77 http://archive.ubuntu.com trusty-security/multiverse Translation-en [587 B]
Err http://archive.ubuntu.com trusty-security/restricted Translation-en_US     
                                                                               
Get:78 http://archive.ubuntu.com trusty-security/restricted Translation-en [14 B]
Err http://archive.ubuntu.com trusty-security/universe Translation-en_US       
                                                                               
Get:79 http://archive.ubuntu.com trusty-security/universe Translation-en [7,383 B]
Get:80 http://archive.ubuntu.com trusty-proposed/universe amd64 Packages [35.6 kB]
Get:81 http://archive.ubuntu.com trusty-proposed/main amd64 Packages [65.0 kB] 
Get:82 http://archive.ubuntu.com trusty-proposed/restricted amd64 Packages [14 B]
Get:83 http://archive.ubuntu.com trusty-proposed/multiverse amd64 Packages [14 B]
Get:84 http://archive.ubuntu.com trusty-proposed/universe i386 Packages [36.0 kB]
Get:85 http://archive.ubuntu.com trusty-proposed/main i386 Packages [62.1 kB]  
Get:86 http://archive.ubuntu.com trusty-proposed/restricted i386 Packages [14 B]
Get:87 http://archive.ubuntu.com trusty-proposed/multiverse i386 Packages [14 B]
Err http://archive.ubuntu.com trusty-proposed/main Translation-en_US           
                                                                               
Get:88 http://archive.ubuntu.com trusty-proposed/main Translation-en [33.3 kB] 
Err http://archive.ubuntu.com trusty-proposed/multiverse Translation-en_US     
                                                                               
Get:89 http://archive.ubuntu.com trusty-proposed/multiverse Translation-en [14 B]
Err http://archive.ubuntu.com trusty-proposed/restricted Translation-en_US     
                                                                               
Get:90 http://archive.ubuntu.com trusty-proposed/restricted Translation-en [14 B]
Err http://archive.ubuntu.com trusty-proposed/universe Translation-en_US       
                                                                               
Get:91 http://archive.ubuntu.com trusty-proposed/universe Translation-en [17.1 kB]
Err http://archive.ubuntu.com trusty/main Translation-en_US                    
                                                                               
Err http://archive.ubuntu.com trusty/multiverse Translation-en_US              
                                                                               
Err http://archive.ubuntu.com trusty/restricted Translation-en_US              
                                                                               
Err http://archive.ubuntu.com trusty/universe Translation-en_US                
                                                                               
Err http://archive.ubuntu.com trusty-updates/main Translation-en_US            
                                                                               
Err http://archive.ubuntu.com trusty-updates/multiverse Translation-en_US      
                                                                               
Err http://archive.ubuntu.com trusty-updates/restricted Translation-en_US      
                                                                               
Err http://archive.ubuntu.com trusty-updates/universe Translation-en_US        
                                                                               
Err http://archive.ubuntu.com trusty-backports/main Translation-en_US          
                                                                               
Err http://archive.ubuntu.com trusty-backports/multiverse Translation-en_US    
                                                                               
Err http://archive.ubuntu.com trusty-backports/restricted Translation-en_US    
                                                                               
Err http://archive.ubuntu.com trusty-backports/universe Translation-en_US      
                                                                               
Err http://archive.ubuntu.com trusty-security/main Translation-en_US           
                                                                               
Err http://archive.ubuntu.com trusty-security/multiverse Translation-en_US     
                                                                               
Err http://archive.ubuntu.com trusty-security/restricted Translation-en_US     
                                                                               
Err http://archive.ubuntu.com trusty-security/universe Translation-en_US       
                                                                               
Err http://archive.ubuntu.com trusty-proposed/main Translation-en_US           
                                                                               
Err http://archive.ubuntu.com trusty-proposed/multiverse Translation-en_US     
                                                                               
Err http://archive.ubuntu.com trusty-proposed/restricted Translation-en_US     
                                                                               
Err http://archive.ubuntu.com trusty-proposed/universe Translation-en_US       
                                                                               
Err http://archive.ubuntu.com trusty/main Translation-en_US                    
                                                                               
Err http://archive.ubuntu.com trusty/multiverse Translation-en_US              
                                                                               
Err http://archive.ubuntu.com trusty/restricted Translation-en_US              
                                                                               
Err http://archive.ubuntu.com trusty/universe Translation-en_US                
                                                                               
Err http://archive.ubuntu.com trusty-updates/main Translation-en_US            
                                                                               
Err http://archive.ubuntu.com trusty-updates/multiverse Translation-en_US      
                                                                               
Err http://archive.ubuntu.com trusty-updates/restricted Translation-en_US      
                                                                               
Err http://archive.ubuntu.com trusty-updates/universe Translation-en_US        
                                                                               
Err http://archive.ubuntu.com trusty-backports/main Translation-en_US          
                                                                               
Err http://archive.ubuntu.com trusty-backports/multiverse Translation-en_US    
                                                                               
Err http://archive.ubuntu.com trusty-backports/restricted Translation-en_US    
                                                                               
Err http://archive.ubuntu.com trusty-backports/universe Translation-en_US      
                                                                               
Err http://archive.ubuntu.com trusty-security/main Translation-en_US           
                                                                               
Err http://archive.ubuntu.com trusty-security/multiverse Translation-en_US     
                                                                               
Err http://archive.ubuntu.com trusty-security/restricted Translation-en_US     
                                                                               
Err http://archive.ubuntu.com trusty-security/universe Translation-en_US       
                                                                               
Err http://archive.ubuntu.com trusty-proposed/main Translation-en_US           
                                                                               
Err http://archive.ubuntu.com trusty-proposed/multiverse Translation-en_US     
                                                                               
Err http://archive.ubuntu.com trusty-proposed/restricted Translation-en_US     
                                                                               
Err http://archive.ubuntu.com trusty-proposed/universe Translation-en_US       
                                                                               
Err http://archive.ubuntu.com trusty/main Translation-en_US                    
                                                                               
Err http://archive.ubuntu.com trusty/multiverse Translation-en_US              
                                                                               
Err http://archive.ubuntu.com trusty/restricted Translation-en_US              
                                                                               
Err http://archive.ubuntu.com trusty/universe Translation-en_US                
                                                                               
Err http://archive.ubuntu.com trusty-updates/main Translation-en_US            
                                                                               
Err http://archive.ubuntu.com trusty-updates/multiverse Translation-en_US      
                                                                               
Err http://archive.ubuntu.com trusty-updates/restricted Translation-en_US      
                                                                               
Err http://archive.ubuntu.com trusty-updates/universe Translation-en_US        
                                                                               
Err http://archive.ubuntu.com trusty-backports/main Translation-en_US          
                                                                               
Err http://archive.ubuntu.com trusty-backports/multiverse Translation-en_US    
                                                                               
Err http://archive.ubuntu.com trusty-backports/restricted Translation-en_US    
                                                                               
Err http://archive.ubuntu.com trusty-backports/universe Translation-en_US      
                                                                               
Err http://archive.ubuntu.com trusty-security/main Translation-en_US           
                                                                               
Err http://archive.ubuntu.com trusty-security/multiverse Translation-en_US     
                                                                               
Err http://archive.ubuntu.com trusty-security/restricted Translation-en_US     
                                                                               
Err http://archive.ubuntu.com trusty-security/universe Translation-en_US       
                                                                               
Err http://archive.ubuntu.com trusty-proposed/main Translation-en_US           
                                                                               
Err http://archive.ubuntu.com trusty-proposed/multiverse Translation-en_US     
                                                                               
Err http://archive.ubuntu.com trusty-proposed/restricted Translation-en_US     
                                                                               
Err http://archive.ubuntu.com trusty-proposed/universe Translation-en_US       
                                                                               
Ign http://archive.ubuntu.com trusty/main Translation-en_US                    
Ign http://archive.ubuntu.com trusty/multiverse Translation-en_US              
Ign http://archive.ubuntu.com trusty/restricted Translation-en_US              
Ign http://archive.ubuntu.com trusty/universe Translation-en_US                
Ign http://archive.ubuntu.com trusty-updates/main Translation-en_US            
Ign http://archive.ubuntu.com trusty-updates/multiverse Translation-en_US      
Ign http://archive.ubuntu.com trusty-updates/restricted Translation-en_US      
Ign http://archive.ubuntu.com trusty-updates/universe Translation-en_US        
Ign http://archive.ubuntu.com trusty-backports/main Translation-en_US          
Ign http://archive.ubuntu.com trusty-backports/multiverse Translation-en_US    
Ign http://archive.ubuntu.com trusty-backports/restricted Translation-en_US    
Ign http://archive.ubuntu.com trusty-backports/universe Translation-en_US      
Ign http://archive.ubuntu.com trusty-security/main Translation-en_US           
Ign http://archive.ubuntu.com trusty-security/multiverse Translation-en_US     
Ign http://archive.ubuntu.com trusty-security/restricted Translation-en_US     
Ign http://archive.ubuntu.com trusty-security/universe Translation-en_US       
Ign http://archive.ubuntu.com trusty-proposed/main Translation-en_US           
Ign http://archive.ubuntu.com trusty-proposed/multiverse Translation-en_US     
Ign http://archive.ubuntu.com trusty-proposed/restricted Translation-en_US     
Ign http://archive.ubuntu.com trusty-proposed/universe Translation-en_US       
Fetched 28.5 MB in 6s (0 B/s)                                                  


Checking package manager
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 


Calculating the changes


Calculating the changes


Could not calculate the upgrade 


An unresolvable problem occurred while calculating the upgrade. 


This can be caused by: 
* Upgrading to a pre-release version of Ubuntu 
* Running the current pre-release version of Ubuntu 
* Unofficial software packages not provided by Ubuntu 


If none of this applies, then please report this bug using the 
command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal. 




Restoring original system state


Aborting
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 
```



```
cat /var/log/dist-upgrade/main.log | grep Obsolete
```

Here is output of above command. 

```
atif@age-ubuntu:~$ cat /var/log/dist-upgrade/main.log | grep Obsolete2014-05-19 01:14:56,820 DEBUG Obsolete: flaremonitor fbmessenger jdownloader-installer cinnamon-control-center-data cinnamon-session flareget intel-linux-graphics-installer libreoffice-avmedia-backend-gstreamer libreoffice-style-sifr gir1.2-cinnamondesktop-3.0 cjs cinnamon-settings-daemon cinnamon-desktop-data mendeleydesktop libcinnamon-control-center1 cinnamon-screensaver cinnamon-translations google-chrome-stable cinnamon-bluetooth tlp libcinnamon-desktop0 libcjs0c tlp-rdw cinnamon-control-center cinnamon-session-common opera allvideodownloader:i386 libcmis-0.4-4 viber



```

---

### Post by monkeybrain20122 on 2014-05-18
Instead of spending two weeks (Op was posted 2 weeks ago) to troubleshoot a bad upgrade it will take you 15 minutes to do fresh install plus less than half an hour to reinstall all your software and you can be sure that all your configurations are clean. This is what you should have done in the first place IMO instead of "upgrade". Before "upgrade" you should have checked the forum, many people are left with a broken mess as a result especially if you have not disabled ppas and removed proprietary graphic driver (if any).

It is also not a very wise move to trade in 13.10 for 14.04 if it is working well. At this point 14.04 is too new and still kind of buggy. Don't be surprised if something that works perfectly in 13.10 is completely broken in 14.04. You should check the launchpad bugs first before jumping on the update/upgrade bandwagon. I would have waited til July when 14.04.1 comes out if I were you.

---

### Post by slickymaster on 2014-05-19
> **susicox143 said:**
> ```
sudo apt-get update && sudo apt-get upgrade && sudo do-release-upgrade
```

Here is the output of above command.... 

```
<...snip...>Fetched 28.5 MB in 6s (0 B/s)                                               

Checking package manager
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 

Calculating the changes

Calculating the changes

Could not calculate the upgrade 

An unresolvable problem occurred while calculating the upgrade. 

This can be caused by: 
* Upgrading to a pre-release version of Ubuntu 
* Running the current pre-release version of Ubuntu 
* Unofficial software packages not provided by Ubuntu 

If none of this applies, then please report this bug using the 
command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal. <...snip...>
```
The error message explains it:
[B]This can be caused by: 
    ...
    * Unofficial software packages not provided by Ubuntu[/B]

> **susicox143 said:**
> ```
cat /var/log/dist-upgrade/main.log | grep Obsolete
```
Here is output of above command. 

```
atif@age-ubuntu:~$ cat /var/log/dist-upgrade/main.log | grep Obsolete2014-05-19 01:14:56,820 DEBUG Obsolete: flaremonitor fbmessenger jdownloader-installer cinnamon-control-center-data cinnamon-session flareget intel-linux-graphics-installer libreoffice-avmedia-backend-gstreamer libreoffice-style-sifr gir1.2-cinnamondesktop-3.0 cjs cinnamon-settings-daemon cinnamon-desktop-data mendeleydesktop libcinnamon-control-center1 cinnamon-screensaver cinnamon-translations google-chrome-stable cinnamon-bluetooth tlp libcinnamon-desktop0 libcjs0c tlp-rdw cinnamon-control-center cinnamon-session-common opera allvideodownloader:i386 libcmis-0.4-4 viber

```

These are the culprits. You'll have to remove these packages in order to able to proceed with the upgrade.

> **monkeybrain20122 said:**
> Instead of spending two weeks (Op was posted 2 weeks ago) to troubleshoot a bad upgrade it will take you 15 minutes to do fresh install plus less than half an hour to reinstall all your software and you can be sure that all your configurations are clean. This is what you should have done in the first place IMO instead of "upgrade". Before "upgrade" you should have checked the forum, many people are left with a broken mess as a result especially if you have not disabled ppas and removed proprietary graphic driver (if any).

It is also not a very wise move to trade in 13.10 for 14.04 if it is working well. At this point 14.04 is too new and still kind of buggy. Don't be surprised if something that works perfectly in 13.10 is completely broken in 14.04. You should check the launchpad bugs first before jumping on the update/upgrade bandwagon. I would have waited til July when 14.04.1 comes out if I were you.

monkeybrain20122 does raise a relevant point and leaves you with food for thought.
You should consider what would be the best, easiest and pragmatic option for you. Would it be preferable to backup all your important data and proceed with a fresh reinstall or, on the other hand, do you rather opt for uninstalling all those offending packages and lose some more time trying to fix your system.

---

### Post by jimford on 2014-05-19
> **susicox143 said:**
> HI All, 

I have followed all the below link steps to update from 13.10 to 14.04 but no success.

You lucky b@stard!

;^)

I've 'upgraded' and am still uncovering problems with was was a perfectly working 13.10 installation!

Jim

---

