---
title: "Where is Firefox Installed please?"
date: 2006-07-26
forum: Installation &amp; Upgrades
---

### Post by Julian David Pitt on 2006-07-26
I am trying to install the flashplayer plugin as it does not seem to work and says it is not installed. When I run the downloaded tarball it asks me for the the default directory and suggests usr/lib/mozilla, if I input this it still seems to not be installed and does not work. Your help would be appreciated. 
Cheers

---

### Post by CompShrink on 2006-07-26
Better than download it and installing manually, you should install everything from Synaptic (System > Administration > Synaptic Package Manager) and the apt-get command in the terminal.

Make sure you have an appropriate sources.list, which includes universe.
open a terminal and first do:
```
sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list
```

Then replace all the text with:

> ## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free                                               
                                                                                                                                          
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

Now you can just install the official Ubuntu Flash plugin:

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by Julian David Pitt on 2006-07-26
Hi Compshrink
Many thanks for the advice mate that worked a treat and no mistake. I am learning but slowly. Is that sources list the most up to date as I could not install flash from the repository list created when I ran automatix. Thanks again.

---

### Post by Julian David Pitt on 2006-07-28
> **Julian David Pitt said:**
> Hi Compshrink
Many thanks for the advice mate that worked a treat and no mistake. Thanks again.

Oops spoke too soon. Next time I visited a flash site I saw a page with just a placeholder where a flash video should have been showing. What am I doing wrong as the install seemmed to go ok. Cheers

---

### Post by CompShrink on 2006-07-30
What site? Unfortunately, Macromedia, the company that makes Flash, has only released version 7 on Linux, but version 8 is available for Windows and Mac. 

So, it might be that the site you were on needs version 8. You can get Firefox working through WINE (windows emulation, kind of) if you really need to use flash version 8. Sad I know, hopefully version 9 which is already in beta will make it to linux, but looking doubtful.

Let me know the site and I'll tell you if it's version 8, or if you have a problem.

---

### Post by wililupy on 2008-04-25
The installer for Flash 9 doesn't work properly. If you extract the tar ball then run:

sudo cp ~home/Desktop/install_flash_player_9_linux/libflashplayer.so /usr/lib/xulrunner-addons/plugins

That is assuming you extracted the tarball to your desktop. Then open your browser and your good to go.

---

