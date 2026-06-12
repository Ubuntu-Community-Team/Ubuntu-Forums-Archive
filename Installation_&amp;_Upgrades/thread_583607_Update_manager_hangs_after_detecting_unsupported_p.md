---
title: "Update manager hangs after detecting unsupported packages (Upgrade from Feisty)"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by Declan Moriarty on 2007-10-20
I am running Ubuntu 7.04 (Feisty) and tried to upgrade to 7.10 (Gutsy).  The Update Mananger runs until it displays a message about unsupported packages (that are presumably old).  When you confirm the dialogue the Update Manager hangs.  Rebooting the update manager comes up with new updates but says that soem cant be updated.  I had updated the syatem before upgrading.  Re-running the upgrade had exactly the same result.  How do I get a successfull upgrade?  

I have tried the Feisty alternate install CD to install the Feisty system, but  I didn't work.  I have the Linux system on an external USB2 hard drive and the alternate CD didn't recognize it and gave a list of the partitions on my main PC hard drive.

Is my only option to backup the (minimal) data I have and do a complete re-install not an upgrade?

I have an Athlon 3200+ processor with 1Gb or RAM.
I am running th i386 (32-bit) version of Feisty because the Dapper 64-bit version Gnomme Mag (Magnifier) didn't work.  So when I installed to the Hard Drive I used the 32-bit version.

What I think has happened is that the upgrade didn't start, but that the upade manager is now looking a the new sources for updates.  The next item i the list before the hang was "Downolad Upgrade".  This didn't start because of the hang.

Your help very much appreciated.

Declan Moriarty.

---

### Post by bapoumba on 2007-10-20
COuld you please post your sources.list file? Open a Terminal (> Accessories > Terminal) and run:
```
cat /etc/apt/sources.list
```
Paste the complete output in here.

---

### Post by Declan Moriarty on 2007-10-21
Hello, 

My sources.list file is as follows:-

> 
cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse



Thank you very much in anticipation.

Declan Moriarty.

---

### Post by bapoumba on 2007-10-21
Please run:
```
sudo aptitude update
sudo aptitude full-upgrade
```
And paste the error message to the second command, if applicable.

---

### Post by Declan Moriarty on 2007-10-21
The first command worked ok.  The second command produced the error "Unknown Command"

>  
Unknown command "full-upgrade"


---

### Post by bapoumba on 2007-10-21
Hmm..
Then please run ```
sudo aptitude dist-upgrade
```

---

### Post by gephik on 2007-10-21
Hi, I'm experiencing the same problem as Declan Moriarty. After starting the upgrade process from 7.04 to 7.10 the update manager loads some files, changes the content of /etc/apt/sources.list and gets the new repository files. Then it prints out a list of no longer supported packages. After closing that list, the interface of the update manager goes blank, and nothing happens anymore.

/var/log/dist-upgrade/main.log ends like this:

```
2007-10-21 17:08:14,200 DEBUG Free space on /: 15730040832
2007-10-21 17:08:14,200 DEBUG Dir /usr mounted on /
2007-10-21 17:08:14,201 DEBUG Dir /var mounted on /
2007-10-21 17:08:14,201 DEBUG Dir /boot mounted on /
2007-10-21 17:08:14,201 DEBUG Dir /var/cache/apt/archives mounted on /
2007-10-21 17:08:14,202 DEBUG Dir /home mounted on /
2007-10-21 17:08:14,202 DEBUG fs_free contains: '{'/var': <DistUpgradeControler.FreeSpace object at 0x3c53810>, '/home': <DistUpgradeControler.FreeSpace object at 0x3c53810>, '/boot': <DistUpgradeControler.FreeSpace object at 0x3c53810>, '/usr': <DistUpgradeControler.FreeSpace object at 0x3c53810>, '/': <DistUpgradeControler.FreeSpace object at 0x3c53810>, '/var/cache/apt/archives': <DistUpgradeControler.FreeSpace object at 0x3c53810>}'
2007-10-21 17:08:14,211 DEBUG linux-image-2.6.20-16-generic (upgrade|installed) added with 10485760 to boot space
2007-10-21 17:08:14,256 DEBUG linux-image-2.6.22-14-generic (new-install) added with 10485760 to boot space
2007-10-21 17:08:14,311 DEBUG linux-image-2.6.20-15-generic (upgrade|installed) added with 10485760 to boot space
2007-10-21 17:08:14,569 DEBUG dir '/var/cache/apt/archives' needs '1175768098.0' of '<DistUpgradeControler.FreeSpace object at 0x3c53810>' (15730040832.000000)
2007-10-21 17:08:14,569 DEBUG dir '/usr' needs '663437312.0' of '<DistUpgradeControler.FreeSpace object at 0x3c53810>' (14554272734.000000)
2007-10-21 17:08:14,569 DEBUG dir '/usr' needs '52428800' of '<DistUpgradeControler.FreeSpace object at 0x3c53810>' (13890835422.000000)
2007-10-21 17:08:14,569 DEBUG dir '/boot' needs '31457280' of '<DistUpgradeControler.FreeSpace object at 0x3c53810>' (13838406622.000000)
2007-10-21 17:08:14,570 DEBUG dir '/' needs '10485760' of '<DistUpgradeControler.FreeSpace object at 0x3c53810>' (13806949342.000000)
```

So I would think the problem occurs shortly after checking the disk space. As the confirmation window for continuing the upgrade never comes up, the upgrade seems to run amok somewhere here (DistUpgradeControler.py):

```

line 1309:
        # calc the dist-upgrade and see if the removals are ok/expected
        # do the dist-upgrade
        self._view.updateStatus(_("Asking for confirmation"))
        if not self.askDistUpgrade():
            self.abort()
...

line 686:
    def askDistUpgrade(self):
        # check what packages got demoted and ask the user
        # if those shall be removed
...
        # check if we have enough free space 
        if not self._checkFreeSpace():
            return False
        # ask the user if he wants to do the changes
        res = self._view.confirmChanges(_("Do you want to start the upgrade?"),
                                        changes,
                                        self.cache.requiredDownload)
        return res

```

At least that's what I think, although I never met a python in person. Any idea what goes wrong here, or how I could get around this?I would rather not use aptitude or apt-get, because I have read somewhere that this may cause problems (don't remember exactly, but sounded like I do not want to try).

gephik, with regards

---

### Post by Declan Moriarty on 2007-10-21
Hello,

I have tried the aptitude method and this worked OK.  The video card didn't configure properly.  Using the generic option in the grub menu  eventually allowed the Restricted Manager available alert to appear.  Downloading the nVida drivers solved the video problem.  I have finally got Full Screen Magnification working out of the box with Ubuntu!

There are a few wrinkles but so far an awfully lot better that Feisty.

---

### Post by bapoumba on 2007-10-21
@ gephik: please paste your sources.list:
```
cat /etc/apt/sources.list
```

If used to using synaptic, you can use apt-get in the command line. Just do not mix apt-get with aptitude. They do not share their log files, and so neither one of them knows about what you have done using the other. Aptitude is often better at handling dependencies, which is usually good, but sometimes problematic.
In any case, you have to confirm the actions. So if you are not sure, paste the question in here. aptitude or apt-get will only perform actions if you hit the "Y" key.

---

### Post by gephik on 2007-10-21
Well, sources.list before starting upgrade:
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://de.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://de.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://de.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://de.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://de.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://de.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://de.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
```

and then sources.list after starting the upgrade:
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://de.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://de.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://de.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://de.archive.ubuntu.com/ubuntu/ gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://de.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://de.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://de.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```

As to aptitude / apt-get, this: [http://kevin.vanzonneveld.net/techblog/article/upgrade_any_version_of_ubuntu_desktop/](http://kevin.vanzonneveld.net/techblog/article/upgrade_any_version_of_ubuntu_desktop/) made me hesitant about manual upgrade. Well, if there's no other way, I may have to do it after all ... but not during the week, I might need my PC up and running ;-)

gephik, with regards

---

### Post by bapoumba on 2007-10-21
These are sound advices, for the backup your own work at least.
Read also [here]("http://ubuntuforums.org/showthread.php?t=583007").
I have to say I use aptitude only, but it's just me ;)

---

### Post by gephik on 2007-10-22
Thanks for the link bapoumba. I'll heed the deep wisdom and postpone my upgrade until weekend. Don't know whether the problem will be solved till then, but my belief is strong :). Anyway, I will post any new development in this.

gephik, with regards

---

