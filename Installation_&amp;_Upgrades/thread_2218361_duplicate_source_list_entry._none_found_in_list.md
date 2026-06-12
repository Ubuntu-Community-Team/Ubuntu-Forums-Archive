---
title: "duplicate source list entry. none found in list"
date: 2014-04-20
forum: Installation &amp; Upgrades
---

### Post by R3linquish3r on 2014-04-20
hello I just updated my laptop from 13.10 to 14.04 and after upgrading when i run apt-get update I get this error:
```
ed@ed-NV55C:~$ sudo apt-get update
[sudo] password for ed: 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
Hit [http://repository.spotify.com](http://repository.spotify.com) stable InRelease                             
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release.gpg [933 B]          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release.gpg                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release                                
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                            
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release [58.5 kB]            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg                     
Hit [http://repository.spotify.com](http://repository.spotify.com) stable/non-free i386 Packages                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources                           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources                       
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages               
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en                
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources [1,712 B]       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages        
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources [14 B]    
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources [648 B]     
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources [1,790 B] 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages          
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages [2,998 B] 
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages [14 B]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages [1,601 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages        
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [6,386 B]
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en_US            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en            
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en_US              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources    
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en_US
Fetched 74.6 kB in 3s (20.4 kB/s)
Reading package lists... Done
W: Duplicate sources.list entry [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/restricted i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_trusty_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/main i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_trusty_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/multiverse i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_trusty_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/universe i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_trusty_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
```

I have looked through my sources.list multiple times and unless im blind (which could be possible) I dont see any duplicates or even the line listed.

```
ed@ed-NV55C:~$ find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;

/etc/apt/sources.list

     1	# deb cdrom:[Ubuntu 14.04 LTS _Trusty Tahr_ - Release i386 (20140417)]/ trusty main restricted
     2	# deb cdrom:[Ubuntu 13.10 _Saucy Salamander_ - Release i386 (20131016.1)]/ saucy main restricted
     3	# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release i386 (20130820.1)]/ precise main restricted
     4	# deb cdrom:[Ubuntu 14.04 LTS _Trusty Tahr_ - Release i386 (20140417)]/ trusty main restricted
     5	
     6	# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     7	# newer versions of the distribution.
     8	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted
     9	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted
    10	
    11	## Major bug fix updates produced after the final release of the
    12	## distribution.
    13	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
    14	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
    15	
    16	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    17	## team. Also, please note that software in universe WILL NOT receive any
    18	## review or updates from the Ubuntu security team.
    19	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty universe
    20	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty universe
    21	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates universe
    22	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates universe
    23	
    24	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    25	## team, and may not be under a free licence. Please satisfy yourself as to 
    26	## your rights to use the software. Also, please note that software in 
    27	## multiverse WILL NOT receive any review or updates from the Ubuntu
    28	## security team.
    29	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty multiverse
    30	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty multiverse
    31	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
    32	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
    33	
    34	## N.B. software from this repository may not have been tested as
    35	## extensively as that contained in the main release, although it includes
    36	## newer versions of some applications which may provide useful features.
    37	## Also, please note that software in backports WILL NOT receive any review
    38	## or updates from the Ubuntu security team.
    39	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
    40	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
    41	
    42	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
    43	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
    44	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
    45	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
    46	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
    47	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
    48	
    49	## Uncomment the following two lines to add software from Canonical's
    50	## 'partner' repository.
    51	## This software is not part of Ubuntu, but is offered by Canonical and the
    52	## respective vendors as a service to Ubuntu users.
    53	deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
    54	deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
    55	
    56	## This software is not part of Ubuntu, but is offered by third-party
    57	## developers who want to ship their latest software.
    58	deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
    59	deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
    60	
    61	# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
    62	# newer versions of the distribution.
    63	
    64	## Major bug fix updates produced after the final release of the
    65	## distribution.
    66	
    67	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    68	## team. Also, please note that software in universe WILL NOT receive any
    69	## review or updates from the Ubuntu security team.
    70	
    71	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    72	## team, and may not be under a free licence. Please satisfy yourself as to 
    73	## your rights to use the software. Also, please note that software in 
    74	## multiverse WILL NOT receive any review or updates from the Ubuntu
    75	## security team.
    76	
    77	## N.B. software from this repository may not have been tested as
    78	## extensively as that contained in the main release, although it includes
    79	## newer versions of some applications which may provide useful features.
    80	## Also, please note that software in backports WILL NOT receive any review
    81	## or updates from the Ubuntu security team.
    82	
    83	
    84	## Uncomment the following two lines to add software from Canonical's
    85	## 'partner' repository.
    86	## This software is not part of Ubuntu, but is offered by Canonical and the
    87	## respective vendors as a service to Ubuntu users.
    88	# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) saucy partner
    89	# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) saucy partner
    90	
    91	## This software is not part of Ubuntu, but is offered by third-party
    92	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty restricted main multiverse universe
    93	## developers who want to ship their latest software.
    94	deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free
    95	
    96	# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
    97	# newer versions of the distribution.
    98	
    99	## Major bug fix updates produced after the final release of the
   100	## distribution.
   101	
   102	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
   103	## team. Also, please note that software in universe WILL NOT receive any
   104	## review or updates from the Ubuntu security team.
   105	
   106	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
   107	## team, and may not be under a free licence. Please satisfy yourself as to 
   108	## your rights to use the software. Also, please note that software in 
   109	## multiverse WILL NOT receive any review or updates from the Ubuntu
   110	## security team.
   111	
   112	## N.B. software from this repository may not have been tested as
   113	## extensively as that contained in the main release, although it includes
   114	## newer versions of some applications which may provide useful features.
   115	## Also, please note that software in backports WILL NOT receive any review
   116	## or updates from the Ubuntu security team.
   117	
   118	
   119	## Uncomment the following two lines to add software from Canonical's
   120	## 'partner' repository.
   121	## This software is not part of Ubuntu, but is offered by Canonical and the
   122	## respective vendors as a service to Ubuntu users.
   123	# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
   124	# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
   125	
   126	## This software is not part of Ubuntu, but is offered by third-party
   127	## developers who want to ship their latest software.
   128	
   129	# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
   130	# newer versions of the distribution.
   131	
   132	## Major bug fix updates produced after the final release of the
   133	## distribution.
   134	
   135	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
   136	## team. Also, please note that software in universe WILL NOT receive any
   137	## review or updates from the Ubuntu security team.
   138	
   139	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
   140	## team, and may not be under a free licence. Please satisfy yourself as to 
   141	## your rights to use the software. Also, please note that software in 
   142	## multiverse WILL NOT receive any review or updates from the Ubuntu
   143	## security team.
   144	
   145	## N.B. software from this repository may not have been tested as
   146	## extensively as that contained in the main release, although it includes
   147	## newer versions of some applications which may provide useful features.
   148	## Also, please note that software in backports WILL NOT receive any review
   149	## or updates from the Ubuntu security team.
   150	
   151	
   152	## Uncomment the following two lines to add software from Canonical's
   153	## 'partner' repository.
   154	## This software is not part of Ubuntu, but is offered by Canonical and the
   155	## respective vendors as a service to Ubuntu users.
   156	# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
   157	# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
   158	
   159	## This software is not part of Ubuntu, but is offered by third-party
   160	## developers 

```
Id hate to ask someone to do my proof reading for me but I cannot find any duplicates and this error on a fresh install is really tickin me off. if theres an extra line im not seeing, or something different i have to do to correct this error, I would love to find out what it is if anyone can help me out with this problem.

---

### Post by R3linquish3r on 2014-04-20
heres a slightly more compact soruces.list without all that extra text: 
```
# deb cdrom:[Ubuntu 14.04 LTS _Trusty Tahr_ - Release i386 (20140417)]/ trusty main restricted
# deb cdrom:[Ubuntu 13.10 _Saucy Salamander_ - Release i386 (20131016.1)]/ saucy main restricted
# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release i386 (20130820.1)]/ precise main restricted
# deb cdrom:[Ubuntu 14.04 LTS _Trusty Tahr_ - Release i386 (20140417)]/ trusty main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates multiverse


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner

deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main

# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) saucy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) saucy partner

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty restricted main multiverse universe

deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free


```

I don't even see the trust/restricted or multiverse error lines in that list

---

### Post by Bashing-om on 2014-04-20
R3linquish3r; Hi !

Sorry, I had responded much earlier, but guess I did not hit the "submit reply" button !

Any way.

Maybe, take a look in the 3rd party sources directory.
```

cat /etc/apt/sources.list.d/*.list

```
for a quick looksee.

[INDENT][INDENT]'nother path to that end
[/INDENT][/INDENT]

---

### Post by R3linquish3r on 2014-04-20
nothing there at all

> ed@ed-NV55C:~$ cat /etc/apt/sources.list.d/*.list
cat: /etc/apt/sources.list.d/*.list: No such file or directory


Just opened the folder and its empty

---

### Post by bapoumba on 2014-04-20
> **R3linquish3r said:**
> heres a slightly more compact soruces.list without all that extra text: 
```
# deb cdrom:[Ubuntu 14.04 LTS _Trusty Tahr_ - Release i386 (20140417)]/ trusty main restricted
# deb cdrom:[Ubuntu 13.10 _Saucy Salamander_ - Release i386 (20131016.1)]/ saucy main restricted
# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release i386 (20130820.1)]/ precise main restricted
# deb cdrom:[Ubuntu 14.04 LTS _Trusty Tahr_ - Release i386 (20140417)]/ trusty main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates multiverse


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner

deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main

# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) saucy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) saucy partner

**[COLOR="#00FF00"]deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty restricted main multiverse universe[/COLOR]**

deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free


```

I don't even see the trust/restricted or multiverse error lines in that list
As far as I can see, last bold green line is a dup of the above ones that appear in 3 different places.

---

### Post by R3linquish3r on 2014-04-20
That was it! I never thought that having all that in one source would link them all together like that

---

### Post by bapoumba on 2014-04-20
> **R3linquish3r said:**
> That was it! I never thought that having all that in one source would link them all together like that

Well, yes, technically they appeared twice :)
Please mark your thread as solved (in Thread Tools), thanks!

---

### Post by Bashing-om on 2014-04-20
R3linquish3r, Yep
+1 bapoumba !

The line;
> 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty restricted main multiverse universe

You have once more enabled 4 repositories for trusty : restricted, main, multiverse, and  universe.

For your reference:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

[INDENT][INDENT]but it's an easy fix
[/INDENT][/INDENT]

---

