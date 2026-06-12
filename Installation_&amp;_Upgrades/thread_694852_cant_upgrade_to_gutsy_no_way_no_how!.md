---
title: "cant upgrade to gutsy no way no how!"
date: 2008-02-12
forum: Installation &amp; Upgrades
---

### Post by curtk69 on 2008-02-12
i have tried every thing.
1.  i downloaded gutsy and tried new installs and get DISK BOOT ERRORS shorty after the screen says loading linux kernel.  incidently i also have problems installing OSX86 from burned disks. it always hangs on lasr second of install.  is there special bios settings besides boot options that need to be changed for linux or osx installs/?
WHATS THE PROBLEM HERE?

2. i try to  automatic upgrade and it hangs and or gets errors and fails to upgrade.

3. i try to change repository and get errors like COULD NOT  DOWNLOAD ALL REPOSITORY INDEXES or 

automatix duplicate sources, blah blah bla and GPG ERROR PUBLIC KEY NOT AVAILABLE

This seems to happen whether i choose main server, custom server or test for best server  and end up with one in usa even though i from canada and cant even choose the greyed out option for canada?

---

### Post by taurus on 2008-02-12
1.  At the first boot screen, there is am option to scan disc for defects.  Have you tried to see if there is anything wrong with the CD?

2.  Post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

3.  If you use automatix, you won't be able to upgrade.  So, if you want to upgrade from Feisty to Gutsy, you NEED to remove all those repos that automatix added to your /etc/apt/sources.list.

---

### Post by Pandemic187 on 2008-02-12
Yeah, based on your first issue it sounds like you are either using bad CDs or the drive itself is bad. That or you're burning at too high a speed.

---

### Post by curtk69 on 2008-02-12
i beleive i tried checking disk for errors at first bootup but it was after it not installing so it may have already been hung up.

i do have automatix installed.
how do i uninstall it and everything it did?
i forget what automatix was for? windows medi codecs etc?

if i uninstall automatix and everyting it did , how much functionality will my computer lose in case the upgrade still fails?

doesnt everyone install automatics to have a completely functional operating system that does everything windows does?  [ except gaming]

---

### Post by curtk69 on 2008-02-12
curt@curt-ubuntu:~$ cat /etc/apt/sources.list

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

#AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) edgy main

deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe multiverse
#AUTOMATIX REPOS END
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
curt@curt-ubuntu:~$

---

### Post by taurus on 2008-02-12
> **curtk69 said:**
> curt@curt-ubuntu:~$ cat /etc/apt/sources.list

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

#AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) edgy main

deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe multiverse
#AUTOMATIX REPOS END
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
curt@curt-ubuntu:~$

No wonder you butcher your machine!  You have both edgy and feisty repos in your /etc/apt/sources.list which is not a good idea.  If you use edgy, include only edgy repos.  And if you are running feisty, include only feisty repos.  

And if you need codecs, then use this guide, [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats).

---

### Post by curtk69 on 2008-02-12
well this is already an upgrade from edgey to fesity and if i recall some 6 -8 months ago when i upgraded i remember havin  trouble then too.
cant remeber how i finally fixed it

so what should i do?

if i had a  easy way to backup all my emails saved to this install i wouldnt hesitate to wipe clean and start over but like i said i cant even do that

---

### Post by curtk69 on 2008-02-12
one of the problems could be a dvd burner problem
its a 2 yr old liteon , was probly only a 4x or maybe 8x burner and now burns at 16x automatically even tho i am pretty i havent upgraded my firmware but i have a bad memeory and work on lots on computers so maybe i did.

can i upgrade the firmware in ubuntu? or should this only be done in windows?

---

### Post by curtk69 on 2008-02-12
i checked and  my dvd liteon burner has newest firmware

---

### Post by Partyboi2 on 2008-02-12
You could move your home folder to its own partition then reinstall clean.
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

