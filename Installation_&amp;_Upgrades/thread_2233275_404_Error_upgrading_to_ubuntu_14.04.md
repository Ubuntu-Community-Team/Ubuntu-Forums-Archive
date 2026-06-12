---
title: "404 Error upgrading to ubuntu 14.04"
date: 2014-07-07
forum: Installation &amp; Upgrades
---

### Post by sooraj2 on 2014-07-07
hi guys 
when i try to upgrade my ubuntu 12.04 to 14.04 by

```
$ sudo update-manager -d 
```

i get this error 

```
W:Failed to fetch http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources  404  Not Found [IP: 91.189.91.15 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources  404  Not Found [IP: 91.189.91.15 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources  404  Not Found [IP: 91.189.91.15 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources  404  Not Found [IP: 91.189.91.15 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```



when i do normal update by
```
$ sudo apt-get update 
$ sudo apt-get upgrade 
```

i get this 

```
Hit http://ubuntu.excellmedia.net precise Release.gpg                          
Hit http://ubuntu.excellmedia.net precise-updates Release.gpg                  
Hit http://www.openprinting.org lsb3.2 Release.gpg                             
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://archive.canonical.com lucid Release.gpg                             
Hit http://ubuntu.excellmedia.net precise-backports Release.gpg                
Ign http://archive.ubuntu.com hardy Release.gpg                                
Ign http://archive.ubuntu.com hardy-updates Release.gpg                        
Hit http://extras.ubuntu.com precise Release                                   
Hit http://archive.canonical.com precise Release                               
Hit http://ubuntu.excellmedia.net precise-security Release.gpg                 
Ign http://archive.ubuntu.com hardy Release                                    
Hit http://www.openprinting.org lsb3.2 Release                                 
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://archive.canonical.com lucid Release                                 
Hit http://ubuntu.excellmedia.net precise Release                              
Ign http://archive.ubuntu.com hardy-updates Release                            
Hit http://ubuntu.excellmedia.net precise-updates Release                      
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Ign http://archive.ubuntu.com hardy/main TranslationIndex                      
Ign http://archive.ubuntu.com hardy/multiverse TranslationIndex                
Hit http://archive.canonical.com precise/partner Sources                       
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://ubuntu.excellmedia.net precise-backports Release                    
Ign http://archive.ubuntu.com hardy-updates/main TranslationIndex              
Ign http://archive.ubuntu.com hardy-updates/multiverse TranslationIndex        
Hit http://www.openprinting.org lsb3.2/contrib amd64 Packages                  
Hit http://archive.canonical.com lucid/partner Sources                         
Hit http://archive.canonical.com lucid/partner amd64 Packages                  
Hit http://archive.canonical.com lucid/partner i386 Packages                   
Ign http://archive.canonical.com lucid/partner TranslationIndex                
Hit http://ubuntu.excellmedia.net precise-security Release                     
Hit http://ubuntu.excellmedia.net precise/main amd64 Packages                  
Hit http://www.openprinting.org lsb3.2/contrib i386 Packages                   
Hit http://ubuntu.excellmedia.net precise/restricted amd64 Packages            
Hit http://ubuntu.excellmedia.net precise/universe amd64 Packages              
Hit http://ubuntu.excellmedia.net precise/multiverse amd64 Packages                                                                             
Ign http://www.openprinting.org lsb3.2/contrib TranslationIndex                                                                                 
Hit http://ubuntu.excellmedia.net precise/main i386 Packages                                                                 
Hit http://ubuntu.excellmedia.net precise/restricted i386 Packages                                                           
Hit http://ubuntu.excellmedia.net precise/universe i386 Packages                                       
Err http://archive.ubuntu.com hardy/main Sources                                                       
  404  Not Found [IP: 91.189.88.153 80]
Err http://archive.ubuntu.com hardy/multiverse Sources                                                 
  404  Not Found [IP: 91.189.88.153 80]
Err http://archive.ubuntu.com hardy/main amd64 Packages                                                                      
  404  Not Found [IP: 91.189.88.153 80]
Err http://archive.ubuntu.com hardy/multiverse amd64 Packages                                                                
  404  Not Found [IP: 91.189.88.153 80]
Err http://archive.ubuntu.com hardy/main i386 Packages                                                 
  404  Not Found [IP: 91.189.88.153 80]
Err http://archive.ubuntu.com hardy/multiverse i386 Packages                                           
  404  Not Found [IP: 91.189.88.153 80]
Hit http://ubuntu.excellmedia.net precise/multiverse i386 Packages                                     
Hit http://ubuntu.excellmedia.net precise/main TranslationIndex                                        
Ign http://extras.ubuntu.com precise/main Translation-en_US                                            
Err http://archive.ubuntu.com hardy-updates/main Sources                                                                                
  404  Not Found [IP: 91.189.88.153 80]
Err http://archive.ubuntu.com hardy-updates/multiverse Sources                                                                          
  404  Not Found [IP: 91.189.88.153 80]
Err http://archive.ubuntu.com hardy-updates/main amd64 Packages                                                              
  404  Not Found [IP: 91.189.88.153 80]
Err http://archive.ubuntu.com hardy-updates/multiverse amd64 Packages                                                        
  404  Not Found [IP: 91.189.88.153 80]
Err http://archive.ubuntu.com hardy-updates/main i386 Packages                                                               
  404  Not Found [IP: 91.189.88.153 80]
Err http://archive.ubuntu.com hardy-updates/multiverse i386 Packages                                   
  404  Not Found [IP: 91.189.88.153 80]
Hit http://ubuntu.excellmedia.net precise/multiverse TranslationIndex                                                        
Ign http://archive.ubuntu.com hardy/main Translation-en_US                                                                   
Ign http://extras.ubuntu.com precise/main Translation-en                                                                                        
Hit http://ubuntu.excellmedia.net precise/restricted TranslationIndex                                                                           
Hit http://ubuntu.excellmedia.net precise/universe TranslationIndex                                                                 
Ign http://archive.ubuntu.com hardy/main Translation-en                                                       
Ign http://archive.ubuntu.com hardy/multiverse Translation-en_US                                
Ign http://archive.ubuntu.com hardy/multiverse Translation-en                                   
Ign http://archive.ubuntu.com hardy-updates/main Translation-en_US                              
Ign http://archive.ubuntu.com hardy-updates/main Translation-en                                 
Ign http://archive.ubuntu.com hardy-updates/multiverse Translation-en_US                                              
Hit http://ubuntu.excellmedia.net precise-updates/main amd64 Packages                                                 
Ign http://archive.ubuntu.com hardy-updates/multiverse Translation-en                                                                           
Hit http://ubuntu.excellmedia.net precise-updates/restricted amd64 Packages                                                                     
Ign http://archive.canonical.com precise/partner Translation-en_US                                   
Hit http://ubuntu.excellmedia.net precise-updates/universe amd64 Packages                                                             
Hit http://ppa.launchpad.net precise Release.gpg                                                                                      
Hit http://ppa.launchpad.net precise Release.gpg                                                                            
Hit http://ppa.launchpad.net precise Release.gpg                                                                            
Ign http://archive.canonical.com precise/partner Translation-en                                                             
Ign http://archive.canonical.com lucid/partner Translation-en_US                                                            
Hit http://ubuntu.excellmedia.net precise-updates/multiverse amd64 Packages                                                 
Hit http://ppa.launchpad.net precise Release                                                                                
Ign http://archive.canonical.com lucid/partner Translation-en                                                                
Hit http://ubuntu.excellmedia.net precise-updates/main i386 Packages 
Hit http://ppa.launchpad.net precise Release                                    
Hit http://ubuntu.excellmedia.net precise-updates/restricted i386 Packages      
Hit http://ppa.launchpad.net precise Release   
Hit http://ubuntu.excellmedia.net precise-updates/universe i386 Packages
Hit http://ubuntu.excellmedia.net precise-updates/multiverse i386 Packages                             
Hit http://ppa.launchpad.net precise/main Sources                               
Hit http://ppa.launchpad.net precise/main amd64 Packages  
Hit http://ppa.launchpad.net precise/main i386 Packages   
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ubuntu.excellmedia.net precise-updates/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources         
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                                           
Hit http://ubuntu.excellmedia.net precise-updates/multiverse TranslationIndex                        
Hit http://ubuntu.excellmedia.net precise-updates/restricted TranslationIndex                        
Hit http://ppa.launchpad.net precise/main Sources                                                     
Hit http://ppa.launchpad.net precise/main amd64 Packages                                              
Hit http://ppa.launchpad.net precise/main i386 Packages                         
Ign http://ppa.launchpad.net precise/main TranslationIndex                      
Hit http://ubuntu.excellmedia.net precise-updates/universe TranslationIndex     
Hit http://ubuntu.excellmedia.net precise-backports/main amd64 Packages         
Hit http://ubuntu.excellmedia.net precise-backports/restricted amd64 Packages
Hit http://ubuntu.excellmedia.net precise-backports/universe amd64 Packages    
Hit http://ubuntu.excellmedia.net precise-backports/multiverse amd64 Packages  
Hit http://ubuntu.excellmedia.net precise-backports/main i386 Packages
Hit http://ubuntu.excellmedia.net precise-backports/restricted i386 Packages
Hit http://ubuntu.excellmedia.net precise-backports/universe i386 Packages
Hit http://ubuntu.excellmedia.net precise-backports/multiverse i386 Packages
Hit http://ubuntu.excellmedia.net precise-backports/main TranslationIndex
Hit http://ubuntu.excellmedia.net precise-backports/multiverse TranslationIndex
Hit http://ubuntu.excellmedia.net precise-backports/restricted TranslationIndex
Hit http://ubuntu.excellmedia.net precise-backports/universe TranslationIndex
Hit http://ubuntu.excellmedia.net precise-security/main amd64 Packages         
Hit http://ubuntu.excellmedia.net precise-security/restricted amd64 Packages                                                          
Ign http://ppa.launchpad.net precise/main Translation-en_US                                                                           
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Hit http://ubuntu.excellmedia.net precise-security/universe amd64 Packages
Ign http://ppa.launchpad.net precise/main Translation-en
Hit http://ubuntu.excellmedia.net precise-security/multiverse amd64 Packages
Hit http://ubuntu.excellmedia.net precise-security/main i386 Packages
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                                                        
Hit http://ubuntu.excellmedia.net precise-security/restricted i386 Packages                                     
Hit http://ubuntu.excellmedia.net precise-security/universe i386 Packages                                       
Hit http://ubuntu.excellmedia.net precise-security/multiverse i386 Packages
Hit http://ubuntu.excellmedia.net precise-security/main TranslationIndex
Hit http://ubuntu.excellmedia.net precise-security/multiverse TranslationIndex
Hit http://ubuntu.excellmedia.net precise-security/restricted TranslationIndex
Hit http://ubuntu.excellmedia.net precise-security/universe TranslationIndex
Hit http://ubuntu.excellmedia.net precise/main Translation-en
Hit http://ubuntu.excellmedia.net precise/multiverse Translation-en
Hit http://ubuntu.excellmedia.net precise/restricted Translation-en
Hit http://ubuntu.excellmedia.net precise/universe Translation-en
Hit http://ubuntu.excellmedia.net precise-updates/main Translation-en
Hit http://ubuntu.excellmedia.net precise-updates/multiverse Translation-en
Hit http://ubuntu.excellmedia.net precise-updates/restricted Translation-en
Hit http://ubuntu.excellmedia.net precise-updates/universe Translation-en
Hit http://ubuntu.excellmedia.net precise-backports/main Translation-en                                         
Hit http://ubuntu.excellmedia.net precise-backports/multiverse Translation-en                                   
Hit http://ubuntu.excellmedia.net precise-backports/restricted Translation-en
Hit http://ubuntu.excellmedia.net precise-backports/universe Translation-en
Hit http://ubuntu.excellmedia.net precise-security/main Translation-en
Hit http://ubuntu.excellmedia.net precise-security/multiverse Translation-en
Hit http://ubuntu.excellmedia.net precise-security/restricted Translation-en
Hit http://ubuntu.excellmedia.net precise-security/universe Translation-en
Ign http://www.openprinting.org lsb3.2/contrib Translation-en_US
Hit http://www.openprinting.org lsb3.2/contrib Translation-en
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources  404  Not Found [IP: 91.189.88.153 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources  404  Not Found [IP: 91.189.88.153 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-amd64/Packages  404  Not Found [IP: 91.189.88.153 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-amd64/Packages  404  Not Found [IP: 91.189.88.153 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages  404  Not Found [IP: 91.189.88.153 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.88.153 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources  404  Not Found [IP: 91.189.88.153 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources  404  Not Found [IP: 91.189.88.153 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-amd64/Packages  404  Not Found [IP: 91.189.88.153 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-amd64/Packages  404  Not Found [IP: 91.189.88.153 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages  404  Not Found [IP: 91.189.88.153 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.88.153 80]


E: Some index files failed to download. They have been ignored, or old ones used instead.


```

any help is appreciated :)

---

### Post by QIII on 2014-07-07
Hello!

You need to remove the PPAs and the sources referring to older, unsupported versions.

Let us know if you need help with that.

---

### Post by sooraj2 on 2014-07-07
> **QIII said:**
> Hello!

You need to remove the PPAs and the sources referring to older, unsupported versions.

Let us know if you need help with that.

thanks for reply 
sorry iam just a beginner in ubuntu 
pls help with that :( ie removing PPAs and the sources referring to older, unsupported versions.

---

### Post by mastablasta on 2014-07-08
in software center go to software sources and then other software and remove any older PPAs such as those with Hardy in them. Hardy is version 8.04 and is no longer supported. more on PPA here: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

alternative method is to fix those old PPA links to archived repositories. more on this here: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades) 

but i would just disable them.

@QIII - i though the upgrade process disables all PPA's on upgrade :O it did in my case.

---

### Post by sooraj2 on 2014-07-08
> **mastablasta said:**
> in software center go to software sources and then other software and remove any older PPAs such as those with Hardy in them. Hardy is version 8.04 and is no longer supported. more on PPA here: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

alternative method is to fix those old PPA links to archived repositories. more on this here: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades) 

but i would just disable them.

@QIII - i though the upgrade process disables all PPA's on upgrade :O it did in my case.

when i open software sources i get the attached screenshot.

```
W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources  404  Not Found [IP: 91.189.91.15 80], W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources  404  Not Found [IP: 91.189.91.15 80]
, W:Failed to fetch http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by Bashing-om on 2014-07-08
sooraj2; Hello.

As I am passing by, and your 1st responders are presently offline, allow me to offer aid.
In USC -> "ubuntu software" you do want main. universe and multiverse tabs enabled ! and as well most likely ( maybe) restricted.
Now look in "other software" and there disable the unwanted repositories .

Will be a good thing to look at the sources.list file directly in a text editor and see for yourself what is enabled there.
```

gedit /etc/apt/sources.list

```
as we are presently only looking, and not making a change, elevated privileges (gksudo) is not required.

[INDENT][INDENT]my little bit to try and help
[/INDENT][/INDENT]

---

### Post by yancek on 2014-07-08
To elaborate briefly on the last post, you can open the /etc/apt/sources.list file as a user to view it to see what you have and using sudo to actually edit it.  You would comment out any lines, particularly those referring to Ubuntu Hardy by placing a hash mark (#) at the beginning of that specific line.  If you are more comfortable with a GUI the post above explains it.

---

### Post by sooraj2 on 2014-07-09
> **Bashing-om said:**
> sooraj2; Hello.

As I am passing by, and your 1st responders are presently offline, allow me to offer aid.
In USC -> "ubuntu software" you do want main. universe and multiverse tabs enabled ! and as well most likely ( maybe) restricted.
Now look in "other software" and there disable the unwanted repositories .

Will be a good thing to look at the sources.list file directly in a text editor and see for yourself what is enabled there.
```

gedit /etc/apt/sources.list

```
as we are presently only looking, and not making a change, elevated privileges (gksudo) is not required.
[INDENT][INDENT]my little bit to try and help
[/INDENT]
[/INDENT]


> **yancek said:**
> To elaborate briefly on the last post, you can open the /etc/apt/sources.list file as a user to view it to see what you have and using sudo to actually edit it.  You would comment out any lines, particularly those referring to Ubuntu Hardy by placing a hash mark (#) at the beginning of that specific line.  If you are more comfortable with a GUI the post above explains it.

thanks for replying 

iam able to open  the file 
```

gedit /etc/apt/sources.list

```

here is my sources.list ```
# 

# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ dists/precise/main/binary-i386/
# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ precise main restricted


# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ dists/precise/main/binary-i386/
# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ precise main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ubuntu.excellmedia.net/archive/ trusty main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://ubuntu.excellmedia.net/archive/ trusty-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ubuntu.excellmedia.net/archive/ trusty universe
deb http://ubuntu.excellmedia.net/archive/ trusty-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ubuntu.excellmedia.net/archive/ trusty multiverse
deb http://ubuntu.excellmedia.net/archive/ trusty-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ubuntu.excellmedia.net/archive/ trusty-backports main restricted universe multiverse


deb http://ubuntu.excellmedia.net/archive/ trusty-security main restricted
deb http://ubuntu.excellmedia.net/archive/ trusty-security universe
deb http://ubuntu.excellmedia.net/archive/ trusty-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu trusty partner
deb-src http://archive.canonical.com/ubuntu trusty partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main
# deb http://archive.canonical.com/ lucid partner
# deb-src http://archive.canonical.com/ lucid partner
# deb http://archive.ubuntu.com/ubuntu hardy-updates main multiverse
# deb-src http://archive.ubuntu.com/ubuntu hardy-updates main multiverse
deb http://ubuntu.excellmedia.net/archive/ precise multiverse restricted universe main
```

but iam unable to save changes i make 
i commented out lines with hardy but i cant save the file its read only i guess 

[IMG]http://i.imgur.com/tKnLLVs.png[/IMG]

and should i disabled anything here 
[IMG]http://i.imgur.com/bnuh1Ud.png[/IMG]

---

### Post by Bucky Ball on 2014-07-09
For future reference: Please attach large pics using 'Go Advanced' or 'Adv Reply' and clicking on the paperclip icon rather than inserting them in the body of you posts. Spare a thought for those with slow connections or vision problems. ;)

* I've attached the one in post #5 as an example.

---

### Post by sooraj2 on 2014-07-09
> **Bucky Ball said:**
> For future reference: Please attach large pics using 'Go Advanced' or 'Adv Reply' and clicking on the paperclip icon rather than inserting them in the body of you posts. Spare a thought for those with slow connections or vision problems. ;)

* I've attached the one in post #5 as an example.
oh ok :)

---

### Post by mastablasta on 2014-07-09
you need to open file as root. hit alt+f2 (or open terminal) and then:

```
gksudo gedit
```

you can then open the file, edit it and save it.

in sources all PPA that have Hardy in it or even better just disable all those PPAs and try again.

---

### Post by sooraj2 on 2014-07-09
> **mastablasta said:**
> you need to open file as root. hit alt+f2 (or open terminal) and then:

```
gksudo gedit
```

you can then open the file, edit it and save it.

in sources all PPA that have Hardy in it or even better just disable all those PPAs and try again.

thanku so much friend looks its working now 
will report back if i face any new errors :)

---

### Post by sooraj2 on 2014-07-09
Oops error again
```
 Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libc/libcap2/libcap2_2.24-0ubuntu2_i386.deb 403  ForbiddenFailed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libc/libcap2/libcap2_2.24-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/systemd/libudev1_204-5ubuntu20.3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/sysvinit/sysv-rc_2.88dsf-41ubuntu6_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgcrypt11/libgcrypt11_1.5.3-2ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgcrypt11/libgcrypt11_1.5.3-2ubuntu4_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libt/libtasn1-6/libtasn1-6_3.4-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libt/libtasn1-6/libtasn1-6_3.4-3_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/systemd/libsystemd-login0_204-5ubuntu20.3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/p11-kit/libp11-kit0_0.20.2-2ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/p11-kit/libp11-kit0_0.20.2-2ubuntu2_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gcr/libgcr-3-1_3.10.1-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/p11-kit/p11-kit-modules_0.20.2-2ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/p11-kit/p11-kit_0.20.2-2ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgnome-keyring/gir1.2-gnomekeyring-1.0_3.8.0-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgnome-keyring/libgnome-keyring0_3.8.0-2_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgnome-keyring/libgnome-keyring0_3.8.0-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgnome-keyring/libgnome-keyring-common_3.8.0-2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libsecret/libsecret-common_0.16-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libsecret/libsecret-1-0_0.16-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/seahorse/seahorse_3.10.2-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lcms2/liblcms2-2_2.5-0ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/f/fonts-freefont/ttf-freefont_20120503-4_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unico/gtk3-engines-unico_1.0.3+14.04.20140109-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xz-utils/liblzma5_5.1.1alpha+20120614-2ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/tiff/libtiff5_4.0.3-7ubuntu0.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xz-utils/liblzma5_5.1.1alpha+20120614-2ubuntu2_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/tiff/libtiff5_4.0.3-7ubuntu0.1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pango1.0/libpango1.0-0_1.36.3-1ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pango1.0/libpango1.0-0_1.36.3-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pango1.0/libpangoft2-1.0-0_1.36.3-1ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pango1.0/libpangocairo-1.0-0_1.36.3-1ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pango1.0/libpangoxft-1.0-0_1.36.3-1ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pangox-compat/libpangox-1.0-0_0.0.2-4ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pango1.0/libpangoft2-1.0-0_1.36.3-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pango1.0/libpangocairo-1.0-0_1.36.3-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pango1.0/libpangoxft-1.0-0_1.36.3-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pangox-compat/libpangox-1.0-0_0.0.2-4ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pango1.0/gir1.2-pango-1.0_1.36.3-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libe/libelf/libelfg0_0.8.13-5_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pcre3/libpcre3_8.31-2ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pcre3/libpcre3_8.31-2ubuntu2_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pcre3/libpcrecpp0_8.31-2ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pcre3/libpcre3-dev_8.31-2ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pango1.0/libpango1.0-dev_1.36.3-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/plymouth/plymouth_0.8.8-0ubuntu17_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pango1.0/libpango-1.0-0_1.36.3-1ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxml2/libxml2_2.9.1+dfsg1-3ubuntu4.3_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxml2/libxml2_2.9.1+dfsg1-3ubuntu4.3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/librsvg/librsvg2-common_2.40.2-1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/librsvg/librsvg2-common_2.40.2-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/librsvg/librsvg2-2_2.40.2-1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/librsvg/librsvg2-2_2.40.2-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/wayland/libwayland-client0_1.4.0-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/wayland/libwayland-cursor0_1.4.0-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxkbcommon/libxkbcommon0_0.4.1-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/wayland/libwayland-server0_1.4.0-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/wayland/libwayland-dev_1.4.0-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxkbcommon/libxkbcommon-dev_0.4.1-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libw/libwacom/libwacom-common_0.8-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libw/libwacom/libwacom2_0.8-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/metacity/metacity_2.34.13-0ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity-lens-files/unity-lens-files_7.1.0+13.10.20130920-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity-lens-music/unity-lens-music_6.9.0+13.10.20131011-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity-lens-video/unity-lens-video_0.3.15+13.10.20130920-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity/unity_7.2.1+14.04.20140513-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mesa/libgbm1_10.1.3-0ubuntu0.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcb/libxcb-xfixes0_1.10-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mesa/libegl1-mesa_10.1.3-0ubuntu0.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcb/libxcb-dri2-0_1.10-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcb/libxcb-dri2-0_1.10-2ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcb/libxcb1-dev_1.10-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcb/libxcb1-dev_1.10-2ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcb/libxcb1_1.10-2ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcb/libxcb1_1.10-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcb/libxcb-dri3-0_1.10-2ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcb/libxcb-present0_1.10-2ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcb/libxcb-sync1_1.10-2ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxshmfence/libxshmfence1_1.1-2_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libn/libnih/libnih-dbus1_1.0.3-4ubuntu25_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libn/libnih/libnih1_1.0.3-4ubuntu25_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libn/libnih/libnih1_1.0.3-4ubuntu25_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libn/libnih/libnih-dbus1_1.0.3-4ubuntu25_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/systemd/libudev1_204-5ubuntu20.3_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcb/libxcb-dri3-0_1.10-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcb/libxcb-present0_1.10-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcb/libxcb-sync1_1.10-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxshmfence/libxshmfence1_1.1-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mesa/mesa-common-dev_10.1.3-0ubuntu0.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libx11/libx11-xcb1_1.6.2-1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libx11/libx11-xcb1_1.6.2-1ubuntu2_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libx11/libx11-xcb-dev_1.6.2-1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcb/libxcb-dri3-dev_1.10-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcb/libxcb-randr0_1.10-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcb/libxcb-randr0-dev_1.10-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcb/libxcb-shape0_1.10-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcb/libxcb-shape0-dev_1.10-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcb/libxcb-xfixes0-dev_1.10-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcb/libxcb-sync-dev_1.10-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcb/libxcb-present-dev_1.10-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxshmfence/libxshmfence-dev_1.1-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcb/libxcb-dri2-0-dev_1.10-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcb/libxcb-glx0_1.10-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcb/libxcb-glx0_1.10-2ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcb/libxcb-glx0-dev_1.10-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxxf86vm/libxxf86vm1_1.1.3-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxxf86vm/libxxf86vm1_1.1.3-1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/x11proto-xf86vidmode/x11proto-xf86vidmode-dev_2.3.1-2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxxf86vm/libxxf86vm-dev_1.1.3-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/x11proto-dri2/x11proto-dri2-dev_2.8-2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/x11proto-gl/x11proto-gl-dev_1.4.17-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mesa/libgl1-mesa-dev_10.1.3-0ubuntu0.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/llvm-toolchain-3.4/libllvm3.4_3.4-1ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xorg-server/xserver-common_1.15.1-0ubuntu2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/nux/libnux-4.0-common_4.0.6+14.04.20140409-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/nux/libnux-4.0-0_4.0.6+14.04.20140409-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libu/libunity/libunity-scopes-json-def-desktop_7.1.4+14.04.20140210-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libc/libcolumbus/libcolumbus1-common_1.1.0+14.04.20140325.3-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libc/libcolumbus/libcolumbus1_1.1.0+14.04.20140325.3-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity-lens-applications/unity-lens-applications_7.1.0+13.10.20131011-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libu/libunity/libunity9_7.1.4+14.04.20140210-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libu/libunity/libunity-protocol-private0_7.1.4+14.04.20140210-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/upstart/libupstart1_1.12.1-0ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/u/unity/unity-2d-spread_7.2.1+14.04.20140513-0ubuntu2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/u/unity/unity-2d-panel_7.2.1+14.04.20140513-0ubuntu2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/u/unity/unity-2d-shell_7.2.1+14.04.20140513-0ubuntu2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/u/unity/libunity-2d-private0_7.2.1+14.04.20140513-0ubuntu2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity/unity-services_7.2.1+14.04.20140513-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity/libunity-core-6.0-9_7.2.1+14.04.20140513-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/z/zeitgeist/libzeitgeist-2.0-0_0.9.14-0ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/session-migration/session-migration_0.2.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/protobuf/libprotobuf8_2.5.0-9ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/c/compiz/compiz-plugins-main-default_0.9.11+14.04.20140423-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/sgml-base/sgml-base_1.26+nmu4ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/metacity/metacity-common_2.34.13-0ubuntu4_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/ubuntu-themes/light-themes_14.04+14.04.20140410-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/metacity/libmetacity-private0a_2.34.13-0ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/c/compiz/compizconfig-backend-gconf_0.9.11+14.04.20140423-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity-scope-home/unity-scopes-master-default_6.8.2+14.04.20131029.1-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity-scope-home/unity-scope-home_6.8.2+14.04.20131029.1-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/orc/liborc-0.4-0_0.4.18-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/orc/liborc-0.4-0_0.4.18-1ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxfixes/libxfixes3_5.0.1-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xorg-server/xserver-xorg-core_1.15.1-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxfixes/libxfixes3_5.0.1-1ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/ginn/ginn_0.2.6-0ubuntu5_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxfixes/libxfixes-dev_5.0.1-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xserver-xorg-video-siliconmotion/xserver-xorg-video-siliconmotion_1.7.7-2build1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xserver-xorg-video-ati/xserver-xorg-video-ati_7.3.0-1ubuntu3.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xserver-xorg-video-mach64/xserver-xorg-video-mach64_6.9.4-1build1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.99.910-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xserver-xorg-video-trident/xserver-xorg-video-trident_1.3.6-0ubuntu5_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xserver-xorg-video-s3/xserver-xorg-video-s3_0.6.5-0ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xserver-xorg-video-mga/xserver-xorg-video-mga_1.6.3-1build1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xserver-xorg-video-nouveau/xserver-xorg-video-nouveau_1.0.10-1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xserver-xorg-video-neomagic/xserver-xorg-video-neomagic_1.2.8-1build1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xserver-xorg-video-r128/xserver-xorg-video-r128_6.9.2-1build1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xserver-xorg-video-cirrus/xserver-xorg-video-cirrus_1.5.2-1build1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xserver-xorg-video-tdfx/xserver-xorg-video-tdfx_1.4.5-1build1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xserver-xorg-video-sisusb/xserver-xorg-video-sisusb_0.9.6-2build1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xserver-xorg-video-vesa/xserver-xorg-video-vesa_2.3.3-1build1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xserver-xorg-video-fbdev/xserver-xorg-video-fbdev_0.4.4-1build1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xserver-xorg-video-savage/xserver-xorg-video-savage_2.3.7-2ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/spice/libspice-server1_0.12.4-0nocelt2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xserver-xorg-video-qxl/xserver-xorg-video-qxl_0.1.1-0ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xserver-xorg-video-ati/xserver-xorg-video-radeon_7.3.0-1ubuntu3.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mesa/libxatracker2_10.1.3-0ubuntu0.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xserver-xorg-video-vmware/xserver-xorg-video-vmware_13.0.2-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xserver-xorg-video-openchrome/xserver-xorg-video-openchrome_0.3.3-1build1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xserver-xorg-video-sis/xserver-xorg-video-sis_0.10.7-0ubuntu6_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xserver-xorg-input-evdev/xserver-xorg-input-evdev_2.8.2-1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mesa/libgl1-mesa-dri_10.1.3-0ubuntu0.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mesa/libgl1-mesa-glx_10.1.3-0ubuntu0.1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mesa/libgl1-mesa-glx_10.1.3-0ubuntu0.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mesa/libglapi-mesa_10.1.3-0ubuntu0.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mesa/libglapi-mesa_10.1.3-0ubuntu0.1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mesa/libopenvg1-mesa_10.1.3-0ubuntu0.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mesa/libwayland-egl1-mesa_10.1.3-0ubuntu0.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mesa/libegl1-mesa-drivers_10.1.3-0ubuntu0.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libv/libvpx/libvpx1_1.3.0-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libsoup2.4/libsoup2.4-1_2.44.2-1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libsoup2.4/libsoup2.4-1_2.44.2-1ubuntu2_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/telepathy-glib/libtelepathy-glib0_0.22.1-1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/webkitgtk/libjavascriptcoregtk-3.0-0_2.4.3-1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libw/libwebp/libwebp5_0.4.0-4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/webkitgtk/libwebkitgtk-3.0-common_2.4.3-1ubuntu2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/webkitgtk/libwebkitgtk-3.0-0_2.4.3-1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gnome-online-accounts/gnome-online-accounts_3.10.3-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/liba/libaccounts-glib/libaccounts-glib0_1.15+14.04.20131126.2-0ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libn/libnice/gstreamer1.0-nice_0.1.4-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgee-0.8/libgee-0.8-2_0.10.5-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/n/nspr/libnspr4-0d_4.10.2-1ubuntu1.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/nspr/libnspr4_4.10.2-1ubuntu1.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/nspr/libnspr4_4.10.2-1ubuntu1.1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/nss/libnss3-nssdb_3.15.4-1ubuntu7_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/nss/libnss3-1d_3.15.4-1ubuntu7_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/nss/libnss3_3.15.4-1ubuntu7_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/nss/libnss3_3.15.4-1ubuntu7_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libi/libical/libical1_1.0-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgweather/libgweather-common_3.10.2-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgweather/libgweather-3-6_3.10.2-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/thunderbird/thunderbird-locale-en_24.6.0+build1-0ubuntu0.14.04.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/thunderbird/thunderbird_24.6.0+build1-0ubuntu0.14.04.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/thunderbird/thunderbird-gnome-support_24.6.0+build1-0ubuntu0.14.04.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libn/libnotify/libnotify4_0.7.6-1ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/url-dispatcher/liburl-dispatcher1_0.1+14.04.20140403-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/systemd/libsystemd-daemon0_204-5ubuntu20.3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lvm2/libdevmapper1.02.1_1.02.77-6ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lvm2/dmsetup_1.02.77-6ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python3.4/libpython3.4-minimal_3.4.0-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python3.4/python3.4-minimal_3.4.0-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mpdecimal/libmpdec2_2.4.0-6_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python3.4/libpython3.4-stdlib_3.4.0-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python3.4/python3.4_3.4.0-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python3-defaults/python3-minimal_3.4.0-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python3-defaults/libpython3-stdlib_3.4.0-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python3-defaults/python3_3.4.0-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/systemd/udev_204-5ubuntu20.3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/systemd-shim/systemd-shim_6-2bzr1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/systemd/systemd-services_204-5ubuntu20.3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libsignon-glib/libsignon-glib1_1.10daily13.06.25-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/telepathy-farstream/libtelepathy-farstream3_0.6.1-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/telepathy-logger/libtelepathy-logger3_0.8.0-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pulseaudio/libpulse0_4.0-0ubuntu11_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pulseaudio/libpulse0_4.0-0ubuntu11_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pulseaudio/libpulse-mainloop-glib0_4.0-0ubuntu11_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pulseaudio/libpulse-mainloop-glib0_4.0-0ubuntu11_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pulseaudio/libpulse-dev_4.0-0ubuntu11_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/nautilus/nautilus-data_3.10.1-0ubuntu9.2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/nautilus/libnautilus-extension1a_3.10.1-0ubuntu9.2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/nautilus/nautilus_3.10.1-0ubuntu9.2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/nautilus-sendto/nautilus-sendto_3.6.1-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libp/libpwquality/libpwquality-common_1.2.3-1ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libp/libpwquality/libpwquality1_1.2.3-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgnomekbd/libgnomekbd-common_3.6.0-0ubuntu2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgnomekbd/libgnomekbd8_3.6.0-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgnomekbd/gkbd-capplet_3.6.0-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gnome-media/gnome-media_3.4.0-1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/systemd/libsystemd-journal0_204-5ubuntu20.3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/v/vino/vino_3.8.1-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-apt/python-apt-common_0.9.3.5_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-apt/python-apt_0.9.3.5_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-apt/python3-apt_0.9.3.5_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-defer/python3-defer_1.0.6-2build1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pygobject/python3-gi_3.12.0-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-setuptools/python3-pkg-resources_3.3-1ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/software-center-aptdaemon-plugins/software-center-aptdaemon-plugins_0.1.6build1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lxml/python-lxml_3.3.3-1ubuntu0.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python2.7/libpython2.7-minimal_2.7.6-8_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python2.7/python2.7-minimal_2.7.6-8_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python2.7/libpython2.7-stdlib_2.7.6-8_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python2.7/libpython2.7_2.7.6-8_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python2.7/python2.7_2.7.6-8_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-defaults/libpython-stdlib_2.7.5-5ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-defaults/python_2.7.5-5ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-defaults/python-minimal_2.7.5-5ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-oauthlib/python-oauthlib_0.6.1-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/oneconf/oneconf-common_0.3.7_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/oneconf/python-oneconf_0.3.7_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/software-center/software-center_13.10-0ubuntu4.1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pygobject/python-gi-cairo_3.12.0-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pygobject/python-gi_3.12.0-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/udisks2/libudisks2-0_2.1.3-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/udisks2/udisks2_2.1.3-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libsecret/libsecret-1-0_0.16-0ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/liba/libarchive/libarchive13_3.1.2-7ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/totem-pl-parser/libtotem-plparser18_3.10.2-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/rhythmbox/librhythmbox-core8_3.0.2-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/rhythmbox/rhythmbox_3.0.2-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/rhythmbox/rhythmbox-data_3.0.2-0ubuntu2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/markupsafe/python3-markupsafe_0.18-1build2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mako/python3-mako_0.9.1-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libsecret/gir1.2-secret-1_0.16-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/rhythmbox/rhythmbox-plugin-magnatune_3.0.2-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/rhythmbox/rhythmbox-plugins_3.0.2-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/rhythmbox/gir1.2-rb-3.0_3.0.2-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/rhythmbox/rhythmbox-plugin-cdrecorder_3.0.2-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/rhythmbox/rhythmbox-plugin-zeitgeist_3.0.2-0ubuntu2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/rhythmbox/rhythmbox-mozilla_3.0.2-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgd2/libgd3_2.1.0-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgphoto2/libgphoto2-port10_2.5.3.1-1ubuntu2.2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgphoto2/libgphoto2-6_2.5.3.1-1ubuntu2.2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/usbmuxd/libusbmuxd2_1.0.8-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libi/libimobiledevice/libimobiledevice4_1.1.5+git20140313.bafe6a9e-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libm/libmtp/libmtp-runtime_1.1.6-20-g1b9f164-1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libm/libmtp/libmtp9_1.1.6-20-g1b9f164-1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/tevent/libtevent0_0.9.19-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/ldb/libldb1_1.1.16-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/ntdb/libntdb1_1.0-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lsb/lsb-base_4.1+Debian11ubuntu6_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/ntdb/python-ntdb_1.0-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/ldb/python-ldb_1.1.16-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/tdb/libtdb1_1.2.12-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/tdb/libtdb1_1.2.12-1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/tdb/python-tdb_1.2.12-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/talloc/python-talloc_2.1.0-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/samba/python-samba_4.1.6+dfsg-1ubuntu2.14.04.2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/samba/smbclient_4.1.6+dfsg-1ubuntu2.14.04.2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/nautilus-share/nautilus-share_0.7.3-1ubuntu5_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/s/samba/libpam-winbind_4.1.6+dfsg-1ubuntu2.14.04.2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/samba/samba-common_4.1.6+dfsg-1ubuntu2.14.04.2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/samba/samba-common-bin_4.1.6+dfsg-1ubuntu2.14.04.2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/samba/samba-dsdb-modules_4.1.6+dfsg-1ubuntu2.14.04.2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/tdb/tdb-tools_1.2.12-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libb/libbsd/libbsd-dev_0.6.0-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libb/libbsd/libbsd0_0.6.0-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/samba/samba_4.1.6+dfsg-1ubuntu2.14.04.2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/samba/winbind_4.1.6+dfsg-1ubuntu2.14.04.2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/samba/libwbclient0_4.1.6+dfsg-1ubuntu2.14.04.2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/samba/samba-libs_4.1.6+dfsg-1ubuntu2.14.04.2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/samba/libsmbclient_4.1.6+dfsg-1ubuntu2.14.04.2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pango1.0/libpango-1.0-0_1.36.3-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/plymouth/plymouth-label_0.8.8-0ubuntu17_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/plymouth/libplymouth2_0.8.8-0ubuntu17_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/sysvinit/initscripts_2.88dsf-41ubuntu6_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mountall/mountall_2.53_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/upstart/upstart_1.12.1-0ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/linux/linux-libc-dev_3.13.0-30.55_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/linux/linux-libc-dev_3.13.0-30.55_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgpg-error/libgpg-error0_1.12-0.2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgpg-error/libgpg-error0_1.12-0.2ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libf/libffi/libffi-dev_3.1~rc1+r3.0.13-12_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libf/libffi/libffi6_3.1~rc1+r3.0.13-12_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libf/libffi/libffi6_3.1~rc1+r3.0.13-12_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pam/libpam0g_1.1.8-1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libselinux/libselinux1_2.2.2-1ubuntu0.1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libselinux/libselinux1_2.2.2-1ubuntu0.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/sensible-utils/sensible-utils_0.0.9_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/z/zlib/lib32z1-dev_1.2.8.dfsg-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/z/zlib/lib32z1_1.2.8.dfsg-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/z/zlib/zlib1g-dev_1.2.8.dfsg-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/z/zlib/zlib1g-dev_1.2.8.dfsg-1ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/z/zlib/zlib1g_1.2.8.dfsg-1ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/z/zlib/zlib1g_1.2.8.dfsg-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mono/libmono-corlib4.0-cil_3.2.8+dfsg-4ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mono/libmono-i18n4.0-cil_3.2.8+dfsg-4ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mono/libmono-system4.0-cil_3.2.8+dfsg-4ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mono/libmono-system-configuration4.0-cil_3.2.8+dfsg-4ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mono/mono-runtime_3.2.8+dfsg-4ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mono/mono-runtime-common_3.2.8+dfsg-4ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mono/mono-runtime-sgen_3.2.8+dfsg-4ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mono/libmono-security4.0-cil_3.2.8+dfsg-4ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mono/libmono-system-xml4.0-cil_3.2.8+dfsg-4ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mono/libmono-system-security4.0-cil_3.2.8+dfsg-4ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mono/libmono-corlib4.5-cil_3.2.8+dfsg-4ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mono/mono-gac_3.2.8+dfsg-4ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mono/mono-4.0-gac_3.2.8+dfsg-4ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/perl/perl_5.18.2-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libc/libcommon-sense-perl/libcommon-sense-perl_3.72-2build1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/perl/libperl5.18_5.18.2-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/net-snmp/libsnmp30_5.7.2~dfsg-8.1ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/poppler/libpoppler44_0.24.5-2ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qpdf/libqpdf13_5.1.1-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pxljr/printer-driver-pxljr_1.4+repack0-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pidgin/libpurple0_2.10.9-0ubuntu3.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libt/libtext-charwidth-perl/libtext-charwidth-perl_0.04-7build3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libc/libclone-perl/libclone-perl_0.36-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libsub-name-perl/libsub-name-perl_0.05-1build4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libi/libio-pty-perl/libio-pty-perl_1.08-1build4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libh/libhtml-parser-perl/libhtml-parser-perl_3.71-1build1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libc/libcairo-perl/libcairo-perl_1.104-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/perl/perl-base_5.18.2-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libl/liblocale-gettext-perl/liblocale-gettext-perl_1.05-7build3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libn/libnet-ssleay-perl/libnet-ssleay-perl_1.58-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libj/libjson-xs-perl/libjson-xs-perl_2.340-1build1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libg/libglib-perl/libglib-perl_1.304-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libg/libgtk2-perl/libgtk2-perl_1.249-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/liba/libalgorithm-diff-xs-perl/libalgorithm-diff-xs-perl_0.04-2build4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libn/libnet-dns-perl/libnet-dns-perl_0.68-1.2build1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libu/libuuid-perl/libuuid-perl_0.05-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libt/libtext-iconv-perl/libtext-iconv-perl_1.7-5build2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/liba/libapt-pkg-perl/libapt-pkg-perl_0.1.29build1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libp/libpango-perl/libpango-perl_1.224-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxml-parser-perl/libxml-parser-perl_2.41-1build3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libsocket6-perl/libsocket6-perl_0.25-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/perl/perl-modules_5.18.2-2ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/texinfo/install-info_5.2.0.dfsg.1-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lm-sensors/libsensors4_3.3.4-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/openssl/libssl-doc_1.0.1f-1ubuntu2.4_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/openssl/libssl-dev_1.0.1f-1ubuntu2.4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/openssl/libssl1.0.0_1.0.1f-1ubuntu2.4_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/openssl/libssl1.0.0_1.0.1f-1ubuntu2.4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/tcp-wrappers/libwrap0_7.6.q-25_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/tcp-wrappers/libwrap0_7.6.q-25_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/net-snmp/libsnmp-base_5.7.2~dfsg-8.1ubuntu3_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mime-support/mime-support_3.54ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/ncurses/libncursesw5-dev_5.9+20140118-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/ncurses/libncursesw5_5.9+20140118-1ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/ncurses/libncursesw5_5.9+20140118-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/ncurses/libtinfo5_5.9+20140118-1ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/ncurses/libtinfo5_5.9+20140118-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/ncurses/ncurses-bin_5.9+20140118-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/ncurses/lib32ncurses5_5.9+20140118-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/ncurses/lib32tinfo-dev_5.9+20140118-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/ncurses/lib32tinfo5_5.9+20140118-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/ncurses/lib32ncurses5-dev_5.9+20140118-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/ncurses/libncurses5-dev_5.9+20140118-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/ncurses/libtinfo-dev_5.9+20140118-1ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/ncurses/libtinfo-dev_5.9+20140118-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/ncurses/libncurses5_5.9+20140118-1ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/ncurses/libncurses5_5.9+20140118-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/readline6/libreadline-dev_6.3-4ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/readline6/libreadline6-dev_6.3-4ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/readline6/libreadline6-dev_6.3-4ubuntu2_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/readline6/readline-common_6.3-4ubuntu2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/readline6/libreadline6_6.3-4ubuntu2_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/readline6/libreadline6_6.3-4ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/sqlite3/libsqlite3-dev_3.8.2-1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/sqlite3/libsqlite3-0_3.8.2-1ubuntu2_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/sqlite3/libsqlite3-0_3.8.2-1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xz-utils/xz-utils_5.1.1alpha+20120614-2ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libj/libjpeg-turbo/libjpeg-turbo8_1.3.0-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libj/libjpeg-turbo/libjpeg-turbo8_1.3.0-0ubuntu2_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libj/libjpeg8-empty/libjpeg8_8c-2ubuntu8_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libj/libjpeg8-empty/libjpeg8_8c-2ubuntu8_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libp/libpng/libpng12-dev_1.2.50-1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libp/libpng/libpng12-0_1.2.50-1ubuntu2_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libp/libpng/libpng12-0_1.2.50-1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/ucf/ucf_3.0027+nmu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pixman/libpixman-1-dev_0.30.2-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pixman/libpixman-1-0_0.30.2-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pixman/libpixman-1-0_0.30.2-2ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libx11/libx11-data_1.6.2-1ubuntu2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xorg-sgml-doctools/xorg-sgml-doctools_1.11-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/x11proto-core/x11proto-core-dev_7.0.24-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxau/libxau-dev_1.0.8-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxau/libxau-dev_1.0.8-1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxau/libxau6_1.0.8-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxau/libxau6_1.0.8-1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxdmcp/libxdmcp-dev_1.1.1-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxdmcp/libxdmcp-dev_1.1.1-1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxdmcp/libxdmcp6_1.1.1-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxdmcp/libxdmcp6_1.1.1-1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/x11proto-input/x11proto-input-dev_2.3-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/x11proto-kb/x11proto-kb-dev_1.0.6-2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xtrans/xtrans-dev_1.3.2-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libp/libpthread-stubs/libpthread-stubs0-dev_0.3-4_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libp/libpthread-stubs/libpthread-stubs0-dev_0.3-4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libx11/libx11-dev_1.6.2-1ubuntu2_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libx11/libx11-dev_1.6.2-1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xkeyboard-config/xkb-data_2.10.1-1ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libx11/libx11-6_1.6.2-1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libx11/libx11-6_1.6.2-1ubuntu2_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcb/libxcb-render0-dev_1.10-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcb/libxcb-render0_1.10-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcb/libxcb-render0_1.10-2ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcb/libxcb-shm0-dev_1.10-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcb/libxcb-shm0_1.10-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcb/libxcb-shm0_1.10-2ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/x11proto-xext/x11proto-xext-dev_7.3.0-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxext/libxext-dev_1.3.2-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxext/libxext6_1.3.2-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxext/libxext6_1.3.2-1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxrender/libxrender-dev_0.9.8-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxrender/libxrender1_0.9.8-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxrender/libxrender1_0.9.8-1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libp/libproxy/libproxy1-plugin-gsettings_0.4.11-0ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libp/libproxy/libproxy1-plugin-networkmanager_0.4.11-0ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libp/libproxy/libproxy1_0.4.11-0ubuntu4_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libp/libproxy/libproxy1_0.4.11-0ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xft/libxft-dev_2.3.1-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xft/libxft2_2.3.1-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xft/libxft2_2.3.1-2_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libt/libthai/libthai-data_0.1.20-3_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libd/libdatrie/libdatrie1_0.2.8-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libd/libdatrie/libdatrie1_0.2.8-1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libt/libthai/libthai0_0.1.20-3_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libt/libthai/libthai0_0.1.20-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/sysvinit/sysvinit-utils_2.88dsf-41ubuntu6_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/tzdata/tzdata-java_2014e-0ubuntu0.14.04_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/tzdata/tzdata_2014e-0ubuntu0.14.04_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/util-linux/util-linux_2.20.1-5.1ubuntu20.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/makedev/makedev_2.3.1-93ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/util-linux/mount_2.20.1-5.1ubuntu20.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libsemanage/libsemanage-common_2.2-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libsepol/libsepol1_2.2-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/ustr/libustr-1.0-1_1.0.4-3ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libsemanage/libsemanage1_2.2-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pam/libpam-modules-bin_1.1.8-1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pam/libpam-modules_1.1.8-1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/shadow/passwd_4.1.5.1-1ubuntu9_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mscompress/mscompress_0.4-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/policykit-1/libpolkit-gobject-1-0_0.105-4ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libc/libcroco/libcroco3_0.6.8-2ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libc/libcroco/libcroco3_0.6.8-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxinerama/libxinerama-dev_1.1.3-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxinerama/libxinerama1_1.1.3-1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxinerama/libxinerama1_1.1.3-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xorg/x11-common_7.7+1ubuntu8_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libi/libice/libice-dev_1.0.8-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libi/libice/libice6_1.0.8-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libi/libice/libice6_1.0.8-2_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libsm/libsm-dev_1.2.1-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/util-linux/libuuid1_2.20.1-5.1ubuntu20.1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/util-linux/libuuid1_2.20.1-5.1ubuntu20.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libsm/libsm6_1.2.1-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libsm/libsm6_1.2.1-2_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxt/libxt-dev_1.1.4-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxt/libxt6_1.1.4-1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxt/libxt6_1.1.4-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxmu/libxmu6_1.1.1-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxmu/libxmu6_1.1.1-1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxpm/libxpm4_3.5.10-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxpm/libxpm4_3.5.10-1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxaw/libxaw7_1.0.12-1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxaw/libxaw7_1.0.12-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxkbfile/libxkbfile1_1.0.8-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/x11-xkb-utils/x11-xkb-utils_7.7+1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/x11proto-fixes/x11proto-fixes-dev_5.0-2ubuntu2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libd/libdrm/libdrm-dev_2.4.52-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libd/libdrm/libdrm2_2.4.52-1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libd/libdrm/libdrm2_2.4.52-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libp/libpciaccess/libpciaccess0_0.13.2-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libp/libpciaccess/libpciaccess0_0.13.2-1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libd/libdrm/libdrm-intel1_2.4.52-1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libd/libdrm/libdrm-intel1_2.4.52-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libd/libdrm/libdrm-radeon1_2.4.52-1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libd/libdrm/libdrm-radeon1_2.4.52-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libd/libdrm/libdrm-nouveau2_2.4.52-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xcb-util/libxcb-util0_0.3.8-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxv/libxv1_1.0.10-1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxv/libxv1_1.0.10-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxvmc/libxvmc1_1.0.8-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mtdev/libmtdev1_1.1.4-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libf/libfontenc/libfontenc1_1.1.2-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxfont/libxfont1_1.4.7-1ubuntu0.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxdamage/libxdamage-dev_1.1.4-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxdamage/libxdamage1_1.1.4-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxdamage/libxdamage1_1.1.4-1ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libglu/libglu1-mesa-dev_9.0.0-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libglu/libglu1-mesa_9.0.0-2_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libglu/libglu1-mesa_9.0.0-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libsigc++-2.0/libsigc++-2.0-dev_2.2.10-0.2ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libsigc++-2.0/libsigc++-2.0-0c2a_2.2.10-0.2ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgee/libgee2_0.6.8-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xapian-core/libxapian22_1.2.16-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libz/libzeitgeist/libzeitgeist-1.0-1_0.3.18-1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libd/libdbusmenu/gir1.2-dbusmenu-gtk-0.4_12.10.3+14.04.20140612-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libd/libdbusmenu/libdbusmenu-gtk4_12.10.3+14.04.20140612-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libd/libdbusmenu/gir1.2-dbusmenu-glib-0.4_12.10.3+14.04.20140612-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libd/libdbusmenu/libdbusmenu-glib4_12.10.3+14.04.20140612-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcomposite/libxcomposite-dev_0.4.4-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcomposite/libxcomposite1_0.4.4-1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcomposite/libxcomposite1_0.4.4-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcursor/libxcursor-dev_1.1.14-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcursor/libxcursor1_1.1.14-1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcursor/libxcursor1_1.1.14-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxrandr/libxrandr-dev_1.4.2-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxrandr/libxrandr2_1.4.2-1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxrandr/libxrandr2_1.4.2-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/x11proto-randr/x11proto-randr-dev_1.4.0+git20120101.is.really.1.4.0-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/shared-mime-info/shared-mime-info_1.2-0ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gtk+2.0/gtk2-engines-pixbuf_2.24.23-0ubuntu1.1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxi/libxi-dev_1.7.1.901-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxi/libxi6_1.7.1.901-1ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxi/libxi6_1.7.1.901-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/ubuntu-themes/ubuntu-mono_14.04+14.04.20140410-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libt/libtool/libltdl-dev_2.4.2-1.7ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libt/libtool/libltdl7_2.4.2-1.7ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libt/libtool/libltdl7_2.4.2-1.7ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libv/libvorbis/libvorbisenc2_1.3.2-1.3ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libv/libvorbis/libvorbisenc2_1.3.2-1.3ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libo/libogg/libogg0_1.3.1-1ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libo/libogg/libogg0_1.3.1-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libv/libvorbis/libvorbisfile3_1.3.2-1.3ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libv/libvorbis/libvorbisfile3_1.3.2-1.3ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libv/libvorbis/libvorbis0a_1.3.2-1.3ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libv/libvorbis/libvorbis0a_1.3.2-1.3ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/sound-theme-freedesktop/sound-theme-freedesktop_0.8-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libc/libcanberra/libcanberra-pulse_0.30-0ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libc/libcanberra/libcanberra0_0.30-0ubuntu3_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libc/libcanberra/libcanberra0_0.30-0ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/liba/libasyncns/libasyncns0_0.8-4ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/liba/libasyncns/libasyncns0_0.8-4ubuntu2_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libsndfile/libsndfile1_1.0.25-7ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libsndfile/libsndfile1_1.0.25-7ubuntu2_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/f/fftw3/libfftw3-3_3.3.3-7ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pam/libpam-runtime_1.1.8-1ubuntu2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/systemd/libpam-systemd_204-5ubuntu20.3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libsamplerate/libsamplerate0_0.1.8-7_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libsamplerate/libsamplerate0_0.1.8-7_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/speex/libspeexdsp1_1.2~rc1.1-1ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/speex/libspeexdsp1_1.2~rc1.1-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pulseaudio/pulseaudio_4.0-0ubuntu11_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libc/libcanberra/libcanberra-gtk3-0_0.30-0ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libc/libcanberra/gnome-session-canberra_0.30-0ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libc/libcanberra/libcanberra-gtk0_0.30-0ubuntu3_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libc/libcanberra/libcanberra-gtk0_0.30-0ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/startup-notification/libstartup-notification0_0.12-3ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/z/zenity/zenity_3.8.0-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/z/zenity/zenity-common_3.8.0-1ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/libreoffice-l10n/libreoffice-l10n-en-za_4.2.4-0ubuntu2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/libreoffice-l10n/libreoffice-l10n-en-gb_4.2.4-0ubuntu2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libr/libreoffice/libreoffice-emailmerge_4.2.4-0ubuntu2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/libreoffice/libreoffice-style-human_4.2.4-0ubuntu2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/libreoffice/libreoffice-calc_4.2.4-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/libreoffice/libreoffice-impress_4.2.4-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/libreoffice/libreoffice-draw_4.2.4-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/libreoffice/libreoffice-style-tango_4.2.4-0ubuntu2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/libreoffice/libreoffice-common_4.2.4-0ubuntu2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/libreoffice/libreoffice-gtk_4.2.4-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/libreoffice/libreoffice-writer_4.2.4-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/libreoffice/libreoffice-core_4.2.4-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/libreoffice/libreoffice-gnome_4.2.4-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/libreoffice/libreoffice-base-core_4.2.4-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/libreoffice/libreoffice-math_4.2.4-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/libreoffice/ure_4.2.4-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/libreoffice/uno-libs3_4.2.4-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/suitesparse/libcolamd2.8.0_4.2.1-3ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lp-solve/lp-solve_5.5.0.13-7build1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libi/libidn/libidn11_1.28-1ubuntu2_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libi/libidn/libidn11_1.28-1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/openldap/libldap-2.4-2_2.4.31-1+nmu2ubuntu8_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/openldap/libldap-2.4-2_2.4.31-1+nmu2ubuntu8_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/rtmpdump/librtmp0_2.4+20121230.gitdf6c518-1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/rtmpdump/librtmp0_2.4+20121230.gitdf6c518-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libc/libcmis/libcmis-0.4-4_0.4.1-3ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libe/libexttextcat/libexttextcat-data_3.4.3-1ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libe/libexttextcat/libexttextcat-2.0-0_3.4.3-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libl/liblangtag/liblangtag-common_0.5.1-2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libl/liblangtag/liblangtag1_0.5.1-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/y/yajl/libyajl2_2.0.4-4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxslt/libxslt1.1_1.1.28-2build1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxslt/libxslt1.1_1.1.28-2build1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/raptor2/libraptor2-0_2.0.13-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mhash/libmhash2_0.9.9.9-4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/rasqal/librasqal3_0.9.32-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/redland/librdf0_1.0.17-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libw/libwpd/libwpd-0.9-9_0.9.9-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libw/libwpg/libwpg-0.2-2_0.2.2-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libw/libwps/libwps-0.2-2_0.2.9-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libo/liborcus/liborcus-0.6-0_0.5.1-7_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libc/libcdr/libcdr-0.0-0_0.0.15-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libm/libmspub/libmspub-0.0-0_0.0.6-1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libv/libvisio/libvisio-0.0-0_0.0.31-1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/psmisc/psmisc_22.20-1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/libreoffice/fonts-opensymbol_102.6+LibO4.2.4-0ubuntu2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mythes/libmythes-1.2-0_1.2.2-1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/neon27/libneon27-gnutls_0.30.0-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/libreoffice-dictionaries/myspell-en-za_4.2.1-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/libreoffice-dictionaries/myspell-en-gb_4.2.1-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/openoffice.org-en-au/myspell-en-au_2.1-5.4_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/libreoffice-dictionaries/hunspell-en-ca_4.2.1-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libc/libcap-ng/libcap-ng0_0.7.3-1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libc/libcap2/libcap2-bin_2.24-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libc/libcap2/libpam-cap_2.24-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/liba/libassuan/libassuan0_2.1.1-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libu/libusb/libusb-0.1-4_0.1.12-23.3ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libu/libusb/libusb-0.1-4_0.1.12-23.3ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/systemd/libgudev-1.0-0_204-5ubuntu20.3_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/systemd/libgudev-1.0-0_204-5ubuntu20.3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libt/libtheora/libtheora0_1.1.1+dfsg.1-3.2_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libt/libtheora/libtheora0_1.1.1+dfsg.1-3.2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libv/libvisual/libvisual-0.4-0_0.4.0-5_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libv/libvisual/libvisual-0.4-0_0.4.0-5_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/slang2/libslang2-dev_2.2.4-15ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/slang2/libslang2_2.2.4-15ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/slang2/libslang2_2.2.4-15ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/libraw1394/libraw1394-11_2.1.0-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/libraw1394/libraw1394-11_2.1.0-1ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/liba/libavc1394/libavc1394-0_0.5.4-2_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/liba/libavc1394/libavc1394-0_0.5.4-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libc/libcaca/libcaca-dev_0.99.beta18-1ubuntu5_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libc/libcaca/libcaca0_0.99.beta18-1ubuntu5_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libc/libcaca/libcaca0_0.99.beta18-1ubuntu5_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libd/libdv/libdv4_1.0.0-6_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libd/libdv/libdv4_1.0.0-6_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libi/libiec61883/libiec61883-0_1.2.0-0.1ubuntu3_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libi/libiec61883/libiec61883-0_1.2.0-0.1ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/speex/libspeex1_1.2~rc1.1-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/speex/libspeex1_1.2~rc1.1-1ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libshout/libshout3_2.3.1-3_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libshout/libshout3_2.3.1-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/taglib/libtag1-vanilla_1.9.1-2_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/taglib/libtag1-vanilla_1.9.1-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/taglib/libtag1c2a_1.9.1-2_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/taglib/libtag1c2a_1.9.1-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/v/v4l-utils/libv4lconvert0_1.0.1-1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/v/v4l-utils/libv4lconvert0_1.0.1-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/v/v4l-utils/libv4l-0_1.0.1-1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/v/v4l-utils/libv4l-0_1.0.1-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/wavpack/libwavpack1_4.70.0-1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/wavpack/libwavpack1_4.70.0-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libsoup2.4/libsoup-gnome2.4-1_2.44.2-1ubuntu2_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libsoup2.4/libsoup-gnome2.4-1_2.44.2-1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/librest/librest-0.7-0_0.7.90-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libn/libnice/libnice10_0.1.4-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libo/liboauth/liboauth0_1.0.1-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgdata/libgdata-common_0.14.1-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgdata/libgdata13_0.14.1-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/telepathy-gabble/telepathy-gabble_0.18.3-0ubuntu0.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/telepathy-mission-control-5/telepathy-mission-control-5_5.16.1-1ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/telepathy-mission-control-5/libmission-control-plugins0_5.16.1-1ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/network-manager/libnm-util2_0.9.8.8-0ubuntu7_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/network-manager/libnm-glib4_0.9.8.8-0ubuntu7_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/upower/libupower-glib1_0.9.23-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/telepathy-logger/telepathy-logger_0.8.0-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libe/libexif/libexif12_0.6.21-1ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libe/libexif/libexif12_0.6.21-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxtst/libxtst6_1.2.2-1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxtst/libxtst6_1.2.2-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/liba/libatasmart/libatasmart4_0.19-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/policykit-1/libpolkit-agent-1-0_0.105-4ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/util-linux/libblkid1_2.20.1-5.1ubuntu20.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/parted/libparted0debian1_2.3-19ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/parted/parted_2.3-19ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lzo2/liblzo2-2_2.06-1.2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/nettle/libnettle4_2.7.1-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libu/libusbx/libusb-1.0-0_1.0.17-1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libp/libplist/libplist1_1.10-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/usbmuxd/usbmuxd_1.0.8-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libm/libmtp/libmtp-common_1.1.6-20-g1b9f164-1ubuntu2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/talloc/libtalloc2_2.1.0-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-crypto/python-crypto_2.6.1-4build1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/popt/libpopt0_1.16-8ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxres/libxres1_1.0.7-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libw/libwnck3/libwnck-3-common_3.4.7-0ubuntu3_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libw/libwnck3/libwnck-3-0_3.4.7-0ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/notify-osd/notify-osd_0.9.35+14.04.20140213-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/powermgmt-base/powermgmt-base_1.31build1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pm-utils/pm-utils_1.4.1-13_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/upower/upower_0.9.23-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libd/libdbusmenu/libdbusmenu-gtk3-4_12.10.3+14.04.20140612-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libi/libindicator/libindicator3-7_12.10.2+14.04.20140402-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/liba/libappindicator/libappindicator3-1_12.10.1+13.10.20130920-0ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/miniupnpc/libminiupnpc8_1.6-3ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/ubuntu-keyring/ubuntu-keyring_2012.05.19_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lsb/lsb-release_4.1+Debian11ubuntu6_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/ubuntu-release-upgrader/python3-distupgrade_0.220.2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/v/vte3/libvte-2.90-9_0.34.9-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/v/vte3/libvte-2.90-common_0.34.9-1ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/v/vte3/gir1.2-vte-2.90_0.34.9-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/webkitgtk/gir1.2-webkit-3.0_2.4.3-1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/webkitgtk/gir1.2-javascriptcoregtk-3.0_2.4.3-1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libsoup2.4/gir1.2-soup-2.4_2.44.2-1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/ubuntu-release-upgrader/ubuntu-release-upgrader-gtk_0.220.2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/policykit-1/libpolkit-backend-1-0_0.105-4ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/policykit-1/policykit-1_0.105-4ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/six/python-six_1.5.2-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-debian/python-debian_0.1.21+nmu2ubuntu2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/patch/patch_2.7.1-4ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/update-notifier/update-notifier_0.154.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/update-notifier/update-notifier-common_0.154.1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/policykit-1-gnome/policykit-1-gnome_0.105-1ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/update-manager/update-manager-core_0.196.12_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/update-manager/update-manager_0.196.12_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/ubuntu-release-upgrader/ubuntu-release-upgrader-core_0.220.2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/update-manager/python3-update-manager_0.196.12_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pycurl/python3-pycurl_7.19.3-0ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unattended-upgrades/unattended-upgrades_0.82.1ubuntu2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/software-properties/python3-software-properties_0.92.37.1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/x-kit/python3-xkit_0.5.0ubuntu2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/u/ubuntu-drivers-common/nvidia-common_0.2.91.5_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pciutils/pciutils_3.2.1-1ubuntu5_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pciutils/libpci3_3.2.1-1ubuntu5_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/usbutils/usbutils_007-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/newt/libnewt0.52_0.52.15-2ubuntu5_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/newt/whiptail_0.52.15-2ubuntu5_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/ubuntu-drivers-common/ubuntu-drivers-common_0.2.91.5_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pycurl/python-pycurl_7.19.3-0ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/s/software-properties/python-software-properties_0.92.37.1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/o/openjdk-6/openjdk-6-jre-lib_6b31-1.13.3-1ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/o/openjdk-6/icedtea-6-jre-cacao_6b31-1.13.3-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/o/openjdk-6/icedtea-6-jre-jamvm_6b31-1.13.3-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pcsc-lite/libpcsclite1_1.8.10-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/o/openjdk-6/openjdk-6-jre-headless_6b31-1.13.3-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/openssl/openssl_1.0.1f-1ubuntu2.4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/software-properties/software-properties-common_0.92.37.1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/software-properties/software-properties-gtk_0.92.37.1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/procps/libprocps3_3.3.9-1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/procps/procps_3.3.9-1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/update-inetd/update-inetd_4.43_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libc/libcdio/libcdio13_0.83-4.1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libc/libcdio/libcdio-cdda1_0.83-4.1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libc/libcdio/libcdio-paranoia1_0.83-4.1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python3.4/libpython3.4_3.4.0-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libp/libpeas/libpeas-common_1.8.1-2ubuntu2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libp/libpeas/libpeas-1.0-0_1.8.1-2ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libp/libpeas/gir1.2-peas-1.0_1.8.1-2ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libd/libdmapsharing/libdmapsharing-3.0-2_2.9.24-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgpod/libgpod4_0.8.3-4ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lirc/liblircclient0_0.9.0-0ubuntu5_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-httplib2/python-httplib2_0.8-2build1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/piston-mini-client/python-piston-mini-client_0.7.5-0ubuntu2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-defer/python-defer_1.0.6-2build1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-setuptools/python-pkg-resources_3.3-1ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pyxdg/python-xdg_0.25-4_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pycairo/python-cairo_1.8.8-1ubuntu5_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xapian-bindings/python-xapian_1.2.16-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pyopenssl/python-openssl_0.13-2ubuntu6_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/twisted/python-twisted-bin_13.2.0-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/z/zope.interface/python-zope.interface_4.0.5-1ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/twisted/python-twisted-core_13.2.0-1ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/twisted/python-twisted-web_13.2.0-1ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/ubuntu-sso-client/ubuntu-sso-client_13.10-0ubuntu6_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/ubuntu-sso-client/python-ubuntu-sso-client_13.10-0ubuntu6_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-crypto/python3-crypto_2.6.1-4build1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-oauthlib/python3-oauthlib_0.6.1-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-httplib2/python3-httplib2_0.8-2build1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/piston-mini-client/python3-piston-mini-client_0.7.5-0ubuntu2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pyxdg/python3-xdg_0.25-4_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/oneconf/python3-oneconf_0.3.7_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/oneconf/oneconf_0.3.7_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libb/libburn/libburn4_1.3.4-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libi/libisofs/libisofs6_1.3.4-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/f/file/python-magic_5.14-2ubuntu3_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pygobject-2/python-gobject-2_2.28.6-12build1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pygobject/python-gobject_3.12.0-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/z/zeitgeist/python-zeitgeist_0.9.14-0ubuntu4_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/z/zeitgeist/zeitgeist-core_0.9.14-0ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/media-player-info/media-player-info_21-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxmu/libxmuu1_1.1.1-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxxf86dga/libxxf86dga1_1.1.4-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/x11-utils/x11-utils_7.7+1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/sed/sed_4.2.2-4ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/obexd/obexd-client_0.46-1ubuntu7_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libo/libopenobex/libopenobex1_1.5-2.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/obex-data-server/obex-data-server_0.4.6-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxklavier/libxklavier16_5.4-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libg/libgnome-media-profiles/libgnome-media-profiles-3.0-0_3.0.0-1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgtop2/libgtop2-common_2.28.5-2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgtop2/libgtop2-7_2.28.5-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/network-manager-applet/libnm-gtk-common_0.9.8.8-0ubuntu4.2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/network-manager-applet/libnm-gtk0_0.9.8.8-0ubuntu4.2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libw/libwnck/libwnck-common_2.30.7-0ubuntu4_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libw/libwnck/libwnck22_2.30.7-0ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libu/libunity-misc/libunity-misc4_4.0.5+14.04.20140115-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/nux/nux-tools_4.0.6+14.04.20140409-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity-asset-pool/unity-asset-pool_0.8.24daily13.06.10-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lightdm/liblightdm-gobject-1-0_1.10.1-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity-greeter/unity-greeter_14.04.10-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/netbase/netbase_5.2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgrip/libgrip0_0.3.7+14.04.20140303-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/poppler/poppler-utils_0.24.5-2ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/wget/wget_1.15-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libp/libpaper/libpaper1_1.1.24+nmu2ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/ssl-cert/ssl-cert_1.0.33_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/poppler-data/poppler-data_0.4.6-4_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libv/libvpx/libvpx1_1.3.0-2_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgd2/libgd3_2.1.0-3_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libu/libusbx/libusb-1.0-0_1.0.17-1ubuntu2_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgphoto2/libgphoto2-port10_2.5.3.1-1ubuntu2.2_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgphoto2/libgphoto2-6_2.5.3.1-1ubuntu2.2_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libi/libieee1284/libieee1284-3_0.2.11-12_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libi/libieee1284/libieee1284-3_0.2.11-12_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/sane-backends/libsane_1.0.23-3ubuntu3.1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/sane-backends/libsane_1.0.23-3ubuntu3.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/sane-backends/libsane-common_1.0.23-3ubuntu3.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libw/libwebp/libwebpmux1_0.4.0-4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pillow/python-imaging_2.3.0-1ubuntu3_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pillow/python-pil_2.3.0-1ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pexpect/python-pexpect_3.1-1ubuntu0.1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-reportlab/python-reportlab-accel_3.0-1build1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-reportlab/python-reportlab_3.0-1build1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libn/libnice/gstreamer0.10-nice_0.1.4-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/meanwhile/libmeanwhile1_1.0.2-4.1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/z/zephyr/libzephyr4_3.1.2-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libu/liburi-perl/liburi-perl_1.60-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/liba/libalgorithm-diff-perl/libalgorithm-diff-perl_1.19.02-3_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libn/libnet-ip-perl/libnet-ip-perl_1.26-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libi/libio-socket-inet6-perl/libio-socket-inet6-perl_2.71-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libn/libnet-http-perl/libnet-http-perl_6.06-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libi/libio-socket-ssl-perl/libio-socket-ssl-perl_1.965-1ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libl/liblwp-protocol-https-perl/liblwp-protocol-https-perl_6.04-2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libt/libtimedate-perl/libtimedate-perl_2.3000-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libh/libhttp-date-perl/libhttp-date-perl_6.02-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libi/libio-html-perl/libio-html-perl_1.00-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libe/libencode-locale-perl/libencode-locale-perl_1.03-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libl/liblwp-mediatypes-perl/liblwp-mediatypes-perl_6.02-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libh/libhttp-message-perl/libhttp-message-perl_6.06-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libh/libhttp-daemon-perl/libhttp-daemon-perl_6.01-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libf/libfile-listing-perl/libfile-listing-perl_6.04-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libh/libhtml-form-perl/libhtml-form-perl_6.03-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libh/libhtml-tree-perl/libhtml-tree-perl_5.03-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libw/libwww-perl/libwww-perl_6.05-2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pkg-config/pkg-config_0.26-1ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity-control-center/libunity-control-center1_14.04.3+14.04.20140604-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/whoopsie-preferences/libwhoopsie-preferences0_0.12_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/z/zeitgeist/zeitgeist-datahub_0.9.14-0ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/z/zeitgeist/zeitgeist_0.9.14-0ubuntu4_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/whoopsie/libwhoopsie0_0.2.24.6_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/whoopsie-preferences/whoopsie-preferences_0.12_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/geany-plugins/geany-plugin-numberedbookmarks_1.23+dfsg-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/geany-plugins/geany-plugin-latex_1.23+dfsg-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/geany-plugins/geany-plugin-shiftcolumn_1.23+dfsg-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/geany-plugins/geany-plugin-insertnum_1.23+dfsg-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/geany-plugins/geany-plugin-doc_1.23+dfsg-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/geany-plugins/geany-plugin-spellcheck_1.23+dfsg-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/geany-plugins/geany-plugin-pg_1.23+dfsg-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/geany-plugins/geany-plugin-gendoc_1.23+dfsg-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/geany-plugins/geany-plugin-lua_1.23+dfsg-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/geany-plugins/geany-plugin-sendmail_1.23+dfsg-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/geany-plugins/geany-plugin-extrasel_1.23+dfsg-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/geany-plugins/geany-plugin-prettyprinter_1.23+dfsg-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/geany-plugins/geany-plugin-xmlsnippets_1.23+dfsg-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/geany-plugins/geany-plugins_1.23+dfsg-3_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/geany-plugins/geany-plugin-debugger_1.23+dfsg-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/geany-plugins/geany-plugin-addons_1.23+dfsg-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/geany-plugins/geany-plugin-prj_1.23+dfsg-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/geany-plugins/geany-plugin-treebrowser_1.23+dfsg-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/geany-plugins/geany-plugin-updatechecker_1.23+dfsg-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/geany-plugins/geany-plugin-codenav_1.23+dfsg-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/geany-plugins/geany-plugin-macro_1.23+dfsg-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/geany-plugins/geany-plugin-vc_1.23+dfsg-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/geany-plugins/geany-plugin-tableconvert_1.23+dfsg-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/geany-plugins/geany-plugin-lipsum_1.23+dfsg-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/geany-plugins/geany-plugin-webhelper_1.23+dfsg-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/geany-plugins/geany-plugin-gproject_1.23+dfsg-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/geany-plugins/geany-plugins-common_1.23+dfsg-3_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/geany/geany_1.23.1+dfsg-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/geany/geany-common_1.23.1+dfsg-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/c/ctpl/libctpl2_0.3.3.dfsg-4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lua5.1/liblua5.1-0_5.1.5-5_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/v/vte/libvte9_0.28.2-5ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/v/vte/libvte-common_0.28.2-5ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/webkitgtk/libwebkitgtk-1.0-0_2.4.3-1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/webkitgtk/libjavascriptcoregtk-1.0-0_2.4.3-1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/webkitgtk/libwebkitgtk-1.0-common_2.4.3-1ubuntu2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/geany-plugins/geany-plugin-devhelp_1.23+dfsg-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/geany-plugins/geany-plugin-geniuspaste_1.23+dfsg-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/geany-plugins/geany-plugin-miniscript_1.23+dfsg-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/geany-plugins/geany-plugin-multiterm_1.23+dfsg-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgxps/libgxps2_0.2.2-2ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/texlive-bin/libkpathsea6_2013.20130729.30972-2build3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/poppler/libpoppler-glib8_0.24.5-2ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libspectre/libspectre1_0.2.7-2ubuntu1.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/t1lib/libt1-5_5.1.2-3.6ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/a/anjuta/libanjuta-3-0_3.10.2-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/a/anjuta/anjuta_3.10.2-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gdl/libgdl-3-common_3.8.1-2ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gdl/libgdl-3-5_3.8.1-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/a/anjuta/anjuta-common_3.10.2-0ubuntu2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libg/libgda5/libgda-5.0-common_5.2.2-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libg/libgda5/libgda-5.0-4_5.2.2-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/glade/glade_3.16.1-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/serf/libserf-1-1_1.3.3-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/subversion/libsvn1_1.8.8-1ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/v/vala-0.20/libvala-0.20-0_0.20.1-2ubuntu5_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/telepathy-indicator/telepathy-indicator_0.3.1+14.04.20140411-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/overlay-scrollbar/overlay-scrollbar_0.2.16+r359+14.04.20131129-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/overlay-scrollbar/overlay-scrollbar-gtk2_0.2.16+r359+14.04.20131129-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/overlay-scrollbar/overlay-scrollbar-gtk3_0.2.16+r359+14.04.20131129-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lua5.2/liblua5.2-0_5.2.3-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/rpm/librpmio3_4.11.1-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/rpm/librpm3_4.11.1-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/rpm/rpm2cpio_4.11.1-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/rpm/rpm_4.11.1-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/rpm/rpm-common_4.11.1-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/rpm/librpmbuild3_4.11.1-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/rpm/librpmsign1_4.11.1-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/rpm/debugedit_4.11.1-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qt4-x11/libqt4-opengl_4.8.5+git192-g085f851+dfsg-2ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qt4-x11/libqt4-opengl_4.8.5+git192-g085f851+dfsg-2ubuntu4_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qt4-x11/libqt4-qt3support_4.8.5+git192-g085f851+dfsg-2ubuntu4_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qt4-x11/libqt4-qt3support_4.8.5+git192-g085f851+dfsg-2ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qt4-x11/libqt4-svg_4.8.5+git192-g085f851+dfsg-2ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qt4-x11/libqt4-svg_4.8.5+git192-g085f851+dfsg-2ubuntu4_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qt4-x11/libqt4-declarative_4.8.5+git192-g085f851+dfsg-2ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qt4-x11/libqt4-declarative_4.8.5+git192-g085f851+dfsg-2ubuntu4_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qt4-x11/libqtgui4_4.8.5+git192-g085f851+dfsg-2ubuntu4_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qt4-x11/libqtgui4_4.8.5+git192-g085f851+dfsg-2ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qt4-x11/libqt4-scripttools_4.8.5+git192-g085f851+dfsg-2ubuntu4_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qt4-x11/libqt4-designer_4.8.5+git192-g085f851+dfsg-2ubuntu4_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qt4-x11/libqt4-designer_4.8.5+git192-g085f851+dfsg-2ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qt4-x11/libqt4-xmlpatterns_4.8.5+git192-g085f851+dfsg-2ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qt4-x11/libqt4-xmlpatterns_4.8.5+git192-g085f851+dfsg-2ubuntu4_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qt4-x11/qdbus_4.8.5+git192-g085f851+dfsg-2ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qt4-x11/libqt4-script_4.8.5+git192-g085f851+dfsg-2ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qt4-x11/libqt4-script_4.8.5+git192-g085f851+dfsg-2ubuntu4_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qt4-x11/libqt4-network_4.8.5+git192-g085f851+dfsg-2ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qt4-x11/libqt4-network_4.8.5+git192-g085f851+dfsg-2ubuntu4_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qt4-x11/libqt4-dbus_4.8.5+git192-g085f851+dfsg-2ubuntu4_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qt4-x11/libqt4-dbus_4.8.5+git192-g085f851+dfsg-2ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qt4-x11/libqt4-xml_4.8.5+git192-g085f851+dfsg-2ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qt4-x11/libqt4-xml_4.8.5+git192-g085f851+dfsg-2ubuntu4_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qt4-x11/libqt4-sql-mysql_4.8.5+git192-g085f851+dfsg-2ubuntu4_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qt4-x11/libqt4-sql_4.8.5+git192-g085f851+dfsg-2ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qt4-x11/libqt4-sql_4.8.5+git192-g085f851+dfsg-2ubuntu4_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qt4-x11/libqt4-sql-sqlite_4.8.5+git192-g085f851+dfsg-2ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qt4-x11/libqtcore4_4.8.5+git192-g085f851+dfsg-2ubuntu4_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qt4-x11/libqtcore4_4.8.5+git192-g085f851+dfsg-2ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qt4-x11/libqt4-test_4.8.5+git192-g085f851+dfsg-2ubuntu4_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/q/qt4-x11/libqt4-gui_4.8.5+git192-g085f851+dfsg-2ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qtchooser/qtchooser_39-g4717841-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qt4-x11/libqtdbus4_4.8.5+git192-g085f851+dfsg-2ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qt4-x11/libqtdbus4_4.8.5+git192-g085f851+dfsg-2ubuntu4_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mysql-5.5/mysql-common_5.5.37-0ubuntu0.14.04.1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mysql-5.5/libmysqlclient18_5.5.37-0ubuntu0.14.04.1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/nas/libaudio2_1.9.4-1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/nas/libaudio2_1.9.4-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qt4-x11/qtcore4-l10n_4.8.5+git192-g085f851+dfsg-2ubuntu4_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libsdl1.2/libsdl1.2-dev_1.2.15-8ubuntu1.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libsdl1.2/libsdl1.2debian_1.2.15-8ubuntu1.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libsdl1.2/libsdl1.2debian_1.2.15-8ubuntu1.1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libw/libwebp/libwebp5_0.4.0-4_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/s/sdl-image1.2/libsdl-image1.2_1.2.12-5build2_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/s/sdl-image1.2/libsdl-image1.2_1.2.12-5build2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libt/libtar/libtar0_1.2.20-3ubuntu0.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libv/libva/libva1_1.3.0-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libv/libva/libva-x11-1_1.3.0-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libp/libproxy/libproxy-tools_0.4.11-0ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/v/vlc/vlc-plugin-notify_2.1.4-0ubuntu14.04.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/v/vlc/vlc-plugin-pulse_2.1.4-0ubuntu14.04.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/v/vlc/libvlc5_2.1.4-0ubuntu14.04.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/v/vlc/vlc_2.1.4-0ubuntu14.04.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/v/vlc/vlc-data_2.1.4-0ubuntu14.04.1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/v/vlc/vlc-nox_2.1.4-0ubuntu14.04.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/v/vlc/libvlccore7_2.1.4-0ubuntu14.04.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcb/libxcb-composite0_1.10-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xcb-util-keysyms/libxcb-keysyms1_0.3.9-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcb/libxcb-xv0_1.10-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/a/a52dec/liba52-0.7.4_0.7.4-17_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/e/enca/libenca0_1.15-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/liba/libass/libass4_0.10.1-3ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/liba/libav/libavutil52_9.13-0ubuntu0.14.04.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libg/libgsm/libgsm1_1.0.13-4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/l/lame/libmp3lame0_3.99.5+repack1-3ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/o/openjpeg/libopenjpeg2_1.3+dfsg-4.7ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/opus/libopus0_1.1-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/s/schroedinger/libschroedinger-1.0-0_1.0.11-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/x/x264/libx264-142_0.142.2389+git956c8d8-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/x/xvidcore/libxvidcore4_1.3.2-9ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/liba/libav/libavcodec54_9.13-0ubuntu0.14.04.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/liba/libav/libavformat54_9.13-0ubuntu0.14.04.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libl/liblivemedia/libbasicusageenvironment0_2014.01.13-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libb/libbluray/libbluray1_0.5.0-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libc/libcddb/libcddb2_1.3.2-4fakesync2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/c/chromaprint/libchromaprint0_1.1-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/c/crystalhd/libcrystalhd3_0.0~git20110715.fdd2f19-9ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libd/libdc1394-22/libdc1394-22_2.2.1-2ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libd/libdca/libdca0_0.0.5-6ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/d/dirac/libdirac-encoder0_1.0.2-6ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/t/tslib/tsconf_1.0-12_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/t/tslib/libts-0.0-0_1.0-12_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/d/directfb/libdirectfb-1.2-9_1.2.10.0-5_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libd/libdvbpsi/libdvbpsi8_1.0.0-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libd/libdvdread/libdvdread4_4.2.1-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libd/libdvdnav/libdvdnav4_4.2.1-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libe/libebml/libebml4_1.3.0-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/f/faad2/libfaad2_2.7-8_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/nettle/libhogweed2_2.7.1-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gnutls28/libgnutls28_3.2.11-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libl/liblivemedia/libgroupsock1_2014.01.13-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libk/libkate/libkate1_0.4.1-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libl/liblivemedia/liblivemedia23_2014.01.13-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libm/libmad/libmad0_0.15.1b-8ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libm/libmad/libmad0_0.15.1b-8ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libm/libmatroska/libmatroska6_1.4.1-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libm/libmodplug/libmodplug1_0.8.8.4-4.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libm/libmpc/libmpcdec6_0.1~r459-1ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/m/mpeg2dec/libmpeg2-4_0.5.1-5ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libp/libpostproc/libpostproc52_0.git20120821-4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/s/sidplay-libs/libresid-builder0c2a_2.1.1-14_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/s/sidplay-libs/libsidplay2_2.1.1-14_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libs/libssh2/libssh2-1_1.4.3-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/liba/libav/libswscale2_9.13-0ubuntu0.14.04.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/t/twolame/libtwolame0_0.3.13-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libu/libupnp/libupnp6_1.6.17-1.2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libl/liblivemedia/libusageenvironment1_2014.01.13-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libc/libcdio/libiso9660-8_0.83-4.1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/v/vcdimager/libvcdinfo0_0.7.24+dfsg-0.1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/z/zvbi/libzvbi-common_0.2.35-2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/z/zvbi/libzvbi0_0.2.35-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libm/libmikmod/libmikmod2_3.1.16-1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/speech-dispatcher/python3-speechd_0.8-5ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pyatspi/python3-pyatspi_2.10.0+dfsg-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libl/liblouis/liblouis-data_2.5.3-2ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libl/liblouis/liblouis2_2.5.3-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libl/liblouis/python3-louis_2.5.3-2ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libw/libwnck3/gir1.2-wnck-3.0_3.4.7-0ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/i/icoutils/icoutils_0.31.0-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/sudo/sudo_1.8.9p5-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/q/q4wine/q4wine_1.1-r2-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lcms2/liblcms2-2_2.5-0ubuntu4_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/m/mpg123/libmpg123-0_1.16.0-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/m/mpg123/libmpg123-0_1.16.0-1ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/o/openal-soft/libopenal1_1.14-4ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/o/openal-soft/libopenal1_1.14-4ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/o/openal-soft/libopenal-data_1.14-4ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/o/ocl-icd/ocl-icd-libopencl1_2.1.3-4_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/o/ocl-icd/ocl-icd-libopencl1_2.1.3-4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/w/wine1.6/wine1.4-i386_1.6.2-0ubuntu4_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/w/wine1.6/wine1.4_1.6.2-0ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/w/wine1.6/wine1.4-amd64_1.6.2-0ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/w/wine1.6/wine1.6-amd64_1.6.2-0ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libp/libpipeline/libpipeline1_1.3.0-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/w/wine1.6/wine1.6_1.6.2-0ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/w/wine1.6/wine1.6-i386_1.6.2-0ubuntu4_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/shadow/login_4.1.5.1-1ubuntu9_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/tar/tar_1.27.1-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/util-linux/bsdutils_2.20.1-5.1ubuntu20.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/ncurses/ncurses-base_5.9+20140118-1ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/util-linux/libmount1_2.20.1-5.1ubuntu20.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libe/libestr/libestr0_0.1.9-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libl/liblockfile/liblockfile-bin_1.09-6ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libl/liblockfile/liblockfile1_1.09-6ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/ntp/ntpdate_4.2.6.p5+dfsg-3ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/resolvconf/resolvconf_1.69ubuntu1.1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mawk/mawk_1.3.3-17ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libe/libedit/libedit2_3.1-20130712-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libn/libnfnetlink/libnfnetlink0_1.0.1-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/numactl/libnuma1_2.0.9~rc5-1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libp/libpcap/libpcap0.8_1.5.3-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/man-db/man-db_2.6.7.1-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/ntfs-3g/ntfs-3g_2013.1.13AR.1-2ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/popularity-contest/popularity-contest_1.57ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/c/chromium-browser/chromium-browser-l10n_34.0.1847.116-0ubuntu2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/x11proto-scrnsaver/x11proto-scrnsaver-dev_1.2.2-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxss/libxss-dev_1.2.2-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxss/libxss1_1.2.2-1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxss/libxss1_1.2.2-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xdg-utils/xdg-utils_1.1.0~rc1-2ubuntu7_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/c/chromium-browser/chromium-codecs-ffmpeg_34.0.1847.116-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/c/chromium-browser/chromium-browser_34.0.1847.116-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/librsync/librsync1_0.9.7-10_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-lockfile/python-lockfile_0.8-2ubuntu2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libsigsegv/libsigsegv2_2.10-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/m4/m4_1.4.17-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/f/fonts-horai-umefont/fonts-horai-umefont_460-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mpfr4/libmpfr4_3.1.2-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mpclib3/libmpc3_1.0.1-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gtk2-engines-oxygen/gtk2-engines-oxygen_1.4.5-0ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/liba/libaacs/libaacs0_0.7.0-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qtbase-opensource-src/libqt5core5a_5.2.1+dfsg-1ubuntu14.2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qtbase-opensource-src/libqt5xml5_5.2.1+dfsg-1ubuntu14.2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/liba/libaccounts-qt/libaccounts-qt5-1_1.11+14.04.20140410.1-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/liba/libaio/libaio1_0.3.109-4_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/liba/libaio/libaio1_0.3.109-4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/suitesparse/libamd2.3.1_4.2.1-3ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/liba/libao/libao-common_1.1.0-2ubuntu2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/liba/libao/libao4_1.1.0-2ubuntu2_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/liba/libappindicator/python-appindicator_12.10.1+13.10.20130920-0ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libi/libindicator/libindicator7_12.10.2+14.04.20140402-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/liba/libappindicator/libappindicator1_12.10.1+13.10.20130920-0ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/liba/libart-lgpl/libart-2.0-2_2.3.21-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/o/openjdk-6/openjdk-6-jre_6b31-1.13.3-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/linux-atm/libatm1_2.5.1-1.5_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libb/libbonobo/libbonobo2-0_2.32.1-0ubuntu5_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libb/libbonobo/libbonobo2-common_2.32.1-0ubuntu5_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libi/libidl/libidl0_0.8.14-0.2ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libi/libidl/libidl-common_0.8.14-0.2ubuntu4_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/orbit2/liborbit2_2.14.19-0.3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/orbit2/liborbit-2-0_2.14.19-0.3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libglade2/libglade2-0_2.6.4-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgnome/libgnome2-common_2.32.1-4ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgnome/libgnome2-bin_2.32.1-4ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgnome/libgnome2-0_2.32.1-4ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgnomecanvas/libgnomecanvas2-common_2.30.3-2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgnomecanvas/libgnomecanvas2-0_2.30.3-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libb/libbonoboui/libbonoboui2-common_2.24.5-0ubuntu3_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libb/libbonoboui/libbonoboui2-0_2.24.5-0ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/suitesparse/libcamd2.3.1_4.2.1-3ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/suitesparse/libccolamd2.8.0_4.2.1-3ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gimp-plugin-registry/gimp-plugin-registry_5.20120621ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/l/lapack/liblapack3gf_3.5.0-2ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/b/blas/libblas3gf_1.2.20110419-7_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lapack/liblapack3_3.5.0-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/suitesparse/libcholmod2.1.2_4.2.1-3ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/d/db/libdb5.1_5.1.29-7ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/d/db/libdb5.1_5.1.29-7ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libd/libdbusmenu-qt/libdbusmenu-qt2_0.9.3+14.04.20140314-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libd/libdbusmenu-qt/libdbusmenu-qt5_0.9.3+14.04.20140314-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lvm2/libdevmapper-event1.02.1_1.02.77-6ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libd/libdiscid/libdiscid0_0.6.1-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libe/libept/libept1.4.12_1.0.12_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/portaudio19/libportaudio2_19+svn20140130-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/sonic/libsonic0_0.1.18-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libe/libevent/libevent-2.0-5_2.0.21-stable-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/f/fluidsynth/libfluidsynth1_1.1.6-2_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libf/libfs/libfs6_1.0.5-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgc/libgc1c2_7.2d-5ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/openexr/libopenexr6_1.6.1-7ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/suitesparse/libumfpack5.6.2_4.2.1-3ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libu/libunistring/libunistring0_0.9.3-5ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libu/libunistring/libunistring0_0.9.3-5ubuntu3_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mesa/libgles2-mesa_10.1.3-0ubuntu0.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgnomeui/libgnomeui-common_2.24.5-3_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgnomeui/libgnomeui-0_2.24.5-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pangomm/libpangomm-1.4-dev_2.34.0-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pangomm/libpangomm-1.4-1_2.34.0-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libj/libjpeg6b/libjpeg62_6b1-4ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/l/lcms/liblcms1_1.19.dfsg-1.2ubuntu5_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/l/lcms/liblcms1_1.19.dfsg-1.2ubuntu5_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libl/liblqr/liblqr-1-0_0.4.1-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lvm2/liblvm2app2.2_2.02.98-6ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libw/libwmf/libwmf0.2-7-gtk_0.2.8.4-10.3ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libw/libwmf/libwmf0.2-7_0.2.8.4-10.3ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libm/libmbim/libmbim-glib0_1.6.0-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/modemmanager/libmm-glib0_1.0.0-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libm/libmng/libmng2_2.0.2-0ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libn/libnl3/libnl-route-3-200_3.2.21-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libn/libnl3/libnl-genl-3-200_3.2.21-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libn/libnl3/libnl-3-200_3.2.21-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libd/libdaemon/libdaemon0_0.14-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/nss-mdns/libnss-mdns_0.10-6_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unixodbc/libodbc1_2.2.14p2-5ubuntu5_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unixodbc/libodbc1_2.2.14p2-5ubuntu5_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libo/liboil/liboil0.3_0.3.17-2ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/opencc/libopencc1_0.4.3-2build1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/o/opencore-amr/libopencore-amrnb0_0.1.3-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/o/opencore-amr/libopencore-amrwb0_0.1.3-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/packagekit/libpackagekit-glib2-16_0.8.12-1ubuntu5_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/phonon/libphonon4_4.7.1-0ubuntu8_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/poppler/libpoppler-qt4-4_0.24.5-2ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pth/libpth20_2.0.7-19ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pulseaudio/libpulsedsp_4.0-0ubuntu11_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pulseaudio/libpulsedsp_4.0-0ubuntu11_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libp/libpyzy/libpyzy-1.0-0_1.0.1-4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qca2/libqca2_2.0.3-5_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qjson/libqjson0_0.8.1-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libq/libqmi/libqmi-glib0_1.4.0-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qt4-x11/libqt4-help_4.8.5+git192-g085f851+dfsg-2ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qt4-x11/libqt4-scripttools_4.8.5+git192-g085f851+dfsg-2ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qt4-x11/libqt4-test_4.8.5+git192-g085f851+dfsg-2ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qtbase-opensource-src/libqt5dbus5_5.2.1+dfsg-1ubuntu14.2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xcb-util-wm/libxcb-icccm4_0.4.1-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xcb-util-image/libxcb-image0_0.3.9-1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xcb-util-renderutil/libxcb-render-util0_0.3.8-1.1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcb/libxcb-xkb1_1.10-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxkbcommon/libxkbcommon-x11-0_0.4.1-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qtbase-opensource-src/libqt5gui5_5.2.1+dfsg-1ubuntu14.2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qtbase-opensource-src/libqt5network5_5.2.1+dfsg-1ubuntu14.2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qtmultimedia-opensource-src/libqt5multimedia5_5.2.1-0ubuntu5_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qtfeedback-opensource-src/libqt5feedback5_5.0~git20130529-0ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qtbase-opensource-src/libqt5widgets5_5.2.1+dfsg-1ubuntu14.2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qtbase-opensource-src/libqt5opengl5_5.2.1+dfsg-1ubuntu14.2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qtpim-opensource-src/libqt5organizer5_5.0~git20140203~e0c5eebe-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qtlocation-opensource-src/libqt5positioning5_5.2.1-1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qtbase-opensource-src/libqt5printsupport5_5.2.1+dfsg-1ubuntu14.2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qtdeclarative-opensource-src/libqt5qml5_5.2.1-3ubuntu15.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qtgraphicaleffects-opensource-src/libqt5qml-graphicaleffects_5.2.1-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qtdeclarative-opensource-src/libqt5quick5_5.2.1-3ubuntu15.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qtsensors-opensource-src/libqt5sensors5_5.2.1+dfsg-2ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qtbase-opensource-src/libqt5sql5_5.2.1+dfsg-1ubuntu14.2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qtbase-opensource-src/libqt5sql5-sqlite_5.2.1+dfsg-1ubuntu14.2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qtsvg-opensource-src/libqt5svg5_5.2.1-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qtbase-opensource-src/libqt5test5_5.2.1+dfsg-1ubuntu14.2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qtwebkit-opensource-src/libqt5webkit5_5.1.1-1ubuntu8_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qtwebkit-opensource-src/libqt5webkit5-qmlwebkitplugin_5.1.1-1ubuntu8_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qt-assistant-compat/libqtassistantclient4_4.6.3-6_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qtwebkit-source/libqtwebkit4_2.3.2-0ubuntu7_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qtwebkit-source/libqtwebkit4_2.3.2-0ubuntu7_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/libraw/libraw9_0.15.4-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/readline5/libreadline5_5.2+dfsg-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/s/sdl-mixer1.2/libsdl-mixer1.2_1.2.12-10_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/s/sdl-net1.2/libsdl-net1.2_1.2.8-4_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/s/sdl-ttf2.0/libsdl-ttf2.0-0_2.0.11-3_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libssh/libssh-4_0.6.1-0ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/o/openssl098/libssl0.9.8_0.9.8o-7ubuntu3.2.14.04.1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-25ubuntu4_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/sysfsutils/libsysfs2_2.1.0+repack-3ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/make-dfsg/make_3.81-8.2ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/tcl8.5/tcl8.5-dev_8.5.15-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/tcl8.5/tcl8.5_8.5.15-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/tcl8.5/libtcl8.5_8.5.15-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/tcl8.6/libtcl8.6_8.6.1-4ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/t/telepathy-farstream-0.4/libtelepathy-farstream2_0.4.0-3ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/thumbnailer/libthumbnailer0_1.1+14.04.20140401.1-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/tk8.5/tk8.5-dev_8.5.15-2ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/tk8.5/tk8.5_8.5.15-2ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/tk8.5/libtk8.5_8.5.15-2ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/tk8.6/libtk8.6_8.6.1-3ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qtdeclarative-opensource-src/qtdeclarative5-qtquick2-plugin_5.2.1-3ubuntu15.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/u/u1db-qt/libu1db-qt5-3_0.1.5+14.04.20140313-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity-firefox-extension/libufe-xidgetter0_3.0.0+14.04.20140416-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity-action-api/libunity-action-qt1_1.1.0+14.04.20140304-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity-gtk-module/libunity-gtk2-parser0_0.0.0+14.04.20140403-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity-gtk-module/libunity-gtk3-parser0_0.0.0+14.04.20140403-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/sphinx-voxforge-en/sphinx-voxforge-hmm-en_0.1.1~daily20130301-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/sphinx-voxforge-en/sphinx-voxforge-lm-en_0.1.1~daily20130301-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/sphinxbase/libsphinxbase1_0.8-0ubuntu10_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pocketsphinx/libpocketsphinx1_0.8.0+real-0ubuntu6_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity-voice/unity-voice-service_0.1+14.04.20140304-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity-voice/libunityvoice1_0.1+14.04.20140304-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/v/vala-0.16/valac-0.16-vapi_0.16.1-2ubuntu4_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/v/vala-0.16/valac-0.16_0.16.1-2ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/v/vala-0.16/libvala-0.16-0_0.16.1-2ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libv/libvncserver/libvncserver0_0.9.9+dfsg-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/w/wxwidgets3.0/libwxbase3.0-0_3.0.0-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/w/wxwidgets3.0/wx-common_3.0.0-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/w/wxwidgets2.8/libwxgtk2.8-dev_2.8.12.1+dfsg-2ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/w/wxwidgets2.8/libwxbase2.8-dev_2.8.12.1+dfsg-2ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/w/wxwidgets2.8/wx2.8-headers_2.8.12.1+dfsg-2ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/w/wxwidgets2.8/libwxgtk2.8-0_2.8.12.1+dfsg-2ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/w/wxwidgets2.8/libwxbase2.8-0_2.8.12.1+dfsg-2ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libx86/libx86-1_1.1+ds1-10_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxp/libxp6_1.0.2-1ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxp/libxp6_1.0.2-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lightdm/lightdm_1.10.1-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/linux/linux-image-3.13.0-30-generic_3.13.0-30.55_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/network-manager/network-manager_0.9.8.8-0ubuntu7_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/ppp/ppp_2.4.5-5.1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/wpa/wpasupplicant_2.1-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libm/libmnl/libmnl0_1.0.3-3ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libn/libnetfilter-conntrack/libnetfilter-conntrack3_1.0.4-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unixodbc/odbcinst_2.2.14p2-5ubuntu5_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unixodbc/odbcinst1debian2_2.2.14p2-5ubuntu5_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unixodbc/odbcinst1debian2_2.2.14p2-5ubuntu5_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pcmciautils/pcmciautils_018-8_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/phonon-backend-gstreamer/phonon-backend-gstreamer_4.7.1+git20140403-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/phonon-backend-gstreamer/phonon-backend-gstreamer-common_4.7.1+git20140403-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qt-at-spi/qt-at-spi_0.3.1-4fakesync1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qtdeclarative-opensource-src/qtdeclarative5-privatewidgets-plugin_5.2.1-3ubuntu15.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qtdeclarative-opensource-src/qtdeclarative5-dialogs-plugin_5.2.1-3ubuntu15.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qtdeclarative-opensource-src/qtdeclarative5-localstorage-plugin_5.2.1-3ubuntu15.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qtfeedback-opensource-src/qtdeclarative5-qtfeedback-plugin_5.0~git20130529-0ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/u/u1db-qt/qtdeclarative5-u1db1.0_0.1.5+14.04.20140313-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/u/ubuntu-settings-components/qtdeclarative5-ubuntu-settings-components-assets_0.1+14.04.20140306-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qtdeclarative-opensource-src/qtdeclarative5-window-plugin_5.2.1-3ubuntu15.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity-action-api/qtdeclarative5-unity-action-plugin_1.1.0+14.04.20140304-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/ubuntu-font-family-sources/ttf-ubuntu-font-family_0.80-0ubuntu6_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/ubuntu-ui-toolkit/ubuntu-ui-toolkit-theme_0.1.46+14.04.20140408.1-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/ubuntu-ui-toolkit/qtdeclarative5-ubuntu-ui-toolkit-plugin_0.1.46+14.04.20140408.1-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/u/ubuntu-settings-components/qtdeclarative5-ubuntu-settings-components_0.1+14.04.20140306-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/speech-dispatcher/libspeechd2_0.8-5ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/speech-dispatcher/speech-dispatcher_0.8-5ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/speech-dispatcher/speech-dispatcher-audio-plugins_0.8-5ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/tasksel/tasksel-data_2.88ubuntu15_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/tasksel/tasksel_2.88ubuntu15_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/c/cabextract/cabextract_1.4-4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xfonts-utils/xfonts-utils_7.7+1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/multiverse/m/msttcorefonts/ttf-mscorefonts-installer_3.4+nmu1ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/f/fonts-unfonts-core/ttf-unfonts-core_1.0.3.is.1.0.2-080608-10ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity-gtk-module/unity-gtk-module-common_0.0.0+14.04.20140403-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity-gtk-module/unity-gtk2-module_0.0.0+14.04.20140403-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity-gtk-module/unity-gtk3-module_0.0.0+14.04.20140403-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/multiverse/w/wine-gecko2.21/wine-gecko2.21_2.21-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/multiverse/w/wine-gecko2.21/wine-gecko2.21_2.21-0ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/multiverse/w/wine-mono0.0.8/wine-mono0.0.8_0.0.8-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xaw3d/xaw3dg_1.5+E-18.2_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/i/isdnutils/libcapi20-3_3.25+dfsg1-3.3ubuntu2_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/i/isdnutils/libcapi20-3_3.25+dfsg1-3.3ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgusb/libgusb2_0.1.6-5_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/network-manager/gir1.2-networkmanager-1.0_0.9.8.8-0ubuntu7_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libn/libnotify/gir1.2-notify-0.7_0.7.6-1ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libsignon-glib/gir1.2-signon-1.0_1.10daily13.06.25-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/liba/libaccounts-glib/gir1.2-accounts-1.0_1.15+14.04.20131126.2-0ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libf/libfriends/libfriends0_0.1.2+14.04.20131108.1-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/wireless-tools/libiw30_30~pre9-8ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mesa/libosmesa6_10.1.3-0ubuntu0.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mesa/libosmesa6_10.1.3-0ubuntu0.1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libq/libquvi-scripts/libquvi-scripts_0.4.21-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libq/libquvi/libquvi7_0.4.1-1ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/sbc/libsbc1_1.1-2ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/s2tc/libtxc-dxtn-s2tc0_0~git20131104-1.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/less/less_458-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/liba/libarchive-extract-perl/libarchive-extract-perl_0.70-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libl/liblog-message-simple-perl/liblog-message-simple-perl_0.10-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libm/libmodule-pluggable-perl/libmodule-pluggable-perl_5.1-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libp/libpod-latex-perl/libpod-latex-perl_0.61-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libt/libterm-ui-perl/libterm-ui-perl_0.42-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libt/libtext-soundex-perl/libtext-soundex-perl_3.4-1build1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lockfile-progs/lockfile-progs_0.1.17_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/logrotate/logrotate_3.8.7-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/net-tools/net-tools_1.60-25ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/netcat-openbsd/netcat-openbsd_1.105-7ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/rsyslog/rsyslog_7.4.4-1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/ureadahead/ureadahead_0.100.0-16_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/v/vim/vim-tiny_7.4.052-1ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/v/vim/vim-common_7.4.052-1ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/ubuntu-meta/ubuntu-minimal_1.325_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python3-stdlib-extensions/python3-gdbm_3.4.0-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/netkit-ftp/ftp_0.17-28_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/texinfo/info_5.2.0.dfsg.1-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lshw/lshw_02.16-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lsof/lsof_4.86+dfsg-1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/ltrace/ltrace_0.7.3-4ubuntu5.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/manpages/manpages_3.54-1ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/memtest86+/memtest86+_4.20-1.1ubuntu8_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mlocate/mlocate_0.26-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mtr/mtr-tiny_0.85-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/nano/nano_2.2.6-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/openssh/openssh-server_6.6p1-2ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/openssh/openssh-sftp-server_6.6p1-2ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/openssh/openssh-client_6.6p1-2ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/plymouth/plymouth-theme-ubuntu-text_0.8.8-0ubuntu17_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pppconfig/pppconfig_2.3.19ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/rsync/rsync_3.1.0-2ubuntu0.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/strace/strace_4.8-1ubuntu5_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/tcpdump/tcpdump_4.5.1-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/netkit-telnet/telnet_0.17-36build2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/time/time_1.7-24_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/ubuntu-meta/ubuntu-standard_1.325_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/ufw/ufw_0.34~rc-0ubuntu2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/util-linux/uuid-runtime_2.20.1-5.1ubuntu20.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xauth/xauth_1.0.7-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xml-core/xml-core_0.13+nmu2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/telepathy-haze/telepathy-haze_0.8.0-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/signon/libsignon-extension1_8.56+14.04.20140307-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/signon/libsignon-plugins-common1_8.56+14.04.20140307-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/signon/signond_8.56+14.04.20140307-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/signon/signon-plugin-password_8.56+14.04.20140307-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/signon/libsignon-qt5-1_8.56+14.04.20140307-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/signon-ui/signon-ui_0.16+14.04.20140304.is.0.15+14.04.20140313-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/signon-plugin-oauth2/signon-plugin-oauth2_0.19+14.04.20140305-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/a/account-plugins/account-plugin-identica_0.11+14.04.20140409.1-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/telepathy-salut/telepathy-salut_0.8.1-1ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-keyring/python-keyring_3.5-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lazr.uri/python-lazr.uri_1.0.3-1build1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/simplejson/python-simplejson_3.3.1-1ubuntu6_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-wadllib/python-wadllib_1.3.2-2build1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-oauth/python-oauth_1.0.1-3build2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lazr.restfulclient/python-lazr.restfulclient_0.13.3-1build1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-launchpadlib/python-launchpadlib_1.10.2+ds-2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xbitmaps/xbitmaps_1.1.1-2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libu/libutempter/libutempter0_1.1.5-4build1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xterm/xterm_297-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mono/libmono-cairo4.0-cil_3.2.8+dfsg-4ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgdiplus/libgdiplus_2.11+git20131008.9732566-5ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mono/libmono-system-drawing4.0-cil_3.2.8+dfsg-4ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mono/libmono-posix4.0-cil_3.2.8+dfsg-4ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/y/yelp/yelp_3.10.2-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/y/yelp/libyelp0_3.10.2-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/y/yelp-xsl/yelp-xsl_3.10.1-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/rarian/librarian0_0.8.1-5ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/sgml-data/sgml-data_2.0.9-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/rarian/rarian-compat_0.8.1-5ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/b/bless/bless_0.6.0-4_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/b/bluez/bluez-gstreamer_4.101-0ubuntu13_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/systemd/gir1.2-gudev-1.0_204-5ubuntu20.3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lxml/python3-lxml_3.3.3-1ubuntu0.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/sg3-utils/libsgutils2-2_1.36-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/u/udisks/udisks_1.0.5-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/c/checkbox/checkbox_0.17.6-0ubuntu6_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/c/checkbox/python3-checkbox_0.17.6-0ubuntu6_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/c/checkbox/checkbox-qt_0.17.6-0ubuntu6_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/plainbox/plainbox-secure-policy_0.5.3-2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/plainbox/python3-plainbox_0.5.3-2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python3-chardet/python3-chardet_2.0.1-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/six/python3-six_1.5.2-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-urllib3/python3-urllib3_1.7.1-1build1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/requests/python3-requests_2.2.1-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pyparsing/python3-pyparsing_2.0.1+dfsg1-1build1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/plainbox-provider-resource-generic/plainbox-provider-resource-generic_0.3-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/plainbox-provider-checkbox/plainbox-provider-checkbox_0.4-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/c/codeblocks/codeblocks-contrib_13.12-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/c/codeblocks/codeblocks_13.12-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/c/codeblocks/codeblocks-common_13.12-3_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/c/codeblocks/libwxsmithlib0_13.12-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/c/codeblocks/libcodeblocks0_13.12-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gamin/gamin_0.1.10-4.1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gamin/libgamin0_0.1.10-4.1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gcc-4.6/g++-4.6-multilib_4.6.4-6ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gcc-4.6/gcc-4.6-multilib_4.6.4-6ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gcc-4.6/libstdc++6-4.6-dev_4.6.4-6ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gcc-4.6/g++-4.6_4.6.4-6ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gcc-4.6/gcc-4.6_4.6.4-6ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gcc-4.6/cpp-4.6_4.6.4-6ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gcc-4.6/gcc-4.6-base_4.6.4-6ubuntu2_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gcc-4.6/gcc-4.6-base_4.6.4-6ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/wireless-regdb/wireless-regdb_2013.02.13-1ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/liby/libyaml-tiny-perl/libyaml-tiny-perl_1.56-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unzip/unzip_6.0-9ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/z/zip/zip_3.0-8_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/b/bsd-finger/finger_0.17-15_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_11.2.202.378ubuntu0.14.04.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/f/fuseiso/fuseiso_20070708-3ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gnome-calculator/gcalctool_3.10.2-0ubuntu1.1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/ubuntu-geoip/geoclue-ubuntu-geoip_1.0.2+14.04.20131125-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gtkglext/libgtkglext1_1.2.0-3.1fakesync3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/tiff/libtiff-tools_4.0.3-7ubuntu0.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pygtk/python-glade2_2.24.0-3ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pygtk/python-gtk2_2.24.0-3ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gnome-scan/gimp-flegita_0.6.2-1.1ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gnome-scan/libgnomescan0_0.6.2-1.1ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gnome-scan/gnome-scan-common_0.6.2-1.1ubuntu4_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gmic/gimp-gmic_1.5.7.1-4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gutenprint/gimp-gutenprint_5.2.10~pre2-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/liba/libappindicator/gir1.2-appindicator3-0.1_12.10.1+13.10.20130920-0ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgdata/gir1.2-gdata-0.0_0.14.1-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libi/libindicate/libindicate5_12.10.1-0ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libi/libindicate/gir1.2-indicate-0.7_12.10.1-0ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/packagekit/gir1.2-packagekitglib-1.0_0.8.12-1ubuntu5_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/totem/totem-mozilla_3.10.1-1ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/totem/totem-plugins_3.10.1-1ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/totem/totem_3.10.1-1ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/totem/totem-common_3.10.1-1ubuntu4_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/totem/gir1.2-totem-1.0_3.10.1-1ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/totem/libtotem0_3.10.1-1ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/totem-pl-parser/gir1.2-totem-plparser-1.0_3.10.2-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/udisks2/gir1.2-udisks-2.0_2.1.3-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libu/libunity/gir1.2-unity-5.0_7.1.4+14.04.20140210-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libe/liberror-perl/liberror-perl_0.17-1.1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libg/libgksu/libgksu2-0_2.0.13~pre1-6ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gksu/gksu_2.0.2-6ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libl/liblinear/liblinear1_1.8+dfsg-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/nmap/nmap_6.40-0.2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/whois/whois_5.1.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gnome-nettool/gnome-nettool_3.8.1-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/py3cairo/python3-cairo_1.10.0+dfsg-3ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pygobject/python3-gi-cairo_3.12.0-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gst-fluendo-mp3/gstreamer0.10-fluendo-mp3_0.10.23.debian-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libs/libsidplay/libsidplay1_1.36.59-5ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gst-plugins-ugly0.10/gstreamer0.10-plugins-ugly_0.10.19-2ubuntu5_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/guile-1.8/guile-1.8-libs_1.8.8+1-8ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gwibber/gwibber-service_3.7.0bzr13.04.05-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gwibber/gwibber-service-facebook_3.7.0bzr13.04.05-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/f/friends/friends-identica_0.2.0+14.04.20140217.1-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gwibber/gwibber-service-identica_3.7.0bzr13.04.05-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gwibber/gwibber-service-twitter_3.7.0bzr13.04.05-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/h/heirloom-mailx/heirloom-mailx_12.5-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/notify-python/python-notify_0.1.1-3ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/k/kate/kate-data_4.13.2-0ubuntu0.1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/k/kde-runtime/kde-runtime-data_4.13.2-0ubuntu0.1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/k/kde-runtime/kde-runtime_4.13.2-0ubuntu0.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/k/kactivities/libkactivities6_4.13.2-0ubuntu0.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/k/kate/katepart_4.13.2-0ubuntu0.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/k/kde4libs/kdelibs5-plugins_4.13.2a-0ubuntu0.2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/soprano/libsoprano4_2.9.4+dfsg1-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/soprano/soprano-daemon_2.9.4+dfsg1-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/strigi/libstreamanalyzer0_0.7.8-1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/strigi/libstreams0_0.7.8-1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libq/libqapt/libqapt2_2.1.70-0ubuntu4.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libk/libkubuntu/libkubuntu0_14.04ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/k/kdepimlibs/libkxmlrpcclient4_4.13.2-0ubuntu0.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/n/ntrack/ntrack-module-libnl-0_016-1.2ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/n/ntrack/libntrack0_016-1.2ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/n/ntrack/libntrack-qt4-1_016-1.2ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/phonon/phonon_4.7.1-0ubuntu8_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/o/oxygen-icons/oxygen-icon-theme_4.13.0-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/shared-desktop-ontologies/shared-desktop-ontologies_0.11.0-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/k/kde-runtime/plasma-scriptengine-javascript_4.13.2-0ubuntu0.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/polkit-qt-1/libpolkit-qt-1-1_0.103.0-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libq/libqapt/libqapt2-runtime_2.1.70-0ubuntu4.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxml2/libxml2-utils_2.9.1+dfsg1-3ubuntu4.3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pkg-kde-tools/libdlrestrictions1_0.15.12ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/k/kate/libkatepartinterfaces4_4.13.2-0ubuntu0.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/k/kernel-package/kernel-package_12.036+nmu3_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libq/libqapt/qapt-batch_2.1.70-0ubuntu4.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/k/kubuntu-debug-installer/kubuntu-debug-installer_13.10ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/readline5/lib32readline-gplv2-dev_5.2+dfsg-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/readline5/lib32readline5_5.2+dfsg-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/readline6/lib32readline6_6.3-4ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/liba/libarchive-zip-perl/libarchive-zip-perl_1.30-7_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libsub-identify-perl/libsub-identify-perl_0.04-1build3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/liba/libautodie-perl/libautodie-perl_2.23-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/b/baloo/libbaloocore4_4.13.2-0ubuntu0.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/b/baloo/libbalooxapian4_4.13.2-0ubuntu0.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/b/baloo/libbaloofiles4_4.13.2-0ubuntu0.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libc/libcanberra/libcanberra-gtk-module_0.30-0ubuntu3_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libc/libcanberra/libcanberra-gtk-module_0.30-0ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libc/libclass-isa-perl/libclass-isa-perl_0.36-5_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libn/libnet-smtp-ssl-perl/libnet-smtp-ssl-perl_1.01-3_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libm/libmailtools-perl/libmailtools-perl_2.12-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libn/libnet-domain-tld-perl/libnet-domain-tld-perl_1.70-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libe/libemail-valid-perl/libemail-valid-perl_1.192-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libz/libzip/libzip2_0.10.1-1.2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/e/ebook-tools/libepub0_0.2.2-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libf/libfile-desktopentry-perl/libfile-desktopentry-perl_0.07-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libf/libfile-fcntllock-perl/libfile-fcntllock-perl_0.14-2build1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libf/libfile-mimeinfo-perl/libfile-mimeinfo-perl_0.22-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libg/libgdchart-gd2/libgdchart-gd2-noxpm_0.11.5-7.1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gnome-menus2/libgnome-menu2_3.0.1-0ubuntu9_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgphoto2/libgphoto2-l10n_2.5.3.1-1ubuntu2.2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgpod/libgpod-common_0.8.3-4ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gtksourceview2/libgtksourceview2.0-common_2.10.5-1ubuntu2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gtksourceview2/libgtksourceview2.0-0_2.10.5-1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libh/libhtml-format-perl/libhtml-format-perl_2.11-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libi/libid3tag/libid3tag0_0.15.1b-10ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libi/libindicate/libindicate-gtk3_12.10.1-0ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libi/libio-string-perl/libio-string-perl_1.08-3_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libi/libipc-run-perl/libipc-run-perl_0.92-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libi/libipc-system-simple-perl/libipc-system-simple-perl_1.25-2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libj/libjson-perl/libjson-perl_2.61-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/n/nepomuk-core/nepomuk-core-data_4.13.2-0ubuntu0.1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/n/nepomuk-core/libnepomukcore4abi1_4.13.2-0ubuntu0.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/k/kactivities/libkactivities-models1_4.13.2-0ubuntu0.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/k/kactivities/libkactivities-bin_4.13.2-0ubuntu0.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libl/liblinear/liblinear-tools_1.8+dfsg-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libl/liblist-moreutils-perl/liblist-moreutils-perl_0.33-1build3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mono/libmono-i18n-west4.0-cil_3.2.8+dfsg-4ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libn/libnatpmp/libnatpmp1_20110808-3ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/n/nepomuk-core/libnepomukcleaner4_4.13.2-0ubuntu0.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/netpbm-free/netpbm_10.0-15ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/netpbm-free/libnetpbm10_10.0-15ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/network-manager/libnm-glib-vpn1_0.9.8.8-0ubuntu7_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libn/libnotify/libnotify-bin_0.7.6-1ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/o/openbox/libobt2_3.5.2-6_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/o/openbox/libobrender29_3.5.2-6_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pango1.0/libpango1.0-doc_1.36.3-1ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libp/libpaper/libpaper-utils_1.1.24+nmu2ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libp/libparse-debcontrol-perl/libparse-debcontrol-perl_2.005-4_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libp/libperlio-gzip-perl/libperlio-gzip-perl_0.18-1build3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libp/libpod-plainer-perl/libpod-plainer-perl_1.03-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/postgresql-9.3/libpq5_9.3.4-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/protobuf/libprotoc8_2.5.0-9ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pidgin/libpurple-bin_2.10.9-0ubuntu3.1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/k/kdegraphics-mobipocket/libqmobipocket1_4.13.0-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libq/libqtbamf/libqtbamf1_0.2.4-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/libreoffice/libreoffice-avmedia-backend-gstreamer_4.2.4-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/libreoffice-l10n/libreoffice-help-en-gb_4.2.4-0ubuntu2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/libreoffice-l10n/libreoffice-help-en-us_4.2.4-0ubuntu2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/libreoffice/libreoffice-presentation-minimizer_4.2.4-0ubuntu2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/openslp-dfsg/libslp1_1.2.1-9_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libsys-hostname-long-perl/libsys-hostname-long-perl_1.4-3_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libt/libtext-levenshtein-perl/libtext-levenshtein-perl_0.06~01-2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libt/libtie-ixhash-perl/libtie-ixhash-perl_1.23-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libt/libtimezonemap/libtimezonemap1_0.4.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libt/libtool/libtool_2.4.2-1.7ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libu/libunique3/libunique-3.0-0_3.0.2-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/oxide-qt/oxideqt-codecs_1.0.0~bzr501-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/oxide-qt/liboxideqtcore0_1.0.0~bzr501-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/oxide-qt/liboxideqt-qmlplugin_1.0.0~bzr501-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity-webapps-qml/unity-webapps-qml_0.1+14.04.20140408-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/webbrowser-app/qtdeclarative5-ubuntu-ui-extras-browser-plugin-assets_0.23+14.04.20140428-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/webbrowser-app/qtdeclarative5-ubuntu-ui-extras-browser-plugin_0.23+14.04.20140428-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/webbrowser-app/webbrowser-app_0.23+14.04.20140428-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/webbrowser-app/webapp-container_0.23+14.04.20140428-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libu/libunity-webapps/unity-webapps-service_2.5.0~+14.04.20140409-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libu/libunity-webapps/libunity-webapps0_2.5.0~+14.04.20140409-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/v/virtuoso-opensource/libvirtodbc0_6.1.6+repack-0ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/v/virtuoso-opensource/virtuoso-opensource-6.1-common_6.1.6+repack-0ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libv/libvisual-plugins/libvisual-0.4-plugins_0.4.0.dfsg.1-7build1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libv/libvisual-plugins/libvisual-0.4-plugins_0.4.0.dfsg.1-7build1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libx11/libx11-doc_1.6.2-1ubuntu2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/patchutils/patchutils_0.3.2-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/t1utils/t1utils_1.37-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lintian/lintian_2.5.22ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/linux-firmware/linux-firmware_1.127.4_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/linux/linux-image-extra-3.13.0-30-generic_3.13.0-30.55_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/linux-meta/linux-image-generic_3.13.0.30.36_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/linux/linux-headers-3.13.0-30_3.13.0-30.55_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/linux/linux-headers-3.13.0-30-generic_3.13.0-30.55_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/linux-meta/linux-headers-generic_3.13.0.30.36_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/linux-meta/linux-generic_3.13.0.30.36_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/linux-meta/linux-generic-lts-raring_3.13.0.30.36_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/linux-meta/linux-headers-generic-lts-raring_3.13.0.30.36_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/linux-meta/linux-image-generic-lts-raring_3.13.0.30.36_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/manpages/manpages-dev_3.54-1ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/m/meld/meld_1.8.4-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/m/mingw32-binutils/mingw32-binutils_2.20-0.2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/modemmanager/modemmanager_1.0.0-2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mousetweaks/mousetweaks_3.8.0-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mtools/mtools_4.0.18-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/openoffice.org-en-au/mythes-en-au_2.1-5.4_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/libreoffice-dictionaries/mythes-en-us_4.2.1-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/ncurses/ncurses-term_5.9+20140118-1ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/n/nepomuk-core/nepomuk-core-runtime_4.13.2-0ubuntu0.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/network-manager-applet/network-manager-gnome_0.9.8.8-0ubuntu4.2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/network-manager-pptp/network-manager-pptp-gnome_0.9.8.2-1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pptp-linux/pptp-linux_1.7.2-7_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/network-manager-pptp/network-manager-pptp_0.9.8.2-1ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/notify-osd-icons/notify-osd-icons_0.8+14.04.20131204-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/o/obconf/obconf_2.0.4+git20130908-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/onboard/onboard_1.0.0-0ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/onboard/onboard-data_1.0.0-0ubuntu4_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/o/openbox/openbox_3.5.2-6_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/openoffice.org-hyphenation/openoffice.org-hyphenation_0.7_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/os-prober/os-prober_1.63ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/o/osspd/osspd-pulseaudio_1.3.2-5_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/o/osspd/osspd_1.3.2-5_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/p/p7zip/p7zip_9.20.1~dfsg.1-4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pastebinit/pastebinit_1.4-3_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pax/pax_20120606-2+deb7u1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/plymouth/plymouth-theme-ubuntu-logo_0.8.8-0ubuntu17_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/p/pngcrush/pngcrush_1.7.65-0.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/policykit-desktop-privileges/policykit-desktop-privileges_0.17_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/min12xxw/printer-driver-min12xxw_0.0.9-8ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pnm2ppa/printer-driver-pnm2ppa_1.13+nondbs-0ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/ptouch-driver/printer-driver-ptouch_1.3-8_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/splix/printer-driver-splix_2.0.0+svn315-2fakesync1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pulseaudio/pulseaudio-module-gconf_4.0-0ubuntu11_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pulseaudio/pulseaudio-utils_4.0-0ubuntu11_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pulseaudio/pulseaudio-module-x11_4.0-0ubuntu11_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-stdlib-extensions/python-gdbm_2.7.5-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/p/python-configglue/python-configglue_1.1.2-0ubuntu2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-cups/python-cups_1.9.66-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/system-config-printer/python-cupshelpers_1.4.3+20140219-0ubuntu2.1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-dateutil/python-dateutil_1.5+dfsg-1ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-dns/python-dns_2.3.6-3_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/f/flup/python-flup_1.0.2-4_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-formencode/python-formencode_1.2.6-1ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pyorbit/python-pyorbit_2.24.0-6ubuntu4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxml2/python-libxml2_2.9.1+dfsg1-3ubuntu4.3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/i/ipy/python-ipy_0.81-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libp/libproxy/python-libproxy_0.4.11-0ubuntu4_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/markupsafe/python-markupsafe_0.18-1build2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mako/python-mako_0.9.1-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-markdown/python-markdown_2.4-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-pam/python-pam_0.4.2-13.1ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/psycopg2/python-psycopg2_2.4.5-1build5_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/p/pyatspi/python-pyatspi2_2.10.0+dfsg-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/p/pyatspi/python-pyatspi_2.10.0+dfsg-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pygments/python-pygments_1.6+dfsg-1ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pyinotify/python-pyinotify_0.9.4-1build1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/sip4/python-sip_4.15.5-1build1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-qt4/python-qt4_4.10.4+dfsg-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-qt4/python-qt4-dbus_4.10.4+dfsg-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-reportlab/python-renderpm_3.0-1build1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-urllib3/python-urllib3_1.7.1-1build1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/requests/python-requests_2.2.1-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-secretstorage/python-secretstorage_2.0.0-1ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pyserial/python-serial_2.6-1build1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-smbc/python-smbc_1.0.14.1-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/s/sqlobject/python-sqlobject_1.5.2-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/p/python-support/python-support_1.0.15_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/twisted/python-twisted-names_13.2.0-1ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/v/virtkey/python-virtkey_0.63.0-0ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/p/pywebkitgtk/python-webkit_1.1.8-3ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/w/webpy/python-webpy_0.37+20120626-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/x/x-kit/python-xkit_0.5.0ubuntu2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-debian/python3-debian_0.1.21+nmu2ubuntu2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/libreoffice/python3-uno_4.2.4-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qpdf/qpdf_5.1.1-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/r/radeontool/radeontool_1.6.3-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/multiverse/r/rar/rar_4.2.0-1_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/remmina/remmina-plugin-rdp_1.0.0-4ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/remmina/remmina-plugin-vnc_1.0.0-4ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/remmina/remmina-common_1.0.0-4ubuntu3_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/remmina/remmina_1.0.0-4ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/rfkill/rfkill_0.5-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/rtkit/rtkit_0.10-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/samba/samba-vfs-modules_4.1.6+dfsg-1ubuntu2.14.04.2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/sane-backends/sane-utils_1.0.23-3ubuntu3.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/sharutils/sharutils_4.14-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/shotwell/shotwell_0.18.0-0ubuntu4.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/shotwell/shotwell-common_0.18.0-0ubuntu4.1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/signon-keyring-extension/signon-keyring-extension_0.6+14.04.20140307-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/simple-scan/simple-scan_3.12.1-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/sni-qt/sni-qt_0.2.6-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/squashfs-tools/squashfs-tools_4.2+20130409-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/openssh/ssh-askpass-gnome_6.6p1-2ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/syslinux/syslinux-common_4.05+dfsg-6+deb8u1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/syslinux/syslinux_4.05+dfsg-6+deb8u1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/system-config-printer/system-config-printer-common_1.4.3+20140219-0ubuntu2.1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/system-config-printer/system-config-printer-udev_1.4.3+20140219-0ubuntu2.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/tcl8.6/tcl8.6_8.6.1-4ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/tcl8.6/tcl8.6-dev_8.6.1-4ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/tk8.6/tk8.6_8.6.1-3ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/tk8.6/tk8.6-dev_8.6.1-3ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/tcltk-defaults/tk-dev_8.6.0+6ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/tcltk-defaults/tcl-dev_8.6.0+6ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/tcltk-defaults/tk_8.6.0+6ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/tcltk-defaults/tcl_8.6.0+6ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/tcp-wrappers/tcpd_7.6.q-25_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/telepathy-idle/telepathy-idle_0.2.0-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/thunderbird/thunderbird-globalmenu_24.6.0+build1-0ubuntu0.14.04.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/thunderbird/thunderbird-locale-en-gb_24.6.0+build1-0ubuntu0.14.04.1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/thunderbird/thunderbird-locale-en-us_24.6.0+build1-0ubuntu0.14.04.1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/tofrodos/tofrodos_1.7.13+ds-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/toshset/toshset_1.76-4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/transmission/transmission-common_2.82-1.1ubuntu3_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/transmission/transmission-gtk_2.82-1.1ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/ttf-indic-fonts/ttf-indic-fonts-core_0.5.14ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/ttf-indic-fonts/ttf-punjabi-fonts_0.5.14ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/ubuntu-wallpapers/ubuntu-wallpapers-trusty_14.04.0.1-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/ubuntu-wallpapers/ubuntu-wallpapers_14.04.0.1-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/ubuntu-themes/ubuntu-artwork_14.04+14.04.20140410-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity-settings-daemon/unity-settings-daemon_14.04.0+14.04.20140606-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/ubuntu-settings/ubuntu-settings_14.04.5_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/ubuntuone-client-data/ubuntuone-client-data_13.05-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/ubuntu-sso-client/ubuntu-sso-client-qt_13.10-0ubuntu6_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity-control-center/unity-control-center_14.04.3+14.04.20140604-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/wireless-tools/wireless-tools_30~pre9-8ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xdg-user-dirs/xdg-user-dirs_0.15-1ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xdg-user-dirs-gtk/xdg-user-dirs-gtk_0.10-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xdiagnose/xdiagnose_3.6.3build2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xserver-xorg-video-modesetting/xserver-xorg-video-modesetting_0.8.1-1build1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xorg/xserver-xorg-video-all_7.7+1ubuntu8_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xorg/xorg_7.7+1ubuntu8_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xorg/xserver-xorg_7.7+1ubuntu8_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/x11-apps/x11-apps_7.7+2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/x11-session-utils/x11-session-utils_7.7+1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/x11-xfs-utils/x11-xfs-utils_7.7+1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/x11-xserver-utils/x11-xserver-utils_7.7+2ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xinit/xinit_1.3.2-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xorg-docs/xorg-docs-core_1.7-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xinput/xinput_1.6.1-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/ubuntu-meta/ubuntu-desktop_1.325_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/ubuntu-docs/ubuntu-docs_14.04.3_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/ubuntu-system-service/ubuntu-system-service_0.2.5build1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/u/ubuntu-wallpapers/ubuntu-wallpapers-precise_14.04.0.1-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/u/unity/unity-2d_7.2.1+14.04.20140513-0ubuntu2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/u/unity/unity-2d-common_7.2.1+14.04.20140513-0ubuntu2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity-lens-photos/unity-lens-photos_1.0+14.04.20140318-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libu/libunity/unity-scopes-runner_7.1.4+14.04.20140210-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity-scope-audacious/unity-scope-audacious_0.1+13.10.20130927.1-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity-scope-calculator/unity-scope-calculator_0.1+14.04.20140328-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity-scope-chromiumbookmarks/unity-scope-chromiumbookmarks_0.1+13.10.20130723-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity-scope-clementine/unity-scope-clementine_0.1+13.10.20130723-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity-scope-colourlovers/unity-scope-colourlovers_0.1+13.10.20130723-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity-scope-devhelp/unity-scope-devhelp_0.1+14.04.20140328-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity-scope-firefoxbookmarks/unity-scope-firefoxbookmarks_0.1+13.10.20130809.1-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity-scope-gmusicbrowser/unity-scope-gmusicbrowser_0.1+13.10.20130723-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity-scope-gourmet/unity-scope-gourmet_0.1+13.10.20130723-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity-scope-guayadeque/unity-scope-guayadeque_0.1+13.10.20130927.1-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity-scope-manpages/unity-scope-manpages_3.0+14.04.20140324-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity-lens-music/unity-scope-musicstores_6.9.0+13.10.20131011-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity-scope-musique/unity-scope-musique_0.1+13.10.20130723-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity-scope-openclipart/unity-scope-openclipart_0.1+13.10.20130723-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity-scope-texdoc/unity-scope-texdoc_0.1+14.04.20140328-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity-scope-tomboy/unity-scope-tomboy_0.1+13.10.20130723-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity-lens-video/unity-scope-video-remote_0.3.15+13.10.20130920-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity-scope-virtualbox/unity-scope-virtualbox_0.1+13.10.20130723-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity-scope-yelp/unity-scope-yelp_0.1+13.10.20130723-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity-scope-zotero/unity-scope-zotero_0.1+13.10.20130723-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/webapps-applications/unity-webapps-common_2.4.17+14.04.20140416-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unixodbc/unixodbc_2.2.14p2-5ubuntu5_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/multiverse/u/unrar-nonfree/unrar_5.0.10-1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/usb-creator/usb-creator-gtk_0.2.56.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/usb-creator/usb-creator-common_0.2.56.1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/v/vala-0.20/valac-0.20-vapi_0.20.1-2ubuntu5_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/v/vala-0.20/valac-0.20_0.20.1-2ubuntu5_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/v/valgrind/valgrind_3.10~20140411-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/v/vbetool/vbetool_1.1-3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/v/virtuoso-opensource/virtuoso-opensource-6.1-bin_6.1.6+repack-0ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/v/virtuoso-opensource/virtuoso-minimal_6.1.6+repack-0ubuntu3_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/wdiff/wdiff_1.2.1-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/webaccounts-browser-extension/webaccounts-extension-common_0.5-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/whoopsie/whoopsie_0.2.24.6_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/w/winetricks/winetricks_0.0+20140302-0ubuntu2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/x/xcftools/xcftools_1.0.7-4ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/x/xclip/xclip_0.12+svn84-4_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxslt/xsltproc_1.1.28-2build1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/ubufox/xul-ext-ubufox_2.9-0ubuntu0.14.04.1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/webapps-greasemonkey/xul-ext-websites-integration_2.3.6+13.10.20130920.1-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity-firefox-extension/xul-ext-unity_3.0.0+14.04.20140416-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/webaccounts-browser-extension/xul-ext-webaccounts_0.5-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/h/haskell-bzlib/libghc-bzlib-dev_0.5.0.4-2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/ghc/ghc_7.6.3-10_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gnome-exe-thumbnailer/gnome-exe-thumbnailer_0.9.3-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/liba/libauthen-sasl-perl/libauthen-sasl-perl_2.1500-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libc/libcanberra/libcanberra-gtk3-module_0.30-0ubuntu3_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/libreoffice/libreoffice-ogltrans_4.2.4-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/libreoffice/libreoffice-pdfimport_4.2.4-0ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lsb/lsb-invalid-mta_4.1+Debian11ubuntu6_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lsb/lsb-security_4.1+Debian11ubuntu6_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lsb/lsb-core_4.1+Debian11ubuntu6_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lsb/lsb-graphics_4.1+Debian11ubuntu6_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lsb/lsb-cxx_4.1+Debian11ubuntu6_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lsb/lsb-multimedia_4.1+Debian11ubuntu6_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lsb/lsb-desktop_4.1+Debian11ubuntu6_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lsb/lsb-printing_4.1+Debian11ubuntu6_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lsb/lsb-languages_4.1+Debian11ubuntu6_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lsb/lsb_4.1+Debian11ubuntu6_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mobile-broadband-provider-info/mobile-broadband-provider-info_20140317-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/o/openjdk-6/openjdk-6-jdk_6b31-1.13.3-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/p11-kit/p11-kit-modules_0.20.2-2ubuntu2_i386.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pbuilder/pbuilder_0.215ubuntu7_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/protobuf/protobuf-compiler_2.5.0-9ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pulseaudio/pulseaudio-module-bluetooth_4.0-0ubuntu11_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/b/brltty/python-brlapi_5.0-2ubuntu2_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libl/liblouis/python-louis_2.5.3-2ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/p/protobuf/python-protobuf_2.5.0-9ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/q/qml-friends/qtdeclarative5-friends0.2_0.2.0+14.04.20140317-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/r/rebuildd/rebuildd_0.4.2_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/sessioninstaller/sessioninstaller_0.20+bzr141-0ubuntu4_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/ssh-import-id/ssh-import-id_3.21-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/f/fonts-liberation/ttf-liberation_1.07.3-3_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity-lens-friends/unity-lens-friends_0.1.3+14.04.20140317-0ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity-scope-gdrive/unity-scope-gdrive_0.9+13.10.20130723-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/usb-modeswitch/usb-modeswitch_2.1.1+repack0-1ubuntu1_amd64.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/usb-modeswitch-data/usb-modeswitch-data_20140327-1_all.deb 403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xfonts-mathml/xfonts-mathml_6ubuntu1_all.deb 403  Forbidden


 
```

:(

---

### Post by mastablasta on 2014-07-09
try changing the server you update/upgrade from. you can try something outside of india but with good ping. also in software sources. 

if another server also says forbiden then there oculd a problem with your digital siganture. 

maybe try main server: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

what is your connection? is it limited or and open unlimited planb? if it's unlimited then select main one. might be slower but just leave it running.

once i couldn't get to my country's server so i chose a neighbouring country server and it worked fine.

---

### Post by westie457 on 2014-07-09
Hi, now is a good time to change the server you are downloading from. The Excellmedia servers are down, probably for maintenance.

Go to Software Sources - posted here previously - in the 'Ubuntu Software' tab find the 'Download from' and click on change server. Choose either the one suggested for your country 'main Server'. Close out this then open a terminal ```
sudo apt-get update
sudo apt-get upgrade
```
Post back with any errors or if the upgrade works.

Thank you.


Edit: Slightly ninja'ed by mastablasta

---

### Post by sooraj2 on 2014-07-09
> **mastablasta said:**
> try changing the server you update/upgrade from. you can try something outside of india but with good ping. also in software sources. 

if another server also says forbiden then there oculd a problem with your digital siganture. 

maybe try main server: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

what is your connection? is it limited or and open unlimited planb? if it's unlimited then select main one. might be slower but just leave it running.

once i couldn't get to my country's server so i chose a neighbouring country server and it worked fine.


my connection is unlimited but only 1mbps download  speed it takes me 3 hrs to download 1gb file 

i tried my country server us server and main server all give forbidden error

---

### Post by mastablasta on 2014-07-09
> **westie457 said:**
>  The Excellmedia servers are down, probably for maintenance.


they are not down. 

it seems to be a permission/singature issue. or perhaps there are partially downloaded files.

hmm could this solve it?
```
[FONT=Courier New]sudo rm -r /var/cache/apt/archives/partial/[/FONT]
```

are you behind a proxy?

before oyu do any commands can you please post the soruces.list file using code tags.

1 MBps is not that bad if it's stable. just takes longer to download...

---

### Post by sooraj2 on 2014-07-09
> **mastablasta said:**
> they are not down. 

it seems to be a permission/singature issue. or perhaps there are partially downloaded files.

hmm could this solve it?
```
[FONT=Courier New]sudo rm -r /var/cache/apt/archives/partial/[/FONT]
```

are you behind a proxy?

before oyu do any commands can you please post the soruces.list file using code tags.

1 MBps is not that bad if it's stable. just takes longer to download...

here is my sources.list  file  
 ```
# 

# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ dists/precise/main/binary-i386/
# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ precise main restricted


# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ dists/precise/main/binary-i386/
# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ precise main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ubuntu.excellmedia.net/archive/ trusty main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://ubuntu.excellmedia.net/archive/ trusty-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ubuntu.excellmedia.net/archive/ trusty universe
deb http://ubuntu.excellmedia.net/archive/ trusty-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ubuntu.excellmedia.net/archive/ trusty multiverse
deb http://ubuntu.excellmedia.net/archive/ trusty-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ubuntu.excellmedia.net/archive/ trusty-backports main restricted universe multiverse


deb http://ubuntu.excellmedia.net/archive/ trusty-security main restricted
deb http://ubuntu.excellmedia.net/archive/ trusty-security universe
deb http://ubuntu.excellmedia.net/archive/ trusty-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu trusty partner
deb-src http://archive.canonical.com/ubuntu trusty partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main
# deb http://archive.canonical.com/ lucid partner
# deb-src http://archive.canonical.com/ lucid partner
# deb http://archive.ubuntu.com/ubuntu hardy-updates main multiverse
# deb-src http://archive.ubuntu.com/ubuntu hardy-updates main multiverse
deb http://mirror.siamdata.co.th/ubuntu/ precise multiverse restricted universe main
```

ya my 1mbps connection is stable

---

### Post by Bashing-om on 2014-07-10
sooraj2; Welp;

I note there is still this "fetch" in /etc/apt/sources.list file:
> 
deb [http://mirror.siamdata.co.th/ubuntu/](http://mirror.siamdata.co.th/ubuntu/) [color=red]precise[/color] multiverse restricted universe main

There should be no reason to have that repository, it can only cause problems. Comment it out also, or disable it from the USC.
Then run terminal commands:
```

sudo apt-get update
sudo apt-get upgrade

``` to see what the package manager thinks now.

[INDENT][INDENT]if the package manager is not happy
[INDENT][INDENT][INDENT][INDENT]nobody is happy
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by sooraj2 on 2014-07-11
> **Bashing-om said:**
> sooraj2; Welp;

I note there is still this "fetch" in /etc/apt/sources.list file:

There should be no reason to have that repository, it can only cause problems. Comment it out also, or disable it from the USC.
Then run terminal commands:
```

sudo apt-get update
sudo apt-get upgrade

``` to see what the package manager thinks now.[INDENT][INDENT]if the package manager is not happy[INDENT][INDENT][INDENT][INDENT]nobody is happy
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]



```

sudo apt-get update

```
```
traeko@Sooraj:~$ sudo apt-get update[sudo] password for traeko: 
Hit http://www.openprinting.org lsb3.2 Release.gpg                             
Hit http://www.openprinting.org lsb3.2 Release                                 
Hit http://www.openprinting.org lsb3.2/contrib amd64 Packages                  
Hit http://www.openprinting.org lsb3.2/contrib i386 Packages                                                                                    
Ign http://www.openprinting.org lsb3.2/contrib TranslationIndex                                                                                 
Hit http://ppa.launchpad.net trusty Release.gpg                                                                                                 
Hit http://ppa.launchpad.net trusty Release.gpg                                                                                                 
Hit http://ppa.launchpad.net trusty Release                                                                                                     
Hit http://archive.canonical.com trusty Release.gpg                                                                                             
Hit http://ppa.launchpad.net trusty Release                                                                                                     
Hit http://archive.canonical.com trusty Release                                                                                                 
Hit http://ppa.launchpad.net trusty/main Sources                                                                                               
Hit http://ppa.launchpad.net trusty/main amd64 Packages                                                                                       
Hit http://ppa.launchpad.net trusty/main i386 Packages                                                                                        
Ign http://ppa.launchpad.net trusty/main TranslationIndex                                                                                     
Hit http://archive.canonical.com trusty/partner Sources                                                                                       
Hit http://ppa.launchpad.net trusty/main Sources                                                                                              
Hit http://ppa.launchpad.net trusty/main amd64 Packages                                                                 
Hit http://ppa.launchpad.net trusty/main i386 Packages                                                                  
Ign http://ppa.launchpad.net trusty/main TranslationIndex                                                               
Hit http://archive.canonical.com trusty/partner amd64 Packages                                                          
Hit http://archive.canonical.com trusty/partner i386 Packages                                                           
Ign http://archive.canonical.com trusty/partner TranslationIndex                                                        
Ign http://archive.canonical.com trusty/partner Translation-en_US                                                                             
Ign http://archive.canonical.com trusty/partner Translation-en                                                                                
Ign http://ppa.launchpad.net trusty/main Translation-en_US                                        
Ign http://ppa.launchpad.net trusty/main Translation-en                                           
Ign http://ppa.launchpad.net trusty/main Translation-en_US                                                                                      
Ign http://ppa.launchpad.net trusty/main Translation-en                                                                                         
Hit http://ubuntu.excellmedia.net trusty Release.gpg                                                                                            
Hit http://ubuntu.excellmedia.net trusty-updates Release.gpg                                      
Hit http://ubuntu.excellmedia.net trusty-backports Release.gpg                                                                                  
Hit http://ubuntu.excellmedia.net trusty-security Release.gpg                                                                                   
Hit http://ubuntu.excellmedia.net precise Release.gpg                                                                                           
Hit http://ubuntu.excellmedia.net trusty Release                                                                  
Hit http://ubuntu.excellmedia.net trusty-updates Release                                                           
Hit http://ubuntu.excellmedia.net trusty-backports Release                                                                                      
Hit http://ubuntu.excellmedia.net trusty-security Release                                                                                       
Hit http://ubuntu.excellmedia.net precise Release                                                                                               
Ign http://www.openprinting.org lsb3.2/contrib Translation-en_US                                                                         
Hit http://ubuntu.excellmedia.net trusty/main amd64 Packages                                                      
Hit http://ubuntu.excellmedia.net trusty/restricted amd64 Packages                          
Hit http://ubuntu.excellmedia.net trusty/universe amd64 Packages                                                                                
Hit http://ubuntu.excellmedia.net trusty/multiverse amd64 Packages                                                                              
Hit http://ubuntu.excellmedia.net trusty/main i386 Packages                                                                                     
Hit http://www.openprinting.org lsb3.2/contrib Translation-en                                                     
Hit http://ubuntu.excellmedia.net trusty/restricted i386 Packages                                                 
Hit http://ubuntu.excellmedia.net trusty/universe i386 Packages                             
Hit http://ubuntu.excellmedia.net trusty/multiverse i386 Packages                           
Hit http://ubuntu.excellmedia.net trusty/main TranslationIndex                              
Hit http://ubuntu.excellmedia.net trusty/multiverse TranslationIndex
Hit http://ubuntu.excellmedia.net trusty/restricted TranslationIndex
Hit http://ubuntu.excellmedia.net trusty/universe TranslationIndex
Hit http://ubuntu.excellmedia.net trusty-updates/main amd64 Packages
Hit http://ubuntu.excellmedia.net trusty-updates/restricted amd64 Packages
Hit http://ubuntu.excellmedia.net trusty-updates/universe amd64 Packages
Hit http://ubuntu.excellmedia.net trusty-updates/multiverse amd64 Packages
Hit http://ubuntu.excellmedia.net trusty-updates/main i386 Packages
Hit http://ubuntu.excellmedia.net trusty-updates/restricted i386 Packages
Hit http://ubuntu.excellmedia.net trusty-updates/universe i386 Packages
Hit http://ubuntu.excellmedia.net trusty-updates/multiverse i386 Packages
Hit http://ubuntu.excellmedia.net trusty-updates/main TranslationIndex
Hit http://ubuntu.excellmedia.net trusty-updates/multiverse TranslationIndex
Hit http://ubuntu.excellmedia.net trusty-updates/restricted TranslationIndex
Hit http://ubuntu.excellmedia.net trusty-updates/universe TranslationIndex
Hit http://ubuntu.excellmedia.net trusty-backports/main amd64 Packages
Hit http://ubuntu.excellmedia.net trusty-backports/restricted amd64 Packages
Hit http://ubuntu.excellmedia.net trusty-backports/universe amd64 Packages
Hit http://ubuntu.excellmedia.net trusty-backports/multiverse amd64 Packages
Hit http://ubuntu.excellmedia.net trusty-backports/main i386 Packages
Hit http://ubuntu.excellmedia.net trusty-backports/restricted i386 Packages
Hit http://ubuntu.excellmedia.net trusty-backports/universe i386 Packages
Hit http://ubuntu.excellmedia.net trusty-backports/multiverse i386 Packages
Hit http://ubuntu.excellmedia.net trusty-backports/main TranslationIndex
Hit http://ubuntu.excellmedia.net trusty-backports/multiverse TranslationIndex
Hit http://ubuntu.excellmedia.net trusty-backports/restricted TranslationIndex
Hit http://ubuntu.excellmedia.net trusty-backports/universe TranslationIndex
Hit http://ubuntu.excellmedia.net trusty-security/main amd64 Packages
Hit http://ubuntu.excellmedia.net trusty-security/restricted amd64 Packages
Hit http://ubuntu.excellmedia.net trusty-security/universe amd64 Packages
Hit http://ubuntu.excellmedia.net trusty-security/multiverse amd64 Packages
Hit http://ubuntu.excellmedia.net trusty-security/main i386 Packages
Hit http://ubuntu.excellmedia.net trusty-security/restricted i386 Packages
Hit http://ubuntu.excellmedia.net trusty-security/universe i386 Packages
Hit http://ubuntu.excellmedia.net trusty-security/multiverse i386 Packages
Err http://extras.ubuntu.com trusty Release.gpg
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Hit http://ubuntu.excellmedia.net trusty-security/main TranslationIndex
Hit http://ubuntu.excellmedia.net trusty-security/multiverse TranslationIndex
Hit http://ubuntu.excellmedia.net trusty-security/restricted TranslationIndex
Hit http://ubuntu.excellmedia.net trusty-security/universe TranslationIndex
Hit http://extras.ubuntu.com trusty Release          
Hit http://ubuntu.excellmedia.net precise/main amd64 Packages
Ign http://extras.ubuntu.com trusty/main Sources/DiffIndex
Hit http://ubuntu.excellmedia.net precise/universe amd64 Packages
Ign http://extras.ubuntu.com trusty/main amd64 Packages/DiffIndex
Ign http://extras.ubuntu.com trusty/main i386 Packages/DiffIndex                
Ign http://extras.ubuntu.com trusty/main TranslationIndex                       
Hit http://ubuntu.excellmedia.net precise/restricted amd64 Packages             
Hit http://extras.ubuntu.com trusty/main Sources                                
Hit http://ubuntu.excellmedia.net precise/multiverse amd64 Packages             
Hit http://extras.ubuntu.com trusty/main amd64 Packages                         
Hit http://extras.ubuntu.com trusty/main i386 Packages                          
Hit http://ubuntu.excellmedia.net precise/main i386 Packages                    
Hit http://ubuntu.excellmedia.net precise/universe i386 Packages                
Hit http://ubuntu.excellmedia.net precise/restricted i386 Packages
Hit http://ubuntu.excellmedia.net precise/multiverse i386 Packages
Hit http://ubuntu.excellmedia.net precise/main TranslationIndex
Hit http://ubuntu.excellmedia.net precise/multiverse TranslationIndex
Hit http://ubuntu.excellmedia.net precise/restricted TranslationIndex
Hit http://ubuntu.excellmedia.net precise/universe TranslationIndex
Hit http://ubuntu.excellmedia.net trusty/main Translation-en
Ign http://extras.ubuntu.com trusty/main Translation-en_US
Hit http://ubuntu.excellmedia.net trusty/multiverse Translation-en
Ign http://extras.ubuntu.com trusty/main Translation-en   
Hit http://ubuntu.excellmedia.net trusty/restricted Translation-en
Hit http://ubuntu.excellmedia.net trusty/universe Translation-en
Hit http://ubuntu.excellmedia.net trusty-updates/main Translation-en
Hit http://ubuntu.excellmedia.net trusty-updates/multiverse Translation-en
Hit http://ubuntu.excellmedia.net trusty-updates/restricted Translation-en
Hit http://ubuntu.excellmedia.net trusty-updates/universe Translation-en
Hit http://ubuntu.excellmedia.net trusty-backports/main Translation-en
Hit http://ubuntu.excellmedia.net trusty-backports/multiverse Translation-en
Hit http://ubuntu.excellmedia.net trusty-backports/restricted Translation-en
Hit http://ubuntu.excellmedia.net trusty-backports/universe Translation-en
Hit http://ubuntu.excellmedia.net trusty-security/main Translation-en
Hit http://ubuntu.excellmedia.net trusty-security/multiverse Translation-en
Hit http://ubuntu.excellmedia.net trusty-security/restricted Translation-en
Hit http://ubuntu.excellmedia.net trusty-security/universe Translation-en
Hit http://ubuntu.excellmedia.net precise/main Translation-en
Hit http://ubuntu.excellmedia.net precise/multiverse Translation-en
Hit http://ubuntu.excellmedia.net precise/restricted Translation-en
Hit http://ubuntu.excellmedia.net precise/universe Translation-en
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/trusty/Release.gpg  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)


E: Some index files failed to download. They have been ignored, or old ones used instead.
traeko@Sooraj:~$ 

```

```

sudo apt-get upgrade

``` 

```
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libt/libtheora/libtheora0_1.1.1+dfsg.1-3.2_amd64.deb  403  ForbiddenFailed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libt/libtheora/libtheora0_1.1.1+dfsg.1-3.2_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libshout/libshout3_2.3.1-3_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libshout/libshout3_2.3.1-3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libsndfile/libsndfile1_1.0.25-7ubuntu2_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libsndfile/libsndfile1_1.0.25-7ubuntu2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libspectre/libspectre1_0.2.7-2ubuntu1.1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libssh/libssh-4_0.6.1-0ubuntu3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/o/openssl098/libssl0.9.8_0.9.8o-7ubuntu3.2.14.04.1_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libx11/libx11-xcb1_1.6.2-1ubuntu2_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libx11/libx11-xcb1_1.6.2-1ubuntu2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xcb-util/libxcb-util0_0.3.8-2ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/startup-notification/libstartup-notification0_0.12-3ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-25ubuntu4_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/sysfsutils/libsysfs2_2.1.0+repack-3ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/taglib/libtag1-vanilla_1.9.1-2_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/taglib/libtag1-vanilla_1.9.1-2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/taglib/libtag1c2a_1.9.1-2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/taglib/libtag1c2a_1.9.1-2_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/talloc/libtalloc2_2.1.0-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/telepathy-glib/libtelepathy-glib0_0.22.1-1ubuntu2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libt/libthai/libthai-data_0.1.20-3_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libt/libthai/libthai0_0.1.20-3_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libt/libthai/libthai0_0.1.20-3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libu/libunistring/libunistring0_0.9.3-5ubuntu3_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libu/libunistring/libunistring0_0.9.3-5ubuntu3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/v/v4l-utils/libv4l-0_1.0.1-1_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/v/v4l-utils/libv4l-0_1.0.1-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/v/v4l-utils/libv4lconvert0_1.0.1-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/v/v4l-utils/libv4lconvert0_1.0.1-1_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libv/libva/libva1_1.3.0-2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libv/libva/libva-x11-1_1.3.0-2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/v/vala-0.16/valac-0.16-vapi_0.16.1-2ubuntu4_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/v/vala-0.16/valac-0.16_0.16.1-2ubuntu4_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/v/vala-0.16/libvala-0.16-0_0.16.1-2ubuntu4_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libv/libvisual/libvisual-0.4-0_0.4.0-5_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libv/libvisual/libvisual-0.4-0_0.4.0-5_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libv/libvpx/libvpx1_1.3.0-2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libw/libwacom/libwacom2_0.8-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libw/libwacom/libwacom-common_0.8-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/wavpack/libwavpack1_4.70.0-1_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/wavpack/libwavpack1_4.70.0-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libw/libwmf/libwmf0.2-7-gtk_0.2.8.4-10.3ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libw/libwmf/libwmf0.2-7_0.2.8.4-10.3ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/tcp-wrappers/libwrap0_7.6.q-25_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/tcp-wrappers/libwrap0_7.6.q-25_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libx86/libx86-1_1.1+ds1-10_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxmu/libxmu6_1.1.1-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxmu/libxmu6_1.1.1-1_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxpm/libxpm4_3.5.10-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxpm/libxpm4_3.5.10-1_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxaw/libxaw7_1.0.12-1_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxaw/libxaw7_1.0.12-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcb/libxcb-composite0_1.10-2ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcb/libxcb-dri2-0_1.10-2ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcb/libxcb-glx0_1.10-2ubuntu1_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcb/libxcb-glx0_1.10-2ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcb/libxcb-randr0_1.10-2ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcb/libxcb-shape0_1.10-2ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcb/libxcb-xv0_1.10-2ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcomposite/libxcomposite-dev_0.4.4-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcomposite/libxcomposite1_0.4.4-1_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcomposite/libxcomposite1_0.4.4-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcursor/libxcursor-dev_1.1.14-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcursor/libxcursor1_1.1.14-1_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcursor/libxcursor1_1.1.14-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxdamage/libxdamage-dev_1.1.4-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxdamage/libxdamage1_1.1.4-1ubuntu1_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxdamage/libxdamage1_1.1.4-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxfont/libxfont1_1.4.7-1ubuntu0.1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xft/libxft-dev_2.3.1-2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xft/libxft2_2.3.1-2_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xft/libxft2_2.3.1-2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxinerama/libxinerama-dev_1.1.3-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxinerama/libxinerama1_1.1.3-1_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxinerama/libxinerama1_1.1.3-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxp/libxp6_1.0.2-1ubuntu1_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxp/libxp6_1.0.2-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxrandr/libxrandr-dev_1.4.2-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxrandr/libxrandr2_1.4.2-1_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxrandr/libxrandr2_1.4.2-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/x11proto-randr/x11proto-randr-dev_1.4.0+git20120101.is.really.1.4.0-0ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxres/libxres1_1.0.7-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/x11proto-scrnsaver/x11proto-scrnsaver-dev_1.2.2-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxss/libxss-dev_1.2.2-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxss/libxss1_1.2.2-1_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxss/libxss1_1.2.2-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxtst/libxtst6_1.2.2-1_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxtst/libxtst6_1.2.2-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxv/libxv1_1.0.10-1_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxv/libxv1_1.0.10-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxvmc/libxvmc1_1.0.8-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxxf86dga/libxxf86dga1_1.1.4-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxxf86vm/libxxf86vm1_1.1.3-1_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxxf86vm/libxxf86vm1_1.1.3-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/z/zephyr/libzephyr4_3.1.2-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/z/zvbi/libzvbi-common_0.2.35-2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/z/zvbi/libzvbi0_0.2.35-2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unixodbc/odbcinst_2.2.14p2-5ubuntu5_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unixodbc/odbcinst1debian2_2.2.14p2-5ubuntu5_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unixodbc/odbcinst1debian2_2.2.14p2-5ubuntu5_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pcmciautils/pcmciautils_018-8_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qt-at-spi/qt-at-spi_0.3.1-4fakesync1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/tasksel/tasksel-data_2.88ubuntu15_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/tasksel/tasksel_2.88ubuntu15_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/c/cabextract/cabextract_1.4-4_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xfonts-utils/xfonts-utils_7.7+1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/multiverse/m/msttcorefonts/ttf-mscorefonts-installer_3.4+nmu1ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/f/fonts-unfonts-core/ttf-unfonts-core_1.0.3.is.1.0.2-080608-10ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xaw3d/xaw3dg_1.5+E-18.2_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/wget/wget_1.15-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/liba/libass/libass4_0.10.1-3ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/liba/libavc1394/libavc1394-0_0.5.4-2_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/liba/libavc1394/libavc1394-0_0.5.4-2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/i/isdnutils/libcapi20-3_3.25+dfsg1-3.3ubuntu2_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/i/isdnutils/libcapi20-3_3.25+dfsg1-3.3ubuntu2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libd/libdc1394-22/libdc1394-22_2.2.1-2ubuntu2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libd/libdca/libdca0_0.0.5-6ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/wireless-tools/libiw30_30~pre9-8ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libl/liblouis/liblouis-data_2.5.3-2ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libl/liblouis/liblouis2_2.5.3-2ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/o/openal-soft/libopenal1_1.14-4ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/o/openal-soft/libopenal1_1.14-4ubuntu1_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/o/openal-soft/libopenal-data_1.14-4ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/speech-dispatcher/libspeechd2_0.8-5ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xcb-util-keysyms/libxcb-keysyms1_0.3.9-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/o/openjdk-6/icedtea-6-jre-cacao_6b31-1.13.3-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/o/openjdk-6/openjdk-6-jre-lib_6b31-1.13.3-1ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/o/openjdk-6/icedtea-6-jre-jamvm_6b31-1.13.3-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/openssl/openssl_1.0.1f-1ubuntu2.4_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/o/openjdk-6/openjdk-6-jre-headless_6b31-1.13.3-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/less/less_458-2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libc/libcap2/libcap2-bin_2.24-0ubuntu2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libc/libcap2/libpam-cap_2.24-0ubuntu2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lockfile-progs/lockfile-progs_0.1.17_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/logrotate/logrotate_3.8.7-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mime-support/mime-support_3.54ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/net-tools/net-tools_1.60-25ubuntu2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/netcat-openbsd/netcat-openbsd_1.105-7ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/sudo/sudo_1.8.9p5-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/ureadahead/ureadahead_0.100.0-16_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/v/vim/vim-tiny_7.4.052-1ubuntu3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/v/vim/vim-common_7.4.052-1ubuntu3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/newt/whiptail_0.52.15-2ubuntu5_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/netkit-ftp/ftp_0.17-28_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/texinfo/info_5.2.0.dfsg.1-2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lshw/lshw_02.16-2ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lsof/lsof_4.86+dfsg-1ubuntu2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/ltrace/ltrace_0.7.3-4ubuntu5.1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/manpages/manpages_3.54-1ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/memtest86+/memtest86+_4.20-1.1ubuntu8_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mlocate/mlocate_0.26-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mtr/mtr-tiny_0.85-2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/nano/nano_2.2.6-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/parted/parted_2.3-19ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/plymouth/plymouth-theme-ubuntu-text_0.8.8-0ubuntu17_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/powermgmt-base/powermgmt-base_1.31build1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/ppp/ppp_2.4.5-5.1ubuntu2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pppconfig/pppconfig_2.3.19ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/psmisc/psmisc_22.20-1ubuntu2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-apt/python-apt-common_0.9.3.5_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/rsync/rsync_3.1.0-2ubuntu0.1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/strace/strace_4.8-1ubuntu5_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/tcpdump/tcpdump_4.5.1-2ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/netkit-telnet/telnet_0.17-36build2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/time/time_1.7-24_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/ubuntu-meta/ubuntu-standard_1.325_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/util-linux/uuid-runtime_2.20.1-5.1ubuntu20.1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xauth/xauth_1.0.7-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xml-core/xml-core_0.13+nmu2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/make-dfsg/make_3.81-8.2ubuntu3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xapian-core/libxapian22_1.2.16-2ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xapian-bindings/python-xapian_1.2.16-2ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libd/libdaemon/libdaemon0_0.14-2ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/rarian/librarian0_0.8.1-5ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/sgml-data/sgml-data_2.0.9-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/rarian/rarian-compat_0.8.1-5ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/b/bless/bless_0.6.0-4_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/b/bluez/bluez-gstreamer_4.101-0ubuntu13_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/liby/libyaml-tiny-perl/libyaml-tiny-perl_1.56-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_11.2.202.394ubuntu0.14.04.1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/libreoffice/fonts-opensymbol_102.6+LibO4.2.4-0ubuntu2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/f/fuseiso/fuseiso_20070708-3ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/liba/libappindicator/gir1.2-appindicator3-0.1_12.10.1+13.10.20130920-0ubuntu4_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/systemd/gir1.2-gudev-1.0_204-5ubuntu20.3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libn/libnotify/gir1.2-notify-0.7_0.7.6-1ubuntu3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libe/liberror-perl/liberror-perl_0.17-1.1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gksu/gksu_2.0.2-6ubuntu2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/x11-utils/x11-utils_7.7+1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gnome-media/gnome-media_3.4.0-1ubuntu2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libn/libnice/gstreamer0.10-nice_0.1.4-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/guile-1.8/guile-1.8-libs_1.8.8+1-8ubuntu3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/h/heirloom-mailx/heirloom-mailx_12.5-2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/libreoffice-dictionaries/hunspell-en-ca_4.2.1-0ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libn/libnet-http-perl/libnet-http-perl_6.06-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libl/liblwp-mediatypes-perl/liblwp-mediatypes-perl_6.02-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libt/libtimedate-perl/libtimedate-perl_2.3000-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libh/libhttp-date-perl/libhttp-date-perl_6.02-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libh/libhttp-daemon-perl/libhttp-daemon-perl_6.01-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libu/liburi-perl/liburi-perl_1.60-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libh/libhtml-form-perl/libhtml-form-perl_6.03-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libf/libfile-listing-perl/libfile-listing-perl_6.04-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libe/libencode-locale-perl/libencode-locale-perl_1.03-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libh/libhtml-tree-perl/libhtml-tree-perl_5.03-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libw/libwww-perl/libwww-perl_6.05-2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/i/icoutils/icoutils_0.31.0-2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xbitmaps/xbitmaps_1.1.1-2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libu/libutempter/libutempter0_1.1.5-4build1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xterm/xterm_297-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/i/im-switch/im-switch_1.23ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/k/kate/kate-data_4.13.2-0ubuntu0.1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/k/kernel-package/kernel-package_12.036+nmu3_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/readline5/lib32readline-gplv2-dev_5.2+dfsg-2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/readline5/lib32readline5_5.2+dfsg-2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/readline6/lib32readline6_6.3-4ubuntu2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/a/a52dec/liba52-0.7.4_0.7.4-17_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/liba/libalgorithm-diff-perl/libalgorithm-diff-perl_1.19.02-3_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/o/openjdk-6/openjdk-6-jre_6b31-1.13.3-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libb/libbonoboui/libbonoboui2-common_2.24.5-0ubuntu3_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libb/libburn/libburn4_1.3.4-0ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libc/libcanberra/libcanberra-gtk-module_0.30-0ubuntu3_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libc/libcanberra/libcanberra-gtk-module_0.30-0ubuntu3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libc/libcddb/libcddb2_1.3.2-4fakesync2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libc/libcdio/libcdio13_0.83-4.1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libc/libcdio/libcdio-cdda1_0.83-4.1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libc/libcdio/libcdio-paranoia1_0.83-4.1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libc/libclass-isa-perl/libclass-isa-perl_0.36-5_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libn/libnet-domain-tld-perl/libnet-domain-tld-perl_1.70-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libe/libemail-valid-perl/libemail-valid-perl_1.192-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libf/libfile-desktopentry-perl/libfile-desktopentry-perl_0.07-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libf/libfile-mimeinfo-perl/libfile-mimeinfo-perl_0.22-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libg/libgda5/libgda-5.0-common_5.2.2-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgdata/libgdata-common_0.14.1-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gnome-menus2/libgnome-menu2_3.0.1-0ubuntu9_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgnome/libgnome2-bin_2.32.1-4ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgnome/libgnome2-common_2.32.1-4ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgnomecanvas/libgnomecanvas2-common_2.30.3-2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgnomekbd/libgnomekbd-common_3.6.0-0ubuntu2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgnomeui/libgnomeui-common_2.24.5-3_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgphoto2/libgphoto2-l10n_2.5.3.1-1ubuntu2.2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gtksourceview2/libgtksourceview2.0-common_2.10.5-1ubuntu2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgtop2/libgtop2-common_2.28.5-2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgtop2/libgtop2-7_2.28.5-2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libh/libhtml-format-perl/libhtml-format-perl_2.11-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libi/libid3tag/libid3tag0_0.15.1b-10ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libi/libindicate/libindicate-gtk3_12.10.1-0ubuntu3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libi/libio-socket-inet6-perl/libio-socket-inet6-perl_2.71-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libi/libio-string-perl/libio-string-perl_1.08-3_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libi/libipc-run-perl/libipc-run-perl_0.92-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libc/libcdio/libiso9660-8_0.83-4.1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libi/libisofs/libisofs6_1.3.4-0ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libk/libkate/libkate1_0.4.1-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/meanwhile/libmeanwhile1_1.0.2-4.1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/miniupnpc/libminiupnpc8_1.6-3ubuntu2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libm/libmodplug/libmodplug1_0.8.8.4-4.1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libm/libmpc/libmpcdec6_0.1~r459-1ubuntu3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mythes/libmythes-1.2-0_1.2.2-1ubuntu2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libn/libnet-ip-perl/libnet-ip-perl_1.26-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/network-manager/libnm-glib-vpn1_0.9.8.8-0ubuntu7_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/network-manager-applet/libnm-gtk-common_0.9.8.8-0ubuntu4.2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libn/libnotify/libnotify-bin_0.7.6-1ubuntu3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/n/ntrack/ntrack-module-libnl-0_016-1.2ubuntu2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/n/ntrack/libntrack0_016-1.2ubuntu2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/n/ntrack/libntrack-qt4-1_016-1.2ubuntu2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libo/libopenobex/libopenobex1_1.5-2.1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pango1.0/libpango1.0-doc_1.36.3-1ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libp/libpaper/libpaper-utils_1.1.24+nmu2ubuntu3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libp/libparse-debcontrol-perl/libparse-debcontrol-perl_2.005-4_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libp/libpostproc/libpostproc52_0.git20120821-4_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/postgresql-9.3/libpq5_9.3.4-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pidgin/libpurple-bin_2.10.9-0ubuntu3.1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/libreoffice/libreoffice-style-human_4.2.4-0ubuntu2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/s/sidplay-libs/libresid-builder0c2a_2.1.1-14_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/sg3-utils/libsgutils2-2_1.36-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libs/libsidplay/libsidplay1_1.36.59-5ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/s/sidplay-libs/libsidplay2_2.1.1-14_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/openslp-dfsg/libslp1_1.2.1-9_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libsys-hostname-long-perl/libsys-hostname-long-perl_1.4-3_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/t1lib/libt1-5_5.1.2-3.6ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libt/libtar/libtar0_1.2.20-3ubuntu0.1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libt/libtie-ixhash-perl/libtie-ixhash-perl_1.23-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libt/libtool/libtool_2.4.2-1.7ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/t/twolame/libtwolame0_0.3.13-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/u/unity/unity-2d-spread_7.2.1+14.04.20140513-0ubuntu2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/u/unity/unity-2d-panel_7.2.1+14.04.20140513-0ubuntu2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/u/unity/unity-2d-shell_7.2.1+14.04.20140513-0ubuntu2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/u/unity/libunity-2d-private0_7.2.1+14.04.20140513-0ubuntu2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/v/vcdimager/libvcdinfo0_0.7.24+dfsg-0.1ubuntu2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/v/virtuoso-opensource/libvirtodbc0_6.1.6+repack-0ubuntu3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/v/virtuoso-opensource/virtuoso-opensource-6.1-common_6.1.6+repack-0ubuntu3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libv/libvisual-plugins/libvisual-0.4-plugins_0.4.0.dfsg.1-7build1_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libv/libvisual-plugins/libvisual-0.4-plugins_0.4.0.dfsg.1-7build1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/v/vte/libvte-common_0.28.2-5ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/v/vte/libvte9_0.28.2-5ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/webkitgtk/libwebkitgtk-1.0-common_2.4.3-1ubuntu2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/webkitgtk/libwebkitgtk-3.0-common_2.4.3-1ubuntu2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libw/libwnck3/libwnck-3-common_3.4.7-0ubuntu3_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libw/libwnck/libwnck-common_2.30.7-0ubuntu4_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libw/libwpd/libwpd-0.9-9_0.9.9-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libw/libwpg/libwpg-0.2-2_0.2.2-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libw/libwps/libwps-0.2-2_0.2.9-2ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libx11/libx11-doc_1.6.2-1ubuntu2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/ubuntu-themes/ubuntu-mono_14.04+14.04.20140410-0ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/ubuntu-themes/light-themes_14.04+14.04.20140410-0ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/linux-firmware/linux-firmware_1.127.4_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/manpages/manpages-dev_3.54-1ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/media-player-info/media-player-info_21-0ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pygobject-2/python-gobject-2_2.28.6-12build1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/patch/patch_2.7.1-4ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/m/meld/meld_1.8.4-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/metacity/metacity-common_2.34.13-0ubuntu4_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/m/mingw32-binutils/mingw32-binutils_2.20-0.2ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mtools/mtools_4.0.18-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/openoffice.org-en-au/myspell-en-au_2.1-5.4_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/libreoffice-dictionaries/myspell-en-gb_4.2.1-0ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/libreoffice-dictionaries/myspell-en-za_4.2.1-0ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/openoffice.org-en-au/mythes-en-au_2.1-5.4_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/libreoffice-dictionaries/mythes-en-us_4.2.1-0ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/ncurses/ncurses-term_5.9+20140118-1ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/notify-osd-icons/notify-osd-icons_0.8+14.04.20131204-0ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/nux/nux-tools_4.0.6+14.04.20140409-0ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/obex-data-server/obex-data-server_0.4.6-0ubuntu2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/obexd/obexd-client_0.46-1ubuntu7_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/openoffice.org-hyphenation/openoffice.org-hyphenation_0.7_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/os-prober/os-prober_1.63ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/o/oxygen-icons/oxygen-icon-theme_4.13.0-0ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/patchutils/patchutils_0.3.2-3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pax/pax_20120606-2+deb7u1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/phonon/phonon_4.7.1-0ubuntu8_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/ubuntu-font-family-sources/ttf-ubuntu-font-family_0.80-0ubuntu6_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/plymouth/plymouth-theme-ubuntu-logo_0.8.8-0ubuntu17_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/p/pngcrush/pngcrush_1.7.65-0.1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/policykit-1-gnome/policykit-1-gnome_0.105-1ubuntu4_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pptp-linux/pptp-linux_1.7.2-7_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/min12xxw/printer-driver-min12xxw_0.0.9-8ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pnm2ppa/printer-driver-pnm2ppa_1.13+nondbs-0ubuntu4_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pulseaudio/pulseaudio-module-gconf_4.0-0ubuntu11_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pulseaudio/pulseaudio-module-x11_4.0-0ubuntu11_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-httplib2/python-httplib2_0.8-2build1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-setuptools/python-pkg-resources_3.3-1ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lazr.uri/python-lazr.uri_1.0.3-1build1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-wadllib/python-wadllib_1.3.2-2build1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/z/zope.interface/python-zope.interface_4.0.5-1ubuntu4_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-oauth/python-oauth_1.0.1-3build2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lazr.restfulclient/python-lazr.restfulclient_0.13.3-1build1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-launchpadlib/python-launchpadlib_1.10.2+ds-2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pycairo/python-cairo_1.8.8-1ubuntu5_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pyxdg/python-xdg_0.25-4_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/p/python-configglue/python-configglue_1.1.2-0ubuntu2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/system-config-printer/python-cupshelpers_1.4.3+20140219-0ubuntu2.1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-dateutil/python-dateutil_1.5+dfsg-1ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/f/flup/python-flup_1.0.2-4_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-stdlib-extensions/python-gdbm_2.7.5-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/i/ipy/python-ipy_0.81-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libp/libproxy/python-libproxy_0.4.11-0ubuntu4_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/markupsafe/python-markupsafe_0.18-1build2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mako/python-mako_0.9.1-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/notify-python/python-notify_0.1.1-3ubuntu2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pyopenssl/python-openssl_0.13-2ubuntu6_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-pam/python-pam_0.4.2-13.1ubuntu3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pexpect/python-pexpect_3.1-1ubuntu0.1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/psycopg2/python-psycopg2_2.4.5-1build5_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pyinotify/python-pyinotify_0.9.4-1build1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-reportlab/python-renderpm_3.0-1build1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-reportlab/python-reportlab-accel_3.0-1build1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pyserial/python-serial_2.6-1build1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/s/software-properties/python-software-properties_0.92.37.1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/p/python-support/python-support_1.0.15_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/twisted/python-twisted-bin_13.2.0-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/twisted/python-twisted-core_13.2.0-1ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/twisted/python-twisted-names_13.2.0-1ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/twisted/python-twisted-web_13.2.0-1ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/v/virtkey/python-virtkey_0.63.0-0ubuntu3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/p/pywebkitgtk/python-webkit_1.1.8-3ubuntu2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/w/webpy/python-webpy_0.37+20120626-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/x/x-kit/python-xkit_0.5.0ubuntu2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/z/zeitgeist/python-zeitgeist_0.9.14-0ubuntu4_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/q/q4wine/q4wine_1.1-r2-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/r/radeontool/radeontool_1.6.3-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/multiverse/r/rar/rar_4.2.0-1_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/rfkill/rfkill_0.5-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/rtkit/rtkit_0.10-3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/update-inetd/update-inetd_4.43_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/sane-backends/sane-utils_1.0.23-3ubuntu3.1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/shared-desktop-ontologies/shared-desktop-ontologies_0.11.0-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/sharutils/sharutils_4.14-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xdg-utils/xdg-utils_1.1.0~rc1-2ubuntu7_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/simple-scan/simple-scan_3.12.1-0ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/sni-qt/sni-qt_0.2.6-0ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/squashfs-tools/squashfs-tools_4.2+20130409-2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/openssh/ssh-askpass-gnome_6.6p1-2ubuntu2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/ssl-cert/ssl-cert_1.0.33_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/syslinux/syslinux-common_4.05+dfsg-6+deb8u1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/syslinux/syslinux_4.05+dfsg-6+deb8u1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/system-config-printer/system-config-printer-common_1.4.3+20140219-0ubuntu2.1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/tcp-wrappers/tcpd_7.6.q-25_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/telepathy-idle/telepathy-idle_0.2.0-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/thunderbird/thunderbird-globalmenu_24.6.0+build1-0ubuntu0.14.04.1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/thunderbird/thunderbird-locale-en-gb_24.6.0+build1-0ubuntu0.14.04.1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/thunderbird/thunderbird-locale-en-us_24.6.0+build1-0ubuntu0.14.04.1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/tofrodos/tofrodos_1.7.13+ds-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/toshset/toshset_1.76-4_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/ttf-indic-fonts/ttf-indic-fonts-core_0.5.14ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/ttf-indic-fonts/ttf-punjabi-fonts_0.5.14ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/ubuntu-themes/ubuntu-artwork_14.04+14.04.20140410-0ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/ubuntu-docs/ubuntu-docs_14.04.4_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/u/ubuntu-wallpapers/ubuntu-wallpapers-precise_14.04.0.1-0ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/u/unity/unity-2d_7.2.1+14.04.20140513-0ubuntu2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/u/unity/unity-2d-common_7.2.1+14.04.20140513-0ubuntu2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity-asset-pool/unity-asset-pool_0.8.24daily13.06.10-0ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unixodbc/unixodbc_2.2.14p2-5ubuntu5_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/multiverse/u/unrar-nonfree/unrar_5.0.10-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unzip/unzip_6.0-9ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/v/valgrind/valgrind_3.10~20140411-0ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/v/vbetool/vbetool_1.1-3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/v/virtuoso-opensource/virtuoso-opensource-6.1-bin_6.1.6+repack-0ubuntu3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/v/virtuoso-opensource/virtuoso-minimal_6.1.6+repack-0ubuntu3_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/wdiff/wdiff_1.2.1-2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/whois/whois_5.1.1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/wireless-tools/wireless-tools_30~pre9-8ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/x11-apps/x11-apps_7.7+2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/x11-session-utils/x11-session-utils_7.7+1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/x11-xfs-utils/x11-xfs-utils_7.7+1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/x11-xkb-utils/x11-xkb-utils_7.7+1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/x11-xserver-utils/x11-xserver-utils_7.7+2ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/x11proto-fixes/x11proto-fixes-dev_5.0-2ubuntu2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/x/xcftools/xcftools_1.0.7-4ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/x/xclip/xclip_0.12+svn84-4_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xdg-user-dirs/xdg-user-dirs_0.15-1ubuntu3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xinit/xinit_1.3.2-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xinput/xinput_1.6.1-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xorg/xorg_7.7+1ubuntu8_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xorg/xserver-xorg_7.7+1ubuntu8_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xorg-docs/xorg-docs-core_1.7-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xorg-server/xserver-common_1.15.1-0ubuntu2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/ubufox/xul-ext-ubufox_2.9-0ubuntu0.14.04.1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/y/yelp-xsl/yelp-xsl_3.10.1-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/z/zeitgeist/zeitgeist_0.9.14-0ubuntu4_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/z/zip/zip_3.0-8_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/c/compiz/compiz-plugins-main-default_0.9.11.1+14.04.20140701-0ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/c/compiz/compizconfig-backend-gconf_0.9.11.1+14.04.20140701-0ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/h/haskell-bzlib/libghc-bzlib-dev_0.5.0.4-2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/ghc/ghc_7.6.3-10_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gnome-exe-thumbnailer/gnome-exe-thumbnailer_0.9.3-0ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libc/libcanberra/libcanberra-gtk3-module_0.30-0ubuntu3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pkg-kde-tools/libdlrestrictions1_0.15.12ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgweather/libgweather-common_3.10.2-0ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lirc/liblircclient0_0.9.0-0ubuntu5_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libp/libpeas/libpeas-common_1.8.1-2ubuntu2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/polkit-qt-1/libpolkit-qt-1-1_0.103.0-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libq/libquvi-scripts/libquvi-scripts_0.4.21-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lsb/lsb-invalid-mta_4.1+Debian11ubuntu6_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mobile-broadband-provider-info/mobile-broadband-provider-info_20140317-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mscompress/mscompress_0.4-3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/o/openjdk-6/openjdk-6-jdk_6b31-1.13.3-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pbuilder/pbuilder_0.215ubuntu7_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-defer/python-defer_1.0.6-2build1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-lockfile/python-lockfile_0.8-2ubuntu2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libl/liblouis/python-louis_2.5.3-2ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/r/rebuildd/rebuildd_0.4.2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/f/fonts-liberation/ttf-liberation_1.07.3-3_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/usb-modeswitch/usb-modeswitch_2.1.1+repack0-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/usb-modeswitch-data/usb-modeswitch-data_20140327-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xfonts-mathml/xfonts-mathml_6ubuntu1_all.deb  403  Forbidden
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
traeko@Sooraj:~$ 



```

```
sudo gedit /etc/apt/sources.list file
```

```
# 

# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ dists/precise/main/binary-i386/
# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ precise main restricted


# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ dists/precise/main/binary-i386/
# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ precise main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ubuntu.excellmedia.net/archive/ trusty main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://ubuntu.excellmedia.net/archive/ trusty-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ubuntu.excellmedia.net/archive/ trusty universe
deb http://ubuntu.excellmedia.net/archive/ trusty-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ubuntu.excellmedia.net/archive/ trusty multiverse
deb http://ubuntu.excellmedia.net/archive/ trusty-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ubuntu.excellmedia.net/archive/ trusty-backports main restricted universe multiverse


deb http://ubuntu.excellmedia.net/archive/ trusty-security main restricted
deb http://ubuntu.excellmedia.net/archive/ trusty-security universe
deb http://ubuntu.excellmedia.net/archive/ trusty-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu trusty partner
deb-src http://archive.canonical.com/ubuntu trusty partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main
# deb http://archive.canonical.com/ lucid partner
# deb-src http://archive.canonical.com/ lucid partner
# deb http://archive.ubuntu.com/ubuntu hardy-updates main multiverse
# deb-src http://archive.ubuntu.com/ubuntu hardy-updates main multiverse
# deb http://ubuntu.excellmedia.net/archive/ precise multiverse restricted universe main
deb http://ubuntu.excellmedia.net/archive/ precise main universe restricted multiverse
```

i commented out 

```
# deb http://archive.ubuntu.com/ubuntu hardy-updates main multiverse
# deb-src http://archive.ubuntu.com/ubuntu hardy-updates main multiverse
# deb http://ubuntu.excellmedia.net/archive/ precise multiverse restricted universe main

```

---

### Post by sooraj2 on 2014-07-12
> **mastablasta said:**
> they are not down. 

it seems to be a permission/singature issue. or perhaps there are partially downloaded files.

hmm could this solve it?
```
[FONT=Courier New]sudo rm -r /var/cache/apt/archives/partial/[/FONT]
```

are you behind a proxy?

before oyu do any commands can you please post the soruces.list file using code tags.

1 MBps is not that bad if it's stable. just takes longer to download...

please help

---

### Post by Bashing-om on 2014-07-12
sooraj2; Well,

I do not recognize that:
> 
deb [http://ubuntu.excellmedia.net/](http://ubuntu.excellmedia.net/)[color=blue]archive[/color]/ trusty main restricted


is a correct format for this control file:
How could the term 'archive" resolve to the particular distribution "ubuntu" , in your use case?
IE:- > mine looks like this:
```

deb http://us.archive.ubuntu.com/[color=red]ubuntu[/color]/ trusty main restricted

```
Where I have changed my Mirror site to that of the United States default site.

Maybe changing your mirror to the "us.archive.ubuntu.com/" will change the formatting of that control file to something we can recognize ( and correct ?)??
Once the system is stable we can change the mirror to a faster/closer site.

Looking for a reason why

---

### Post by sooraj2 on 2014-07-12
> **Bashing-om said:**
> sooraj2; Well,

I do not recognize that:


is a correct format for this control file:
How could the term 'archive" resolve to the particular distribution "ubuntu" , in your use case?
IE:- > mine looks like this:
```

deb http://us.archive.ubuntu.com/[COLOR=red]ubuntu[/COLOR]/ trusty main restricted

```
Where I have changed my Mirror site to that of the United States default site.

Maybe changing your mirror to the "us.archive.ubuntu.com/" will change the formatting of that control file to something we can recognize ( and correct ?)??
Once the system is stable we can change the mirror to a faster/closer site.

Looking for a reason why


thanks for replying Bashing-om

can i use your source.list  and same us server you used  will it work ?
if yes please paste your source.list

---

### Post by Bashing-om on 2014-07-12
sooraj2; Nope.

You would not want to even try and use my sources.list file; it is highly customized for my use case.

What I suggest is to change your mirror:
As an instance:
ubuntu Software Center ->SOFTWARE SOURCES
On the Ubuntu Software tab, select the drop down for "Download From"
Select Other
Choose your country then click on Choose best server....This will ping all the mirror sites for the best ping and then it will select the better server.
I do this all the time when version upgrade time comes....it makes an unbelievable difference.
Once you do this, In Synaptic Package manager, click reload to get the updated info from your new mirror.
In this use case, choosing the "us.archive.ubuntu.com/" mirror-site for trouble-shooting I suggest is the better course.

As I have advised, I do not understand how "archive" could resolve - others with greater knowledge may advise better. Let's get your source.list file into something we recognize and then we can work with it. Keep in mind, I would not at all be surprised if "archive" is an invalid field and we have to then intervene once more and manually edit in the change. Let's see what happens with the above first before manually editing.

[INDENT][INDENT]me in that situation, is just
[INDENT][INDENT][INDENT]what i would do[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by sooraj2 on 2014-07-12
> **Bashing-om said:**
> sooraj2; Nope.

You would not want to even try and use my sources.list file; it is highly customized for my use case.

What I suggest is to change your mirror:
As an instance:
ubuntu Software Center ->SOFTWARE SOURCES
On the Ubuntu Software tab, select the drop down for "Download From"
Select Other
Choose your country then click on Choose best server....This will ping all the mirror sites for the best ping and then it will select the better server.
I do this all the time when version upgrade time comes....it makes an unbelievable difference.
Once you do this, In Synaptic Package manager, click reload to get the updated info from your new mirror.
In this use case, choosing the "us.archive.ubuntu.com/" mirror-site for trouble-shooting I suggest is the better course.

As I have advised, I do not understand how "archive" could resolve - others with greater knowledge may advise better. Let's get your source.list file into something we recognize and then we can work with it. Keep in mind, I would not at all be surprised if "archive" is an invalid field and we have to then intervene once more and manually edit in the change. Let's see what happens with the above first before manually editing.
[INDENT][INDENT]me in that situation, is just[INDENT][INDENT][INDENT]what i would do[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]

after making my server "us.archive.ubuntu.com/" it seems to work well with 
```
sudo apt-get update
```

```
traeko@Sooraj:~$ sudo apt-get update[sudo] password for traeko: 
Hit http://ubuntu.excellmedia.net trusty Release.gpg
Hit http://ubuntu.excellmedia.net trusty-updates Release.gpg                                                                                    
Hit http://extras.ubuntu.com trusty Release.gpg                                                                                                 
Hit http://ppa.launchpad.net trusty Release.gpg                                                                                                 
Hit http://ppa.launchpad.net trusty Release.gpg                                                                                                 
Hit http://archive.canonical.com trusty Release.gpg                                                                                             
Hit http://ubuntu.excellmedia.net trusty-backports Release.gpg                                                                                  
Hit http://extras.ubuntu.com trusty Release                                                                                                     
Hit http://ppa.launchpad.net trusty Release                                                                                                     
Hit http://archive.canonical.com trusty Release                                                                                         
Hit http://www.openprinting.org lsb3.2 Release.gpg                                                                                      
Hit http://ubuntu.excellmedia.net trusty-security Release.gpg                                                                                   
Hit http://us.archive.ubuntu.com precise Release.gpg                                                                                            
Hit http://ppa.launchpad.net trusty Release                                                                                                     
Hit http://extras.ubuntu.com trusty/main Sources                                                                                                
Hit http://ubuntu.excellmedia.net trusty Release                                                                                                
Hit http://archive.canonical.com trusty/partner Sources                                                                                         
Hit http://ppa.launchpad.net trusty/main Sources                                                                                                
Hit http://ubuntu.excellmedia.net trusty-updates Release                                                                                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                                                                                         
Hit http://ppa.launchpad.net trusty/main i386 Packages                                                                                          
Ign http://ppa.launchpad.net trusty/main TranslationIndex                                                                                       
Hit http://extras.ubuntu.com trusty/main amd64 Packages                                                                                         
Hit http://extras.ubuntu.com trusty/main i386 Packages                                                                                          
Ign http://extras.ubuntu.com trusty/main TranslationIndex                                                                                       
Hit http://archive.canonical.com trusty/partner amd64 Packages                                                                                  
Hit http://archive.canonical.com trusty/partner i386 Packages                                                                                   
Ign http://archive.canonical.com trusty/partner TranslationIndex                                                                                
Hit http://us.archive.ubuntu.com precise Release                                                                                                
Hit http://ubuntu.excellmedia.net trusty-backports Release                                                                                      
Hit http://ppa.launchpad.net trusty/main Sources                                                                                                
Hit http://ppa.launchpad.net trusty/main amd64 Packages                                                                                         
Hit http://ppa.launchpad.net trusty/main i386 Packages                                                                                          
Ign http://ppa.launchpad.net trusty/main TranslationIndex                                                                                       
Hit http://www.openprinting.org lsb3.2 Release                                                                                                  
Hit http://ubuntu.excellmedia.net trusty-security Release                                                                                       
Hit http://us.archive.ubuntu.com precise/main amd64 Packages                                                                                    
Hit http://ubuntu.excellmedia.net trusty/main amd64 Packages                                                                                    
Hit http://ubuntu.excellmedia.net trusty/restricted amd64 Packages                                                                              
Hit http://us.archive.ubuntu.com precise/universe amd64 Packages                                                                                
Hit http://us.archive.ubuntu.com precise/restricted amd64 Packages                                                                              
Hit http://us.archive.ubuntu.com precise/multiverse amd64 Packages                                                                              
Hit http://us.archive.ubuntu.com precise/main i386 Packages                                                                                     
Hit http://us.archive.ubuntu.com precise/universe i386 Packages                                                                                 
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages                                                                               
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages                                                                               
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                                                                                  
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex                                                                            
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex                                                                            
Hit http://www.openprinting.org lsb3.2/contrib amd64 Packages                                                                                   
Hit http://ubuntu.excellmedia.net trusty/universe amd64 Packages                                                                                
Hit http://ubuntu.excellmedia.net trusty/multiverse amd64 Packages                                                                              
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex                                                                              
Hit http://ubuntu.excellmedia.net trusty/main i386 Packages                                                                                     
Hit http://us.archive.ubuntu.com precise/main Translation-en                                                                                    
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en                                                                              
Hit http://ubuntu.excellmedia.net trusty/restricted i386 Packages                                                                      
Hit http://www.openprinting.org lsb3.2/contrib i386 Packages                                                                                    
Hit http://ubuntu.excellmedia.net trusty/universe i386 Packages                                                                                 
Hit http://us.archive.ubuntu.com precise/restricted Translation-en                                                                              
Hit http://ubuntu.excellmedia.net trusty/multiverse i386 Packages                                                                               
Ign http://extras.ubuntu.com trusty/main Translation-en_US                                                                                      
Ign http://archive.canonical.com trusty/partner Translation-en_US                                                                               
Hit http://ubuntu.excellmedia.net trusty/main TranslationIndex                                                                                  
Ign http://extras.ubuntu.com trusty/main Translation-en                                                                                         
Ign http://archive.canonical.com trusty/partner Translation-en                                                                                  
Hit http://us.archive.ubuntu.com precise/universe Translation-en                                                                                
Ign http://www.openprinting.org lsb3.2/contrib TranslationIndex                                                             
Hit http://ubuntu.excellmedia.net trusty/multiverse TranslationIndex 
Hit http://ubuntu.excellmedia.net trusty/restricted TranslationIndex            
Ign http://ppa.launchpad.net trusty/main Translation-en_US                      
Hit http://ubuntu.excellmedia.net trusty/universe TranslationIndex              
Ign http://ppa.launchpad.net trusty/main Translation-en                                                                               
Ign http://ppa.launchpad.net trusty/main Translation-en_US                                                                            
Hit http://ubuntu.excellmedia.net trusty-updates/main amd64 Packages                                 
Ign http://ppa.launchpad.net trusty/main Translation-en                                                                               
Hit http://ubuntu.excellmedia.net trusty-updates/restricted amd64 Packages                                                            
Hit http://ubuntu.excellmedia.net trusty-updates/universe amd64 Packages        
Hit http://ubuntu.excellmedia.net trusty-updates/multiverse amd64 Packages      
Hit http://ubuntu.excellmedia.net trusty-updates/main i386 Packages             
Hit http://ubuntu.excellmedia.net trusty-updates/restricted i386 Packages
Hit http://ubuntu.excellmedia.net trusty-updates/universe i386 Packages
Hit http://ubuntu.excellmedia.net trusty-updates/multiverse i386 Packages
Hit http://ubuntu.excellmedia.net trusty-updates/main TranslationIndex
Hit http://ubuntu.excellmedia.net trusty-updates/multiverse TranslationIndex
Hit http://ubuntu.excellmedia.net trusty-updates/restricted TranslationIndex
Hit http://ubuntu.excellmedia.net trusty-updates/universe TranslationIndex
Hit http://ubuntu.excellmedia.net trusty-backports/main amd64 Packages
Hit http://ubuntu.excellmedia.net trusty-backports/restricted amd64 Packages
Hit http://ubuntu.excellmedia.net trusty-backports/universe amd64 Packages
Hit http://ubuntu.excellmedia.net trusty-backports/multiverse amd64 Packages
Hit http://ubuntu.excellmedia.net trusty-backports/main i386 Packages
Hit http://ubuntu.excellmedia.net trusty-backports/restricted i386 Packages
Hit http://ubuntu.excellmedia.net trusty-backports/universe i386 Packages
Hit http://ubuntu.excellmedia.net trusty-backports/multiverse i386 Packages
Hit http://ubuntu.excellmedia.net trusty-backports/main TranslationIndex
Hit http://ubuntu.excellmedia.net trusty-backports/multiverse TranslationIndex
Hit http://ubuntu.excellmedia.net trusty-backports/restricted TranslationIndex
Hit http://ubuntu.excellmedia.net trusty-backports/universe TranslationIndex
Hit http://ubuntu.excellmedia.net trusty-security/main amd64 Packages
Hit http://ubuntu.excellmedia.net trusty-security/restricted amd64 Packages
Hit http://ubuntu.excellmedia.net trusty-security/universe amd64 Packages
Hit http://ubuntu.excellmedia.net trusty-security/multiverse amd64 Packages
Hit http://ubuntu.excellmedia.net trusty-security/main i386 Packages
Hit http://ubuntu.excellmedia.net trusty-security/restricted i386 Packages
Hit http://ubuntu.excellmedia.net trusty-security/universe i386 Packages
Hit http://ubuntu.excellmedia.net trusty-security/multiverse i386 Packages
Hit http://ubuntu.excellmedia.net trusty-security/main TranslationIndex
Hit http://ubuntu.excellmedia.net trusty-security/multiverse TranslationIndex
Hit http://ubuntu.excellmedia.net trusty-security/restricted TranslationIndex
Hit http://ubuntu.excellmedia.net trusty-security/universe TranslationIndex
Hit http://ubuntu.excellmedia.net trusty/main Translation-en
Hit http://ubuntu.excellmedia.net trusty/multiverse Translation-en
Hit http://ubuntu.excellmedia.net trusty/restricted Translation-en
Hit http://ubuntu.excellmedia.net trusty/universe Translation-en
Hit http://ubuntu.excellmedia.net trusty-updates/main Translation-en
Hit http://ubuntu.excellmedia.net trusty-updates/multiverse Translation-en
Hit http://ubuntu.excellmedia.net trusty-updates/restricted Translation-en
Hit http://ubuntu.excellmedia.net trusty-updates/universe Translation-en
Hit http://ubuntu.excellmedia.net trusty-backports/main Translation-en
Hit http://ubuntu.excellmedia.net trusty-backports/multiverse Translation-en
Hit http://ubuntu.excellmedia.net trusty-backports/restricted Translation-en
Hit http://ubuntu.excellmedia.net trusty-backports/universe Translation-en
Ign http://www.openprinting.org lsb3.2/contrib Translation-en_US
Hit http://ubuntu.excellmedia.net trusty-security/main Translation-en
Hit http://ubuntu.excellmedia.net trusty-security/multiverse Translation-en
Hit http://ubuntu.excellmedia.net trusty-security/restricted Translation-en
Hit http://ubuntu.excellmedia.net trusty-security/universe Translation-en
Hit http://www.openprinting.org lsb3.2/contrib Translation-en
Reading package lists... Done
```


```
sudo apt-get upgrade
```
```
 apt-transport-https apt-xapian-index aptdaemon-data aspell aspell-en autoconf automake autotools-dev avahi-autoipd avahi-utils base-files  bash bash-completion bc binutils binutils-arm-linux-gnueabihf bison bless bluez-alsa bluez-alsa:i386 bluez-cups bluez-gstreamer
  branding-ubuntu bsdmainutils bsdutils build-essential busybox-initramfs busybox-static bzip2 ca-certificates ca-certificates-java cabextract
  chromium-codecs-ffmpeg cli-common command-not-found-data compiz-plugins-main-default compizconfig-backend-gconf console-setup consolekit
  coreutils cpio cron cups-common curl dash dbus-x11 dc dctrl-tools debconf debconf-i18n debianutils debootstrap desktop-file-utils dh-apparmor
  dictionaries-common diffstat diffutils dmidecode dmz-cursor-theme dnsmasq-base doc-base docbook-xml docbook-xsl dosfstools dpkg dput
  dvd+rw-tools e2fslibs e2fsprogs ed eject enchant esound-common espeak espeak-data example-content file findutils firefox-locale-en
  flashplugin-installer flex folks-common fontconfig fontconfig-config fonts-horai-umefont fonts-kacst fonts-kacst-one fonts-khmeros-core
  fonts-lao fonts-liberation fonts-nanum fonts-opensymbol fonts-takao-pgothic fonts-thai-tlwg fonts-tlwg-garuda fonts-tlwg-kinnari
  fonts-tlwg-loma fonts-tlwg-mono fonts-tlwg-norasi fonts-tlwg-purisa fonts-tlwg-sawasdee fonts-tlwg-typewriter fonts-tlwg-typist
  fonts-tlwg-typo fonts-tlwg-umpush fonts-tlwg-waree fonts-unfonts-core foomatic-db-engine foomatic-filters ftp fuse fuseiso gawk genisoimage
  geoip-database ghc gir1.2-appindicator3-0.1 gir1.2-atspi-2.0 gir1.2-gnomekeyring-1.0 gir1.2-gst-plugins-base-0.10 gir1.2-gstreamer-0.10
  gir1.2-gtk-2.0 gir1.2-gudev-1.0 gir1.2-notify-0.7 git git-core git-man gksu gnome-accessibility-themes gnome-exe-thumbnailer gnome-icon-theme
  gnome-icon-theme-symbolic gnome-media gnome-session-canberra gnome-user-guide gnupg gperf gpgv grep groff-base growisofs
  gsettings-desktop-schemas gstreamer0.10-alsa gstreamer0.10-gconf gstreamer0.10-nice gstreamer0.10-plugins-base-apps gstreamer0.10-tools
  gtk2-engines-murrine gtk2-engines-murrine:i386 guile-1.8-libs gutenprint-locales gzip hdparm heirloom-mailx hicolor-icon-theme hostname
  html2text humanity-icon-theme hunspell-en-ca hwdata hyphen-en-us icedtea-6-jre-cacao icedtea-6-jre-jamvm icedtea-netx icedtea-netx-common
  icoutils im-switch imagemagick-common info initscripts inputattach insserv install-info installation-report intel-gpu-tools iputils-arping
  iputils-tracepath iso-codes java-common kate-data kbd kernel-package kerneloops-daemon keyboard-configuration krb5-locales
  landscape-client-ui-install language-pack-en language-pack-en-base language-pack-gnome-en language-pack-gnome-en-base less lib32bz2-1.0
  lib32bz2-dev lib32ncurses5 lib32ncurses5-dev lib32readline-gplv2-dev lib32readline5 lib32readline6 lib32tinfo-dev lib32tinfo5 lib32z1
  lib32z1-dev liba52-0.7.4 libaa1 libaa1:i386 libaacs0 libacl1 libacl1:i386 libaio1:i386 libalgorithm-diff-perl libao-common libao4:i386
  libapr1 libapt-pkg4.12 libart-2.0-2 libasn1-8-heimdal libasn1-8-heimdal:i386 libasound2-plugins libasound2-plugins:i386 libaspell15 libass4
  libasyncns0 libasyncns0:i386 libatk-wrapper-java libatk1.0-doc libattr1 libattr1:i386 libaudio2 libaudio2:i386 libaudiofile-dev libaudiofile1
  libaudiofile1:i386 libavahi-client-dev libavahi-client3 libavahi-client3:i386 libavahi-common-data libavahi-common-data:i386
  libavahi-common-dev libavahi-common3 libavahi-common3:i386 libavahi-core7 libavahi-glib1 libavc1394-0 libavc1394-0:i386 libbison-dev
  libblkid1 libbluetooth3 libbluray1 libbonoboui2-common libbsd-dev libbsd0 libburn4 libbz2-1.0 libbz2-1.0:i386 libbz2-dev libc-bin
  libc-dev-bin libc6 libc6:i386 libc6-armhf-cross libc6-dbg libc6-dev libc6-dev:i386 libc6-dev-armhf-cross libc6-dev-i386 libc6-i386
  libcaca-dev libcaca0 libcaca0:i386 libcairo-gobject2 libcairo-gobject2:i386 libcairo-script-interpreter2 libcairo2 libcairo2:i386
  libcairo2-dev libcairomm-1.0-1 libcairomm-1.0-dev libcanberra-gtk-module libcanberra-gtk-module:i386 libcanberra-gtk0 libcanberra-gtk0:i386
  libcanberra-gtk3-0 libcanberra-gtk3-module libcanberra-pulse libcanberra0 libcanberra0:i386 libcap-ng0 libcap2 libcap2:i386 libcap2-bin
  libcapi20-3 libcapi20-3:i386 libcddb2 libcdio-cdda1 libcdio-paranoia1 libcdio13 libcdparanoia0 libcdparanoia0:i386 libck-connector0
  libclass-isa-perl libcomerr2 libcomerr2:i386 libcroco3 libcroco3:i386 libcrystalhd3 libctpl2 libcurl3 libcurl3:i386 libcwidget3 libdaemon0
  libdatrie1 libdatrie1:i386 libdb5.1 libdb5.1:i386 libdbus-1-3 libdbus-1-3:i386 libdbus-1-dev libdbus-glib-1-2 libdbus-glib-1-2:i386
  libdbusmenu-qt2 libdc1394-22 libdca0 libdirac-encoder0 libdirectfb-1.2-9 libdiscid0 libdjvulibre-text libdjvulibre21 libdlrestrictions1
  libdrm-dev libdrm-intel1 libdrm-intel1:i386 libdrm-nouveau2 libdrm-radeon1 libdrm-radeon1:i386 libdrm2 libdrm2:i386 libdv4 libdv4:i386
  libdvdnav4 libdvdread4 libedit2 libelf1 libemail-valid-perl libenca0 libencode-locale-perl libept1.4.12 liberror-perl libesd0 libesd0:i386
  libesd0-dev libespeak1 libevent-2.0-5 libexempi3 libexif12 libexif12:i386 libexpat1 libexpat1:i386 libexpat1-dev libfaad2 libffi-dev libffi6
  libffi6:i386 libfile-desktopentry-perl libfile-listing-perl libfile-mimeinfo-perl libfl-dev libflac8 libflac8:i386 libfontconfig1
  libfontconfig1:i386 libfontconfig1-dev libfontenc1 libframe6 libfreerdp-plugins-standard libfreerdp1 libfreetype6 libfreetype6:i386
  libfreetype6-dev libfribidi0 libfs6 libfuse2 libgcr-3-common libgcrypt11 libgcrypt11:i386 libgda-5.0-common libgdata-common libgdbm-dev
  libgdbm3 libgdbm3:i386 libgee2 libgeoip1 libghc-bzlib-dev libgif4 libgif4:i386 libglade2.0-cil libglib2.0-data libglib2.0-doc libglu1-mesa
  libglu1-mesa:i386 libglu1-mesa-dev libgmime-2.6-0 libgmp-dev libgmp10 libgmpxx4ldbl libgnome-keyring-common libgnome-keyring0
  libgnome-keyring0:i386 libgnome-menu2 libgnome2-bin libgnome2-common libgnomecanvas2-common libgnomekbd-common libgnomeui-common
  libgnomevfs2-common libgpg-error0 libgpg-error0:i386 libgphoto2-l10n libgpm2 libgpm2:i386 libgsm1 libgssapi-krb5-2 libgssapi-krb5-2:i386
  libgssapi3-heimdal libgssapi3-heimdal:i386 libgtk-3-doc libgtk2.0-common libgtksourceview2.0-common libgtkspell0 libgtop2-7 libgtop2-common
  libgutenprint2 libgweather-common libhcrypto4-heimdal libhcrypto4-heimdal:i386 libheimbase1-heimdal libheimbase1-heimdal:i386
  libheimntlm0-heimdal libheimntlm0-heimdal:i386 libhtml-form-perl libhtml-format-perl libhtml-tree-perl libhttp-daemon-perl libhttp-date-perl
  libhunspell-1.3-0 libhx509-5-heimdal libhx509-5-heimdal:i386 libhyphen0 libice-dev libice6 libice6:i386 libid3tag0 libidl-common libidl0
  libidn11 libidn11:i386 libiec61883-0 libiec61883-0:i386 libieee1284-3 libieee1284-3:i386 libijs-0.35 libilmbase6 libindicate-gtk3
  libio-socket-inet6-perl libio-string-perl libipc-run-perl libiso9660-8 libisofs6 libiw30 libjack-jackd2-0 libjack-jackd2-0:i386 libjasper1
  libjasper1:i386 libjbig2dec0 libjpeg-turbo8 libjpeg-turbo8:i386 libjpeg62 libjpeg8 libjpeg8:i386 libjs-jquery libjte1 libk5crypto3
  libk5crypto3:i386 libkate1 libkeyutils1 libkeyutils1:i386 libkrb5-26-heimdal libkrb5-26-heimdal:i386 libkrb5-3 libkrb5-3:i386 libkrb5support0
  libkrb5support0:i386 liblcms1 liblcms1:i386 liblcms2-2 liblircclient0 liblockfile-bin liblockfile1 liblouis-data liblouis2 liblqr-1-0
  libltdl-dev libltdl7 libltdl7:i386 liblua5.1-0 liblwp-mediatypes-perl liblzma5 liblzo2-2 libmad0 libmad0:i386 libmagic1 libmeanwhile1
  libmhash2 libmikmod2:i386 libminiupnpc8 libmodplug1 libmount1 libmp3lame0 libmpcdec6 libmpeg2-4 libmpfr4 libmpg123-0 libmpg123-0:i386
  libmtdev1 libmtp-common libmtp-runtime libmtp9 libmysqlclient18:i386 libmythes-1.2-0 libncurses5 libncurses5:i386 libncurses5-dev
  libncursesw5 libncursesw5:i386 libncursesw5-dev libnet-domain-tld-perl libnet-http-perl libnet-ip-perl libnettle4 libnewt0.52 libnfnetlink0
  libnice10 libnih-dbus1 libnih1 libnl-3-200 libnl-genl-3-200 libnl-route-3-200 libnm-glib-vpn1 libnm-gtk-common libnotify-bin libnspr4
  libnspr4:i386 libnspr4-0d libnss-mdns libntrack-qt4-1 libntrack0 liboauth0 libodbc1 libodbc1:i386 libogg0 libogg0:i386 liboil0.3
  libopenal-data libopenal1 libopenal1:i386 libopencc1 libopencore-amrnb0 libopencore-amrwb0 libopenexr6 libopenobex1 liborc-0.4-0
  liborc-0.4-0:i386 libp11-kit0 libp11-kit0:i386 libpam-cap libpam-ck-connector libpam-gnome-keyring libpam-runtime libpango1.0-doc
  libpaper-utils libpaper1 libparse-debcontrol-perl libparted0debian1 libpathplan4 libpcap0.8 libpci3 libpciaccess0 libpciaccess0:i386 libpcre3
  libpcre3:i386 libpcre3-dev libpcrecpp0 libpcsclite1 libpeas-common libphonon4 libpipeline1 libpixman-1-0 libpixman-1-0:i386 libpixman-1-dev
  libplist1 libpng12-0 libpng12-0:i386 libpng12-dev libpolkit-qt-1-1 libpopt0 libportaudio2 libpostproc52 libpq5 libproxy1 libproxy1:i386
  libproxy1-plugin-gsettings libproxy1-plugin-networkmanager libpth20 libpthread-stubs0-dev libpthread-stubs0-dev:i386 libpulsedsp
  libpulsedsp:i386 libpurple-bin libqca2 libquvi-scripts librarian0 libraw1394-11 libraw1394-11:i386 libreadline-dev libreadline6
  libreadline6:i386 libreadline6-dev libreadline6-dev:i386 libreoffice-style-human libresid-builder0c2a librest-0.7-0 libroken18-heimdal
  libroken18-heimdal:i386 librsync1 libsamplerate0 libsamplerate0:i386 libsasl2-modules libsasl2-modules:i386 libschroedinger-1.0-0
  libsdl-net1.2:i386 libsdl-ttf2.0-0:i386 libsdl1.2-dev libsdl1.2debian libsdl1.2debian:i386 libselinux1 libselinux1:i386 libsensors4
  libsgutils2-2 libshout3 libshout3:i386 libsidplay1 libsidplay2 libsigc++-2.0-0c2a libsigc++-2.0-dev libsigsegv2 libslang2 libslang2:i386
  libslang2-dev libslp1 libsm-dev libsm6 libsm6:i386 libsndfile1 libsndfile1:i386 libsonic0 libspectre1 libspeechd2 libspeex1 libspeex1:i386
  libspeexdsp1 libspeexdsp1:i386 libsqlite3-0 libsqlite3-0:i386 libsqlite3-dev libss2 libssh-4 libssl-dev libssl-doc libssl0.9.8:i386
  libssl1.0.0 libssl1.0.0:i386 libstartup-notification0 libstdc++5:i386 libsys-hostname-long-perl libsysfs2 libt1-5 libtag1-vanilla
  libtag1-vanilla:i386 libtag1c2a libtag1c2a:i386 libtalloc2 libtar0 libtdb1 libtdb1:i386 libtelepathy-glib0 libthai-data libthai0
  libthai0:i386 libtheora0 libtheora0:i386 libtie-ixhash-perl libtimedate-perl libtinfo-dev libtinfo-dev:i386 libtinfo5 libtinfo5:i386 libtool
  libts-0.0-0 libtwolame0 libunistring0 libunistring0:i386 libunity-2d-private0 liburi-perl libusb-0.1-4 libusb-0.1-4:i386 libutempter0
  libuuid1 libuuid1:i386 libv4l-0 libv4l-0:i386 libv4lconvert0 libv4lconvert0:i386 libva-x11-1 libva1 libvala-0.16-0 libvcdinfo0 libvirtodbc0
  libvisual-0.4-0 libvisual-0.4-0:i386 libvisual-0.4-plugins libvisual-0.4-plugins:i386 libvorbis0a libvorbis0a:i386 libvorbisenc2
  libvorbisenc2:i386 libvorbisfile3 libvorbisfile3:i386 libvpx1 libvte-common libvte9 libwacom-common libwacom2 libwavpack1 libwavpack1:i386
  libwebkitgtk-1.0-common libwebkitgtk-3.0-common libwind0-heimdal libwind0-heimdal:i386 libwmf0.2-7 libwmf0.2-7-gtk libwnck-3-common
  libwnck-common libwpd-0.9-9 libwpg-0.2-2 libwps-0.2-2 libwrap0 libwrap0:i386 libwww-perl libx11-6 libx11-6:i386 libx11-data libx11-dev
  libx11-dev:i386 libx11-doc libx11-xcb1 libx11-xcb1:i386 libx86-1 libxapian22 libxau-dev libxau-dev:i386 libxau6 libxau6:i386 libxaw7
  libxaw7:i386 libxcb-composite0 libxcb-dri2-0 libxcb-glx0 libxcb-glx0:i386 libxcb-keysyms1 libxcb-randr0 libxcb-render0 libxcb-render0:i386
  libxcb-render0-dev libxcb-shape0 libxcb-shm0 libxcb-shm0:i386 libxcb-shm0-dev libxcb-util0 libxcb-xv0 libxcb1 libxcb1:i386 libxcb1-dev
  libxcb1-dev:i386 libxcomposite-dev libxcomposite1 libxcomposite1:i386 libxcursor-dev libxcursor1 libxcursor1:i386 libxdamage-dev libxdamage1
  libxdamage1:i386 libxdmcp-dev libxdmcp-dev:i386 libxdmcp6 libxdmcp6:i386 libxext-dev libxext6 libxext6:i386 libxfont1 libxft-dev libxft2
  libxft2:i386 libxinerama-dev libxinerama1 libxinerama1:i386 libxkbfile1 libxmu6 libxmu6:i386 libxmuu1 libxp6 libxp6:i386 libxpm4 libxpm4:i386
  libxrandr-dev libxrandr2 libxrandr2:i386 libxrender-dev libxrender1 libxrender1:i386 libxres1 libxss-dev libxss1 libxss1:i386 libxt-dev
  libxt6 libxt6:i386 libxtst6 libxtst6:i386 libxv1 libxv1:i386 libxvmc1 libxxf86dga1 libxxf86vm1 libxxf86vm1:i386 libyaml-tiny-perl libzephyr4
  libzvbi-common libzvbi0 light-themes linux-firmware linux-libc-dev linux-libc-dev:i386 linux-libc-dev-armhf-cross linux-sound-base locales
  lockfile-progs login logrotate lsb-base lsb-invalid-mta lshw lsof ltrace m4 make makedev man-db manpages manpages-dev mawk media-player-info
  meld memtest86+ metacity-common mime-support mingw32-binutils mlocate mobile-broadband-provider-info mount mscompress mtools mtr-tiny
  multiarch-support myspell-en-au myspell-en-gb myspell-en-za mysql-common mythes-en-au mythes-en-us nano ncurses-base ncurses-bin ncurses-term
  net-tools netcat-openbsd notify-osd-icons ntpdate ntrack-module-libnl-0 nux-tools obex-data-server obexd-client odbcinst odbcinst1debian2
  odbcinst1debian2:i386 openjdk-6-jdk openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib openoffice.org-hyphenation openssl os-prober
  oxygen-icon-theme parted patch patchutils pax pbuilder pciutils pcmciautils phonon pkg-config plymouth-theme-ubuntu-logo
  plymouth-theme-ubuntu-text pngcrush policykit-1-gnome popularity-contest powermgmt-base ppp pppconfig pptp-linux printer-driver-min12xxw
  printer-driver-pnm2ppa psmisc pulseaudio-module-gconf pulseaudio-module-x11 python-apport python-apt-common python-cairo python-chardet
  python-cheetah python-configglue python-configobj python-cupshelpers python-dateutil python-dbus python-dbus-dev python-debtagshw
  python-defer python-dirspec python-egenix-mxdatetime python-egenix-mxtools python-flup python-gdbm python-gnomekeyring python-gobject-2
  python-httplib2 python-ipy python-launchpadlib python-lazr.restfulclient python-lazr.uri python-libproxy python-lockfile python-louis
  python-magic python-mako python-markupsafe python-notify python-oauth python-openssl python-pam python-pexpect python-pkg-resources
  python-problem-report python-psycopg2 python-pyinotify python-renderpm python-reportlab-accel python-serial python-software-properties
  python-support python-twisted-bin python-twisted-core python-twisted-names python-twisted-web python-virtkey python-wadllib python-webkit
  python-webpy python-xapian python-xdg python-xkit python-zeitgeist python-zope.interface q4wine qt-at-spi radeontool rar:i386 rarian-compat
  readline-common rebuildd resolvconf rfkill rsync rtkit sane-utils sed sensible-utils sgml-base sgml-data shared-desktop-ontologies sharutils
  simple-scan sni-qt sound-theme-freedesktop squashfs-tools ssh-askpass-gnome ssl-cert strace sudo syslinux syslinux-common
  system-config-printer-common sysv-rc sysvinit-utils tar tasksel tasksel-data tcpd tcpdump telepathy-idle telnet thunderbird-globalmenu
  thunderbird-locale-en-gb thunderbird-locale-en-us time tofrodos toshset tsconf ttf-indic-fonts-core ttf-liberation ttf-mscorefonts-installer
  ttf-punjabi-fonts ttf-ubuntu-font-family ttf-unfonts-core tzdata tzdata-java ubuntu-artwork ubuntu-docs ubuntu-keyring ubuntu-mono
  ubuntu-standard ubuntu-wallpapers-precise ucf unity-2d unity-2d-common unity-2d-panel unity-2d-shell unity-2d-spread unity-asset-pool
  unixodbc unrar unzip update-inetd ureadahead usb-modeswitch usb-modeswitch-data util-linux uuid-runtime valac-0.16 valac-0.16-vapi valgrind
  vbetool vim-common vim-tiny virtuoso-minimal virtuoso-opensource-6.1-bin virtuoso-opensource-6.1-common wdiff wget whiptail whois
  wireless-tools wodim x11-apps x11-common x11-session-utils x11-utils x11-xfs-utils x11-xkb-utils x11-xserver-utils x11proto-core-dev
  x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-scrnsaver-dev x11proto-xext-dev xauth xaw3dg:i386 xbitmaps
  xcftools xclip xdg-user-dirs xdg-utils xfonts-mathml xfonts-utils xinit xinput xkb-data xml-core xorg xorg-docs-core xorg-sgml-doctools
  xserver-common xserver-xorg xterm xtrans-dev xul-ext-ubufox yelp-xsl zeitgeist zip zlib1g zlib1g:i386 zlib1g-dev zlib1g-dev:i386
1137 upgraded, 0 newly installed, 0 to remove and 900 not upgraded.
Need to get 391 MB/405 MB of archives.
After this operation, 106 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ubuntu.excellmedia.net/archive/ trusty/main base-files amd64 7.2ubuntu5 [67.2 kB]
Err http://ubuntu.excellmedia.net/archive/ trusty/main sensible-utils all 0.0.9
  403  Forbidden
Get:2 http://ubuntu.excellmedia.net/archive/ trusty/main debianutils amd64 4.4 [88.7 kB]
Get:3 http://ubuntu.excellmedia.net/archive/ trusty-updates/main bash amd64 4.3-7ubuntu1 [575 kB]
Err http://ubuntu.excellmedia.net/archive/ trusty/main libcap2 i386 1:2.24-0ubuntu2
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libcap2 amd64 1:2.24-0ubuntu2
  403  Forbidden
Get:4 http://ubuntu.excellmedia.net/archive/ trusty/main libc6-i386 amd64 2.19-0ubuntu6 [2,204 kB]
Get:5 http://ubuntu.excellmedia.net/archive/ trusty/main libc6-dev-i386 amd64 2.19-0ubuntu6 [1,149 kB]                                          
Get:6 http://ubuntu.excellmedia.net/archive/ trusty/main libc6-dev i386 2.19-0ubuntu6 [1,555 kB]                                                
Get:7 http://ubuntu.excellmedia.net/archive/ trusty/main libc6-dev amd64 2.19-0ubuntu6 [1,911 kB]                                               
Get:8 http://ubuntu.excellmedia.net/archive/ trusty/main libc-dev-bin amd64 2.19-0ubuntu6 [69.0 kB]                                             
Get:9 http://ubuntu.excellmedia.net/archive/ trusty/main libc6 amd64 2.19-0ubuntu6 [4,729 kB]                                                   
Get:10 http://ubuntu.excellmedia.net/archive/ trusty/main libc6 i386 2.19-0ubuntu6 [4,017 kB]                                                   
Err http://ubuntu.excellmedia.net/archive/ trusty/main libnih-dbus1 amd64 1.0.3-4ubuntu25                                                       
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libnih1 amd64 1.0.3-4ubuntu25                                                            
  403  Forbidden
Get:11 http://ubuntu.excellmedia.net/archive/ trusty/main libc6-dbg amd64 2.19-0ubuntu6 [3,456 kB]                                              
Get:12 http://ubuntu.excellmedia.net/archive/ trusty/main libc-bin amd64 2.19-0ubuntu6 [1,168 kB]                                               
Err http://ubuntu.excellmedia.net/archive/ trusty/main libpopt0 amd64 1.16-8ubuntu1                                                             
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main pkg-config amd64 0.26-1ubuntu4                                                           
  403  Forbidden
Get:13 http://ubuntu.excellmedia.net/archive/ trusty/main libattr1 i386 1:2.4.47-1ubuntu1 [9,414 B]                                             
Get:14 http://ubuntu.excellmedia.net/archive/ trusty/main libattr1 amd64 1:2.4.47-1ubuntu1 [9,590 B]                                            
Get:15 http://ubuntu.excellmedia.net/archive/ trusty/main libacl1 i386 2.2.52-1 [18.1 kB]                                                       
Get:16 http://ubuntu.excellmedia.net/archive/ trusty/main libacl1 amd64 2.2.52-1 [18.1 kB]                                                      
Get:17 http://ubuntu.excellmedia.net/archive/ trusty/main coreutils amd64 8.21-1ubuntu5 [1,091 kB]                                              
Err http://ubuntu.excellmedia.net/archive/ trusty/main liblzma5 amd64 5.1.1alpha+20120614-2ubuntu2                                              
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libpcre3-dev amd64 1:8.31-2ubuntu2                                                       
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libpcrecpp0 amd64 1:8.31-2ubuntu2                                                        
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libpcre3 amd64 1:8.31-2ubuntu2                                                           
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libpcre3 i386 1:8.31-2ubuntu2                                                            
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty-updates/main libselinux1 i386 2.2.2-1ubuntu0.1                                                
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty-updates/main libselinux1 amd64 2.2.2-1ubuntu0.1                                               
  403  Forbidden
Get:18 http://ubuntu.excellmedia.net/archive/ trusty/main debconf all 1.5.51ubuntu2 [136 kB]                                                    
Get:19 http://ubuntu.excellmedia.net/archive/ trusty/main adduser all 3.113+nmu3ubuntu3 [169 kB]                                                
Err http://ubuntu.excellmedia.net/archive/ trusty/main lsb-base all 4.1+Debian11ubuntu6                                                         
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libpam-runtime all 1.1.8-1ubuntu2                                                        
  403  Forbidden
Get:20 http://ubuntu.excellmedia.net/archive/ trusty/main cron amd64 3.0pl1-124ubuntu2 [81.7 kB]                                                
Get:21 http://ubuntu.excellmedia.net/archive/ trusty/main dash amd64 0.5.7-4ubuntu1 [85.1 kB]                                                   
Get:22 http://ubuntu.excellmedia.net/archive/ trusty/main diffutils amd64 1:3.3-1 [206 kB]                                                      
Get:23 http://ubuntu.excellmedia.net/archive/ trusty/main e2fslibs amd64 1.42.9-3ubuntu1 [183 kB]                                               
Get:24 http://ubuntu.excellmedia.net/archive/ trusty/main e2fsprogs amd64 1.42.9-3ubuntu1 [666 kB]                                              
Get:25 http://ubuntu.excellmedia.net/archive/ trusty/main findutils amd64 4.4.2-7 [272 kB]                                                      
Err http://ubuntu.excellmedia.net/archive/ trusty/main install-info amd64 5.2.0.dfsg.1-2                                                        
  403  Forbidden
Get:26 http://ubuntu.excellmedia.net/archive/ trusty/main grep amd64 2.16-1 [163 kB]                                                            
Get:27 http://ubuntu.excellmedia.net/archive/ trusty/main gzip amd64 1.6-3ubuntu1 [86.8 kB]                                                     
Get:28 http://ubuntu.excellmedia.net/archive/ trusty/main insserv amd64 1.14.0-5ubuntu2 [43.3 kB]                                               
Err http://ubuntu.excellmedia.net/archive/ trusty/main sysv-rc all 2.88dsf-41ubuntu6                                                            
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main sysvinit-utils amd64 2.88dsf-41ubuntu6                                                   
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty-updates/main mount amd64 2.20.1-5.1ubuntu20.1                                                 
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main initscripts amd64 2.88dsf-41ubuntu6                                                      
  403  Forbidden
Get:29 http://ubuntu.excellmedia.net/archive/ trusty/main hostname amd64 3.15ubuntu1 [11.3 kB]                                                  
Err http://ubuntu.excellmedia.net/archive/ trusty/main login amd64 1:4.1.5.1-1ubuntu9                                                           
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libncursesw5-dev amd64 5.9+20140118-1ubuntu1                                             
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libncursesw5 i386 5.9+20140118-1ubuntu1                                                  
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libncursesw5 amd64 5.9+20140118-1ubuntu1                                                 
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libtinfo5 i386 5.9+20140118-1ubuntu1                                                     
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libtinfo5 amd64 5.9+20140118-1ubuntu1                                                    
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main ncurses-bin amd64 5.9+20140118-1ubuntu1                                                  
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main lib32tinfo-dev amd64 5.9+20140118-1ubuntu1                                               
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main lib32ncurses5 amd64 5.9+20140118-1ubuntu1                                                
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main lib32tinfo5 amd64 5.9+20140118-1ubuntu1                                                  
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main lib32ncurses5-dev amd64 5.9+20140118-1ubuntu1                                            
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libncurses5-dev amd64 5.9+20140118-1ubuntu1                                              
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libtinfo-dev i386 5.9+20140118-1ubuntu1                                                  
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libtinfo-dev amd64 5.9+20140118-1ubuntu1                                                 
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libncurses5 i386 5.9+20140118-1ubuntu1                                                   
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libncurses5 amd64 5.9+20140118-1ubuntu1                                                  
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main sed amd64 4.2.2-4ubuntu1                                                                 
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main tar amd64 1.27.1-1                                                                       
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main xkb-data all 2.10.1-1ubuntu1                                                             
  403  Forbidden
Get:30 http://ubuntu.excellmedia.net/archive/ trusty/main keyboard-configuration all 1.70ubuntu8 [556 kB]                                       
Get:31 http://ubuntu.excellmedia.net/archive/ trusty/main console-setup all 1.70ubuntu8 [1,113 kB]                                              
Get:32 http://ubuntu.excellmedia.net/archive/ trusty/main kbd amd64 1.15.5-1ubuntu1 [254 kB]                                                    
Err http://ubuntu.excellmedia.net/archive/ trusty-updates/main util-linux amd64 2.20.1-5.1ubuntu20.1                                            
  403  Forbidden
Get:33 http://ubuntu.excellmedia.net/archive/ trusty/main bsdmainutils amd64 9.0.5ubuntu1 [203 kB]                                              
Err http://ubuntu.excellmedia.net/archive/ trusty-updates/main bsdutils amd64 1:2.20.1-5.1ubuntu20.1                                            
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main ncurses-base all 5.9+20140118-1ubuntu1                                                   
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main ubuntu-keyring all 2012.05.19                                                            
  403  Forbidden
Get:34 http://ubuntu.excellmedia.net/archive/ trusty/main lib32bz2-1.0 amd64 1.0.6-5 [33.2 kB]                                                  
Get:35 http://ubuntu.excellmedia.net/archive/ trusty/main lib32bz2-dev amd64 1.0.6-5 [29.9 kB]                                                  
Get:36 http://ubuntu.excellmedia.net/archive/ trusty/main libbz2-dev amd64 1.0.6-5 [33.2 kB]                                                    
Get:37 http://ubuntu.excellmedia.net/archive/ trusty/main bzip2 amd64 1.0.6-5 [38.8 kB]                                                         
Get:38 http://ubuntu.excellmedia.net/archive/ trusty/main libbz2-1.0 i386 1.0.6-5 [33.9 kB]                                                     
Get:39 http://ubuntu.excellmedia.net/archive/ trusty/main libbz2-1.0 amd64 1.0.6-5 [33.9 kB]                                                    
Err http://ubuntu.excellmedia.net/archive/ trusty/main libreadline-dev amd64 6.3-4ubuntu2                                                       
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libreadline6-dev amd64 6.3-4ubuntu2                                                      
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libreadline6-dev i386 6.3-4ubuntu2                                                       
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main readline-common all 6.3-4ubuntu2                                                         
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libreadline6 i386 6.3-4ubuntu2                                                           
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libreadline6 amd64 6.3-4ubuntu2                                                          
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libusb-0.1-4 i386 2:0.1.12-23.3ubuntu1                                                   
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libusb-0.1-4 amd64 2:0.1.12-23.3ubuntu1                                                  
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main lib32z1-dev amd64 1:1.2.8.dfsg-1ubuntu1                                                  
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main lib32z1 amd64 1:1.2.8.dfsg-1ubuntu1                                                      
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main zlib1g-dev amd64 1:1.2.8.dfsg-1ubuntu1                                                   
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main zlib1g-dev i386 1:1.2.8.dfsg-1ubuntu1                                                    
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main zlib1g i386 1:1.2.8.dfsg-1ubuntu1                                                        
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main zlib1g amd64 1:1.2.8.dfsg-1ubuntu1                                                       
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty-updates/main libuuid1 i386 2.20.1-5.1ubuntu20.1                                               
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty-updates/main libuuid1 amd64 2.20.1-5.1ubuntu20.1                                              
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty-updates/main libblkid1 amd64 2.20.1-5.1ubuntu20.1                                             
  403  Forbidden
Get:40 http://ubuntu.excellmedia.net/archive/ trusty/main libcomerr2 i386 1.42.9-3ubuntu1 [62.6 kB]                                             
Get:41 http://ubuntu.excellmedia.net/archive/ trusty/main libcomerr2 amd64 1.42.9-3ubuntu1 [62.6 kB]                                            
Err http://ubuntu.excellmedia.net/archive/ trusty-updates/main libmount1 amd64 2.20.1-5.1ubuntu20.1                                             
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libslang2-dev amd64 2.2.4-15ubuntu1                                                      
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libslang2 i386 2.2.4-15ubuntu1                                                           
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libslang2 amd64 2.2.4-15ubuntu1                                                          
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libpng12-dev amd64 1.2.50-1ubuntu2                                                       
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libpng12-0 i386 1.2.50-1ubuntu2                                                          
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libpng12-0 amd64 1.2.50-1ubuntu2                                                         
  403  Forbidden
Get:42 http://ubuntu.excellmedia.net/archive/ trusty/main libss2 amd64 1.42.9-3ubuntu1 [66.9 kB]                                                
Err http://ubuntu.excellmedia.net/archive/ trusty/universe libdb5.1 i386 5.1.29-7ubuntu1                                                        
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/universe libdb5.1 amd64 5.1.29-7ubuntu1                                                       
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libbsd-dev amd64 0.6.0-2ubuntu1                                                          
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libbsd0 amd64 0.6.0-2ubuntu1                                                             
  403  Forbidden
Get:43 http://ubuntu.excellmedia.net/archive/ trusty/main libexpat1-dev amd64 2.1.0-4ubuntu1 [115 kB]                                           
Get:44 http://ubuntu.excellmedia.net/archive/ trusty/main libexpat1 i386 2.1.0-4ubuntu1 [71.4 kB]                                               
Get:45 http://ubuntu.excellmedia.net/archive/ trusty/main libexpat1 amd64 2.1.0-4ubuntu1 [71.1 kB]                                              
Err http://ubuntu.excellmedia.net/archive/ trusty/main libffi-dev amd64 3.1~rc1+r3.0.13-12                                                      
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libffi6 i386 3.1~rc1+r3.0.13-12                                                          
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libffi6 amd64 3.1~rc1+r3.0.13-12                                                         
  403  Forbidden
Get:46 http://ubuntu.excellmedia.net/archive/ trusty/main libfribidi0 amd64 0.19.6-1 [25.6 kB]                                                  
Err http://ubuntu.excellmedia.net/archive/ trusty/main libgpg-error0 amd64 1.12-0.2ubuntu1                                                      
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libgpg-error0 i386 1.12-0.2ubuntu1                                                       
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libgcrypt11 i386 1.5.3-2ubuntu4                                                          
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libgcrypt11 amd64 1.5.3-2ubuntu4                                                         
  403  Forbidden
Get:47 http://ubuntu.excellmedia.net/archive/ trusty/main libgdbm-dev amd64 1.8.3-12build1 [24.9 kB]                                            
Get:48 http://ubuntu.excellmedia.net/archive/ trusty/main libgdbm3 i386 1.8.3-12build1 [33.3 kB]                                                
Get:49 http://ubuntu.excellmedia.net/archive/ trusty/main libgdbm3 amd64 1.8.3-12build1 [33.5 kB]                                               
Err http://ubuntu.excellmedia.net/archive/ trusty/main liblockfile-bin amd64 1.09-6ubuntu1                                                      
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main liblockfile1 amd64 1.09-6ubuntu1                                                         
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/universe python-magic all 1:5.14-2ubuntu3                                                     
  403  Forbidden
Get:50 http://ubuntu.excellmedia.net/archive/ trusty/main file amd64 1:5.14-2ubuntu3 [18.8 kB]                                                  
Get:51 http://ubuntu.excellmedia.net/archive/ trusty/main libmagic1 amd64 1:5.14-2ubuntu3 [183 kB]                                              
Err http://ubuntu.excellmedia.net/archive/ trusty/main libnewt0.52 amd64 0.52.15-2ubuntu5                                                       
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libp11-kit0 i386 0.20.2-2ubuntu2                                                         
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libp11-kit0 amd64 0.20.2-2ubuntu2                                                        
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libsqlite3-dev amd64 3.8.2-1ubuntu2                                                      
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libsqlite3-0 i386 3.8.2-1ubuntu2                                                         
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libsqlite3-0 amd64 3.8.2-1ubuntu2                                                        
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main ntpdate amd64 1:4.2.6.p5+dfsg-3ubuntu2                                                   
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty-updates/main resolvconf all 1.69ubuntu1.1                                                     
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libdrm-dev amd64 2.4.52-1                                                                
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libdrm2 i386 2.4.52-1                                                                    
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libdrm2 amd64 2.4.52-1                                                                   
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libpciaccess0 amd64 0.13.2-1                                                             
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libpciaccess0 i386 0.13.2-1                                                              
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libdrm-intel1 i386 2.4.52-1                                                              
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libdrm-intel1 amd64 2.4.52-1                                                             
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libdrm-radeon1 i386 2.4.52-1                                                             
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libdrm-radeon1 amd64 2.4.52-1                                                            
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libdrm-nouveau2 amd64 2.4.52-1                                                           
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main mawk amd64 1.3.3-17ubuntu2                                                               
  403  Forbidden
Get:52 http://ubuntu.excellmedia.net/archive/ trusty/main bash-completion all 1:2.1-4 [154 kB]                                                  
Get:53 http://ubuntu.excellmedia.net/archive/ trusty/main libroken18-heimdal amd64 1.6~git20131207+dfsg-1ubuntu1 [40.0 kB]                      
Get:54 http://ubuntu.excellmedia.net/archive/ trusty/main libroken18-heimdal i386 1.6~git20131207+dfsg-1ubuntu1 [40.9 kB]                       
Get:55 http://ubuntu.excellmedia.net/archive/ trusty/main libasn1-8-heimdal i386 1.6~git20131207+dfsg-1ubuntu1 [169 kB]                         
Get:56 http://ubuntu.excellmedia.net/archive/ trusty/main libasn1-8-heimdal amd64 1.6~git20131207+dfsg-1ubuntu1 [160 kB]                        
Err http://ubuntu.excellmedia.net/archive/ trusty/main libcap-ng0 amd64 0.7.3-1ubuntu2                                                          
  403  Forbidden
Get:57 http://ubuntu.excellmedia.net/archive/ trusty/main libdbus-glib-1-2 i386 0.100.2-1 [74.2 kB]                                             
Get:58 http://ubuntu.excellmedia.net/archive/ trusty/main libdbus-glib-1-2 amd64 0.100.2-1 [74.1 kB]                                            
Err http://ubuntu.excellmedia.net/archive/ trusty/main libedit2 amd64 3.1-20130712-2                                                            
  403  Forbidden
Get:59 http://ubuntu.excellmedia.net/archive/ trusty-updates/main libelf1 amd64 0.158-0ubuntu5.1 [38.3 kB]                                      
Err http://ubuntu.excellmedia.net/archive/ trusty/main makedev all 2.3.1-93ubuntu1                                                              
  403  Forbidden
Get:60 http://ubuntu.excellmedia.net/archive/ trusty/main fuse amd64 2.9.2-4ubuntu4 [25.1 kB]                                                   
Get:61 http://ubuntu.excellmedia.net/archive/ trusty/main libfuse2 amd64 2.9.2-4ubuntu4 [87.2 kB]                                               
Get:62 http://ubuntu.excellmedia.net/archive/ trusty/main geoip-database all 20140313-1 [1,196 kB]                                              
Get:63 http://ubuntu.excellmedia.net/archive/ trusty/main libgeoip1 amd64 1.6.0-1 [71.0 kB]                                                     
Get:64 http://ubuntu.excellmedia.net/archive/ trusty/main libkeyutils1 i386 1.5.6-1 [7,266 B]                                                   
Get:65 http://ubuntu.excellmedia.net/archive/ trusty/main libkeyutils1 amd64 1.5.6-1 [7,318 B]                                                  
Get:66 http://ubuntu.excellmedia.net/archive/ trusty/main libk5crypto3 i386 1.12+dfsg-2ubuntu4 [77.6 kB]                                        
Get:67 http://ubuntu.excellmedia.net/archive/ trusty/main libk5crypto3 amd64 1.12+dfsg-2ubuntu4 [79.5 kB]                                       
Get:68 http://ubuntu.excellmedia.net/archive/ trusty/main libgssapi-krb5-2 i386 1.12+dfsg-2ubuntu4 [111 kB]                                     
Get:69 http://ubuntu.excellmedia.net/archive/ trusty/main libgssapi-krb5-2 amd64 1.12+dfsg-2ubuntu4 [113 kB]                                    
Get:70 http://ubuntu.excellmedia.net/archive/ trusty/main libkrb5-3 amd64 1.12+dfsg-2ubuntu4 [262 kB]                                           
Get:71 http://ubuntu.excellmedia.net/archive/ trusty/main libkrb5-3 i386 1.12+dfsg-2ubuntu4 [260 kB]                                            
Get:72 http://ubuntu.excellmedia.net/archive/ trusty/main libkrb5support0 i386 1.12+dfsg-2ubuntu4 [29.8 kB]                                     
Get:73 http://ubuntu.excellmedia.net/archive/ trusty/main libkrb5support0 amd64 1.12+dfsg-2ubuntu4 [29.5 kB]                                    
Get:74 http://ubuntu.excellmedia.net/archive/ trusty/main libhcrypto4-heimdal amd64 1.6~git20131207+dfsg-1ubuntu1 [84.0 kB]                     
Get:75 http://ubuntu.excellmedia.net/archive/ trusty/main libhcrypto4-heimdal i386 1.6~git20131207+dfsg-1ubuntu1 [82.3 kB]                      
Get:76 http://ubuntu.excellmedia.net/archive/ trusty/main libheimbase1-heimdal amd64 1.6~git20131207+dfsg-1ubuntu1 [29.0 kB]                    
Get:77 http://ubuntu.excellmedia.net/archive/ trusty/main libheimbase1-heimdal i386 1.6~git20131207+dfsg-1ubuntu1 [28.9 kB]                     
Get:78 http://ubuntu.excellmedia.net/archive/ trusty/main libwind0-heimdal i386 1.6~git20131207+dfsg-1ubuntu1 [48.2 kB]                         
Get:79 http://ubuntu.excellmedia.net/archive/ trusty/main libwind0-heimdal amd64 1.6~git20131207+dfsg-1ubuntu1 [47.8 kB]                        
Get:80 http://ubuntu.excellmedia.net/archive/ trusty/main libhx509-5-heimdal amd64 1.6~git20131207+dfsg-1ubuntu1 [104 kB]                       
Get:81 http://ubuntu.excellmedia.net/archive/ trusty/main libhx509-5-heimdal i386 1.6~git20131207+dfsg-1ubuntu1 [103 kB]                        
Get:82 http://ubuntu.excellmedia.net/archive/ trusty/main libkrb5-26-heimdal i386 1.6~git20131207+dfsg-1ubuntu1 [198 kB]                        
Get:83 http://ubuntu.excellmedia.net/archive/ trusty/main libkrb5-26-heimdal amd64 1.6~git20131207+dfsg-1ubuntu1 [197 kB]                       
Get:84 http://ubuntu.excellmedia.net/archive/ trusty/main libheimntlm0-heimdal amd64 1.6~git20131207+dfsg-1ubuntu1 [15.2 kB]                    
Get:85 http://ubuntu.excellmedia.net/archive/ trusty/main libheimntlm0-heimdal i386 1.6~git20131207+dfsg-1ubuntu1 [15.5 kB]                     
Get:86 http://ubuntu.excellmedia.net/archive/ trusty/main libgssapi3-heimdal i386 1.6~git20131207+dfsg-1ubuntu1 [89.5 kB]                       
Get:87 http://ubuntu.excellmedia.net/archive/ trusty/main libgssapi3-heimdal amd64 1.6~git20131207+dfsg-1ubuntu1 [90.1 kB
Err http://ubuntu.excellmedia.net/archive/ trusty/main libidn11 i386 1.28-1ubuntu2                                                              
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libidn11 amd64 1.28-1ubuntu2                                                             
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libnfnetlink0 amd64 1.0.1-2                                                              
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libparted0debian1 amd64 2.3-19ubuntu1                                                    
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libpcap0.8 amd64 1.5.3-2                                                                 
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main pciutils amd64 1:3.2.1-1ubuntu5                                                          
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libpci3 amd64 1:3.2.1-1ubuntu5                                                           
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libpipeline1 amd64 1.3.0-1                                                               
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libx11-data all 2:1.6.2-1ubuntu2                                                         
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libxau-dev i386 1:1.0.8-1                                                                
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libxau-dev amd64 1:1.0.8-1                                                               
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libxau6 amd64 1:1.0.8-1                                                                  
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libxau6 i386 1:1.0.8-1                                                                   
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main xorg-sgml-doctools all 1:1.11-1                                                          
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main x11proto-core-dev all 7.0.24-1                                                           
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libxdmcp-dev i386 1:1.1.1-1                                                              
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libxdmcp-dev amd64 1:1.1.1-1                                                             
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libxdmcp6 amd64 1:1.1.1-1                                                                
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libxdmcp6 i386 1:1.1.1-1                                                                 
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main x11proto-input-dev all 2.3-1                                                             
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main x11proto-kb-dev all 1.0.6-2                                                              
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main xtrans-dev all 1.3.2-1                                                                   
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libxcb1-dev i386 1.10-2ubuntu1                                                           
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libxcb1-dev amd64 1.10-2ubuntu1                                                          
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libxcb1 amd64 1.10-2ubuntu1                                                              
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libxcb1 i386 1.10-2ubuntu1                                                               
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libpthread-stubs0-dev amd64 0.3-4                                                        
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libpthread-stubs0-dev i386 0.3-4                                                         
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libx11-dev amd64 2:1.6.2-1ubuntu2                                                        
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libx11-dev i386 2:1.6.2-1ubuntu2                                                         
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libx11-6 i386 2:1.6.2-1ubuntu2                                                           
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libx11-6 amd64 2:1.6.2-1ubuntu2                                                          
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main x11proto-xext-dev all 7.3.0-1                                                            
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libxext-dev amd64 2:1.3.2-1                                                              
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libxext6 i386 2:1.3.2-1                                                                  
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libxext6 amd64 2:1.3.2-1                                                                 
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main libxmuu1 amd64 2:1.1.1-1                                                                 
  403  Forbidden
Get:88 http://ubuntu.excellmedia.net/archive/ trusty/main groff-base amd64 1.22.2-5 [1,053 kB]                                                  
Err http://ubuntu.excellmedia.net/archive/ trusty/main man-db amd64 2.6.7.1-1                                                                   
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main popularity-contest all 1.57ubuntu1                                                       
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main sgml-base all 1.26+nmu4ubuntu1                                                           
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/universe chromium-codecs-ffmpeg amd64 34.0.1847.116-0ubuntu2                                  
  403  Forbidden
Get:89 http://ubuntu.excellmedia.net/archive/ trusty/main flex amd64 2.5.35-10.1ubuntu2 [211 kB]                                                
Get:90 http://ubuntu.excellmedia.net/archive/ trusty/main libfl-dev amd64 2.5.35-10.1ubuntu2 [17.2 kB]                                          
Err http://ubuntu.excellmedia.net/archive/ trusty/main libsigsegv2 amd64 2.10-2                                                                 
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/main m4 amd64 1.4.17-2ubuntu1                                                                 
  403  Forbidden
Err http://ubuntu.excellmedia.net/archive/ trusty/universe fonts-horai-umefont all 460-1                                                        
  403  Forbidden
Get:91 http://ubuntu.excellmedia.net/archive/ trusty/main fonts-kacst all 2.01+mry-10 [305 kB]                                                  
Get:92 http://ubuntu.excellmedia.net/archive/ trusty/main fonts-kacst-one all 5.0+svn11846-7 [46.7 kB]                                          
Get:93 http://ubuntu.excellmedia.net/archive/ trusty/main fonts-nanum all 20131007-1 [8,709 kB]                                                 
Get:94 http://ubuntu.excellmedia.net/archive/ trusty/main fonts-takao-pgothic all 003.02.01-9ubuntu2 [3,403 kB]         

```

i guess it have much improved from earlier 
hvae reduced no of errors
after it completes ill do upgrade to 14.04 
and see if it work 
will be back with report
thanks

---

### Post by Bashing-om on 2014-07-12
sooraj2; Yes, much better;

But there is yet these 403 errors:
> 
Err [http://ubuntu.excellmedia.net/archive/](http://ubuntu.excellmedia.net/archive/) trusty/main sensible-utils all 0.0.9
  403  Forbidden
Get:2 [http://ubuntu.excellmedia.net/archive/](http://ubuntu.excellmedia.net/archive/) trusty/main debianutils amd64 4.4 [88.7 kB]
Get:3 [http://ubuntu.excellmedia.net/archive/](http://ubuntu.excellmedia.net/archive/) trusty-updates/main bash amd64 4.3-7ubuntu1 [575 kB]
Err [http://ubuntu.excellmedia.net/archive/](http://ubuntu.excellmedia.net/archive/) trusty/main libcap2 i386 1:2.24-0ubuntu2
  403  Forbidden
 and so on and on.

Need to find the source of this repository and find out what is not taking place. Perhaps "excellmedia" has not caught up with the current ubuntu release; and 'should' also be turned down in your install.

[INDENT][INDENT]still, fixable
[/INDENT][/INDENT]

---

### Post by sooraj2 on 2014-07-13
> **Bashing-om said:**
> sooraj2; Yes, much better;

But there is yet these 403 errors:
 and so on and on.

Need to find the source of this repository and find out what is not taking place. Perhaps "excellmedia" has not caught up with the current ubuntu release; and 'should' also be turned down in your install.[INDENT][INDENT]still, fixable
[/INDENT]
[/INDENT]


i changed my server to 
```
[COLOR=#000000]"us.archive.ubuntu.com/" [/COLOR]
```

and it still have ```
[http://ubuntu.excellmedia.net/archive/](http://ubuntu.excellmedia.net/archive/)
```
in download i dont understand why 

[http://ubuntu.excellmedia.net/archive/](http://ubuntu.excellmedia.net/archive/) is indian server my old one i changed it and still it shows 

```
[COLOR=#000000]*Err *[/COLOR][http://ubuntu.excellmedia.net/archive/](http://ubuntu.excellmedia.net/archive/)[COLOR=#000000]* trusty/main sensible-utils all 0.0.9*[/COLOR]
[COLOR=#000000]*403 Forbidden*[/COLOR]
[COLOR=#000000]*Get:2 *[/COLOR][http://ubuntu.excellmedia.net/archive/](http://ubuntu.excellmedia.net/archive/)[COLOR=#000000]* trusty/main debianutils amd64 4.4 [88.7 kB]*[/COLOR]
[COLOR=#000000]*Get:3 *[/COLOR][http://ubuntu.excellmedia.net/archive/](http://ubuntu.excellmedia.net/archive/)[COLOR=#000000]* trusty-updates/main bash amd64 4.3-7ubuntu1 [575 kB]*[/COLOR]
[COLOR=#000000]*Err *[/COLOR][http://ubuntu.excellmedia.net/archive/](http://ubuntu.excellmedia.net/archive/)[COLOR=#000000]* trusty/main libcap2 i386 1:2.24-0ubuntu2*[/COLOR]
[COLOR=#000000]*403 Forbidden*[/COLOR]
```

and on ```
sudo apt-get upgrade 
``` i get this

```
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libt/libtheora/libtheora0_1.1.1+dfsg.1-3.2_amd64.deb  403  ForbiddenFailed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libt/libtheora/libtheora0_1.1.1+dfsg.1-3.2_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libshout/libshout3_2.3.1-3_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libshout/libshout3_2.3.1-3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libsndfile/libsndfile1_1.0.25-7ubuntu2_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libsndfile/libsndfile1_1.0.25-7ubuntu2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libspectre/libspectre1_0.2.7-2ubuntu1.1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libssh/libssh-4_0.6.1-0ubuntu3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/o/openssl098/libssl0.9.8_0.9.8o-7ubuntu3.2.14.04.1_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libx11/libx11-xcb1_1.6.2-1ubuntu2_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libx11/libx11-xcb1_1.6.2-1ubuntu2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xcb-util/libxcb-util0_0.3.8-2ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/startup-notification/libstartup-notification0_0.12-3ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-25ubuntu4_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/sysfsutils/libsysfs2_2.1.0+repack-3ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/taglib/libtag1-vanilla_1.9.1-2_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/taglib/libtag1-vanilla_1.9.1-2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/taglib/libtag1c2a_1.9.1-2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/taglib/libtag1c2a_1.9.1-2_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/talloc/libtalloc2_2.1.0-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/telepathy-glib/libtelepathy-glib0_0.22.1-1ubuntu2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libt/libthai/libthai-data_0.1.20-3_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libt/libthai/libthai0_0.1.20-3_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libt/libthai/libthai0_0.1.20-3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libu/libunistring/libunistring0_0.9.3-5ubuntu3_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libu/libunistring/libunistring0_0.9.3-5ubuntu3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/v/v4l-utils/libv4l-0_1.0.1-1_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/v/v4l-utils/libv4l-0_1.0.1-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/v/v4l-utils/libv4lconvert0_1.0.1-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/v/v4l-utils/libv4lconvert0_1.0.1-1_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libv/libva/libva1_1.3.0-2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libv/libva/libva-x11-1_1.3.0-2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/v/vala-0.16/valac-0.16-vapi_0.16.1-2ubuntu4_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/v/vala-0.16/valac-0.16_0.16.1-2ubuntu4_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/v/vala-0.16/libvala-0.16-0_0.16.1-2ubuntu4_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libv/libvisual/libvisual-0.4-0_0.4.0-5_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libv/libvisual/libvisual-0.4-0_0.4.0-5_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libv/libvpx/libvpx1_1.3.0-2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libw/libwacom/libwacom2_0.8-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libw/libwacom/libwacom-common_0.8-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/wavpack/libwavpack1_4.70.0-1_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/wavpack/libwavpack1_4.70.0-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libw/libwmf/libwmf0.2-7-gtk_0.2.8.4-10.3ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libw/libwmf/libwmf0.2-7_0.2.8.4-10.3ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/tcp-wrappers/libwrap0_7.6.q-25_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/tcp-wrappers/libwrap0_7.6.q-25_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libx86/libx86-1_1.1+ds1-10_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxmu/libxmu6_1.1.1-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxmu/libxmu6_1.1.1-1_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxpm/libxpm4_3.5.10-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxpm/libxpm4_3.5.10-1_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxaw/libxaw7_1.0.12-1_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxaw/libxaw7_1.0.12-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcb/libxcb-composite0_1.10-2ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcb/libxcb-dri2-0_1.10-2ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcb/libxcb-glx0_1.10-2ubuntu1_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcb/libxcb-glx0_1.10-2ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcb/libxcb-randr0_1.10-2ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcb/libxcb-shape0_1.10-2ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcb/libxcb-xv0_1.10-2ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcomposite/libxcomposite-dev_0.4.4-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcomposite/libxcomposite1_0.4.4-1_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcomposite/libxcomposite1_0.4.4-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcursor/libxcursor-dev_1.1.14-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcursor/libxcursor1_1.1.14-1_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxcursor/libxcursor1_1.1.14-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxdamage/libxdamage-dev_1.1.4-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxdamage/libxdamage1_1.1.4-1ubuntu1_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxdamage/libxdamage1_1.1.4-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxfont/libxfont1_1.4.7-1ubuntu0.1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xft/libxft-dev_2.3.1-2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xft/libxft2_2.3.1-2_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xft/libxft2_2.3.1-2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxinerama/libxinerama-dev_1.1.3-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxinerama/libxinerama1_1.1.3-1_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxinerama/libxinerama1_1.1.3-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxp/libxp6_1.0.2-1ubuntu1_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxp/libxp6_1.0.2-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxrandr/libxrandr-dev_1.4.2-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxrandr/libxrandr2_1.4.2-1_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxrandr/libxrandr2_1.4.2-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/x11proto-randr/x11proto-randr-dev_1.4.0+git20120101.is.really.1.4.0-0ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxres/libxres1_1.0.7-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/x11proto-scrnsaver/x11proto-scrnsaver-dev_1.2.2-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxss/libxss-dev_1.2.2-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxss/libxss1_1.2.2-1_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxss/libxss1_1.2.2-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxtst/libxtst6_1.2.2-1_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxtst/libxtst6_1.2.2-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxv/libxv1_1.0.10-1_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxv/libxv1_1.0.10-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxvmc/libxvmc1_1.0.8-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxxf86dga/libxxf86dga1_1.1.4-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxxf86vm/libxxf86vm1_1.1.3-1_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libxxf86vm/libxxf86vm1_1.1.3-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/z/zephyr/libzephyr4_3.1.2-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/z/zvbi/libzvbi-common_0.2.35-2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/z/zvbi/libzvbi0_0.2.35-2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unixodbc/odbcinst_2.2.14p2-5ubuntu5_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unixodbc/odbcinst1debian2_2.2.14p2-5ubuntu5_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unixodbc/odbcinst1debian2_2.2.14p2-5ubuntu5_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pcmciautils/pcmciautils_018-8_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/q/qt-at-spi/qt-at-spi_0.3.1-4fakesync1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/tasksel/tasksel-data_2.88ubuntu15_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/tasksel/tasksel_2.88ubuntu15_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/c/cabextract/cabextract_1.4-4_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xfonts-utils/xfonts-utils_7.7+1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/multiverse/m/msttcorefonts/ttf-mscorefonts-installer_3.4+nmu1ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/f/fonts-unfonts-core/ttf-unfonts-core_1.0.3.is.1.0.2-080608-10ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xaw3d/xaw3dg_1.5+E-18.2_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/wget/wget_1.15-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/liba/libass/libass4_0.10.1-3ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/liba/libavc1394/libavc1394-0_0.5.4-2_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/liba/libavc1394/libavc1394-0_0.5.4-2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/i/isdnutils/libcapi20-3_3.25+dfsg1-3.3ubuntu2_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/i/isdnutils/libcapi20-3_3.25+dfsg1-3.3ubuntu2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libd/libdc1394-22/libdc1394-22_2.2.1-2ubuntu2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libd/libdca/libdca0_0.0.5-6ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/wireless-tools/libiw30_30~pre9-8ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libl/liblouis/liblouis-data_2.5.3-2ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libl/liblouis/liblouis2_2.5.3-2ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/o/openal-soft/libopenal1_1.14-4ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/o/openal-soft/libopenal1_1.14-4ubuntu1_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/o/openal-soft/libopenal-data_1.14-4ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/speech-dispatcher/libspeechd2_0.8-5ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xcb-util-keysyms/libxcb-keysyms1_0.3.9-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/o/openjdk-6/icedtea-6-jre-cacao_6b31-1.13.3-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/o/openjdk-6/openjdk-6-jre-lib_6b31-1.13.3-1ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/o/openjdk-6/icedtea-6-jre-jamvm_6b31-1.13.3-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/openssl/openssl_1.0.1f-1ubuntu2.4_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/o/openjdk-6/openjdk-6-jre-headless_6b31-1.13.3-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/less/less_458-2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libc/libcap2/libcap2-bin_2.24-0ubuntu2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libc/libcap2/libpam-cap_2.24-0ubuntu2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lockfile-progs/lockfile-progs_0.1.17_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/logrotate/logrotate_3.8.7-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mime-support/mime-support_3.54ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/net-tools/net-tools_1.60-25ubuntu2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/netcat-openbsd/netcat-openbsd_1.105-7ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/sudo/sudo_1.8.9p5-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/ureadahead/ureadahead_0.100.0-16_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/v/vim/vim-tiny_7.4.052-1ubuntu3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/v/vim/vim-common_7.4.052-1ubuntu3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/newt/whiptail_0.52.15-2ubuntu5_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/netkit-ftp/ftp_0.17-28_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/texinfo/info_5.2.0.dfsg.1-2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lshw/lshw_02.16-2ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lsof/lsof_4.86+dfsg-1ubuntu2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/ltrace/ltrace_0.7.3-4ubuntu5.1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/manpages/manpages_3.54-1ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/memtest86+/memtest86+_4.20-1.1ubuntu8_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mlocate/mlocate_0.26-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mtr/mtr-tiny_0.85-2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/nano/nano_2.2.6-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/parted/parted_2.3-19ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/plymouth/plymouth-theme-ubuntu-text_0.8.8-0ubuntu17_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/powermgmt-base/powermgmt-base_1.31build1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/ppp/ppp_2.4.5-5.1ubuntu2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pppconfig/pppconfig_2.3.19ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/psmisc/psmisc_22.20-1ubuntu2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-apt/python-apt-common_0.9.3.5_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/rsync/rsync_3.1.0-2ubuntu0.1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/strace/strace_4.8-1ubuntu5_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/tcpdump/tcpdump_4.5.1-2ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/netkit-telnet/telnet_0.17-36build2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/time/time_1.7-24_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/ubuntu-meta/ubuntu-standard_1.325_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/util-linux/uuid-runtime_2.20.1-5.1ubuntu20.1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xauth/xauth_1.0.7-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xml-core/xml-core_0.13+nmu2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/make-dfsg/make_3.81-8.2ubuntu3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xapian-core/libxapian22_1.2.16-2ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xapian-bindings/python-xapian_1.2.16-2ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libd/libdaemon/libdaemon0_0.14-2ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/rarian/librarian0_0.8.1-5ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/sgml-data/sgml-data_2.0.9-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/rarian/rarian-compat_0.8.1-5ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/b/bless/bless_0.6.0-4_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/b/bluez/bluez-gstreamer_4.101-0ubuntu13_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/liby/libyaml-tiny-perl/libyaml-tiny-perl_1.56-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_11.2.202.394ubuntu0.14.04.1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/libreoffice/fonts-opensymbol_102.6+LibO4.2.4-0ubuntu2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/f/fuseiso/fuseiso_20070708-3ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/liba/libappindicator/gir1.2-appindicator3-0.1_12.10.1+13.10.20130920-0ubuntu4_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/systemd/gir1.2-gudev-1.0_204-5ubuntu20.3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libn/libnotify/gir1.2-notify-0.7_0.7.6-1ubuntu3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libe/liberror-perl/liberror-perl_0.17-1.1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gksu/gksu_2.0.2-6ubuntu2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/x11-utils/x11-utils_7.7+1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gnome-media/gnome-media_3.4.0-1ubuntu2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libn/libnice/gstreamer0.10-nice_0.1.4-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/guile-1.8/guile-1.8-libs_1.8.8+1-8ubuntu3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/h/heirloom-mailx/heirloom-mailx_12.5-2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/libreoffice-dictionaries/hunspell-en-ca_4.2.1-0ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libn/libnet-http-perl/libnet-http-perl_6.06-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libl/liblwp-mediatypes-perl/liblwp-mediatypes-perl_6.02-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libt/libtimedate-perl/libtimedate-perl_2.3000-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libh/libhttp-date-perl/libhttp-date-perl_6.02-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libh/libhttp-daemon-perl/libhttp-daemon-perl_6.01-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libu/liburi-perl/liburi-perl_1.60-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libh/libhtml-form-perl/libhtml-form-perl_6.03-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libf/libfile-listing-perl/libfile-listing-perl_6.04-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libe/libencode-locale-perl/libencode-locale-perl_1.03-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libh/libhtml-tree-perl/libhtml-tree-perl_5.03-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libw/libwww-perl/libwww-perl_6.05-2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/i/icoutils/icoutils_0.31.0-2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xbitmaps/xbitmaps_1.1.1-2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libu/libutempter/libutempter0_1.1.5-4build1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xterm/xterm_297-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/i/im-switch/im-switch_1.23ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/k/kate/kate-data_4.13.2-0ubuntu0.1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/k/kernel-package/kernel-package_12.036+nmu3_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/readline5/lib32readline-gplv2-dev_5.2+dfsg-2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/readline5/lib32readline5_5.2+dfsg-2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/readline6/lib32readline6_6.3-4ubuntu2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/a/a52dec/liba52-0.7.4_0.7.4-17_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/liba/libalgorithm-diff-perl/libalgorithm-diff-perl_1.19.02-3_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/o/openjdk-6/openjdk-6-jre_6b31-1.13.3-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libb/libbonoboui/libbonoboui2-common_2.24.5-0ubuntu3_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libb/libburn/libburn4_1.3.4-0ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libc/libcanberra/libcanberra-gtk-module_0.30-0ubuntu3_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libc/libcanberra/libcanberra-gtk-module_0.30-0ubuntu3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libc/libcddb/libcddb2_1.3.2-4fakesync2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libc/libcdio/libcdio13_0.83-4.1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libc/libcdio/libcdio-cdda1_0.83-4.1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libc/libcdio/libcdio-paranoia1_0.83-4.1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libc/libclass-isa-perl/libclass-isa-perl_0.36-5_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libn/libnet-domain-tld-perl/libnet-domain-tld-perl_1.70-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libe/libemail-valid-perl/libemail-valid-perl_1.192-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libf/libfile-desktopentry-perl/libfile-desktopentry-perl_0.07-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libf/libfile-mimeinfo-perl/libfile-mimeinfo-perl_0.22-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libg/libgda5/libgda-5.0-common_5.2.2-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgdata/libgdata-common_0.14.1-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gnome-menus2/libgnome-menu2_3.0.1-0ubuntu9_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgnome/libgnome2-bin_2.32.1-4ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgnome/libgnome2-common_2.32.1-4ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgnomecanvas/libgnomecanvas2-common_2.30.3-2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgnomekbd/libgnomekbd-common_3.6.0-0ubuntu2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgnomeui/libgnomeui-common_2.24.5-3_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgphoto2/libgphoto2-l10n_2.5.3.1-1ubuntu2.2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gtksourceview2/libgtksourceview2.0-common_2.10.5-1ubuntu2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgtop2/libgtop2-common_2.28.5-2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgtop2/libgtop2-7_2.28.5-2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libh/libhtml-format-perl/libhtml-format-perl_2.11-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libi/libid3tag/libid3tag0_0.15.1b-10ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libi/libindicate/libindicate-gtk3_12.10.1-0ubuntu3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libi/libio-socket-inet6-perl/libio-socket-inet6-perl_2.71-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libi/libio-string-perl/libio-string-perl_1.08-3_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libi/libipc-run-perl/libipc-run-perl_0.92-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libc/libcdio/libiso9660-8_0.83-4.1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libi/libisofs/libisofs6_1.3.4-0ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libk/libkate/libkate1_0.4.1-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/meanwhile/libmeanwhile1_1.0.2-4.1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/miniupnpc/libminiupnpc8_1.6-3ubuntu2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libm/libmodplug/libmodplug1_0.8.8.4-4.1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libm/libmpc/libmpcdec6_0.1~r459-1ubuntu3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mythes/libmythes-1.2-0_1.2.2-1ubuntu2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libn/libnet-ip-perl/libnet-ip-perl_1.26-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/network-manager/libnm-glib-vpn1_0.9.8.8-0ubuntu7_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/network-manager-applet/libnm-gtk-common_0.9.8.8-0ubuntu4.2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libn/libnotify/libnotify-bin_0.7.6-1ubuntu3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/n/ntrack/ntrack-module-libnl-0_016-1.2ubuntu2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/n/ntrack/libntrack0_016-1.2ubuntu2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/n/ntrack/libntrack-qt4-1_016-1.2ubuntu2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libo/libopenobex/libopenobex1_1.5-2.1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pango1.0/libpango1.0-doc_1.36.3-1ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libp/libpaper/libpaper-utils_1.1.24+nmu2ubuntu3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libp/libparse-debcontrol-perl/libparse-debcontrol-perl_2.005-4_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libp/libpostproc/libpostproc52_0.git20120821-4_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/postgresql-9.3/libpq5_9.3.4-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pidgin/libpurple-bin_2.10.9-0ubuntu3.1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/libreoffice/libreoffice-style-human_4.2.4-0ubuntu2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/s/sidplay-libs/libresid-builder0c2a_2.1.1-14_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/sg3-utils/libsgutils2-2_1.36-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libs/libsidplay/libsidplay1_1.36.59-5ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/s/sidplay-libs/libsidplay2_2.1.1-14_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/openslp-dfsg/libslp1_1.2.1-9_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libs/libsys-hostname-long-perl/libsys-hostname-long-perl_1.4-3_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/t1lib/libt1-5_5.1.2-3.6ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libt/libtar/libtar0_1.2.20-3ubuntu0.1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libt/libtie-ixhash-perl/libtie-ixhash-perl_1.23-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libt/libtool/libtool_2.4.2-1.7ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/t/twolame/libtwolame0_0.3.13-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/u/unity/unity-2d-spread_7.2.1+14.04.20140513-0ubuntu2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/u/unity/unity-2d-panel_7.2.1+14.04.20140513-0ubuntu2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/u/unity/unity-2d-shell_7.2.1+14.04.20140513-0ubuntu2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/u/unity/libunity-2d-private0_7.2.1+14.04.20140513-0ubuntu2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/v/vcdimager/libvcdinfo0_0.7.24+dfsg-0.1ubuntu2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/v/virtuoso-opensource/libvirtodbc0_6.1.6+repack-0ubuntu3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/v/virtuoso-opensource/virtuoso-opensource-6.1-common_6.1.6+repack-0ubuntu3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libv/libvisual-plugins/libvisual-0.4-plugins_0.4.0.dfsg.1-7build1_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libv/libvisual-plugins/libvisual-0.4-plugins_0.4.0.dfsg.1-7build1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/v/vte/libvte-common_0.28.2-5ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/v/vte/libvte9_0.28.2-5ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/webkitgtk/libwebkitgtk-1.0-common_2.4.3-1ubuntu2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/webkitgtk/libwebkitgtk-3.0-common_2.4.3-1ubuntu2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libw/libwnck3/libwnck-3-common_3.4.7-0ubuntu3_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libw/libwnck/libwnck-common_2.30.7-0ubuntu4_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libw/libwpd/libwpd-0.9-9_0.9.9-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libw/libwpg/libwpg-0.2-2_0.2.2-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libw/libwps/libwps-0.2-2_0.2.9-2ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libx/libx11/libx11-doc_1.6.2-1ubuntu2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/ubuntu-themes/ubuntu-mono_14.04+14.04.20140410-0ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/ubuntu-themes/light-themes_14.04+14.04.20140410-0ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/linux-firmware/linux-firmware_1.127.4_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/manpages/manpages-dev_3.54-1ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/media-player-info/media-player-info_21-0ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pygobject-2/python-gobject-2_2.28.6-12build1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/patch/patch_2.7.1-4ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/m/meld/meld_1.8.4-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/metacity/metacity-common_2.34.13-0ubuntu4_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/m/mingw32-binutils/mingw32-binutils_2.20-0.2ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mtools/mtools_4.0.18-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/openoffice.org-en-au/myspell-en-au_2.1-5.4_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/libreoffice-dictionaries/myspell-en-gb_4.2.1-0ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/libreoffice-dictionaries/myspell-en-za_4.2.1-0ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/openoffice.org-en-au/mythes-en-au_2.1-5.4_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libr/libreoffice-dictionaries/mythes-en-us_4.2.1-0ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/ncurses/ncurses-term_5.9+20140118-1ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/notify-osd-icons/notify-osd-icons_0.8+14.04.20131204-0ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/nux/nux-tools_4.0.6+14.04.20140409-0ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/obex-data-server/obex-data-server_0.4.6-0ubuntu2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/obexd/obexd-client_0.46-1ubuntu7_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/openoffice.org-hyphenation/openoffice.org-hyphenation_0.7_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/os-prober/os-prober_1.63ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/o/oxygen-icons/oxygen-icon-theme_4.13.0-0ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/patchutils/patchutils_0.3.2-3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pax/pax_20120606-2+deb7u1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/phonon/phonon_4.7.1-0ubuntu8_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/ubuntu-font-family-sources/ttf-ubuntu-font-family_0.80-0ubuntu6_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/plymouth/plymouth-theme-ubuntu-logo_0.8.8-0ubuntu17_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/p/pngcrush/pngcrush_1.7.65-0.1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/policykit-1-gnome/policykit-1-gnome_0.105-1ubuntu4_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pptp-linux/pptp-linux_1.7.2-7_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/min12xxw/printer-driver-min12xxw_0.0.9-8ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pnm2ppa/printer-driver-pnm2ppa_1.13+nondbs-0ubuntu4_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pulseaudio/pulseaudio-module-gconf_4.0-0ubuntu11_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pulseaudio/pulseaudio-module-x11_4.0-0ubuntu11_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-httplib2/python-httplib2_0.8-2build1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-setuptools/python-pkg-resources_3.3-1ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lazr.uri/python-lazr.uri_1.0.3-1build1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-wadllib/python-wadllib_1.3.2-2build1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/z/zope.interface/python-zope.interface_4.0.5-1ubuntu4_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-oauth/python-oauth_1.0.1-3build2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lazr.restfulclient/python-lazr.restfulclient_0.13.3-1build1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-launchpadlib/python-launchpadlib_1.10.2+ds-2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pycairo/python-cairo_1.8.8-1ubuntu5_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pyxdg/python-xdg_0.25-4_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/p/python-configglue/python-configglue_1.1.2-0ubuntu2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/system-config-printer/python-cupshelpers_1.4.3+20140219-0ubuntu2.1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-dateutil/python-dateutil_1.5+dfsg-1ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/f/flup/python-flup_1.0.2-4_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-stdlib-extensions/python-gdbm_2.7.5-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/i/ipy/python-ipy_0.81-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libp/libproxy/python-libproxy_0.4.11-0ubuntu4_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/markupsafe/python-markupsafe_0.18-1build2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mako/python-mako_0.9.1-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/n/notify-python/python-notify_0.1.1-3ubuntu2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pyopenssl/python-openssl_0.13-2ubuntu6_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-pam/python-pam_0.4.2-13.1ubuntu3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pexpect/python-pexpect_3.1-1ubuntu0.1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/psycopg2/python-psycopg2_2.4.5-1build5_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pyinotify/python-pyinotify_0.9.4-1build1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-reportlab/python-renderpm_3.0-1build1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-reportlab/python-reportlab-accel_3.0-1build1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pyserial/python-serial_2.6-1build1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/s/software-properties/python-software-properties_0.92.37.1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/p/python-support/python-support_1.0.15_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/twisted/python-twisted-bin_13.2.0-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/twisted/python-twisted-core_13.2.0-1ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/twisted/python-twisted-names_13.2.0-1ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/twisted/python-twisted-web_13.2.0-1ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/v/virtkey/python-virtkey_0.63.0-0ubuntu3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/p/pywebkitgtk/python-webkit_1.1.8-3ubuntu2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/w/webpy/python-webpy_0.37+20120626-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/x/x-kit/python-xkit_0.5.0ubuntu2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/z/zeitgeist/python-zeitgeist_0.9.14-0ubuntu4_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/q/q4wine/q4wine_1.1-r2-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/r/radeontool/radeontool_1.6.3-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/multiverse/r/rar/rar_4.2.0-1_i386.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/rfkill/rfkill_0.5-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/r/rtkit/rtkit_0.10-3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/update-inetd/update-inetd_4.43_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/sane-backends/sane-utils_1.0.23-3ubuntu3.1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/shared-desktop-ontologies/shared-desktop-ontologies_0.11.0-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/sharutils/sharutils_4.14-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xdg-utils/xdg-utils_1.1.0~rc1-2ubuntu7_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/simple-scan/simple-scan_3.12.1-0ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/sni-qt/sni-qt_0.2.6-0ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/squashfs-tools/squashfs-tools_4.2+20130409-2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/o/openssh/ssh-askpass-gnome_6.6p1-2ubuntu2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/ssl-cert/ssl-cert_1.0.33_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/syslinux/syslinux-common_4.05+dfsg-6+deb8u1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/syslinux/syslinux_4.05+dfsg-6+deb8u1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/s/system-config-printer/system-config-printer-common_1.4.3+20140219-0ubuntu2.1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/tcp-wrappers/tcpd_7.6.q-25_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/telepathy-idle/telepathy-idle_0.2.0-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/thunderbird/thunderbird-globalmenu_24.6.0+build1-0ubuntu0.14.04.1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/thunderbird/thunderbird-locale-en-gb_24.6.0+build1-0ubuntu0.14.04.1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/thunderbird/thunderbird-locale-en-us_24.6.0+build1-0ubuntu0.14.04.1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/tofrodos/tofrodos_1.7.13+ds-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/toshset/toshset_1.76-4_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/ttf-indic-fonts/ttf-indic-fonts-core_0.5.14ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/t/ttf-indic-fonts/ttf-punjabi-fonts_0.5.14ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/ubuntu-themes/ubuntu-artwork_14.04+14.04.20140410-0ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/ubuntu-docs/ubuntu-docs_14.04.4_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/u/ubuntu-wallpapers/ubuntu-wallpapers-precise_14.04.0.1-0ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/u/unity/unity-2d_7.2.1+14.04.20140513-0ubuntu2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/u/unity/unity-2d-common_7.2.1+14.04.20140513-0ubuntu2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unity-asset-pool/unity-asset-pool_0.8.24daily13.06.10-0ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unixodbc/unixodbc_2.2.14p2-5ubuntu5_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/multiverse/u/unrar-nonfree/unrar_5.0.10-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/unzip/unzip_6.0-9ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/v/valgrind/valgrind_3.10~20140411-0ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/v/vbetool/vbetool_1.1-3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/v/virtuoso-opensource/virtuoso-opensource-6.1-bin_6.1.6+repack-0ubuntu3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/v/virtuoso-opensource/virtuoso-minimal_6.1.6+repack-0ubuntu3_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/wdiff/wdiff_1.2.1-2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/whois/whois_5.1.1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/w/wireless-tools/wireless-tools_30~pre9-8ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/x11-apps/x11-apps_7.7+2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/x11-session-utils/x11-session-utils_7.7+1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/x11-xfs-utils/x11-xfs-utils_7.7+1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/x11-xkb-utils/x11-xkb-utils_7.7+1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/x11-xserver-utils/x11-xserver-utils_7.7+2ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/x11proto-fixes/x11proto-fixes-dev_5.0-2ubuntu2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/x/xcftools/xcftools_1.0.7-4ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/x/xclip/xclip_0.12+svn84-4_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xdg-user-dirs/xdg-user-dirs_0.15-1ubuntu3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xinit/xinit_1.3.2-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xinput/xinput_1.6.1-1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xorg/xorg_7.7+1ubuntu8_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xorg/xserver-xorg_7.7+1ubuntu8_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xorg-docs/xorg-docs-core_1.7-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xorg-server/xserver-common_1.15.1-0ubuntu2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/ubufox/xul-ext-ubufox_2.9-0ubuntu0.14.04.1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/y/yelp-xsl/yelp-xsl_3.10.1-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/z/zeitgeist/zeitgeist_0.9.14-0ubuntu4_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/z/zip/zip_3.0-8_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/c/compiz/compiz-plugins-main-default_0.9.11.1+14.04.20140701-0ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/c/compiz/compizconfig-backend-gconf_0.9.11.1+14.04.20140701-0ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/h/haskell-bzlib/libghc-bzlib-dev_0.5.0.4-2_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/ghc/ghc_7.6.3-10_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/g/gnome-exe-thumbnailer/gnome-exe-thumbnailer_0.9.3-0ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libc/libcanberra/libcanberra-gtk3-module_0.30-0ubuntu3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pkg-kde-tools/libdlrestrictions1_0.15.12ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libg/libgweather/libgweather-common_3.10.2-0ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lirc/liblircclient0_0.9.0-0ubuntu5_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/libp/libpeas/libpeas-common_1.8.1-2ubuntu2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/polkit-qt-1/libpolkit-qt-1-1_0.103.0-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libq/libquvi-scripts/libquvi-scripts_0.4.21-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/l/lsb/lsb-invalid-mta_4.1+Debian11ubuntu6_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mobile-broadband-provider-info/mobile-broadband-provider-info_20140317-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/m/mscompress/mscompress_0.4-3_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/o/openjdk-6/openjdk-6-jdk_6b31-1.13.3-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/pbuilder/pbuilder_0.215ubuntu7_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-defer/python-defer_1.0.6-2build1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/p/python-lockfile/python-lockfile_0.8-2ubuntu2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/libl/liblouis/python-louis_2.5.3-2ubuntu1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/r/rebuildd/rebuildd_0.4.2_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/universe/f/fonts-liberation/ttf-liberation_1.07.3-3_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/usb-modeswitch/usb-modeswitch_2.1.1+repack0-1ubuntu1_amd64.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/u/usb-modeswitch-data/usb-modeswitch-data_20140327-1_all.deb  403  Forbidden
Failed to fetch http://ubuntu.excellmedia.net/archive/pool/main/x/xfonts-mathml/xfonts-mathml_6ubuntu1_all.deb  403  Forbidden
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?



``` 
a lot of errors again


now trying again after disabling all  [http://ubuntu.excellmedia.net/archive/](http://ubuntu.excellmedia.net/archive/) in software sources > other  software

---

### Post by sooraj2 on 2014-07-13
disabled all ```
[http://ubuntu.excellmedia.net/archive/](http://ubuntu.excellmedia.net/archive/)
```
in software sources > other sources 

and server is us best server 
```
mirror.kku.ac.th
```
till now all good 
```
traeko@Sooraj:~$ sudo apt-get updateHit http://ppa.launchpad.net trusty Release.gpg                                                                                           
Hit http://www.openprinting.org lsb3.2 Release.gpg                                                                                        
Hit http://ppa.launchpad.net trusty Release               
Hit http://ppa.launchpad.net trusty/main Sources                                                                 
Hit http://ppa.launchpad.net trusty/main amd64 Packages                                   
Hit http://ppa.launchpad.net trusty/main i386 Packages                                    
Ign http://ppa.launchpad.net trusty/main TranslationIndex                       
Hit http://www.openprinting.org lsb3.2 Release                                  
Hit http://www.openprinting.org lsb3.2/contrib amd64 Packages                    
Hit http://www.openprinting.org lsb3.2/contrib i386 Packages                    
Ign http://ppa.launchpad.net trusty/main Translation-en_US                                                      
Ign http://www.openprinting.org lsb3.2/contrib TranslationIndex                                                 
Ign http://ppa.launchpad.net trusty/main Translation-en   
Hit http://mirror.kku.ac.th precise Release.gpg                                           
Hit http://mirror.kku.ac.th precise Release
Hit http://mirror.kku.ac.th precise/main amd64 Packages
Hit http://mirror.kku.ac.th precise/universe amd64 Packages
Hit http://mirror.kku.ac.th precise/restricted amd64 Packages                  
Hit http://mirror.kku.ac.th precise/multiverse amd64 Packages                  
Hit http://mirror.kku.ac.th precise/main i386 Packages                         
Hit http://mirror.kku.ac.th precise/universe i386 Packages                     
Hit http://mirror.kku.ac.th precise/restricted i386 Packages                   
Hit http://mirror.kku.ac.th precise/multiverse i386 Packages                   
Hit http://mirror.kku.ac.th precise/main TranslationIndex                      
Hit http://mirror.kku.ac.th precise/multiverse TranslationIndex                
Hit http://mirror.kku.ac.th precise/restricted TranslationIndex                
Hit http://mirror.kku.ac.th precise/universe TranslationIndex                  
Hit http://mirror.kku.ac.th precise/main Translation-en                        
Hit http://mirror.kku.ac.th precise/multiverse Translation-en
Hit http://mirror.kku.ac.th precise/restricted Translation-en
Hit http://mirror.kku.ac.th precise/universe Translation-en
Ign http://www.openprinting.org lsb3.2/contrib Translation-en_US
Hit http://www.openprinting.org lsb3.2/contrib Translation-en
Reading package lists... Done    
```                       
```
traeko@Sooraj:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
```
traeko@Sooraj:~$ sudo update-manager -d
authenticate 'trusty.tar.gz' against 'trusty.tar.gz.gpg' 
extracting 'trusty.tar.gz'



```

---

### Post by Bucky Ball on 2014-07-13
All looks good so far. Let us know the upshot.

---

### Post by sooraj2 on 2014-07-13
> **Bucky Ball said:**
> All looks good so far. Let us know the upshot.
 looks like its done 
 
thanks guys 
thanks for all your helps

---

### Post by Bucky Ball on 2014-07-13
All looks good. To help others, please mark thread as solved by following the instructions in the second link in my signature and post new threads for any further issues/questions that may arise. Good luck and enjoy the OS. ;)

---

