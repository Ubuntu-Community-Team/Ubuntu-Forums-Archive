---
title: "Update Prob Maybe Linked to gstreamer Plugin Prob"
date: 2015-02-22
forum: Installation &amp; Upgrades
---

### Post by gregory7 on 2015-02-22
Firstly I am getting an error on update

This happened when I was trying to fix a prob with Clementine which is unable to link to a radio station I want and came up with a gstreamer plugin missing. I looked for that and it seemed simple, just rename the registry file and it would generate a new one. And yet that failed and during the update required I saw the update prob and reckoned that maybe that was the problem??

---

### Post by sandyd on 2015-02-22
> **gregory7 said:**
> Firstly I am getting an error on update

This happened when I was trying to fix a prob with Clementine which is unable to link to a radio station I want and came up with a gstreamer plugin missing. I looked for that and it seemed simple, just rename the registry file and it would generate a new one. And yet that failed and during the update required I saw the update prob and reckoned that maybe that was the problem??

The error you are seeing is due to the fact that you added a PPA to Ubuntu - however that PPA does not have any software for trusty. As a result, it gives the error and is not related to the gstreamer error.

You can remove the PPA from Software Center -> Edit -> Software Sources.

If you create a thread in the Multimedia forums, you may get more help with your gstreamer issue :)

---

### Post by gregory7 on 2015-02-22
[ATTACH=CONFIG]260141[/ATTACH]

---

### Post by sandyd on 2015-02-22
> **gregory7 said:**
> Thanks, I think I did OK - I unticked all the options below Independent (see image) - Isn't this a bit risky? Should I remove them if they are not being maintained? Did I put them there? Last one probably, but therefore they might be needed for something...?

And now I shall go to multimedia to fix the gstreamer issue

You should only remove the one that is causing the error, should show up in the list as
```

deb http://ppa.launchpad.net/pmcenery/ppa/ubuntu
deb-src http://ppa.launchpad.net/pmcenery/ppa/ubuntu
```

---

### Post by gregory7 on 2015-02-22
Let's try that reply again!

Thanks for your help - :)

I have unticked everything as in the image attached

Is that safe? Why would they be ticked if they needn't be?

---

### Post by gregory7 on 2015-02-22
> **sandyd said:**
> You should only remove the one that is causing the error, should show up in the list as
```

deb http://ppa.launchpad.net/pmcenery/ppa/ubuntu
deb-src http://ppa.launchpad.net/pmcenery/ppa/ubuntu
```

Ah! OK just a sec :)

---

### Post by gregory7 on 2015-02-22
OK, I got a failure message about downloading certain files:

E:Could not open file /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_trusty_main_binary-i386_Packages - open (2: No such file or directory), E:Could not open file /var/lib/apt/lists/ubuntu.uestc.edu.cn_ubuntu_dists_trusty_multiverse_i18n_Translation-en%5fGB - open (2: No such file or directory), E:Could not open file /var/lib/apt/lists/ubuntu.uestc.edu.cn_ubuntu_dists_trusty_multiverse_i18n_Translation-en - open (2: No such file or directory), E:Could not open file /var/lib/apt/lists/ubuntu.uestc.edu.cn_ubuntu_dists_trusty_main_i18n_Translation-en%5fGB - open (2: No such file or directory), E:Could not open file /var/lib/apt/lists/ubuntu.uestc.edu.cn_ubuntu_dists_trusty_main_i18n_Translation-en - open (2: No such file or directory), E:Could not open file /var/lib/apt/lists/ubuntu.uestc.edu.cn_ubuntu_dists_trusty_multiverse_binary-i386_Packages - open (2: No such file or directory), E:Could not open file /var/lib/apt/lists/ubuntu.uestc.edu.cn_ubuntu_dists_trusty_universe_binary-i386_Packages - open (2: No such file or directory), E:Could not open file /var/lib/apt/lists/ubuntu.uestc.edu.cn_ubuntu_dists_trusty_restricted_binary-i386_Packages - open (2: No such file or directory), E:Could not open file /var/lib/apt/lists/ubuntu.uestc.edu.cn_ubuntu_dists_trusty_main_binary-i386_Packages - open (2: No such file or directory)

Is this usual? Maybe I need to restart?

---

### Post by sandyd on 2015-02-22
That's not normal, you have something odd in your sources

Did you do an upgrade to Trusty by any chance?

Whats the output of
```

cat /etc/apt/sources.list
tail -n +1 -- /etc/apt/sources.list.d/*
```

---

### Post by gregory7 on 2015-02-22
> **sandyd said:**
> That's not normal, you have something odd in your sources

Did you do an upgrade to Trusty by any chance?

Whats the output of
```

cat /etc/apt/sources.list
tail -n +1 -- /etc/apt/sources.list.d/*
```

OK, thanks again for yr time :)

I put this in terminal yes?

greg@greg-Inspiron-9300:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to

# newer versions of the distribution.
deb [http://ubuntu.uestc.edu.cn/ubuntu/](http://ubuntu.uestc.edu.cn/ubuntu/) trusty main restricted
deb-src [http://ubuntu.uestc.edu.cn/ubuntu/](http://ubuntu.uestc.edu.cn/ubuntu/) trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntu.uestc.edu.cn/ubuntu/](http://ubuntu.uestc.edu.cn/ubuntu/) trusty-updates main restricted
deb-src [http://ubuntu.uestc.edu.cn/ubuntu/](http://ubuntu.uestc.edu.cn/ubuntu/) trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ubuntu.uestc.edu.cn/ubuntu/](http://ubuntu.uestc.edu.cn/ubuntu/) trusty universe
deb-src [http://ubuntu.uestc.edu.cn/ubuntu/](http://ubuntu.uestc.edu.cn/ubuntu/) trusty universe
deb [http://ubuntu.uestc.edu.cn/ubuntu/](http://ubuntu.uestc.edu.cn/ubuntu/) trusty-updates universe
deb-src [http://ubuntu.uestc.edu.cn/ubuntu/](http://ubuntu.uestc.edu.cn/ubuntu/) trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ubuntu.uestc.edu.cn/ubuntu/](http://ubuntu.uestc.edu.cn/ubuntu/) trusty multiverse
deb-src [http://ubuntu.uestc.edu.cn/ubuntu/](http://ubuntu.uestc.edu.cn/ubuntu/) trusty multiverse
deb [http://ubuntu.uestc.edu.cn/ubuntu/](http://ubuntu.uestc.edu.cn/ubuntu/) trusty-updates multiverse
deb-src [http://ubuntu.uestc.edu.cn/ubuntu/](http://ubuntu.uestc.edu.cn/ubuntu/) trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ubuntu.uestc.edu.cn/ubuntu/](http://ubuntu.uestc.edu.cn/ubuntu/) trusty-backports main restricted universe multiverse
deb-src [http://ubuntu.uestc.edu.cn/ubuntu/](http://ubuntu.uestc.edu.cn/ubuntu/) trusty-backports main restricted universe multiverse

deb [http://ubuntu.uestc.edu.cn/ubuntu/](http://ubuntu.uestc.edu.cn/ubuntu/) trusty-security main restricted
deb-src [http://ubuntu.uestc.edu.cn/ubuntu/](http://ubuntu.uestc.edu.cn/ubuntu/) trusty-security main restricted
deb [http://ubuntu.uestc.edu.cn/ubuntu/](http://ubuntu.uestc.edu.cn/ubuntu/) trusty-security universe
deb-src [http://ubuntu.uestc.edu.cn/ubuntu/](http://ubuntu.uestc.edu.cn/ubuntu/) trusty-security universe
deb [http://ubuntu.uestc.edu.cn/ubuntu/](http://ubuntu.uestc.edu.cn/ubuntu/) trusty-security multiverse
deb-src [http://ubuntu.uestc.edu.cn/ubuntu/](http://ubuntu.uestc.edu.cn/ubuntu/) trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
greg@greg-Inspiron-9300:~$ tail -n +1 -- /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/atareao-atareao-trusty.list <==
deb [http://ppa.launchpad.net/atareao/atareao/ubuntu](http://ppa.launchpad.net/atareao/atareao/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/atareao/atareao/ubuntu](http://ppa.launchpad.net/atareao/atareao/ubuntu) trusty main

==> /etc/apt/sources.list.d/atareao-atareao-trusty.list.save <==
# deb [http://ppa.launchpad.net/atareao/atareao/ubuntu](http://ppa.launchpad.net/atareao/atareao/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/atareao/atareao/ubuntu](http://ppa.launchpad.net/atareao/atareao/ubuntu) trusty main

==> /etc/apt/sources.list.d/diesch-testing-trusty.list <==
deb [http://ppa.launchpad.net/diesch/testing/ubuntu](http://ppa.launchpad.net/diesch/testing/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/diesch/testing/ubuntu](http://ppa.launchpad.net/diesch/testing/ubuntu) trusty main

==> /etc/apt/sources.list.d/diesch-testing-trusty.list.save <==
deb [http://ppa.launchpad.net/diesch/testing/ubuntu](http://ppa.launchpad.net/diesch/testing/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/diesch/testing/ubuntu](http://ppa.launchpad.net/diesch/testing/ubuntu) trusty main

==> /etc/apt/sources.list.d/mc3man-trusty-media-trusty.list <==
deb [http://ppa.launchpad.net/mc3man/trusty-media/ubuntu](http://ppa.launchpad.net/mc3man/trusty-media/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/mc3man/trusty-media/ubuntu](http://ppa.launchpad.net/mc3man/trusty-media/ubuntu) trusty main

==> /etc/apt/sources.list.d/mc3man-trusty-media-trusty.list.save <==
deb [http://ppa.launchpad.net/mc3man/trusty-media/ubuntu](http://ppa.launchpad.net/mc3man/trusty-media/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/mc3man/trusty-media/ubuntu](http://ppa.launchpad.net/mc3man/trusty-media/ubuntu) trusty main

==> /etc/apt/sources.list.d/pinta-maintainers-pinta-daily-trusty.list <==
deb [http://ppa.launchpad.net/pinta-maintainers/pinta-daily/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-daily/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/pinta-maintainers/pinta-daily/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-daily/ubuntu) trusty main

==> /etc/apt/sources.list.d/pinta-maintainers-pinta-daily-trusty.list.save <==
deb [http://ppa.launchpad.net/pinta-maintainers/pinta-daily/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-daily/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/pinta-maintainers/pinta-daily/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-daily/ubuntu) trusty main

==> /etc/apt/sources.list.d/pmcenery-ppa-trusty.list <==
# deb [http://ppa.launchpad.net/pmcenery/ppa/ubuntu](http://ppa.launchpad.net/pmcenery/ppa/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/pmcenery/ppa/ubuntu](http://ppa.launchpad.net/pmcenery/ppa/ubuntu) trusty main

==> /etc/apt/sources.list.d/pmcenery-ppa-trusty.list.save <==
# deb [http://ppa.launchpad.net/pmcenery/ppa/ubuntu](http://ppa.launchpad.net/pmcenery/ppa/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/pmcenery/ppa/ubuntu](http://ppa.launchpad.net/pmcenery/ppa/ubuntu) trusty main
greg@greg-Inspiron-9300:~$

!!!!! :confused:

---

### Post by sandyd on 2015-02-22
Can you post the entire output of```
sudo apt-get update
```

Something is still not getting downloaded.

---

### Post by gregory7 on 2015-02-22
sudo apt-get update
[sudo] password for greg: 
Ign [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty InRelease
Ign [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty-updates InRelease                        
Ign [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty-backports InRelease                      
Ign [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty-security InRelease                       
Hit [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty Release.gpg                              
Get:1 [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty-updates Release.gpg [933 B]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                              
Get:2 [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty-backports Release.gpg [933 B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                               
Hit [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty-security Release.gpg           
Hit [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty Release                        
Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg [72 B]                       
Get:4 [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty-updates Release [62.0 kB]              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Get:5 [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty-backports Release [62.0 kB]   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                              
Hit [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty-security Release                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty/main Sources                             
Hit [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty/restricted Sources                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Hit [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty/universe Sources                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty/multiverse Sources                       
Hit [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty/main i386 Packages                       
Hit [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty/restricted i386 Packages                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty/universe i386 Packages                   
Hit [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty/multiverse i386 Packages                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty/main Translation-en_GB                   
Hit [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty/main Translation-en                      
Hit [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty/multiverse Translation-en_GB             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty/multiverse Translation-en                
Hit [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty/restricted Translation-en_GB             
Hit [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty/restricted Translation-en                
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg [316 B]                      
Hit [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty/universe Translation-en_GB               
Hit [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty/universe Translation-en                  
Get:7 [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty-updates/main Sources [179 kB]          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Get:8 [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty-updates/restricted Sources [2,061 B]   
Get:9 [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty-updates/universe Sources [104 kB]      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Get:10 [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty-updates/multiverse Sources [4,463 B]  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Get:11 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release [15.1 kB]                       
Get:12 [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty-updates/main i386 Packages [431 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Get:13 [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty-updates/restricted i386 Packages [8,846 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Get:14 [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty-updates/universe i386 Packages [253 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Get:15 [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty-updates/multiverse i386 Packages [11.3 kB]
Hit [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty-updates/main Translation-en              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty-updates/multiverse Translation-en        
Hit [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty-updates/restricted Translation-en        
Hit [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty-updates/universe Translation-en          
Get:16 [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty-backports/main Sources [5,298 B]      
Get:17 [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty-backports/restricted Sources [28 B]   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Get:18 [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty-backports/universe Sources [20.0 kB]  
Get:19 [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty-backports/multiverse Sources [1,898 B]
Get:20 [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty-backports/main i386 Packages [5,550 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Get:21 [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty-backports/restricted i386 Packages [28 B]
Get:22 [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty-backports/universe i386 Packages [24.1 kB]
Get:23 [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty-backports/multiverse i386 Packages [1,249 B]
Hit [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty-backports/main Translation-en
Get:24 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages [620 B]  
Hit [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty-backports/multiverse Translation-en
Hit [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty-backports/restricted Translation-en
Hit [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty-backports/universe Translation-en
Get:25 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en [376 B] 
Hit [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty-security/main Sources        
Hit [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty-security/restricted Sources  
Hit [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty-security/universe Sources    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages             
Hit [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty-security/multiverse Sources  
Hit [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty-security/main i386 Packages  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en            
Hit [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty-security/restricted i386 Packages        
Hit [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty-security/universe i386 Packages          
Hit [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty-security/multiverse i386 Packages        
Hit [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty-security/main Translation-en             
Hit [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty-security/multiverse Translation-en       
Hit [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty-security/restricted Translation-en       
Hit [http://ubuntu.uestc.edu.cn](http://ubuntu.uestc.edu.cn) trusty-security/universe Translation-en         
Fetched 1,195 kB in 14s (84.0 kB/s)                                            
Reading package lists... Done


Seems fine eh?

Thanks again for your time, much appreciated :)

---

### Post by sandyd on 2015-02-23
Seems fine, seems software sources was just confusing itself :)

Which gstreamer plugin are you having issues with?

---

### Post by gregory7 on 2015-02-23
> **sandyd said:**
> Seems fine, seems software sources was just confusing itself :)

Which gstreamer plugin are you having issues with?

It won't tell me - it just says: "Gstreamer installation missing plugin" without any details. I have started the thread as you suggested in multimedia, but I cannot find a way to identify which plugin is missing :(

---

