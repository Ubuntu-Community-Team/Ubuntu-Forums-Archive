---
title: "Package Delivery &quot;massive failure&quot;"
date: 2010-09-03
forum: Installation &amp; Upgrades
---

### Post by Fazed Out on 2010-09-03
After just installing for the first time and updating, everything seemed ok.  I could install normally using package delivery.  The next day, I get the following error when launching Ubuntu Software Center, Synaptic, or anything that launches package delivery:


Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Read error - read (5: Input/output error), E:The package lists or status file could not be parsed or opened.'


It says there's a massive failure in the package delivery system, and based off of previous answers I needed to make sure a certain path existed.
 /var/lib/apt/lists/partial already exists, so I tried:
sudo dpkg --configure -a
sudo aptitude update

based off of what I found in searches.

However, at the aptitude update I get this:


loginname@computername:~$ sudo mkdir /var/lib/apt/lists/partial
[sudo] password for loginname: 
mkdir: cannot create directory `/var/lib/apt/lists/partial': File exists
loginname@computername:~$ sudo dpkg --configure -a
loginname@computername:~$ sudo aptitude update
E: Read error - read (5: Input/output error)
E: The package lists or status file could not be parsed or opened.
E: Read error - read (5: Input/output error)
E: The package lists or status file could not be parsed or opened.
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg [189B]  
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                              
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US           
Get:2 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                            
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg [189B]  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                       
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release [38.5kB]     
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/main Translation-en_US    
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release [44.7kB]               
Get:6 [http://dl.google.com](http://dl.google.com) stable Release [2,544B]                              
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                         
Get:7 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,076B]                        
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages [67.5kB]          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages [294kB]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages [14B]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources [22.0kB]    
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources [14B]       
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages [33.6kB]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources [7,304B]      
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages [1,998B]   
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources [573B]      
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages [3,252B]  
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources [106kB]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources [1,292B]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages [108kB]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources [37.0kB]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages [3,771B]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources [1,508B]
Fetched 775kB in 3s (219kB/s)                          
Reading package lists... Error!
E: Read error - read (5: Input/output error)
E: The package lists or status file could not be parsed or opened.
E: Couldn't rebuild package cache
E: Read error - read (5: Input/output error)
E: The package lists or status file could not be parsed or opened.

E: Read error - read (5: Input/output error)
E: The package lists or status file could not be parsed or opened.


After messing around with it and randomly doing things google turned up that I didn't truly understand (I'm new to ubuntu) I figured I would be doing more harm than good.  So I reinstalled Ubuntu completely, and it worked/updated until the next day when I got the exact error again.

Whenever I launch synaptic, it takes forever to load, and greys out quite often.  Then it finally turns up the error.

The etc/apt/sources.list file it seems to refer to exists, though I'm not sure how to check it for problems if that is actually the source.

Has this been encountered before?  Are there any insights to the cause I should look at, or general fixes to perform?

---

### Post by Fazed Out on 2010-09-10
I suppose a different approach would be to ask if anyone knew a way to repair/create a new valid "sources.list" as that seems to be the cause of the problem.

---

### Post by plucky on 2010-09-10
> **Fazed Out said:**
> I suppose a different approach would be to ask if anyone knew a way to repair/create a new valid "sources.list" as that seems to be the cause of the problem.

To create a new sources.list go [Here](http://repogen.simplylinux.ch/).

But first make a copy of your current sources.list from a terminal ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.old
```

Also post your current sources.list so we can take a look ```
cat /etc/apt/sources.list
``` Copy and Paste to the Forum.

Good Luck

---

### Post by Fazed Out on 2010-09-18
Unfortunately that wasn't much luck.  The copy command you had listed isn't complete, but I managed to copy it after some digging.  That actually went through ok, and I made a new sources.list from the spot you linked.  It didn't change the error though.

I talked to a friend who runs Ubuntu, and he suggested trying to revert to a previous kernel using grub (since a kernel update seemed to be the time I noticed a problem).  I found that Grub was set to a 0 interval and I couldn't modify it to get time to run it on a start up.  It was blocked by the same timing out/disappearing problem as package manager.

So I gave up and reinstalled 10.04.  After installing chrome, VLC, and the restricted codecs/etc, I rebooted and found I had the same problem.

Running apt-get, any option after that hangs on "building dependency tree" at 0%.  I notice that Synaptic will freeze at building the tree as well.  I can't apt-get build-dep, check, remove, or purge.


Here's my sources.list currently:
```

# deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse

```

---

### Post by plucky on 2010-09-19
> So I gave up and reinstalled 10.04. After installing chrome, VLC, and the restricted codecs/etc, I rebooted and found I had the same problem.

What other repositories have you added?

Post output of ```
ls -l /etc/apt/sources.list.d
```

After you re-installed,did it download and install the updates correctly?
Did the problem occur after you added new repositories?

Disable any new repositories (in Software Sources) and then add them back in one at a time and see if one of them is causing the problem.

Good Luck

---

### Post by Fazed Out on 2010-09-20
```

total 4
-rw-r--r-- 1 root root 176 2010-09-18 20:21 google-chrome.list

```

is the result.  The only things I installed this go around are the ones I mentioned, plus the add on that lets DVDs play from the DVD drive when encryption wouldn't otherwise allow it (as I can't use streaming netflix as-is or try to figure out a work around.)

Everything was installed via Ubuntu Software Center with the exception of chrome, which I got off google.com.  Though in the second OS install I did it all via software center.

I'll try disabling my repositories and post how it goes.  So far I've been installing the bulk of the things I need right after the OS installs so I can use this laptop as it sits.  I'd be surprised if installing these apps ISN'T the cause, honestly.

---

### Post by Fazed Out on 2010-09-25
It's fixed!  

As I went into Software Sources and disabled things and started adding them back.  I got a pop up that said my packages were out of date, and gave me the option to reload them.

I hit yes, and a few installs later it was fixed!  I can load Synaptic, install things again, no more notices or time outs.

Pretty excited about this, I can finally start customizing and finding out what Ubuntu is capable of :)

Thanks for all your help, everyone!

---

