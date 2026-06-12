---
title: "can't upgrade from 10.04 to 12.04"
date: 2013-05-27
forum: Installation &amp; Upgrades
---

### Post by livetobefree on 2013-05-27
Ok, I need some help here please.
        
        So I've tried to upgrade many times from 10.04 LTS to 12.04 LTS and I get these error messages.  I've visited the forums and tried terminal commands using "sudo" upgrade, autoclean, update & upgrade etc, and I always get the same error messages.  If anyone sees the reason why I'm being prevented from upgrading, in the follow string of terminal output messages please get back to me.  I'm not new to Ubuntu but I am not knowledgeable about programming nor do I know the ins and outs of using commands in Terminal, except for what little I've learned from forum troubleshooting.  Anyway, here goes, this is the message from when I tried to upgrade from 10.04 LTS to 12.04 LTS through synaptic=

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release)  Unable to find expected entry  partner/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox/ubuntu/lucid/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/mozillateam/firefox/ubuntu/lucid/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release](http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release)  Unable to find expected entry  partner/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release)  Unable to find expected entry  partner/binary-i386/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.


so then I tried a terminal upgrade and got this=

Error during update 

A problem occurred during the update. This is usually some sort of 
network problem, please check your network connection and retry. 

W:Failed to fetch 
[http://archive.ubuntu.com/ubuntu/dists/precise/Release](http://archive.ubuntu.com/ubuntu/dists/precise/Release) Unable to find 
expected entry 'partner/binary-i386/Packages' in Release file (Wrong 
sources.list entry or malformed file) 
, E:Some index files failed to download. They have been ignored, or 
old ones used instead. 


Restoring original system state

Aborting
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 
=== Command detached from window (Mon May 27 00:20:31 2013) ===
=== Command terminated with exit status 1 (Mon May 27 00:20:31 2013) ===



I have searched in the forums for troubleshooting methods, but nothing worked.  If anyone can please lend a hand I would really appreciate it.

---

### Post by sudo san on 2013-05-28
Perhaps the launchpad ppa for the Mozilla team may be out of date. Maybe the paths to the release files on the server are incorrect. I see you are using 32 bit Ubuntu. I would happily send you a copy of the contents of my sources.list file an see if it solves te problem.

---

### Post by grahammechanical on 2013-05-28
Ubuntu 10.04 reached End Of Life almost 20 days ago. The first thing you should do is remove that mozillateam ppa. That will most definitely cause the Update Manager to trip up. The second thing you should do is read this:

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

It is old but you might find something useful, especially the advice about doing a fresh install. A question:

Did you try to update 10.04 before you ran the Upgrade command? If so, then that is the reason for the first set of error messages. It is not possible to update 10.04 after it has reached End Of Life. The repositories have been moved.

You may try going for the Upgrade without first updating.

---

### Post by livetobefree on 2013-05-28
thanks for the reply Grahammechanical,   ok so I deleted that mozillateam ppa, I checked out that link you sent me, and yeah i did try to update before i upgraded, but i have not done anything since i posted, so I will await more advice, if you would like to share any, Ill be on here ( off and on all day, more or less) because i would to resolve this as quickly as I can since Im not receiving security updates any more.  thanks                                                                              Livetobefree(jason)

---

### Post by livetobefree on 2013-05-28
sudosan,    hey thanks for the reply, yeah Id accept any help you're willing to give me.  So if you want to send those source lists Id happily receive them, I can look up how to change them myself so I don't have to trouble you any further.  Thanks

---

### Post by livetobefree on 2013-05-28
ok so I tried to update again and got this output from terminal,  its long but here goes=


empty@empty-zen:~$ sudo apt-get update
[sudo] password for empty: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/partner Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal Release.gpg                           
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) quantal/partner Translation-en_US     
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal Release                               
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/partner Translation-en_US       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/partner Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release               
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) lucid Release.gpg                           
Ign [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg 
Ign [http://ppa.launchpad.net/fossfreedom/packagefixes/ubuntu/](http://ppa.launchpad.net/fossfreedom/packagefixes/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Ign [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) lucid-updates Release.gpg
Ign [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) lucid-security Release.gpg
Ign [http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/](http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/) lucid/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg 
Ign [http://ppa.launchpad.net/mozillateam/firefox/ubuntu/lucid/](http://ppa.launchpad.net/mozillateam/firefox/ubuntu/lucid/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg 
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                       
Ign [http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages                     
Ign [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                           
Ign [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) lucid Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) lucid-updates Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) lucid-security Release
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
  404  Not Found
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) lucid/main Packages
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) lucid/restricted Packages
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) lucid/universe Packages
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) lucid/multiverse Packages
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) lucid-updates/main Packages
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) lucid-updates/restricted Packages
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) lucid-updates/universe Packages
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) lucid-updates/multiverse Packages
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) lucid-security/main Packages
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) lucid-security/restricted Packages
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) lucid-security/universe Packages
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) lucid-security/multiverse Packages
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) lucid/main Packages
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) lucid/restricted Packages
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) lucid/universe Packages
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) lucid/multiverse Packages
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) lucid-updates/main Packages
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) lucid-updates/restricted Packages
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) lucid-updates/universe Packages
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) lucid-updates/multiverse Packages
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) lucid-security/main Packages
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) lucid-security/restricted Packages
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) lucid-security/universe Packages
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) lucid-security/multiverse Packages
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) lucid/main Packages
  404  Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) lucid/restricted Packages
  404  Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) lucid/universe Packages
  404  Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) lucid/multiverse Packages
  404  Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) lucid-updates/main Packages
  404  Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) lucid-updates/restricted Packages
  404  Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) lucid-updates/universe Packages
  404  Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) lucid-updates/multiverse Packages
  404  Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) lucid-security/main Packages
  404  Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) lucid-security/restricted Packages
  404  Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) lucid-security/universe Packages
  404  Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) lucid-security/multiverse Packages
  404  Not Found
W: There is no public key available for the following key IDs:
3B4FE6ACC0B21F32
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release)  Unable to find expected entry  partner/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release](http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release)  Unable to find expected entry  partner/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release)  Unable to find expected entry  partner/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox/ubuntu/lucid/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/mozillateam/firefox/ubuntu/lucid/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://old-releases.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz](http://old-releases.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz](http://old-releases.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz](http://old-releases.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz](http://old-releases.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz](http://old-releases.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz](http://old-releases.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz](http://old-releases.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.gz](http://old-releases.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.gz](http://old-releases.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-i386/Packages.gz](http://old-releases.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.gz](http://old-releases.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
empty@empty-zen



Does that mean anything to anyone?  if someone could help out with why I am getting these error messages I would really appreciate it!

---

### Post by livetobefree on 2013-05-28
ok I ran this 

cat /etc/apt/sources.list

and got this

empty@empty-zen:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main universe restricted multiverse

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid partner


# deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates partner universe main multiverse restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security partner universe main multiverse restricted
deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) lucid main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) lucid-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) lucid-security main restricted universe multiverse
empty@empty-zen:~$ 

I read it, but its not for me to decipher this stuff, anyone know what this means?

---

### Post by sudo san on 2013-05-29
That file tells apt where to look for your updates and programs. Infanct, that's the file I want you to open, remove everything in it and paste my repos in it. I will give my copy of the repos in te next post. Also, you **are** using 32 bit Ubuntu right?

---

### Post by sudo san on 2013-05-29
Ok, before you do this, make sure you backup all your stuff to an external device such as an external hard drive.

When you have done that, open terminal and bash in this command:
```
sudo gedit /etc/apt/sources.list
```

From there, delete all content of that file and replace it with this:
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to# newer versions of the distribution.
deb http://ubuntu.datahop.net/ubuntu/ precise main restricted
deb-src http://ubuntu.datahop.net/ubuntu/ precise main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://ubuntu.datahop.net/ubuntu/ precise-updates main restricted
deb-src http://ubuntu.datahop.net/ubuntu/ precise-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ubuntu.datahop.net/ubuntu/ precise universe
deb-src http://ubuntu.datahop.net/ubuntu/ precise universe
deb http://ubuntu.datahop.net/ubuntu/ precise-updates universe
deb-src http://ubuntu.datahop.net/ubuntu/ precise-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ubuntu.datahop.net/ubuntu/ precise multiverse
deb-src http://ubuntu.datahop.net/ubuntu/ precise multiverse
deb http://ubuntu.datahop.net/ubuntu/ precise-updates multiverse
deb-src http://ubuntu.datahop.net/ubuntu/ precise-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ubuntu.datahop.net/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://ubuntu.datahop.net/ubuntu/ precise-backports main restricted universe multiverse


deb http://ubuntu.datahop.net/ubuntu/ precise-security main restricted
deb-src http://ubuntu.datahop.net/ubuntu/ precise-security main restricted
deb http://ubuntu.datahop.net/ubuntu/ precise-security universe
deb-src http://ubuntu.datahop.net/ubuntu/ precise-security universe
deb http://ubuntu.datahop.net/ubuntu/ precise-security multiverse
deb-src http://ubuntu.datahop.net/ubuntu/ precise-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner


## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
```

Then save and close.

As you now have the correct repositories, you can then upgrade to the new version but it might take a while:
```
sudo apt-get update
sudo apt-get dist-upgrade -y
sudo dpkg --configure -a
sudo update-grub
```

The last two commands are just to ensure that no packages are left un-configured  and that grub is ready to boot into the new kernel. After that you can of course reboot.
```
sudo reboot
```  :o

After you reboot, you will want to change your download server as I am in the UK and using a UK server, so open terminal and input this command:
```
software-properties-gtk
```

You will then want to select the drop-down menu and select other and in the new window, choose select best server. Choose ok and close. Done!   :)

---

