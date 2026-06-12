---
title: "Unable to upgrade 13.04 Ubuntu desktop"
date: 2015-02-07
forum: Installation &amp; Upgrades
---

### Post by Pratik_Mehta on 2015-02-07
Hi all,

I have seen several posts on this problem where people said they are not able to upgrade/update EOL (end of life) version, however i did not see anything specific to my version 13.04.Also none of the other version solutions i saw helped me! :(

$ [COLOR=#0000cd]cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.04
DISTRIB_CODENAME=raring
DISTRIB_DESCRIPTION="Ubuntu 13.04"[/COLOR]

On running [COLOR=#0000cd]"sudo apt-get update"[/COLOR]
or
[COLOR=#0000cd]"sudo apt-get upgrade"[/COLOR]
or
[COLOR=#0000cd]"sudo apt-get dist-upgrade"[/COLOR]

I always get [COLOR=#ff0000]*Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-11 - System error)*[/COLOR]
Since 13.04 is no longer supported, i have updated the paths in sources.list file with following command:
[COLOR=#0000cd]sudo sed -i -e 's/archive.ubuntu.com\|security.ubuntu.com/old-releases.ubuntu.com/g' /etc/apt/sources.list[/COLOR]
but still no success! :(

I also tried removing the locks with both of the below cmds:
[COLOR=#0000cd]sudo rm /var/lib/apt/lists/lock
[/COLOR][COLOR=#0000cd]sudo rm /var/cache/apt/archives/lock[/COLOR]

also restarted my machine several times...

I keep on getting above System error messages, and [COLOR=#0000cd]sudo apt-get update[/COLOR] always gets stuck at 
*[COLOR=#a52a2a]59% [Connecting to us.old-releases.ubuntu.com][/COLOR]* for more than 1hr and then it timeouts! I get some internet problem error, however fact is that i have a very good internet connection. I tried all these the whole day but in vain :(

Note that my Ubuntu had IPv6 enabled. However after all the trial failures i disabled it
[COLOR=#0000cd]$ cat /proc/sys/net/ipv6/conf/all/disable_ipv6
1[/COLOR]

However after that too, same problem persists!:(

Can someone please suggest what to do to come to latest supported version of Ubuntu?

---

### Post by Pratik_Mehta on 2015-02-07
Here are the contents of my sources.list file[COLOR=#800080]

# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com|security.ubuntu.com|archive.ubuntu.com|security.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com|security.ubuntu.com|archive.ubuntu.com|security.ubuntu.com/ubuntu/) raring main restricted
deb-src [http://us.archive.ubuntu.com|security.ubuntu.com|archive.ubuntu.com|security.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com|security.ubuntu.com|archive.ubuntu.com|security.ubuntu.com/ubuntu/) raring main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com|security.ubuntu.com|archive.ubuntu.com|security.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com|security.ubuntu.com|archive.ubuntu.com|security.ubuntu.com/ubuntu/) raring-updates main restricted
deb-src [http://us.archive.ubuntu.com|security.ubuntu.com|archive.ubuntu.com|security.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com|security.ubuntu.com|archive.ubuntu.com|security.ubuntu.com/ubuntu/) raring-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com|security.ubuntu.com|archive.ubuntu.com|security.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com|security.ubuntu.com|archive.ubuntu.com|security.ubuntu.com/ubuntu/) raring universe
deb-src [http://us.archive.ubuntu.com|security.ubuntu.com|archive.ubuntu.com|security.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com|security.ubuntu.com|archive.ubuntu.com|security.ubuntu.com/ubuntu/) raring universe
deb [http://us.archive.ubuntu.com|security.ubuntu.com|archive.ubuntu.com|security.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com|security.ubuntu.com|archive.ubuntu.com|security.ubuntu.com/ubuntu/) raring-updates universe
deb-src [http://us.archive.ubuntu.com|security.ubuntu.com|archive.ubuntu.com|security.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com|security.ubuntu.com|archive.ubuntu.com|security.ubuntu.com/ubuntu/) raring-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com|security.ubuntu.com|archive.ubuntu.com|security.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com|security.ubuntu.com|archive.ubuntu.com|security.ubuntu.com/ubuntu/) raring multiverse
deb-src [http://us.archive.ubuntu.com|security.ubuntu.com|archive.ubuntu.com|security.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com|security.ubuntu.com|archive.ubuntu.com|security.ubuntu.com/ubuntu/) raring multiverse
deb [http://us.archive.ubuntu.com|security.ubuntu.com|archive.ubuntu.com|security.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com|security.ubuntu.com|archive.ubuntu.com|security.ubuntu.com/ubuntu/) raring-updates multiverse
deb-src [http://us.archive.ubuntu.com|security.ubuntu.com|archive.ubuntu.com|security.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com|security.ubuntu.com|archive.ubuntu.com|security.ubuntu.com/ubuntu/) raring-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com|security.ubuntu.com|archive.ubuntu.com|security.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com|security.ubuntu.com|archive.ubuntu.com|security.ubuntu.com/ubuntu/) raring-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com|security.ubuntu.com|archive.ubuntu.com|security.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com|security.ubuntu.com|archive.ubuntu.com|security.ubuntu.com/ubuntu/) raring-backports main restricted universe multiverse

deb [http://archive.ubuntu.com|security.ubuntu.com|archive.ubuntu.com|security.ubuntu.com/ubuntu](http://archive.ubuntu.com|security.ubuntu.com|archive.ubuntu.com|security.ubuntu.com/ubuntu) raring-security main restricted
deb-src [http://archive.ubuntu.com|security.ubuntu.com|archive.ubuntu.com|security.ubuntu.com/ubuntu](http://archive.ubuntu.com|security.ubuntu.com|archive.ubuntu.com|security.ubuntu.com/ubuntu) raring-security main restricted
deb [http://archive.ubuntu.com|security.ubuntu.com|archive.ubuntu.com|security.ubuntu.com/ubuntu](http://archive.ubuntu.com|security.ubuntu.com|archive.ubuntu.com|security.ubuntu.com/ubuntu) raring-security universe
deb-src [http://archive.ubuntu.com|security.ubuntu.com|archive.ubuntu.com|security.ubuntu.com/ubuntu](http://archive.ubuntu.com|security.ubuntu.com|archive.ubuntu.com|security.ubuntu.com/ubuntu) raring-security universe
deb [http://archive.ubuntu.com|security.ubuntu.com|archive.ubuntu.com|security.ubuntu.com/ubuntu](http://archive.ubuntu.com|security.ubuntu.com|archive.ubuntu.com|security.ubuntu.com/ubuntu) raring-security multiverse
deb-src [http://archive.ubuntu.com|security.ubuntu.com|archive.ubuntu.com|security.ubuntu.com/ubuntu](http://archive.ubuntu.com|security.ubuntu.com|archive.ubuntu.com|security.ubuntu.com/ubuntu) raring-security multiverse



[/COLOR]As i mentioned above, even after updating this file with following cmd[COLOR=#800080]
[COLOR=#0000cd]sudo sed -i -e 's/archive.ubuntu.com\|security.ubuntu.com/old-releases.ubuntu.com/g' /etc/apt/sources.list
[/COLOR][/COLOR]the cmd[COLOR=#800080][COLOR=#0000cd]
sudo apt-get update [/COLOR][/COLOR]does not help[COLOR=#800080][COLOR=#0000cd]
[/COLOR][/COLOR]it still gives [COLOR=#ff0000]system errors[/COLOR] ! :([COLOR=#800080][COLOR=#0000cd]
[/COLOR] [/COLOR]

---

### Post by Pratik_Mehta on 2015-02-07
When i use the GUI "Software Updater", for more than 2 hours it just keeps on searching for updates! :O
Then it gives some internet error, which is very crap! :S


Following is the output of "[COLOR=#0000ff]sudo apt-get update[/COLOR]"

[COLOR=#800080]Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg
Hit [http://dl.google.com](http://dl.google.com) stable Release                                                                                                         
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                                                                                              
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                                                                                          
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                                                                                             
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security Release.gpg                                                                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                                                                        
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security Release                                                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                                                  
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/main Sources                                                                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                                                  
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/restricted Sources                                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                                                  
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/universe Sources                                                                    
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/multiverse Sources                                                                  
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/main i386 Packages                                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                                                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                                                                                     
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/restricted i386 Packages                                                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                                                                            
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/universe i386 Packages                                                                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                                                                            
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/multiverse i386 Packages                                                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages                                                                                 
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/main Translation-en                                                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages                                                                                 
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/multiverse Translation-en                                                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages                                                                                 
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/restricted Translation-en                                                           
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/universe Translation-en                                                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages                                                                                 
Hit [http://downloads-distro.mongodb.org](http://downloads-distro.mongodb.org) dist Release.gpg                                                                                        
Hit [http://downloads-distro.mongodb.org](http://downloads-distro.mongodb.org) dist Release                                                                                            
Hit [http://downloads-distro.mongodb.org](http://downloads-distro.mongodb.org) dist/10gen i386 Packages                                                 
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/main Translation-en_US                                                                       
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/multiverse Translation-en_US                                 
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/restricted Translation-en_US           
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) raring-security/universe Translation-en_US             
Ign [http://downloads-distro.mongodb.org](http://downloads-distro.mongodb.org) dist/10gen Translation-en_US                                                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_US                                
Ign [http://downloads-distro.mongodb.org](http://downloads-distro.mongodb.org) dist/10gen Translation-en                         
Err [http://us.old-releases.ubuntu.com](http://us.old-releases.ubuntu.com) raring Release.gpg                                  
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-11 - System error)
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_US          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_US          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en
Err [http://us.old-releases.ubuntu.com](http://us.old-releases.ubuntu.com) raring-updates Release.gpg
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-11 - System error)
Err [http://us.old-releases.ubuntu.com](http://us.old-releases.ubuntu.com) raring-backports Release.gpg
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-11 - System error)
Ign [http://us.old-releases.ubuntu.com](http://us.old-releases.ubuntu.com) raring Release
Ign [http://us.old-releases.ubuntu.com](http://us.old-releases.ubuntu.com) raring-updates Release
Ign [http://us.old-releases.ubuntu.com](http://us.old-releases.ubuntu.com) raring-backports Release
59% [Connecting to us.old-releases.ubuntu.com]
[/COLOR]

...here it gets stuck! this does not go ahead even after 1.5hours of waiting!!

---

### Post by grahammechanical on 2015-02-07
My guess is that the sed command that you used was inaccurate. And you have replaced the URL to the us.archive.ubuntu.com with something that is not a valid URL. This is an example from my sources.list file

> deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) vivid main restricted

I would need to replace "gb.archive.ubuntu.com" with "old-releases.ubuntu.com" I know this is correct because as an experiment I recently installed Ubuntu 9.04 and used that method to upgrade to 9.10 and 10.04 and 10.10. I did that to test the advice I give.

So, "http://us.old-releases.ubuntu.com" is inaccurate. You should also disable those PPAs. The first time you ran that sed command you gave the instruction to replace "us.archive.ubuntu.com" with "security.ubuntu.com/old-releases.ubuntu.com"

Regards.

---

### Post by Pratik_Mehta on 2015-02-07
Hey Grahammechanical, thanks for the quick reply.

Two questions: 1. What is PPAs ??!:O
2. What exactly should i change in my sources.list file ?  (note that above, i have pasted the current contents of sources.list file)

Regards,
Pratik

---

### Post by Bucky Ball on 2015-02-07
*Thread moved to **Installation & Upgrades**.*

A fresh install is probably best. You would only be able to upgrade to 13.10 from where you are, and that is also EOL, so I doubt that's possible anyway. If you do make it to 13.10, then you are going to need to upgrade to 14.04 LTS to get to the latest LTS release (supported until April 2019). This will take time, bandwidth, and can be problematic. As I say, also probably impossible to do as first you would need to upgrade an EOL release to an EOL release. 

Personally, I'd back up valuable data, [download the 14.04 LTS ISO]("http://www.ubuntu.com/download/desktop"), create install media and install 14.04 LTS and start from there. LTS can upgrade directly to the next LTS, so 14.04 LTS will upgrade to 16.04 LTS when it comes out, leapfrogging the interim releases in between. 

Good luck. ;)

---

### Post by Pratik_Mehta on 2015-02-08
Hey Bucky ball,
Thanks for your inputs. I will start downloading 14.04 LTS ISO

Side by side, i am trying to upgrade this to 13.10 (until 14.04 gets downloaded). Following is the changes i have made in the sources.list file. Is this fine ?
```
deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) raring main universe restricted multiverse
#deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) raring-security restricted universe multiverse main
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) raring-security restricted universe multiverse main
deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) raring-updates restricted universe multiverse main
deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) raring-proposed restricted universe multiverse main
deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) raring-backports restricted universe multiverse main
```

---

### Post by Bucky Ball on 2015-02-08
Sorry, I can't help with that. Not familiar with the process(es) involved with upgrading EOL releases. As mentioned, 13.10 is also EOL, so you might be working in the dark here. It might be possible to upgrade EOL to EOL release via the backports and old repos. No idea, but good luck. 

If you have any questions about installing the 14.04 LTS release, though, just ask. ;)

PS: Please use code tags for terminal output. Neater, space-saving and easier to read. See the last link in my signature for how or look at how I've done it in your last post by clicking 'Edit Post'. Thanks.

---

### Post by beforelogic on 2015-09-18
THANK YOU all concerned for this post / thread!  Saved some hair pulling!

I had the depricated us.old-releases.ubuntu.com in sources.list instead of just the newer format old-releases.ubuntu.com

Best regards,

- Tyler

> **grahammechanical said:**
> 
I would need to replace "gb.archive.ubuntu.com" with "old-releases.ubuntu.com" I know this is correct because as an experiment I recently installed Ubuntu 9.04 and used that method to upgrade to 9.10 and 10.04 and 10.10. I did that to test the advice I give.

So, "http://us.old-releases.ubuntu.com" is inaccurate.

---

