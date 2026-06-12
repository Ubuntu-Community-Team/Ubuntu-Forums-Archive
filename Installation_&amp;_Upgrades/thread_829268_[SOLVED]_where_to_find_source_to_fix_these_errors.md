---
title: "[SOLVED] where to find source to fix these errors?"
date: 2008-06-14
forum: Installation &amp; Upgrades
---

### Post by upchucky on 2008-06-14
Hello there,
I am trying to upgrade my 7.04 to 7.11, the following errors are stopping the upgrade.

I am assuming that I need to add some new repositories but where do i find them if this is true?

I found a link that was posted for this very problem, but the web site it directs to has not been available for about a year.

and if they are new repositories why does the Ubuntu update not automatically use them?





Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.bz2) Sub-process bzip2 returned an error code (2)

---

### Post by avtolle on 2008-06-14
One question: are you running the ppc version? I ask this due to a change in the repositories which is not necessarily automatically picked up by the update manager. Otherwise, I'll be back in a bit with a link that might be helpful.

---

### Post by avtolle on 2008-06-14
[https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades) may help you if you are not caught in the ppc change thing, and are on i386 (32 bit version).

EDIT: Perhaps the most important thing is to get the 7.04 totally updated before proceeding, which is maybe what you were trying to do.

---

### Post by upchucky on 2008-06-14
I did the 7.04 update just before trying to do the upgrade to 7.10, it went fine no errors.

I do not know what the ppc change is that u have mentioned.

I am running i386, nvidia graphics, and beryl on this sys.

I am getting a bit better at commandline stuff, i did this,

cat /etc/apt/sources.list  

and got this,

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
#######################################################################################
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted universe multiverse
## LG3D repsoitories
# deb [http://javadesktop.org/lg3d/debian](http://javadesktop.org/lg3d/debian) stable contrib
# deb [http://javadesktop.org/lg3d/debian](http://javadesktop.org/lg3d/debian) testing contrib
# deb [http://javadesktop.org/lg3d/debian](http://javadesktop.org/lg3d/debian) unstable contrib

but nothing is jumping out at me as a possible problem.

Thanks for the quick replies.

---

### Post by upchucky on 2008-06-14
k just figured out that I am not on a ppc version.

what is next?

---

### Post by avtolle on 2008-06-14
Don't worry about the ppc changes; I just wanted to be sure you were not on that platform (I am), as things really were bollixed a bit until it all sorted.

Nothing is jumping out at me, either, but another set of eyes might find something instanter.

---

### Post by avtolle on 2008-06-14
Hmm, I wonder whether doing this from the command line will give us any other information```
sudo aptitude update && sudo aptitude dist-upgrade
```

Give that a try, and post error messages (if any) you get.

---

### Post by upchucky on 2008-06-14
ok we are gettin closer, 

apt-get update in terminal produced several instances of the following, all the errors are referencing the same package (stdin) and say it is not a bzip2 file


if i can figure out what package (stdin) is from and remove it then i think I can upgrade, then re-install the package later if i really need it.

what is your opinion?



Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages [96.0kB]                                                                                       
99% [7 Packages bzip2 0] [Waiting for headers] [Waiting for headers] [Waiting for headers]                                                           63B/s 0sbzip2: (stdin) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                                                                                                  
  Sub-process bzip2 returned an error code (2)

---

### Post by avtolle on 2008-06-14
You DO NOT want to be messing around with stdin. The problem is not with that anyway, it is with the file from the security repo itself. (stdin) is reporting that the file is not a proper bzip2 file. 

Looks like there's some corrupted, for lack of a better term, files on that repository.

---

### Post by avtolle on 2008-06-14
(Winding up for a long shot): OK, have we discussed trying this? In your software sources, changing the server from US to Main or, thinking out loud, clicking on the drop down list in Download from: appears (where the name of your current server is listed), selecting "Other", and then asking for the package to find the Best one (click on the bar). After it checks around a bit, the name of one will come up, so use that one (I'm operating from memory a bit here), then reload the sources, and see what happens.

---

### Post by upchucky on 2008-06-14
ok changed sources from main to united states.
it did the apt-get update with no errors this time.

crossing me fingers that the upgrade to 7.10 works this time.

I may lose my nvidia settings on the upgrade so it may be a while to redo that.

In the meantime I thank you for your time and patience and will post my end results.

---

### Post by avtolle on 2008-06-14
> **upchucky said:**
> ok changed sources from main to united states.
it did the apt-get update with no errors this time.

crossing me fingers that the upgrade to 7.10 works this time.

I may lose my nvidia settings on the upgrade so it may be a while to redo that.

In the meantime I thank you for your time and patience and will post my end results.
Appreciate the update, and, as always, good luck. Will be interested to see the end results.

---

### Post by upchucky on 2008-06-14
Ok all seems to be fine now.

the upgrade made it all the way to where it is ready to start the download this time, but I have to wait until 03:00 am to do the actual upgrade as it is a 1025m download.

I am on a satellite system and my download threshold is cut off at 350m in a  twenty four hour period, except at 03:00 am it is wide open until 6 am.

---

### Post by avtolle on 2008-06-14
Set the alarm! Best of luck, I think we may have resolved this one.

---

### Post by upchucky on 2008-06-14
I found a dvd with 7.10 on it that i had tucked away, i made a new post to see if it could be used to upgrade my existing 7.04 install, can you look at the post and give opinion please?

---

