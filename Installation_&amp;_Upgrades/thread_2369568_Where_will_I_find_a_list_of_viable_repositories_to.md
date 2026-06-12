---
title: "Where will I find a list of viable repositories to add?"
date: 2017-08-24
forum: Installation &amp; Upgrades
---

### Post by mmmmna on 2017-08-24
A couple days ago I reinstalled Kubuntu 14.04 after seeing many failures of more modern Debian based distros.

I'm having problems getting stock 14.04 repos to refresh. As configured by a fresh install, the repos rarely refresh flawlessly nor quickly.
Today, almost nothing happens at all. VERY slow. So far today, 20+ minutes and finally all the repositories have refreshed. Yet I composed, fact checked, link checked and edited this post, staying in the forum all the while. My internet connection is certainly not at fault.


To help myself, I want to see if I need to change repository mirrors, and one necessary step for that is knowing what repository mirrors to select.


I see a lot of URLs talking about _how_ to add repos using muon, using synaptic, using the command line, etcetera, but I really have no ideas _what_ to add.

I Bing-ed "kubuntu official repositories". Bing, the MS search engine.

The top entry I got was: "Repositories/Kubuntu - Community Help Wiki", Sounds like a good result, so I went there.

That page shows me what I will see on a screen when adding a repo (a repo that you already know about), Early on, it offers this sentence with a link to a different page:
[quote="Repositories/Kubuntu"]You can find more information about the Repositories [here]("https://help.ubuntu.com/community/Repositories/Ubuntu")..[/quote]

So I went there. The word 'repository' does not appear on _that_ page. (Uhh, really? Link check, please!)

Anyways, the assumption always seems to be that you _already_ know the URL of the repositories, and I need to change my setup because of reloading issues when I refresh in Synaptic. Several days now.

Again, this is a fresh install of 'Kubuntu 14.04.nothing i386', installed on 2017 08 20. The md5sum of what I downloaded matches the md5sum for 'kubuntu-14.04-desktop-i386.iso', so what I have is not 14.04.1/2/3/4/5. Not yet interested in jumping away from 14.04, since I know how well this exact iso worked when it was installed last year.

As I posted a few sentences above, I already have links showing me the procedure.

**Where do I find a list of appropriate** (i.e. recently curated and still serving files) **repository mirrors for Kubuntu 14.04?**

---

### Post by Bucky Ball on 2017-08-24
Does Kubuntu have 'Software and Updates' or something like it? In there. First tab. Choose your mirror. 

Doubtful a fresh install of Kubuntu is going to land you at a dodgy mirror, but I generally change my mirror to one that my ISP allows free uploads and downloads to and from. Cool. You might want to experiment and change to a mirror in your country. See what works best. Also, open a terminal and:
```

sudo apt autoremove
sudo apt update
sudo apt full-upgrade
```

This last command WON'T upgrade your OS to a newer release, just the software in your current release. ;)

Did any of those commands throw any errors? If so, post them here between code tags, please.

---

### Post by QIII on 2017-08-24
You may find a list of repository mirrors [here]("https://launchpad.net/ubuntu/+archivemirrors").  You don't need to look for specific Kubuntu repos.  Remember that any repo may be under heavy load from time to time, which will slow down the update process.

Also, please see my edit above and have a look at the [Ubuntu Forums Rules]("https://ubuntuforums.org/misc.php?do=showrules").  In particular:

> Attacks and derogatory terms of any kind are not welcome. This includes references to any operating systems or the companies that produce them.

---

### Post by ajgreeny on 2017-08-24
You might also like to look at the site at [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/) which will produce a sources.list file for you and allow you to choose your country and add many ppa repos as well if you wish, including some for kubuntu backports.

Save the text it produces, name it **sources.list** in your home somewhere, then rename the current **/etc/apt/sources.list** file as a backup just in case, and finally move the version in your home to /etc/apt/.

As you kept the old version as a backup you can easily restore that if necessary.

---

### Post by mmmmna on 2017-08-24
> **Bucky Ball said:**
> Doubtful a fresh install of Kubuntu is going to land you at a dodgy mirror, but I generally change my mirror to one that my ISP allows free uploads and downloads to and from. Cool. You might want to experiment and change to a mirror in your country.

The command line provides a clue: I'm hanging for several minutes at us.archive.ubuntu.com (which is in my country), then, after simply waiting, the floodgates open.
Providing what I feel is the most relevant statement:
```
Get:19 http://us.archive.ubuntu.com/ubuntu/ trusty/universe youtube-dl all 2014.02.17-1 [237 kB]
Fetched 5,835 kB in 4min 3s (24.0 kB/s)
```
Note that this long time before opening the floodgates isn't visible in what I've posted, but the cited code contains the mirror name that my command line of sudo apt-get install foo (and sudo apt install foo) will hang on for several minutes, I just wanted to provide that the time wasn't me making exaggerated statements, the fetch statement is from a sessions of 'sudo apt install youtube-dl' that I just executed at around 6:45 p.m. eastern U.S. time.

QIII: thanks for the correction.



Possibly I checked a checkbox during install which was sub-optimal, but the [http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/) remains the same server for both source and non source repos; would the source repository selections be to blame? Well, I suppose I could simply uncheck and refresh in Synaptic and try another run; the problem has been pretty consistent at 4 slows for 4 attempts. While I test my last suggestion:
> mmmmna@Kubuntu-1404-MCP61SM2MA:~$ cat /etc/apt/sources.list
#deb cdrom:[Kubuntu 14.04 LTS _Trusty Tahr_ - Release i386 (20140416.1)]/ trusty main multiverse restricted universe

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
mmmmna@Kubuntu-1404-MCP61SM2MA:~$

Will try/post sudo apt autoremove, sudo apt update, sudo apt full-upgrade if unselecting deb-src does not fix my issues.

---

### Post by mmmmna on 2017-08-24
In Synaptic, I unchecked deb-src repositories if they had us.archive.ubuntu.com in the URL, I went to a command line, refreshed and got this for several minutes (no, this is not an edit error):
```
mmmmna@Kubuntu-1404-MCP61SM2MA:~$ sudo apt update
[sudo] password for mmmmna: 
0% [Connecting to us.archive.ubuntu.com (2001:67c:1562::19)] [Connecting to sec
```It ended at sec. Yes, Konsole was wide enough, no, the line was not wrapped below.
The session would eventually get past a stall on one repo, step through some other repo URLs in quick order, but each time it chose another us.archive.ubuntu.com, it would stall, and only part of the line was printed on screen when the stall happens.

Well, maybe not _just_ us.archive.ubuntu.com. As of now, I'm getting a stall at```
100% [Connecting to security.ubuntu.com (2001:67c:1560:8001::11)]
```

And when it finally completed, I got this:```
mmmmna@Kubuntu-1404-MCP61SM2MA:~$ sudo apt update
[sudo] password for mmmmna: 
Ign http://extras.ubuntu.com trusty InRelease                                  
Get:1 http://extras.ubuntu.com trusty Release.gpg [72 B]                       
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Ign http://us.archive.ubuntu.com trusty InRelease                              
Get:2 http://us.archive.ubuntu.com trusty-updates InRelease [65.9 kB]          
Hit http://us.archive.ubuntu.com trusty-backports InRelease                    
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Get:3 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [960 kB]  
Get:4 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [16.9 kB]
Get:5 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [425 kB]
Get:6 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [14.7 kB]
Get:7 http://us.archive.ubuntu.com trusty-updates/main Translation-en [502 kB] 
Get:8 http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en [7,430 B]
Get:9 http://us.archive.ubuntu.com trusty-updates/restricted Translation-en [3,978 B]
Get:10 http://us.archive.ubuntu.com trusty-updates/universe Translation-en [228 kB]
Hit http://us.archive.ubuntu.com trusty Release                                
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages           
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages     
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages       
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages     
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en      
Hit http://us.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://us.archive.ubuntu.com trusty/main Translation-en                    
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://us.archive.ubuntu.com trusty/universe Translation-en                
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US             
Get:11 http://security.ubuntu.com trusty-security InRelease [65.9 kB]          
Get:12 http://security.ubuntu.com trusty-security/main Sources [140 kB]
Get:13 http://security.ubuntu.com trusty-security/restricted Sources [4,955 B] 
Get:14 http://security.ubuntu.com trusty-security/universe Sources [62.3 kB]   
Get:15 http://security.ubuntu.com trusty-security/multiverse Sources [3,193 B] 
Get:16 http://security.ubuntu.com trusty-security/main i386 Packages [607 kB]  
Get:17 http://security.ubuntu.com trusty-security/restricted i386 Packages [13.7 kB]
Get:18 http://security.ubuntu.com trusty-security/universe i386 Packages [184 kB]
Get:19 http://security.ubuntu.com trusty-security/multiverse i386 Packages [4,280 B]
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Hit http://security.ubuntu.com trusty-security/restricted Translation-en    
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
**Fetched 3,309 kB in 12min 3s (4,573 B/s)**
``` 3.3 megabytes in just over 12 minutes. I am using 802.11G gear which does not stall like this. I surf _DURING_ the stall, my network works fine for browsers during the stall.

As requested:
sudo apt autoremove```
mmmmna@Kubuntu-1404-MCP61SM2MA:~$ sudo apt autoremove
E: Invalid operation autoremove
mmmmna@Kubuntu-1404-MCP61SM2MA:~$
```More on this below.

sudo apt update```
mmmmna@Kubuntu-1404-MCP61SM2MA:~$ sudo apt update
0% [Connecting to us.archive.ubuntu.com (2001:67c:1562::16)] [Connecting to sec
```Stalls at us.archive.ubuntu.com

Before I did the full-upgrade, I saw that autoremove is only an option to apt-get, so:```
mmmmna@Kubuntu-1404-MCP61SM2MA:~$ sudo apt-get autoremove
[sudo] password for mmmmna: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
mmmmna@Kubuntu-1404-MCP61SM2MA:~$
```Personally, I heard that apt-get is about to be deprecated, so I'm trying to only use apt, but I understand the situation.


sudo apt full-upgrade```
mmmmna@Kubuntu-1404-MCP61SM2MA:~$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  libcgmanager0
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.                                                             
Need to get 29.4 kB of archives.                                                                                           
After this operation, 33.8 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
WARNING: The following packages cannot be authenticated!
  libcgmanager0
Install these packages without verification? [y/N] n
E: Some packages could not be authenticated
mmmmna@Kubuntu-1404-MCP61SM2MA:~$ 
```

Hmm. Maybe after discussion I might allow the unauthenticated package to upgrade.


Awaiting further directions.

---

### Post by mmmmna on 2017-08-24
Maybe I need this? [https://askubuntu.com/questions/298177/a-failed-to-fetch-error-occurs-when-apt-get-update-is-run-how-do-i-fix-this](https://askubuntu.com/questions/298177/a-failed-to-fetch-error-occurs-when-apt-get-update-is-run-how-do-i-fix-this)

---

### Post by mmmmna on 2017-08-24
```
mmmmna@Kubuntu-1404-MCP61SM2MA:~$ nslookup us.archive.ubuntu.com
Server:         127.0.1.1
Address:        127.0.1.1#53

Non-authoritative answer:
Name:   us.archive.ubuntu.com
Address: 91.189.91.26
Name:   us.archive.ubuntu.com
Address: 91.189.91.23

mmmmna@Kubuntu-1404-MCP61SM2MA:~$ 
mmmmna@Kubuntu-1404-MCP61SM2MA:~$ 
mmmmna@Kubuntu-1404-MCP61SM2MA:~$ 
mmmmna@Kubuntu-1404-MCP61SM2MA:~$ nslookup google.com
Server:         127.0.1.1
Address:        127.0.1.1#53

Non-authoritative answer:
Name:   google.com
Address: 172.217.7.14

mmmmna@Kubuntu-1404-MCP61SM2MA:~$
```

2 different addresses for us.archive.ubuntu.com. Is that optimal?

---

### Post by Bucky Ball on 2017-08-24
> **mmmmna said:**
> ```

Do you want to continue? [Y/n] y
WARNING: The following packages cannot be authenticated!
  libcgmanager0
Install these packages without verification? [y/N] n
E: Some packages could not be authenticated
mmmmna@Kubuntu-1404-MCP61SM2MA:~$ 
```

Hmm. Maybe after discussion I might allow the unauthenticated package to upgrade.

Yes. You should be hitting 'y' and continuing with the upgrade. You have tried different mirrors and still the same?

---

### Post by mmmmna on 2017-08-24
You are implying the unauthenticated package is authentic, so I will install later.

Chose Princeton for repositories, is just a few hundred miles away, fast and up to date as of 3 hours ago.

Added the Princeton repos via Synaptic, both deb and deb-src.
Opened a Konsole.
apt update still stalls at us.archive.ubuntu.com and security.ubuntu.com.
Example:```
mmmmna@Kubuntu-1404-MCP61SM2MA:~$ sudo apt update
Ign http://mirror.math.princeton.edu trusty InRelease                          
Hit http://mirror.math.princeton.edu trusty Release.gpg                        
Hit http://mirror.math.princeton.edu trusty Release                            
Hit http://mirror.math.princeton.edu trusty/main i386 Packages                 
Hit http://mirror.math.princeton.edu trusty/main Translation-en                
Ign http://mirror.math.princeton.edu trusty/main Translation-en_US             
100% [Connecting to us.archive.ubuntu.com (2001:67c:1562::16)] [Connecting to s
```

and later, the stall on security.ubuntu.com:```
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US             
100% [Connecting to security.ubuntu.com (2001:67c:1360:8001::17)]
```


Should I deactivate/unselect repositories which are not Princeton?

---

### Post by Bucky Ball on 2017-08-25
Please post your /etc/apt/sources.list file again so we can see what that now looks like.

---

### Post by mmmmna on 2017-08-25
Sources.list
```
mmmmna@Kubuntu-1404-MCP61SM2MA:~/Downloads$ 
mmmmna@Kubuntu-1404-MCP61SM2MA:~/Downloads$ cat /etc/apt/sources.list
# deb cdrom:[Kubuntu 14.04 LTS _Trusty Tahr_ - Release i386 (20140416.1)]/ trusty main multiverse restricted universe 

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
# deb http://us.archive.ubuntu.com/ubuntu/ trusty restricted main 
# deb-src http://us.archive.ubuntu.com/ubuntu/ trusty restricted main 

## Major bug fix updates produced after the final release of the
## distribution.
# deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates restricted main 
# deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates restricted main 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ trusty universe 
# deb-src http://us.archive.ubuntu.com/ubuntu/ trusty universe 
# deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe 
# deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse 
# deb-src http://us.archive.ubuntu.com/ubuntu/ trusty multiverse 
# deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse 
# deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse 

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ trusty-backports multiverse universe restricted main 
# deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-backports multiverse universe restricted main 

deb http://security.ubuntu.com/ubuntu/ trusty-security restricted main  
deb-src http://security.ubuntu.com/ubuntu/ trusty-security restricted main   
deb http://security.ubuntu.com/ubuntu/ trusty-security universe  
deb-src http://security.ubuntu.com/ubuntu/ trusty-security universe 
deb http://security.ubuntu.com/ubuntu/ trusty-security multiverse 
deb-src http://security.ubuntu.com/ubuntu/ trusty-security multiverse 

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu/ trusty partner 
# deb-src http://archive.canonical.com/ubuntu/ trusty partner 

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu/ trusty main 
deb-src http://extras.ubuntu.com/ubuntu/ trusty main 


deb-src http://mirror.math.princeton.edu/pub/ubuntu/ trusty main   
deb http://mirror.math.princeton.edu/pub/ubuntu/ trusty main    


mmmmna@Kubuntu-1404-MCP61SM2MA:~/Downloads$ 

```

Then apt update:
```
mmmmna@Kubuntu-1404-MCP61SM2MA:~$ 
mmmmna@Kubuntu-1404-MCP61SM2MA:~$ sudo apt update
[sudo] password for mmmmna: 
Ign http://mirror.math.princeton.edu trusty InRelease                          
Hit http://mirror.math.princeton.edu trusty Release.gpg                        
Hit http://mirror.math.princeton.edu trusty Release                            
Hit http://mirror.math.princeton.edu trusty/main Sources                       
Hit http://mirror.math.princeton.edu trusty/main i386 Packages                 
Hit http://mirror.math.princeton.edu trusty/main Translation-en                
Ign http://mirror.math.princeton.edu trusty/main Translation-en_US             
100% [Connecting to security.ubuntu.com (2001:67c:1562::16)] [Connecting to ext
```Still stalling on security.ubuntu.com

---

### Post by deadflowr on 2017-08-25
Once in a while you see issues like this if your connection is using ipv6.
You might see if forcing ipv4 give a better result:
You can test that with
```
sudo apt-get -o Acquire::ForceIPv4=true update
```

---

### Post by mmmmna on 2017-08-25
I hope I didn't just get a lucky update, but 3 seconds is appropriate.
```
mmmmna@Kubuntu-1404-MCP61SM2MA:~/Downloads$ 
mmmmna@Kubuntu-1404-MCP61SM2MA:~/Downloads$ sudo sudo apt-get -o Acquire::ForceIPv4=true update
Ign http://mirror.math.princeton.edu trusty InRelease
Hit http://mirror.math.princeton.edu trusty Release.gpg                        
Hit http://mirror.math.princeton.edu trusty Release                            
Get:1 http://security.ubuntu.com trusty-security InRelease [65.9 kB]  
Ign http://extras.ubuntu.com trusty InRelease                                  
Hit http://mirror.math.princeton.edu trusty/main Sources                       
Get:2 http://extras.ubuntu.com trusty Release.gpg [72 B]                       
Hit http://mirror.math.princeton.edu trusty/main i386 Packages                 
Hit http://mirror.math.princeton.edu trusty/main Translation-en                
Hit http://extras.ubuntu.com trusty Release                             
Ign http://mirror.math.princeton.edu trusty/main Translation-en_US             
Get:3 http://security.ubuntu.com trusty-security/restricted Sources [4,955 B]
Hit http://extras.ubuntu.com trusty/main Sources                               
Get:4 http://security.ubuntu.com trusty-security/main Sources [140 kB]         
Hit http://extras.ubuntu.com trusty/main i386 Packages                    
Get:5 http://security.ubuntu.com trusty-security/universe Sources [62.3 kB]    
Get:6 http://security.ubuntu.com trusty-security/multiverse Sources [3,193 B]  
Get:7 http://security.ubuntu.com trusty-security/restricted i386 Packages [13.7 kB]
Get:8 http://security.ubuntu.com trusty-security/main i386 Packages [607 kB]   
Get:9 http://security.ubuntu.com trusty-security/universe i386 Packages [184 kB]
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Get:10 http://security.ubuntu.com trusty-security/multiverse i386 Packages [4,280 B]
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en   
Hit http://security.ubuntu.com trusty-security/restricted Translation-en   
Hit http://security.ubuntu.com trusty-security/universe Translation-en     
Fetched 1,085 kB in 3s (348 kB/s)                                          
Reading package lists... Done
mmmmna@Kubuntu-1404-MCP61SM2MA:~/Downloads$ 
```

With my sources.list:```
mmmmna@Kubuntu-1404-MCP61SM2MA:~/Downloads$ cat /etc/apt/sources.list
# deb cdrom:[Kubuntu 14.04 LTS _Trusty Tahr_ - Release i386 (20140416.1)]/ trusty main multiverse restricted universe 

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
# deb http://us.archive.ubuntu.com/ubuntu/ trusty restricted main 
# deb-src http://us.archive.ubuntu.com/ubuntu/ trusty restricted main 

## Major bug fix updates produced after the final release of the
## distribution.
# deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates restricted main 
# deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates restricted main 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ trusty universe 
# deb-src http://us.archive.ubuntu.com/ubuntu/ trusty universe 
# deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe 
# deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse 
# deb-src http://us.archive.ubuntu.com/ubuntu/ trusty multiverse 
# deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse 
# deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse 

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ trusty-backports multiverse universe restricted main 
# deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-backports multiverse universe restricted main 

deb http://security.ubuntu.com/ubuntu/ trusty-security restricted main  
deb-src http://security.ubuntu.com/ubuntu/ trusty-security restricted main  
deb http://security.ubuntu.com/ubuntu/ trusty-security universe  
deb-src http://security.ubuntu.com/ubuntu/ trusty-security universe  
deb http://security.ubuntu.com/ubuntu/ trusty-security multiverse  
deb-src http://security.ubuntu.com/ubuntu/ trusty-security multiverse  

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu/ trusty partner 
# deb-src http://archive.canonical.com/ubuntu/ trusty partner 

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu/ trusty main 
deb-src http://extras.ubuntu.com/ubuntu/ trusty main 


deb-src http://mirror.math.princeton.edu/pub/ubuntu/ trusty main 
deb http://mirror.math.princeton.edu/pub/ubuntu/ trusty main 




mmmmna@Kubuntu-1404-MCP61SM2MA:~/Downloads$ 
```






Restoring sources.list to the original file:```
mmmmna@Kubuntu-1404-MCP61SM2MA:~/Downloads$ cat /etc/apt/sources.list
# deb cdrom:[Kubuntu 14.04 LTS _Trusty Tahr_ - Release i386 (20140416.1)]/ trusty main multiverse restricted universe 

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted 
# deb-src http://us.archive.ubuntu.com/ubuntu/ trusty restricted main  

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted 
# deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates restricted main  

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty universe 
# deb-src http://us.archive.ubuntu.com/ubuntu/ trusty universe  
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe 
# deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe  

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse 
# deb-src http://us.archive.ubuntu.com/ubuntu/ trusty multiverse  
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse 
# deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse  

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse 
# deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-backports multiverse universe restricted main  

deb http://security.ubuntu.com/ubuntu/ trusty-security main restricted 
deb-src http://security.ubuntu.com/ubuntu/ trusty-security main restricted 
deb http://security.ubuntu.com/ubuntu/ trusty-security universe 
deb-src http://security.ubuntu.com/ubuntu/ trusty-security universe 
deb http://security.ubuntu.com/ubuntu/ trusty-security multiverse 
deb-src http://security.ubuntu.com/ubuntu/ trusty-security multiverse 

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu/ trusty partner 
# deb-src http://archive.canonical.com/ubuntu/ trusty partner 

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu/ trusty main 
deb-src http://extras.ubuntu.com/ubuntu/ trusty main 

mmmmna@Kubuntu-1404-MCP61SM2MA:~/Downloads$
```

And another IPv4 forced update:```
mmmmna@Kubuntu-1404-MCP61SM2MA:~/Downloads$ sudo sudo apt-get -o Acquire::ForceIPv4=true update
Ign http://us.archive.ubuntu.com trusty InRelease
Get:1 http://us.archive.ubuntu.com trusty-updates InRelease [65.9 kB]          
Get:2 http://us.archive.ubuntu.com trusty-backports InRelease [65.9 kB]        
Get:3 http://us.archive.ubuntu.com trusty Release.gpg [933 B]                  
Hit http://security.ubuntu.com trusty-security InRelease                   
Get:4 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [960 kB]
Ign http://extras.ubuntu.com trusty InRelease                                  
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://security.ubuntu.com trusty-security/main Sources
Get:5 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [16.9 kB]
Get:6 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [425 kB]
Hit http://security.ubuntu.com trusty-security/restricted Sources              
Hit http://extras.ubuntu.com trusty Release                                    
Get:7 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [14.7 kB]
Hit http://security.ubuntu.com trusty-security/universe Sources                
Get:8 http://us.archive.ubuntu.com trusty-updates/main Translation-en [502 kB] 
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://security.ubuntu.com trusty-security/multiverse Sources              
Get:9 http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en [7,430 B]
Get:10 http://us.archive.ubuntu.com trusty-updates/restricted Translation-en [3,978 B]
Hit http://security.ubuntu.com trusty-security/main i386 Packages              
Get:11 http://us.archive.ubuntu.com trusty-updates/universe Translation-en [228 kB]
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages        
Get:12 http://us.archive.ubuntu.com trusty Release [58.5 kB]                   
Get:13 http://us.archive.ubuntu.com trusty-backports/main i386 Packages [13.4 kB]
Hit http://security.ubuntu.com trusty-security/universe i386 Packages          
Get:14 http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages [28 B]
Get:15 http://us.archive.ubuntu.com trusty-backports/universe i386 Packages [43.2 kB]
Get:16 http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages [1,552 B]
Get:17 http://us.archive.ubuntu.com trusty-backports/main Translation-en [7,503 B]
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages        
Get:18 http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en [1,215 B]
Get:19 http://us.archive.ubuntu.com trusty-backports/restricted Translation-en [28 B]
Get:20 http://us.archive.ubuntu.com trusty-backports/universe Translation-en [36.8 kB]
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Get:21 http://us.archive.ubuntu.com trusty/main i386 Packages [1,348 kB]       
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Get:22 http://us.archive.ubuntu.com trusty/restricted i386 Packages [13.4 kB]  
Get:23 http://us.archive.ubuntu.com trusty/universe i386 Packages [5,866 kB]   
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Get:24 http://us.archive.ubuntu.com trusty/multiverse i386 Packages [134 kB]   
Get:25 http://us.archive.ubuntu.com trusty/main Translation-en [762 kB]
Get:26 http://us.archive.ubuntu.com trusty/multiverse Translation-en [102 kB]
Get:27 http://us.archive.ubuntu.com trusty/restricted Translation-en [3,457 B]
Get:28 http://us.archive.ubuntu.com trusty/universe Translation-en [4,089 kB]
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US             
Fetched 14.8 MB in 14s (1,014 kB/s)                                            
Reading package lists... Done
mmmmna@Kubuntu-1404-MCP61SM2MA:~/Downloads$
```
14 seconds is still reasonable.
2 fast updates in a row.


Verified Network Manager settings, neither IPV4 nor IPV6 are check marked as required.
What next?

---

### Post by mmmmna on 2017-09-01
Ok, was sick for a few days, but before that, I posted that the "sudo apt-get -o Acquire::ForceIPv4=true update" works nicely, I mentioned that I undid a few changes to see if the ipv6 issues was there from the beginning and finally I asked what to do next.

What should I change in network settings to make the issue go away?

---

### Post by mmmmna on 2017-09-02
Looking into what was discovered here: [https://ubuntuforums.org/showthread.php?t=2367462&highlight=sysctl.conf](https://ubuntuforums.org/showthread.php?t=2367462&highlight=sysctl.conf)

---

### Post by mmmmna on 2017-09-02
Per [https://ubuntuforums.org/showthread.php?t=2367462&highlight=sysctl.conf](https://ubuntuforums.org/showthread.php?t=2367462&highlight=sysctl.conf)

I edited /etc/sysctl.conf

Added
```
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
```

Saved, issued```
sudo sysctl.conf -p
```at a Konsole, and then launched Synaptic. Synaptic refresh was just a few seconds, no more hangs (but I'm only on the first attempt).

---

### Post by mmmmna on 2017-09-03
Well, that didn't stay fixed.

I'm on Comcast, went to [http://test-ipv6-ct.comcast.net/](http://test-ipv6-ct.comcast.net/) and discovered these results:
```
&#65532;Your IPv4 address on the public Internet appears to be xx.xxx.xxx.xxx
Your Internet Service Provider (ISP) appears to be COMCAST-7922 - Comcast Cable Communications, LLC, US
No IPv6 address detected [more info]
When a publisher offers both IPv4 and IPv6, your browser appears to be happy to take the IPv4 site without delay.
Connections to IPv6-only sites are timing out. Any web site that is IPv6 only, will appear to be down to you.
To ensure the best Internet performance and connectivity, ask your ISP about native IPv6. [more info]
Your DNS server (possibly run by your ISP) appears to have IPv6 Internet access.
Your readiness score
0/10	for your IPv6 stability and readiness, when publishers are forced to go IPv6 only
```

And the test results were:```
How this test works: Your browser will be instructed to reach a series of URLs. The combination of successes and failures tells a story about how ready you are for when publishers start offering their web sites on IPv6.

Click to see Tests Run

Test with IPv4 DNS record
ok (0.628s) using ipv4
http://ipv4.test-ipv6-ct.comcast.net/ip/?callback=?
Fetches an object that has just an A record in DNS. This is expected to use IPv4. IPv6-only users might still reach this, if their provider has employed a NAT64/DNS64 or proxy solution.
Test with IPv6 DNS record
timeout (15.009s)
http://ipv6.test-ipv6-ct.comcast.net/ip/?callback=?
Fetches an object that has just an AAAA record in DNS. This is expected to use IPv6. Users not yet on the IPv6 Internet are likely to see this fail. As long as it fails quickly, it will be OK - for now.
Test with Dual Stack DNS record
ok (0.704s) using ipv4
http://ds.test-ipv6-ct.comcast.net/ip/?callback=?
This is the most important test. This verifies your browser can connect to a site that has both IPv4 and IPv6 records published. IPv4 only hosts should connect fine (using IPv4).
If this test fails or times out, you can expect major problems as publishers start offering their sites on IPv6.

Test for Dual Stack DNS and large packet
ok (0.604s) using ipv4
http://ds.test-ipv6-ct.comcast.net/ip/?callback=?&size=1600&fill=xxx...xxx
Validates that you can connect to a dual-stack server (like the ds test); and that you can send/receive large packets on that connection. If this test times out for any reason, it indicates trouble for World IPv6 Day.
Test IPv4 without DNS
ok (0.697s) using ipv4
http://96.119.0.221/ip/?callback=?
This will try connecting with a literal IPv4 numeric address. This should work for most people, unless they are running IPv6-only. If the first test worked, but this fails, it likely confirms your provider is using NAT64/DNS64; you'll need to only try connecting using hostnames instead of numeric IP addresses.
Test IPv6 without DNS
timeout (15.010s)
http://[2001:558:fc00:100:f816:3eff:fe2b:6488]:80/ip/?callback=?
This will try connecting with a literal IPv6 hexadecimal address. The primary purpose of this test is to separate out your connectivity on IPv6 from your ability to fetch DNS for it. A secondary purpose is to see if you have Teredo enabled; some systems may only use Teredo when an IPv6 address is in the URL.
Test IPv6 large packet
timeout (15.012s)
http://mtu1280.test-ipv6-ct.comcast.net/ip/?callback=?&size=1600&fill=xxx...xxx
Validates that IPv6 requests with large packets work. If this test times out, but other IPv6 tests work, it suggests that there may be PMTUD issues; possibly involving IP tunnels. Double check to make sure that ICMPv6 Type 2 ("Packet Too Big") messages are not filtered by your firewall.
Test if your ISP's DNS server uses IPv6
ok (0.623s) using ipv4
http://ds.v6ns.test-ipv6-ct.comcast.net/ip/?callback=?
(This is bonus credit)
This is a test of your ISP's resolver (instead of a test of your host). If this test passes, your DNS server (often run by your ISP) is capable of reaching IPV6-only DNS authoritative servers on the Internet. This is not critical (at this time) for you to reach sites via IPv6.
Find IPv4 Service Provider
ok (0.644s) using ipv4 ASN 7922
http://ipv4.test-ipv6-ct.comcast.net/ip/?callback=?&asn=1
Attempts to identify what Internet Service Provider you use for IPv4. This may be different from the marketing name you see in your local market; or may reflect a previous company name. The name shown reflects how it is known in the network operator community.
Find IPv6 Service Provider
timeout (15.006s)
http://ipv6.test-ipv6-ct.comcast.net/ip/?callback=?&asn=1
Attempts to identify what Internet Service Provider you use for IPv6. When the IPv4 name and the IPv6 name don't match, it may suggest that you're using a tunnel; or some form of third party provider for IPv6.
If the summary results indicated problems, you (or your technical support) may be able to use the information above to diagnose the issues. Each of the test urls and their results is shown on the left side. To the right you'll see a description of what that URL was designed to test.

After each test is ran. The summary page attempts to look at the results If the summary doesn't seem to make sense given the symptoms recorded above, or if you need further assistance, please feel free to contact us.


```Every IPV6 test went to timeout?

Not quite sure where to make changes. Thinking I'll peruse the cable modem configuration soon, but naivety warns me to make no changes unless someone is familiar with IPV6 configuration issues on very late model Comcast hardware (issued to us in June 2017).

---

