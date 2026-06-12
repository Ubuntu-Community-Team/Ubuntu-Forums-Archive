---
title: "Multiple issues. Please help"
date: 2012-07-12
forum: Installation &amp; Upgrades
---

### Post by deep2sunny on 2012-07-12
I've Ubuntu 12.04 LTS. n i'm new to ubuntu... My issues

1. Sometimes when I start my ubuntu, my both browsers(firefox n chrome) fail to load. Chrome gives Aw Snap! on very site and firefox exits giving an error. Then I've to restart ubuntu n becomes normal, but y does it fail to start when I start ubuntu for the 1st time.

2. Sometimes I get "System Program Problem Detected". I even performed ... sudo rm /var/crash/*. It disappers on restart but it comes back again.

3. How to check if my all packages are properly installed and there r no errors. 

Please help guys.

---

### Post by carl4926 on 2012-07-12
Can I ask
Is your system fully updated.

Reason I ask is: My system recently displayed these symptoms following the most recent updates. It's not critical for me as I have multiple Linux installs, so I'm working on the problem when I can, currently working with Mint though.
I didn't trawl through my logs yet either

---

### Post by deep2sunny on 2012-07-12
yeah my ubuntu 12.04 LTS is fully updated. But y these issues occur

---

### Post by carl4926 on 2012-07-12
> **deep2sunny said:**
> yeah my ubuntu 12.04 LTS is fully updated. But y these issues occur

Which is why I said
> My system recently displayed these symptoms following the most recent updates

---

### Post by deep2sunny on 2012-07-12
Ok both of us are in the same problem but what about others.

---

### Post by Shadius on 2012-07-12
My install has exhibited these symptoms as well. Chrome would crash multiple times in a row, but Firefox wouldn't crash. I stopped using Chrome and went to using Firefox.

I've gotten the "System Program Problem Detected" and something about an internal error. Then Apport makes a report to send.

---

### Post by deep2sunny on 2012-07-12
brillant guys, but y does my firefox fails to start

---

### Post by dino99 on 2012-07-12
a few questions:

- is there some extra archive(s) used ? like ppa ?
- do you get usefull warnings/errors logged ?
watch .xsession-errors inside /home (ctrl+h to unhide it), and into /var/log/

into a terminal, run:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install --fix-missing

sudo dpkg-reconfigure -phigh -a
( be patient, it can take a while, dont stop it before it end itself)

---

### Post by Shadius on 2012-07-12
> **deep2sunny said:**
> brillant guys, but y does my firefox fails to start

Have you tried reinstalling Firefox?

---

### Post by deep2sunny on 2012-07-12
wait i'll just show u something related to ppa

when i run : sudo apt-get update,

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

can u plz anyalse this

no i cannot log errors

yeah i've reinstalled firefox but that also didn't help either

---

### Post by deep2sunny on 2012-07-12
> **dino99 said:**
> a few questions:

- is there some extra archive(s) used ? like ppa ?
- do you get usefull warnings/errors logged ?
watch .xsession-errors inside /home (ctrl+h to unhide it), and into /var/log/

into a terminal, run:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install --fix-missing

sudo dpkg-reconfigure -phigh -a
( be patient, it can take a while, dont stop it before it end itself)

i'm sitting on my windows PC, will surely try that sudo on my laptop ubuntu

---

### Post by Shadius on 2012-07-12
> **deep2sunny said:**
> wait i'll just show u something related to ppa

when i run : sudo apt-get update,

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

can u plz anyalse this

no i cannot log errors

yeah i've reinstalled firefox but that also didn't help either

Now try the next commands to see if it resolves the problem.

---

### Post by dino99 on 2012-07-12
if you want to use the bleeding-edge packages archives (ppa) then you need to read & understand how to install & use a ppa:

you get that error:

[http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release

of course that means nothing  :confused:  (ppa.launchpad is fullfilled with ppas, but which one to use ? you have selected none :( )

and not all ppas have packages "source" , you really need to use some logic here (and be a little bit more curious)

---

### Post by deep2sunny on 2012-07-12
so which one should i select to resolve it, plz direct me. Does that error have any major effect?

---

### Post by deep2sunny on 2012-07-12
i've 0 knowledge about ubuntu, give me some useful links to read. or u solve it for me that will be better

---

### Post by Shadius on 2012-07-12
> **deep2sunny said:**
> i've 0 knowledge about ubuntu, give me some useful links to read. or u solve it for me that will be better

Did you try to install Chromium using a PPA?

---

### Post by dino99 on 2012-07-12
> **deep2sunny said:**
> so which one should i select to resolve it, plz direct me. Does that error have any major effect?

i can make decisions for myself :P but i'm not inside your mind :( to know what you are looking for  :confused:

if you have decided to install/use ppa(s), the main question is "why" and you only can answer to that question. Then which one(s) have you tried to install and how ?

you seems like a kid wanting to try all the toys he can see and find. 

Generally speaking "ppa" is not needed, and often push troubles ahead as these packages are often too "new" to be "stable"

---

### Post by deep2sunny on 2012-07-12
yaar i tried chromium. i installed it using software center but whenever i run the chromium prowser "System program problem detcted " used to pop up. so i unistalled it n installed google chrome stable from chrome's website, that is kind of stable but now creating issues like Aw snap!

---

### Post by deep2sunny on 2012-07-12
@ DINO99, HOW CAN i check if all my ubuntu packages n dependcies are intact and there r no errors in it.

---

### Post by Shadius on 2012-07-12
> **deep2sunny said:**
> @ DINO99, HOW CAN i check if all my ubuntu packages n dependcies are intact and there r no errors in it.

Try:
```
sudo apt-get upgrade 
```
Along with the previous commands suggested.

---

### Post by deep2sunny on 2012-07-12
sudo apt-get install --fix-missing

"sudo dpkg-reconfigure -phigh -a" what does this command do? n why is taking so long..n by mistake i forgot to run "sudo apt-get install --fix-missing" before  the one mentioned in the 1st line.

---

### Post by deep2sunny on 2012-07-12
> **dino99 said:**
> a few questions:

- is there some extra archive(s) used ? like ppa ?
- do you get usefull warnings/errors logged ?
watch .xsession-errors inside /home (ctrl+h to unhide it), and into /var/log/

into a terminal, run:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install --fix-missing

sudo dpkg-reconfigure -phigh -a
( be patient, it can take a while, dont stop it before it end itself)

here is the result

```
akash@akash-Satellite-A60:~$ sudo apt-get clean
[sudo] password for akash: 
akash@akash-Satellite-A60:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
akash@akash-Satellite-A60:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
akash@akash-Satellite-A60:~$ sudo apt-get update
Ign http://dl.google.com stable InRelease                                      
Ign http://archive.canonical.com precise InRelease                             
Get:1 http://dl.google.com stable Release.gpg [198 B]                          
Ign http://in.archive.ubuntu.com precise InRelease                             
Ign http://in.archive.ubuntu.com precise-updates InRelease                     
Ign http://in.archive.ubuntu.com precise-backports InRelease                   
Ign http://security.ubuntu.com precise-security InRelease                      
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://extras.ubuntu.com precise InRelease                                 
Hit http://archive.canonical.com precise Release.gpg                           
Get:2 http://in.archive.ubuntu.com precise Release.gpg [198 B]                 
Get:3 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Ign http://ppa.launchpad.net precise Release.gpg                               
Ign http://archive.ubuntu.com precise InRelease                                
Hit http://archive.canonical.com precise Release                               
Get:4 http://extras.ubuntu.com precise Release.gpg [72 B]                      
Get:5 http://in.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Get:6 http://security.ubuntu.com precise-security Release [49.6 kB]            
Ign http://ppa.launchpad.net precise Release                                   
Hit http://extras.ubuntu.com precise Release                                   
Get:7 http://in.archive.ubuntu.com precise-backports Release.gpg [198 B]       
Get:8 http://archive.ubuntu.com precise Release.gpg [198 B]                    
Hit http://archive.canonical.com precise/partner i386 Packages                 
Err http://ppa.launchpad.net precise/main Sources                              
  
Hit http://extras.ubuntu.com precise/main Sources                              
Get:9 http://in.archive.ubuntu.com precise Release [49.6 kB]                   
Get:10 http://archive.ubuntu.com precise Release [49.6 kB]                     
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Err http://ppa.launchpad.net precise/main Sources                              
  
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Err http://ppa.launchpad.net precise/main Sources                              
  
Ign http://archive.canonical.com precise/partner Translation-en_IN             
Err http://ppa.launchpad.net precise/main Sources                              
  
Get:11 http://security.ubuntu.com precise-security/restricted Sources [14 B]   
Ign http://archive.canonical.com precise/partner Translation-en                
Get:12 http://in.archive.ubuntu.com precise-updates Release [49.6 kB]          
Err http://ppa.launchpad.net precise/main Sources                              
  404  Not Found
Ign http://extras.ubuntu.com precise/main Translation-en_IN                    
Get:13 http://security.ubuntu.com precise-security/main Sources [24.8 kB]      
Ign http://extras.ubuntu.com precise/main Translation-en                       
Get:14 http://archive.ubuntu.com precise/main Sources [934 kB]                 
Get:15 http://in.archive.ubuntu.com precise-backports Release [49.6 kB]        
Get:16 http://security.ubuntu.com precise-security/multiverse Sources [713 B]  
Get:17 http://security.ubuntu.com precise-security/universe Sources [7,832 B]  
Get:18 http://security.ubuntu.com precise-security/main i386 Packages [75.5 kB]
Get:19 http://dl.google.com stable Release [1,347 B]                           
Get:20 http://security.ubuntu.com precise-security/restricted i386 Packages [14 B]
Get:21 http://security.ubuntu.com precise-security/multiverse i386 Packages [1,394 B]
Get:22 http://security.ubuntu.com precise-security/universe i386 Packages [19.7 kB]
Get:23 http://dl.google.com stable/main i386 Packages [1,243 B]                
Get:24 http://in.archive.ubuntu.com precise/restricted Sources [5,470 B]       
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Get:25 http://in.archive.ubuntu.com precise/main Sources [934 kB]              
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Ign http://dl.google.com stable/main TranslationIndex                          
Ign http://dl.google.com stable/main Translation-en_IN                         
Ign http://dl.google.com stable/main Translation-en                            
Get:26 http://in.archive.ubuntu.com precise/multiverse Sources [155 kB]        
Get:27 http://archive.ubuntu.com precise/restricted Sources [5,470 B]          
Get:28 http://in.archive.ubuntu.com precise/universe Sources [5,019 kB]        
Get:29 http://in.archive.ubuntu.com precise/main i386 Packages [1,274 kB]      
Get:30 http://in.archive.ubuntu.com precise/restricted i386 Packages [8,431 B] 
Get:31 http://in.archive.ubuntu.com precise/multiverse i386 Packages [121 kB]  
Get:32 http://in.archive.ubuntu.com precise/universe i386 Packages [4,796 kB]  
Hit http://in.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://in.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://in.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://in.archive.ubuntu.com precise/universe TranslationIndex             
Get:33 http://in.archive.ubuntu.com precise-updates/restricted Sources [1,379 B]
Get:34 http://in.archive.ubuntu.com precise-updates/main Sources [127 kB]      
Get:35 http://in.archive.ubuntu.com precise-updates/multiverse Sources [1,058 B]
Get:36 http://in.archive.ubuntu.com precise-updates/universe Sources [33.0 kB] 
Get:37 http://in.archive.ubuntu.com precise-updates/main i386 Packages [321 kB]
Get:38 http://in.archive.ubuntu.com precise-updates/restricted i386 Packages [2,439 B]
Get:39 http://in.archive.ubuntu.com precise-updates/multiverse i386 Packages [2,047 B]
Get:40 http://in.archive.ubuntu.com precise-updates/universe i386 Packages [88.6 kB]
Get:41 http://in.archive.ubuntu.com precise-updates/universe i386 Packages [88.6 kB]
Hit http://in.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://in.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://in.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://in.archive.ubuntu.com precise-updates/universe TranslationIndex     
Get:42 http://in.archive.ubuntu.com precise-backports/main Sources [1,845 B]   
Get:43 http://in.archive.ubuntu.com precise-backports/restricted Sources [14 B]
Get:44 http://in.archive.ubuntu.com precise-backports/universe Sources [11.9 kB]
Get:45 http://in.archive.ubuntu.com precise-backports/multiverse Sources [1,383 B]
Get:46 http://in.archive.ubuntu.com precise-backports/main i386 Packages [1,271 B]
Get:47 http://in.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Get:48 http://in.archive.ubuntu.com precise-backports/universe i386 Packages [10.2 kB]
Get:49 http://in.archive.ubuntu.com precise-backports/multiverse i386 Packages [999 B]
Hit http://in.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://in.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://in.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://in.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://in.archive.ubuntu.com precise/main Translation-en                   
Hit http://in.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://in.archive.ubuntu.com precise/restricted Translation-en             
Hit http://in.archive.ubuntu.com precise/universe Translation-en               
Hit http://in.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://in.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://in.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://in.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://in.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://in.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://in.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://in.archive.ubuntu.com precise-backports/universe Translation-en     
Fetched 14.2 MB in 5min 14s (45.2 kB/s)                                        
W: Failed to fetch http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/dists/precise/main/source/Sources  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
akash@akash-Satellite-A60:~$ sudp apt-get install --fix-missing
No command 'sudp' found, did you mean:
 Command 'sup' from package 'sup' (universe)
 Command 'sudo' from package 'sudo' (main)
 Command 'sudo' from package 'sudo-ldap' (universe)
 Command 'sfdp' from package 'graphviz' (main)
sudp: command not found
akash@akash-Satellite-A60:~$ sudo dpkg-reconfigure -phigh -a
akash@akash-Satellite-A60:~$ sudo apt-get install --fix-missing
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
akash@akash-Satellite-A60:~$ 

```

---

### Post by deep2sunny on 2012-07-12
Please analyse the above post. Sometimes my ubuntu's chat also doesn't work , it gives internal error. Something is wrong somewhere. Please guys help me, sometimes i face internal error n sometimes "System Program problem Detected". its getting frustrated, i've to restart my laptop to sort out things.

---

### Post by steakneggs on 2012-10-11
I know this is an old post but I had similar problems and nothing seemed to work. Firefox would crash and Chrome would give me the Aw Shucks screen all the time. I tried all the usual remedy's - cleaning up apt, removing FF profile, installing Flash-aid, installing the latest stable kernel. None of it worked. The whole system seemed un-stable. (BTW running 12.04 64-bit). Then Ubuntu started to randomly set my hard drive to read-only. I checked the hard drive using the Smart utility and no errors were found. I then downloaded memtest86 from [memtest.org]("http://www.memtest.org/") and ran the bootable CD. There were thousands of errors detected! I have since replaced the RAM, and retested it (0 errors). Now Firefox and Chrome are working perfectly! Before you upgrade or install Ubuntu, I highly recommend checking your memory for errors first. It could save you a lot of frustration.

---

