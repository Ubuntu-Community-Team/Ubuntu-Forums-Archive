---
title: "I can NOT upgrade Lucid to Maverick"
date: 2011-04-13
forum: Installation &amp; Upgrades
---

### Post by doctortonic on 2011-04-13
Hello! 
I installed Lucid in my laptop like this:

/sda1 - ntfs windows xp
/sda2 - /boot (ext4,350M)
/sda5 - /      (31528.59M)
/sda6 swap (3,2g)
/sda4 - ntfs windows data, music etc.

After I installed 10.04, I installed following programs:
-Chromium BSU (game)
-Chromium - Brownser
-Xchat

Then I followe EXACTLY this guide:

[https://help.ubuntu.com/community/MaverickUpgrades](https://help.ubuntu.com/community/MaverickUpgrades)
Network Upgrade for Ubuntu Desktops (Recommended)

But NO UPGRADE button appears. How Can I upgrade, without and make a fresh install?


I also tried in CLI to:

z@z-laptop:/$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.2 LTS
Release:	10.04
Codename:	lucid
z@z-laptop:/$ sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US  
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                                                        
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                                                           
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages          
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources     
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


z@z-laptop:/$ sudo do-release-upgrade -d
Checking for a new ubuntu release
No new release found

z@z-laptop:/$ cd /var/log/dist-upgrade/
z@z-laptop:/var/log/dist-upgrade$ ls
z@z-laptop:/var/log/dist-upgrade$

---

### Post by garvinrick4 on 2011-04-13
#Open a terminal and copy and paste these one at a time:
```
sudo apt-get install aptitude
```
```
sudo apt-get update && sudo aptitude upgrade
```
```
sudo sed -i 's/lucid/maverick/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude dist-upgrade 
```

---

### Post by PCNetSpec on 2011-04-13
To upgrade an LTS release to a Normal release... eg. 10.04 to 10.10....

Got to **System>Administration>Synaptic package manager**

When Synaptic opens...

Go to **Settings>Repositories>Updates** (tab)

Change -  **Show new distribution releases:**
from
**Long term support releases only**
to
**Normal releases**

click **Close**... then **Reload**

**Close synaptic.** (you MUST close synaptic)

open the Update manager (**System>Administartion>Update Manager**)

You should now have a button telling you there is a new release, and asking if you want to upgrade.

==================

or...

Hit **Alt+F2**

in the "Run Application" dialogue box, enter:
**update-manager -d**
click, **Run**

and follow the instructions.

---

### Post by coolbrook on 2011-04-13
Something appears to be wrong.  One of my systems isn't upgrading either.  Even after removing the nouveau driver  ```
sudo apt-get remove xserver-xorg-video-nouveau 
```

---

### Post by doctortonic on 2011-04-13
I started with the cli, following garvinrick4 instructions. Seem it works, now is unpacking things.

But something is wrong/wierd/wiked because I did exactly as in instruction.

Why in the grafical way there are no instruction to add maverick repors?

EDIT: ps. I have Ati card driver, I usually go with fgrlx or smthg. like that, don/t know what is novoeau

sry for typos

---

### Post by doctortonic on 2011-04-13
variant with aptitude worked! 


z@z-laptop:~$ uname -a
Linux z-laptop 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:40:58 UTC 2011 i686 GNU/Linux
z@z-laptop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.10
Release:	10.10
Codename:	maverick
z@z-laptop:~$

---

### Post by mwallette on 2011-04-22
> **garvinrick4 said:**
> #Open a terminal and copy and paste these one at a time:
```
sudo apt-get install aptitude
```
```
sudo apt-get update && sudo aptitude upgrade
```
```
sudo sed -i 's/lucid/maverick/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude dist-upgrade 
```

I was having the same problem as the O.P., only upgrading from Karmic to Lucid on a remote box (about 500 miles away...).  garvinrick4's solution worked when none of the other solutions I could find on-line did.  Many, MANY thanks!

---

