---
title: "Software Update - the package system is broken error"
date: 2015-07-20
forum: Installation &amp; Upgrades
---

### Post by ray_silva on 2015-07-20
Can anyone please help me.

I'm running 14.04 LTS

It was running fine, then I tried to install emby media server.

I had to manually add the repository, but even that got an error while installing.

I tried to get help in the emby forum - not blaming them; I'm guessing something was wrong with the repository server at the time.

Anyway, I slogged on with the installation, expecting some errors but figuring that a software update would later catch and fix the unmet dependencies.

Well, bottom line is that now my package system is broken.

Does anyone know how I can go about cleaning and fixing it back to before I messed it up?

---

### Post by Bashing-om on 2015-07-20
ray_silva; Sure !

Let's look and see what the sources are. Then we have an idea of what to do to make the package manager happy:
please post back the outputs - Between Code Tags, Please - of terminal commands:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by ray_silva on 2015-07-20
Do you want me to paste it right on my post? It's a little long.

---

### Post by v3.xx on 2015-07-20
Hey Bashing, whats going on :)

I would like to see what errors a update puts out (if your sources check out).
```
sudo apt-get update
```

---

### Post by PaulW2U on 2015-07-20
> **ray_silva said:**
> Do you want me to paste it right on my post? It's a little long.

The length of the output won't matter if you use code tags.

If you are using New Reply button - highlight text and use the # button in the text box header. If you are using Quick Reply then add [noparse]```
 at the beginning of the section and 
```[/noparse] at the end.

---

### Post by ray_silva on 2015-07-20
```
ray@ray-OptiPlex-GX280:~$ sudo apt-get update
[sudo] password for ray: 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg                     
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release                         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Ign [http://download.opensuse.org](http://download.opensuse.org)  InRelease                                    
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release.gpg [933 B]          
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) precise InRelease                               
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release [63.5 kB]            
Hit [http://download.opensuse.org](http://download.opensuse.org)  Release.gpg                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages          
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en         
Hit [http://download.opensuse.org](http://download.opensuse.org)  Release                                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) precise/main i386 Packages                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                 
Hit [http://download.opensuse.org](http://download.opensuse.org)  Packages                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages [555 kB]  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                               
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages [296 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en            
Ign [http://download.opensuse.org](http://download.opensuse.org)  Translation-en_US                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Ign [http://download.opensuse.org](http://download.opensuse.org)  Translation-en                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) precise/main Translation-en_US                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) precise/main Translation-en                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en             
Fetched 916 kB in 8s (109 kB/s)                                                
Reading package lists... Done
W: Duplicate sources.list entry [http://download.opensuse.org/repositories/home:/emby/xUbuntu_14.04/](http://download.opensuse.org/repositories/home:/emby/xUbuntu_14.04/)  Packages (/var/lib/apt/lists/download.opensuse.org_repositories_home:_emby_xUbuntu%5f14.04_Packages)
W: You may want to run apt-get update to correct these problems
ray@ray-OptiPlex-GX280:~$

```

---

### Post by ray_silva on 2015-07-20
Sorry, I did that before I read about using the ```

``` block

---

### Post by ray_silva on 2015-07-20
```

ray@ray-OptiPlex-GX280:~$ cat -n /etc/apt/sources.list
     1    # deb cdrom:[Ubuntu 12.04.4 LTS _Precise Pangolin_ - Release i386 (20140204)]/ precise main restricted
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://us.archive.ubuntu.com/ubuntu/ trusty main
     6    
     7    ## Major bug fix updates produced after the final release of the
     8    ## distribution.
     9    deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main
    10    
    11    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    12    ## team. Also, please note that software in universe WILL NOT receive any
    13    ## review or updates from the Ubuntu security team.
    14    deb http://us.archive.ubuntu.com/ubuntu/ trusty universe
    15    deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
    16    
    17    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    18    ## team, and may not be under a free licence. Please satisfy yourself as to 
    19    ## your rights to use the software. Also, please note that software in 
    20    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    21    ## security team.
    22    
    23    ## N.B. software from this repository may not have been tested as
    24    ## extensively as that contained in the main release, although it includes
    25    ## newer versions of some applications which may provide useful features.
    26    ## Also, please note that software in backports WILL NOT receive any review
    27    ## or updates from the Ubuntu security team.
    28    
    29    deb http://security.ubuntu.com/ubuntu trusty-security main
    30    deb http://security.ubuntu.com/ubuntu trusty-security universe
    31    
    32    ## Uncomment the following two lines to add software from Canonical's
    33    ## 'partner' repository.
    34    ## This software is not part of Ubuntu, but is offered by Canonical and the
    35    ## respective vendors as a service to Ubuntu users.
    36    deb http://archive.canonical.com/ubuntu trusty partner
    37    # deb-src http://archive.canonical.com/ubuntu precise partner
    38    
    39    ## This software is not part of Ubuntu, but is offered by third-party
    40    ## developers who want to ship their latest software.
    41    deb http://extras.ubuntu.com/ubuntu trusty main
    42    # deb-src http://extras.ubuntu.com/ubuntu trusty main
    43    # deb http://repo.acestream.org/ubuntu trusty main
ray@ray-OptiPlex-GX280:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/caffeine-developers-ppa-trusty.list <==
deb http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu trusty main
deb-src http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/caffeine-developers-ppa-trusty.list.save <==
deb http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu trusty main
deb-src http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/emby-server.list <==
# deb http://download.opensuse.org/repositories/home:/emby/{Repository}/ /
# deb http://download.opensuse.org/repositories/home:/emby/xUbuntu_14.04/ /
deb http://download.opensuse.org/repositories/home:/emby/xUbuntu_14.04/ /
deb http://download.opensuse.org/repositories/home:/emby/xUbuntu_14.04/ /

==> /etc/apt/sources.list.d/emby-server.list.save <==
deb http://download.opensuse.org/repositories/home:/emby/{Repository}/ /
# deb http://download.opensuse.org/repositories/home:/emby/xUbuntu_14.04/ /

==> /etc/apt/sources.list.d/kirillshkrogalev-ffmpeg-next-trusty.list <==
# deb http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu trusty main
# deb-src http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu trusty main

==> /etc/apt/sources.list.d/kirillshkrogalev-ffmpeg-next-trusty.list.save <==
# deb http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu trusty main
# deb-src http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu trusty main

==> /etc/apt/sources.list.d/playonlinux.list <==
deb http://deb.playonlinux.com/ precise main

==> /etc/apt/sources.list.d/playonlinux.list.save <==
deb http://deb.playonlinux.com/ precise main

==> /etc/apt/sources.list.d/team-xbmc-ppa-trusty.list <==
deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu trusty main
deb-src http://ppa.launchpad.net/team-xbmc/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/team-xbmc-ppa-trusty.list.save <==
deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu trusty main
deb-src http://ppa.launchpad.net/team-xbmc/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/team-xbmc-xbmc-nightly-precise.list <==
deb http://ppa.launchpad.net/team-xbmc/xbmc-nightly/ubuntu trusty main # disabled on upgrade to trusty
# deb-src http://ppa.launchpad.net/team-xbmc/xbmc-nightly/ubuntu trusty main # disabled on upgrade to trusty

==> /etc/apt/sources.list.d/team-xbmc-xbmc-nightly-precise.list.distUpgrade <==
deb http://ppa.launchpad.net/team-xbmc/xbmc-nightly/ubuntu precise main
deb-src http://ppa.launchpad.net/team-xbmc/xbmc-nightly/ubuntu precise main

==> /etc/apt/sources.list.d/team-xbmc-xbmc-nightly-precise.list.save <==
deb http://ppa.launchpad.net/team-xbmc/xbmc-nightly/ubuntu trusty main # disabled on upgrade to trusty
# deb-src http://ppa.launchpad.net/team-xbmc/xbmc-nightly/ubuntu trusty main # disabled on upgrade to trusty

==> /etc/apt/sources.list.d/xorg-edgers-ppa-trusty.list <==
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/xorg-edgers-ppa-trusty.list.save <==
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu trusty main

```

---

### Post by v3.xx on 2015-07-20
Post#6

> W: Duplicate sources.list entry [http://download.opensuse.org/reposit...xUbuntu_14.04/](http://download.opensuse.org/reposit...xUbuntu_14.04/)  Packages (/var/lib/apt/lists/download.opensuse.org_repositories_home:_emby_xUbuntu%5f14.04_Packages)

Open up your sources list and remove the duplicate.

```
software-properties-gtk
```

---

### Post by Bashing-om on 2015-07-20
ray_silva;

Hey v3.xx :) ; always a pleasure in any event .

@ray_silva; UH oh ! In addition to the ups, does not appear that "emby" is supported in release 14.04 for ubuntu !
per:
[http://download.opensuse.org/repositories/Ubuntu:/](http://download.opensuse.org/repositories/Ubuntu:/)
12.10 was the last supported release.
It is now back to the package maintainers to see what they are going to do . ( do you really really really want to mix archives ?? - opensusie)

[INDENT][INDENT]if it ain't there
[INDENT][INDENT]it just ain't there
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ray_silva on 2015-07-20
everything seems now removed from the sources that was duplicated, but when the updates reload it still shows the vlc Direct Media Player and fails to update it.

---

### Post by ray_silva on 2015-07-20
Yeah, I didn't find any info at the emby site or forum on lack of support for 14.04. Maybe I should just remove it completely. What's the best quick way to do that since it was done from repository and I don't know what else it installed?

---

### Post by ray_silva on 2015-07-20
Thanks...it's such a different experience getting help on Ubuntu forums compared to the Microsoft one.

---

### Post by Bashing-om on 2015-07-20
ray_silva; Hey ;

> **ray_silva said:**
> Thanks...it's such a different experience getting help on Ubuntu forums compared to the Microsoft one.

Open source, we do what we can to take care of one another.
Now at the risk of getting a slap on the wrist - because I respond and can add nothing positive to the thread - /
> 
Maybe I should just remove it completely. What's the best quick way to do that since it was done from repository and I don't know what else it installed?

I can not advise directly. Did the installer perhaps also provide a UN-install script ?
Be aware, it is never ever acceptable to go behind the package manager's back IF the manager is aware of the existence of some package. Proper procedure should be observed or breakage will ensue . Sometimes in the case of foreign sotware, finding the proper procedure can be a real pain.

[INDENT][INDENT]but.
[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ray_silva on 2015-07-20
Thanks, I will observe that...

---

### Post by ray_silva on 2015-08-15
Sorry, I thought I had this fixed, but it's probably worse than ever. I can post the results of the 
```

cat -n /etc/apt/sources.list tail -v -n +1 /etc/apt/sources.list.d/*
</block>
again, if you could help me...
Here it is:
<block>
       1	# deb cdrom:[Ubuntu 12.04.4 LTS _Precise Pangolin_ - Release i386 (20140204)]/ precise main restricted 
      2	 
      3	# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to 
      4	# newer versions of the distribution. 
      5	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main 
      6	 
      7	## Major bug fix updates produced after the final release of the 
      8	## distribution. 
      9	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates main 
     10	 
     11	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
     12	## team. Also, please note that software in universe WILL NOT receive any 
     13	## review or updates from the Ubuntu security team. 
     14	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty universe 
     15	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates universe 
     16	 
     17	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu  
     18	## team, and may not be under a free licence. Please satisfy yourself as to  
     19	## your rights to use the software. Also, please note that software in  
     20	## multiverse WILL NOT receive any review or updates from the Ubuntu 
     21	## security team. 
     22	 
     23	## N.B. software from this repository may not have been tested as 
     24	## extensively as that contained in the main release, although it includes 
     25	## newer versions of some applications which may provide useful features. 
     26	## Also, please note that software in backports WILL NOT receive any review 
     27	## or updates from the Ubuntu security team. 
     28	 
     29	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main 
     30	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe 
     31	 
     32	## Uncomment the following two lines to add software from Canonical's 
     33	## 'partner' repository. 
     34	## This software is not part of Ubuntu, but is offered by Canonical and the 
     35	## respective vendors as a service to Ubuntu users. 
     36	deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner 
     37	# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner 
     38	 
     39	## This software is not part of Ubuntu, but is offered by third-party 
     40	## developers who want to ship their latest software. 
     41	# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main 
     42	# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main 
     43	# deb [http://repo.acestream.org/ubuntu](http://repo.acestream.org/ubuntu) trusty main 
 ray@ray-OptiPlex-GX280:~$ tail -v -n +1 /etc/apt/sources.list.d/* 
 ==> /etc/apt/sources.list.d/caffeine-developers-ppa-trusty.list <== 
 # deb [http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu](http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu) trusty main 
 # deb-src [http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu](http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu) trusty main 
  
 ==> /etc/apt/sources.list.d/caffeine-developers-ppa-trusty.list.save <== 
 # deb [http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu](http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu) trusty main 
 # deb-src [http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu](http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu) trusty main 
  
 ==> /etc/apt/sources.list.d/emby-server.list <== 
 # deb [http://download.opensuse.org/repositories/home:/emby/xUbuntu_14.04/](http://download.opensuse.org/repositories/home:/emby/xUbuntu_14.04/) / 
 deb http://download.opensuse.org/repositories/home:/emby/{Repository}/ / 
  
 ==> /etc/apt/sources.list.d/emby-server.list.save <== 
 # deb [http://download.opensuse.org/repositories/home:/emby/xUbuntu_14.04/](http://download.opensuse.org/repositories/home:/emby/xUbuntu_14.04/) / 
  
 ==> /etc/apt/sources.list.d/kirillshkrogalev-ffmpeg-next-trusty.list <== 
 # deb [http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu](http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu) trusty main 
 # deb-src [http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu](http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu) trusty main 
  
 ==> /etc/apt/sources.list.d/kirillshkrogalev-ffmpeg-next-trusty.list.save <== 
 # deb [http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu](http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu) trusty main 
 # deb-src [http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu](http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu) trusty main 
  
 ==> /etc/apt/sources.list.d/playonlinux.list <== 
 # deb [http://deb.playonlinux.com/](http://deb.playonlinux.com/) precise main 
  
 ==> /etc/apt/sources.list.d/playonlinux.list.save <== 
 # deb [http://deb.playonlinux.com/](http://deb.playonlinux.com/) precise main 
  
 ==> /etc/apt/sources.list.d/team-xbmc-ppa-trusty.list <== 
 # deb [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) trusty main 
 # deb-src [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) trusty main 
  
 ==> /etc/apt/sources.list.d/team-xbmc-ppa-trusty.list.save <== 
 # deb [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) trusty main 
 # deb-src [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) trusty main 
  
 ==> /etc/apt/sources.list.d/team-xbmc-xbmc-nightly-precise.list <== 
 # deb [http://ppa.launchpad.net/team-xbmc/xbmc-nightly/ubuntu](http://ppa.launchpad.net/team-xbmc/xbmc-nightly/ubuntu) trusty main # disabled on upgrade to trusty 
 # deb-src [http://ppa.launchpad.net/team-xbmc/xbmc-nightly/ubuntu](http://ppa.launchpad.net/team-xbmc/xbmc-nightly/ubuntu) trusty main # disabled on upgrade to trusty 
  
 ==> /etc/apt/sources.list.d/team-xbmc-xbmc-nightly-precise.list.distUpgrade <== 
 deb [http://ppa.launchpad.net/team-xbmc/xbmc-nightly/ubuntu](http://ppa.launchpad.net/team-xbmc/xbmc-nightly/ubuntu) precise main 
 deb-src [http://ppa.launchpad.net/team-xbmc/xbmc-nightly/ubuntu](http://ppa.launchpad.net/team-xbmc/xbmc-nightly/ubuntu) precise main 
  
 ==> /etc/apt/sources.list.d/team-xbmc-xbmc-nightly-precise.list.save <== 
 # deb [http://ppa.launchpad.net/team-xbmc/xbmc-nightly/ubuntu](http://ppa.launchpad.net/team-xbmc/xbmc-nightly/ubuntu) trusty main # disabled on upgrade to trusty 
 # deb-src [http://ppa.launchpad.net/team-xbmc/xbmc-nightly/ubuntu](http://ppa.launchpad.net/team-xbmc/xbmc-nightly/ubuntu) trusty main # disabled on upgrade to trusty 
  
 ==> /etc/apt/sources.list.d/xorg-edgers-ppa-trusty.list <== 
 # deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) trusty main 
 # deb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) trusty main 
  
 ==> /etc/apt/sources.list.d/xorg-edgers-ppa-trusty.list.save <== 
 # deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) trusty main 
 # deb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) trusty main 

```

I can't remove repository sources from the software & updates preferences, although I did uncheck them. I can't install or uninstall anything from the Ubuntu Software Center. The whole installer package system is broken.

The libsdl dependency keeps coming up and never gets installed. It keeps giving me an error number (1), which I don't know what it means.

Thanks if you can help me. At this point I'm seriously considering re-partitioning and doing a complete re-installation of Ubuntu. I'm running 14.0.4 LTS.

---

### Post by ray_silva on 2015-08-15
OK, I'm an idiot. I did <block></block> instead of the right "["code"]" "[/"code"]". I don't know what kind of gunk was running through my head.
SO...sorry.

---

### Post by Bashing-om on 2015-08-15
ray_silva; Well ....

There is still this:
> 
 deb http://download.opensuse.org/repositories/home:/emby/{Repository}/ /

I do not know how the PPA for emby works in 'buntu, or what the application "emby" is. Please explain it's purpose.

Also you remain on an old source:
```

 ==> /etc/apt/sources.list.d/team-xbmc-xbmc-nightly-precise.list.distUpgrade <== 
 deb http://ppa.launchpad.net/team-xbmc/xbmc-nightly/ubuntu precise main 
 deb-src http://ppa.launchpad.net/team-xbmc/xbmc-nightly/ubuntu precise main 

```
Which should be updated ( trusty is supported) .

We need to know what "emby" is, and update "xbmc" .
Once we know what the sources are, and that the sources are as required then we run terminal commands:
```

sudo apt-get update
sudo apt-get upgrade

```
to see what the state of the package management is.

[INDENT][INDENT][INDENT]cause and results
[/INDENT][/INDENT][/INDENT]

---

