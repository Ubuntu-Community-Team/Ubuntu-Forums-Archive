---
title: "Synaptic shows nothing, i may have ruined it"
date: 2007-01-14
forum: Installation &amp; Upgrades
---

### Post by La muerte del DIos on 2007-01-14
[SIZE="2"]Well here's my story. I've got an error trying to install wpasupplicant from the update manager. So, seeing it involved wireless Internet connection (which i don't have) i chose to erase the whole /etc/apt/sources.list repo line (it was like tuxfamily.org or something, i don't even remember why i put it there). I did an apt-get update and then got into the update manager again, when i click on it, it just closed.

So finally i decided to do some research of my own. I looked at **apt-get -h ** and search for a way to stop the upgrade to be performed. Then i did **apt-clean, apt-autoclean, apt-remove**. The problem was still there, so i thought maybe i could erase it from the **"Synaptic package manager"** and when i opened it up it showed this mistake:

> 
E: The package wpasupplicant needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

When i click on close, it all seemed normal except THERES NOTHING IN THERE. Just the "all" on the left column, and nothing on the right column, even when i clicked "reload" everything stays the same. So, here the thing, did i just destroyed my computer or can i do something to fix this?](*,) ](*,) ](*,) 

Please help me and thanks for reading.[/SIZE]

Here's my sources.list by the way:

> ## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe main multiverse restricted #Added by software-properties

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse #Added by software-properties

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main


#AUTOMATIX REPOS START

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse #Added by software-properties

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main

deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-security main restricted universe multiverse #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted multiverse

#AUTOMATIX REPOS END

deb [http://morgoth.free.fr/ubuntu](http://morgoth.free.fr/ubuntu) dapper-backports main

deb [http://exodus.xmms.se/debian](http://exodus.xmms.se/debian) dapper main


##Canon##

deb [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu) ./

##Satanic Edition##

deb [http://parker1.co.uk/hell](http://parker1.co.uk/hell) edgy main

deb-src [http://parker1.co.uk/hell](http://parker1.co.uk/hell) edgy main

---

### Post by arnieboy on 2007-01-15
The broken package came from Trevino's repository which you correctly deleted. (Please do not use it again)
To fix this try the following (one by one, dont skip steps, and yes steps 2 and 4 are the same but you need to repeat them):
```
sudo rm -f /var/lib/dpkg/info/wpasupplicant.postrm
wget http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/wpasupplicant_0.5.7+3v1ubuntu3_i386.deb
sudo dpkg -i wpasupplicant_0.5.7+3v1ubuntu3_i386.deb
sudo rm -f /var/lib/dpkg/info/wpasupplicant.postrm
sudo apt-get remove wpasupplicant
```

---

### Post by Skyler0 on 2007-01-16
thx, I had the same issue, and it fixed it all up. :)

Just our of curiousity, what is wrong with the Trevino's repo exactly?

---

