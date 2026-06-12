---
title: "The old 404 error on apt-get update"
date: 2017-08-02
forum: Installation &amp; Upgrades
---

### Post by steve234 on 2017-08-02
Hi there,

I am trying to install various packages via apt-get. That did not work, neither did updating (apt-get update).

This is a new issue for me. I have been running this machine on Lubuntu 14.04 LTS for a number of years.

I've tried a number of (years old) fixes on stackexchange but to no avail. My error looks like this:

```


$ sudo apt-get update
Ign http://gb.archive.ubuntu.com trusty InRelease
Ign http://archive.canonical.com trusty InRelease                              
Get:1 http://gb.archive.ubuntu.com trusty-updates InRelease [65.9 kB]          
Ign http://extras.ubuntu.com trusty InRelease                                  
Hit http://repository.spotify.com stable InRelease                             
Hit http://archive.canonical.com trusty Release.gpg                            
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://ppa.launchpad.net trusty InRelease                                  
Get:2 http://deb.opera.com stable InRelease [2,592 B]                          
Hit http://www.netfabb.com stable InRelease                                    
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.canonical.com trusty Release                                
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://gb.archive.ubuntu.com trusty-backports InRelease                    
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:3 http://gb.archive.ubuntu.com trusty-proposed InRelease [65.9 kB]         
Get:4 http://security.ubuntu.com trusty-security InRelease [65.9 kB]           
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://repository.spotify.com stable/non-free i386 Packages                
Ign http://deb.opera.com stable InRelease                                      
Hit http://ppa.launchpad.net trusty InRelease                                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://gb.archive.ubuntu.com trusty Release.gpg                            
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://deb.opera.com stable/non-free i386 Packages/DiffIndex               
Hit http://gb.archive.ubuntu.com trusty Release                                
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://www.netfabb.com stable/non-free i386 Packages                       
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://repo.steampowered.com precise InRelease                             
Get:5 http://gb.archive.ubuntu.com trusty-updates/main Sources [401 kB]        
Hit http://archive.canonical.com trusty/partner Sources                        
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.canonical.com trusty/partner Translation-en                 
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty InRelease                                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://repository.spotify.com stable/non-free Translation-en_GB            
Hit http://repo.steampowered.com precise/steam Sources                         
Get:6 http://gb.archive.ubuntu.com trusty-updates/restricted Sources [6,331 B] 
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://repository.spotify.com stable/non-free Translation-en               
Get:7 http://gb.archive.ubuntu.com trusty-updates/universe Sources [186 kB]    
Hit http://deb.opera.com stable/non-free i386 Packages                         
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:8 http://security.ubuntu.com trusty-security/main Sources [138 kB]         
Ign http://deb.opera.com stable/non-free Translation-en_GB                     
Hit http://ppa.launchpad.net trusty InRelease                                  
Ign http://deb.opera.com stable/non-free Translation-en                        
Get:9 http://ppa.launchpad.net trusty InRelease [15.4 kB]                      
Hit http://repo.steampowered.com precise/steam amd64 Packages                  
Get:10 http://gb.archive.ubuntu.com trusty-updates/multiverse Sources [7,769 B]
Ign http://extras.ubuntu.com trusty/main Translation-en_GB                     
Get:11 http://gb.archive.ubuntu.com trusty-updates/main i386 Packages [950 kB] 
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Ign http://ppa.launchpad.net trusty Release.gpg                                
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://ppa.launchpad.net trusty Release.gpg                                
Get:12 http://security.ubuntu.com trusty-security/restricted Sources [4,955 B] 
Hit http://repo.steampowered.com precise/steam i386 Packages                   
Hit http://ppa.launchpad.net trusty Release.gpg                                
Get:13 http://gb.archive.ubuntu.com trusty-updates/restricted i386 Packages [16.9 kB]
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://ppa.launchpad.net trusty Release.gpg                                
Get:14 http://gb.archive.ubuntu.com trusty-updates/universe i386 Packages [419 kB]
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:15 http://security.ubuntu.com trusty-security/universe Sources [60.3 kB]   
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Get:16 http://gb.archive.ubuntu.com trusty-updates/multiverse i386 Packages [14.7 kB]
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Get:17 http://gb.archive.ubuntu.com trusty-updates/main Translation-en [491 kB]
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:18 http://security.ubuntu.com trusty-security/multiverse Sources [3,189 B] 
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Get:19 http://security.ubuntu.com trusty-security/main i386 Packages [596 kB]  
Ign http://ppa.launchpad.net trusty Release.gpg                                
Get:20 http://gb.archive.ubuntu.com trusty-updates/multiverse Translation-en [7,430 B]
Hit http://ppa.launchpad.net trusty Release.gpg                                
Get:21 http://gb.archive.ubuntu.com trusty-updates/restricted Translation-en [3,978 B]
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:22 http://gb.archive.ubuntu.com trusty-updates/universe Translation-en [224 kB]
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://ppa.launchpad.net trusty Release                                    
Ign http://ppa.launchpad.net trusty/main i386 Packages/DiffIndex               
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty Release                                    
Ign http://ppa.launchpad.net trusty Release                                    
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://gb.archive.ubuntu.com trusty-backports/main Sources                 
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://gb.archive.ubuntu.com trusty-backports/restricted Sources           
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://gb.archive.ubuntu.com trusty-backports/universe Sources             
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://gb.archive.ubuntu.com trusty-backports/multiverse Sources           
Ign http://ppa.launchpad.net trusty Release                                    
Hit http://gb.archive.ubuntu.com trusty-backports/main i386 Packages           
Hit http://gb.archive.ubuntu.com trusty-backports/restricted i386 Packages     
Hit http://gb.archive.ubuntu.com trusty-backports/universe i386 Packages       
Hit http://gb.archive.ubuntu.com trusty-backports/multiverse i386 Packages     
Hit http://gb.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://gb.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://gb.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://gb.archive.ubuntu.com trusty-backports/universe Translation-en      
Get:23 http://security.ubuntu.com trusty-security/restricted i386 Packages [13.7 kB]
Get:24 http://gb.archive.ubuntu.com trusty-proposed/restricted i386 Packages [772 B]
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:25 http://security.ubuntu.com trusty-security/universe i386 Packages [179 kB]
Get:26 http://gb.archive.ubuntu.com trusty-proposed/multiverse i386 Packages [28 B]
Get:27 http://gb.archive.ubuntu.com trusty-proposed/main i386 Packages [87.8 kB]
Get:28 http://security.ubuntu.com trusty-security/multiverse i386 Packages [4,288 B]
Get:29 http://gb.archive.ubuntu.com trusty-proposed/universe i386 Packages [13.1 kB]
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://gb.archive.ubuntu.com trusty-proposed/main Translation-en           
Hit http://gb.archive.ubuntu.com trusty-proposed/multiverse Translation-en     
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://gb.archive.ubuntu.com trusty-proposed/restricted Translation-en     
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Hit http://gb.archive.ubuntu.com trusty-proposed/universe Translation-en       
Hit http://gb.archive.ubuntu.com trusty/main Sources                           
Hit http://gb.archive.ubuntu.com trusty/restricted Sources                     
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://gb.archive.ubuntu.com trusty/universe Sources                       
Hit http://gb.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://gb.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://gb.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://gb.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Hit http://gb.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://gb.archive.ubuntu.com trusty/main Translation-en_GB                 
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://gb.archive.ubuntu.com trusty/main Translation-en                    
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://gb.archive.ubuntu.com trusty/multiverse Translation-en_GB           
Hit http://gb.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://gb.archive.ubuntu.com trusty/restricted Translation-en_GB           
Hit http://gb.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://gb.archive.ubuntu.com trusty/universe Translation-en_GB             
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://gb.archive.ubuntu.com trusty/universe Translation-en                
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://ppa.launchpad.net trusty/main Translation-en_GB                     
Ign http://repo.steampowered.com precise/steam Translation-en_GB               
Err http://ppa.launchpad.net trusty/main i386 Packages                         
  404  Not Found
Ign http://ppa.launchpad.net trusty/main Translation-en_GB                     
Ign http://repo.steampowered.com precise/steam Translation-en                  
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Err http://ppa.launchpad.net trusty/main i386 Packages                      
  404  Not Found
Ign http://ppa.launchpad.net trusty/main Translation-en_GB                  
Ign http://ppa.launchpad.net trusty/main Translation-en                     
Ign http://ppa.launchpad.net trusty/main Translation-en_GB                     
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Err http://ppa.launchpad.net trusty/main i386 Packages                      
  404  Not Found
Ign http://ppa.launchpad.net trusty/main Translation-en_GB                  
Ign http://ppa.launchpad.net trusty/main Translation-en                     
Fetched 4,238 kB in 28s (150 kB/s)                                             
W: GPG error: http://deb.opera.com stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D615560BA5C7FF72
W: GPG error: http://ppa.launchpad.net trusty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7F0BB3BE5BF00518
W: Failed to fetch http://ppa.launchpad.net/eee-control/eee-control/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/kilian/f.lux/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/thopiekar/cura/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

$ sudo apt-get install python-qt4
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/www.netfabb.com_debian_dists_stable_non-free_i18n_Translation-en%5fGB
E: The package lists or status file could not be parsed or opened.


```

My /etc/apt/sources.list file looks like this.

```
# deb cdrom:[Lubuntu 14.04.3 LTS _Trusty Tahr_ - Beta i386 (20150805)]/ trusty main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty universe
deb http://gb.archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse

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
deb http://gb.archive.ubuntu.com/ubuntu/ trusty-proposed restricted multiverse main universe
deb http://www.netfabb.com/debian/ stable non-free
# deb-src http://www.netfabb.com/debian/ stable non-free


```

Grateful for any help. 

Steve

---

### Post by vasa1 on 2017-08-02
Lubuntu 14.04 is end-of-life, unsupported. You'd be better off finding a supported OS.

[https://wiki.ubuntu.com/Releases#End_of_Life_.28EOL.29](https://wiki.ubuntu.com/Releases#End_of_Life_.28EOL.29)

---

### Post by deadflowr on 2017-08-02
the problem here, beyond Lubuntu EOL, is that the cura ppa has no version for trusty.
So you need to remove it.

Also same for the killian/f.lux ppa as that does not even seem to exist
(alternative ppa for f.lux here, maybe: [https://launchpad.net/~nathan-renniewaldock/+archive/ubuntu/flux]("https://launchpad.net/~nathan-renniewaldock/+archive/ubuntu/flux")

And finally the ppa for the eee-control has no trusty packages and hasn't had any updates for years
(Last version was for 11.04, so six years)

To clean up all three run
```
sudo add-apt-repository -r ppa:thopiekar/cura
sudo add-apt-repository -r ppa:eee-control/eee-control
sudo add-apt-repository -r ppa:kilian/f.lux
sudo apt-get update
```

Hope it helps

---

### Post by steve234 on 2017-08-02
Thanks for the responses:

@vasa - I thought I was running the version  of Lubuntu supported until 2019. I though I chose wisely and installed that version (to avoid the faff of upgrading on a legacy 32bit machine). 

It seems from the link you helpfully provided that various flavours of 14.04 LTS are unsupported but 14.04.1 is supproted until 2019. Can I check my version and upgrade / downgrade if nessecary?

@deadflowr - thanks but:
(1) the f.lux repository couldn't even be found by apt to remove it; and
(2) those commands make no difference to the overall issue - error on install of any package still exists - e.g.:

```
sudo apt-get install python-qt4
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/www.netfabb.com_debian_dists_stable_non-free_i18n_Translation-en%5fGB
E: The package lists or status file could not be parsed or opened.


```

---

### Post by #&amp;thj^% on 2017-08-02
You should get an idea with:
```
ubuntu-support-status
ubuntu-support-status --show-unsupported
ubuntu-support-status --show-supported

```

---

### Post by steve234 on 2017-08-02
That just throws more errors:

```
$ ubuntu-support-status
Traceback (most recent call last):
  File "/usr/bin/ubuntu-support-status", line 120, in <module>
    with apt.Cache() as cache:
  File "/usr/lib/python3/dist-packages/apt/cache.py", line 107, in __init__
    self.open(progress)
  File "/usr/lib/python3/dist-packages/apt/cache.py", line 151, in open
    self._cache = apt_pkg.Cache(progress)
SystemError: E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/www.netfabb.com_debian_dists_stable_non-free_i18n_Translation-en%5fGB, E:The package lists or status file could not be parsed or opened.


```

---

### Post by deadflowr on 2017-08-02
The f.lux ppa probably has a different name
post back what
```
grep f.lux /etc/apt/sources.list.d/*
```
tells you

as for the python install problem, clean the lists folder
```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```

but you still need to get rid of whatever the f.lux ppa entry is, or it will just repeat the same errors again.
So post that before you rm the lists folder, please.

---

### Post by steve234 on 2017-08-02
I'm a bit confused as to what I am taking from the grep-output.

The grep output is this - and I tried that and the shortened version but it was not found (see end of output):

```
$ grep f.lux /etc/apt/sources.list.d/*
/etc/apt/sources.list.d/kilian-f_lux-trusty.list:deb http://ppa.launchpad.net/kilian/f.lux/ubuntu trusty main
/etc/apt/sources.list.d/kilian-f_lux-trusty.list:# deb-src http://ppa.launchpad.net/kilian/f.lux/ubuntu trusty main
/etc/apt/sources.list.d/kilian-f_lux-trusty.list.save:deb http://ppa.launchpad.net/kilian/f.lux/ubuntu trusty main
/etc/apt/sources.list.d/kilian-f_lux-trusty.list.save:# deb-src http://ppa.launchpad.net/kilian/f.lux/ubuntu trusty main

$ sudo add-apt-repository -r ppa:/kilian/f.lux/ubuntu trusty main
Error: need a single repository as argument

$ sudo add-apt-repository -r ppa:/kilian/f.lux/
Cannot add PPA: 'ppa:/kilian/f.lux/'.
Please check that the PPA name or format is correct.

```

Any idea what I'm doing wrong?

---

### Post by steve234 on 2017-08-02
Also... I am ona supported version:

```
~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:    14.04
Codename:    trusty

```

This is listed in @vasa's link as supported - unless it's suddenly past 2019.

Ubuntu 14.04.5 LTS - supported until April 2019

---

### Post by #&amp;thj^% on 2017-08-02
> **steve234 said:**
> Also... I am ona supported version:

```
~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:    14.04
Codename:    trusty

```

This is listed in @vasa's link as supported - unless it's suddenly past 2019.

Ubuntu 14.04.5 LTS - supported until April 2019

Just bits are suported...mostly security only. (LTS Support (3 years).)
But try to remove with just this;
 "ppa:kilian/f.lux" no end/
```
sudo add-apt-repository -r ppa:/kilian/f.lux
```

---

### Post by deadflowr on 2017-08-02
**SEE post #10 above before trying the command from this post**

Okay so see the first entry from the output of the grep command.
Take that one and remove it
```
sudo rm /etc/apt/sources.list.d/kilian-f_lux-trusty.list
```
(the other 3 are dead and have no affect on apt-get, so they can stay or you can also remove them.)
This a manual approach, but does the job.

Then try clean the /var/lib/apt/lists folder as posted earlier and then run an apt-get update.
Then see what happens when you try installing the python package.

Good Luck

**EDIT:**
Try 1fallen's command first, before trying the rm command I've posted in this post.

---

### Post by steve234 on 2017-08-02
Cheers deadflowr, that seems to have removed it

also rm-ed the lists

no luck:

```
$ sudo rm /etc/apt/sources.list.d/kilian-f_lux-trusty.list

$ sudo apt-get updateGet:1 http://security.ubuntu.com trusty-security InRelease [65.9 kB]
Ign http://extras.ubuntu.com trusty InRelease                                  
Ign http://archive.canonical.com trusty InRelease                              
Get:2 http://deb.opera.com stable InRelease [2,592 B]                          
Ign http://gb.archive.ubuntu.com trusty InRelease                              
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://www.netfabb.com stable InRelease                                    
Hit http://archive.canonical.com trusty Release.gpg                            
Get:3 http://gb.archive.ubuntu.com trusty-updates InRelease [65.9 kB]          
Hit http://extras.ubuntu.com trusty Release                                    
Ign http://deb.opera.com stable InRelease                                      
Hit http://archive.canonical.com trusty Release                                
Ign http://deb.opera.com stable/non-free i386 Packages/DiffIndex               
Hit http://gb.archive.ubuntu.com trusty-backports InRelease                    
Get:4 http://gb.archive.ubuntu.com trusty-proposed InRelease [65.9 kB]         
Hit http://gb.archive.ubuntu.com trusty Release.gpg                            
Hit http://gb.archive.ubuntu.com trusty Release                                
Hit http://repo.steampowered.com precise InRelease                             
Get:5 http://security.ubuntu.com trusty-security/main Sources [138 kB]         
Hit http://www.netfabb.com stable/non-free i386 Packages                       
Get:6 http://security.ubuntu.com trusty-security/restricted Sources [4,955 B]  
Get:7 http://security.ubuntu.com trusty-security/universe Sources [60.3 kB]    
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://deb.opera.com stable/non-free i386 Packages                         
Get:8 http://security.ubuntu.com trusty-security/multiverse Sources [3,189 B]  
Get:9 http://security.ubuntu.com trusty-security/main i386 Packages [596 kB]   
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty InRelease                                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://ppa.launchpad.net trusty InRelease                                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://deb.opera.com stable/non-free Translation-en_GB                     
Ign http://deb.opera.com stable/non-free Translation-en                        
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.canonical.com trusty/partner Sources                        
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.canonical.com trusty/partner Translation-en                 
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://ppa.launchpad.net trusty InRelease                                  
Ign http://extras.ubuntu.com trusty/main Translation-en_GB                     
Get:10 http://ppa.launchpad.net trusty InRelease [15.4 kB]                     
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://ppa.launchpad.net trusty Release.gpg                                
Get:11 http://security.ubuntu.com trusty-security/restricted i386 Packages [13.7 kB]
Hit http://ppa.launchpad.net trusty Release.gpg                                
Get:12 http://gb.archive.ubuntu.com trusty-updates/main Sources [401 kB]       
Hit http://ppa.launchpad.net trusty Release.gpg                                
Get:13 http://security.ubuntu.com trusty-security/universe i386 Packages [179 kB]
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://ppa.launchpad.net trusty Release                                    
Get:14 http://security.ubuntu.com trusty-security/multiverse i386 Packages [4,288 B]
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Get:15 http://gb.archive.ubuntu.com trusty-updates/restricted Sources [6,331 B]
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:16 http://gb.archive.ubuntu.com trusty-updates/universe Sources [186 kB]   
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://repo.steampowered.com precise/steam Sources                         
Get:17 http://gb.archive.ubuntu.com trusty-updates/multiverse Sources [7,769 B]
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:18 http://gb.archive.ubuntu.com trusty-updates/main i386 Packages [950 kB] 
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://repo.steampowered.com precise/steam amd64 Packages                  
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://ppa.launchpad.net trusty/main i386 Packages/DiffIndex               
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://repo.steampowered.com precise/steam i386 Packages                   
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Get:19 http://gb.archive.ubuntu.com trusty-updates/restricted i386 Packages [16.9 kB]
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:20 http://gb.archive.ubuntu.com trusty-updates/universe i386 Packages [419 kB]
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://repository.spotify.com stable InRelease                             
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:21 http://gb.archive.ubuntu.com trusty-updates/multiverse i386 Packages [14.7 kB]
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://gb.archive.ubuntu.com trusty-updates/main Translation-en            
Hit http://gb.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Hit http://repository.spotify.com stable/non-free i386 Packages                
Hit http://gb.archive.ubuntu.com trusty-updates/restricted Translation-en      
Hit http://gb.archive.ubuntu.com trusty-updates/universe Translation-en        
Hit http://gb.archive.ubuntu.com trusty-backports/main Sources                 
Hit http://gb.archive.ubuntu.com trusty-backports/restricted Sources           
Hit http://gb.archive.ubuntu.com trusty-backports/universe Sources             
Hit http://gb.archive.ubuntu.com trusty-backports/multiverse Sources           
Ign http://ppa.launchpad.net trusty/main Translation-en_GB                     
Hit http://gb.archive.ubuntu.com trusty-backports/main i386 Packages           
Ign http://ppa.launchpad.net trusty/main Translation-en_GB                     
Hit http://gb.archive.ubuntu.com trusty-backports/restricted i386 Packages     
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://gb.archive.ubuntu.com trusty-backports/universe i386 Packages       
Hit http://gb.archive.ubuntu.com trusty-backports/multiverse i386 Packages     
Hit http://gb.archive.ubuntu.com trusty-backports/main Translation-en          
Ign http://repository.spotify.com stable/non-free Translation-en_GB            
Hit http://gb.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Ign http://repository.spotify.com stable/non-free Translation-en               
Hit http://gb.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://gb.archive.ubuntu.com trusty-backports/universe Translation-en      
Get:22 http://gb.archive.ubuntu.com trusty-proposed/restricted i386 Packages [772 B]
Get:23 http://gb.archive.ubuntu.com trusty-proposed/multiverse i386 Packages [28 B]
Get:24 http://gb.archive.ubuntu.com trusty-proposed/main i386 Packages [87.8 kB]
Get:25 http://gb.archive.ubuntu.com trusty-proposed/universe i386 Packages [13.1 kB]
Hit http://gb.archive.ubuntu.com trusty-proposed/main Translation-en           
Hit http://gb.archive.ubuntu.com trusty-proposed/multiverse Translation-en 
Hit http://gb.archive.ubuntu.com trusty-proposed/restricted Translation-en     
Hit http://gb.archive.ubuntu.com trusty-proposed/universe Translation-en       
Hit http://gb.archive.ubuntu.com trusty/main Sources                           
Hit http://gb.archive.ubuntu.com trusty/restricted Sources                     
Hit http://gb.archive.ubuntu.com trusty/universe Sources                   
Hit http://gb.archive.ubuntu.com trusty/multiverse Sources                 
Hit http://gb.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://gb.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://gb.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://gb.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://gb.archive.ubuntu.com trusty/main Translation-en_GB             
Hit http://gb.archive.ubuntu.com trusty/main Translation-en                
Hit http://gb.archive.ubuntu.com trusty/multiverse Translation-en_GB       
Hit http://gb.archive.ubuntu.com trusty/multiverse Translation-en          
Hit http://gb.archive.ubuntu.com trusty/restricted Translation-en_GB       
Hit http://gb.archive.ubuntu.com trusty/restricted Translation-en          
Hit http://gb.archive.ubuntu.com trusty/universe Translation-en_GB         
Hit http://gb.archive.ubuntu.com trusty/universe Translation-en                
Ign http://repo.steampowered.com precise/steam Translation-en_GB               
Ign http://repo.steampowered.com precise/steam Translation-en                  
Fetched 3,512 kB in 32s (109 kB/s)                                             
Reading package lists... Error!
W: GPG error: http://deb.opera.com stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D615560BA5C7FF72
W: GPG error: http://ppa.launchpad.net trusty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7F0BB3BE5BF00518
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/www.netfabb.com_debian_dists_stable_non-free_i18n_Translation-en%5fGB
E: The package lists or status file could not be parsed or opened.

$ sudo rm -rf /var/lib/apt/lists/*

$ sudo apt-get update
Get:1 http://security.ubuntu.com trusty-security InRelease [65.9 kB]
Ign http://archive.canonical.com trusty InRelease                              
Ign http://gb.archive.ubuntu.com trusty InRelease                              
Ign http://extras.ubuntu.com trusty InRelease                                  
Get:2 http://archive.canonical.com trusty Release.gpg [933 B]                  
Get:3 http://ppa.launchpad.net trusty InRelease [15.5 kB]                      
Get:4 http://repo.steampowered.com precise InRelease [2,842 B]                 
Get:5 http://gb.archive.ubuntu.com trusty-updates InRelease [65.9 kB]          
Get:6 http://extras.ubuntu.com trusty Release.gpg [72 B]                       
Get:7 http://www.netfabb.com stable InRelease [1,942 B]                        
Get:8 http://deb.opera.com stable InRelease [2,592 B]                          
Get:9 http://archive.canonical.com trusty Release [9,359 B]                    
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:10 http://extras.ubuntu.com trusty Release [11.9 kB]                       
Get:11 http://ppa.launchpad.net trusty InRelease [15.5 kB]                     
Get:12 http://repo.steampowered.com precise/steam Sources [550 B]              
Get:13 http://gb.archive.ubuntu.com trusty-backports InRelease [65.9 kB]       
Get:14 http://repo.steampowered.com precise/steam amd64 Packages [601 B]       
Get:15 http://ppa.launchpad.net trusty InRelease [15.5 kB]                     
Ign http://deb.opera.com stable InRelease                                      
Get:16 http://repo.steampowered.com precise/steam i386 Packages [799 B]        
Get:17 http://repository.spotify.com stable InRelease [3,302 B]                
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:18 http://gb.archive.ubuntu.com trusty-proposed InRelease [65.9 kB]        
Get:19 http://www.netfabb.com stable/non-free i386 Packages [596 B]            
Get:20 http://archive.canonical.com trusty/partner Sources [9,713 B]           
Get:21 http://security.ubuntu.com trusty-security/main Sources [138 kB]        
Get:22 http://gb.archive.ubuntu.com trusty Release.gpg [933 B]                 
Get:23 http://extras.ubuntu.com trusty/main Sources [14 B]                     
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:24 http://gb.archive.ubuntu.com trusty-updates/main Sources [401 kB]       
Get:25 http://archive.canonical.com trusty/partner i386 Packages [5,770 B]     
Get:26 http://extras.ubuntu.com trusty/main i386 Packages [14 B]               
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:27 http://repository.spotify.com stable/non-free i386 Packages [1,136 B]   
Get:28 http://archive.canonical.com trusty/partner Translation-en [4,207 B]    
Get:29 http://ppa.launchpad.net trusty InRelease [16.0 kB]                     
Get:30 http://ppa.launchpad.net trusty InRelease [15.4 kB]                     
Get:31 http://gb.archive.ubuntu.com trusty-updates/restricted Sources [6,331 B]
Get:32 http://ppa.launchpad.net trusty InRelease [15.5 kB]                     
Ign http://repo.steampowered.com precise/steam Translation-en_GB               
Ign http://repo.steampowered.com precise/steam Translation-en                  
Get:33 http://gb.archive.ubuntu.com trusty-updates/universe Sources [186 kB]   
Get:34 http://security.ubuntu.com trusty-security/restricted Sources [4,955 B] 
Get:35 http://ppa.launchpad.net trusty InRelease [15.4 kB]                     
Get:36 http://security.ubuntu.com trusty-security/universe Sources [60.3 kB]   
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://extras.ubuntu.com trusty/main Translation-en_GB                     
Ign http://repository.spotify.com stable/non-free Translation-en_GB            
Get:37 http://ppa.launchpad.net trusty InRelease [15.5 kB]                     
Get:38 http://security.ubuntu.com trusty-security/multiverse Sources [3,189 B] 
Get:39 http://deb.opera.com stable/non-free i386 Packages [1,820 B]            
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Get:40 http://security.ubuntu.com trusty-security/main i386 Packages [596 kB]  
Get:41 http://ppa.launchpad.net trusty InRelease [15.4 kB]                     
Ign http://repository.spotify.com stable/non-free Translation-en               
Get:42 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:43 http://gb.archive.ubuntu.com trusty-updates/multiverse Sources [7,769 B]
Get:44 http://ppa.launchpad.net trusty/main i386 Packages [560 B]              
Get:45 http://gb.archive.ubuntu.com trusty-updates/main i386 Packages [950 kB] 
Ign http://deb.opera.com stable/non-free Translation-en_GB                     
Get:46 http://ppa.launchpad.net trusty/main Translation-en [341 B]             
Get:47 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Ign http://deb.opera.com stable/non-free Translation-en                        
Get:48 http://ppa.launchpad.net trusty/main i386 Packages [4,799 B]            
Get:49 http://ppa.launchpad.net trusty/main Translation-en [3,244 B]           
Get:50 http://ppa.launchpad.net trusty/main i386 Packages [7,012 B]            
Get:51 http://ppa.launchpad.net trusty/main Translation-en [5,526 B]           
Get:52 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Get:53 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Get:54 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Get:55 http://security.ubuntu.com trusty-security/restricted i386 Packages [13.7 kB]
Get:56 http://security.ubuntu.com trusty-security/universe i386 Packages [179 kB]
Get:57 http://ppa.launchpad.net trusty/main i386 Packages [1,463 B]            
Get:58 http://ppa.launchpad.net trusty/main Translation-en [1,309 B]           
Get:59 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Get:60 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Get:61 http://security.ubuntu.com trusty-security/multiverse i386 Packages [4,288 B]
Get:62 http://ppa.launchpad.net trusty/main i386 Packages [39.9 kB]            
Get:63 http://security.ubuntu.com trusty-security/main Translation-en [345 kB] 
Get:64 http://gb.archive.ubuntu.com trusty-updates/restricted i386 Packages [16.9 kB]
Get:65 http://gb.archive.ubuntu.com trusty-updates/universe i386 Packages [419 kB]
Get:66 http://ppa.launchpad.net trusty/main Translation-en [29.3 kB]           
Get:67 http://ppa.launchpad.net trusty Release [14.0 kB]                       
Get:68 http://ppa.launchpad.net trusty/main i386 Packages [4,460 B]            
Get:69 http://ppa.launchpad.net trusty/main Translation-en [2,502 B]           
Get:70 http://ppa.launchpad.net trusty/main i386 Packages [2,988 B]            
Get:71 http://security.ubuntu.com trusty-security/multiverse Translation-en [2,201 B]
Get:72 http://ppa.launchpad.net trusty/main Translation-en [1,343 B]           
Get:73 http://security.ubuntu.com trusty-security/restricted Translation-en [3,491 B]
Get:74 http://ppa.launchpad.net trusty/main i386 Packages [1,954 B]            
Get:75 http://security.ubuntu.com trusty-security/universe Translation-en [102 kB]
Get:76 http://ppa.launchpad.net trusty/main Translation-en [2,123 B]           
Get:77 http://ppa.launchpad.net trusty/main i386 Packages [594 B]              
Get:78 http://gb.archive.ubuntu.com trusty-updates/multiverse i386 Packages [14.7 kB]
Get:79 http://gb.archive.ubuntu.com trusty-updates/main Translation-en [491 kB]
Get:80 http://ppa.launchpad.net trusty/main Translation-en [429 B]             
Get:81 http://ppa.launchpad.net trusty Release [15.1 kB]                       
Get:82 http://ppa.launchpad.net trusty Release [15.1 kB]                       
Get:83 http://ppa.launchpad.net trusty Release [15.1 kB]                       
Get:84 http://ppa.launchpad.net trusty Release [14.5 kB]                       
Get:85 http://ppa.launchpad.net trusty Release [15.1 kB]                       
Get:86 http://ppa.launchpad.net trusty Release [15.1 kB]                       
Get:87 http://gb.archive.ubuntu.com trusty-updates/multiverse Translation-en [7,430 B]
Get:88 http://ppa.launchpad.net trusty/main i386 Packages [669 B]      
Get:89 http://gb.archive.ubuntu.com trusty-updates/restricted Translation-en [3,978 B]
Get:90 http://gb.archive.ubuntu.com trusty-updates/universe Translation-en [224 kB]
Get:91 http://ppa.launchpad.net trusty/main i386 Packages [5,597 B]            
Get:92 http://gb.archive.ubuntu.com trusty Release [58.5 kB]                   
Get:93 http://ppa.launchpad.net trusty/main Translation-en [3,926 B]           
Get:94 http://gb.archive.ubuntu.com trusty-backports/main Sources [9,712 B]    
Get:95 http://ppa.launchpad.net trusty/main i386 Packages [3,707 B]            
Get:96 http://gb.archive.ubuntu.com trusty-backports/restricted Sources [28 B] 
Get:97 http://ppa.launchpad.net trusty/main Translation-en [653 B]             
Get:98 http://gb.archive.ubuntu.com trusty-backports/universe Sources [35.3 kB]
Get:99 http://ppa.launchpad.net trusty/main i386 Packages [872 B]              
Get:100 http://gb.archive.ubuntu.com trusty-backports/multiverse Sources [1,898 B]
Get:101 http://ppa.launchpad.net trusty/main Translation-en [543 B]     
Get:102 http://gb.archive.ubuntu.com trusty-backports/main i386 Packages [13.3 kB]
Get:103 http://ppa.launchpad.net trusty/main i386 Packages [4,637 B]           
Get:104 http://ppa.launchpad.net trusty/main Translation-en [2,473 B]   
Get:105 http://gb.archive.ubuntu.com trusty-backports/restricted i386 Packages [28 B]
Get:106 http://gb.archive.ubuntu.com trusty-backports/universe i386 Packages [43.2 kB]
Get:107 http://ppa.launchpad.net trusty/main i386 Packages [624 B]             
Get:108 http://gb.archive.ubuntu.com trusty-backports/multiverse i386 Packages [1,552 B]
Get:109 http://ppa.launchpad.net trusty/main Translation-en [177 B]     
Get:110 http://gb.archive.ubuntu.com trusty-backports/main Translation-en [7,503 B]
Get:111 http://ppa.launchpad.net trusty/main i386 Packages [818 B]      
Get:112 http://gb.archive.ubuntu.com trusty-backports/multiverse Translation-en [1,215 B]
Get:113 http://ppa.launchpad.net trusty/main Translation-en [1,196 B]   
Get:114 http://gb.archive.ubuntu.com trusty-backports/restricted Translation-en [28 B]
Get:115 http://gb.archive.ubuntu.com trusty-backports/universe Translation-en [36.8 kB]
Get:116 http://gb.archive.ubuntu.com trusty-proposed/restricted i386 Packages [772 B]
Get:117 http://gb.archive.ubuntu.com trusty-proposed/multiverse i386 Packages [28 B]
Get:118 http://gb.archive.ubuntu.com trusty-proposed/main i386 Packages [87.8 kB]
Get:119 http://gb.archive.ubuntu.com trusty-proposed/universe i386 Packages [13.1 kB]
Get:120 http://gb.archive.ubuntu.com trusty-proposed/main Translation-en [29.4 kB]
Ign http://ppa.launchpad.net trusty/main Translation-en_GB                     
Get:121 http://gb.archive.ubuntu.com trusty-proposed/multiverse Translation-en [28 B]
Ign http://ppa.launchpad.net trusty/main Translation-en_GB              
Get:122 http://gb.archive.ubuntu.com trusty-proposed/restricted Translation-en [281 B]
Ign http://ppa.launchpad.net trusty/main Translation-en                 
Get:123 http://gb.archive.ubuntu.com trusty-proposed/universe Translation-en [10.5 kB]
Get:124 http://gb.archive.ubuntu.com trusty/main Sources [1,064 kB]  
Get:125 http://gb.archive.ubuntu.com trusty/restricted Sources [5,433 B]
Get:126 http://gb.archive.ubuntu.com trusty/universe Sources [6,399 kB]
Get:127 http://gb.archive.ubuntu.com trusty/multiverse Sources [174 kB]        
Get:128 http://gb.archive.ubuntu.com trusty/main i386 Packages [1,348 kB]      
Get:129 http://gb.archive.ubuntu.com trusty/restricted i386 Packages [13.4 kB] 
Get:130 http://gb.archive.ubuntu.com trusty/universe i386 Packages [5,866 kB]  
Get:131 http://gb.archive.ubuntu.com trusty/multiverse i386 Packages [134 kB]  
Get:132 http://gb.archive.ubuntu.com trusty/main Translation-en_GB [96.8 kB]   
Get:133 http://gb.archive.ubuntu.com trusty/main Translation-en [762 kB]       
Get:134 http://gb.archive.ubuntu.com trusty/multiverse Translation-en_GB [98.3 kB]
Get:135 http://gb.archive.ubuntu.com trusty/multiverse Translation-en [102 kB] 
Get:136 http://gb.archive.ubuntu.com trusty/restricted Translation-en_GB [3,483 B]
Get:137 http://gb.archive.ubuntu.com trusty/restricted Translation-en [3,457 B]
Get:138 http://gb.archive.ubuntu.com trusty/universe Translation-en_GB [7,557 B]
Get:139 http://gb.archive.ubuntu.com trusty/universe Translation-en [4,089 kB] 
Fetched 25.6 MB in 53s (475 kB/s)                                              
Reading package lists... Error!
W: GPG error: http://deb.opera.com stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D615560BA5C7FF72
W: GPG error: http://ppa.launchpad.net trusty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7F0BB3BE5BF00518
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/www.netfabb.com_debian_dists_stable_non-free_i18n_Translation-en%5fGB
E: The package lists or status file could not be parsed or opened.

$ sudo apt-get install python-qt4Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/www.netfabb.com_debian_dists_stable_non-free_i18n_Translation-en%5fGB
E: The package lists or status file could not be parsed or opened.

```

---

### Post by #&amp;thj^% on 2017-08-02
This one looks like it might need to go also.
deb [http://www.netfabb.com/debian/](http://www.netfabb.com/debian/) stable non-free

---

### Post by steve234 on 2017-08-02
Thanks - tried to get rid of it - obviously it's not a case of simply rm-ing that path?? - Do I need to remove it from somewhere else?

no cigar anyway:

```


$ sudo rm /var/lib/apt/lists/www.netfabb.com_debian_dists_stable_non-free_i18n_Translation-en%5fGB

$ sudo rm -rf /var/lib/apt/lists/*

$ sudo apt-get update

Ign http://archive.canonical.com trusty InRelease
Ign http://gb.archive.ubuntu.com trusty InRelease                              
Ign http://extras.ubuntu.com trusty InRelease                                  
Get:1 http://repo.steampowered.com precise InRelease [2,842 B]                 
Get:2 http://gb.archive.ubuntu.com trusty-updates InRelease [65.9 kB]          
Get:3 http://security.ubuntu.com trusty-security InRelease [65.9 kB]           
Get:4 http://archive.canonical.com trusty Release.gpg [933 B]                  
Get:5 http://ppa.launchpad.net trusty InRelease [15.5 kB]                      
Get:6 http://repository.spotify.com stable InRelease [3,302 B]                 
Get:7 http://extras.ubuntu.com trusty Release.gpg [72 B]                       
Get:8 http://deb.opera.com stable InRelease [2,592 B]                          
Get:9 http://www.netfabb.com stable InRelease [1,942 B]                        
Get:10 http://archive.canonical.com trusty Release [9,359 B]                   
Get:11 http://extras.ubuntu.com trusty Release [11.9 kB]                       
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:12 http://ppa.launchpad.net trusty InRelease [15.5 kB]                     
Get:13 http://gb.archive.ubuntu.com trusty-backports InRelease [65.9 kB]       
Get:14 http://repository.spotify.com stable/non-free i386 Packages [1,136 B]   
Get:15 http://ppa.launchpad.net trusty InRelease [15.5 kB]                     
Get:16 http://www.netfabb.com stable/non-free i386 Packages [596 B]            
Get:17 http://gb.archive.ubuntu.com trusty-proposed InRelease [65.9 kB]        
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://deb.opera.com stable InRelease                                      
Get:18 http://archive.canonical.com trusty/partner Sources [9,713 B]           
Get:19 http://gb.archive.ubuntu.com trusty Release.gpg [933 B]                 
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:20 http://repo.steampowered.com precise/steam Sources [550 B]              
Get:21 http://archive.canonical.com trusty/partner i386 Packages [5,770 B]     
Get:22 http://ppa.launchpad.net trusty InRelease [16.0 kB]                     
Get:23 http://gb.archive.ubuntu.com trusty Release [58.5 kB]                   
Get:24 http://security.ubuntu.com trusty-security/main Sources [138 kB]        
Get:25 http://archive.canonical.com trusty/partner Translation-en [4,207 B]    
Get:26 http://extras.ubuntu.com trusty/main Sources [14 B]                     
Get:27 http://ppa.launchpad.net trusty InRelease [15.4 kB]                     
Get:28 http://extras.ubuntu.com trusty/main i386 Packages [14 B]               
Get:29 http://ppa.launchpad.net trusty InRelease [15.5 kB]                     
Get:30 http://gb.archive.ubuntu.com trusty-updates/main Sources [401 kB]       
Get:31 http://ppa.launchpad.net trusty InRelease [15.4 kB]                     
Get:32 http://security.ubuntu.com trusty-security/restricted Sources [4,955 B] 
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:33 http://security.ubuntu.com trusty-security/universe Sources [60.3 kB]   
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:34 http://ppa.launchpad.net trusty InRelease [15.5 kB]                     
Get:35 http://ppa.launchpad.net trusty InRelease [15.4 kB]                     
Get:36 http://repo.steampowered.com precise/steam amd64 Packages [601 B]       
Get:37 http://security.ubuntu.com trusty-security/multiverse Sources [3,189 B] 
Get:38 http://security.ubuntu.com trusty-security/main i386 Packages [596 kB]  
Get:39 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Ign http://repository.spotify.com stable/non-free Translation-en_GB            
Get:40 http://deb.opera.com stable/non-free i386 Packages [1,820 B]            
Ign http://extras.ubuntu.com trusty/main Translation-en_GB                     
Get:41 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Ign http://repository.spotify.com stable/non-free Translation-en               
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Get:42 http://ppa.launchpad.net trusty/main i386 Packages [560 B]              
Ign http://deb.opera.com stable/non-free Translation-en_GB                     
Get:43 http://ppa.launchpad.net trusty/main Translation-en [341 B]             
Ign http://deb.opera.com stable/non-free Translation-en                        
Get:44 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Get:45 http://gb.archive.ubuntu.com trusty-updates/restricted Sources [6,331 B]
Get:46 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Get:47 http://gb.archive.ubuntu.com trusty-updates/universe Sources [186 kB]   
Get:48 http://repo.steampowered.com precise/steam i386 Packages [799 B]        
Get:49 http://ppa.launchpad.net trusty/main i386 Packages [4,799 B]            
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:50 http://ppa.launchpad.net trusty/main Translation-en [3,244 B]           
Get:51 http://ppa.launchpad.net trusty/main i386 Packages [7,012 B]            
Get:52 http://gb.archive.ubuntu.com trusty-updates/multiverse Sources [7,769 B]
Get:53 http://gb.archive.ubuntu.com trusty-updates/main i386 Packages [950 kB] 
Get:54 http://ppa.launchpad.net trusty/main Translation-en [5,526 B]           
Get:55 http://ppa.launchpad.net trusty/main i386 Packages [1,463 B]            
Get:56 http://ppa.launchpad.net trusty/main Translation-en [1,309 B]           
Get:57 http://security.ubuntu.com trusty-security/restricted i386 Packages [13.7 kB]
Get:58 http://ppa.launchpad.net trusty/main i386 Packages [39.9 kB]            
Get:59 http://security.ubuntu.com trusty-security/universe i386 Packages [179 kB]
Get:60 http://ppa.launchpad.net trusty/main Translation-en [29.3 kB]           
Get:61 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Get:62 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Get:63 http://security.ubuntu.com trusty-security/multiverse i386 Packages [4,288 B]
Get:64 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Get:65 http://security.ubuntu.com trusty-security/main Translation-en [345 kB] 
Get:66 http://ppa.launchpad.net trusty/main i386 Packages [4,460 B]            
Get:67 http://ppa.launchpad.net trusty/main Translation-en [2,502 B]           
Get:68 http://ppa.launchpad.net trusty Release [14.0 kB]                       
Get:69 http://ppa.launchpad.net trusty Release [15.1 kB]                       
Get:70 http://gb.archive.ubuntu.com trusty-updates/restricted i386 Packages [16.9 kB]
Get:71 http://gb.archive.ubuntu.com trusty-updates/universe i386 Packages [420 kB]
Get:72 http://ppa.launchpad.net trusty/main i386 Packages [2,988 B]            
Get:73 http://ppa.launchpad.net trusty/main Translation-en [1,343 B]           
Get:74 http://ppa.launchpad.net trusty Release [15.1 kB]                       
Get:75 http://security.ubuntu.com trusty-security/multiverse Translation-en [2,201 B]
Get:76 http://security.ubuntu.com trusty-security/restricted Translation-en [3,491 B]
Get:77 http://ppa.launchpad.net trusty Release [15.1 kB]                       
Get:78 http://security.ubuntu.com trusty-security/universe Translation-en [102 kB]
Get:79 http://ppa.launchpad.net trusty/main i386 Packages [1,954 B]            
Get:80 http://ppa.launchpad.net trusty/main Translation-en [2,123 B]           
Get:81 http://ppa.launchpad.net trusty/main i386 Packages [594 B]              
Get:82 http://gb.archive.ubuntu.com trusty-updates/multiverse i386 Packages [14.7 kB]
Get:83 http://gb.archive.ubuntu.com trusty-updates/main Translation-en [491 kB]
Get:84 http://ppa.launchpad.net trusty/main Translation-en [429 B]             
Get:85 http://ppa.launchpad.net trusty Release [14.5 kB]                       
Get:86 http://ppa.launchpad.net trusty Release [15.1 kB]                       
Get:87 http://ppa.launchpad.net trusty Release [15.1 kB]                       
Get:88 http://gb.archive.ubuntu.com trusty-updates/multiverse Translation-en [7,430 B]
Get:89 http://ppa.launchpad.net trusty/main i386 Packages [669 B]              
Get:90 http://gb.archive.ubuntu.com trusty-updates/restricted Translation-en [3,978 B]
Get:91 http://gb.archive.ubuntu.com trusty-updates/universe Translation-en [224 kB]
Get:92 http://ppa.launchpad.net trusty/main i386 Packages [5,597 B]            
Get:93 http://ppa.launchpad.net trusty/main Translation-en [3,926 B]           
Get:94 http://ppa.launchpad.net trusty/main i386 Packages [3,707 B]            
Get:95 http://gb.archive.ubuntu.com trusty-backports/main Sources [9,712 B]    
Get:96 http://ppa.launchpad.net trusty/main Translation-en [653 B]             
Get:97 http://gb.archive.ubuntu.com trusty-backports/restricted Sources [28 B] 
Get:98 http://gb.archive.ubuntu.com trusty-backports/universe Sources [35.3 kB]
Get:99 http://ppa.launchpad.net trusty/main i386 Packages [872 B]              
Get:100 http://gb.archive.ubuntu.com trusty-backports/multiverse Sources [1,898 B]
Get:101 http://ppa.launchpad.net trusty/main Translation-en [543 B]            
Get:102 http://gb.archive.ubuntu.com trusty-backports/main i386 Packages [13.3 kB]
Get:103 http://ppa.launchpad.net trusty/main i386 Packages [4,637 B]           
Get:104 http://ppa.launchpad.net trusty/main Translation-en [2,473 B]          
Get:105 http://gb.archive.ubuntu.com trusty-backports/restricted i386 Packages [28 B]
Get:106 http://ppa.launchpad.net trusty/main i386 Packages [624 B]             
Get:107 http://gb.archive.ubuntu.com trusty-backports/universe i386 Packages [43.2 kB]
Get:108 http://ppa.launchpad.net trusty/main Translation-en [177 B]            
Get:109 http://gb.archive.ubuntu.com trusty-backports/multiverse i386 Packages [1,552 B]
Get:110 http://ppa.launchpad.net trusty/main i386 Packages [818 B]             
Get:111 http://ppa.launchpad.net trusty/main Translation-en [1,196 B]          
Get:112 http://gb.archive.ubuntu.com trusty-backports/main Translation-en [7,503 B]
Get:113 http://gb.archive.ubuntu.com trusty-backports/multiverse Translation-en [1,215 B]
Get:114 http://gb.archive.ubuntu.com trusty-backports/restricted Translation-en [28 B]
Get:115 http://gb.archive.ubuntu.com trusty-backports/universe Translation-en [36.8 kB]
Get:116 http://gb.archive.ubuntu.com trusty-proposed/restricted i386 Packages [772 B]
Get:117 http://gb.archive.ubuntu.com trusty-proposed/multiverse i386 Packages [28 B]
Get:118 http://gb.archive.ubuntu.com trusty-proposed/main i386 Packages [87.8 kB]
Ign http://ppa.launchpad.net trusty/main Translation-en_GB                     
Get:119 http://gb.archive.ubuntu.com trusty-proposed/universe i386 Packages [13.1 kB]
Ign http://ppa.launchpad.net trusty/main Translation-en_GB                     
Get:120 http://gb.archive.ubuntu.com trusty-proposed/main Translation-en [29.4 kB]
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Get:121 http://gb.archive.ubuntu.com trusty-proposed/multiverse Translation-en [28 B]
Get:122 http://gb.archive.ubuntu.com trusty-proposed/restricted Translation-en [281 B]
Get:123 http://gb.archive.ubuntu.com trusty-proposed/universe Translation-en [10.5 kB]
Get:124 http://gb.archive.ubuntu.com trusty/main Sources [1,064 kB]            
Get:125 http://gb.archive.ubuntu.com trusty/restricted Sources [5,433 B]       
Get:126 http://gb.archive.ubuntu.com trusty/universe Sources [6,399 kB]        
Ign http://repo.steampowered.com precise/steam Translation-en_GB               
Ign http://repo.steampowered.com precise/steam Translation-en                  
Get:127 http://gb.archive.ubuntu.com trusty/multiverse Sources [174 kB]        
Get:128 http://gb.archive.ubuntu.com trusty/main i386 Packages [1,348 kB]      
Get:129 http://gb.archive.ubuntu.com trusty/restricted i386 Packages [13.4 kB] 
Get:130 http://gb.archive.ubuntu.com trusty/universe i386 Packages [5,866 kB]  
Get:131 http://gb.archive.ubuntu.com trusty/multiverse i386 Packages [134 kB]  
Get:132 http://gb.archive.ubuntu.com trusty/main Translation-en_GB [96.8 kB]   
Get:133 http://gb.archive.ubuntu.com trusty/main Translation-en [762 kB]       
Get:134 http://gb.archive.ubuntu.com trusty/multiverse Translation-en_GB [98.3 kB]
Get:135 http://gb.archive.ubuntu.com trusty/multiverse Translation-en [102 kB] 
Get:136 http://gb.archive.ubuntu.com trusty/restricted Translation-en_GB [3,483 B]
Get:137 http://gb.archive.ubuntu.com trusty/restricted Translation-en [3,457 B]
Get:138 http://gb.archive.ubuntu.com trusty/universe Translation-en_GB [7,557 B]
Get:139 http://gb.archive.ubuntu.com trusty/universe Translation-en [4,089 kB] 
Fetched 25.6 MB in 1min 4s (394 kB/s)                                          
Reading package lists... Error!
W: GPG error: http://deb.opera.com stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D615560BA5C7FF72
W: GPG error: http://ppa.launchpad.net trusty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7F0BB3BE5BF00518
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/www.netfabb.com_debian_dists_stable_non-free_i18n_Translation-en%5fGB
E: The package lists or status file could not be parsed or opened.


```

---

### Post by #&amp;thj^% on 2017-08-02
Do this for me:
```
sudo apt-get install inxi
```
After it is installed run this:
```
inxi -Sr
```

---

### Post by steve234 on 2017-08-02
Sorry man I can't - the whole reason for this post is because I can't install packages:

```
$ sudo apt-get install inxi

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/www.netfabb.com_debian_dists_stable_non-free_i18n_Translation-en%5fGB
E: The package lists or status file could not be parsed or opened.

```

---

### Post by #&amp;thj^% on 2017-08-02
Crap I forgot sorry bout that: ;)
OK lets go this route;
```
cd /etc/apt/sources.list.d
ls
```
Run one line at a time, and paste back

---

### Post by steve234 on 2017-08-02
lol - no worries:

```

$ cd /etc/apt/sources.list.d

/etc/apt/sources.list.d$ ls
dismine-valentina-trusty.list
dismine-valentina-trusty.list.save
eee-control-eee-control-trusty.list
eee-control-eee-control-trusty.list.save
fossfreedom-byzanz-trusty.list
fossfreedom-byzanz-trusty.list.save
freecad-maintainers-freecad-stable-trusty.list
freecad-maintainers-freecad-stable-trusty.list.save
jon-hedgerows-get-iplayer-trusty.list
jon-hedgerows-get-iplayer-trusty.list.save
kilian-f_lux-trusty.list.save
kirillshkrogalev-ffmpeg-next-trusty.list
kirillshkrogalev-ffmpeg-next-trusty.list.save
mc3man-gstffmpeg-keep-trusty.list
mc3man-gstffmpeg-keep-trusty.list.save
midori-ppa-trusty.list
midori-ppa-trusty.list.save
mkusb-ppa-trusty.list
mkusb-ppa-trusty.list.save
nilarimogard-webupd8-trusty.list
nilarimogard-webupd8-trusty.list.save
openjdk-r-ppa-trusty.list
openjdk-r-ppa-trusty.list.save
opera.list
opera.list.save
pj-assis-ppa-trusty.list
pj-assis-ppa-trusty.list.save
spotify.list
spotify.list.save
steam.list
steam.list.save
sunab-kdenlive-release-trusty.list
sunab-kdenlive-release-trusty.list.save
thefanclub-grive-tools-trusty.list
thefanclub-grive-tools-trusty.list.save
thopiekar-cura-trusty.list
thopiekar-cura-trusty.list.save
unit193-xombrero-trusty.list
unit193-xombrero-trusty.list.save
vincent-c-nevernote-trusty.list
vincent-c-nevernote-trusty.list.save
yannubuntu-boot-repair-trusty.list
yannubuntu-boot-repair-trusty.list.save
zarquon42-meshlab-trusty.list
zarquon42-meshlab-trusty.list.save

```

---

### Post by #&amp;thj^% on 2017-08-02
> **steve234 said:**
> lol - no worries:

```

$ cd /etc/apt/sources.list.d

/etc/apt/sources.list.d$ ls
dismine-valentina-trusty.list
dismine-valentina-trusty.list.save
eee-control-eee-control-trusty.list
eee-control-eee-control-trusty.list.save
fossfreedom-byzanz-trusty.list
fossfreedom-byzanz-trusty.list.save
freecad-maintainers-freecad-stable-trusty.list
freecad-maintainers-freecad-stable-trusty.list.save
jon-hedgerows-get-iplayer-trusty.list
jon-hedgerows-get-iplayer-trusty.list.save
kilian-f_lux-trusty.list.save
kirillshkrogalev-ffmpeg-next-trusty.list
kirillshkrogalev-ffmpeg-next-trusty.list.save
mc3man-gstffmpeg-keep-trusty.list
mc3man-gstffmpeg-keep-trusty.list.save
midori-ppa-trusty.list
midori-ppa-trusty.list.save
mkusb-ppa-trusty.list
mkusb-ppa-trusty.list.save
nilarimogard-webupd8-trusty.list
nilarimogard-webupd8-trusty.list.save
openjdk-r-ppa-trusty.list
openjdk-r-ppa-trusty.list.save
opera.list
opera.list.save
pj-assis-ppa-trusty.list
pj-assis-ppa-trusty.list.save
spotify.list
spotify.list.save
steam.list
steam.list.save
sunab-kdenlive-release-trusty.list
sunab-kdenlive-release-trusty.list.save
thefanclub-grive-tools-trusty.list
thefanclub-grive-tools-trusty.list.save
thopiekar-cura-trusty.list
thopiekar-cura-trusty.list.save
unit193-xombrero-trusty.list
unit193-xombrero-trusty.list.save
vincent-c-nevernote-trusty.list
vincent-c-nevernote-trusty.list.save
yannubuntu-boot-repair-trusty.list
yannubuntu-boot-repair-trusty.list.save
zarquon42-meshlab-trusty.list
zarquon42-meshlab-trusty.list.save

```

in that same terminal run this:
```
sudo rm kilian-f_lux-trusty.list.save
```
Now lets have look here:
```
cd /etc/apt
nano sources.list.save
```
paste back

---

### Post by steve234 on 2017-08-02
Cheers:

rm done

```
dismine-valentina-trusty.list
dismine-valentina-trusty.list.save
eee-control-eee-control-trusty.list
eee-control-eee-control-trusty.list.save
fossfreedom-byzanz-trusty.list
fossfreedom-byzanz-trusty.list.save
freecad-maintainers-freecad-stable-trusty.list
freecad-maintainers-freecad-stable-trusty.list.save
jon-hedgerows-get-iplayer-trusty.list
jon-hedgerows-get-iplayer-trusty.list.save
kirillshkrogalev-ffmpeg-next-trusty.list
kirillshkrogalev-ffmpeg-next-trusty.list.save
mc3man-gstffmpeg-keep-trusty.list
mc3man-gstffmpeg-keep-trusty.list.save
midori-ppa-trusty.list
midori-ppa-trusty.list.save
mkusb-ppa-trusty.list
mkusb-ppa-trusty.list.save
nilarimogard-webupd8-trusty.list
nilarimogard-webupd8-trusty.list.save
openjdk-r-ppa-trusty.list
openjdk-r-ppa-trusty.list.save
opera.list
opera.list.save
pj-assis-ppa-trusty.list
pj-assis-ppa-trusty.list.save
spotify.list
spotify.list.save
steam.list
steam.list.save
sunab-kdenlive-release-trusty.list
sunab-kdenlive-release-trusty.list.save
thefanclub-grive-tools-trusty.list
thefanclub-grive-tools-trusty.list.save
thopiekar-cura-trusty.list
thopiekar-cura-trusty.list.save
unit193-xombrero-trusty.list
unit193-xombrero-trusty.list.save
vincent-c-nevernote-trusty.list
vincent-c-nevernote-trusty.list.save
yannubuntu-boot-repair-trusty.list
yannubuntu-boot-repair-trusty.list.save
zarquon42-meshlab-trusty.list
zarquon42-meshlab-trusty.list.save


```


Contents of sources.list.save:

```

# deb cdrom:[Lubuntu 14.04.3 LTS _Trusty Tahr_ - Beta i386 (20150805)]/ trusty main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty universe
deb http://gb.archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse

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
deb http://gb.archive.ubuntu.com/ubuntu/ trusty-proposed restricted multiverse main universe
deb http://www.netfabb.com/debian/ stable non-free
# deb-src http://www.netfabb.com/debian/ stable non-free


```

---

### Post by #&amp;thj^% on 2017-08-02
Cool now we comment out this:
```
deb http://www.netfabb.com/debian/ stable non-free
```
so it looks like this
```
# deb http://www.netfabb.com/debian/ stable non-free
```
By way of 
```
sudo nano sources.list.save
```
next we try to get clean here with:
```
sudo rm /var/lib/apt/lists/* -vf 
```
Now we try again by removing:
```
sudo apt-get remove --purge netfabb studio basic
```
If no errors show run now:
```
sudo apt-get update && sudo apt-get dist-upgrade  

```
Fingers crossed.:)

---

### Post by steve234 on 2017-08-02
Thanks:

My 
sources.list.save file now looks like

```
# deb cdrom:[Lubuntu 14.04.3 LTS _Trusty Tahr_ - Beta i386 (20150805)]/ trusty main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty universe
deb http://gb.archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse

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
deb http://gb.archive.ubuntu.com/ubuntu/ trusty-proposed restricted multiverse main universe
# deb http://www.netfabb.com/debian/ stable non-free
# deb-src http://www.netfabb.com/debian/ stable non-free


```

There was one error rlating to a directory on the rm 

```
$ sudo rm /var/lib/apt/lists/* -vf
removed &#8216;/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_trusty_partner_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_trusty_partner_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_trusty_partner_source_Sources&#8217;
removed &#8216;/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_trusty_Release&#8217;
removed &#8216;/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_trusty_Release.gpg&#8217;
removed &#8216;/var/lib/apt/lists/deb.opera.com_opera_dists_stable_non-free_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/deb.opera.com_opera_dists_stable_Release&#8217;
removed &#8216;/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_trusty_main_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_trusty_main_source_Sources&#8217;
removed &#8216;/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_trusty_Release&#8217;
removed &#8216;/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_trusty_Release.gpg&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-backports_InRelease&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-backports_main_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-backports_main_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-backports_main_source_Sources&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-backports_multiverse_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-backports_multiverse_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-backports_multiverse_source_Sources&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-backports_restricted_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-backports_restricted_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-backports_restricted_source_Sources&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-backports_universe_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-backports_universe_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-backports_universe_source_Sources&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_main_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_main_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_main_i18n_Translation-en%5fGB&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_main_source_Sources&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_multiverse_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_multiverse_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_multiverse_i18n_Translation-en%5fGB&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_multiverse_source_Sources&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-proposed_InRelease&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-proposed_main_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-proposed_main_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-proposed_multiverse_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-proposed_multiverse_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-proposed_restricted_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-proposed_restricted_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-proposed_universe_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-proposed_universe_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_Release&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_Release.gpg&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_restricted_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_restricted_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_restricted_i18n_Translation-en%5fGB&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_restricted_source_Sources&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_universe_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_universe_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_universe_i18n_Translation-en%5fGB&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_universe_source_Sources&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-updates_InRelease&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-updates_main_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-updates_main_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-updates_main_source_Sources&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-updates_multiverse_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-updates_multiverse_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-updates_multiverse_source_Sources&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-updates_restricted_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-updates_restricted_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-updates_restricted_source_Sources&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-updates_universe_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-updates_universe_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-updates_universe_source_Sources&#8217;
removed &#8216;/var/lib/apt/lists/lock&#8217;
rm: cannot remove &#8216;/var/lib/apt/lists/partial&#8217;: Is a directory
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_dismine_valentina_ubuntu_dists_trusty_InRelease&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_dismine_valentina_ubuntu_dists_trusty_main_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_dismine_valentina_ubuntu_dists_trusty_main_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_fossfreedom_byzanz_ubuntu_dists_trusty_main_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_fossfreedom_byzanz_ubuntu_dists_trusty_Release&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_fossfreedom_byzanz_ubuntu_dists_trusty_Release.gpg&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_freecad-maintainers_freecad-stable_ubuntu_dists_trusty_InRelease&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_freecad-maintainers_freecad-stable_ubuntu_dists_trusty_main_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_freecad-maintainers_freecad-stable_ubuntu_dists_trusty_main_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_jon-hedgerows_get-iplayer_ubuntu_dists_trusty_InRelease&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_jon-hedgerows_get-iplayer_ubuntu_dists_trusty_main_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_jon-hedgerows_get-iplayer_ubuntu_dists_trusty_main_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_kirillshkrogalev_ffmpeg-next_ubuntu_dists_trusty_main_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_kirillshkrogalev_ffmpeg-next_ubuntu_dists_trusty_main_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_kirillshkrogalev_ffmpeg-next_ubuntu_dists_trusty_Release&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_kirillshkrogalev_ffmpeg-next_ubuntu_dists_trusty_Release.gpg&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_mc3man_gstffmpeg-keep_ubuntu_dists_trusty_main_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_mc3man_gstffmpeg-keep_ubuntu_dists_trusty_main_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_mc3man_gstffmpeg-keep_ubuntu_dists_trusty_Release&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_mc3man_gstffmpeg-keep_ubuntu_dists_trusty_Release.gpg&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_midori_ppa_ubuntu_dists_trusty_main_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_midori_ppa_ubuntu_dists_trusty_main_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_midori_ppa_ubuntu_dists_trusty_Release&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_midori_ppa_ubuntu_dists_trusty_Release.gpg&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_mkusb_ppa_ubuntu_dists_trusty_InRelease&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_mkusb_ppa_ubuntu_dists_trusty_main_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_mkusb_ppa_ubuntu_dists_trusty_main_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_nilarimogard_webupd8_ubuntu_dists_trusty_InRelease&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_nilarimogard_webupd8_ubuntu_dists_trusty_main_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_nilarimogard_webupd8_ubuntu_dists_trusty_main_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_openjdk-r_ppa_ubuntu_dists_trusty_InRelease&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_openjdk-r_ppa_ubuntu_dists_trusty_main_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_openjdk-r_ppa_ubuntu_dists_trusty_main_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_pj-assis_ppa_ubuntu_dists_trusty_InRelease&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_pj-assis_ppa_ubuntu_dists_trusty_main_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_pj-assis_ppa_ubuntu_dists_trusty_main_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_sunab_kdenlive-release_ubuntu_dists_trusty_main_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_sunab_kdenlive-release_ubuntu_dists_trusty_main_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_sunab_kdenlive-release_ubuntu_dists_trusty_Release&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_sunab_kdenlive-release_ubuntu_dists_trusty_Release.gpg&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_thefanclub_grive-tools_ubuntu_dists_trusty_main_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_thefanclub_grive-tools_ubuntu_dists_trusty_main_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_thefanclub_grive-tools_ubuntu_dists_trusty_Release&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_thefanclub_grive-tools_ubuntu_dists_trusty_Release.gpg&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_unit193_xombrero_ubuntu_dists_trusty_main_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_unit193_xombrero_ubuntu_dists_trusty_main_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_unit193_xombrero_ubuntu_dists_trusty_Release&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_unit193_xombrero_ubuntu_dists_trusty_Release.gpg&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_yannubuntu_boot-repair_ubuntu_dists_trusty_InRelease&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_yannubuntu_boot-repair_ubuntu_dists_trusty_main_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_yannubuntu_boot-repair_ubuntu_dists_trusty_main_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_zarquon42_meshlab_ubuntu_dists_trusty_main_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_zarquon42_meshlab_ubuntu_dists_trusty_main_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_zarquon42_meshlab_ubuntu_dists_trusty_Release&#8217;
removed &#8216;/var/lib/apt/lists/repository.spotify.com_dists_stable_InRelease&#8217;
removed &#8216;/var/lib/apt/lists/repository.spotify.com_dists_stable_non-free_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/repo.steampowered.com_steam_dists_precise_InRelease&#8217;
removed &#8216;/var/lib/apt/lists/repo.steampowered.com_steam_dists_precise_steam_binary-amd64_Packages&#8217;
removed &#8216;/var/lib/apt/lists/repo.steampowered.com_steam_dists_precise_steam_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/repo.steampowered.com_steam_dists_precise_steam_source_Sources&#8217;
removed &#8216;/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_InRelease&#8217;
removed &#8216;/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_main_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_main_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_main_source_Sources&#8217;
removed &#8216;/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_multiverse_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_multiverse_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_multiverse_source_Sources&#8217;
removed &#8216;/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_restricted_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_restricted_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_restricted_source_Sources&#8217;
removed &#8216;/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_universe_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_universe_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_universe_source_Sources&#8217;
removed &#8216;/var/lib/apt/lists/www.netfabb.com_debian_dists_stable_InRelease&#8217;
removed &#8216;/var/lib/apt/lists/www.netfabb.com_debian_dists_stable_non-free_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/www.netfabb.com_debian_dists_stable_non-free_i18n_Translation-en%5fGB&#8217;

:/etc/apt$ sudo rm /var/lib/apt/lists/* -vf
rm: cannot remove &#8216;/var/lib/apt/lists/partial&#8217;: Is a directory


```

and the same errors down the line.

```
:/etc/apt$ sudo apt-get update && sudo apt-get dist-upgrade
Ign http://gb.archive.ubuntu.com trusty InRelease
Get:1 http://repo.steampowered.com precise InRelease [2,842 B]                 
Get:2 http://gb.archive.ubuntu.com trusty-updates InRelease [65.9 kB]          
Ign http://archive.canonical.com trusty InRelease                              
Ign http://extras.ubuntu.com trusty InRelease                                  
Get:3 http://ppa.launchpad.net trusty InRelease [15.5 kB]                      
Get:4 http://deb.opera.com stable InRelease [2,592 B]                          
Get:5 http://www.netfabb.com stable InRelease [1,942 B]                        
Get:6 http://archive.canonical.com trusty Release.gpg [933 B]                  
Get:7 http://extras.ubuntu.com trusty Release.gpg [72 B]                       
Get:8 http://repository.spotify.com stable InRelease [3,302 B]                 
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://deb.opera.com stable InRelease                                      
Get:9 http://extras.ubuntu.com trusty Release [11.9 kB]                        
Get:10 http://gb.archive.ubuntu.com trusty-backports InRelease [65.9 kB]       
Get:11 http://archive.canonical.com trusty Release [9,359 B]                   
Get:12 http://ppa.launchpad.net trusty InRelease [15.5 kB]                     
Get:13 http://security.ubuntu.com trusty-security InRelease [65.9 kB]          
Get:14 http://ppa.launchpad.net trusty InRelease [15.5 kB]                     
Get:15 http://gb.archive.ubuntu.com trusty-proposed InRelease [65.9 kB]        
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:16 http://gb.archive.ubuntu.com trusty Release.gpg [933 B]                 
Get:17 http://www.netfabb.com stable/non-free i386 Packages [596 B]            
Get:18 http://gb.archive.ubuntu.com trusty Release [58.5 kB]                   
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:19 http://ppa.launchpad.net trusty InRelease [16.0 kB]                     
Get:20 http://ppa.launchpad.net trusty InRelease [15.4 kB]                     
Get:21 http://gb.archive.ubuntu.com trusty-updates/main Sources [401 kB]       
Get:22 http://ppa.launchpad.net trusty InRelease [15.5 kB]                     
Get:23 http://repository.spotify.com stable/non-free i386 Packages [1,136 B]   
Get:24 http://ppa.launchpad.net trusty InRelease [15.4 kB]                     
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:25 http://deb.opera.com stable/non-free i386 Packages [1,820 B]            
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:26 http://archive.canonical.com trusty/partner Sources [9,713 B]           
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:27 http://ppa.launchpad.net trusty InRelease [15.5 kB]                     
Get:28 http://repo.steampowered.com precise/steam Sources [550 B]              
Get:29 http://ppa.launchpad.net trusty InRelease [15.4 kB]                     
Get:30 http://archive.canonical.com trusty/partner i386 Packages [5,770 B]     
Get:31 http://extras.ubuntu.com trusty/main Sources [14 B]                     
Get:32 http://repo.steampowered.com precise/steam amd64 Packages [601 B]       
Ign http://deb.opera.com stable/non-free Translation-en_GB                     
Get:33 http://archive.canonical.com trusty/partner Translation-en [4,207 B]    
Get:34 http://repo.steampowered.com precise/steam i386 Packages [799 B]        
Get:35 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Get:36 http://extras.ubuntu.com trusty/main i386 Packages [14 B]               
Ign http://deb.opera.com stable/non-free Translation-en                        
Get:37 http://ppa.launchpad.net trusty/main i386 Packages [560 B]              
Get:38 http://ppa.launchpad.net trusty/main Translation-en [341 B]             
Get:39 http://gb.archive.ubuntu.com trusty-updates/restricted Sources [6,331 B]
Ign http://repository.spotify.com stable/non-free Translation-en_GB            
Get:40 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Get:41 http://gb.archive.ubuntu.com trusty-updates/universe Sources [186 kB]   
Ign http://repository.spotify.com stable/non-free Translation-en               
Get:42 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Get:43 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Ign http://extras.ubuntu.com trusty/main Translation-en_GB                     
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Get:44 http://gb.archive.ubuntu.com trusty-updates/multiverse Sources [7,769 B]
Get:45 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Get:46 http://gb.archive.ubuntu.com trusty-updates/main i386 Packages [950 kB] 
Get:47 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Get:48 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Get:49 http://ppa.launchpad.net trusty Release [14.0 kB]                       
Get:50 http://ppa.launchpad.net trusty/main i386 Packages [4,799 B]            
Get:51 http://ppa.launchpad.net trusty/main Translation-en [3,244 B]           
Get:52 http://ppa.launchpad.net trusty Release [15.1 kB]                       
Get:53 http://ppa.launchpad.net trusty Release [15.1 kB]                       
Get:54 http://ppa.launchpad.net trusty Release [15.1 kB]                       
Get:55 http://ppa.launchpad.net trusty Release [14.5 kB]                       
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:56 http://ppa.launchpad.net trusty Release [15.1 kB]                       
Get:57 http://gb.archive.ubuntu.com trusty-updates/restricted i386 Packages [16.9 kB]
Get:58 http://ppa.launchpad.net trusty Release [15.1 kB]                       
Get:59 http://gb.archive.ubuntu.com trusty-updates/universe i386 Packages [420 kB]
Get:60 http://security.ubuntu.com trusty-security/main Sources [138 kB]        
Get:61 http://ppa.launchpad.net trusty/main i386 Packages [7,012 B]            
Get:62 http://ppa.launchpad.net trusty/main Translation-en [5,526 B]           
Get:63 http://ppa.launchpad.net trusty/main i386 Packages [1,463 B]            
Get:64 http://ppa.launchpad.net trusty/main Translation-en [1,309 B]           
Get:65 http://ppa.launchpad.net trusty/main i386 Packages [39.9 kB]            
Get:66 http://ppa.launchpad.net trusty/main Translation-en [29.3 kB]           
Get:67 http://ppa.launchpad.net trusty/main i386 Packages [4,460 B]            
Get:68 http://gb.archive.ubuntu.com trusty-updates/multiverse i386 Packages [14.7 kB]
Get:69 http://ppa.launchpad.net trusty/main Translation-en [2,502 B]           
Get:70 http://gb.archive.ubuntu.com trusty-updates/main Translation-en [491 kB]
Get:71 http://ppa.launchpad.net trusty/main i386 Packages [2,988 B]            
Get:72 http://ppa.launchpad.net trusty/main Translation-en [1,343 B]           
Get:73 http://ppa.launchpad.net trusty/main i386 Packages [1,954 B]            
Get:74 http://ppa.launchpad.net trusty/main Translation-en [2,123 B]           
Get:75 http://ppa.launchpad.net trusty/main i386 Packages [594 B]              
Get:76 http://security.ubuntu.com trusty-security/restricted Sources [4,955 B] 
Get:77 http://ppa.launchpad.net trusty/main Translation-en [429 B]             
Get:78 http://gb.archive.ubuntu.com trusty-updates/multiverse Translation-en [7,430 B]
Get:79 http://ppa.launchpad.net trusty/main i386 Packages [669 B]              
Get:80 http://gb.archive.ubuntu.com trusty-updates/restricted Translation-en [3,978 B]
Get:81 http://security.ubuntu.com trusty-security/universe Sources [60.3 kB]   
Get:82 http://gb.archive.ubuntu.com trusty-updates/universe Translation-en [224 kB]
Get:83 http://ppa.launchpad.net trusty/main i386 Packages [5,597 B]            
Get:84 http://ppa.launchpad.net trusty/main Translation-en [3,926 B]           
Get:85 http://ppa.launchpad.net trusty/main i386 Packages [3,707 B]            
Get:86 http://ppa.launchpad.net trusty/main Translation-en [653 B]             
Get:87 http://ppa.launchpad.net trusty/main i386 Packages [872 B]              
Get:88 http://security.ubuntu.com trusty-security/multiverse Sources [3,189 B] 
Get:89 http://gb.archive.ubuntu.com trusty-backports/main Sources [9,712 B]    
Get:90 http://ppa.launchpad.net trusty/main Translation-en [543 B]             
Get:91 http://gb.archive.ubuntu.com trusty-backports/restricted Sources [28 B] 
Get:92 http://gb.archive.ubuntu.com trusty-backports/universe Sources [35.3 kB]
Get:93 http://ppa.launchpad.net trusty/main i386 Packages [4,637 B]            
Get:94 http://security.ubuntu.com trusty-security/main i386 Packages [596 kB]  
Get:95 http://gb.archive.ubuntu.com trusty-backports/multiverse Sources [1,898 B]
Get:96 http://gb.archive.ubuntu.com trusty-backports/main i386 Packages [13.3 kB]
Get:97 http://ppa.launchpad.net trusty/main Translation-en [2,473 B]           
Get:98 http://ppa.launchpad.net trusty/main i386 Packages [624 B]              
Get:99 http://ppa.launchpad.net trusty/main Translation-en [177 B]             
Get:100 http://gb.archive.ubuntu.com trusty-backports/restricted i386 Packages [28 B]
Get:101 http://gb.archive.ubuntu.com trusty-backports/universe i386 Packages [43.2 kB]
Get:102 http://ppa.launchpad.net trusty/main i386 Packages [818 B]             
Get:103 http://gb.archive.ubuntu.com trusty-backports/multiverse i386 Packages [1,552 B]
Get:104 http://ppa.launchpad.net trusty/main Translation-en [1,196 B]          
Get:105 http://gb.archive.ubuntu.com trusty-backports/main Translation-en [7,503 B]
Get:106 http://gb.archive.ubuntu.com trusty-backports/multiverse Translation-en [1,215 B]
Get:107 http://gb.archive.ubuntu.com trusty-backports/restricted Translation-en [28 B]
Ign http://ppa.launchpad.net trusty/main Translation-en_GB                     
Get:108 http://security.ubuntu.com trusty-security/restricted i386 Packages [13.7 kB]
Get:109 http://gb.archive.ubuntu.com trusty-backports/universe Translation-en [36.8 kB]
Ign http://ppa.launchpad.net trusty/main Translation-en_GB                     
Get:110 http://security.ubuntu.com trusty-security/universe i386 Packages [179 kB]
Get:111 http://gb.archive.ubuntu.com trusty-proposed/restricted i386 Packages [772 B]
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Get:112 http://gb.archive.ubuntu.com trusty-proposed/multiverse i386 Packages [28 B]
Get:113 http://gb.archive.ubuntu.com trusty-proposed/main i386 Packages [87.8 kB]
Get:114 http://security.ubuntu.com trusty-security/multiverse i386 Packages [4,288 B]
Get:115 http://gb.archive.ubuntu.com trusty-proposed/universe i386 Packages [13.1 kB]
Get:116 http://gb.archive.ubuntu.com trusty-proposed/main Translation-en [29.4 kB]
Get:117 http://security.ubuntu.com trusty-security/main Translation-en [345 kB]
Get:118 http://gb.archive.ubuntu.com trusty-proposed/multiverse Translation-en [28 B]
Get:119 http://gb.archive.ubuntu.com trusty-proposed/restricted Translation-en [281 B]
Get:120 http://gb.archive.ubuntu.com trusty-proposed/universe Translation-en [10.5 kB]
Get:121 http://gb.archive.ubuntu.com trusty/main Sources [1,064 kB]            
Get:122 http://security.ubuntu.com trusty-security/multiverse Translation-en [2,201 B]
Get:123 http://security.ubuntu.com trusty-security/restricted Translation-en [3,491 B]
Get:124 http://security.ubuntu.com trusty-security/universe Translation-en [102 kB]
Ign http://repo.steampowered.com precise/steam Translation-en_GB               
Get:125 http://gb.archive.ubuntu.com trusty/restricted Sources [5,433 B]       
Get:126 http://gb.archive.ubuntu.com trusty/universe Sources [6,399 kB]        
Ign http://repo.steampowered.com precise/steam Translation-en                  
Get:127 http://gb.archive.ubuntu.com trusty/multiverse Sources [174 kB]        
Get:128 http://gb.archive.ubuntu.com trusty/main i386 Packages [1,348 kB]      
Get:129 http://gb.archive.ubuntu.com trusty/restricted i386 Packages [13.4 kB] 
Get:130 http://gb.archive.ubuntu.com trusty/universe i386 Packages [5,866 kB]  
Get:131 http://gb.archive.ubuntu.com trusty/multiverse i386 Packages [134 kB]  
Get:132 http://gb.archive.ubuntu.com trusty/main Translation-en_GB [96.8 kB]   
Get:133 http://gb.archive.ubuntu.com trusty/main Translation-en [762 kB]       
Get:134 http://gb.archive.ubuntu.com trusty/multiverse Translation-en_GB [98.3 kB]
Get:135 http://gb.archive.ubuntu.com trusty/multiverse Translation-en [102 kB] 
Get:136 http://gb.archive.ubuntu.com trusty/restricted Translation-en_GB [3,483 B]
Get:137 http://gb.archive.ubuntu.com trusty/restricted Translation-en [3,457 B]
Get:138 http://gb.archive.ubuntu.com trusty/universe Translation-en_GB [7,557 B]
Get:139 http://gb.archive.ubuntu.com trusty/universe Translation-en [4,089 kB] 
Fetched 25.6 MB in 57s (446 kB/s)                                              
Reading package lists... Error!
W:  GPG error: http://deb.opera.com stable InRelease: The following  signatures couldn't be verified because the public key is not available:  NO_PUBKEY D615560BA5C7FF72
W: GPG error: http://ppa.launchpad.net  trusty InRelease: The following signatures couldn't be verified because  the public key is not available: NO_PUBKEY 7F0BB3BE5BF00518
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/www.netfabb.com_debian_dists_stable_non-free_i18n_Translation-en%5fGB
E: The package lists or status file could not be parsed or opened.

```

---

### Post by steve234 on 2017-08-02
oops missed the purge step - that throws errors...

```
$ sudo apt-get remove --purge netfabb studio basic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package netfabb
E: Unable to locate package studio
E: Unable to locate package basic

```

Will be sleep time soon here - happy to pick up tomorrow....

---

### Post by #&amp;thj^% on 2017-08-02
Did you run this:
```
sudo apt-get remove --purge netfabb studio basic
```

---

### Post by steve234 on 2017-08-02
Sorry - think our posts crossed - I missed that step, but it produced errors - do i need to escapre the spaces?

```
$ sudo apt-get remove --purge netfabb studio basic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package netfabb
E: Unable to locate package studio
E: Unable to locate package basic

```

defo sleep time soon here

---

### Post by #&amp;thj^% on 2017-08-02
No you did it right...but do you remember how you installed that netfabb studio, as I was guessing there.(For the name)
Maybe open synaptic and search for that and choose to completely remove it.
And then you will have to run again:
```
sudo rm /var/lib/apt/lists/* -vf
```

---

### Post by steve234 on 2017-08-03
I installed netfabb to help with mesh manipulation for 3d printing, but never used it. I revisited the install instructions online and it seems I would have used synaptic [https://www.netfabb.com/blog/best-practices-installing-and-upgrading-netfabb-studio-basic-linux](https://www.netfabb.com/blog/best-practices-installing-and-upgrading-netfabb-studio-basic-linux)

Opening synaptic fails unless I do do from the cli (with sudo). It gives two errors:

One in the terminal window:

```
** (synaptic:24990): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-jRO3XbM68A: Connection refused

```

and one in a pop-up:

```
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/www.netfabb.com_debian_dists_stable_non-free_i18n_Translation-en%5fGB
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.
```

Once the pop-up is acknowleged it closes.

---

### Post by steve234 on 2017-08-03
Was looking promisingI'd removed netfabb-basic when I did another of these:

```

$ sudo rm -vf /var/lib/apt/lists/*

removed ‘/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_trusty_partner_binary-i386_Packages’
removed ‘/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_trusty_partner_i18n_Translation-en’
removed ‘/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_trusty_partner_source_Sources’
removed ‘/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_trusty_Release’
removed ‘/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_trusty_Release.gpg’
removed ‘/var/lib/apt/lists/deb.opera.com_opera_dists_stable_non-free_binary-i386_Packages’
removed ‘/var/lib/apt/lists/deb.opera.com_opera_dists_stable_Release’
removed ‘/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_trusty_main_binary-i386_Packages’
removed ‘/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_trusty_main_source_Sources’
removed ‘/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_trusty_Release’
removed ‘/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_trusty_Release.gpg’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-backports_InRelease’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-backports_main_binary-i386_Packages’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-backports_main_i18n_Translation-en’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-backports_main_source_Sources’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-backports_multiverse_binary-i386_Packages’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-backports_multiverse_i18n_Translation-en’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-backports_multiverse_source_Sources’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-backports_restricted_binary-i386_Packages’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-backports_restricted_i18n_Translation-en’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-backports_restricted_source_Sources’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-backports_universe_binary-i386_Packages’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-backports_universe_i18n_Translation-en’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-backports_universe_source_Sources’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_main_binary-i386_Packages’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_main_i18n_Translation-en’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_main_i18n_Translation-en%5fGB’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_main_source_Sources’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_multiverse_binary-i386_Packages’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_multiverse_i18n_Translation-en’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_multiverse_i18n_Translation-en%5fGB’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_multiverse_source_Sources’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-proposed_InRelease’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-proposed_main_binary-i386_Packages’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-proposed_main_i18n_Translation-en’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-proposed_multiverse_binary-i386_Packages’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-proposed_multiverse_i18n_Translation-en’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-proposed_restricted_binary-i386_Packages’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-proposed_restricted_i18n_Translation-en’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-proposed_universe_binary-i386_Packages’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-proposed_universe_i18n_Translation-en’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_Release’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_Release.gpg’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_restricted_binary-i386_Packages’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_restricted_i18n_Translation-en’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_restricted_i18n_Translation-en%5fGB’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_restricted_source_Sources’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_universe_binary-i386_Packages’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_universe_i18n_Translation-en’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_universe_i18n_Translation-en%5fGB’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_universe_source_Sources’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-updates_InRelease’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-updates_main_binary-i386_Packages’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-updates_main_i18n_Translation-en’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-updates_main_source_Sources’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-updates_multiverse_binary-i386_Packages’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-updates_multiverse_i18n_Translation-en’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-updates_multiverse_source_Sources’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-updates_restricted_binary-i386_Packages’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-updates_restricted_i18n_Translation-en’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-updates_restricted_source_Sources’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-updates_universe_binary-i386_Packages’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-updates_universe_i18n_Translation-en’
removed ‘/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-updates_universe_source_Sources’
removed ‘/var/lib/apt/lists/lock’
rm: cannot remove ‘/var/lib/apt/lists/partial’: Is a directory
removed ‘/var/lib/apt/lists/ppa.launchpad.net_dismine_valentina_ubuntu_dists_trusty_InRelease’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_dismine_valentina_ubuntu_dists_trusty_main_binary-i386_Packages’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_dismine_valentina_ubuntu_dists_trusty_main_i18n_Translation-en’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_fossfreedom_byzanz_ubuntu_dists_trusty_main_binary-i386_Packages’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_fossfreedom_byzanz_ubuntu_dists_trusty_Release’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_fossfreedom_byzanz_ubuntu_dists_trusty_Release.gpg’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_freecad-maintainers_freecad-stable_ubuntu_dists_trusty_InRelease’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_freecad-maintainers_freecad-stable_ubuntu_dists_trusty_main_binary-i386_Packages’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_freecad-maintainers_freecad-stable_ubuntu_dists_trusty_main_i18n_Translation-en’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_jon-hedgerows_get-iplayer_ubuntu_dists_trusty_InRelease’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_jon-hedgerows_get-iplayer_ubuntu_dists_trusty_main_binary-i386_Packages’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_jon-hedgerows_get-iplayer_ubuntu_dists_trusty_main_i18n_Translation-en’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_kirillshkrogalev_ffmpeg-next_ubuntu_dists_trusty_main_binary-i386_Packages’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_kirillshkrogalev_ffmpeg-next_ubuntu_dists_trusty_main_i18n_Translation-en’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_kirillshkrogalev_ffmpeg-next_ubuntu_dists_trusty_Release’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_kirillshkrogalev_ffmpeg-next_ubuntu_dists_trusty_Release.gpg’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_mc3man_gstffmpeg-keep_ubuntu_dists_trusty_main_binary-i386_Packages’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_mc3man_gstffmpeg-keep_ubuntu_dists_trusty_main_i18n_Translation-en’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_mc3man_gstffmpeg-keep_ubuntu_dists_trusty_Release’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_mc3man_gstffmpeg-keep_ubuntu_dists_trusty_Release.gpg’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_midori_ppa_ubuntu_dists_trusty_main_binary-i386_Packages’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_midori_ppa_ubuntu_dists_trusty_main_i18n_Translation-en’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_midori_ppa_ubuntu_dists_trusty_Release’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_midori_ppa_ubuntu_dists_trusty_Release.gpg’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_mkusb_ppa_ubuntu_dists_trusty_InRelease’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_mkusb_ppa_ubuntu_dists_trusty_main_binary-i386_Packages’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_mkusb_ppa_ubuntu_dists_trusty_main_i18n_Translation-en’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_nilarimogard_webupd8_ubuntu_dists_trusty_InRelease’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_nilarimogard_webupd8_ubuntu_dists_trusty_main_binary-i386_Packages’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_nilarimogard_webupd8_ubuntu_dists_trusty_main_i18n_Translation-en’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_openjdk-r_ppa_ubuntu_dists_trusty_InRelease’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_openjdk-r_ppa_ubuntu_dists_trusty_main_binary-i386_Packages’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_openjdk-r_ppa_ubuntu_dists_trusty_main_i18n_Translation-en’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_pj-assis_ppa_ubuntu_dists_trusty_InRelease’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_pj-assis_ppa_ubuntu_dists_trusty_main_binary-i386_Packages’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_pj-assis_ppa_ubuntu_dists_trusty_main_i18n_Translation-en’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_sunab_kdenlive-release_ubuntu_dists_trusty_main_binary-i386_Packages’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_sunab_kdenlive-release_ubuntu_dists_trusty_main_i18n_Translation-en’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_sunab_kdenlive-release_ubuntu_dists_trusty_Release’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_sunab_kdenlive-release_ubuntu_dists_trusty_Release.gpg’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_thefanclub_grive-tools_ubuntu_dists_trusty_main_binary-i386_Packages’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_thefanclub_grive-tools_ubuntu_dists_trusty_main_i18n_Translation-en’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_thefanclub_grive-tools_ubuntu_dists_trusty_Release’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_thefanclub_grive-tools_ubuntu_dists_trusty_Release.gpg’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_unit193_xombrero_ubuntu_dists_trusty_main_binary-i386_Packages’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_unit193_xombrero_ubuntu_dists_trusty_main_i18n_Translation-en’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_unit193_xombrero_ubuntu_dists_trusty_Release’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_unit193_xombrero_ubuntu_dists_trusty_Release.gpg’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_yannubuntu_boot-repair_ubuntu_dists_trusty_InRelease’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_yannubuntu_boot-repair_ubuntu_dists_trusty_main_binary-i386_Packages’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_yannubuntu_boot-repair_ubuntu_dists_trusty_main_i18n_Translation-en’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_zarquon42_meshlab_ubuntu_dists_trusty_main_binary-i386_Packages’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_zarquon42_meshlab_ubuntu_dists_trusty_main_i18n_Translation-en’
removed ‘/var/lib/apt/lists/ppa.launchpad.net_zarquon42_meshlab_ubuntu_dists_trusty_Release’
removed ‘/var/lib/apt/lists/repository.spotify.com_dists_stable_InRelease’
removed ‘/var/lib/apt/lists/repository.spotify.com_dists_stable_non-free_binary-i386_Packages’
removed ‘/var/lib/apt/lists/repo.steampowered.com_steam_dists_precise_InRelease’
removed ‘/var/lib/apt/lists/repo.steampowered.com_steam_dists_precise_steam_binary-amd64_Packages’
removed ‘/var/lib/apt/lists/repo.steampowered.com_steam_dists_precise_steam_binary-i386_Packages’
removed ‘/var/lib/apt/lists/repo.steampowered.com_steam_dists_precise_steam_source_Sources’
removed ‘/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_InRelease’
removed ‘/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_main_binary-i386_Packages’
removed ‘/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_main_i18n_Translation-en’
removed ‘/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_main_source_Sources’
removed ‘/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_multiverse_binary-i386_Packages’
removed ‘/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_multiverse_i18n_Translation-en’
removed ‘/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_multiverse_source_Sources’
removed ‘/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_restricted_binary-i386_Packages’
removed ‘/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_restricted_i18n_Translation-en’
removed ‘/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_restricted_source_Sources’
removed ‘/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_universe_binary-i386_Packages’
removed ‘/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_universe_i18n_Translation-en’
removed ‘/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_universe_source_Sources’
removed ‘/var/lib/apt/lists/www.netfabb.com_debian_dists_stable_InRelease’
removed ‘/var/lib/apt/lists/www.netfabb.com_debian_dists_stable_non-free_binary-i386_Packages’
removed ‘/var/lib/apt/lists/www.netfabb.com_debian_dists_stable_non-free_i18n_Translation-en%5fGB’

$ sudo apt-get purge netfabb-basic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  netfabb-basic*
0 to upgrade, 0 to newly install, 1 to remove and 0 not to upgrade.
After this operation, 15.7 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 663495 files and directories currently installed.)
Removing netfabb-basic (5.2.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...

```

but the apt-get update failed again!

```

$ sudo apt-get update
Ign http://archive.canonical.com trusty InRelease
Get:1 http://security.ubuntu.com trusty-security InRelease [65.9 kB]           
Get:2 http://repo.steampowered.com precise InRelease [2,842 B]                 
Get:3 http://ppa.launchpad.net trusty InRelease [15.5 kB]                      
Ign http://gb.archive.ubuntu.com trusty InRelease                              
Get:4 http://repository.spotify.com stable InRelease [3,302 B]                 
Ign http://extras.ubuntu.com trusty InRelease                                  
Get:5 http://deb.opera.com stable InRelease [2,592 B]                          
Get:6 http://gb.archive.ubuntu.com trusty-updates InRelease [65.9 kB]          
Get:7 http://www.netfabb.com stable InRelease [1,942 B]                        
Get:8 http://extras.ubuntu.com trusty Release.gpg [72 B]                       
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:9 http://ppa.launchpad.net trusty InRelease [15.5 kB]                      
Get:10 http://extras.ubuntu.com trusty Release [11.9 kB]                       
Get:11 http://gb.archive.ubuntu.com trusty-backports InRelease [65.9 kB]       
Get:12 http://ppa.launchpad.net trusty InRelease [15.5 kB]                     
Get:13 http://repository.spotify.com stable/non-free i386 Packages [1,136 B]   
Get:14 http://gb.archive.ubuntu.com trusty-proposed InRelease [65.9 kB]        
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:15 http://archive.canonical.com trusty Release.gpg [933 B]                 
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:16 http://archive.canonical.com trusty Release [9,359 B]                   
Ign http://deb.opera.com stable InRelease                                      
Get:17 http://gb.archive.ubuntu.com trusty Release.gpg [933 B]                 
Get:18 http://ppa.launchpad.net trusty InRelease [16.0 kB]                     
Get:19 http://gb.archive.ubuntu.com trusty Release [58.5 kB]                   
Get:20 http://ppa.launchpad.net trusty InRelease [15.4 kB]                     
Get:21 http://www.netfabb.com stable/non-free i386 Packages [596 B]            
Get:22 http://repo.steampowered.com precise/steam Sources [550 B]              
Get:23 http://gb.archive.ubuntu.com trusty-updates/main Sources [401 kB]       
Get:24 http://security.ubuntu.com trusty-security/main Sources [138 kB]        
Get:25 http://extras.ubuntu.com trusty/main Sources [14 B]                     
Get:26 http://ppa.launchpad.net trusty InRelease [15.5 kB]                     
Get:27 http://extras.ubuntu.com trusty/main i386 Packages [14 B]               
Get:28 http://ppa.launchpad.net trusty InRelease [15.4 kB]                     
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:29 http://gb.archive.ubuntu.com trusty-updates/restricted Sources [6,331 B]
Get:30 http://security.ubuntu.com trusty-security/restricted Sources [4,955 B] 
Get:31 http://ppa.launchpad.net trusty InRelease [15.5 kB]                     
Get:32 http://gb.archive.ubuntu.com trusty-updates/universe Sources [186 kB]   
Get:33 http://archive.canonical.com trusty/partner Sources [9,713 B]           
Get:34 http://security.ubuntu.com trusty-security/universe Sources [60.3 kB]   
Get:35 http://repo.steampowered.com precise/steam amd64 Packages [601 B]       
Ign http://repository.spotify.com stable/non-free Translation-en_GB            
Get:36 http://archive.canonical.com trusty/partner i386 Packages [5,770 B]     
Ign http://repository.spotify.com stable/non-free Translation-en               
Get:37 http://archive.canonical.com trusty/partner Translation-en [4,207 B]    
Get:38 http://ppa.launchpad.net trusty InRelease [15.4 kB]                     
Ign http://extras.ubuntu.com trusty/main Translation-en_GB                     
Get:39 http://security.ubuntu.com trusty-security/multiverse Sources [3,189 B] 
Get:40 http://security.ubuntu.com trusty-security/main i386 Packages [597 kB]  
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Get:41 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Get:42 http://deb.opera.com stable/non-free i386 Packages [1,820 B]            
Get:43 http://ppa.launchpad.net trusty/main i386 Packages [560 B]              
Get:44 http://ppa.launchpad.net trusty/main Translation-en [341 B]             
Get:45 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Get:46 http://gb.archive.ubuntu.com trusty-updates/multiverse Sources [7,769 B]
Get:47 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Ign http://deb.opera.com stable/non-free Translation-en_GB                     
Get:48 http://gb.archive.ubuntu.com trusty-updates/main i386 Packages [951 kB] 
Get:49 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Ign http://deb.opera.com stable/non-free Translation-en                        
Get:50 http://repo.steampowered.com precise/steam i386 Packages [799 B]        
Get:51 http://ppa.launchpad.net trusty/main i386 Packages [4,799 B]            
Get:52 http://ppa.launchpad.net trusty/main Translation-en [3,244 B]           
Get:53 http://ppa.launchpad.net trusty/main i386 Packages [7,012 B]            
Get:54 http://ppa.launchpad.net trusty/main Translation-en [5,526 B]           
Get:55 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Get:56 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Get:57 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Get:58 http://ppa.launchpad.net trusty/main i386 Packages [1,463 B]            
Get:59 http://ppa.launchpad.net trusty/main Translation-en [1,309 B]           
Get:60 http://ppa.launchpad.net trusty Release [14.0 kB]                       
Get:61 http://ppa.launchpad.net trusty Release [15.1 kB]                       
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:62 http://ppa.launchpad.net trusty Release [15.1 kB]                       
Get:63 http://security.ubuntu.com trusty-security/restricted i386 Packages [13.7 kB]
Get:64 http://ppa.launchpad.net trusty/main i386 Packages [39.9 kB]            
Get:65 http://security.ubuntu.com trusty-security/universe i386 Packages [179 kB]
Get:66 http://ppa.launchpad.net trusty/main Translation-en [29.3 kB]           
Get:67 http://ppa.launchpad.net trusty Release [15.1 kB]                       
Get:68 http://ppa.launchpad.net trusty/main i386 Packages [4,460 B]            
Get:69 http://ppa.launchpad.net trusty/main Translation-en [2,502 B]           
Get:70 http://security.ubuntu.com trusty-security/multiverse i386 Packages [4,288 B]
Get:71 http://ppa.launchpad.net trusty Release [14.5 kB]                       
Get:72 http://security.ubuntu.com trusty-security/main Translation-en [346 kB] 
Get:73 http://ppa.launchpad.net trusty Release [15.1 kB]                       
Get:74 http://gb.archive.ubuntu.com trusty-updates/restricted i386 Packages [16.9 kB]
Get:75 http://gb.archive.ubuntu.com trusty-updates/universe i386 Packages [420 kB]
Get:76 http://ppa.launchpad.net trusty Release [15.1 kB]                       
Get:77 http://ppa.launchpad.net trusty/main i386 Packages [2,988 B]            
Get:78 http://ppa.launchpad.net trusty/main Translation-en [1,343 B]           
Get:79 http://ppa.launchpad.net trusty/main i386 Packages [1,954 B]            
Get:80 http://ppa.launchpad.net trusty/main Translation-en [2,123 B]           
Get:81 http://ppa.launchpad.net trusty/main i386 Packages [594 B]              
Get:82 http://security.ubuntu.com trusty-security/multiverse Translation-en [2,201 B]
Get:83 http://gb.archive.ubuntu.com trusty-updates/multiverse i386 Packages [14.7 kB]
Get:84 http://security.ubuntu.com trusty-security/restricted Translation-en [3,491 B]
Get:85 http://gb.archive.ubuntu.com trusty-updates/main Translation-en [492 kB]
Get:86 http://ppa.launchpad.net trusty/main Translation-en [429 B]             
Get:87 http://security.ubuntu.com trusty-security/universe Translation-en [102 kB]
Get:88 http://ppa.launchpad.net trusty/main i386 Packages [669 B]              
Get:89 http://ppa.launchpad.net trusty/main i386 Packages [5,597 B]            
Get:90 http://ppa.launchpad.net trusty/main Translation-en [3,926 B]           
Get:91 http://ppa.launchpad.net trusty/main i386 Packages [3,707 B]            
Get:92 http://ppa.launchpad.net trusty/main Translation-en [653 B]             
Get:93 http://gb.archive.ubuntu.com trusty-updates/multiverse Translation-en [7,430 B]
Get:94 http://ppa.launchpad.net trusty/main i386 Packages [872 B]              
Get:95 http://gb.archive.ubuntu.com trusty-updates/restricted Translation-en [3,978 B]
Get:96 http://ppa.launchpad.net trusty/main Translation-en [543 B]             
Get:97 http://gb.archive.ubuntu.com trusty-updates/universe Translation-en [224 kB]
Get:98 http://gb.archive.ubuntu.com trusty-backports/main Sources [9,712 B]    
Get:99 http://ppa.launchpad.net trusty/main i386 Packages [4,637 B]            
Get:100 http://gb.archive.ubuntu.com trusty-backports/restricted Sources [28 B]
Get:101 http://gb.archive.ubuntu.com trusty-backports/universe Sources [35.3 kB]
Get:102 http://ppa.launchpad.net trusty/main Translation-en [2,473 B]          
Get:103 http://gb.archive.ubuntu.com trusty-backports/multiverse Sources [1,898 B]
Get:104 http://gb.archive.ubuntu.com trusty-backports/main i386 Packages [13.3 kB]
Get:105 http://gb.archive.ubuntu.com trusty-backports/restricted i386 Packages [28 B]
Get:106 http://ppa.launchpad.net trusty/main i386 Packages [624 B]             
Get:107 http://gb.archive.ubuntu.com trusty-backports/universe i386 Packages [43.2 kB]
Get:108 http://gb.archive.ubuntu.com trusty-backports/multiverse i386 Packages [1,552 B]
Get:109 http://ppa.launchpad.net trusty/main Translation-en [177 B]            
Get:110 http://gb.archive.ubuntu.com trusty-backports/main Translation-en [7,503 B]
Get:111 http://ppa.launchpad.net trusty/main i386 Packages [818 B]             
Get:112 http://gb.archive.ubuntu.com trusty-backports/multiverse Translation-en [1,215 B]
Get:113 http://ppa.launchpad.net trusty/main Translation-en [1,196 B]          
Get:114 http://gb.archive.ubuntu.com trusty-backports/restricted Translation-en [28 B]
Get:115 http://gb.archive.ubuntu.com trusty-backports/universe Translation-en [36.8 kB]
Get:116 http://gb.archive.ubuntu.com trusty-proposed/restricted i386 Packages [772 B]
Get:117 http://gb.archive.ubuntu.com trusty-proposed/multiverse i386 Packages [28 B]
Get:118 http://gb.archive.ubuntu.com trusty-proposed/main i386 Packages [88.9 kB]
Get:119 http://gb.archive.ubuntu.com trusty-proposed/universe i386 Packages [13.1 kB]
Get:120 http://gb.archive.ubuntu.com trusty-proposed/main Translation-en [30.5 kB]
Get:121 http://gb.archive.ubuntu.com trusty-proposed/multiverse Translation-en [28 B]
Ign http://ppa.launchpad.net trusty/main Translation-en_GB                     
Get:122 http://gb.archive.ubuntu.com trusty-proposed/restricted Translation-en [281 B]
Ign http://ppa.launchpad.net trusty/main Translation-en_GB                     
Get:123 http://gb.archive.ubuntu.com trusty-proposed/universe Translation-en [10.5 kB]
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Get:124 http://gb.archive.ubuntu.com trusty/main Sources [1,064 kB]    
Get:125 http://gb.archive.ubuntu.com trusty/restricted Sources [5,433 B]       
Get:126 http://gb.archive.ubuntu.com trusty/universe Sources [6,399 kB]        
Ign http://repo.steampowered.com precise/steam Translation-en_GB               
Ign http://repo.steampowered.com precise/steam Translation-en                  
Get:127 http://gb.archive.ubuntu.com trusty/multiverse Sources [174 kB]        
Get:128 http://gb.archive.ubuntu.com trusty/main i386 Packages [1,348 kB]      
Get:129 http://gb.archive.ubuntu.com trusty/restricted i386 Packages [13.4 kB] 
Get:130 http://gb.archive.ubuntu.com trusty/universe i386 Packages [5,866 kB]  
Get:131 http://gb.archive.ubuntu.com trusty/multiverse i386 Packages [134 kB]  
Get:132 http://gb.archive.ubuntu.com trusty/main Translation-en_GB [96.8 kB]   
Get:133 http://gb.archive.ubuntu.com trusty/main Translation-en [762 kB]       
Get:134 http://gb.archive.ubuntu.com trusty/multiverse Translation-en_GB [98.3 kB]
Get:135 http://gb.archive.ubuntu.com trusty/multiverse Translation-en [102 kB] 
Get:136 http://gb.archive.ubuntu.com trusty/restricted Translation-en_GB [3,483 B]
Get:137 http://gb.archive.ubuntu.com trusty/restricted Translation-en [3,457 B]
Get:138 http://gb.archive.ubuntu.com trusty/universe Translation-en_GB [7,557 B]
Get:139 http://gb.archive.ubuntu.com trusty/universe Translation-en [4,089 kB] 
Fetched 25.6 MB in 1min 7s (378 kB/s)                                          
Reading package lists... Error!
W: GPG error: http://deb.opera.com stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D615560BA5C7FF72
W: GPG error: http://ppa.launchpad.net trusty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7F0BB3BE5BF00518
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/www.netfabb.com_debian_dists_stable_non-free_i18n_Translation-en%5fGB
E: The package lists or status file could not be parsed or opened.

```

Both synaptic and Ubuntu Software Centre crash on startup (see post above)...

Really confused by this now - how did my system go from fine to jacked-up. It's only had normal use.

---

### Post by deadflowr on 2017-08-03
Well, seems you still have the pubkey error showing,
so try this
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys D615560BA5C7FF72 7F0BB3BE5BF00518
```
which should clear up the 2 gpg errors.
then see what sudo apt-get update does.

---

### Post by steve234 on 2017-08-03
Result of that - with an "rm lists" thrown in for good measure:

```
$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys D615560BA5C7FF72 7F0BB3BE5BF00518

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --homedir /tmp/tmp.pv9XVXcsXm --no-auto-check-trustdb --trust-model always --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyring /etc/apt/trusted.gpg.d/dismine-valentina.gpg --keyring /etc/apt/trusted.gpg.d/eee-control-eee-control.gpg --keyring /etc/apt/trusted.gpg.d/fossfreedom-byzanz.gpg --keyring /etc/apt/trusted.gpg.d/freecad-maintainers-freecad-stable.gpg --keyring /etc/apt/trusted.gpg.d/jon-hedgerows-get-iplayer.gpg --keyring /etc/apt/trusted.gpg.d/kilian-f_lux.gpg --keyring /etc/apt/trusted.gpg.d/kirillshkrogalev-ffmpeg-next.gpg --keyring /etc/apt/trusted.gpg.d/mc3man-gstffmpeg-keep.gpg --keyring /etc/apt/trusted.gpg.d/midori-ppa.gpg --keyring /etc/apt/trusted.gpg.d/mkusb-ppa.gpg --keyring /etc/apt/trusted.gpg.d/nilarimogard-webupd8.gpg --keyring /etc/apt/trusted.gpg.d/openjdk-r-ppa.gpg --keyring /etc/apt/trusted.gpg.d/pj-assis-ppa.gpg --keyring /etc/apt/trusted.gpg.d/spotify-2015-05-28-D2C19886.gpg --keyring /etc/apt/trusted.gpg.d/steam.gpg --keyring /etc/apt/trusted.gpg.d/sunab-kdenlive-release.gpg --keyring /etc/apt/trusted.gpg.d/thefanclub-grive-tools.gpg --keyring /etc/apt/trusted.gpg.d/thopiekar-cura.gpg --keyring /etc/apt/trusted.gpg.d/unit193-xombrero.gpg --keyring /etc/apt/trusted.gpg.d/yannubuntu-boot-repair.gpg --keyserver keyserver.ubuntu.com --recv-keys D615560BA5C7FF72 7F0BB3BE5BF00518
gpg: requesting key A5C7FF72 from hkp server keyserver.ubuntu.com
gpg: requesting key 5BF00518 from hkp server keyserver.ubuntu.com
gpg: key A5C7FF72: public key "Opera Software Archive Automatic Signing Key 2017 <packager@opera.com>" imported
gpg: key 5BF00518: public key "Launchpad PPA for zarquon42" imported
gpg: Total number processed: 2
gpg:               imported: 2  (RSA: 2)

$ sudo rm /var/lib/apt/lists/* -vfremoved &#8216;/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_trusty_partner_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_trusty_partner_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_trusty_partner_source_Sources&#8217;
removed &#8216;/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_trusty_Release&#8217;
removed &#8216;/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_trusty_Release.gpg&#8217;
removed &#8216;/var/lib/apt/lists/deb.opera.com_opera_dists_stable_non-free_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/deb.opera.com_opera_dists_stable_Release&#8217;
removed &#8216;/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_trusty_main_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_trusty_main_source_Sources&#8217;
removed &#8216;/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_trusty_Release&#8217;
removed &#8216;/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_trusty_Release.gpg&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-backports_InRelease&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-backports_main_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-backports_main_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-backports_main_source_Sources&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-backports_multiverse_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-backports_multiverse_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-backports_multiverse_source_Sources&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-backports_restricted_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-backports_restricted_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-backports_restricted_source_Sources&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-backports_universe_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-backports_universe_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-backports_universe_source_Sources&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_main_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_main_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_main_i18n_Translation-en%5fGB&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_main_source_Sources&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_multiverse_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_multiverse_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_multiverse_i18n_Translation-en%5fGB&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_multiverse_source_Sources&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-proposed_InRelease&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-proposed_main_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-proposed_main_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-proposed_multiverse_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-proposed_multiverse_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-proposed_restricted_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-proposed_restricted_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-proposed_universe_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-proposed_universe_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_Release&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_Release.gpg&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_restricted_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_restricted_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_restricted_i18n_Translation-en%5fGB&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_restricted_source_Sources&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_universe_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_universe_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_universe_i18n_Translation-en%5fGB&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty_universe_source_Sources&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-updates_InRelease&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-updates_main_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-updates_main_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-updates_main_source_Sources&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-updates_multiverse_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-updates_multiverse_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-updates_multiverse_source_Sources&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-updates_restricted_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-updates_restricted_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-updates_restricted_source_Sources&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-updates_universe_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-updates_universe_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-updates_universe_source_Sources&#8217;
removed &#8216;/var/lib/apt/lists/lock&#8217;
rm: cannot remove &#8216;/var/lib/apt/lists/partial&#8217;: Is a directory
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_dismine_valentina_ubuntu_dists_trusty_InRelease&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_dismine_valentina_ubuntu_dists_trusty_main_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_dismine_valentina_ubuntu_dists_trusty_main_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_fossfreedom_byzanz_ubuntu_dists_trusty_main_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_fossfreedom_byzanz_ubuntu_dists_trusty_Release&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_fossfreedom_byzanz_ubuntu_dists_trusty_Release.gpg&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_freecad-maintainers_freecad-stable_ubuntu_dists_trusty_InRelease&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_freecad-maintainers_freecad-stable_ubuntu_dists_trusty_main_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_freecad-maintainers_freecad-stable_ubuntu_dists_trusty_main_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_jon-hedgerows_get-iplayer_ubuntu_dists_trusty_InRelease&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_jon-hedgerows_get-iplayer_ubuntu_dists_trusty_main_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_jon-hedgerows_get-iplayer_ubuntu_dists_trusty_main_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_kirillshkrogalev_ffmpeg-next_ubuntu_dists_trusty_main_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_kirillshkrogalev_ffmpeg-next_ubuntu_dists_trusty_main_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_kirillshkrogalev_ffmpeg-next_ubuntu_dists_trusty_Release&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_kirillshkrogalev_ffmpeg-next_ubuntu_dists_trusty_Release.gpg&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_mc3man_gstffmpeg-keep_ubuntu_dists_trusty_main_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_mc3man_gstffmpeg-keep_ubuntu_dists_trusty_main_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_mc3man_gstffmpeg-keep_ubuntu_dists_trusty_Release&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_mc3man_gstffmpeg-keep_ubuntu_dists_trusty_Release.gpg&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_midori_ppa_ubuntu_dists_trusty_main_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_midori_ppa_ubuntu_dists_trusty_main_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_midori_ppa_ubuntu_dists_trusty_Release&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_midori_ppa_ubuntu_dists_trusty_Release.gpg&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_mkusb_ppa_ubuntu_dists_trusty_InRelease&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_mkusb_ppa_ubuntu_dists_trusty_main_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_mkusb_ppa_ubuntu_dists_trusty_main_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_nilarimogard_webupd8_ubuntu_dists_trusty_InRelease&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_nilarimogard_webupd8_ubuntu_dists_trusty_main_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_nilarimogard_webupd8_ubuntu_dists_trusty_main_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_openjdk-r_ppa_ubuntu_dists_trusty_InRelease&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_openjdk-r_ppa_ubuntu_dists_trusty_main_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_openjdk-r_ppa_ubuntu_dists_trusty_main_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_pj-assis_ppa_ubuntu_dists_trusty_InRelease&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_pj-assis_ppa_ubuntu_dists_trusty_main_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_pj-assis_ppa_ubuntu_dists_trusty_main_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_sunab_kdenlive-release_ubuntu_dists_trusty_main_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_sunab_kdenlive-release_ubuntu_dists_trusty_main_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_sunab_kdenlive-release_ubuntu_dists_trusty_Release&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_sunab_kdenlive-release_ubuntu_dists_trusty_Release.gpg&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_thefanclub_grive-tools_ubuntu_dists_trusty_main_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_thefanclub_grive-tools_ubuntu_dists_trusty_main_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_thefanclub_grive-tools_ubuntu_dists_trusty_Release&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_thefanclub_grive-tools_ubuntu_dists_trusty_Release.gpg&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_unit193_xombrero_ubuntu_dists_trusty_main_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_unit193_xombrero_ubuntu_dists_trusty_main_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_unit193_xombrero_ubuntu_dists_trusty_Release&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_unit193_xombrero_ubuntu_dists_trusty_Release.gpg&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_yannubuntu_boot-repair_ubuntu_dists_trusty_InRelease&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_yannubuntu_boot-repair_ubuntu_dists_trusty_main_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_yannubuntu_boot-repair_ubuntu_dists_trusty_main_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_zarquon42_meshlab_ubuntu_dists_trusty_main_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_zarquon42_meshlab_ubuntu_dists_trusty_main_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/ppa.launchpad.net_zarquon42_meshlab_ubuntu_dists_trusty_Release&#8217;
removed &#8216;/var/lib/apt/lists/repository.spotify.com_dists_stable_InRelease&#8217;
removed &#8216;/var/lib/apt/lists/repository.spotify.com_dists_stable_non-free_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/repo.steampowered.com_steam_dists_precise_InRelease&#8217;
removed &#8216;/var/lib/apt/lists/repo.steampowered.com_steam_dists_precise_steam_binary-amd64_Packages&#8217;
removed &#8216;/var/lib/apt/lists/repo.steampowered.com_steam_dists_precise_steam_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/repo.steampowered.com_steam_dists_precise_steam_source_Sources&#8217;
removed &#8216;/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_InRelease&#8217;
removed &#8216;/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_main_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_main_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_main_source_Sources&#8217;
removed &#8216;/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_multiverse_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_multiverse_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_multiverse_source_Sources&#8217;
removed &#8216;/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_restricted_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_restricted_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_restricted_source_Sources&#8217;
removed &#8216;/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_universe_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_universe_i18n_Translation-en&#8217;
removed &#8216;/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_universe_source_Sources&#8217;
removed &#8216;/var/lib/apt/lists/www.netfabb.com_debian_dists_stable_InRelease&#8217;
removed &#8216;/var/lib/apt/lists/www.netfabb.com_debian_dists_stable_non-free_binary-i386_Packages&#8217;
removed &#8216;/var/lib/apt/lists/www.netfabb.com_debian_dists_stable_non-free_i18n_Translation-en%5fGB&#8217;
sallen@steve2:~$ sudo apt-get update
Ign http://archive.canonical.com trusty InRelease
Ign http://gb.archive.ubuntu.com trusty InRelease                              
Ign http://extras.ubuntu.com trusty InRelease                                  
Get:1 http://repo.steampowered.com precise InRelease [2,842 B]                 
Get:2 http://gb.archive.ubuntu.com trusty-updates InRelease [65.9 kB]          
Get:3 http://archive.canonical.com trusty Release.gpg [933 B]                  
Get:4 http://extras.ubuntu.com trusty Release.gpg [72 B]                       
Get:5 http://ppa.launchpad.net trusty InRelease [15.5 kB]                      
Get:6 http://deb.opera.com stable InRelease [2,592 B]                          
Get:7 http://repository.spotify.com stable InRelease [3,302 B]                 
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:8 http://archive.canonical.com trusty Release [9,359 B]                    
Get:9 http://extras.ubuntu.com trusty Release [11.9 kB]                        
Get:10 http://www.netfabb.com stable InRelease [1,942 B]                       
Get:11 http://ppa.launchpad.net trusty InRelease [15.5 kB]                     
Get:12 http://gb.archive.ubuntu.com trusty-backports InRelease [65.9 kB]       
Get:13 http://security.ubuntu.com trusty-security InRelease [65.9 kB]          
Get:14 http://ppa.launchpad.net trusty InRelease [15.5 kB]                     
Get:15 http://gb.archive.ubuntu.com trusty-proposed InRelease [65.9 kB]        
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:16 http://deb.opera.com stable/non-free i386 Packages [1,820 B]            
Get:17 http://gb.archive.ubuntu.com trusty Release.gpg [933 B]                 
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:18 http://ppa.launchpad.net trusty InRelease [16.0 kB]                     
Get:19 http://gb.archive.ubuntu.com trusty Release [58.5 kB]                   
Get:20 http://ppa.launchpad.net trusty InRelease [15.4 kB]                     
Get:21 http://repository.spotify.com stable/non-free i386 Packages [1,136 B]   
Get:22 http://repo.steampowered.com precise/steam Sources [550 B]              
Get:23 http://repo.steampowered.com precise/steam amd64 Packages [601 B]       
Get:24 http://gb.archive.ubuntu.com trusty-updates/main Sources [401 kB]       
Get:25 http://archive.canonical.com trusty/partner Sources [9,713 B]           
Get:26 http://www.netfabb.com stable/non-free i386 Packages [596 B]            
Get:27 http://ppa.launchpad.net trusty InRelease [15.5 kB]                     
Get:28 http://extras.ubuntu.com trusty/main Sources [14 B]                     
Get:29 http://repo.steampowered.com precise/steam i386 Packages [799 B]        
Get:30 http://archive.canonical.com trusty/partner i386 Packages [5,770 B]     
Get:31 http://extras.ubuntu.com trusty/main i386 Packages [14 B]               
Get:32 http://archive.canonical.com trusty/partner Translation-en [4,207 B]    
Get:33 http://ppa.launchpad.net trusty InRelease [15.4 kB]                     
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:34 http://gb.archive.ubuntu.com trusty-updates/restricted Sources [6,331 B]
Get:35 http://ppa.launchpad.net trusty InRelease [15.5 kB]                     
Get:36 http://gb.archive.ubuntu.com trusty-updates/universe Sources [186 kB]   
Get:37 http://ppa.launchpad.net trusty InRelease [15.4 kB]                     
Ign http://repository.spotify.com stable/non-free Translation-en_GB            
Get:38 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Ign http://repository.spotify.com stable/non-free Translation-en               
Ign http://extras.ubuntu.com trusty/main Translation-en_GB                     
Get:39 http://gb.archive.ubuntu.com trusty-updates/multiverse Sources [7,769 B]
Ign http://deb.opera.com stable/non-free Translation-en_GB                     
Get:40 http://ppa.launchpad.net trusty/main i386 Packages [560 B]              
Get:41 http://gb.archive.ubuntu.com trusty-updates/main i386 Packages [951 kB] 
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Ign http://deb.opera.com stable/non-free Translation-en                        
Get:42 http://ppa.launchpad.net trusty/main Translation-en [341 B]             
Get:43 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Get:44 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Get:45 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Get:46 http://ppa.launchpad.net trusty/main i386 Packages [4,799 B]            
Get:47 http://ppa.launchpad.net trusty/main Translation-en [3,244 B]           
Get:48 http://ppa.launchpad.net trusty/main i386 Packages [7,012 B]            
Get:49 http://security.ubuntu.com trusty-security/main Sources [138 kB]        
Get:50 http://ppa.launchpad.net trusty/main Translation-en [5,526 B]           
Get:51 http://ppa.launchpad.net trusty/main i386 Packages [1,463 B]            
Get:52 http://ppa.launchpad.net trusty/main Translation-en [1,309 B]           
Get:53 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Get:54 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Get:55 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Get:56 http://security.ubuntu.com trusty-security/restricted Sources [4,955 B] 
Get:57 http://ppa.launchpad.net trusty Release [14.0 kB]                       
Get:58 http://ppa.launchpad.net trusty Release [15.1 kB]                       
Get:59 http://security.ubuntu.com trusty-security/universe Sources [60.3 kB]   
Get:60 http://ppa.launchpad.net trusty Release [15.1 kB]                       
Get:61 http://ppa.launchpad.net trusty Release [15.1 kB]                       
Get:62 http://ppa.launchpad.net trusty/main i386 Packages [39.9 kB]            
Get:63 http://gb.archive.ubuntu.com trusty-updates/restricted i386 Packages [16.9 kB]
Get:64 http://security.ubuntu.com trusty-security/multiverse Sources [3,189 B] 
Get:65 http://gb.archive.ubuntu.com trusty-updates/universe i386 Packages [420 kB]
Get:66 http://ppa.launchpad.net trusty/main Translation-en [29.3 kB]           
Get:67 http://security.ubuntu.com trusty-security/main i386 Packages [597 kB]  
Get:68 http://ppa.launchpad.net trusty/main i386 Packages [4,460 B]            
Get:69 http://ppa.launchpad.net trusty/main Translation-en [2,502 B]           
Get:70 http://ppa.launchpad.net trusty Release [14.5 kB]                       
Get:71 http://ppa.launchpad.net trusty/main i386 Packages [2,988 B]            
Get:72 http://ppa.launchpad.net trusty/main Translation-en [1,343 B]           
Get:73 http://ppa.launchpad.net trusty Release [15.1 kB]                       
Get:74 http://ppa.launchpad.net trusty/main i386 Packages [1,954 B]            
Get:75 http://ppa.launchpad.net trusty/main Translation-en [2,123 B]           
Get:76 http://gb.archive.ubuntu.com trusty-updates/multiverse i386 Packages [14.7 kB]
Get:77 http://gb.archive.ubuntu.com trusty-updates/main Translation-en [492 kB]
Get:78 http://ppa.launchpad.net trusty Release [15.1 kB]                       
Get:79 http://ppa.launchpad.net trusty/main i386 Packages [594 B]              
Get:80 http://ppa.launchpad.net trusty/main Translation-en [429 B]             
Get:81 http://ppa.launchpad.net trusty/main i386 Packages [669 B]              
Get:82 http://security.ubuntu.com trusty-security/restricted i386 Packages [13.7 kB]
Get:83 http://ppa.launchpad.net trusty/main i386 Packages [5,597 B]            
Get:84 http://security.ubuntu.com trusty-security/universe i386 Packages [179 kB]
Get:85 http://ppa.launchpad.net trusty/main Translation-en [3,926 B]           
Get:86 http://gb.archive.ubuntu.com trusty-updates/multiverse Translation-en [7,430 B]
Get:87 http://gb.archive.ubuntu.com trusty-updates/restricted Translation-en [3,978 B]
Get:88 http://ppa.launchpad.net trusty/main i386 Packages [3,707 B]            
Get:89 http://gb.archive.ubuntu.com trusty-updates/universe Translation-en [224 kB]
Get:90 http://ppa.launchpad.net trusty/main Translation-en [653 B]             
Get:91 http://ppa.launchpad.net trusty/main i386 Packages [872 B]              
Get:92 http://ppa.launchpad.net trusty/main Translation-en [543 B]             
Get:93 http://gb.archive.ubuntu.com trusty-backports/main Sources [9,712 B]    
Get:94 http://security.ubuntu.com trusty-security/multiverse i386 Packages [4,288 B]
Get:95 http://gb.archive.ubuntu.com trusty-backports/restricted Sources [28 B] 
Get:96 http://gb.archive.ubuntu.com trusty-backports/universe Sources [35.3 kB]
Get:97 http://ppa.launchpad.net trusty/main i386 Packages [4,637 B]            
Get:98 http://security.ubuntu.com trusty-security/main Translation-en [346 kB] 
Get:99 http://gb.archive.ubuntu.com trusty-backports/multiverse Sources [1,898 B]
Get:100 http://ppa.launchpad.net trusty/main Translation-en [2,473 B]          
Get:101 http://gb.archive.ubuntu.com trusty-backports/main i386 Packages [13.3 kB]
Get:102 http://ppa.launchpad.net trusty/main i386 Packages [624 B]             
Get:103 http://ppa.launchpad.net trusty/main Translation-en [177 B]            
Get:104 http://gb.archive.ubuntu.com trusty-backports/restricted i386 Packages [28 B]
Get:105 http://ppa.launchpad.net trusty/main i386 Packages [818 B]             
Get:106 http://gb.archive.ubuntu.com trusty-backports/universe i386 Packages [43.2 kB]
Get:107 http://ppa.launchpad.net trusty/main Translation-en [1,196 B]          
Get:108 http://gb.archive.ubuntu.com trusty-backports/multiverse i386 Packages [1,552 B]
Get:109 http://gb.archive.ubuntu.com trusty-backports/main Translation-en [7,503 B]
Get:110 http://gb.archive.ubuntu.com trusty-backports/multiverse Translation-en [1,215 B]
Get:111 http://gb.archive.ubuntu.com trusty-backports/restricted Translation-en [28 B]
Get:112 http://gb.archive.ubuntu.com trusty-backports/universe Translation-en [36.8 kB]
Get:113 http://security.ubuntu.com trusty-security/multiverse Translation-en [2,201 B]
Get:114 http://gb.archive.ubuntu.com trusty-proposed/restricted i386 Packages [772 B]
Get:115 http://gb.archive.ubuntu.com trusty-proposed/multiverse i386 Packages [28 B]
Get:116 http://gb.archive.ubuntu.com trusty-proposed/main i386 Packages [87.5 kB]
Get:117 http://security.ubuntu.com trusty-security/restricted Translation-en [3,491 B]
Ign http://ppa.launchpad.net trusty/main Translation-en_GB                     
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Get:118 http://gb.archive.ubuntu.com trusty-proposed/universe i386 Packages [13.1 kB]
Get:119 http://gb.archive.ubuntu.com trusty-proposed/main Translation-en [29.4 kB]
Get:120 http://security.ubuntu.com trusty-security/universe Translation-en [102 kB]
Get:121 http://gb.archive.ubuntu.com trusty-proposed/multiverse Translation-en [28 B]
Get:122 http://gb.archive.ubuntu.com trusty-proposed/restricted Translation-en [281 B]
Get:123 http://gb.archive.ubuntu.com trusty-proposed/universe Translation-en [10.5 kB]
Get:124 http://gb.archive.ubuntu.com trusty/main Sources [1,064 kB]            
Ign http://repo.steampowered.com precise/steam Translation-en_GB               
Get:125 http://gb.archive.ubuntu.com trusty/restricted Sources [5,433 B]       
Get:126 http://gb.archive.ubuntu.com trusty/universe Sources [6,399 kB]        
Ign http://repo.steampowered.com precise/steam Translation-en                  
Get:127 http://gb.archive.ubuntu.com trusty/multiverse Sources [174 kB]        
Get:128 http://gb.archive.ubuntu.com trusty/main i386 Packages [1,348 kB]      
Get:129 http://gb.archive.ubuntu.com trusty/restricted i386 Packages [13.4 kB] 
Get:130 http://gb.archive.ubuntu.com trusty/universe i386 Packages [5,866 kB]  
Get:131 http://gb.archive.ubuntu.com trusty/multiverse i386 Packages [134 kB]  
Get:132 http://gb.archive.ubuntu.com trusty/main Translation-en_GB [96.8 kB]   
Get:133 http://gb.archive.ubuntu.com trusty/main Translation-en [762 kB]       
Get:134 http://gb.archive.ubuntu.com trusty/multiverse Translation-en_GB [98.3 kB]
Get:135 http://gb.archive.ubuntu.com trusty/multiverse Translation-en [102 kB] 
Get:136 http://gb.archive.ubuntu.com trusty/restricted Translation-en_GB [3,483 B]
Get:137 http://gb.archive.ubuntu.com trusty/restricted Translation-en [3,457 B]
Get:138 http://gb.archive.ubuntu.com trusty/universe Translation-en_GB [7,557 B]
Get:139 http://gb.archive.ubuntu.com trusty/universe Translation-en [4,089 kB] 
Fetched 25.6 MB in 1min 1s (415 kB/s)                                          
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/www.netfabb.com_debian_dists_stable_non-free_i18n_Translation-en%5fGB
E: The package lists or status file could not be parsed or opened.

$ 

```

---

### Post by #&amp;thj^% on 2017-08-03
You can do that all day and night>>until we figure out how to uninstall it.
```
apt search netfabb
```
BTW have tried consulting Netfab yet for help?

---

### Post by steve234 on 2017-08-03
I should email them I suppose. Did I not uninstall is when I got this to work:

```
$ sudo apt-get purge netfabb-basic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  netfabb-basic*
0 to upgrade, 0 to newly install, 1 to remove and 0 not to upgrade.
After this operation, 15.7 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 663495 files and directories currently installed.)
Removing netfabb-basic (5.2.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...

```

apt-get search netfabb is an invalid operation

---

### Post by steve234 on 2017-08-03
Sent a message to Autodesk customer care - I imagine they will view this as a system error.

What exactly is a Mergelist - can I not delete it / somehow hide it from apt, Synaptic and Software centre (the same error seems to be taking all of them out)

---

### Post by deadflowr on 2017-08-03
> apt-get search netfabb is an invalid operation
try
```
apt search netfabb
```
or
```
apt-cache search netfabb
```
also
```
dpkg -l | grep netfabb
```

---

### Post by #&amp;thj^% on 2017-08-03
EDIT Did not see deadflowr's post before I posted this one.:) 
Well try this one more time:
```
sudo rm -rf /var/lib/apt/lists
sudo mkdir /var/lib/apt/lists
sudo mkdir /var/lib/apt/lists/partial
```
And see if this helps:
```
sudo apt-get clean && sudo apt-get update
```

> **steve234 said:**
> Sent a message to Autodesk customer care - I imagine they will view this as a system error.

What exactly is a Mergelist - can I not delete it / somehow hide it from apt, Synaptic and Software centre (the same error seems to be taking all of them out)

One of the most common error a user encounters while updating is Problem with MergeList. The error could be encountered while using both Ubuntu Update Manager, Synaptic and using the sudo apt-get update in terminal. Think of it as an indexing mechanism.

---

### Post by steve234 on 2017-08-03
Thanks guys appreciate the help - in turn:

@deadflowr = I got a segmentation fault, the same issue, and then no return.

```

$ apt search netfabb
Segmentation fault (core dumped)

$ apt-cache search netfabb
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/www.netfabb.com_debian_dists_stable_non-free_i18n_Translation-en%5fGB
E: The package lists or status file could not be parsed or opened.

$ dpkg -l | grep netfabb
$ 
 

```


@1fallen

```

$ sudo rm -rf /var/lib/apt/lists
$ sudo mkdir /var/lib/apt/lists
$ sudo mkdir /var/lib/apt/lists/partial

$ sudo apt-get clean && sudo apt-get update
Ign http://gb.archive.ubuntu.com trusty InRelease
Ign http://archive.canonical.com trusty InRelease                              
Get:1 http://gb.archive.ubuntu.com trusty-updates InRelease [65.9 kB]          
Get:2 http://repo.steampowered.com precise InRelease [2,842 B]                 
Ign http://extras.ubuntu.com trusty InRelease                                  
Get:3 http://archive.canonical.com trusty Release.gpg [933 B]                  
Get:4 http://repository.spotify.com stable InRelease [3,302 B]                 
Get:5 http://deb.opera.com stable InRelease [2,592 B]                          
Get:6 http://ppa.launchpad.net trusty InRelease [15.5 kB]                      
Get:7 http://archive.canonical.com trusty Release [9,359 B]                    
Get:8 http://extras.ubuntu.com trusty Release.gpg [72 B]                       
Get:9 http://www.netfabb.com stable InRelease [1,942 B]                        
Get:10 http://repo.steampowered.com precise/steam Sources [550 B]              
Get:11 http://gb.archive.ubuntu.com trusty-backports InRelease [65.9 kB]       
Get:12 http://extras.ubuntu.com trusty Release [11.9 kB]                       
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:13 http://security.ubuntu.com trusty-security InRelease [65.9 kB]          
Get:14 http://ppa.launchpad.net trusty InRelease [15.5 kB]                     
Get:15 http://repo.steampowered.com precise/steam amd64 Packages [601 B]       
Get:16 http://repository.spotify.com stable/non-free i386 Packages [1,136 B]   
Get:17 http://repo.steampowered.com precise/steam i386 Packages [799 B]        
Get:18 http://gb.archive.ubuntu.com trusty-proposed InRelease [65.9 kB]        
Get:19 http://deb.opera.com stable/non-free i386 Packages [1,820 B]            
Get:20 http://ppa.launchpad.net trusty InRelease [15.5 kB]                     
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:21 http://archive.canonical.com trusty/partner Sources [9,713 B]           
Get:22 http://gb.archive.ubuntu.com trusty Release.gpg [933 B]                 
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:23 http://archive.canonical.com trusty/partner i386 Packages [5,770 B]     
Get:24 http://gb.archive.ubuntu.com trusty Release [58.5 kB]                   
Get:25 http://ppa.launchpad.net trusty InRelease [16.0 kB]                     
Get:26 http://www.netfabb.com stable/non-free i386 Packages [596 B]            
Get:27 http://archive.canonical.com trusty/partner Translation-en [4,207 B]    
Get:28 http://ppa.launchpad.net trusty InRelease [15.4 kB]                     
Get:29 http://ppa.launchpad.net trusty InRelease [15.5 kB]                     
Get:30 http://ppa.launchpad.net trusty InRelease [15.4 kB]                     
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:31 http://gb.archive.ubuntu.com trusty-updates/main Sources [401 kB]       
Ign http://repository.spotify.com stable/non-free Translation-en_GB            
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:32 http://extras.ubuntu.com trusty/main Sources [14 B]                     
Get:33 http://ppa.launchpad.net trusty InRelease [15.5 kB]                     
Ign http://repository.spotify.com stable/non-free Translation-en               
Get:34 http://extras.ubuntu.com trusty/main i386 Packages [14 B]               
Ign http://deb.opera.com stable/non-free Translation-en_GB                     
Ign http://deb.opera.com stable/non-free Translation-en                        
Get:35 http://ppa.launchpad.net trusty InRelease [15.4 kB]                     
Get:36 http://gb.archive.ubuntu.com trusty-updates/restricted Sources [6,331 B]
Get:37 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Get:38 http://gb.archive.ubuntu.com trusty-updates/universe Sources [186 kB]   
Get:39 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Get:40 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Get:41 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Get:42 http://ppa.launchpad.net trusty/main i386 Packages [560 B]              
Get:43 http://gb.archive.ubuntu.com trusty-updates/multiverse Sources [7,769 B]
Ign http://extras.ubuntu.com trusty/main Translation-en_GB                     
Get:44 http://gb.archive.ubuntu.com trusty-updates/main i386 Packages [951 kB] 
Get:45 http://security.ubuntu.com trusty-security/main Sources [138 kB]        
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Get:46 http://ppa.launchpad.net trusty/main Translation-en [341 B]             
Get:47 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Get:48 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Get:49 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Get:50 http://ppa.launchpad.net trusty/main i386 Packages [4,799 B]            
Get:51 http://ppa.launchpad.net trusty/main Translation-en [3,244 B]           
Get:52 http://ppa.launchpad.net trusty/main i386 Packages [7,012 B]            
Get:53 http://security.ubuntu.com trusty-security/restricted Sources [4,955 B] 
Get:54 http://ppa.launchpad.net trusty/main Translation-en [5,526 B]           
Get:55 http://ppa.launchpad.net trusty Release [14.0 kB]                       
Get:56 http://security.ubuntu.com trusty-security/universe Sources [60.3 kB]   
Get:57 http://ppa.launchpad.net trusty Release [15.1 kB]                       
Get:58 http://ppa.launchpad.net trusty Release [15.1 kB]                       
Get:59 http://security.ubuntu.com trusty-security/multiverse Sources [3,189 B] 
Get:60 http://ppa.launchpad.net trusty Release [15.1 kB]                       
Get:61 http://gb.archive.ubuntu.com trusty-updates/restricted i386 Packages [16.9 kB]
Get:62 http://security.ubuntu.com trusty-security/main i386 Packages [597 kB]  
Get:63 http://ppa.launchpad.net trusty/main i386 Packages [1,463 B]            
Get:64 http://gb.archive.ubuntu.com trusty-updates/universe i386 Packages [420 kB]
Get:65 http://ppa.launchpad.net trusty/main Translation-en [1,309 B]           
Get:66 http://ppa.launchpad.net trusty Release [14.5 kB]                       
Get:67 http://ppa.launchpad.net trusty Release [15.1 kB]                       
Get:68 http://ppa.launchpad.net trusty/main i386 Packages [39.9 kB]            
Get:69 http://ppa.launchpad.net trusty/main Translation-en [29.3 kB]           
Get:70 http://ppa.launchpad.net trusty Release [15.1 kB]                       
Get:71 http://ppa.launchpad.net trusty/main i386 Packages [4,460 B]            
Get:72 http://ppa.launchpad.net trusty/main Translation-en [2,502 B]           
Get:73 http://ppa.launchpad.net trusty/main i386 Packages [2,988 B]            
Get:74 http://gb.archive.ubuntu.com trusty-updates/multiverse i386 Packages [14.7 kB]
Get:75 http://ppa.launchpad.net trusty/main Translation-en [1,343 B]           
Get:76 http://gb.archive.ubuntu.com trusty-updates/main Translation-en [492 kB]
Get:77 http://ppa.launchpad.net trusty/main i386 Packages [1,954 B]            
Get:78 http://security.ubuntu.com trusty-security/restricted i386 Packages [13.7 kB]
Get:79 http://ppa.launchpad.net trusty/main Translation-en [2,123 B]           
Get:80 http://security.ubuntu.com trusty-security/universe i386 Packages [179 kB]
Get:81 http://ppa.launchpad.net trusty/main i386 Packages [594 B]              
Get:82 http://ppa.launchpad.net trusty/main Translation-en [429 B]             
Get:83 http://ppa.launchpad.net trusty/main i386 Packages [669 B]              
Get:84 http://gb.archive.ubuntu.com trusty-updates/multiverse Translation-en [7,430 B]
Get:85 http://ppa.launchpad.net trusty/main i386 Packages [5,597 B]            
Get:86 http://gb.archive.ubuntu.com trusty-updates/restricted Translation-en [3,978 B]
Get:87 http://security.ubuntu.com trusty-security/multiverse i386 Packages [4,288 B]
Get:88 http://gb.archive.ubuntu.com trusty-updates/universe Translation-en [224 kB]
Get:89 http://ppa.launchpad.net trusty/main Translation-en [3,926 B]           
Get:90 http://security.ubuntu.com trusty-security/main Translation-en [346 kB] 
Get:91 http://gb.archive.ubuntu.com trusty-backports/main Sources [9,712 B]    
Get:92 http://ppa.launchpad.net trusty/main i386 Packages [3,707 B]            
Get:93 http://gb.archive.ubuntu.com trusty-backports/restricted Sources [28 B] 
Get:94 http://gb.archive.ubuntu.com trusty-backports/universe Sources [35.3 kB]
Get:95 http://ppa.launchpad.net trusty/main Translation-en [653 B]             
Get:96 http://security.ubuntu.com trusty-security/multiverse Translation-en [2,201 B]
Get:97 http://ppa.launchpad.net trusty/main i386 Packages [872 B]              
Get:98 http://gb.archive.ubuntu.com trusty-backports/multiverse Sources [1,898 B]
Get:99 http://gb.archive.ubuntu.com trusty-backports/main i386 Packages [13.3 kB]
Get:100 http://ppa.launchpad.net trusty/main Translation-en [543 B]            
Get:101 http://security.ubuntu.com trusty-security/restricted Translation-en [3,491 B]
Get:102 http://ppa.launchpad.net trusty/main i386 Packages [4,637 B]           
Get:103 http://gb.archive.ubuntu.com trusty-backports/restricted i386 Packages [28 B]
Get:104 http://ppa.launchpad.net trusty/main Translation-en [2,473 B]          
Get:105 http://gb.archive.ubuntu.com trusty-backports/universe i386 Packages [43.2 kB]
Get:106 http://security.ubuntu.com trusty-security/universe Translation-en [102 kB]
Get:107 http://ppa.launchpad.net trusty/main i386 Packages [624 B]             
Get:108 http://ppa.launchpad.net trusty/main Translation-en [177 B]            
Get:109 http://gb.archive.ubuntu.com trusty-backports/multiverse i386 Packages [1,552 B]
Get:110 http://gb.archive.ubuntu.com trusty-backports/main Translation-en [7,503 B]
Get:111 http://ppa.launchpad.net trusty/main i386 Packages [818 B]             
Get:112 http://gb.archive.ubuntu.com trusty-backports/multiverse Translation-en [1,215 B]
Get:113 http://ppa.launchpad.net trusty/main Translation-en [1,196 B]          
Get:114 http://gb.archive.ubuntu.com trusty-backports/restricted Translation-en [28 B]
Get:115 http://gb.archive.ubuntu.com trusty-backports/universe Translation-en [36.8 kB]
Get:116 http://gb.archive.ubuntu.com trusty-proposed/restricted i386 Packages [772 B]
Get:117 http://gb.archive.ubuntu.com trusty-proposed/multiverse i386 Packages [28 B]
Get:118 http://gb.archive.ubuntu.com trusty-proposed/main i386 Packages [87.5 kB]
Get:119 http://gb.archive.ubuntu.com trusty-proposed/universe i386 Packages [13.1 kB]
Ign http://ppa.launchpad.net trusty/main Translation-en_GB                     
Get:120 http://gb.archive.ubuntu.com trusty-proposed/main Translation-en [29.4 kB]
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Get:121 http://gb.archive.ubuntu.com trusty-proposed/multiverse Translation-en [28 B]
Get:122 http://gb.archive.ubuntu.com trusty-proposed/restricted Translation-en [281 B]
Get:123 http://gb.archive.ubuntu.com trusty-proposed/universe Translation-en [10.5 kB]
Get:124 http://gb.archive.ubuntu.com trusty/main Sources [1,064 kB]            
Get:125 http://gb.archive.ubuntu.com trusty/restricted Sources [5,433 B]       
Get:126 http://gb.archive.ubuntu.com trusty/universe Sources [6,399 kB]        
Ign http://repo.steampowered.com precise/steam Translation-en_GB               
Ign http://repo.steampowered.com precise/steam Translation-en                  
Get:127 http://gb.archive.ubuntu.com trusty/multiverse Sources [174 kB]        
Get:128 http://gb.archive.ubuntu.com trusty/main i386 Packages [1,348 kB]      
Get:129 http://gb.archive.ubuntu.com trusty/restricted i386 Packages [13.4 kB] 
Get:130 http://gb.archive.ubuntu.com trusty/universe i386 Packages [5,866 kB]  
Get:131 http://gb.archive.ubuntu.com trusty/multiverse i386 Packages [134 kB]  
Get:132 http://gb.archive.ubuntu.com trusty/main Translation-en_GB [96.8 kB]   
Get:133 http://gb.archive.ubuntu.com trusty/main Translation-en [762 kB]       
Get:134 http://gb.archive.ubuntu.com trusty/multiverse Translation-en_GB [98.3 kB]
Get:135 http://gb.archive.ubuntu.com trusty/multiverse Translation-en [102 kB] 
Get:136 http://gb.archive.ubuntu.com trusty/restricted Translation-en_GB [3,483 B]
Get:137 http://gb.archive.ubuntu.com trusty/restricted Translation-en [3,457 B]
Get:138 http://gb.archive.ubuntu.com trusty/universe Translation-en_GB [7,557 B]
Get:139 http://gb.archive.ubuntu.com trusty/universe Translation-en [4,089 kB] 
Fetched 25.6 MB in 54s (471 kB/s)                                              
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/www.netfabb.com_debian_dists_stable_non-free_i18n_Translation-en%5fGB
E: The package lists or status file could not be parsed or opened.

```

Sleep time again here I'm afraid... will carry on tomorow

Thanks again

---

### Post by #&amp;thj^% on 2017-08-03
Ok I finally had the idea to boot to another OS with the same drive(Ubuntu/Lubuntu) hooked up.
You should also be able to do this with a live install cd/dvd/usb installer.
Mounted the partition navigated to "/var/lib/apt/lists/" with the file manager "As Root".
For me I used **"sudo -H thunar" **to get the root access.
Then i was able to delete the partial /Folder in there. You should be able to delete this file Also.
**"www.netfabb.com_debian_dists_stable_non-free_i18n_Translation-en%5fGB"** 
Next I rebooted to Ubuntu ran the updates and upgrades with no errors.
Something worth trying. **_And of course the standard warn of having a good back up in place._**
Also just a note of caution here you are living on the cutting edge here with these Repos enabled.
trusty-proposed/main
trusty-backports/multiverse
And Mixed with several PPA's (Just saying :)) Usually pretty advanced experience required here.;)

---

### Post by vasa1 on 2017-08-03
> **steve234 said:**
> Also... I am ona supported version:

```
~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:    14.04
Codename:    trusty

```

This is listed in @vasa's link as supported - unless it's suddenly past 2019.

Ubuntu 14.04.5 LTS - supported until April 2019That's pretty funny. Are you on Ubuntu or Lubuntu?

---

### Post by steve234 on 2017-08-04
@vasa1 - I'm on lubuntu

@deadflowr - I will dig out my live USB - is there a reason I'm living on the cutting edge - I don't remember needing to add backports or proposed to do anything.

I'm on an oooooold eeepc (eee1000h - 2gb Ram, 1.6 Atom processor, 32 bit, with SSD as an upgrade). It runs really well on lubuntu - used to be a hackingtosh until OSX 10.5 became unsupported and everything useful (dropbox Gdrive, browsers) got dropped. There are quite a few eee specific tweaks.

I'ts a kinda - sling it in my bag and use on my commute - type of machine. For arduino coding, basic 3D design and print slicing.

---

### Post by steve234 on 2017-08-09
Some progress....

I can delete the offending files in var/lib/apt/lists manually and use apt as normal - until I run apt-update. 

Something then re-populates the following files into apt/lists:

```
www.netfabb.com_debian_dists_stable_InRelease
www.netfabb.com_debian_dists_stable_non-free_binary-i386_Packages
www.netfabb.com_debian_dists_stable_non-free_i18n_Translation-en%5fGB


```

This causes apt to break and I need to manually remove those files from var/lib/apt/lists to make it work again.

I wonder how this is happening?

---

### Post by steve234 on 2017-08-09
Fixed!!!

Needed to comment out the netfabb line in  /etc/*apt*/*sources*.list (same as we did for list /etc/*apt*/*sources*.list.d).

Massive bodge, or genuine fix? Shall I mark as solved?

Now back to the daunting task of writing a JS compatible scraper that can alert me when my local skatepark release their free tickets for skateboard lessons!

---

