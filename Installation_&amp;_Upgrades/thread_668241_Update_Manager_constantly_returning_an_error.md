---
title: "Update Manager constantly returning an error"
date: 2008-01-15
forum: Installation &amp; Upgrades
---

### Post by hnick on 2008-01-15
For some time now, Update manager has been returning this error:

E: karrigell-demo: subprocess post-installation script returned error exit status 1

Any suggestions? It doesn't appear to be causing trouble, but I dislike consistent error messages.

Thanks.

---

### Post by Partyboi2 on 2008-01-15
Can you post the output for this from a terminal (Applications>accessories>terminal)
```
sudo apt-get update
``````
sudo apt-get upgrade
```

---

### Post by hnick on 2008-01-15
hnick@TwoFlower:~$ sudo apt-get update
[sudo] password for hnick:
Get:1 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US               
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US       
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US    
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports Release.gpg [191B]          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Translation-en_US        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release                         
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports Release [44.0kB]            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources         
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Packages [14.8kB]      
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Packages [14B]   
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe Packages [62.7kB]  
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Packages [3175B] 
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Sources [5758B]       
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Sources [14B]   
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe Sources [11.8kB]  
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Sources [1379B] 
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages              
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US       
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Translation-en_US      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Packages               
Fetched 144kB in 15s (9098B/s)                                                 
Reading package lists... Done
hnick@TwoFlower:~$ 
hnick@TwoFlower:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
Setting up karrigell-demo (2.3.3-1) ...
chown: cannot access `/usr/share/karrigell/webapps/demo/records': No such file or directory
dpkg: error processing karrigell-demo (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 karrigell-demo
E: Sub-process /usr/bin/dpkg returned an error code (1)
hnick@TwoFlower:~$ 

Thanks

---

### Post by hnick on 2008-01-17
I'm guessing that karrigell-demo is broken. Oh well...]

---

### Post by PmDematagoda on 2008-01-17
Execute:-
```
sudo apt-get install -f
```
and
```
sudo dpkg --configure -a
```

Post the outputs you get for both commands.

---

### Post by Partyboi2 on 2008-01-17
here is a [bug report]("https://bugs.launchpad.net/ubuntu/+source/karrigell/+bug/183407")
Have a look in ```
/usr/share/karrigell/webapps/demo

``` if there is no folder named "records" then create it.
```
sudo mkdir /usr/share/karrigell/webapps/demo/records
```
then```
 sudo apt-get update
```
```
sudo apt-get upgrade
```
that should have hopefully taken care of the error message. You may want to add to that bug report so that it is confirmed and so that there will be some action taken to fix the problem with the package.:)

---

