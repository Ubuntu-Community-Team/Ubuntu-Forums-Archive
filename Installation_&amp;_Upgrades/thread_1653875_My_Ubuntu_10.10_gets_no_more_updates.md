---
title: "My Ubuntu 10.10 gets no more updates"
date: 2010-12-27
forum: Installation &amp; Upgrades
---

### Post by bleriot13 on 2010-12-27
Hi,

My old Ubuntu box, now running 10.10, is getting no more updates since a few days ago.

When I say "no more updates" I mean that when I try to get these via the update manager the answer is "there is none available", not that any kind of error appears.

I think that it all began about three weeks ago; the update manager downloaded a kernel update (2.6.35-23) but it was unable to install it by some reason. In fact, my box is running 2.6.35-22 since then, although I know (I have another ubuntu 10.10 computer) that the kernel has been updated at least twice since then.

However, I was getting some updates after this problem, although these were fewer every day. I get none since two days ago.

I have made no changes concerning update sources etc. so a configuration error should not be the cause of the problem. In fact, the only administrative task I perform is to launch update manager every now and then.

My theory is that, since my kernel is frozen at version 35-22, the updates that appear recently are not valid for my box, so they can not be applied and therefore not shown in the update manager.

What should I do to get the new kernels and restablish the update process to a normal state?

Thank you very much.

BTW: Excuse my poor english; it is not my mother tongue.

---

### Post by Honzifox on 2010-12-30
I am getting this issue as well. I tried to update via the terminal with the following commands:```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get clean
```
...which updated wine for me (progress!) but not anything else. I have not had any updates in about a week or two now.

Please help!

---

### Post by Sef on 2010-12-30
Applications > Accessories > Terminal

Then type in this command 

```
sudo apt-get update && sudo apt-get upgrade -y
```

Copy and paste the results here.

---

### Post by Honzifox on 2010-12-30
```
Get:1 http://dl.google.com stable Release.gpg [197B]
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_US                                                                                    
Get:2 http://dl.google.com stable Release [1,347B]                                                                                                          
Get:3 http://dl.google.com stable/main Packages [1,076B]                                      
Hit http://ppa.launchpad.net lucid Release.gpg                                                       
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://security.ubuntu.com lucid-security Release.gpg            
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US               
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US         
Hit http://us.archive.ubuntu.com lucid Release.gpg                                         
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Hit http://ppa.launchpad.net lucid Release                           
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security Release                
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg           
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release 
Hit http://ppa.launchpad.net lucid/main Packages                                           
Hit http://us.archive.ubuntu.com lucid-updates Release               
Hit http://security.ubuntu.com lucid-security/main Packages
Hit http://us.archive.ubuntu.com lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://us.archive.ubuntu.com lucid/universe Sources
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://security.ubuntu.com lucid-security/restricted Packages
Hit http://security.ubuntu.com lucid-security/main Sources
Hit http://security.ubuntu.com lucid-security/universe Packages
Hit http://security.ubuntu.com lucid-security/universe Sources
Hit http://security.ubuntu.com lucid-security/multiverse Packages
Hit http://security.ubuntu.com lucid-security/multiverse Sources
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Fetched 2,620B in 1s (1,963B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by presence1960 on 2010-12-30
you have all lucid 10.04 repositories, I thought you were running 10.10?

---

### Post by Sef on 2010-12-31
> you have all lucid 10.04 repositories, I thought you were running 10.10?

I noticed the same thing. 

Op - go to System > About Ubuntu and what version of Ubuntu does it list.  (Note: If you are running maverick, you may get an error saying that you are running 11.04, ignore it and just post the results, including that one.)

---

### Post by Honzifox on 2010-12-31
Hmm, yes. Wow. I really dropped the ball on that one :P

Yea, I have 10.04, i'm terribly sorry for the mixup...but alas I am still not getting updates. Does it being 10.04 change anything that could be of use to me? Should I start a new thread?

Again, sorry for the fail D:

---

### Post by Sathors on 2010-12-31
I have exactly the same problem than you, no more updates since two weeks ago. Before I had nearly one update each day, and now nothing ...

---

### Post by zastomito on 2010-12-31
Same thing here. Running Lucid, stopped getting updates 5 or 6 days ago. I have Maverick installed on VirtualBox and also not getting any updates for the last few days.

---

### Post by grahammechanical on 2010-12-31
I have not had updates for a few days. It is not a problem. We only get updates when there are updates available. Before I had broadband I would run Update Manager every week or so and click check . It would often return a "there are none available" message. Now I have broadband Update Manager does a check soon after booting. If there are updates I get a message. If I do not get a message, I do not worry.

Regards

BTW: Excuse my poor English. It IS my mother tongue. Quality of communication is more important than quality of language.

PS. It is a holiday season in many parts of the world. I do not celebrate myself but I understand that many people have time off and do things other than work. Or develop Linux.

---

### Post by wangsuda on 2010-12-31
I have also noticed this. I received a small kernel update about four or five days ago (very small - 600k) and expected a full kernel update soon. Nothing has happened. Perhaps we just don;t need updates!

---

### Post by cjett on 2010-12-31
I'm having the same problem.

---

### Post by z49x2vmq on 2010-12-31
Same problem.

No update for a week.

---

### Post by Tom_AUT on 2011-01-01
Same here, unfortunately. Not a single update for about a week now. Could it be because of the Error 104 - reading from server? If yes, how do I fix that? I like my systems to be up-to-date.

```
Get:1 http://at.archive.ubuntu.com maverick Release.gpg [198B]
Ign http://at.archive.ubuntu.com/ubuntu/ maverick/main Translation-en                              
Get:2 http://at.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_GB [94.5kB]                
Hit http://extras.ubuntu.com maverick Release.gpg                                                  
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en                                  
Hit http://ppa.launchpad.net maverick Release.gpg                                                  
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_GB                               
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en                    
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en_GB                 
Hit http://security.ubuntu.com maverick-security Release.gpg                                       
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en                       
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_GB                    
Hit http://repository.glx-dock.org maverick Release.gpg                                            
Hit http://ppa.launchpad.net maverick Release                                                      
Hit http://extras.ubuntu.com maverick Release                                                      
Ign http://repository.glx-dock.org/ubuntu/ maverick/cairo-dock Translation-en                      
Ign http://repository.glx-dock.org/ubuntu/ maverick/cairo-dock Translation-en_GB                   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en                 
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_GB              
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en                 
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_GB              
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en                   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_GB                
Ign http://at.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en                        
Get:3 http://at.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_GB [91.2kB]  
Hit http://ppa.launchpad.net maverick/main amd64 Packages                                          
Hit http://repository.glx-dock.org maverick Release                                                
Hit http://extras.ubuntu.com maverick/main Sources                                                 
Hit http://security.ubuntu.com maverick-security Release                                           
Hit http://extras.ubuntu.com maverick/main amd64 Packages                                          
Ign http://at.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en                
Get:4 http://at.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_GB [2,332B]
Ign http://at.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en              
Hit http://security.ubuntu.com maverick-security/main Sources                 
Hit http://repository.glx-dock.org maverick/cairo-dock amd64 Packages
Err http://at.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_GB
  Error reading from server - read (104: Connection reset by peer)
Hit http://security.ubuntu.com maverick-security/restricted Sources
Hit http://security.ubuntu.com maverick-security/universe Sources
Hit http://security.ubuntu.com maverick-security/multiverse Sources
Hit http://security.ubuntu.com maverick-security/main amd64 Packages
Hit http://security.ubuntu.com maverick-security/restricted amd64 Packages
Hit http://security.ubuntu.com maverick-security/universe amd64 Packages
Hit http://security.ubuntu.com maverick-security/multiverse amd64 Packages
Get:5 http://at.archive.ubuntu.com maverick-updates Release.gpg [198B]
Ign http://at.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://at.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_GB
Ign http://at.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://at.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_GB
Ign http://at.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://at.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_GB
Ign http://at.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://at.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_GB
Get:6 http://at.archive.ubuntu.com maverick Release [39.8kB]
Get:7 http://at.archive.ubuntu.com maverick-updates Release [31.4kB]
Get:8 http://at.archive.ubuntu.com maverick/main Sources [829kB]
Get:9 http://at.archive.ubuntu.com maverick/main Sources [829kB]
Get:10 http://at.archive.ubuntu.com maverick/restricted Sources [4,370B]
Get:11 http://at.archive.ubuntu.com maverick/universe Sources [4,179kB]
Get:12 http://at.archive.ubuntu.com maverick/multiverse Sources [151kB]
Get:13 http://at.archive.ubuntu.com maverick/main amd64 Packages [1,491kB]
Get:14 http://at.archive.ubuntu.com maverick/main amd64 Packages [1,491kB]
Get:15 http://at.archive.ubuntu.com maverick/restricted amd64 Packages [6,002B]
Get:16 http://at.archive.ubuntu.com maverick/universe amd64 Packages [5,771kB]
Get:17 http://at.archive.ubuntu.com maverick/multiverse amd64 Packages [180kB]                     
Get:18 http://at.archive.ubuntu.com maverick-updates/main Sources [67.9kB]                         
Get:19 http://at.archive.ubuntu.com maverick-updates/restricted Sources [14B]                      
Get:20 http://at.archive.ubuntu.com maverick-updates/universe Sources [21.4kB]                     
Get:21 http://at.archive.ubuntu.com maverick-updates/multiverse Sources [1,068B]                   
Get:22 http://at.archive.ubuntu.com maverick-updates/main amd64 Packages [187kB]                   
Get:23 http://at.archive.ubuntu.com maverick-updates/restricted amd64 Packages [14B]               
Get:24 http://at.archive.ubuntu.com maverick-updates/universe amd64 Packages [69.0kB]              
Get:25 http://at.archive.ubuntu.com maverick-updates/multiverse amd64 Packages [2,382B]            
Fetched 13.2MB in 9s (1,429kB/s)                                                                   
W: Failed to fetch http://at.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en_GB.bz2  Error reading from server - read (104: Connection reset by peer)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by zastomito on 2011-01-01
Still no updates on either 10.04 or 10.10.
Installed Slackware 13.1 on VirtualBox and managed to find updates, updated without any problem.

---

### Post by Sathors on 2011-01-05
Personaly today I've had three minor updates, so it seems that everything is normal ...

I think developers were celebrating the new year !!!

---

### Post by wangsuda on 2011-01-05
Gnome reader updated today. 800 whole k! We're jamming now!

---

### Post by presence1960 on 2011-01-05
Except for errors not reading your repositories, it is normal to not get updates frequently. When there are updates you will get them. Updates are only submitted when needed. Linux is not like windows full of vulnerabilities that require massive updates.

---

### Post by Parikx on 2011-05-28
same problem here :(
I tried every thing but nothing works!

and this is wht I when I run that command:


[sudo] password for parikshit: 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg                   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/) lucid/main Translation-en 
Ign [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release.gpg                          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US       
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197B]                           
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/) maverick/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/bisigi/ppa/ubuntu/](http://ppa.launchpad.net/bisigi/ppa/ubuntu/) maverick/main Translation-en   
Ign [http://ppa.launchpad.net/bisigi/ppa/ubuntu/](http://ppa.launchpad.net/bisigi/ppa/ubuntu/) maverick/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/](http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/) maverick/main Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) ma[sudo] password for parikshit: 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg                   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/) lucid/main Translation-en 
Ign [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release.gpg                          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US       
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197B]                           
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/) maverick/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/bisigi/ppa/ubuntu/](http://ppa.launchpad.net/bisigi/ppa/ubuntu/) maverick/main Translation-en   
Ign [http://ppa.launchpad.net/bisigi/ppa/ubuntu/](http://ppa.launchpad.net/bisigi/ppa/ubuntu/) maverick/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/](http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/) maverick/main Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release.gpg                  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en  
Ign [http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/](http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/) maverick/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) maverick/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu/) maverick/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main Translation-en      
Ign [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main Translation-en_US   
Ign [http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu/) maverick/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/unity/ppa/ubuntu/](http://ppa.launchpad.net/unity/ppa/ubuntu/) maverick/main Translation-en    
Ign [http://ppa.launchpad.net/unity/ppa/ubuntu/](http://ppa.launchpad.net/unity/ppa/ubuntu/) maverick/main Translation-en_US 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main amd64 Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted amd64 Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe amd64 Packages       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main amd64 Packages                      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release                      
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse amd64 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main amd64 Packages               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main amd64 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted amd64 Packages  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe amd64 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse amd64 Packages  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse amd64 Packages
Get:3 [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages [773B]
Fetched 2,317B in 2s (920B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-video-apm xserver-xorg-video-ark xserver-xorg-video-ati
  xserver-xorg-video-chips xserver-xorg-video-cirrus xserver-xorg-video-fbdev
  xserver-xorg-video-i128 xserver-xorg-video-intel xserver-xorg-video-mach64
  xserver-xorg-video-mga xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-nv xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-tseng xserver-xorg-video-vesa xserver-xorg-video-vmware
  xserver-xorg-video-voodoo
0 upgraded, 0 newly installed, 0 to remove and 32 not upgraded.
verick/multiverse Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release.gpg                  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en  
Ign [http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/](http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/) maverick/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) maverick/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu/) maverick/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main Translation-en      
Ign [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main Translation-en_US   
Ign [http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu/) maverick/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/unity/ppa/ubuntu/](http://ppa.launchpad.net/unity/ppa/ubuntu/) maverick/main Translation-en    
Ign [http://ppa.launchpad.net/unity/ppa/ubuntu/](http://ppa.launchpad.net/unity/ppa/ubuntu/) maverick/main Translation-en_US 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main amd64 Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted amd64 Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe amd64 Packages       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main amd64 Packages                      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release                      
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse amd64 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main amd64 Packages               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main amd64 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted amd64 Packages  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe amd64 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse amd64 Packages  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse amd64 Packages
Get:3 [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages [773B]
Fetched 2,317B in 2s (920B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-video-apm xserver-xorg-video-ark xserver-xorg-video-ati
  xserver-xorg-video-chips xserver-xorg-video-cirrus xserver-xorg-video-fbdev
  xserver-xorg-video-i128 xserver-xorg-video-intel xserver-xorg-video-mach64
  xserver-xorg-video-mga xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-nv xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-tseng xserver-xorg-video-vesa xserver-xorg-video-vmware
  xserver-xorg-video-voodoo
0 upgraded, 0 newly installed, 0 to remove and 32 not upgraded.

---

