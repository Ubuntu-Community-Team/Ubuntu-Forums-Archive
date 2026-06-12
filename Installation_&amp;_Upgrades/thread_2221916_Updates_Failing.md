---
title: "Updates Failing"
date: 2014-05-04
forum: Installation &amp; Upgrades
---

### Post by Charlie_Smith on 2014-05-04
I am a Ubuntu 12.04 user and I want to upgrade to 12.10. I have tried the method of upgradig in the packkage manager, but it does not work. What I did: Opened package manager and clicked the "New realease 12.10 is avalible"
The I agreed to the terms page. It put me in a window that notified me where I was in updating. I passed "Getting ready to update" and then it said right at the start of the "Grabbing new software channels" A message told me that some third-party sources were disabled. I dismissed the window. It finished "Grabbing the new software channels" and then told me another message that read:W::Failed to fetch http://archive.canonical.com/dists/$/-sc)/source/Sources  404  Not Found [IP: 91.189.92.150 80]
, W:Failed to fetch http://archive.canonical.com/dists/$/partner/source/Sources  404  Not Found [IP: 91.189.92.150 80]
Help!
Btw, I am missing one link from the error message. I do not have 10 beans yet. That link will be in the comments.

---

### Post by Charlie_Smith on 2014-05-04
, W:Failed to fetch http://archive.canonical.com/dists/$/(lsb_realese/source/Sources  404  Not Found [IP: 91.189.92.150 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by Frogs Hair on 2014-05-04
12.10  reached end of life last month and the repository closed. A direct upgrade from 12.04  to 14.04 will be available in the near future so you may want to set the update manager to notify for LTS releases only. The other choice would be to backup and perform a clean installation of 14.04 if you have the means to create a dvd or usb. There is no hurry because 12.04  is supported until 2017.

---

### Post by ibjsb4 on 2014-05-04
> **Charlie_Smith said:**
> , W:Failed to fetch http://archive.canonical.com/dists/$/(lsb_realese/source/Sources  404  Not Found [IP: 91.189.92.150 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.

This is not right; can you update at all?

```
sudo apt-get update
```

Any errors?

[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

---

### Post by Charlie_Smith on 2014-05-04
I can update, but it fails:W: Failed to fetch http://archive.canonical.com/dists/$/-sc)/source/Sources  404  Not Found [IP: 91.189.92.150 80]

W: Failed to fetch http://archive.canonical.com/dists/$/partner/source/Sources  404  Not Found [IP: 91.189.92.150 80]

W: Failed to fetch http://archive.canonical.com/dists/$/(lsb_realese/source/Sources  404  Not Found [IP: 91.189.92.150 80]

W: Failed to fetch http://archive.canonical.com/dists/$/-sc)/binary-i386/Packages  404  Not Found [IP: 91.189.92.150 80]

W: Failed to fetch http://archive.canonical.com/dists/$/partner/binary-i386/Packages  404  Not Found [IP: 91.189.92.150 80]

W: Failed to fetch http://archive.canonical.com/dists/$/(lsb_realese/binary-i386/Packages  404  Not Found [IP: 91.189.92.150 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by Charlie_Smith on 2014-05-04
I have tried updating to 14.04 LTS but that does the same thing as trying to upgrade to 12.10

---

### Post by ibjsb4 on 2014-05-04
Please post the output (using code tags) of:

```
cat /etc/apt/sources.list
```

[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168)

---

### Post by slooksterpsv on 2014-05-04
Something's not right:
```

W: Failed to fetch http://archive.canonical.com/dists/**$**/partner/binary-i386/Packages 404 Not Found [IP: 91.189.92.150 80]

W: Failed to fetch http://archive.canonical.com/dists/**$**/**(lsb_realese**/binary-i386/Packages 404 Not Found [IP: 91.189.92.150 80]

```
Its like it can't tell what release you're on cause it should be looking like this:
```
http://archive.canonical.com/dists/precise/binary-i386/Packages
```

---

### Post by Charlie_Smith on 2014-05-04
You guys are great! I will post a reply of the 
cat /etc/apt/sources.list

---

### Post by Charlie_Smith on 2014-05-04
```

# deb cdrom:[Ubuntu 12.04.4 LTS _Precise Pangolin_ - Release i386 (20140204)]/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted #Added by software-properties

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse #Added by software-properties

deb http://us.archive.ubuntu.com/ubuntu/ precise-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-security restricted main multiverse universe #Added by software-properties
deb http://us.archive.ubuntu.com/ubuntu/ precise-security universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
deb http://archive.canonical.com/ $ -sc) partner (lsb_realese
deb-src http://archive.canonical.com/ $ -sc) partner (lsb_realese
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner
deb http://us.archive.ubuntu.com/ubuntu/ precise-proposed restricted main multiverse
universe 
```

Is this right?

---

### Post by ibjsb4 on 2014-05-04
Open up your software sources and **UN**check sources.  Then do another update.

Should be good to go.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab)

---

### Post by Charlie_Smith on 2014-05-04
> **ibjsb4 said:**
> Open up your software sources and **UN**check sources.  Then do another update.

Should be good to go.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab)
I am still getting the Error during update message even after this, I think I need to crack some code...

---

### Post by ibjsb4 on 2014-05-04
Please post the sources list again, let me see what I missed.

---

### Post by Bashing-om on 2014-05-04
Charlie_Smith; Hi !

In passing by I note in your original sources.list file the following:
> 
deb [http://archive.canonical.com/](http://archive.canonical.com/) $ -sc) partner (lsb_realese
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) $ -sc) partner (lsb_realese


@ ibjsb4; Recon this is an invalid format for the indexing ?
As the 'partner' repository is already enabled: per:
> 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner


Might we not just remove the obfuscated lines, and all be good ?

Hey;
[INDENT][INDENT][INDENT]just my thought
[/INDENT][/INDENT][/INDENT]

---

### Post by ibjsb4 on 2014-05-04
I going offline and want to leave you with this (going by the first list)

Ok, so first make a backup.

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.broke
```

Then the sources.list needs to be edited

```
gksudo gedit /etc/apt/sources.list
```

This line needs to be commented (#) out.

deb [http://archive.canonical.com/](http://archive.canonical.com/) $ -sc) partner (lsb_realese

Put an # in front of that line to read

#deb [http://archive.canonical.com/](http://archive.canonical.com/) $ -sc) partner (lsb_realese

save and close and again update

---

### Post by ibjsb4 on 2014-05-04
Hi Bashing :D

Did not see your post, please feel free to step in as I am off to the store :)

---

