---
title: "help update"
date: 2012-12-14
forum: Installation &amp; Upgrades
---

### Post by albaniaguard on 2012-12-14
Hi 
i have a problem with update.
for some days i have a mesage in my laptop:
"the update informations is outdates.this may be caused by network problems or by a repository that is no longer avivable.please update manualy by selection 'show updates' from the indicator menu and watching for any failing repositories"
my network is ok and when i go in show update i dont have new update.
what i can doing?

---

### Post by howefield on 2012-12-14
What version of Ubuntu are you running ?

---

### Post by albaniaguard on 2012-12-14
ubuntu 12.10

some times i teking som updates,but 1 or 2 our later again i have this problem

---

### Post by grahammechanical on 2012-12-14
Have you installed any software through a PPA? If so go to System Settings>Software Sources and under the Other Software tab and uncheck the PPAs. Then see if the details page will offer to install updates. It may take a few minutes to check what is available.

Regards.

---

### Post by albaniaguard on 2012-12-14
[http://dl.google.com/linux/earth/deb/stable](http://dl.google.com/linux/earth/deb/stable) this is no marked

i have ubuntu in albania language and i dont know what is the PPA :(

---

### Post by ibjsb4 on 2012-12-14
Hi albaniaguard

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and please post the output of:

```
sudo apt-get update
```

Edit:  Posted wrong command, sorry

---

### Post by albaniaguard on 2012-12-14
1	deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted
     2	# /etc/apt/sources.list
     3	
     4	deb [http://al.archive.ubuntu.com/ubuntu/](http://al.archive.ubuntu.com/ubuntu/) quantal main restricted
     5	deb-src [http://al.archive.ubuntu.com/ubuntu/](http://al.archive.ubuntu.com/ubuntu/) quantal restricted main multiverse universe #Added by software-properties
     6	deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) quantal-security main restricted
     7	deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) quantal-security main restricted #Added by software-properties
     8	deb [http://al.archive.ubuntu.com/ubuntu/](http://al.archive.ubuntu.com/ubuntu/) quantal-updates main restricted
     9	deb-src [http://al.archive.ubuntu.com/ubuntu/](http://al.archive.ubuntu.com/ubuntu/) quantal-updates restricted main multiverse universe #Added by software-properties
    10	
    11	# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
    12	# newer versions of the distribution.
    13	deb [http://al.archive.ubuntu.com/ubuntu/](http://al.archive.ubuntu.com/ubuntu/) quantal restricted
    14	
    15	## Major bug fix updates produced after the final release of the
    16	## distribution.
    17	deb [http://al.archive.ubuntu.com/ubuntu/](http://al.archive.ubuntu.com/ubuntu/) quantal-updates restricted
    18	
    19	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    20	## team. Also, please note that software in universe WILL NOT receive any
    21	## review or updates from the Ubuntu security team.
    22	deb [http://al.archive.ubuntu.com/ubuntu/](http://al.archive.ubuntu.com/ubuntu/) quantal universe
    23	deb [http://al.archive.ubuntu.com/ubuntu/](http://al.archive.ubuntu.com/ubuntu/) quantal-updates universe
    24	
    25	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    26	## team, and may not be under a free licence. Please satisfy yourself as to 
    27	## your rights to use the software. Also, please note that software in 
    28	## multiverse WILL NOT receive any review or updates from the Ubuntu
    29	## security team.
    30	deb [http://al.archive.ubuntu.com/ubuntu/](http://al.archive.ubuntu.com/ubuntu/) quantal multiverse
    31	deb [http://al.archive.ubuntu.com/ubuntu/](http://al.archive.ubuntu.com/ubuntu/) quantal-updates multiverse
    32	
    33	## N.B. software from this repository may not have been tested as
    34	## extensively as that contained in the main release, although it includes
    35	## newer versions of some applications which may provide useful features.
    36	## Also, please note that software in backports WILL NOT receive any review
    37	## or updates from the Ubuntu security team.
    38	deb [http://al.archive.ubuntu.com/ubuntu/](http://al.archive.ubuntu.com/ubuntu/) quantal-backports main restricted universe multiverse
    39	deb-src [http://al.archive.ubuntu.com/ubuntu/](http://al.archive.ubuntu.com/ubuntu/) quantal-backports main restricted universe multiverse #Added by software-properties
    40	
    41	deb [http://al.archive.ubuntu.com/ubuntu/](http://al.archive.ubuntu.com/ubuntu/) quantal-security main restricted
    42	deb-src [http://al.archive.ubuntu.com/ubuntu/](http://al.archive.ubuntu.com/ubuntu/) quantal-security restricted main multiverse universe #Added by software-properties
    43	deb [http://al.archive.ubuntu.com/ubuntu/](http://al.archive.ubuntu.com/ubuntu/) quantal-security universe
    44	deb [http://al.archive.ubuntu.com/ubuntu/](http://al.archive.ubuntu.com/ubuntu/) quantal-security multiverse
    45	
    46	## Uncomment the following two lines to add software from Canonical's
    47	## 'partner' repository.
    48	## This software is not part of Ubuntu, but is offered by Canonical and the
    49	## respective vendors as a service to Ubuntu users.
    50	deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner
    51	deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner
    52	
    53	## This software is not part of Ubuntu, but is offered by third-party
    54	## developers who want to ship their latest software.
    55	deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main
    56	deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main
    57	deb [http://al.archive.ubuntu.com/ubuntu/](http://al.archive.ubuntu.com/ubuntu/) quantal-proposed restricted main multiverse universe
ervis@Aspire-5810T:~$

---

### Post by ibjsb4 on 2012-12-14
Guess I wasn't fast enough, sorry.  Please reread post #6.

---

### Post by albaniaguard on 2012-12-14
what i can do?

---

### Post by ibjsb4 on 2012-12-14
Please post the output of:

```
sudo apt-get update
```

---

### Post by albaniaguard on 2012-12-14
```
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric InRelease
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric Release.gpg
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric Release
Err cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main Translation-sq_AL
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main Translation-sq
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main Translation-en
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted Translation-sq_AL
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted Translation-sq
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted Translation-en
Ign [http://archive.getdeb.net](http://archive.getdeb.net) quantal-getdeb InRelease                         
Err [http://archive.getdeb.net](http://archive.getdeb.net) quantal-getdeb Release.gpg                       
  Unable to connect to archive.getdeb.net:http:
Ign [http://archive.getdeb.net](http://archive.getdeb.net) quantal-getdeb Release                           
Ign [http://archive.getdeb.net](http://archive.getdeb.net) quantal-getdeb/apps i386 Packages/DiffIndex      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal InRelease                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security InRelease                      
Err [http://archive.getdeb.net](http://archive.getdeb.net) quantal-getdeb/apps Translation-sq_AL  
  Unable to connect to archive.getdeb.net:http:
Err [http://archive.getdeb.net](http://archive.getdeb.net) quantal-getdeb/apps Translation-sq     
  Unable to connect to archive.getdeb.net:http:
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal InRelease                             
Err [http://archive.getdeb.net](http://archive.getdeb.net) quantal-getdeb/apps Translation-en               
  Unable to connect to archive.getdeb.net:http:
Err [http://archive.getdeb.net](http://archive.getdeb.net) quantal-getdeb/apps i386 Packages      
  Unable to connect to archive.getdeb.net:http:
Ign [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal InRelease                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release.gpg                               
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release.gpg [933 B]          
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal Release.gpg                 
Ign [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-updates InRelease           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release                                   
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release [49,6 kB]            
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal Release                               
Ign [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-backports InRelease                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Sources                              
Ign [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-security InRelease                    
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Sources                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main i386 Packages                        
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal/partner i386 Packages                 
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Sources [22,1 kB]       
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Sources [14 B]    
Ign [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-proposed InRelease                    
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main i386 Packages [60,0 kB] 
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal Release.gpg                           
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-updates Release.gpg                   
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted i386 Packages [14 B]
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-backports Release.gpg                 
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-security Release.gpg                  
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-proposed Release.gpg                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en            
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal Release                               
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-updates Release                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-sq_AL                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en      
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-backports Release                     
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Translation-sq_AL             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-sq                       
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-security Release                      
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Translation-sq                
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-proposed Release                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en                       
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Translation-en                
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal/restricted Sources           
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal/main Sources
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal/multiverse Sources
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal/universe Sources
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal/main i386 Packages
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal/restricted i386 Packages
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal/universe i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-sq_AL
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal/multiverse i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-sq
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-sq_AL
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal/main Translation-sq
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-sq
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal/main Translation-en
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal/multiverse Translation-en
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal/restricted Translation-en
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal/universe Translation-sq
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal/universe Translation-en
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-updates/restricted Sources
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-updates/main Sources
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-updates/multiverse Sources
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-updates/universe Sources              
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-updates/main i386 Packages            
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-updates/restricted i386 Packages      
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-updates/universe i386 Packages        
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-updates/multiverse i386 Packages      
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-updates/main Translation-en           
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-updates/multiverse Translation-en     
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-updates/restricted Translation-en     
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-updates/universe Translation-en       
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-backports/main Sources                
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-backports/restricted Sources          
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-backports/universe Sources            
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-backports/multiverse Sources          
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-backports/main i386 Packages          
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-backports/restricted i386 Packages    
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-backports/universe i386 Packages      
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-backports/multiverse i386 Packages    
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-backports/main Translation-en         
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-backports/multiverse Translation-en   
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-backports/restricted Translation-en   
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-backports/universe Translation-en     
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-security/restricted Sources           
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-security/main Sources                 
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-security/multiverse Sources           
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-security/universe Sources             
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-security/main i386 Packages           
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-security/restricted i386 Packages     
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-security/universe i386 Packages
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-security/multiverse i386 Packages
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-security/main Translation-en
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-security/multiverse Translation-en
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-security/restricted Translation-en
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-security/universe Translation-en
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-proposed/restricted i386 Packages
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-proposed/main i386 Packages
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-proposed/multiverse i386 Packages
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-proposed/universe i386 Packages
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-proposed/main Translation-en
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-proposed/multiverse Translation-en
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-proposed/restricted Translation-en
Hit [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-proposed/universe Translation-en
Ign [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal/main Translation-sq_AL
Ign [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal/multiverse Translation-sq_AL
Ign [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal/multiverse Translation-sq
Ign [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal/restricted Translation-sq_AL
Ign [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal/restricted Translation-sq
Ign [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal/universe Translation-sq_AL
Ign [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-updates/main Translation-sq_AL
Ign [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-updates/main Translation-sq
Ign [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-updates/multiverse Translation-sq_AL
Ign [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-updates/multiverse Translation-sq
Ign [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-updates/restricted Translation-sq_AL
Ign [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-updates/restricted Translation-sq
Ign [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-updates/universe Translation-sq_AL
Ign [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-updates/universe Translation-sq
Ign [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-backports/main Translation-sq_AL
Ign [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-backports/main Translation-sq
Ign [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-backports/multiverse Translation-sq_AL
Ign [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-backports/multiverse Translation-sq
Ign [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-backports/restricted Translation-sq_AL
Ign [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-backports/restricted Translation-sq
Ign [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-backports/universe Translation-sq_AL
Ign [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-backports/universe Translation-sq
Ign [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-security/main Translation-sq_AL
Ign [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-security/main Translation-sq
Ign [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-security/multiverse Translation-sq_AL
Ign [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-security/multiverse Translation-sq
Ign [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-security/restricted Translation-sq_AL
Ign [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-security/restricted Translation-sq
Ign [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-security/universe Translation-sq_AL
Ign [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-security/universe Translation-sq
Ign [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-proposed/main Translation-sq_AL
Ign [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-proposed/main Translation-sq
Ign [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-proposed/multiverse Translation-sq_AL
Ign [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-proposed/multiverse Translation-sq
Ign [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-proposed/restricted Translation-sq_AL
Ign [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-proposed/restricted Translation-sq
Ign [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-proposed/universe Translation-sq_AL
Ign [http://al.archive.ubuntu.com](http://al.archive.ubuntu.com) quantal-proposed/universe Translation-sq
Fetched 133 kB in 37s (3.549 B/s)
W: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)/dists/oneiric/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)/dists/oneiric/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/Release.gpg](http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/Release.gpg)  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/apps/i18n/Translation-sq_AL](http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/apps/i18n/Translation-sq_AL)  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/apps/i18n/Translation-sq](http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/apps/i18n/Translation-sq)  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/apps/i18n/Translation-en](http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/apps/i18n/Translation-en)  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/apps/binary-i386/Packages](http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/apps/binary-i386/Packages)  Unable to connect to archive.getdeb.net:http:

E: Some index files failed to download. They have been ignored, or old ones used instead.
ervis@Aspire-5810T:~$
```

---

### Post by ibjsb4 on 2012-12-14
Ok, you need to do two things.  First:

Uncheck CDrom in your sources list.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab)

Second:

Getdeb is down.  You can for the moment just uncheck them in your software sources and wait for it to come back up.

[http://ubuntuforums.org/showthread.php?t=2088127](http://ubuntuforums.org/showthread.php?t=2088127)

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

---

### Post by albaniaguard on 2012-12-14
the frist i doing bat the 2 i cant :([http://yfrog.com/jxscreenshotfrom201212142p]("http://yfrog.com/jxscreenshotfrom201212142p")
in this mode is ok,i have problem in this mode?

---

### Post by ibjsb4 on 2012-12-14
It looks like you have unchecked the getdeb entries so you should be ok.  Go ahead and do another update.

```
sudo apt-get update
```If you get more errors about getdeb then you must find and uncheck those.  If you are not sure or you get different errors then please post and we will figure them out.

Any other questions?  Just ask  :)

---

### Post by albaniaguard on 2012-12-15
```
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal InRelease                      
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal InRelease                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal InRelease                      
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release.gpg [933 B]
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release.gpg [72 B]            
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal Release.gpg                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates InRelease              
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release [49,6 kB]  
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal Release                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release                                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security InRelease                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed InRelease                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports InRelease                      
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Sources                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Sources                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal Release.gpg                        
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal/partner i386 Packages        
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main i386 Packages [60,0 kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates Release.gpg [933 B]          
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security Release.gpg [933 B]           
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed Release.gpg [933 B]           
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted i386 Packages [14 B]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports Release.gpg [933 B]          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal Release                         
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates Release [49,6 kB]             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en      
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security Release [49,6 kB]   
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed Release [49,6 kB]            
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Translation-sq_AL             
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Translation-sq                
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports Release [49,6 kB]  
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Translation-en                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main i386 Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main Translation-sq
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-sq_AL
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-sq
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-sq_AL
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-sq
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe Translation-sq
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe Translation-en
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main i386 Packages [149 kB]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted i386 Packages [1.979 B]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe i386 Packages [132 kB]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse i386 Packages [8.106 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main Translation-en              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe Translation-en          
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/main i386 Packages [60,0 kB] 
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/restricted i386 Packages [14 B]
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/universe i386 Packages [21,0 kB]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/multiverse i386 Packages [1.391 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/main Translation-en             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/multiverse Translation-en       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/restricted Translation-en       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/universe Translation-en         
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/restricted i386 Packages [14 B]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/main i386 Packages [32,6 kB] 
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/multiverse i386 Packages [14 B]
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/universe i386 Packages [10,2 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/main Translation-en             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/multiverse Translation-en       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/restricted Translation-en       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/universe Translation-en         
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/restricted i386 Packages [14 B]
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/main i386 Packages [14 B]   
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/multiverse i386 Packages [14 B]
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/universe i386 Packages [5.306 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/main Translation-en            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/multiverse Translation-en      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/restricted Translation-en      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/universe Translation-en        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main Translation-sq_AL                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse Translation-sq_AL
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse Translation-sq
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted Translation-sq_AL
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted Translation-sq
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe Translation-sq_AL
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main Translation-sq_AL
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main Translation-sq
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse Translation-sq_AL
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse Translation-sq
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted Translation-sq_AL
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted Translation-sq
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe Translation-sq_AL
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe Translation-sq
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/main Translation-sq_AL
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/main Translation-sq
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/multiverse Translation-sq_AL
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/multiverse Translation-sq
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/restricted Translation-sq_AL
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/restricted Translation-sq
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/universe Translation-sq_AL
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/universe Translation-sq
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/main Translation-sq_AL
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/main Translation-sq
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/multiverse Translation-sq_AL
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/multiverse Translation-sq
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/restricted Translation-sq_AL
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/restricted Translation-sq
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/universe Translation-sq_AL
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/universe Translation-sq
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/main Translation-sq_AL
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/main Translation-sq
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/multiverse Translation-sq_AL
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/multiverse Translation-sq
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/restricted Translation-sq_AL
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/restricted Translation-sq
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/universe Translation-sq_AL
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/universe Translation-sq
Fetched 734 kB in 32s (22,7 kB/s)
Reading package lists... U Bë
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) quantal/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_quantal_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
```

now i think is ok,i dont have again this alert. Thanks :D

---

### Post by ibjsb4 on 2012-12-16
Congratulations  :)

But you got this "W: Duplicate sources.list entry".  No big deal, just means that its been entered twice in your sources.list.  So if you want a easy way to clean that up just uncheck "source code" in your software sources.  Source code is something that a developer uses or someone wanting to modify a software package.  So in your case it can be unchecked to solve the problem without any loss to you or your system.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab)

You then should be able to update without any error messages.

And then you can  :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by albaniaguard on 2012-12-16
thankyou vary much :D

---

