---
title: "Messed up repos"
date: 2006-04-03
forum: Installation &amp; Upgrades
---

### Post by theredcross on 2006-04-03
Ok, I was trying out the guide to installing WoW on ubuntu somewhere else on this forum, and I came to a point where i realised I hadn't installed any nvidia drivers (I just switched to Ubuntu from Fedora about a week ago). So I went to [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/) and started going through the process of setting up some new repo's. Well, after getting to the step where you actually edit the /etc/apt/sources.list I managed to screw up. Not quite sure how, but ```
sudo apt-get update
sudo apt-get upgrade
```
is giving me a nice pretty list of errors, the bottom of which informs me I should try updating to fix the problem. Oh, and as a nice surprise, when I went to back up my sources.list i made a typo somewhere and wasn't paying attention at the time. What I'm wondering is could I simply get what originally comes in the file, replace it, then go back and update/upgrade/try to add the extra repo's again? I'm wondering if the half-update things that go on may have made a more complicated mess out of it. just for reference, here is the error that spews out when I try to update (sorry for length):
```
# sudo apt-get update
Ign cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy Release.gpg
Ign cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy ReleaseIgn cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages
Ign cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages
Err cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err http: archive.ubuntu.com/ubuntu Release.gpg
  Could not resolve 'dists'
Err http: archive.ubuntu.com.ubuntu Release.gpg
  Could not resolve 'dists'
Get:1 http://us.archive.ubuntu.com breezy-updates Release.gpg [189B]
Get:2 http://us.archive.ubuntu.com breezy Release.gpg [189B]
Ign http: archive.ubuntu.com/ubuntu Release
Get:3 http://us.archive.ubuntu.com breezy-backports Release.gpg [189B]
Hit http://us.archive.ubuntu.com breezy-updates Release
Get:4 http://security.ubuntu.com breezy-security Release.gpg [189B]
Ign http: archive.ubuntu.com.ubuntu Release
Hit http://us.archive.ubuntu.com breezy Release
Hit http://us.archive.ubuntu.com breezy-backports Release
Hit http://security.ubuntu.com breezy-security Release
Ign http: archive.ubuntu.com/ubuntu/breezy-backports Packages
Hit http://us.archive.ubuntu.com breezy-updates/main Packages
Hit http://us.archive.ubuntu.com breezy-updates/restricted Packages
Hit http://us.archive.ubuntu.com breezy-updates/universe Packages
Hit http://us.archive.ubuntu.com breezy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com breezy/universe Packages
Hit http://us.archive.ubuntu.com breezy/main Packages
Hit http://us.archive.ubuntu.com breezy/restricted Packages
Hit http://security.ubuntu.com breezy-security/universe Packages
Hit http://us.archive.ubuntu.com breezy/multiverse Packages
Hit http://us.archive.ubuntu.com breezy-backports/main Packages
Hit http://us.archive.ubuntu.com breezy-backports/restricted Packages
Hit http://us.archive.ubuntu.com breezy-backports/universe Packages
Hit http://us.archive.ubuntu.com breezy-backports/multiverse Packages
Hit http://security.ubuntu.com breezy-security/main Packages
Hit http://security.ubuntu.com breezy-security/restricted Packages
Hit http://security.ubuntu.com breezy-security/multiverse Packages
Ign http: archive.ubuntu.com/ubuntu/main Packages
Ign http: archive.ubuntu.com/ubuntu/universe Packages
Ign http: archive.ubuntu.com/ubuntu/multiverse Packages
Ign http: archive.ubuntu.com/ubuntu/restricted Packages
Ign http: archive.ubuntu.com.ubuntu/breezy-backports Packages
Ign http: archive.ubuntu.com.ubuntu/main Packages
Ign http: archive.ubuntu.com.ubuntu/universe Packages
Ign http: archive.ubuntu.com.ubuntu/multiverse Packages
Ign http: archive.ubuntu.com.ubuntu/restricted Packages
Err http: archive.ubuntu.com/ubuntu/breezy-backports Packages
  Could not resolve 'dists'
Err http: archive.ubuntu.com/ubuntu/main Packages
  Could not resolve 'dists'
Err http: archive.ubuntu.com/ubuntu/universe Packages
  Could not resolve 'dists'
Err http: archive.ubuntu.com/ubuntu/multiverse Packages
  Could not resolve 'dists'
Err http: archive.ubuntu.com/ubuntu/restricted Packages
  Could not resolve 'dists'
Err http: archive.ubuntu.com.ubuntu/breezy-backports Packages
  Could not resolve 'dists'
Err http: archive.ubuntu.com.ubuntu/main Packages
  Could not resolve 'dists'
Err http: archive.ubuntu.com.ubuntu/universe Packages
  Could not resolve 'dists'
Err http: archive.ubuntu.com.ubuntu/multiverse Packages
  Could not resolve 'dists'
Err http: archive.ubuntu.com.ubuntu/restricted Packages
  Could not resolve 'dists'
Fetched 4B in 7s (1B/s)
Failed to fetch http://dists/archive.ubuntu.com/ubuntu/Release.gpg  Could not resolve 'dists'
Failed to fetch http://dists/archive.ubuntu.com.ubuntu/Release.gpg  Could not resolve 'dists'
Failed to fetch cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/dists/breezy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/dists/breezy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch http://dists/archive.ubuntu.com/ubuntu/breezy-backports/binary-i386/Packages.gz  Could not resolve 'dists'
Failed to fetch http://dists/archive.ubuntu.com/ubuntu/main/binary-i386/Packages.gz  Could not resolve 'dists'
Failed to fetch http://dists/archive.ubuntu.com/ubuntu/universe/binary-i386/Packages.gz  Could not resolve 'dists'
Failed to fetch http://dists/archive.ubuntu.com/ubuntu/multiverse/binary-i386/Packages.gz  Could not resolve 'dists'
Failed to fetch http://dists/archive.ubuntu.com/ubuntu/restricted/binary-i386/Packages.gz  Could not resolve 'dists'
Failed to fetch http://dists/archive.ubuntu.com.ubuntu/breezy-backports/binary-i386/Packages.gz  Could not resolve 'dists'
Failed to fetch http://dists/archive.ubuntu.com.ubuntu/main/binary-i386/Packages.gz  Could not resolve 'dists'
Failed to fetch http://dists/archive.ubuntu.com.ubuntu/universe/binary-i386/Packages.gz  Could not resolve 'dists'
Failed to fetch http://dists/archive.ubuntu.com.ubuntu/multiverse/binary-i386/Packages.gz  Could not resolve 'dists'
Failed to fetch http://dists/archive.ubuntu.com.ubuntu/restricted/binary-i386/Packages.gz  Could not resolve 'dists'
Reading package lists... Done
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http: archive.ubuntu.com/ubuntu/breezy-backports Packages (/var/lib/apt/lists/dists_archive.ubuntu.com_ubuntu_breezy-backports_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http: archive.ubuntu.com/ubuntu/main Packages (/var/lib/apt/lists/dists_archive.ubuntu.com_ubuntu_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http: archive.ubuntu.com/ubuntu/universe Packages (/var/lib/apt/lists/dists_archive.ubuntu.com_ubuntu_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http: archive.ubuntu.com/ubuntu/multiverse Packages (/var/lib/apt/lists/dists_archive.ubuntu.com_ubuntu_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http: archive.ubuntu.com/ubuntu/restricted Packages (/var/lib/apt/lists/dists_archive.ubuntu.com_ubuntu_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http: archive.ubuntu.com.ubuntu/breezy-backports Packages (/var/lib/apt/lists/dists_archive.ubuntu.com.ubuntu_breezy-backports_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http: archive.ubuntu.com.ubuntu/main Packages (/var/lib/apt/lists/dists_archive.ubuntu.com.ubuntu_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http: archive.ubuntu.com.ubuntu/universe Packages (/var/lib/apt/lists/dists_archive.ubuntu.com.ubuntu_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http: archive.ubuntu.com.ubuntu/multiverse Packages (/var/lib/apt/lists/dists_archive.ubuntu.com.ubuntu_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http: archive.ubuntu.com.ubuntu/restricted Packages (/var/lib/apt/lists/dists_archive.ubuntu.com.ubuntu_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by r4ik on 2006-04-03
you could create your own,

[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

Good luck.

---

### Post by theredcross on 2006-04-03
well, that was really quick. no more errors, i no longer live in fear of destroying my repo list. thanks a ton!

---

### Post by r4ik on 2006-04-03
My pleasure.

---

