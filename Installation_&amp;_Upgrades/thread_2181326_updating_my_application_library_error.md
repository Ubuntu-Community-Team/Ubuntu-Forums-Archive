---
title: "updating my application library error"
date: 2013-10-17
forum: Installation &amp; Upgrades
---

### Post by ubilli on 2013-10-17
[h=1]W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>


W: GPG error: [http://ng.archive.ubuntu.com](http://ng.archive.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/Release](http://extras.ubuntu.com/ubuntu/dists/precise/Release)  


W: Some index files failed to download. They have been ignored, or old ones used instead.


[/h]

---

### Post by slickymaster on 2013-10-17
Hi [COLOR=#000000]ubilli[/COLOR], try to clean the content of **/var/lib/apt/lists** directory and rebuild it:
```
sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update
```

---

### Post by ubilli on 2013-10-18
Failed to fetch cdrom://Ubuntu 13.04 _Raring Ringtail_ - Alpha i386 (20130417)/dists/raring/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 13.04 _Raring Ringtail_ - Alpha i386 (20130417)/dists/raring/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by ubilli on 2013-10-18
this is what it said...

---

### Post by slickymaster on 2013-10-18
> **ubilli said:**
> Failed to fetch cdrom://Ubuntu 13.04 _Raring Ringtail_ - Alpha i386 (20130417)/dists/raring/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 13.04 _Raring Ringtail_ - Alpha i386 (20130417)/dists/raring/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download. They have been ignored, or old ones used instead.

Assuming that is the output you obtained after cleaning the content [COLOR=#000000]of your [/COLOR]**/var/lib/apt/lists** directory and you've run the command```
sudo apt-get update && sudo apt-get upgrade
```apparently your first problem is solved and now the update manager is looking for packages on the Ubuntu CD/DVD. If it is not inserted you get that error. You can disable the CD as package source. Open the software center, go to Edit/Software Sources... and disable the CD on the first tab.

---

### Post by ubilli on 2013-10-18
W: Failed to fetch cdrom://Ubuntu 13.04 _Raring Ringtail_ - Alpha i386 (20130417)/dists/raring/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Ubuntu 13.04 _Raring Ringtail_ - Alpha i386 (20130417)/dists/raring/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by slickymaster on 2013-10-18
Have you tried any of the suggestions made?
If you really want someone to be able to provide some help, it isn't enough just to post some output, you should also explain what you've done in order to get said output.

Can you please post the output of:```
cat /etc/apt/sources.list
```

---

### Post by ubilli on 2013-10-21
# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/main/binary-i386/


# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ precise main restricted


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb cdrom:[Ubuntu 13.04 _Raring Ringtail_ - Alpha i386 (20130417)]/ dists/raring/main/binary-i386/
deb cdrom:[Ubuntu 13.04 _Raring Ringtail_ - Alpha i386 (20130417)]/ dists/raring/restricted/binary-i386/
deb [http://ng.archive.ubuntu.com/ubuntu/](http://ng.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://ng.archive.ubuntu.com/ubuntu/](http://ng.archive.ubuntu.com/ubuntu/) precise main restricted


## Major bug fix updates produced after the final release of the
## distribution.


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ng.archive.ubuntu.com/ubuntu/](http://ng.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://ng.archive.ubuntu.com/ubuntu/](http://ng.archive.ubuntu.com/ubuntu/) precise universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ng.archive.ubuntu.com/ubuntu/](http://ng.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://ng.archive.ubuntu.com/ubuntu/](http://ng.archive.ubuntu.com/ubuntu/) precise multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.




## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) precise partner


this is the output of what you said i should do...

---

### Post by ubilli on 2013-10-21
am sorry for not commenting...[[COLOR=#000000]slickymaster[/COLOR]]("http://ubuntuforums.org/member.php?u=1753126")[COLOR=#000000] [/COLOR]

---

### Post by fantab on 2013-10-21
> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb cdrom:[Ubuntu 13.04 _Raring Ringtail_ - Alpha i386 (20130417)]/ dists/raring/main/binary-i386/
deb cdrom:[Ubuntu 13.04 _Raring Ringtail_ - Alpha i386 (20130417)]/ dists/raring/restricted/binary-i386/


There is your problem.
```
gksu gedit /etc/apt/sources.list
```

... and add [COLOR=#b22222]**#**[/COLOR] in front of the deb as suggested below:
> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
[COLOR=#b22222]**#**[/COLOR]deb cdrom:[Ubuntu 13.04 _Raring Ringtail_ - Alpha i386 (20130417)]/ dists/raring/main/binary-i386/
[COLOR=#b22222]**#**[/COLOR]deb cdrom:[Ubuntu 13.04 _Raring Ringtail_ - Alpha i386 (20130417)]/ dists/raring/restricted/binary-i386/


Close Gedit. and in terminal run:
```
sudo apt-get update && sudo apt-get upgrade
```

EDIT: By the way what is your Ubuntu Version, 12.04 or 13.04?

---

### Post by slickymaster on 2013-10-21
> **fantab said:**
> There is your problem.
```
sudo gedit /etc/apt/sources.list
```

... and add [COLOR=#b22222]**#**[/COLOR] in front of the deb as suggested below:


Close Gedit. and in terminal run:
```
sudo apt-get update && sudo apt-get upgrade
```

EDIT: By the way what is your Ubuntu Version, 12.04 or 13.04?

+1

Your sources list as it is now contains repositories from 2 different Ubuntu releases, 12.04 - Precise and 13.04 - Raring, but it looks to me that currently you're running 12.04, not 13.04. So all you have to do is to follow fantab's advise and you'll be ready to go.

I'm curious though on how you ended up with raring repositories in your sources.

---

### Post by fantab on 2013-10-21
I edited my earlier post to use 'gksu' instead of 'sudo'. 'gksu' is not installed by default in 13.10, at least in my development version it wasn't, hence the confusion.

---

### Post by slickymaster on 2013-10-21
> **fantab said:**
> I edited my earlier post to use 'gksu' instead of 'sudo'. 'gksu' is not installed by default in 13.10, at least in my development version it wasn't, hence the confusion.

Good call.

_@_[U]ubilli
[/U]Just as a matter of information, regarding fantab's editing, please refer to:
[Why is gksu no longer installed by default in 13.04?]("http://askubuntu.com/questions/284306/why-is-gksu-no-longer-installed-by-default-in-13-04")
[When to use pkexec vs. gksu/gksudo?]("http://askubuntu.com/questions/78352/when-to-use-pkexec-vs-gksu-gksudo")

---

### Post by ubilli on 2013-10-24
i did it and when i tied to install with apt-get this is what it said...

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by fantab on 2013-10-24
Try:
```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

report back if there are any further errors.

---

