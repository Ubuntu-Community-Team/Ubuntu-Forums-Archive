---
title: "aptitude update error - duplicate sources"
date: 2007-02-21
forum: Installation &amp; Upgrades
---

### Post by magichsjx on 2007-02-21
Hello,
I am running Ubuntu Dapper 6.0.6 and have been getting an error when trying to update:
> sudo aptitude update
It goes fine 99% of the way after which the following errors are outputtted:
> Fetched 521kB in 6m26s (1347B/s)
Reading package lists... Done
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release: Unknown error executing gpgv
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release: Unknown error executing gpgv
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release: Unknown error executing gpgv
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_multiverse_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

When I subsequently run
> sudo apt-get update
as suggested to fix the error(s), agan after 99% is done, I get:
> Ign [http://theli.free.fr](http://theli.free.fr) dapper/listen Packages
Err [http://theli.free.fr](http://theli.free.fr) dapper/listen Packages
  301 Moved Permanently
Fetched 35.1kB in 1m41s (346B/s)
Failed to fetch [ftp://archive.ubuntu.com/ubuntu/dists/dapper/Release](ftp://archive.ubuntu.com/ubuntu/dists/dapper/Release)  Unable to find expected entry  multiversedeb/source/Sources in Meta-index file (malformed Release file?)
Failed to fetch [http://theli.free.fr/packages/dists/dapper/listen/binary-i386/Packages.gz](http://theli.free.fr/packages/dists/dapper/listen/binary-i386/Packages.gz)  301 Moved Permanently
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

Can someone please help me understand what the problem is. TY in advance.

---

### Post by Kateikyoushi on 2007-02-21
Check your sources.list seems you have one entry two times.

```
sudo nano /etc/apt/sources.list
```

---

### Post by magichsjx on 2007-02-21
TY for your response. Appreciate it. I am pasting my sources list here, do not want to delete something if not supposed to. One entry I think is repeated on the third line. Also one in the Automatix section but I do not know if Automatix has to have its own. I have marked those in bold:

> 
deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)]/ dapper main restricted
deb [ftp://archive.ubuntu.com/ubuntu/](ftp://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb-src [ftp://archive.ubuntu.com/ubuntu/](ftp://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiversedeb **[http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dap$**
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
#AUTOMATIX REPOS START

**deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse**

deb [http://people.ubuntu.com/~seb128/deb](http://people.ubuntu.com/~seb128/deb) ./

deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) dapper listen

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main

#AUTOMATIX REPOS END
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse



---

### Post by magichsjx on 2007-02-21
I removed the double entry (The first highlighted entry above). Now I get the following, can someone help.

> sudo aptitude update]

> Err [http://theli.free.fr](http://theli.free.fr) dapper/listen Packages
  301 Moved Permanently


> sudo apt-get update

> Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Ign [http://theli.free.fr](http://theli.free.fr) dapper Release
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Sources
Ign [http://theli.free.fr](http://theli.free.fr) dapper/listen Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Err [http://theli.free.fr](http://theli.free.fr) dapper/listen Packages
  301 Moved Permanently
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Packages
Fetched 9B in 6s (1B/s)
Failed to fetch [http://theli.free.fr/packages/dists/dapper/listen/binary-i386/Packages.gz](http://theli.free.fr/packages/dists/dapper/listen/binary-i386/Packages.gz)  301 Moved Permanently
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


---

### Post by Kateikyoushi on 2007-02-21
Glad you could solve the duplication. You do not have to delete content it is enough if you put # to the beginning of the line, then it will be ignored.

Listen seems to got it's own domain so that adress is not in use anymore. You could delete it.

---

