---
title: "Update Manager fails to fetch from old-releases (Intrepid Ibex)"
date: 2011-01-15
forum: Installation &amp; Upgrades
---

### Post by rivercobble on 2011-01-15
I'm relatively new to Ubuntu, and am trying to do an application update in Intrepid with the end goal of upgrading up to Lucid Lynx.  

Earlier, in my sources.list, I had changed archive.ubuntu.com to old-releases.ubuntu.com, as suggested on a couple other threads, to address 404 Not Found errors from Intepid no longer being supported.  I was able to install a couple of applications immediately afterwards.

Now when I run Update Manager I get the following messages:

Could not download all repository indexes

Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/intrepid/Release](http://old-releases.ubuntu.com/ubuntu/dists/intrepid/Release)  Unable to find expected entry  deb-src/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://wine.budgetdedicated.com/apt/dists/intrepid/main/binary-i386/Packages.gz](http://wine.budgetdedicated.com/apt/dists/intrepid/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Some index files failed to download, they have been ignored, or old ones used instead.

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.


I tried from the command line:

sudo apt-get update

as suggested on another thread, and got similar errors:

Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release.gpg
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Translation-en_US                  
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid Release.gpg                        
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid/main Translation-en_US             
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197B]                           
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Translation-en_US     
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid/universe Translation-en_US         
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid/multiverse Translation-en_US       
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid/deb-src Translation-en_US          
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid/http://archive.ubuntu.com/ubuntu Translation-en_US
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid/intrepid Translation-en_US  
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-updates Release.gpg                
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-updates/main Translation-en_US     
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-updates/universe Translation-en_US 
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release                                 
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Packages                     
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-security Release.gpg     
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Packages                       
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Packages                     
  404 Not Found
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-security/universe Translation-en_US
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-security/multiverse Translation-en_US
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid Release                  
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-updates Release          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Packages                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Packages                     
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-security Release                   
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Packages             
  404 Not Found [IP: 91.189.88.46 80]
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid/restricted Sources       
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid/main Sources
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid/multiverse Packages      
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages                 
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Packages           
  404 Not Found [IP: 91.189.88.46 80]
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid/universe Sources         
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid/multiverse Sources       
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-updates/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-updates/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-updates/main Sources     
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Packages           
  404 Not Found [IP: 91.189.88.46 80]
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-updates/universe Sources 
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-updates/multiverse Sources
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-security/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-security/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-security/multiverse Packages
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1347B]
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-security/main Sources
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-security/universe Sources
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) intrepid-security/multiverse Sources
Get:3 [http://dl.google.com](http://dl.google.com) stable/main Packages [1091B]
Fetched 2635B in 1s (1640B/s)   
W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/intrepid/Release](http://old-releases.ubuntu.com/ubuntu/dists/intrepid/Release)  Unable to find expected entry  deb-src/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/intrepid/main/binary-i386/Packages.gz](http://wine.budgetdedicated.com/apt/dists/intrepid/main/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.


I tried switching to other mirrors, which didn't help.  Using defaults (System > Administration > Software Sources > Authentication, Restore Defaults) seems to have no effect either; it still seems to use my sources.list file (at least, the error messages still refer to old-releases, etc).

My sources.list file looks like this:

# 
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081028)]/ intrepid main restricted
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid restricted main #Added by software-properties

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081028)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid main universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid universe multiverse #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid-updates main universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid-updates main universe multiverse #Added by software-properties

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
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid-security main universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid-security main universe multiverse #Added by software-properties
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex"
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid multiverse deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid universe intrepid [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) deb-src #Added by software-properties
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid multiverse
# deb [http://ppa.launchpad.net/jcfp/ppa/ubuntu](http://ppa.launchpad.net/jcfp/ppa/ubuntu) intrepid main
deb [http://ftp.utexas.edu/ubuntu/](http://ftp.utexas.edu/ubuntu/) intrepid universe main restricted multiverse

Could someone advise?  Thanks in advance!

- rivercobble

---

### Post by coffeecat on 2011-01-15
> **rivercobble said:**
> I'm relatively new to Ubuntu, and am trying to do an application update in Intrepid with the end goal of upgrading up to Lucid Lynx. 

First, welcome to the forum.

To be absolutely honest, it would be quicker and easier simply to backup all your personal files and do a fresh install of Lucid. Even if you were able to completely update Intrepid in order to update it to Jaunty, you'll probably have similar problems in Jaunty which is also end-of-life. Then you'd have to upgrade to Karmic, and then finally to Lucid.

That's a lot to download and much to go wrong.

Glancing through your post, you have a lot of stuff still which is not pointing to the old-release server. Anything that is not old-release with a time-expired release is going to fail.

---

### Post by rivercobble on 2011-01-15
Thanks for the welcome and the input.  

Well... I had debated awhile whether to rebuild from scratch and decided to try the incremental approach first.  One issue is that I have a lot of applications that have been configured and would prefer to keep those intact as much as possible.  I'm hoping (perhaps foolishly) for a smoother, though maybe slower, ride from Intrepid to Jaunty and up, than restarting from zero, and for an operational machine between my release upgrades.  Also I figure that if the incremental approach gets too tangled I'll still have the option to do the one-off install of Lucid, where as if I start with the latter, if I get stuck... I'll be stuck.

So... any idea, coffeecat or anyone else, how to address this?

And why is it trying to hit the old-release server in the first place?  The only possible candidate that might cause this, that I see in my sources.list is the following line:

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex"

But getting rid of this doesn't change the Update Manager's error messages at all.  Is there another place that I'm supposed to be managing the servers besides sources.list?

---

### Post by coffeecat on 2011-01-16
I've highlighted in red what I think are the problematic parts of your   sources.list. Anything which is not old-release.ubuntu.com will fail   with a 404. 

> **rivercobble said:**
> My sources.list file looks like this:

# 
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081028)]/ intrepid main restricted
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid restricted main #Added by software-properties

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081028)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid main universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid universe multiverse #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid-updates main universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid-updates main universe multiverse #Added by software-properties

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
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid-security main universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid-security main universe multiverse #Added by software-properties
deb [color=red]http://wine.budgetdedicated.com/apt intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex"[/color]
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid multiverse deb-src [COLOR=Red]http://archive.ubuntu.com/ubuntu intrepid multiverse[/COLOR]
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid universe intrepid [COLOR=Red]http://archive.ubuntu.com/ubuntu deb-src #Added by software-properties[/COLOR]
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid multiverse
# deb http://ppa.launchpad.net/jcfp/ppa/ubuntu intrepid main
[COLOR=Red]deb http://ftp.utexas.edu/ubuntu/ intrepid universe main restricted multiverse[/COLOR]

There are a few archive.ubuntu.com lines still there, but they are   commented (preceded by #) so they won't matter. I'm puzzled by the two   archive.ubuntu.com lines that are tagged onto the end of old-releases   lines. It's best to simply delete the archive.ubuntu com bits.

> **rivercobble said:**
> And why is it trying to hit the old-release  server in the first place?  The only possible candidate that might cause  this, that I see in my sources.list is the following line:

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex"

I don't follow that. You have to use the old-releases.ubuntu.com server  for end-of-life releases. A third party server such as that  budgetdedicated one has probably had all the Intrepid packages removed -  hence the 404 messages. You must remove all archive.ubuntu.com and all  3rd party stuff from your sources.list and have only  old-releases.ubuntu.com lines.

I still believe that a fresh install will be better despite all the  configuration you want to keep. The fact that you have 3rd-party stuff  installed at all makes upgrade problems more likely.

---

### Post by rivercobble on 2011-01-16
It works now!

> 
Anything which is not old-release.ubuntu.com will fail   with a 404. 
I first changed the remaining archive.ubuntu.com references to old-releases.ubuntu.com and commented out the budgetdedicated server and that got rid of the 404 errors.  The utexas server was for one of the mirrors I tried; I've deleted it.

> 
 I'm puzzled by the two archive.ubuntu.com lines that are tagged onto the end of old-releases lines. It's best to simply delete the archive.ubuntu com bits.
I don't know where these came from; I didn't put them in by hand.   The first was the culprit behind this error:

Failed to fetch [http://old-releases.ubuntu.com/ubunt...trepid/Release]("http://old-releases.ubuntu.com/ubuntu/dists/intrepid/Release")  Unable to find expected entry  deb-src/binary-i386/Packages in Meta-index file (malformed Release file?)

Error goes away if I put deb and deb-src on different lines.  I don't think this had been a problem before, not sure why it is now (or maybe I should say, why it wasn't earlier). The other line, which looks entirely scrambled, seems to be innocuous.  I've gotten rid of both lines, and I guess I can delete others with duplicate uris as well.  They seem to be appended sometimes when I make changes in Software Sources.

So I'm good to go.  I'll give Jaunty a try and if it gets too hairy will go straight to Lucid.

I appreciate your help, coffeecat!

---

### Post by coffeecat on 2011-01-16
Good luck!

---

