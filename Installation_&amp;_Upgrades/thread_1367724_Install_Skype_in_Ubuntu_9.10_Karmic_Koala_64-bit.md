---
title: "Install Skype in Ubuntu 9.10 Karmic Koala 64-bit?"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by joelzehring on 2009-12-29
I followed both sets of instructions at this blog:

[http://blog.dipinkrishna.info/2009/08/how-to-install-skype-on-ubuntu-910.html#](http://blog.dipinkrishna.info/2009/08/how-to-install-skype-on-ubuntu-910.html#)

Neither resulted in a successful install of Skype.

Any advice?

---

### Post by lrcaballero on 2009-12-29
Install it via Applications/Ubuntu Software Center and then go to Applications/Accessories/ Skype and you are all done....Sometimes you have to restart you computer....

Good Luck

Luis

---

### Post by uplink3r on 2009-12-29
It's working fine for me (64-bit).  I ran it last night, didn't explicitly update skype, but I assume it was updated with the upgrade from 9.04 to 9.10.  My friend DID have trouble seeing me, but I think that was a problem on her end.

What exactly is your problem?

EDIT: I installed from repositories, obviously.  Do what the dude above me says.

---

### Post by taurus on 2009-12-29
What was the error message?  Can't really help you much if you don't include which command you ran and the error message when you ran that command.

---

### Post by joelzehring on 2009-12-29
> **lrcaballero said:**
> Install it via Applications/Ubuntu Software Center and then go to Applications/Accessories/ Skype and you are all done....Sometimes you have to restart you computer....

Good Luck

Luis

A little background:

Ubuntu Software Center search shows no sign of Skype. It just doesn't show up, even when I scroll through the complete list of apps.

Ubuntu Tweak Application tab shows Skype under its list of Third-Party Sources, but adding the repo and refreshing results in a 404 Error.

Which brings me to the blog post. After adding a source, the following command is prescribed to add a medibuntu source list to my systems sources, but entering it in the terminal results in a 404 Error:

[INDENT][COLOR="Red"]$ sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list[/COLOR][/INDENT]

Downloading the linked 64-bit .deb package results in this error:

[IMG]http://lh3.ggpht.com/_zL3JwrE_pLo/Szq97zcB8eI/AAAAAAAABZs/Wv9pzNk0v-I/screenshot_001.png[/IMG]

Does that provide enough info to troubleshoot the issue?

Thanks.

Joel

---

### Post by taurus on 2009-12-29
You are running **karmic**, not hardy or intrepid!  That is your problem, mixing releases.

You need to edit /etc/apt/sources.list.d/medibuntu.list and change hardy (or whatever) to karmic.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list.d/medibuntu.list
```

---

### Post by joelzehring on 2009-12-29
I'll try.

Why doesn't Skype show in the Software Center?

---

### Post by joelzehring on 2009-12-29
No Hardy in the file. All Karmic.

---

### Post by taurus on 2009-12-29
Post the outputs of these commands.

```
more /etc/apt/sources.list
ls -la /etc/apt/sources.list.d
more /etc/apt/sources.list.d/medibuntu.list
```

---

### Post by joelzehring on 2009-12-29
joelzehring@joel-msinotebook:~$ more /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main
 restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted univ
erse multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted 
universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb [http://ppa.launchpad.net/do-core/ppa/ubuntu](http://ppa.launchpad.net/do-core/ppa/ubuntu) jaunty main
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free

joelzehring@joel-msinotebook:~$ ls -la /etc/apt/sources.list.d
total 76
drwxr-xr-x 2 root root 4096 2009-12-29 20:13 .
drwxr-xr-x 5 root root 4096 2009-12-29 20:21 ..
-rw-r--r-- 1 root root  107 2009-12-29 20:06 avant-window-navigator.list
-rw-r--r-- 1 root root  107 2009-12-29 20:06 avant-window-navigator.list.save
-rw-r--r-- 1 root root   48 2009-12-29 20:06 google-chrome.list
-rw-r--r-- 1 root root   48 2009-12-29 20:06 google-chrome.list.save
-rw-r--r-- 1 root root  272 2009-05-01 10:26 medibuntu.list
-rw-r--r-- 1 root root  272 2009-05-01 10:26 medibuntu.list~
-rw-r--r-- 1 root root   69 2009-12-29 20:06 mplayer.list
-rw-r--r-- 1 root root   69 2009-12-29 20:06 mplayer.list.save
-rw-r--r-- 1 root root   95 2009-12-29 20:06 openshot.list
-rw-r--r-- 1 root root   95 2009-12-29 20:06 openshot.list.save
-rw-r--r-- 1 root root   73 2009-12-29 20:06 pdfmod.list
-rw-r--r-- 1 root root   73 2009-12-29 20:06 pdfmod.list.save
-rw-r--r-- 1 root root    0 2009-12-29 20:02 skype.list
-rw-r--r-- 1 root root   72 2009-12-29 20:02 skype.list.save
-rw-r--r-- 1 root root   71 2009-12-29 20:06 smplayer.list
-rw-r--r-- 1 root root   71 2009-12-29 20:06 smplayer.list.save
-rw-r--r-- 1 root root   68 2009-12-29 20:06 xbmc.list
-rw-r--r-- 1 root root   68 2009-12-29 20:06 xbmc.list.save

joelzehring@joel-msinotebook:~$ more /etc/apt/sources.list.d/medibuntu.list
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free #Medibuntu - Ubuntu 9.10
 "karmic koala"
#deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free #Medibuntu (source)
 - Ubuntu 9.10 "karmic koala"

---

### Post by joelzehring on 2009-12-29
Incidentally, I tried to manually install the Medibuntu package from this URL:

[http://packages.medibuntu.org/karmic/skype.html](http://packages.medibuntu.org/karmic/skype.html)

I got this error:

[IMG]http://lh4.ggpht.com/_zL3JwrE_pLo/SzrN78tah9I/AAAAAAAABZ4/K-vQ18LHjc4/screenshot_002.png[/IMG]

---

### Post by taurus on 2009-12-29
> **joelzehring said:**
> joelzehring@joel-msinotebook:~$ more /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main
 restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted univ
erse multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted 
universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb [http://ppa.launchpad.net/do-core/ppa/ubuntu](http://ppa.launchpad.net/do-core/ppa/ubuntu) **[COLOR="Red"]jaunty[/COLOR]** main
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free

joelzehring@joel-msinotebook:~$ ls -la /etc/apt/sources.list.d
total 76
drwxr-xr-x 2 root root 4096 2009-12-29 20:13 .
drwxr-xr-x 5 root root 4096 2009-12-29 20:21 ..
-rw-r--r-- 1 root root  107 2009-12-29 20:06 avant-window-navigator.list
-rw-r--r-- 1 root root  107 2009-12-29 20:06 avant-window-navigator.list.save
-rw-r--r-- 1 root root   48 2009-12-29 20:06 google-chrome.list
-rw-r--r-- 1 root root   48 2009-12-29 20:06 google-chrome.list.save
-rw-r--r-- 1 root root  272 2009-05-01 10:26 medibuntu.list
-rw-r--r-- 1 root root  272 2009-05-01 10:26 medibuntu.list~
-rw-r--r-- 1 root root   69 2009-12-29 20:06 mplayer.list
-rw-r--r-- 1 root root   69 2009-12-29 20:06 mplayer.list.save
-rw-r--r-- 1 root root   95 2009-12-29 20:06 openshot.list
-rw-r--r-- 1 root root   95 2009-12-29 20:06 openshot.list.save
-rw-r--r-- 1 root root   73 2009-12-29 20:06 pdfmod.list
-rw-r--r-- 1 root root   73 2009-12-29 20:06 pdfmod.list.save
-rw-r--r-- 1 root root    0 2009-12-29 20:02 skype.list
-rw-r--r-- 1 root root   72 2009-12-29 20:02 skype.list.save
-rw-r--r-- 1 root root   71 2009-12-29 20:06 smplayer.list
-rw-r--r-- 1 root root   71 2009-12-29 20:06 smplayer.list.save
-rw-r--r-- 1 root root   68 2009-12-29 20:06 xbmc.list
-rw-r--r-- 1 root root   68 2009-12-29 20:06 xbmc.list.save

joelzehring@joel-msinotebook:~$ more /etc/apt/sources.list.d/medibuntu.list
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free #Medibuntu - Ubuntu 9.10
 "karmic koala"
#deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free #Medibuntu (source)
 - Ubuntu 9.10 "karmic koala"

A couple of things.

1.  Change the jaunty in /etc/apt/sources.list to karmic because it is not a good idea to mix repos in /etc/apt/sources.list.

2.  Look in /etc/apt/sources.list.d/skype.list to see which release you have in there.  Bet it says _intrepid_.  Change it to karmic if it says anything else in there.

---

### Post by joelzehring on 2009-12-29
1. Change the jaunty in /etc/apt/sources.list to karmic because it is not a good idea to mix repos in /etc/apt/sources.list.

It says jaunty in a ppa for do, and that's it. I change it, but can't save the file as it is Read-Only. How do I change this permission?

2. Look in /etc/apt/sources.list.d/skype.list to see which release you have in there. Bet it says intrepid. Change it to karmic if it says anything else in there.

This file is empty. /etc/apt/sources.list.d/skype.list.save contains this string:

[COLOR="Red"]deb [http://download.skype.com/linux/repos/debian](http://download.skype.com/linux/repos/debian) stable non-free[/COLOR]

---

### Post by taurus on 2009-12-29
What are the outputs of these two commands?

```
sudo apt-get update
sudo apt-get install skype
```

To edit /etc/apt/sources.list, run

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by joelzehring on 2009-12-29
joelzehring@joel-msinotebook:~$ sudo apt-get update
[sudo] password for joelzehring: 
Sorry, try again.
[sudo] password for joelzehring: 
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                           
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [2,540B]                             
Get:3 [http://dl.google.com](http://dl.google.com) stable/main Packages [873B]                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US                 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg                           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Translation-en_US                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Translation-en_US            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release                                
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release                        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Fetched 3,602B in 6s (531B/s)                                                  
Reading package lists... Done


joelzehring@joel-msinotebook:~$ sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package skype is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package skype has no installation candidate

---

### Post by taurus on 2009-12-29
Open synaptic (System -> Administration -> Synaptic) and Search for skype.

---

### Post by joelzehring on 2009-12-30
Related packages, but no Skype.

[IMG]http://lh3.ggpht.com/_zL3JwrE_pLo/Szrj91TxluI/AAAAAAAABaE/9IyhXhsdkIQ/s800/screenshot_002.png[/IMG]

---

### Post by joelzehring on 2009-12-30
Success! These forum post helped greatly:

[http://ubuntuforums.org/showthread.php?t=1366355&highlight=skype&page=2](http://ubuntuforums.org/showthread.php?t=1366355&highlight=skype&page=2)

[http://ubuntuforums.org/showthread.php?t=1352648&page=6](http://ubuntuforums.org/showthread.php?t=1352648&page=6)

I found the right packages (skype common and skype 2.1.0.47) here:

[http://packages.medibuntu.org/pool/non-free/s/skype/](http://packages.medibuntu.org/pool/non-free/s/skype/)

Should I expect any negative behavior from this solution?

---

