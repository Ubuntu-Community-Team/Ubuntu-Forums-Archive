---
title: "Synaptic package manager out of date"
date: 2012-05-16
forum: Installation &amp; Upgrades
---

### Post by wonderingwhy on 2012-05-16
I'm trying to upgrade to the latest firefox version - which I believe is 12?  Firefox keeps telling me the version I have is out of date and insecure - I"m on version 3.6.22.  But when I go to Synaptic package manager it tells me I have the latest version.  (Which co-incidentally it also does for Kaffeine - which I don't!) 

I'm on Ubuntu 10.4. - I don't know anything much about computers and so have to wait for some help to install 12.4.  

Should I just sit it out until the ubuntu upgrade and will that sort the prob with synaptic package manager or is there something else amiss?

Thanks

---

### Post by mörgæs on 2012-05-16
[http://ubuntuforums.org/showthread.php?t=1712247](http://ubuntuforums.org/showthread.php?t=1712247)

---

### Post by plucky on 2012-05-16
I am on 10.04.4 and Firefox is version 12.

I am wondering whether the OP hasn't been installing updates regularly.

Open a terminal and post output for ```
uname -a
lsb_release -a
sudo apt-get update && sudo apt-get upgrade
```


Good Luck

---

### Post by wonderingwhy on 2012-05-16
Hey 

mörgæs that link was really helpful - thanks.  
Plucky thanks too, really appreciate the code.

All sorted and upgraded to firefox 13 actually.

I think hope that once I get Ubuntu 12.4 the repo will be up to date again.

---

### Post by mörgæs on 2012-05-16
Good, then please mark the thread 'solved'.

---

### Post by Cavsfan on 2012-05-16
> **wonderingwhy said:**
> Hey 

mörgæs that link was really helpful - thanks.  
Plucky thanks too, really appreciate the code.

All sorted and upgraded to firefox 13 actually.

I think hope that once I get Ubuntu 12.4 the repo will be up to date again.

I suggest you use plucky's way of updating instead of Update Manager.
A friend **ranch hand** in this forum calls it Update Mangler.

```
sudo apt-get update 
sudo apt-get upgrade
```

Then if there is a kernel or something held back you would use

```
sudo apt-get dist-upgrade
```

Just my opinion but, I am on 10.04 too and I am going to wait until July to get 12.04.1 when it comes out.
I see a lot of issues and by the time 12.04.1 comes out, it will be very stable like 10.04 is now.

---

### Post by wonderingwhy on 2012-05-16
Hey Cavsfan

Thanks for that: I was just reading around for 'how to' with upgrading to 12.04 and saw that Ubuntu actually recommend waiting until July [https://help.ubuntu.com/community/PreciseUpgrades](https://help.ubuntu.com/community/PreciseUpgrades) 

- so that's absolutely what I'll do.

---

### Post by wonderingwhy on 2012-05-16
I've marked this Thread as solved - the upgrade to firefox is solved - but why synaptic package manager is out of date - that remains a mystery to me!

---

### Post by Cavsfan on 2012-05-17
> **wonderingwhy said:**
> I've marked this Thread as solved - the upgrade to firefox is solved - but why synaptic package manager is out of date - that remains a mystery to me!

What does the output of these commands entered into a terminal say?

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by wonderingwhy on 2012-05-20
Hey Cavsfan

Sorry for the delayed response.

So I did that and this is what I got:

> Need to get 157MB of archives.
After this operation, 36.9kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.


Which I assume means that the whole command was aborted?

I feel like my system is cursed?

---

### Post by Cavsfan on 2012-05-21
> **wonderingwhy said:**
> Hey Cavsfan

Sorry for the delayed response.

So I did that and this is what I got:

> Need to get 157MB of archives.
After this operation, 36.9kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.Which I assume means that the whole command was aborted?

I feel like my system is cursed?

That means it was updating several programs with 157MB.
Can you post the entire output of 

```
sudo apt-get update  
sudo apt-get upgrade
```

Highlight it all and click the # button at the top right to put CODE around the text.

---

### Post by wonderingwhy on 2012-06-25
Hey Cavsfan

I know it's been 4 weeks and so I totally understand if you don't have time to review this and give me your thoughts.  

```
phil@muir:~$ sudo apt-get update 
[sudo] password for phil: 
Ign cdrom://Mythbuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1)/ lucid/main Translation-en_NZ
Ign cdrom://Mythbuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1)/ lucid/multiverse Translation-en_NZ                                                                                                                                
Ign cdrom://Mythbuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1)/ lucid/restricted Translation-en_NZ                                                                                                                                
Ign cdrom://Mythbuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1)/ lucid/universe Translation-en_NZ                                                                                                                                  
Hit http://nz.archive.ubuntu.com hardy-backports Release.gpg                                                                                                                                                                                
Ign http://nz.archive.ubuntu.com/ubuntu/ hardy-backports/main Translation-en_NZ                                                                                                                                                             
Ign http://nz.archive.ubuntu.com/ubuntu/ hardy-backports/restricted Translation-en_NZ                                                                                                                                                       
Ign http://nz.archive.ubuntu.com/ubuntu/ hardy-backports/universe Translation-en_NZ                                                                                                                
Ign http://nz.archive.ubuntu.com/ubuntu/ hardy-backports/multiverse Translation-en_NZ                                                                                                                              
Hit http://nz.archive.ubuntu.com hardy-backports Release                                                                                                                                                           
Hit http://nz.archive.ubuntu.com hardy-backports/main Packages                                                                                                                                                     
Hit http://nz.archive.ubuntu.com hardy-backports/restricted Packages                                                                                                                  
Hit http://nz.archive.ubuntu.com hardy-backports/universe Packages                                                                                                            
Hit http://nz.archive.ubuntu.com hardy-backports/multiverse Packages                                                                                                          
Hit http://nz.archive.ubuntu.com hardy-backports/main Sources                                                                                                                 
Hit http://nz.archive.ubuntu.com hardy-backports/restricted Sources                                                                                                           
Hit http://nz.archive.ubuntu.com hardy-backports/universe Sources                                                                                                             
Hit http://nz.archive.ubuntu.com hardy-backports/multiverse Sources                                                                                                           
Get:1 http://dl.google.com stable Release.gpg [198B]                                                                                                                          
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_NZ                                                                                                                      
Hit http://archive.canonical.com lucid Release.gpg                                                                                                                                            
Get:2 http://archive.ubuntu.com lucid Release.gpg [189B]                                                                                                
Hit http://ppa.launchpad.net lucid Release.gpg                                                                                                                                                         
Get:3 http://dl.google.com stable Release [1,347B]                                                                                                                      
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_NZ                                                                                                                          
Hit http://deb.opera.com stable Release.gpg                                                                                            
Hit http://packages.medibuntu.org lucid Release.gpg                                                                                    
Get:4 http://dl.google.com stable/main Packages [1,243B]                                                                               
Hit http://archive.getdeb.net lucid-getdeb Release.gpg                                                                                                           
Hit http://archive.canonical.com lucid Release                                                                                                                                                    
Ign http://archive.ubuntu.com/ubuntu/ lucid/main Translation-en_NZ                                                                     
Hit http://archive.canonical.com lucid/partner Packages                                                          
Ign http://archive.getdeb.net/ubuntu/ lucid-getdeb/apps Translation-en_NZ                                        
Ign http://archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_NZ                                         
Ign http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/ lucid/main Translation-en_NZ              
Ign http://packages.medibuntu.org/ lucid/free Translation-en_NZ                                         
Ign http://deb.opera.com/opera/ stable/non-free Translation-en_NZ                                                        
Ign http://archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_NZ                                                   
Hit http://ppa.launchpad.net lucid Release.gpg                                                                                                                                                                                               
Ign http://archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_NZ                                                                                                                                                                     
Hit http://deb.opera.com stable Release                                                                                                                                                                                                      
Ign http://packages.medibuntu.org/ lucid/non-free Translation-en_NZ                                                                                                                                                                          
Get:5 http://archive.ubuntu.com lucid-updates Release.gpg [198B]                                                                                                                                                                             
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_NZ                                                                                                                                                                   
Hit http://archive.getdeb.net lucid-getdeb Release                                                                                                                                                                                           
Ign http://ppa.launchpad.net/mtron/kaffeine-stable/ubuntu/ lucid/main Translation-en_NZ                                                                                                                                                      
Ign http://deb.opera.com stable/non-free Packages                                                                                                                                                                                            
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_NZ                                                                                                                                                             
Hit http://packages.medibuntu.org lucid Release                                                                                                                                                                                              
Hit http://ppa.launchpad.net lucid Release.gpg                                                                                                                                                                                               
Ign http://deb.opera.com stable/non-free Packages                                                                                                                                                                                            
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_NZ                                                                                                                                                               
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_NZ                                                                                                                                                             
Get:6 http://deb.opera.com stable/non-free Packages [2,551B]                                                                                                                                                                                 
99% [6 Packages gzip 0B] [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting for headers]                                                                                                                             
gzip: stdin: not in gzip format                                                                                                                                                                                                              
Err http://deb.opera.com stable/non-free Packages                                                                                                                                                                                            
  Sub-process gzip returned an error code (1)                                                                                                                                                                                                
Hit http://archive.getdeb.net lucid-getdeb/apps Packages                                                                                                                                                                                     
Get:7 http://archive.ubuntu.com lucid-security Release.gpg [198B]                                                                                                                                                                            
Hit http://packages.medibuntu.org lucid/free Packages                                                                                                                                                                                        
Ign http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/ lucid/main Translation-en_NZ                                                                                                                                                       
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_NZ                                                                                                                                                                  
Hit http://ppa.launchpad.net lucid Release                                                                                                                                                                                                   
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_NZ                                                                                                                                                            
Hit http://packages.medibuntu.org lucid/non-free Packages                                        
Hit http://ppa.launchpad.net lucid Release     
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_NZ                                        
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_NZ                
Hit http://ppa.launchpad.net lucid Release     
Get:8 http://archive.ubuntu.com lucid Release [57.2kB]                                                                 
Hit http://packages.medibuntu.org lucid/free Sources                                             
Hit http://ppa.launchpad.net lucid/main Packages                            
Hit http://packages.medibuntu.org lucid/non-free Sources
Hit http://ppa.launchpad.net lucid/main Packages                       
Get:9 http://archive.ubuntu.com lucid-updates Release [57.3kB]                                                                                                                                                                              
Hit http://ppa.launchpad.net lucid/main Packages                                                                                                                                                                                            
Get:10 http://archive.ubuntu.com lucid-security Release [57.3kB]                                                                                                                                                                            
Get:11 http://archive.ubuntu.com lucid/main Packages [1,386kB]                                                                                                                                                                              
Get:12 http://archive.ubuntu.com lucid/restricted Packages [6,208B]                                                                                                                                                                         
Get:13 http://archive.ubuntu.com lucid/main Sources [659kB]                                                                                                                                                                                 
Get:14 http://archive.ubuntu.com lucid/restricted Sources [3,775B]                                                                                                                                                                          
Get:15 http://archive.ubuntu.com lucid/universe Packages [5,448kB]                                                                                                                                                                          
Get:16 http://archive.ubuntu.com lucid/universe Sources [3,165kB]                                                                                                                                                                           
Get:17 http://archive.ubuntu.com lucid/multiverse Packages [180kB]                                                                                                                                                                          
Get:18 http://archive.ubuntu.com lucid/multiverse Sources [119kB]                                                                                                                                                                           
Get:19 http://archive.ubuntu.com lucid-updates/main Packages [617kB]                                                                                                                                                                        
Get:20 http://archive.ubuntu.com lucid-updates/restricted Packages [4,617B]                                                                                                                                                                 
Get:21 http://archive.ubuntu.com lucid-updates/main Sources [222kB]                                                                                                                                                                         
Get:22 http://archive.ubuntu.com lucid-updates/restricted Sources [2,194B]                                                                                                                                                                  
Get:23 http://archive.ubuntu.com lucid-updates/universe Packages [270kB]                                                                                                                                                                    
Get:24 http://archive.ubuntu.com lucid-updates/universe Sources [101kB]                                                                                                                                                                     
Get:25 http://archive.ubuntu.com lucid-updates/multiverse Packages [11.5kB]                                                                                                                                                                 
Get:26 http://archive.ubuntu.com lucid-updates/multiverse Sources [5,818B]                                                                                                                                                                  
Get:27 http://archive.ubuntu.com lucid-security/main Packages [417kB]                                                                                                                                                                       
Get:28 http://archive.ubuntu.com lucid-security/restricted Packages [2,855B]                                                                                                                                                                
Get:29 http://archive.ubuntu.com lucid-security/main Sources [124kB]                                                                                                                                                                        
Get:30 http://archive.ubuntu.com lucid-security/restricted Sources [1,259B]                                                                                                                                                                 
Get:31 http://archive.ubuntu.com lucid-security/universe Packages [131kB]                                                                                                                                                                   
Get:32 http://archive.ubuntu.com lucid-security/universe Sources [40.8kB]                                                                                                                                                                   
Get:33 http://archive.ubuntu.com lucid-security/multiverse Packages [5,370B]                                                                                                                                                                
Get:34 http://archive.ubuntu.com lucid-security/multiverse Sources [2,316B]                                                                                                                                                                 
Fetched 13.1MB in 2min 49s (77.2kB/s)                                                                                                                                                                                                       
W: Failed to fetch http://deb.opera.com/opera/dists/stable/non-free/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)

E: Some index files failed to download, they have been ignored, or old ones used instead.
phil@muir:~$ 

```

I still can't update, and now I'm getting a little red triangle danger icon in my tool bar telling me it can't find the repos.  It doesn't seem to help which server I go for the main one or a New Zealand one. Thanks muchly

---

### Post by plucky on 2012-06-25
> W: Failed to fetch [http://deb.opera.com/opera/dists/stable/non-free/binary-i386/Packages.gz](http://deb.opera.com/opera/dists/stable/non-free/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)

E: Some index files failed to download, they have been ignored, or old ones used instead.

Open Software sources and disable the deb.opera.com repository and then try the terminal commands again after you have closed Software Sources.

Post the output to the forum if there is still an error.

Good luck

---

