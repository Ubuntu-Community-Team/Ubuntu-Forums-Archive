---
title: "Update Error : W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/trusty-up"
date: 2017-09-14
forum: Installation &amp; Upgrades
---

### Post by martharamkoti on 2017-09-14
HI Everyone, i am trying to update using cmd sudo apt update, but i am facing the the error:
```
vave@vave-Lenovo-G500:~$ sudo apt update[sudo] password for vave: 
Ign http://extras.ubuntu.com trusty InRelease
Ign http://archive.canonical.com trusty InRelease                              
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://extras.ubuntu.com trusty Release.gpg                                
Ign http://in.archive.ubuntu.com trusty InRelease                              
Hit http://ppa.launchpad.net trusty InRelease                                  
Get:1 http://security.ubuntu.com trusty-security InRelease [65.9 kB]           
Hit http://archive.canonical.com trusty Release.gpg                            
Ign http://dl.google.com stable InRelease                                      
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.canonical.com trusty Release                                
Hit http://dl.google.com stable Release.gpg                                    
Get:2 http://in.archive.ubuntu.com trusty-updates InRelease [65.9 kB]          
Hit http://dl.google.com stable Release                                        
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://dl.google.com stable/main amd64 Packages                            
Get:3 http://security.ubuntu.com trusty-security/main Sources [142 kB]         
Hit http://in.archive.ubuntu.com trusty-backports InRelease                  
Hit http://in.archive.ubuntu.com trusty Release.gpg                            
Get:4 http://in.archive.ubuntu.com trusty-updates/main Sources [405 kB]        
Get:5 http://security.ubuntu.com trusty-security/restricted Sources [4,955 B]
Ign http://dl.google.com stable/main Translation-en_IN                         
Ign http://dl.google.com stable/main Translation-en                           
Get:6 http://security.ubuntu.com trusty-security/universe Sources [63.0 kB]
Get:7 http://in.archive.ubuntu.com trusty-updates/restricted Sources [6,331 B] 
Get:8 http://in.archive.ubuntu.com trusty-updates/universe Sources [189 kB]    
Get:9 http://security.ubuntu.com trusty-security/multiverse Sources [3,215 B] 
Get:10 http://in.archive.ubuntu.com trusty-updates/multiverse Sources [7,747 B]
Hit http://in.archive.ubuntu.com trusty-backports/main Sources
Hit http://in.archive.ubuntu.com trusty-backports/restricted Sources
Hit http://in.archive.ubuntu.com trusty-backports/universe Sources
Hit http://in.archive.ubuntu.com trusty-backports/multiverse Sources
Hit http://in.archive.ubuntu.com trusty Release
Hit http://in.archive.ubuntu.com trusty/main Sources
Hit http://in.archive.ubuntu.com trusty/restricted Sources
Hit http://in.archive.ubuntu.com trusty/universe Sources
Hit http://in.archive.ubuntu.com trusty/multiverse Sources
Fetched 953 kB in 6s (155 kB/s)                                                
W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/trusty-updates/InRelease  Unable to find expected entry 'main/binary-1386/Packages' in Release file (Wrong sources.list entry or malformed file)
W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/trusty-backports/InRelease  Unable to find expected entry 'main/binary-1386/Packages' in Release file (Wrong sources.list entry or malformed file)
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/InRelease  Unable to find expected entry 'main/binary-1386/Packages' in Release file (Wrong sources.list entry or malformed file)
W: Failed to fetch http://ppa.launchpad.net/notepadqq-team/notepadqq/ubuntu/dists/trusty/InRelease  Unable to find expected entry 'main/binary-1386/Packages' in Release file (Wrong sources.list entry or malformed file)
W: Failed to fetch http://ppa.launchpad.net/umang/indicator-stickynotes/ubuntu/dists/trusty/InRelease  Unable to find expected entry 'main/binary-1386/Packages' in Release file (Wrong sources.list entry or malformed file)
W: Failed to fetch http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/trusty/InRelease  Unable to find expected entry 'main/binary-1386/Packages' in Release file (Wrong sources.list entry or malformed file)
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/trusty/Release  Unable to find expected entry 'main/binary-1386/Packages' in Release file (Wrong sources.list entry or malformed file)
W: Failed to fetch http://archive.canonical.com/dists/trusty/Release  Unable to find expected entry 'partner/binary-1386/Packages' in Release file (Wrong sources.list entry or malformed file)
W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/trusty/Release  Unable to find expected entry 'main/binary-1386/Packages' in Release file (Wrong sources.list entry or malformed file)
E: Some index files failed to download. They have been ignored, or old ones used instead.
vave@vave-Lenovo-G500:~$ 



```


And i am unable to install chromium browser using terminal and ubuntu software center : please find the question in ask ubuntu site 
[https://askubuntu.com/questions/955340/unable-to-install-chrominum-browser-in-ubuntu-14-04-4](https://askubuntu.com/questions/955340/unable-to-install-chrominum-browser-in-ubuntu-14-04-4)

i am using ubuntu 14.04.4
So please help me.

---

### Post by Bashing-om on 2017-09-14
martharamkoti; Hello;

" 1386 " is not a valid architecture .
where as i386 is valid. ( that silly one vice eye )
Confirm:
```

dpkg --print-foreign-architectures

```

Then if 1386  is listed do:
```

sudo dpkg --remove-architecture 1386

```

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by martharamkoti on 2017-09-14
HI Bashing-om, Thanks for your quick response i have tried your codes :

dpkg --print-foregin-architectures
sudo dpkg --remove-architecture 1386

and i tried sudo apt update, but got one warning:
```
Reading package lists... Done                                                  
W: Duplicate sources.list entry http://dl.google.com/linux/chrome/deb/ stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems
vave@vave-Lenovo-G500:~$ 



```

I tried sudo apt-get update also but same occurs.

---

### Post by Bashing-om on 2017-09-14
martharamkoti; Hey ... 

Another issue all together .
> 
W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/)................


So what you have to do here is find that duplicate entry.
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
and remove the duplicate . ( the 3rd party source belongs in the /etc/apt/sources.list.d/ directory )

[INDENT][INDENT]ain't nothing bit a thing
[/INDENT][/INDENT]

---

### Post by martharamkoti on 2017-09-14
Hello Bashing-om,
Thanks for suggesting the code, and its works fine. Thanks a lot.

---

### Post by ajgreeny on 2017-09-14
Great news! 
Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

### Post by Bashing-om on 2017-09-14
martharamkoti; Great !

> **martharamkoti said:**
> Hello Bashing-om,
Thanks for suggesting the code, and its works fine. Thanks a lot.


Glad2help

[INDENT]'buntu
[INDENT][INDENT]all for one and one for all
[/INDENT][/INDENT][/INDENT]

---

