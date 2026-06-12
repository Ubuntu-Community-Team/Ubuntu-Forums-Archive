---
title: "Parted and udisk won't update"
date: 2010-03-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by executorvs on 2010-03-09
There appears to be a conflict between the libparted packages used by ubuntu standard and parted and those needed for the updates of udisk and parted. has anyone else noticed this and is it worth filing a bug? I'm sure as the repos keep changing with package updates daily this sort of thing happens.

---

### Post by jppr on 2010-03-09
> **executorvs said:**
> There appears to be a conflict between the libparted packages used by ubuntu standard and parted and those needed for the updates of udisk and parted. has anyone else noticed this and is it worth filing a bug? I'm sure as the repos keep changing with package updates daily this sort of thing happens.

Update it synaptic

---

### Post by DoeRayMe on 2010-03-09
I went in Synaptic and chose to install libparted0 and it sorted the others out.

---

### Post by executorvs on 2010-03-09
That's what I did. I'm thinking the ubuntu-standard meta package needs to be updated/fixed as it's (I think) causing the conflict.

---

### Post by tcchris on 2010-03-09
I also installed libparted0 and it fixed .
It uninstalled two others

---

### Post by QwUo173Hy on 2010-03-10
I'm unsure if it's worth bugging, since we're mid development. But if it doesn't sort itself out by Beta1, I'll do a clean install then and I come across a similar problem on a subsequent update - I'll report it.

---

### Post by kansasnoob on 2010-03-10
I think it'll be fixed in Beta 1, look at todays daily manifest:

[http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.manifest](http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.manifest)

> libparted0 2.2-1ubuntu2

I'll pay extra special attention to that during iso testing and do some additional testing to follow up and see if I was right to mark this bug fix released:

[https://bugs.launchpad.net/ubuntu/+source/parted/+bug/510179](https://bugs.launchpad.net/ubuntu/+source/parted/+bug/510179)

I will add a note there that libparted failed to upgrade properly :)

On second thought I'll go ahead and zsync my Live CD.iso and burn a disc so I can check this out. Then I'll decide whether or not to file a new bug report.

Edit #2: this will have to wait until tomorrow because the .iso is oversize. The daily build site says it's 685MB but it's 718!!!!!!!!!!!!!

Oops??????????????

---

### Post by kansasnoob on 2010-03-12
Just now checked running the 03/12/2010 Live CD and it's OK so there probably is no need to file a bug report IMO.

---

### Post by QwUo173Hy on 2010-03-12
That's great. Thanks KN

---

### Post by Vanishing on 2010-03-12
this package was meant to be deleted i think..
[https://launchpad.net/ubuntu/lucid/i386/devicekit-disks](https://launchpad.net/ubuntu/lucid/i386/devicekit-disks)

---

### Post by QwUo173Hy on 2010-03-12
It's not installed on my system and I still have the update conflict.

---

### Post by kansasnoob on 2010-03-12
This is what I did to get mine working:

> Commit Log for Tue Mar  9 17:39:34 2010


Removed the following packages:
devicekit-disks
libparted-2.1-0
libparted1.8-12

Upgraded the following packages:
gparted (0.5.1-1ubuntu1) to 0.5.1-1ubuntu2
parted (2.1-4ubuntu1) to 2.2-1ubuntu2
udisks (1.0.0~git20100227.36c8a4-1) to 1.0.0~git20100305.fa313b2-1ubuntu1

Installed the following packages:
libparted0 (2.2-1ubuntu2)


So there should be no need to reinstall, unless you just want to :)

---

### Post by Vanishing on 2010-03-12
> **kansasnoob said:**
> This is what I did to get mine working:



So there should be no need to reinstall, unless you just want to :)

yup..all three packages listed above can be removed:
[https://launchpad.net/ubuntu/lucid/i386/libparted1.8-12](https://launchpad.net/ubuntu/lucid/i386/libparted1.8-12)
[https://launchpad.net/ubuntu/lucid/i386/libparted-2.1-0](https://launchpad.net/ubuntu/lucid/i386/libparted-2.1-0)
[https://launchpad.net/ubuntu/lucid/i386/devicekit-disks](https://launchpad.net/ubuntu/lucid/i386/devicekit-disks)

all of the status are marked as "Deleted"

---

### Post by QwUo173Hy on 2010-03-12
Kansasnoob / Vanishing - thank you very much!

---

### Post by Vanishing on 2010-03-12
> **jarlath said:**
> Kansasnoob / Vanishing - thank you very much!

no problem:popcorn:

---

### Post by executorvs on 2010-03-12
This may have resolved itself. I'm looking at which files are marked as dependent from ubuntu-standard to parted to libparted0 and it seems like the version numbers match up better now. has anyone looked at yesterdays or todays daily to check. I think the problem was just the repo packages being slightly out of sync.
EDIT:nevermind I'm blind and missed the deleted package comment.

---

### Post by kansasnoob on 2010-03-12
> **executorvs said:**
> This may have resolved itself. I'm looking at which files are marked as dependent from ubuntu-standard to parted to libparted0 and it seems like the version numbers match up better now. has anyone looked at yesterdays or todays daily to check. I think the problem was just the repo packages being slightly out of sync.
EDIT:nevermind I'm blind and missed the deleted package comment.

That's why I ran todays daily build:)

If it was still messed up I'd hoped to get it fixed before Beta 1, but it's fine now.

---

### Post by phillw on 2010-03-12
For some reason,

```
sudo apt-get update
sudo apt-get dist-upgrade
```

did not sort out the dependancy issue in this case, however

```
sudo aptitude update
sudo aptitude full-upgrade
```

does resolve it.

Guess I'll try the aptitude method next time apt-get has a problem although I'm not sure if that puts me into the 'partial update' warning category ?

Regards,

Phill.

---

