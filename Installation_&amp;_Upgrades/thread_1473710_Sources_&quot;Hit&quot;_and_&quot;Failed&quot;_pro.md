---
title: "Sources &quot;Hit&quot; and &quot;Failed&quot; problem"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by Belki on 2010-05-05
I am using Ubuntu 10.04 Lucid. Recently, when i try making update, all of my sources are hit or failed and they are 0 B. If I go to server page and click "Select Best Server", it's testing, finding best server for me (different servers every time), refreshing and downloading sources but only for first time. If I refresh my update manager second time, it is same again. How can I fix this?

In my Terminal, this issue is same and after finish refreshing there is no error.

---

### Post by uRock on 2010-05-05
Can you run ```
sudo apt-get update
``` in a terminal and post the results for us? To put the text in a box like I did the command, just highlight the text, then click the # sign in the menu above.

---

### Post by Belki on 2010-05-05
```
yn@yn-bs:~$ sudo apt-get update
[sudo] password for yn: 
Hit http://packages.medibuntu.org lucid Release.gpg                 
Ign http://packages.medibuntu.org/ lucid/free Translation-en_US     
Ign http://packages.medibuntu.org/ lucid/non-free Translation-en_US 
Hit http://packages.medibuntu.org lucid Release                      
Hit http://packages.medibuntu.org lucid/free Packages                
Hit http://packages.medibuntu.org lucid/non-free Packages
Hit http://ubuntu.cica.es lucid Release.gpg    
Hit http://ppa.launchpad.net lucid Release.gpg 
Ign http://ubuntu.cica.es/ubuntu/ lucid/main Translation-en_US
Ign http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/ lucid/main Translation-en_US
Ign http://ubuntu.cica.es/ubuntu/ lucid/restricted Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg 
Ign http://ubuntu.cica.es/ubuntu/ lucid/universe Translation-en_US
Ign http://ppa.launchpad.net/sevenmachines/flash/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg 
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ lucid/main Translation-en_US
Ign http://ubuntu.cica.es/ubuntu/ lucid/multiverse Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg 
Ign http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release     
Hit http://ppa.launchpad.net lucid Release                           
Hit http://ppa.launchpad.net lucid Release                           
Hit http://ppa.launchpad.net lucid Release                           
Hit http://ubuntu.cica.es lucid-updates Release.gpg                  
Hit http://ppa.launchpad.net lucid/main Packages
Ign http://ubuntu.cica.es/ubuntu/ lucid-updates/main Translation-en_US
Hit http://ppa.launchpad.net lucid/main Packages
Ign http://ubuntu.cica.es/ubuntu/ lucid-updates/restricted Translation-en_US
Hit http://ppa.launchpad.net lucid/main Packages
Ign http://ubuntu.cica.es/ubuntu/ lucid-updates/universe Translation-en_US
Hit http://ppa.launchpad.net lucid/main Packages
Ign http://ubuntu.cica.es/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://ubuntu.cica.es lucid-security Release.gpg
Ign http://ubuntu.cica.es/ubuntu/ lucid-security/main Translation-en_US
Ign http://ubuntu.cica.es/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://ubuntu.cica.es/ubuntu/ lucid-security/universe Translation-en_US
Ign http://ubuntu.cica.es/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://ubuntu.cica.es lucid Release
Hit http://ubuntu.cica.es lucid-updates Release
Hit http://ubuntu.cica.es lucid-security Release
Hit http://ubuntu.cica.es lucid/main Packages  
Hit http://ubuntu.cica.es lucid/restricted Packages
Hit http://ubuntu.cica.es lucid/main Sources
Hit http://ubuntu.cica.es lucid/restricted Sources
Hit http://ubuntu.cica.es lucid/universe Packages
Hit http://ubuntu.cica.es lucid/universe Sources
Hit http://ubuntu.cica.es lucid/multiverse Packages
Hit http://ubuntu.cica.es lucid/multiverse Sources
Hit http://ubuntu.cica.es lucid-updates/main Packages
Hit http://ubuntu.cica.es lucid-updates/restricted Packages
Hit http://ubuntu.cica.es lucid-updates/main Sources
Hit http://ubuntu.cica.es lucid-updates/restricted Sources
Hit http://ubuntu.cica.es lucid-updates/universe Packages
Hit http://ubuntu.cica.es lucid-updates/universe Sources
Hit http://ubuntu.cica.es lucid-updates/multiverse Packages
Hit http://ubuntu.cica.es lucid-updates/multiverse Sources
Hit http://ubuntu.cica.es lucid-security/main Packages
Hit http://ubuntu.cica.es lucid-security/restricted Packages
Hit http://ubuntu.cica.es lucid-security/main Sources
Hit http://ubuntu.cica.es lucid-security/restricted Sources
Hit http://ubuntu.cica.es lucid-security/universe Packages
Hit http://ubuntu.cica.es lucid-security/universe Sources
Hit http://ubuntu.cica.es lucid-security/multiverse Packages
Hit http://ubuntu.cica.es lucid-security/multiverse Sources
Reading package lists... Done
yn@yn-bs:~$ 
```My server is cica.es for now. Because i made "Select Best Server" and it found this one. By the way, the main server and others which i tried are same.

---

### Post by uRock on 2010-05-05
That actually looks normal.

```
Writing extended state information... Done
Hit http://us.archive.ubuntu.com karmic Release.gpg
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US      
Get:1 http://ppa.launchpad.net karmic Release.gpg [307B]            
Ign http://ppa.launchpad.net karmic/main Translation-en_US          
Hit http://security.ubuntu.com karmic-security Release.gpg           
Ign http://security.ubuntu.com karmic-security/main Translation-en_US
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US   
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US 
Hit http://us.archive.ubuntu.com karmic-updates Release.gpg          
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com karmic Release
Get:2 http://ppa.launchpad.net karmic Release.gpg [307B]                                  
Ign http://ppa.launchpad.net karmic/main Translation-en_US           
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US
Get:3 http://ppa.launchpad.net karmic Release [66.0kB]               
Hit http://security.ubuntu.com karmic-security Release                   
Hit http://us.archive.ubuntu.com karmic-updates Release                  
Hit http://us.archive.ubuntu.com karmic/main Packages                                         
Hit http://us.archive.ubuntu.com karmic/restricted Packages                
Hit http://us.archive.ubuntu.com karmic/main Sources               

```

---

### Post by Belki on 2010-05-05
As i can see, you have 

```
Get:2 http://ppa.launchpad.net karmic Release.gpg [307B]
```

this code but i don't have. May be my problem is related with public keys?
[FONT=monospace][/FONT]

---

### Post by uRock on 2010-05-05
That is a Karmic update on mine. Lucid doesn't get the same updates.

---

### Post by Belki on 2010-05-05
Ok, i know that karmic and lucid are not using same sources but my friend sent me his update codes and he has same gets. You can see his codes below.

```

Hit http://tr.archive.ubuntu.com lucid/restricted Packages
Hit http://tr.archive.ubuntu.com lucid/main Sources
Hit http://tr.archive.ubuntu.com lucid/restricted Sources
Hit http://tr.archive.ubuntu.com lucid/universe Packages
Hit http://tr.archive.ubuntu.com lucid/universe Sources
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://tr.archive.ubuntu.com lucid/multiverse Packages
Hit http://tr.archive.ubuntu.com lucid/multiverse Sources
Get:7 http://tr.archive.ubuntu.com lucid-updates/main Packages [24.7kB]
Get:8 http://ppa.launchpad.net lucid/main Packages [1,008B]
Get:9 http://tr.archive.ubuntu.com lucid-updates/restricted Packages [14B]
Get:10 http://tr.archive.ubuntu.com lucid-updates/main Sources [10.8kB]
Get:11 http://tr.archive.ubuntu.com lucid-updates/restricted Sources [14B]
Get:12 http://tr.archive.ubuntu.com lucid-updates/universe Packages [8,840B]
Get:13 http://tr.archive.ubuntu.com lucid-updates/universe Sources [1,959B]
Get:14 http://tr.archive.ubuntu.com lucid-updates/multiverse Packages [14B]
Get:15 http://tr.archive.ubuntu.com lucid-updates/multiverse Sources [14B]
```

The problem is i don't have any get line in my codes. At first, when i tried to update, it was taking around 3 minutes but now it is taking 10 seconds, that's why i could recognize this issue.

---

### Post by uRock on 2010-05-05
Unless update-manager ran in the background and you didn't know it, then you should have had updates today. I just ran them on my Netbook running Lucid and had a Kernel upgrade amongst other things.

---

### Post by Belki on 2010-05-05
Ok i have updates now, but how? I went to software sources, i made "select best server" and it found 58 MB update. 5 minutes ago it couldn't find. there is a problem and now I am sure of this. I can Download now but second time it won't not find anything again.

---

### Post by uRock on 2010-05-05
> **Belki said:**
> Ok i have updates now, but how? I went to software sources, i made "select best server" and it found 58 MB update. 5 minutes ago it couldn't find. there is a problem and now I am sure of this. I can Download now but second time it won't not find anything again.
I think it doesn't find them again once they have already been found. I could be wrong though. Next time I see some updates are ready, I'll run the command again to see if it shows them a second time.

---

### Post by uRock on 2010-05-05
Ok, I just booted a vbox and ran sudo apt-get update in two different terminals. The first one shows the updates, but the second one doesn't. I'd say that once they are cached, then they will not show again unless the are dropped from the cache.

---

### Post by Belki on 2010-05-05
> **uRock said:**
> Ok, I just booted a vbox and ran sudo apt-get update in two different terminals. The first one shows the updates, but the second one doesn't. I'd say that once they are cached, then they will not show again unless the are dropped from the cache.

I have always use same method since 8.10 up to now and this is the first problem. My method is always same but result is different now. Also I clean the caches, it is same.

Yesterday i changed that country of server of my sources. There was "done" instead of "hit" and refresh time was taking around 3 minutes. Ok, There was not any update but it was running fine. 10 minutes later then this, again i saw 0 B for every source and it took 10 seconds. Today it was same. When i press refresh on my update manager it was taking 10 seconds, it displays 0 B for my sources and there was not any update. I saw your post in this thread, i tried with my old server and nothing, and then i changed server again with another country, made refresh, it took 3-4 minutes and finally i could see and download the updates. Namely, I need to change update server for my every refresh if I want to be able to see updates. Is this method very exhausting, isn't it?

Can you help to fix it or making it easier way?

---

