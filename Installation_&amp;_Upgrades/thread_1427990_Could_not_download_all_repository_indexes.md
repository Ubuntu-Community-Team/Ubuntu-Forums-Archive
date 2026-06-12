---
title: "Could not download all repository indexes"
date: 2010-03-12
forum: Installation &amp; Upgrades
---

### Post by PDA1 on 2010-03-12
The subject line above is the error message I get when Update Manager runs.

**I also get the following;**

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

**....and this;**

Failed to fetch [http://ppa.launchpad.net/ubuntu-wine/pp/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/ubuntu-wine/pp/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://archive.ubuntu.com/dists/karmic/main/binary-i386/Packages.gz](http://archive.ubuntu.com/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/dists/karmic/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/dists/karmic/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.45 80]
Some index files failed to download, they have been ignored, or old ones used instead.

Also, Update Manager says,** "Your System is up-to date.  The package information was last updated 55 days ago"**

I supposedly updated yesterday, so why does it say 55 days ago?

How do I fix this stuff?

---

### Post by ajgreeny on 2010-03-12
Try ```
sudo apt-get update
``` and then ```
sudo apt-get upgrade
``` and see if you get similar error messages.

If that does not help, just try a different server for your installations and updates from *System ->Administration ->Software Sources*

---

### Post by Kevbert on 2010-03-12
The links should be:
[http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)
[http://archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz)
[http://archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.gz)

---

### Post by PDA1 on 2010-03-12
Here's what I just got....again.



Failed to fetch [http://ppa.launchpad.net/ubuntu-wine/pp/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/ubuntu-wine/pp/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://archive.ubuntu.com/dists/karmic/main/binary-i386/Packages.gz](http://archive.ubuntu.com/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/dists/karmic/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/dists/karmic/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.46 80]
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by PDA1 on 2010-03-12
> **Kevbert said:**
> The links should be:
[http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)
[http://archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz)
[http://archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.gz)


If they should be as you show.....which ones do I change and how do I do it?  That stuff is meaningless to me.

---

### Post by Kevbert on 2010-03-12
Is this a standard install ? How did you install Wine ? (via Synaptic ?) 
Please post your /etc/apt/sources.list file and we'll go from there.

---

### Post by PDA1 on 2010-03-12
The answer to all of your questions is, "I don't know".


Here's the /etc/apt/sources.list

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
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
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

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

---

### Post by Kevbert on 2010-03-12
Very strange the sources that are showing up as being unavailable are not shown in your sources.list file. Please try going to System-Administration-Software Sources and see if they appear under the 'Other Software' tab. If so, make sure they aren't ticked (you're looking for [http://ppa.launchpad.net](http://ppa.launchpad.net)...and [http://archive.ubuntu.com](http://archive.ubuntu.com)...) Then select Close and run the commands in terminal as suggested by ajgreeny (above).

---

### Post by ajgreeny on 2010-03-12
Have a look for a folder ** /etc/apt/sources.list.d**  as this may contain the rogue entries in a separate file.

---

### Post by PDA1 on 2010-03-12
> **Kevbert said:**
> Very strange the sources that are showing up as being unavailable are not shown in your sources.list file. Please try going to System-Administration-Software Sources and see if they appear under the 'Other Software' tab. If so, make sure they aren't ticked (you're looking for [http://ppa.launchpad.net](http://ppa.launchpad.net)...and [http://archive.ubuntu.com](http://archive.ubuntu.com)...) Then select Close and run the commands in terminal as suggested by ajgreeny (above).


Ok....here's what I did- I unchecked in Other Software Tab any address that had even a part of the addresses; [http://ppa.launchpad.net](http://ppa.launchpad.net)  or [http://archive.ubuntu.com](http://archive.ubuntu.com) in it.

There were a lot of addresses that began with the 2 addresses above and each had a bunch of stuff after it.

I then reloaded (or whatever it said....I don't remember) and it looks like everything updated to the current date and time....in other words there was no more reference to my updating 55 days ago.

What do you folks think of what I did?  Do you think that fixed the problem or am I just avoiding others?

---

### Post by Kevbert on 2010-03-13
The repositories that you should be using are [http://**us](http://**us)**.archive.ubuntu.com according to your previous sources.list. These addresses should cover all your updates (including Wine) so any update problems are less likely. 
If you get the http 404 error this normally means that the address either does not exist (as it's been changed) or is temporarily unavailable (often due to server updates). You can normally check this by entering the failing address in Firefox (or whatever browser you use (less the end part Packages.gz).
Hope this helps.

---

### Post by PDA1 on 2010-03-13
> **Kevbert said:**
> The repositories that you should be using are [http://**us**]("http://%3Cb%3Eus%3C/b%3E").archive.ubuntu.com according to your previous sources.list. These addresses should cover all your updates (including Wine) so any update problems are less likely. 
If you get the http 404 error this normally means that the address either does not exist (as it's been changed) or is temporarily unavailable (often due to server updates). You can normally check this by entering the failing address in Firefox (or whatever browser you use (less the end part Packages.gz).
Hope this helps.


Concerning this address- [http://**us**]("http://%3cb%3eus%3c/b%3E").archive.ubuntu.com.....where do I add it in the Software Sources application?

---

### Post by Kevbert on 2010-03-13
You don't need to it's already there in your sources.list. For example
```
deb **http://us.archive.ubuntu.com**/ubuntu/ karmic main restricted
```

---

