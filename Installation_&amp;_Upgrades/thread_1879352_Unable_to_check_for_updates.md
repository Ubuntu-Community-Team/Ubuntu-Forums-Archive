---
title: "Unable to check for updates"
date: 2011-11-11
forum: Installation &amp; Upgrades
---

### Post by agamjain on 2011-11-11
I have installed Ubuntu 11.10 on my Samsung N148 netbook. I had upgraded it from the 11.04 that I had earlier. After the upgrade, for some reason, I am unable to check and install updates through the update manager. When I click on "Check" button in the update manager, it searches for the updates but in the end it displays an error message saying "Could not check for updates. Please check your internet connection." My internet connection is working fine. I have a Sprint USB Wireless internet and it is configured properly. Can you please advise what I can do to resolve this error?

---

### Post by raja.genupula on 2011-11-11
give me update of ```
sudo apt-get update 
```

---

### Post by agamjain on 2011-11-11
Is there some bug with the GUI version of the Update Manager?

---

### Post by raja.genupula on 2011-11-11
no we need that information of update command , we need that to resolve your issue.you're not having any GUI problem .post that output

---

### Post by Hakunka-Matata on 2011-11-11
> **agamjain said:**
> Is there some bug with the GUI version of the Update Manager?

Maybe, suggestion: add the oneiric repositories to your "software sources" first.  I'll post a list of mine, I'm on oneiric 11.10 32bit Desktop, 3.0.0.12.  Gnome 3

**EDIT:  OK, try this:  **[http://ubuntuforums.org/showthread.php?t=1742588](http://ubuntuforums.org/showthread.php?t=1742588)

---

### Post by Hakunka-Matata on 2011-11-11
```
das@sdb1GUID:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://mirror.math.ucdavis.edu/ubuntu/ oneiric main restricted
deb-src http://mirror.math.ucdavis.edu/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.math.ucdavis.edu/ubuntu/ oneiric-updates main restricted
deb-src http://mirror.math.ucdavis.edu/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror.math.ucdavis.edu/ubuntu/ oneiric universe
deb-src http://mirror.math.ucdavis.edu/ubuntu/ oneiric universe
deb http://mirror.math.ucdavis.edu/ubuntu/ oneiric-updates universe
deb-src http://mirror.math.ucdavis.edu/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.math.ucdavis.edu/ubuntu/ oneiric multiverse
deb-src http://mirror.math.ucdavis.edu/ubuntu/ oneiric multiverse
deb http://mirror.math.ucdavis.edu/ubuntu/ oneiric-updates multiverse
deb-src http://mirror.math.ucdavis.edu/ubuntu/ oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://mirror.math.ucdavis.edu/ubuntu/ oneiric-backports main restricted universe multiverse
deb-src http://mirror.math.ucdavis.edu/ubuntu/ oneiric-backports main restricted universe multiverse

deb http://mirror.math.ucdavis.edu/ubuntu/ oneiric-security main restricted
deb-src http://mirror.math.ucdavis.edu/ubuntu/ oneiric-security main restricted
deb http://mirror.math.ucdavis.edu/ubuntu/ oneiric-security universe
deb-src http://mirror.math.ucdavis.edu/ubuntu/ oneiric-security universe
deb http://mirror.math.ucdavis.edu/ubuntu/ oneiric-security multiverse
deb-src http://mirror.math.ucdavis.edu/ubuntu/ oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
# deb-src http://extras.ubuntu.com/ubuntu oneiric main
das@sdb1GUID:~$ 

```

---

### Post by agamjain on 2011-11-11
Thanks all for the quick help. I will try running this on my Ubuntu and let you know the output.

---

### Post by agamjain on 2011-11-12
This is the error message that I get:

> Fetched 5,077 B in 23s (217 B/s)                                               
W: Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/dists/natty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/dists/natty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.


---

### Post by raja.genupula on 2011-11-12
do this open your update manager --> settings --> other software and uncheck that cd-rom check box and then update again.

---

### Post by agamjain on 2011-11-12
This seems to work. But would I not be losing some of the updates if I uncheck that box?

---

### Post by PaulW2U on 2011-11-12
> **agamjain said:**
> This seems to work. But would I not be losing some of the updates if I uncheck that box?

No, you can only get updates from the repositories, not the CD.

---

### Post by agamjain on 2011-11-12
I see. That option needs a CD inserted for updates? I am sorry but I am kind of new so do not know.

---

### Post by PaulW2U on 2011-11-12
> **agamjain said:**
> I see. That option needs a CD inserted for updates? I am sorry but I am kind of new so do not know.

That entry refers to your original installation CD, so you have already used what is on it to install your system. There's no point checking it for updates as the repositories will always give you newer files if there are any.

---

### Post by agamjain on 2011-11-12
Thanks a lot for all your help. I can rest a lot easier now knowing that I have the latest updated. ;)

---

