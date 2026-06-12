---
title: "Adobe reader not installing"
date: 2012-07-11
forum: Installation &amp; Upgrades
---

### Post by deep2sunny on 2012-07-11
Hello i've ubuntu 12.04 LTS. I'm trying to install adobe reader via software center but its not installing. Its throwing some Package Operation failed. Please help me with it

n I'm new to ubuntu

---

### Post by kc1di on 2012-07-11
> **deep2sunny said:**
> Hello i've ubuntu 12.04 LTS. I'm trying to install adobe reader via software center but its not installing. Its throwing some Package Operation failed. Please help me with it

n I'm new to ubuntu

Hi and welcome to Ubuntu. 
it would be helpful if we could see the error message it's giving you. but here are a couple things to try.

Go to a terminal and type the following command one at a time:

```
sudo apt-get clean
sudo rm /var/lib/apt/lists/* -vf 
sudo apt-get update
```
you can just copy and past them in a terminal.

then try install Acrobat Reader again.

If that fails  try this.
in a terminal again
install synaptic package manager.
```
sudo apt-get install syanptic
```
when that finished installing do a search for syanptic and in synaptic search for Arcoread or adobe and try to install it from there. should work.

Good luck :)

---

### Post by deep2sunny on 2012-07-11
thnaks for the help i solved it myself. but i'm getting an error while doing

sudo apt-get update

```
akash@akash-Satellite-A60:~$ sudo apt-get update
Ign http://archive.canonical.com precise InRelease                             
Ign http://security.ubuntu.com precise-security InRelease                      
Get:1 http://archive.canonical.com precise Release.gpg [198 B]                 
Ign http://extras.ubuntu.com precise InRelease                                 
Ign http://in.archive.ubuntu.com precise InRelease                             
Ign http://in.archive.ubuntu.com precise-updates InRelease                     
Ign http://in.archive.ubuntu.com precise-backports InRelease                   
Ign http://archive.ubuntu.com precise InRelease                                
Ign http://ppa.launchpad.net precise InRelease                                 
Get:2 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Get:3 http://archive.canonical.com precise Release [7,078 B]                   
Get:4 http://extras.ubuntu.com precise Release.gpg [72 B]                      
Get:5 http://in.archive.ubuntu.com precise Release.gpg [198 B]                 
Get:6 http://archive.ubuntu.com precise Release.gpg [198 B]                    
Ign http://ppa.launchpad.net precise Release.gpg                               
Get:7 http://security.ubuntu.com precise-security Release [49.6 kB]            
Get:8 http://in.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Get:9 http://extras.ubuntu.com precise Release [11.9 kB]                       
Get:10 http://archive.ubuntu.com precise Release [49.6 kB]                     
Ign http://ppa.launchpad.net precise Release                                   
Get:11 http://in.archive.ubuntu.com precise-backports Release.gpg [198 B]      
Err http://ppa.launchpad.net precise/main Sources                              
  
Get:12 http://archive.canonical.com precise/partner i386 Packages [4,982 B]    
Get:13 http://in.archive.ubuntu.com precise Release [49.6 kB]                  
Err http://ppa.launchpad.net precise/main Sources                              
  
Err http://ppa.launchpad.net precise/main Sources                              
  
Err http://ppa.launchpad.net precise/main Sources                              
  
Err http://ppa.launchpad.net precise/main Sources                              
  404  Not Found
Ign http://archive.canonical.com precise/partner TranslationIndex              
Get:14 http://extras.ubuntu.com precise/main Sources [1,020 B]                 
Get:15 http://extras.ubuntu.com precise/main i386 Packages [1,229 B]           
Get:16 http://archive.ubuntu.com precise/main Sources [934 kB]                 
Get:17 http://security.ubuntu.com precise-security/restricted Sources [14 B]   
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Get:18 http://security.ubuntu.com precise-security/main Sources [24.8 kB]      
Get:19 http://in.archive.ubuntu.com precise-updates Release [49.6 kB]          
Ign http://archive.canonical.com precise/partner Translation-en_IN             
Ign http://archive.canonical.com precise/partner Translation-en                
Ign http://extras.ubuntu.com precise/main Translation-en_IN                    
Ign http://extras.ubuntu.com precise/main Translation-en                       
Get:20 http://security.ubuntu.com precise-security/multiverse Sources [713 B]  
Get:21 http://security.ubuntu.com precise-security/universe Sources [7,832 B]  
Get:22 http://in.archive.ubuntu.com precise-backports Release [49.6 kB]        
Get:23 http://security.ubuntu.com precise-security/main i386 Packages [75.5 kB]
Get:24 http://in.archive.ubuntu.com precise/restricted Sources [5,470 B]       
Get:25 http://in.archive.ubuntu.com precise/main Sources [934 kB]              
Get:26 http://security.ubuntu.com precise-security/restricted i386 Packages [14 B]
Get:27 http://security.ubuntu.com precise-security/multiverse i386 Packages [1,394 B]
Get:28 http://security.ubuntu.com precise-security/universe i386 Packages [19.7 kB]
Get:29 http://security.ubuntu.com precise-security/main TranslationIndex [73 B]
Get:30 http://security.ubuntu.com precise-security/multiverse TranslationIndex [71 B]
Get:31 http://security.ubuntu.com precise-security/restricted TranslationIndex [70 B]
Get:32 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B]
Get:33 http://security.ubuntu.com precise-security/main Translation-en [38.4 kB]
Get:34 http://security.ubuntu.com precise-security/multiverse Translation-en [587 B]
Get:35 http://security.ubuntu.com precise-security/restricted Translation-en [14 B]
Get:36 http://security.ubuntu.com precise-security/universe Translation-en [13.3 kB]
Get:37 http://archive.ubuntu.com precise/restricted Sources [5,470 B]          
Get:38 http://in.archive.ubuntu.com precise/multiverse Sources [155 kB]        
Get:39 http://in.archive.ubuntu.com precise/universe Sources [5,019 kB]        
Get:40 http://in.archive.ubuntu.com precise/main i386 Packages [1,274 kB]      
Get:41 http://in.archive.ubuntu.com precise/restricted i386 Packages [8,431 B] 
Get:42 http://in.archive.ubuntu.com precise/multiverse i386 Packages [121 kB]  
Get:43 http://in.archive.ubuntu.com precise/universe i386 Packages [4,796 kB]  
Get:44 http://in.archive.ubuntu.com precise/main TranslationIndex [3,706 B]    
Get:45 http://in.archive.ubuntu.com precise/multiverse TranslationIndex [2,676 B]
Get:46 http://in.archive.ubuntu.com precise/restricted TranslationIndex [2,596 B]
Get:47 http://in.archive.ubuntu.com precise/universe TranslationIndex [2,922 B]
Get:48 http://in.archive.ubuntu.com precise-updates/restricted Sources [1,379 B]
Get:49 http://in.archive.ubuntu.com precise-updates/main Sources [127 kB]      
Get:50 http://in.archive.ubuntu.com precise-updates/multiverse Sources [1,058 B]
Get:51 http://in.archive.ubuntu.com precise-updates/universe Sources [33.0 kB] 
Get:52 http://in.archive.ubuntu.com precise-updates/main i386 Packages [321 kB]
Get:53 http://in.archive.ubuntu.com precise-updates/restricted i386 Packages [2,439 B]
Get:54 http://in.archive.ubuntu.com precise-updates/multiverse i386 Packages [2,047 B]
Get:55 http://in.archive.ubuntu.com precise-updates/universe i386 Packages [88.6 kB]
Get:56 http://in.archive.ubuntu.com precise-updates/main TranslationIndex [74 B]
Get:57 http://in.archive.ubuntu.com precise-updates/multiverse TranslationIndex [71 B]
Get:58 http://in.archive.ubuntu.com precise-updates/restricted TranslationIndex [71 B]
Get:59 http://in.archive.ubuntu.com precise-updates/universe TranslationIndex [73 B]
Get:60 http://in.archive.ubuntu.com precise-backports/main Sources [1,845 B]   
Get:61 http://in.archive.ubuntu.com precise-backports/restricted Sources [14 B]
Get:62 http://in.archive.ubuntu.com precise-backports/universe Sources [11.9 kB]
Get:63 http://in.archive.ubuntu.com precise-backports/multiverse Sources [1,383 B]
Get:64 http://in.archive.ubuntu.com precise-backports/main i386 Packages [1,271 B]
Get:65 http://in.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Get:66 http://in.archive.ubuntu.com precise-backports/universe i386 Packages [10.2 kB]
Get:67 http://in.archive.ubuntu.com precise-backports/multiverse i386 Packages [999 B]
Get:68 http://in.archive.ubuntu.com precise-backports/main TranslationIndex [71 B]
Get:69 http://in.archive.ubuntu.com precise-backports/multiverse TranslationIndex [71 B]
Get:70 http://in.archive.ubuntu.com precise-backports/restricted TranslationIndex [70 B]
Get:71 http://in.archive.ubuntu.com precise-backports/universe TranslationIndex [72 B]
Get:72 http://in.archive.ubuntu.com precise/main Translation-en [726 kB]       
Get:73 http://in.archive.ubuntu.com precise/multiverse Translation-en [93.4 kB]
Get:74 http://in.archive.ubuntu.com precise/restricted Translation-en [2,395 B]
Get:75 http://in.archive.ubuntu.com precise/universe Translation-en [3,341 kB] 
Get:76 http://in.archive.ubuntu.com precise-updates/main Translation-en [150 kB]
Get:77 http://in.archive.ubuntu.com precise-updates/multiverse Translation-en [912 B]
Get:78 http://in.archive.ubuntu.com precise-updates/restricted Translation-en [798 B]
Get:79 http://in.archive.ubuntu.com precise-updates/universe Translation-en [52.8 kB]
Get:80 http://in.archive.ubuntu.com precise-backports/main Translation-en [908 B]
Get:81 http://in.archive.ubuntu.com precise-backports/multiverse Translation-en [422 B]
Get:82 http://in.archive.ubuntu.com precise-backports/restricted Translation-en [14 B]
Get:83 http://in.archive.ubuntu.com precise-backports/universe Translation-en [7,494 B]
Fetched 18.7 MB in 6min 58s (44.7 kB/s)                                        
W: Failed to fetch http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/dists/precise/main/source/Sources  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
akash@akash-Satellite-A60:~$ 

```


Please check this n tell what is wrong n how to correct it.

---

### Post by kc1di on 2012-07-11
it looks like you have a ppa installed that you no longer need or is no longer valid.  here's a web page that will tell you how to uninstall it. that should take care of your error message. 

[http://bigbrovar.aoizora.org/index.php/2010/01/10/how-to-safely-remove-ppa-repository-from-ubuntu/]("http://bigbrovar.aoizora.org/index.php/2010/01/10/how-to-safely-remove-ppa-repository-from-ubuntu/")

---

### Post by deep2sunny on 2012-07-11
so should i remove it or let be like that. Is it important to do so. Thanks in advance

---

### Post by deep2sunny on 2012-07-12
my PPA is damaged or what. how to reinstall.

---

### Post by kc1di on 2012-07-12
> **deep2sunny said:**
> so should i remove it or let be like that. Is it important to do so. Thanks in advance

I would remove it and re install it if it's needed.  If your Chromium-Browser is up to date then you may not need it.

---

