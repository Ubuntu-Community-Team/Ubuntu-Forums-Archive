---
title: "Unable to upgrade to Ubuntu 13.10 fro Ubuntu 13.04"
date: 2013-10-24
forum: Installation &amp; Upgrades
---

### Post by AmitSinha on 2013-10-24
Hi,
I am new to Ubuntu and I am loving it !
I am using Ubuntu 13.04 , and I want to upgrade to the latest Ubuntu 13.10 , but am unable to.

Here is what I am doing :


[LIST]
[*]Open "Software Updater" - it checks for the list of available updates/upgrades and comes up with the message :
[/LIST]
          ```
 The Software on this computer is up to date.
           However,Ubuntu 13.10 is now available(you have 13.04).
          
```
[LIST]
[*]It gives me a list of options :
[/LIST]
         ```
Settings    Upgrade..   OK 
```
[LIST]
[*]I click on - Upgrade
[*]The authentication window comes up,and I give my password.
[/LIST]

Now , nothing happens :-(

Please help !

Thanks.

---

### Post by su:bhatta on 2013-10-24
How about trying from the terminal

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by AmitSinha on 2013-10-24
> **bhattabhishek said:**
> How about trying from the terminal

```
sudo apt-get update && sudo apt-get dist-upgrade
```

Didn't help :-(

Here is the O/P of :
sudo apt-get update 

```


amit@amit-desktop:~$ sudo apt-get update
[sudo] password for amit: 
Hit http://archive.ubuntu.com raring Release.gpg                               
Hit http://archive.canonical.com oneiric Release.gpg                           
Hit http://ppa.launchpad.net raring Release.gpg                                
Get:1 http://extras.ubuntu.com raring Release.gpg [72 B]                       
Get:2 http://archive.ubuntu.com raring-updates Release.gpg [933 B]   
Hit http://archive.canonical.com raring Release.gpg                            
Hit http://ppa.launchpad.net raring Release.gpg                      
Hit http://extras.ubuntu.com raring Release                          
Hit http://archive.ubuntu.com raring-backports Release.gpg           
Hit http://archive.canonical.com oneiric Release                               
Hit http://ppa.launchpad.net raring Release.gpg                                
Get:3 http://archive.ubuntu.com raring-security Release.gpg [933 B]            
Hit http://archive.canonical.com raring Release                                
Hit http://ppa.launchpad.net raring Release                                    
Hit http://extras.ubuntu.com raring/main i386 Packages                         
Get:4 http://archive.ubuntu.com raring-proposed Release.gpg [933 B]            
Hit http://archive.canonical.com oneiric/partner Sources                       
Hit http://ppa.launchpad.net raring Release                          
Hit http://archive.ubuntu.com raring Release                                   
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Hit http://ppa.launchpad.net raring Release                                    
Get:5 http://archive.ubuntu.com raring-updates Release [40.8 kB]               
Hit http://ppa.launchpad.net raring/main i386 Packages                         
Hit http://archive.canonical.com raring/partner i386 Packages                  
Hit http://archive.ubuntu.com raring-backports Release                         
Hit http://ppa.launchpad.net raring/main i386 Packages                         
Get:6 http://archive.ubuntu.com raring-security Release [40.8 kB]              
Get:7 http://archive.ubuntu.com raring-proposed Release [40.8 kB]              
Ign http://extras.ubuntu.com raring/main Translation-en_IN                     
Hit http://ppa.launchpad.net raring/main i386 Packages                         
Ign http://extras.ubuntu.com raring/main Translation-en                        
Hit http://archive.ubuntu.com raring/main i386 Packages                        
Hit http://archive.ubuntu.com raring/restricted i386 Packages         
Hit http://archive.ubuntu.com raring/universe i386 Packages
Hit http://archive.ubuntu.com raring/multiverse i386 Packages
Hit http://archive.ubuntu.com raring/main Translation-en
Hit http://archive.ubuntu.com raring/multiverse Translation-en
Hit http://archive.ubuntu.com raring/restricted Translation-en
Ign http://archive.canonical.com oneiric/partner Translation-en_IN
Hit http://archive.ubuntu.com raring/universe Translation-en
Ign http://archive.canonical.com oneiric/partner Translation-en
Get:8 http://archive.ubuntu.com raring-updates/main i386 Packages [195 kB]
Ign http://archive.canonical.com raring/partner Translation-en_IN             
Ign http://archive.canonical.com raring/partner Translation-en                
Get:9 http://archive.ubuntu.com raring-updates/restricted i386 Packages [14 B]
Get:10 http://archive.ubuntu.com raring-updates/universe i386 Packages [153 kB]
Get:11 http://archive.ubuntu.com raring-updates/multiverse i386 Packages [3,864 B]
Hit http://archive.ubuntu.com raring-updates/main Translation-en               
Ign http://ppa.launchpad.net raring/main Translation-en_IN                     
Ign http://ppa.launchpad.net raring/main Translation-en                        
Hit http://archive.ubuntu.com raring-updates/multiverse Translation-en         
Ign http://ppa.launchpad.net raring/main Translation-en_IN                     
Hit http://archive.ubuntu.com raring-updates/restricted Translation-en         
Ign http://ppa.launchpad.net raring/main Translation-en                        
Ign http://ppa.launchpad.net raring/main Translation-en_IN                     
Hit http://archive.ubuntu.com raring-updates/universe Translation-en           
Ign http://ppa.launchpad.net raring/main Translation-en                        
Hit http://archive.ubuntu.com raring-backports/main i386 Packages              
Hit http://archive.ubuntu.com raring-backports/restricted i386 Packages        
Hit http://archive.ubuntu.com raring-backports/universe i386 Packages          
Hit http://archive.ubuntu.com raring-backports/multiverse i386 Packages        
Hit http://archive.ubuntu.com raring-backports/main Translation-en             
Hit http://archive.ubuntu.com raring-backports/multiverse Translation-en       
Hit http://archive.ubuntu.com raring-backports/restricted Translation-en       
Hit http://archive.ubuntu.com raring-backports/universe Translation-en         
Get:12 http://archive.ubuntu.com raring-security/main i386 Packages [127 kB]   
Get:13 http://archive.ubuntu.com raring-security/restricted i386 Packages [14 B]
Get:14 http://archive.ubuntu.com raring-security/universe i386 Packages [40.5 kB]
Get:15 http://archive.ubuntu.com raring-security/multiverse i386 Packages [3,864 B]
Hit http://archive.ubuntu.com raring-security/main Translation-en              
Hit http://archive.ubuntu.com raring-security/multiverse Translation-en        
Hit http://archive.ubuntu.com raring-security/restricted Translation-en        
Hit http://archive.ubuntu.com raring-security/universe Translation-en          
Get:16 http://archive.ubuntu.com raring-proposed/restricted i386 Packages [14 B]
Get:17 http://archive.ubuntu.com raring-proposed/main i386 Packages [72.4 kB]  
Get:18 http://archive.ubuntu.com raring-proposed/multiverse i386 Packages [1,554 B]
Get:19 http://archive.ubuntu.com raring-proposed/universe i386 Packages [33.6 kB]
Hit http://archive.ubuntu.com raring-proposed/main Translation-en              
Hit http://archive.ubuntu.com raring-proposed/multiverse Translation-en        
Hit http://archive.ubuntu.com raring-proposed/restricted Translation-en        
Hit http://archive.ubuntu.com raring-proposed/universe Translation-en          
Ign http://archive.ubuntu.com raring/main Translation-en_IN                    
Ign http://archive.ubuntu.com raring/multiverse Translation-en_IN
Ign http://archive.ubuntu.com raring/restricted Translation-en_IN
Ign http://archive.ubuntu.com raring/universe Translation-en_IN
Ign http://archive.ubuntu.com raring-updates/main Translation-en_IN
Ign http://archive.ubuntu.com raring-updates/multiverse Translation-en_IN
Ign http://archive.ubuntu.com raring-updates/restricted Translation-en_IN
Ign http://archive.ubuntu.com raring-updates/universe Translation-en_IN
Ign http://archive.ubuntu.com raring-backports/main Translation-en_IN
Ign http://archive.ubuntu.com raring-backports/multiverse Translation-en_IN
Ign http://archive.ubuntu.com raring-backports/restricted Translation-en_IN
Ign http://archive.ubuntu.com raring-backports/universe Translation-en_IN
Ign http://archive.ubuntu.com raring-security/main Translation-en_IN
Ign http://archive.ubuntu.com raring-security/multiverse Translation-en_IN
Ign http://archive.ubuntu.com raring-security/restricted Translation-en_IN
Ign http://archive.ubuntu.com raring-security/universe Translation-en_IN
Ign http://archive.ubuntu.com raring-proposed/main Translation-en_IN
Ign http://archive.ubuntu.com raring-proposed/multiverse Translation-en_IN
Ign http://archive.ubuntu.com raring-proposed/restricted Translation-en_IN
Ign http://archive.ubuntu.com raring-proposed/universe Translation-en_IN
Fetched 756 kB in 29s (25.8 kB/s)
Reading package lists... Done
amit@amit-desktop:~$ 

```


Here is the O/P of :
sudo apt-get dist-upgrade

```


amit@amit-desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
amit@amit-desktop:~$ 


```

Please help further , thanks !

---

### Post by Dennis N on 2013-10-24
**apt-get dist-upgrade** does not a perform an upgrade to the next distribution. See [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading) for information on how to upgrade from 13.04 to 13.10.

See:
[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

for general information on apt-get and its options.
.

---

### Post by AmitSinha on 2013-10-24
> **Dennis N said:**
> **apt-get dist-upgrade** does not a perform an upgrade to the next distribution. See [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading) for information on how to upgrade from 13.04 to 13.10.

See:
[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

for general information on apt-get and its options.
.



Thanks Dennis !
I followed all the steps at [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading) and then came here.But as suggested in the page,I have posted in AskUbuntu - [http://askubuntu.com/questions/364987/unable-to-upgrade-to-ubuntu-13-10-fro-ubuntu-13-04](http://askubuntu.com/questions/364987/unable-to-upgrade-to-ubuntu-13-10-fro-ubuntu-13-04)

Hope it will be resolved soon.

Thanks again...

---

### Post by sanderj on 2013-10-24
I would just type:

```
do-release-upgrade
```

HTH

---

### Post by craig10x on 2013-10-24
If you are only running one ubuntu, burn the 13.10 iso and run the live session....after your in it, hit the install ubuntu icon on the unity bar and when the installer opens, one of the automatic options it should offer is to UPGRADE your 13.04 to 13.10...if it does, use that!  It will do the upgrade directly from the iso image (doesn't need to go to the internet) and will be fast too (like 25 minutes tops)...I've used it twice and it works great...

Be sure to turn off (uncheck) any ppas you have in your software sources before you boot into the 13.10 live session cd...

---

### Post by AmitSinha on 2013-10-30
> **craig10x said:**
> If you are only running one ubuntu, burn the 13.10 iso and run the live session....after your in it, hit the install ubuntu icon on the unity bar and when the installer opens, one of the automatic options it should offer is to UPGRADE your 13.04 to 13.10...if it does, use that!  It will do the upgrade directly from the iso image (doesn't need to go to the internet) and will be fast too (like 25 minutes tops)...I've used it twice and it works great...

Be sure to turn off (uncheck) any ppas you have in your software sources before you boot into the 13.10 live session cd...


Hi Dennis/Craig/All , Thanks a ton for the help ! Finally ```
do-release-upgrade
```helped , and I now have Ubuntu 13.10 !!!
But my desktop has turned black , and I am not able to set any wallpaper !! I will check for similar issues..

Thanks again !

---

### Post by AmitSinha on 2013-10-30
> **AmitSinha said:**
> Hi Dennis/Craig/All , Thanks a ton for the help ! Finally ```
do-release-upgrade
```helped , and I now have Ubuntu 13.10 !!!
But my desktop has turned black , and I am not able to set any wallpaper !! I will check for similar issues..

Thanks again !


Oops ! I mean Sanderj .. Dennis was there at the back of my mind :-) Thanks Sanderj !!

---

