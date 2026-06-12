---
title: "Failed Upgrade"
date: 2008-04-17
forum: Installation &amp; Upgrades
---

### Post by Funbug on 2008-04-17
Thought I would catch up still back on LTS6.06 so ran "gksu "update-manager -c" as per instructions to come up to 6.10 but it stopped a file 42 of 54 with the following errors, anybody any ideas.


Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg) Could not connect to packages.freecontrib.org:80 (34.52.53.34), connection timed out
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz) 404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz) 404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz) 404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz) 404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz) 404 Not Found

---

### Post by Funbug on 2008-04-18
Nobody fancy giving me a clue then.

Alan...

---

### Post by zvacet on 2008-04-19
```
gksudo gedit /etc/apt/sources.list
```

Put # in front of [http://packages.freecontrib.org/ubun...er/Release.gpg](http://packages.freecontrib.org/ubun...er/Release.gpg)

save file and close.

```
sudo apt-get update && sudo apt-get upgrade
```

Why do you want to upgrade to Edgy which is no longer supported when you can directly upgrade to Hardy? [Here]("https://help.ubuntu.com/community/HardyUpgrades")

---

### Post by Funbug on 2008-04-19
I was only updating to Edgy as I was under the impression from the website I had to. It appeared to suggest you had to work all the way through each release. 

But now you have provided the link I will come straight up to Hardy, THANK YOU very much you have saved me several hours I'm sure. :)

Regards

Alan...

---

### Post by Funbug on 2008-04-19
Bad form I know to reply to your own post but I now have another problem sorry. I put in your first command & got the following file

deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
# deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

# #deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) edgy main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) edgy-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://ftp.uk.debian.org/debian](http://ftp.uk.debian.org/debian) unstable main contrib non-free

Also the system tells me that I have 151 updates to apply which appear to be Edgy updates so I think (which is always worrying) that I am sort of stuck between 2 releases.

Any idea how to proceed.

Alan..

---

### Post by zvacet on 2008-04-19
If you have separate home partition do fresh Hardy install when it becomes stable (one week or so).If you don´t have separate home [make one.]("http://www.psychocats.net/ubuntu/separatehome")Back up your files anyway.

---

### Post by Funbug on 2008-04-19
Thanks again, I'm about to create a /home on a seperate partition as reccomended, can I just ask where evolution hides my emails as those really are th efiles I need to backup.

Alan...

---

### Post by Partyboi2 on 2008-04-19
Try [this]("http://library.gnome.org/users/evolution/stable/b17qy921.html.en") or [this]("http://salahuddin66.blogspot.com/2007/06/backup-evolution-mail.html")

---

### Post by Funbug on 2008-04-27
Well I took the plunge & moved my /home onto another drive. Then just spent a couple of hours updating to 8.04. All appears to be well apart from my resolution, 6.06 detected my graphics card fine & I was running 1024x768 but now I can only select 640x480. I seem to remember it's just a S3 generic on-board card, but suley if 6.06 found it 8.04 should have as well. Where do I go from here?

Alan...

---

### Post by Palamedes234 on 2008-04-27
I got the same problem. 640x480 with a Gforce 8600... no option to change it.

---

### Post by Funbug on 2008-04-28
If it helps anybody the motherboard is a MSI KM2M Combo with Onboard ProSavage8 2D/3D Graphics.

My xorg.conf says

Section "Device"
        Identifier      "Configured Video Device"
        Boardname       "vesa"
        Busid           "PCI:1:0:0"
        Driver          "vesa"
        Screen  0
EndSection

Which is what I assume is wrong but don't know how to change it to S3 SavagePro8

Alan...

---

