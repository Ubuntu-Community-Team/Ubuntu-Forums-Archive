---
title: "Failed installations from Ubuntu Software Center."
date: 2010-10-29
forum: Installation &amp; Upgrades
---

### Post by Ben_G_9C9 on 2010-10-29
I just upgraded to Ubuntu Desktop 10.10 and am anxious to get back all the programs that I 
collected in 10.04.

Using the Ubuntu Software Center (USC), I have tried to download and install several programs 
and have failed in all of them. Here is the order of events:

--I look-up the program.
--I select "install".
--I enter my password when prompted to do so.

--After a moment, the USC screen returns to normal without indicating that the program can not be 
installed or that there was any failure.

I haven't seen this issue anywhere else in the forum. Perhaps my USC was just installed badly. 
Is there a way to reinstall the USC or would this require an O/S re-install?

---

### Post by oldos2er on 2010-10-29
In order to see what's going on, can you run this command in a terminal and post the output here? For <package name>, choose one of the programs you're trying to install. ```
 sudo apt-get update && sudo apt-get install <package name>
```

---

### Post by Ben_G_9C9 on 2010-10-29
I tried this code with Skype. 
It did not install and here's what displayed in Terminal....

Code: 

Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release.gpg [198B]
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US       
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release.gpg                  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main i386 Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted i386 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe i386 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse i386 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main i386 Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse i386 Packages     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release.gpg                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted Sources                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main Sources                            
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg                   
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release [27.2kB]        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources/DiffIndex  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources/DiffIndex    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages/DiffIndex
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources [14B]    
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources [9,786B]       
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources [14B]    
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources [2,606B]   
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages [26.1kB] 
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages [14B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages [11.1kB]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages [14B]
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                              
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources/DiffIndex                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages/DiffIndex             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                       
Err [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                                                          
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages/DiffIndex
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages
Fetched 77.0kB in 20s (3,726B/s)
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg](http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by oldos2er on 2010-10-30
Does ```
sudo apt-key update
``` help?

If not, try a different server.

---

### Post by jonaustin on 2010-12-21
FYI - I had the same issue (the 'something wicked' error with apt-get update, etc), with 2 separate laptops, that I hadn't used for a few months, but had been working just fine before. 

Anyway saw lots of posts, but not much clear info, so hopefully this may help.

In my case the issue appears to be completely the fault of Comcast..

The fix is simple - don't use comcast's DNS.
(or possibly <insert ISP here> dns period.)

Use one of the ones from here (google's and openDNS worked fine for me):
[http://theos.in/windows-xp/free-fast-public-dns-server-list/](http://theos.in/windows-xp/free-fast-public-dns-server-list/)

All I did was replace the contents of /etc/resolv.conf with this:
nameserver 208.67.222.222

And suddenly, no more dns errors.

Notes:
* Last time I used these laptops, I was with Qwest (though no guarantee there, as I tend to use unaffiliated dns servers for privacy reasons).
  * i.e. this may occur with other ISPs as well. What partially lead me to this was someone commenting that ISPs have been manipulating DNS when it comes to high-bandwidth servers like youtube, etc. (i.e. us.archive.ubuntu.com would fit in that category, I'm sure.)
* If you don't understand resolv.conf, you probably shouldn't do it this way -- personally, I tend to use bare-metal style techniques (cli junkie) -- but most people should probably set the DNS using NetworkManager's settings.
  * If this helps you, please add a reply instructing how to fix this in networkManager.

---

