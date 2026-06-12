---
title: "resolving unmet dependencies to upgrade"
date: 2014-11-24
forum: Installation &amp; Upgrades
---

### Post by richard_frye on 2014-11-24
Trying to upgrade, keep running into this:

~$ sudo apt-get -f install
[sudo] password for richf: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  libc6: Depends: libc-bin (= 2.11.1-0ubuntu7.10) but 2.15-0ubuntu10.2 is installed
         Recommends: libc6-i686
  python-louis: Depends: liblouis0 (>= 1.7.0-2) but it is not installable
  ubuntu-minimal: Depends: libc6-i686
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

Ideas???

Thanks!

---

### Post by ibjsb4 on 2014-11-25
Sounds like a third party app hanging up.  Whats in:
```
ls /etc/apt/sources.list.d/*.list
```
and
```
cat /etc/apt/sources.list
```

---

### Post by slickymaster on 2014-11-25
> **richard_frye said:**
> Trying to upgrade, keep running into this:

~$ sudo apt-get -f install
[sudo] password for richf: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  libc6: Depends: libc-bin (= 2.11.1-0ubuntu7.10) but 2.15-0ubuntu10.2 is installed
         Recommends: libc6-i686
  python-louis: Depends: liblouis0 (>= 1.7.0-2) but it is not installable
  ubuntu-minimal: Depends: libc6-i686
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

Ideas???

Thanks!

Further to the output ibjsb4 requested, can you also provide us the output of```
lsb_release -a && uname -r
```The reason that lead me to request it is that I'm under the impression that you're trying to upgrade from 10.04 and I just want to be sure.

---

### Post by richard_frye on 2014-11-26
Thanks for suggestions...here's what happens:

                         ls /etc/apt/sources.list.d/*.list 
 /etc/apt/sources.list.d/google-chrome.list 
 /etc/apt/sources.list.d/videolan-stable-daily-lucid.list 
 

 cat /etc/apt/sources.list ~$ cat /etc/apt/sources.list 

```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted 
 # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to 
 # newer versions of the distribution. 
  
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted 
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted 
  
 ## Major bug fix updates produced after the final release of the 
 ## distribution. 
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted 
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted 
  
 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
 ## team, and may not be under a free licence. Please satisfy yourself as to 
 ## your rights to use the software. Also, please note that software in 
 ## universe WILL NOT receive any review or updates from the Ubuntu security 
 ## team. 
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe 
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe 
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe 
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe 
  
 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu  
 ## team, and may not be under a free licence. Please satisfy yourself as to  
 ## your rights to use the software. Also, please note that software in  
 ## multiverse WILL NOT receive any review or updates from the Ubuntu 
 ## security team. 
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse 
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse 
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse 
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse 
  
 ## Uncomment the following two lines to add software from the 'backports' 
 ## repository. 
 ## N.B. software from this repository may not have been tested as 
 ## extensively as that contained in the main release, although it includes 
 ## newer versions of some applications which may provide useful features. 
 ## Also, please note that software in backports WILL NOT receive any review 
 ## or updates from the Ubuntu security team. 
 # deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse 
 # deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse 
  
 ## Uncomment the following two lines to add software from Canonical's 
 ## 'partner' repository. This software is not part of Ubuntu, but is 
 ## offered by Canonical and the respective vendors as a service to Ubuntu 
 ## users. 
 # deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner 
 # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner 
  
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted 
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted 
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe 
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe 
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse 
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse 
```
  

   [COLOR=#800000]Distributor ID:    Ubuntu [/COLOR]
 [COLOR=#800000]Description:    Ubuntu 10.04.4 LTS [/COLOR]
 [COLOR=#800000]Release:    10.04 [/COLOR]
 [COLOR=#800000]Codename:    lucid [/COLOR]
 [COLOR=#800000]2.6.32-42-generic [/COLOR]

---

### Post by deadflowr on 2014-11-26
You might look into disabling the videolan-stable-daily repo for lucid.
Open the update manager, got to the bottom left corner open settings, go to Other Software, find the entry for the videolan repo, and either uncheck it or remove it.
Then close and re-run "Check" in the main update manager window.
See how that works...

---

### Post by slickymaster on 2014-11-26
> **deadflowr said:**
> You might look into disabling the videolan-stable-daily repo for lucid.
Open the update manager, got to the bottom left corner open settings, go to Other Software, find the entry for the videolan repo, and either uncheck it or remove it.
Then close and re-run "Check" in the main update manager window.
See how that works...

+1 ^^^

Also, please take in consideration that 10.04 desktop edition has reached End Of Life on May 09 - 2013, so it's highly recommendable that you upgrade to a supported release, unless you're using the server edition, which will be supported until April 2015.

Upgrade to 12.04 : [https://wiki.ubuntu.com/PrecisePango...untu_12.04_LTS](https://wiki.ubuntu.com/PrecisePango...untu_12.04_LTS)
Install 14.04 : [https://help.ubuntu.com/14.04/instal...ide/index.html](https://help.ubuntu.com/14.04/instal...ide/index.html)

For old computers with lower specifications, you may :
Read this link: [Old hardware brought back to life]("http://ubuntuforums.org/showthread.php?t=2130640")
Try Lubuntu or Xubuntu 14.04 LTS (supported until April 2017)
Try Xubuntu 12.04 LTS (supported until April 2015)
Alternative to Unity on 12.04 LTS: [Gnome Classic]("https://help.ubuntu.com/community/PreciseGnomeClassicTweaks")

---

### Post by ibjsb4 on 2014-11-26
Yep, remove or disable videolan-stable-daily, then you should be able to ..

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

And welcome to the forums :)

---

### Post by richard_frye on 2014-11-26
yes, thanks, this whole exercise is about trying to upgrade to newer (and hopefully on to newest) version...

---

### Post by richard_frye on 2014-11-26
thanks, but update manager says can't install upgrades (how I got here in the first place), and then says "[I]Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.[/I]

??

---

### Post by ibjsb4 on 2014-11-26
Do install -f as instructed.
```
sudo apt-get install -f
```
and
```
sudo apt-get update && sudo apt-get upgrade
```
Please post the errors.

---

### Post by richard_frye on 2014-11-27
Thanks, giving it a shot...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  libc6: Depends: libc-bin (= 2.11.1-0ubuntu7.10) but 2.15-0ubuntu10.2 is installed
         Recommends: libc6-i686
  python-louis: Depends: liblouis0 (>= 1.7.0-2) but it is not installable
  ubuntu-minimal: Depends: libc6-i686
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

[B]
```
$ sudo apt-get update && sudo apt-get upgrade[/B]
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198B]
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main Translation-en_US 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/multiverse Translation-en_US
Get:2 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198B]                           
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [53.0kB]             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/videolan/stable-daily/ubuntu/](http://ppa.launchpad.net/videolan/stable-daily/ubuntu/) lucid/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                         
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main Translation-en_US      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/restricted Translation-en_US  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe Translation-en_US    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/multiverse Translation-en_US
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198B]        
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/multiverse Translation-en_US
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_US       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                               
Get:5 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [194kB]             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                           
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Packages [481kB]        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
  404  Not Found
Get:8 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,188B]                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources             
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Packages [879kB]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Packages [4,620B]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [114kB]        
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [2,494B] 
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Packages [107kB]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [33.5kB]   
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Packages [2,634B]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,805B] 
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Packages [13.2kB]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [479kB]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [8,000B]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Packages [257kB]  
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [112kB]   
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Packages [15.5kB]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [8,914B]
Fetched 2,770kB in 8s (334kB/s)                                                
W: Failed to fetch [http://ppa.launchpad.net/videolan/stable-daily/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/videolan/stable-daily/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

Hmm, this looks promising, although I confess I have no idea what any of it means...  :(

---

### Post by deadflowr on 2014-11-27
You still have not removed the videolan ppa.

As I posted earlier, you do not open the update manage to run updates, but to access the software sources window by clicking on the button marked settings inside the update manager. 
After you have unchecked the videolan ppa in Other Software, then you run an update ( click on the check button in the update manager).

If for some odd reason the update manager is greying out or you are unable to open the settings window, you can also access the software sources window through the terminal, with the following command
```
software-properties-gtk
```

---

### Post by richard_frye on 2014-11-28
thanks, here's what happens:

~$ sudo apt-get install -f

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  libc6: Depends: libc-bin (= 2.11.1-0ubuntu7.10) but 2.15-0ubuntu10.2 is installed
         Recommends: libc6-i686
  python-louis: Depends: liblouis0 (>= 1.7.0-2) but it is not installable
  ubuntu-minimal: Depends: libc6-i686
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

```
richf@richf:~$ sudo apt-get update && sudo apt-get upgrade
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_US       
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                           
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main Translation-en_US        
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe Translation-en_US    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/multiverse Translation-en_US  
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198B]
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/multiverse Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/videolan/stable-daily/ubuntu/](http://ppa.launchpad.net/videolan/stable-daily/ubuntu/) lucid/main Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198B] 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main Translation-en_US 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                     
Hit [http://dl.google.com](http://dl.google.com) stable/main Packages                                  
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [194kB]             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [53.0kB]        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages              
  404  Not Found
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Packages [482kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Packages [879kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Packages [4,620B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [115kB]         
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [2,494B]  
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Packages [108kB]  
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Packages [13.2kB]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [480kB]       
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [33.5kB]   
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Packages [2,634B]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,805B] 
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [8,000B]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Packages [257kB]  
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [112kB]   
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Packages [15.5kB]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [8,914B]
Fetched 2,771kB in 9s (296kB/s)                                                
W: Failed to fetch [http://ppa.launchpad.net/videolan/stable-daily/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/videolan/stable-daily/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by ibjsb4 on 2014-11-28
Why has the videolan ppa not been removed?

Have the above commands not worked?

[COLOR=#ff0000]Edit[/COLOR]
Maybe some links on the subject would help.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=how+to+remove+ppa&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=how+to+remove+ppa&sa=Search&cof=FORID:9)

---

### Post by deadflowr on 2014-11-28
Is there a problem with removing the videolan ppa?
Or have just you not done so...
You can sudo apt-get install -f until the cows come home, but nothing will be fixed until that ppa is either removed/disabled, or you upgrade it to the version for precise.
The lucid ppa no longer exists.
What you might try is a removal then a re-apt-add, something like this
```
sudo add-apt-repository --remove ppa:videolan/stable-daily/ppa
```
then re-add it with
```
sudo add-apt-repository ppa:videolan/stable-daily
```
This will remove the entry for lucid, and then re-add the entry for precise.
After you re-add the entry, run 
```
sudo apt-get update
```
and you will no longer have the err entries, and the package list will be up-to-date, and then the broken packages will also be fixable, since the ppa vlc packages are also the ones that have been holding it back.
(The libc6 package you have installed, which the lucid ppa version of vlc wants/needs, is too old for 12.04, but the ppa is forcing the system to use it. Upgrading or removing the ppa will fix that problem)

---

### Post by richard_frye on 2014-11-29
cannot remove videolan ppa or anything else via package manager (see earlier post). 

sudo add-apt-repository --remove ppa:videolan/stable-daily/ppa
yielded this:  
 
Usage: add-apt-repository sourceline
add-apt-repository is a script for adding apt sources.list entries. 
It can be used to add any repository and also provides a shorthand 
synatax for Launchpad PPA (Personal Package Archive) repositories via
ppa:user/repository 
add-apt-repository: error: no such option: --remove


doesn't sound like it got removed...??

---

### Post by deadflowr on 2014-11-29
Something even odder is wrong with your system if add-apt-repository does not work right.
Looks like a manual move/or disable is needed.
You could try either to move the file:
```
sudo mv /etc/apt/sources.list.d/videolan-stable-daily-lucid.list /etc/apt/sources.list.d/videolan-stable-daily-lucid.list.bak
```
Which should move the file in question into a backup file
OR
Try this editing the file, which I would recommend because it is simple and works.
Open a terminal and run
```
gksu gedit /etc/apt/sources.list.d/videolan-stable-daily-lucid.list
```
It should contain a line that looks like this
```
deb http://archive.something something
```
Change it and add a # symbol to the front like so
```
# deb http://archive.something something
```
Note that the above are very generic and yours should not look exactly like them, but the entries will have a deb in front. Disable every line in the file that has a deb in front. 
Then hit save and close, then run the update command.

The # makes the system ignore the line, and when it ignores the line the updater will not keep looking for whatever it tells it to, and then the updates will bring in all the freshest package lists, which does not happen when any of the entries is repos is broken. If any entry in the update command is not found or corrupt the system simply ignores all of the new entries and reverts to the oldest good state the system has. Which is not good, because the current state has problematic packages.

---

### Post by Ubi_one_2014 on 2014-11-29
what shows:

dpkg -s libc6

dpkg -s libc-bin


what happend when you do:
apt-get remove liblouis0 [ do not press yes to confirm when there are a lot of packages involved that got removed too ]

---

### Post by richard_frye on 2014-11-30
thanks...I very much appreciate all this hand-holding.

I did your second approach (gksu gedit) and looks like it worked, but I still can't upgrade. 

richf@richf:~$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/multiverse Translation-en_US
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg    
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release
Hit [http://dl.google.com](http://dl.google.com) stable Release                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Packages               
Hit [http://dl.google.com](http://dl.google.com) stable/main Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources
Reading package lists... Done

---

### Post by deadflowr on 2014-11-30
Now that the updates are up-to-date, how does the install -f command work?

---

### Post by richard_frye on 2014-11-30
looks kinda familiar...

~$ sudo apt-get install -f

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  libc6: Depends: libc-bin (= 2.11.1-0ubuntu7.10) but 2.15-0ubuntu10.2 is installed
         Recommends: libc6-i686
  python-louis: Depends: liblouis0 (>= 1.7.0-2) but it is not installable
  ubuntu-minimal: Depends: libc6-i686
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies


dependencies:
  	 	 	 	   [TABLE]
 	 	 	 	[TR]
 		[TD="width: 29%"] 			Package
 		[/TD]
 		[TD="width: 36%"] 			Installed version
 		[/TD]
 		[TD="width: 35%"] 			Latest version
 		[/TD]
 	[/TR]
 	[TR]
 		[TD="width: 29%"] 			libc6
 		[/TD]
 		[TD="width: 36%"] 			2.11.1-Oubuntu7.10
 		[/TD]
 		[TD="width: 35%"] 			2.15-Oubuntu10.7
 		[/TD]
 	[/TR]
 	[TR]
 		[TD="width: 29%"] 			python-louis
 		[/TD]
 		[TD="width: 36%"] 			1.7.0-2
 		[/TD]
 		[TD="width: 35%"] 			2.30.-3
 		[/TD]
 	[/TR]
 	[TR]
 		[TD="width: 29%"] 			ubuntu-minimal
 		[/TD]
 		[TD="width: 36%"] 			1.20
 		[/TD]
 		[TD="width: 35%"] 			1.267.1
 		[/TD]
 	[/TR]
 [/TABLE]

---

### Post by ibjsb4 on 2014-12-01
I would try a general cleaning.  Enter one line at a time.
```
sudo -i
apt-get autoremove
mv /var/lib/apt/lists /var/lib/apt/lists.old
mkdir -p /var/lib/apt/lists/partial
apt-get clean
apt-get update
apt-get dist-upgrade
exit
```

---

### Post by richard_frye on 2014-12-01
thanks...here's the output.


```
richf@richf:~$ sudo -i
root@richf:~# apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libc6: Depends: libc-bin (= 2.11.1-0ubuntu7.10) but 2.15-0ubuntu10.2 is installed
         Recommends: libc6-i686
  python-louis: Depends: liblouis0 (>= 1.7.0-2) but it is not installable
  ubuntu-minimal: Depends: libc6-i686
E: Unmet dependencies. Try using -f.
root@richf:~# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  libc6: Depends: libc-bin (= 2.11.1-0ubuntu7.10) but 2.15-0ubuntu10.2 is installed
         Recommends: libc6-i686
  python-louis: Depends: liblouis0 (>= 1.7.0-2) but it is not installable
  ubuntu-minimal: Depends: libc6-i686
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
root@richf:~# mv /var/lib/apt/lists /var/lib/apt/lists.old
mv: cannot move `/var/lib/apt/lists' to `/var/lib/apt/lists.old/lists': Directory not empty
root@richf:~# mkdir -p /var/lib/apt/lists/partial
root@richf:~# apt-get clean
root@richf:~# apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198B]
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/multiverse Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198B]
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/multiverse Translation-en_US
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg    
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [53.0kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                           
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_US       
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [194kB]           
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Packages [482kB]        
Hit [http://dl.google.com](http://dl.google.com) stable/main Packages                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Packages [880kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Packages [13.2kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [481kB]        
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Packages [4,620B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [116kB]        
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [2,494B] 
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Packages [108kB]   
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [8,000B]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Packages [257kB]  
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [33.5kB]   
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Packages [2,634B]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [112kB]   
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,805B]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Packages [15.5kB]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [8,914B]
Fetched 2,773kB in 4s (662kB/s)                       
Reading package lists... Done
root@richf:~# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libc6: Depends: libc-bin (= 2.11.1-0ubuntu7.10) but 2.15-0ubuntu10.2 is installed
         Recommends: libc6-i686
  python-louis: Depends: liblouis0 (>= 1.7.0-2) but it is not installable
  ubuntu-minimal: Depends: libc6-i686
E: Unmet dependencies. Try using -f.
root@richf:~# exit
```

---

### Post by ibjsb4 on 2014-12-01
Something didn't go right.  Try this:
```
sudo -i
mv /var/lib/apt/lists /var/lib/apt/lists.bak
mkdir -p /var/lib/apt/lists/partial
apt-get update
apt-get -f install
```

When you upgraded from 10.04 to 12.04, it did not complete the upgrade; libc-bin, libc6-i686 and liblouis0 are Lucid 10.04 packages.

Please post the version of libc6 you have.
```
apt-cache show libc6
```

---

### Post by richard_frye on 2014-12-02
you make me really want to understand what is going on here...continuing thanks


```
root@richf:~# mv /var/lib/apt/lists /var/lib/apt/lists.bak
root@richf:~# mkdir -p /var/lib/apt/lists/partial
root@richf:~# apt-get update
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198B]
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_US       
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                             
Get:3 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,188B]                       
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg [198B]                  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/multiverse Translation-en_US
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198B]
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/multiverse Translation-en_US
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198B]
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/multiverse Translation-en_US
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release [49.6kB]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [53.0kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [194kB]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Packages [482kB]       
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Packages [1,274kB]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Packages [8,431B]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources [934kB]               
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources [5,470B]        
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Packages [4,796kB]        
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Packages [4,620B]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [116kB]        
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [2,494B] 
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Packages [108kB]   
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [33.5kB]   
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Packages [2,634B]
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,805B] 
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources [5,019kB]         
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Packages [121kB]        
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources [155kB]         
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Packages [880kB]      
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Packages [13.2kB]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [481kB]       
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [8,000B]
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Packages [257kB]  
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [112kB]   
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Packages [15.5kB]
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [8,914B]
Fetched 15.1MB in 1min 13s (207kB/s)                                           
Reading package lists... Done
root@richf:~# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  libc6: Depends: libc-bin (= 2.11.1-0ubuntu7.10) but 2.15-0ubuntu10.2 is installed
         Recommends: libc6-i686
  python-louis: Depends: liblouis0 (>= 1.7.0-2) but it is not installable
  ubuntu-minimal: Depends: libc6-i686
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
```


```
root@richf:~# apt-cache show libc6
Package: libc6
Priority: required
Section: libs
Installed-Size: 9130
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: GNU Libc Maintainers <debian-glibc@lists.debian.org>
Architecture: i386
Source: eglibc
Version: 2.15-0ubuntu10.7
Replaces: belocs-locales-bin, libc6-i386
Provides: glibc-2.13-1, libc6-i686
Depends: libc-bin (= 2.15-0ubuntu10.7), libgcc1, tzdata
Suggests: glibc-doc, debconf | debconf-2.0, locales
Conflicts: belocs-locales-bin, libc6-i686, prelink (<< 0.0.20090925), tzdata (<< 2007k-1), tzdata-etch
Breaks: libhwloc0, liblouis0 (<< 2.3.0-2), liblouisxml1 (<< 2.4.0-2), nscd (<< 2.15)
Filename: pool/main/e/eglibc/libc6_2.15-0ubuntu10.7_i386.deb
Size: 3942080
MD5sum: bef2e789c374232cecf48f2ad11c30f3
SHA1: 3a7e3be6d46a295e0c871cb25e244346bd79a428
SHA256: 4df634c34d85d024e7c07063891d3d67c840eb6e3ea5e4cdff8e99a4b037352b
Description: Embedded GNU C Library: Shared libraries
Multi-Arch: same
Homepage: [http://www.eglibc.org](http://www.eglibc.org)
Description-md5: 5089b4da6684d7432ab618fb5b79cec5
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu
Supported: 5y
Task: minimal

Package: libc6
Priority: required
Section: libs
Installed-Size: 9105
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: GNU Libc Maintainers <debian-glibc@lists.debian.org>
Architecture: i386
Source: eglibc
Version: 2.15-0ubuntu10
Replaces: belocs-locales-bin, libc6-i386
Provides: glibc-2.13-1, libc6-i686
Depends: libc-bin (= 2.15-0ubuntu10), libgcc1, tzdata
Suggests: glibc-doc, debconf | debconf-2.0, locales
Conflicts: belocs-locales-bin, libc6-i686, prelink (<< 0.0.20090925), tzdata (<< 2007k-1), tzdata-etch
Breaks: libhwloc0, liblouis0 (<< 2.3.0-2), liblouisxml1 (<< 2.4.0-2), nscd (<< 2.15)
Filename: pool/main/e/eglibc/libc6_2.15-0ubuntu10_i386.deb
Size: 3788146
MD5sum: 941333dcbfcc262636b89e6e387ebe18
SHA1: 23b7f10515fc8952646b12d15392a9885a55d5c1
SHA256: 051fa85e11b0aaf4ad3fd579bfb1c5f94870b7a2cf93aa518e6f4c10a6232fa2
Description: Embedded GNU C Library: Shared libraries
Multi-Arch: same
Homepage: [http://www.eglibc.org](http://www.eglibc.org)
Description-md5: 5089b4da6684d7432ab618fb5b79cec5
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu
Supported: 5y
Task: minimal

Package: libc6
Status: install ok installed
Priority: required
Section: libs
Installed-Size: 9368
Maintainer: Ubuntu Core developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: eglibc
Version: 2.11.1-0ubuntu7.10
Replaces: belocs-locales-bin
Provides: glibc-2.10-1
Depends: libc-bin (= 2.11.1-0ubuntu7.10), debconf (>= 0.5) | debconf-2.0, libgcc1, tzdata, findutils (>= 4.4.0-2ubuntu2)
Recommends: libc6-i686
Suggests: glibc-doc, locales
Breaks: nscd (<< 2.9)
Conflicts: belocs-locales-bin, tzdata (<< 2007k-1), tzdata-etch
Conffiles:
 /etc/ld.so.conf.d/i486-linux-gnu.conf 36f09aeeab18f6af453d0a1db0a0942c
Description: Embedded GNU C Library: Shared libraries
 Contains the standard libraries that are used by nearly all programs on
 the system. This package includes shared versions of the standard C library
 and the standard math library, as well as many others.
Homepage: [http://www.eglibc.org](http://www.eglibc.org)
Original-Maintainer: GNU Libc Maintainers <debian-glibc@lists.debian.org>
```

---

### Post by ibjsb4 on 2014-12-02
You have the latest Precise libc6 v2.15 available, but Lucid v2.11 is trying to install.

Makes me think Trusty package or configure files are still present.  Open your file manager and go to the 'FileSystem' and do a search for 'vlc'.  See if there could be any leftover files causing this.

An obvious answer would be to remove or reinstall package(s), but we are dealing with system files.  This could go well or it could trash your system.  You have backup, right?

Perhaps you should consider a fresh install of 14.04.  This is your goal.  Which may or may not work well on your equipment (cpu, ram, graphics).  Post your specs if interested.

Whats your thoughts?

ps:  please use code tags :)

---

### Post by richard_frye on 2014-12-02
search on' vlc' yields no files

yes, skipping to fresh install 14.04 would be fine if compatible with my old machine:

Intel(R) Pentium(R) Dual  CPU  E2200  @ 2.20GHz
cpu MHz        : 1200.000
cache size    : 1024 KB
MemTotal:        2051012 kB
MemFree:          715420 kB

Could also use a reference on backup if going this route...!

thanks!

---

### Post by ibjsb4 on 2014-12-02
> yes, skipping to fresh install 14.04 would be fine if compatible with my old machine:
There is the unity (desktop) test.
```
/usr/lib/nux/unity_support_test -p
```
If Unity runs slow you can install a alternate desktop (Flashback).

> Could also use a reference on backup if going this route...!
You need to backup your personal files.  Creating a data partition would allow you to backup your personal files to a separate part of your HDD, space permitting.
Please post:
```
sudo fdisk -l
```
and
```
df -h
```
What kind of graphics do you have:
```
lspci | grep VGA
```

---

### Post by richard_frye on 2014-12-07
step one yeilds:

 /usr/lib/nux/unity_support_test -p
bash: /usr/lib/nux/unity_support_test: No such file or directory

Meaning...??

---

### Post by mörgæs on 2014-12-07
Seems like the file was not there, maybe because it first appeared in a later version.
Anyway, the test is not that important. I have installed Ubuntu 14.04.1 on computers where some of its questions are answered 'no'. It is not fast, but it works.

The important thing is the output from the VGA command.

---

### Post by richard_frye on 2014-12-09
*The important thing is the output from the VGA command.*

~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)

thx

---

### Post by mörgæs on 2014-12-09
Then I think you will be more satisfied with X/Lubuntu 14.04.1 or 14.10.

---

### Post by richard_frye on 2014-12-11
> **mörgæs said:**
> Then I think you will be more satisfied with X/Lubuntu 14.04.1 or 14.10.

Sounds good to me. In browsing around on the idea, I found [this ]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu")which suggested, "If you’re not sure about installing Lubuntu, you can try it out [without affecting]("http://en.wikipedia.org/wiki/Live_CD") your current installed system.
Hint:  With the default CD, you can boot your computer with Lubuntu to [back-up your data]("http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/")!

That seems an appealing approach for a "know just enough to be dangerous" user like me...

Your thoughts? And, as always, I very much appreciate your generous help with this! :?

---

### Post by mörgæs on 2014-12-12
Thanks. 
Yes, a back up from a live session is a good idea.

---

### Post by richard_frye on 2014-12-21
okay, after spending a week pretending I could figure out how to a) backup system, and then b) upgrade system to 14.10, I have to admit I keep running into roadblocks. All I have to show for it is a sense that I need to do two things: 1) back up existing 10.04, and then install Lubuntu or Xubuntu 14.04 or `14.10. 

I could describe my epic and frustrating journey, but suffice it to say many options are not open because of the issues with my 10.04 system. I have a USB download of Clonezilla (though not at all sure which version is appropriate, and am now stuck on how to proceed with steps a and b above. 

??

---

### Post by mörgæs on 2014-12-21
One thing at a time. Are you able to do a live boot using any version of Buntu?

---

### Post by richard_frye on 2014-12-22
I have successfully put Clonezilla on a USB, boot and backup process initiates, but stops because not enough space available in intended destination, which is another 2 gb USB. 

So how much space do I need in the destination partition, and if on USB, how should it be formatted? If too much for a 2gb USB, can I partition the hard drive  on the same machine (18 gb in use, 225 gb free) I want to upgrade to 14.10 to hold the backup of 10.04? 

Or other suggestion?

Thanks!

---

### Post by mörgæs on 2014-12-22
I recommend booting with a standard Lubuntu in a live boot. No need for Clonezilla.

From the live boot you can shrink the existing partition(s), create an empty partition and move your /home here. 

Post again when you are sure that you have everything of value in the new partition and have checked that files are readable.

---

### Post by richard_frye on 2014-12-25
okay, thanks long learning curve but have successfully partitioned and installed lubuntu 14.10, slowly learning where things are. 

Ubuntu 10.04 is still functioning (in it now), and all my files seem intact along with it. 

Now it's a matter of getting Lubuntu desktop set up. Have not worked with partitions before. When you say "create an empty partition and move your /home here," is **[this]("http://www.maketecheasier.com/move-home-folder-ubuntu/")** the process to follow? 

Thanks again for your help with this!

---

### Post by mörgæs on 2014-12-25
Are you saying that you have Ubuntu 10.04 and Lubuntu 14.10 in a dual boot?

---

### Post by MAFoElffen on 2014-12-26
By the sources list and system info you posted, your system was installed as 8.04 LTS Hardy, so far it's release is upgraded to 10.04 LTS Lucid... and your sources list is already now pointed to the newer 12.04 LTS Precise repos... 

Since 10.04 is EOL, the 10.04 Lucid repos are now at digital ocean. So if the sources list was still pointed to the old ones and you had tried to do an update/upgrade, it would have broken the apt cache (then). Correcting that for 10.04, you would have had to change your sources list to the new place for the old repo's which is at digitalocean... 

The 12.04 Precise repo's are still at Ubuntu main. The software update may be broke because you don't have the right version of the update manager yet. (with the conflicting sourcelist already done...) 

On testing new dev version repo's, we just switch the pointers in the sources list to the new repos, then update/upgrade on those new repo's... like they are trying to describe to you above. (So have you tried the above commandline in a terminal yet?)

*** If I get a broken pipe on those new repo's... (which the error message is the same you are now getting.) Then the first thing I suspect... is that there is a typo in the sources list file. Try this one:
```

#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################


###### Ubuntu Main Repos
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse 


###### Ubuntu Update Repos
deb http://us.archive.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse 


###### Ubuntu Extras Repo
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main

```
Or generate your own at:
[http://repogen.simplylinux.ch/#](http://repogen.simplylinux.ch/#)

If that does not work, you might try:
```

sudo do-release-upgrade

```
Which first downloads and upgrades the update manager... which may fix your between version conflicts that you are experiencing...Just a thought.

---

### Post by richard_frye on 2014-12-31
yes, if "dual boot" means can I choose which one to boot when I turn on the machine, yes.

---

### Post by MAFoElffen on 2015-01-01
Bump. I don't see this resovled,. Curious where this is now and what it is doing.

(I didn't respond yesterday... As I was a bit confused by who that last post was directed to.)

---

### Post by schragge on 2015-01-01
As I understand the situation (@OP: please correct me if I'm wrong):

 Instead of going the recommended path for distro upgrade from lucid to precise through upgrade-manager/do-release-upgrade, the OP just edited */etc/apt/sources.lists* and made it pointing to precise repositories. After the upgrade got stuck at some point, the OP managed to free some place on disk and install Lubuntu 14.10 in dual-boot with Ubuntu 10.04 (interspersed with some packages from Ubuntu 12.04).

Alternative explanation: the OP *did* try to upgrade the system through *do-release-upgrade*, but the upgrade process either went wrong early on or was interrupted leaving the system mostly lucid with some components from precise.

Currently, there's an old install of Ubuntu 10.04 with sources pointing to Ubuntu 12.04 plus a fresh install of Lubuntu 14.10.
 
 If the OP has already migrated his settings and personal files in /home to the new install, and satisfied with it, he can just ditch the old 10.04 install and use that place for backups, whatever.

Otherwise, the only sane thing to do is
```
sudo do-release-upgrade
``` on the old installation as **MAFoElffen** suggests above. Before that, I'd revert *sources.list* to point back at lucid repositories (they are still available at *archive.ubuntu.com* till April this year), and purged anything installed from /etc/sources.list.d/*.list, if needed, forcibly, with
```
dpkg --force-all --purge <package_name>
```
As there appear to be only two third-part repositories, and the OP said vlc is not installed, that leaves only google-chrome-{stable,beta,unstable} to be purged.

---

### Post by richard_frye on 2015-01-01
Okay, I have no idea what any of that means. To review: Been running on 10.04 for couple of years, upgraded from 8.04. Couple of months ago tried to upgrade, couldn't because of unmet dependencies. Started this thread, and tried numerous ways to resolve the unmet dependencies, with no luck. It was suggested to do a new install of Lubuntu 14.xx to bypass. After some discussion on this thread and a lot of exploration, I managed to partition and install Lubuntu 14.10. 

At the moment I am indeed trying *"migrate settings and personal files in /home to the new install" *without screwing anything up. I have really appreciated all the help here; hopefully this last piece will complete the new install.

---

### Post by mörgæs on 2015-01-02
Don't migrate settings, just do the changes in the new system.

Copying personal files from the old to the new /home should be easy. You might have to add extra reading rights in the old /home, though.

Don't move the entire /home, only select files and directories one by one.

---

### Post by richard_frye on 2015-01-11
Many thanks to all of you who have patiently walked me through this process over the last many weeks...I appreciate your individual dedication as well as the appealing alternative that Ununtu offers, even to us old-timers that need to be spoon-fed. 

Having been successfully steered through challenging upgrade process, I think it's time to say "Thanks!" and mark this case "closed." No doubt there will be lots of additional questions down the road. For now, thanks again for all your help, all very much appreciated!

Rich

---

### Post by mörgæs on 2015-01-11
You're welcome. What was the solution, a clean install of 14.04?  

> **richard_frye said:**
> ...and mark this case "closed." 

Please see the Thread Tools menu.

---

