---
title: "Adept Package Manager Problem."
date: 2007-12-31
forum: Installation &amp; Upgrades
---

### Post by ti1ion on 2007-12-31
I have noticed a problem with Adept that I would like to get help resolving.  I am running Kubuntu 7.10, upgraded from 7.04.  At first, Adept worked fine.  Now, when I try to install or remove packages I get a commit error.  Packages are neither installed, nor removed.  Looking around for help I found some commands to run and discovered the following:

Running sudo apt-get install, or sudo apt-get install -f gives me:

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  librsvg2-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


So, running sudo apt-get autoremove gives:

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  librsvg2-common
The following packages will be REMOVED:
  librsvg2-common
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 160kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... dpkg: error processing librsvg2-common (--remove):
 files list file for package `libapm1' is missing final newline
Errors were encountered while processing:
 librsvg2-common
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)


Now, I may be wrong, but I am thinking this is the source of my commit errors.  So, I would like assistance on safely forcing the system to remove this librsvg2-common package, or any other advice to fix the problem.

Thank you.

---

### Post by PmDematagoda on 2007-12-31
Execute:-
```

sudo apt-get update
```

Then see if that solves your problem.

---

### Post by ti1ion on 2007-12-31
I should have mentioned I did that first.

The commands I ran were:

sudo apt-get update
sudo apt-get install
sudo dpkg --configure -a

Still can't remove librsvg2-common.

---

### Post by steveneddy on 2008-01-01
The last time this happened to me I had to reinstall.

Hope you don't fall to the same fate.

---

### Post by Partyboi2 on 2008-01-01
Maybe this might help
[http://ubuntuforums.org/showpost.php?p=1635843&postcount=9](http://ubuntuforums.org/showpost.php?p=1635843&postcount=9)

---

### Post by Pumalite on 2008-01-01
You might want to try:
sudo dpkg --remove --force-remove-reinstreq <packagename>
sudo apt-get update
sudo apt-get upgrade

---

### Post by ti1ion on 2008-01-01
Thanks for the replies.

"sudo dpkg --remove --force-remove-reinstreq librsvg2-common" gave me:

(Reading database ... dpkg: error processing librsvg2-common (--remove):
 files list file for package `libapm1' is missing final newline
Errors were encountered while processing:
 librsvg2-common
Processing was halted because there were too many errors.

So, that did not work.  I am trying the other suggested solution.

---

### Post by Pumalite on 2008-01-01
Try:
sudo apt-get remove --purge <packagename>

---

### Post by bapoumba on 2008-01-01
Can you try:
```
sudo dpkg --remove --force-remove-reinstreq libapm1
```
Looks to me this is the package with problems, not librsvg2-common.

---

### Post by ti1ion on 2008-01-01
Partyboi2, thank you for the link.

The solution provided fixed the problem.  Adept now works and installed an update.  However, if I bring back my old info folder (after backing it up), I get the problem again.  So, I have left the new, empty info folder in place and the old info folder is still renamed.  Now, am I going to have problems because I don't have all the package information from my old info folder?

---

### Post by ti1ion on 2008-01-01
Bapoumba,

Interesting point.

sudo dpkg --remove --force-remove-reinstreq libapm1

dpkg: dependency problems prevent removal of libapm1:
 apmd depends on libapm1 (>= 3.2.0-7).
dpkg: error processing libapm1 (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 libapm1

---

### Post by bapoumba on 2008-01-01
I'm looking. What is your sources.list?
```
cat /etc/apt/sources.list
```

---

### Post by ti1ion on 2008-01-02
Bapoumba,

If you are still monitoring this thread, here is the sources.list:

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

##Medibuntu - Ubuntu 7.04 "feisty fawn"
# deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free non-free deb-src
# deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free non-free


# deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main multiverse universe
#AUTOMATIX REPOS END

Thanks.

---

### Post by bapoumba on 2008-01-02
I would keep only basic gutsy repos. Please backup the file:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_bak
```

You can edit the file with nano, a small text editor:
```
sudo nano /etc/apt/sources.list
```

Remove all these lines, from the feisty medibuntu down. You can add medibuntu repos for gutsy after, once everything is straighten up:
```
##Medibuntu - Ubuntu 7.04 "feisty fawn"
# deb http://medibuntu.sos-sts.com/repo/ edgy free non-free deb-src
# deb-src http://medibuntu.sos-sts.com/repo/ edgy free non-free


# deb http://www.getautomatix.com/apt feisty main

#AUTOMATIX REPOS START

deb http://www.getautomatix.com/apt gutsy main

deb http://archive.canonical.com/ubuntu gutsy partner

deb http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu gutsy-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main multiverse universe
#AUTOMATIX REPOS END
```

Save the file: CTRL-O (same name, hit <enter>)
Exit nano: CTRL-X

```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by ti1ion on 2008-01-04
Bapoumba,

Thanks for your help.  I removed the feisty entries for medibuntu and the automatix entries.  I am not sure if that did anything, but there was nothing to upgrade once the change was made.

It seems that once I followed the instructions for removing the entries for the librsvg2-common package in the status file and then cleared the info file, everything went back to normal.  I was even able to use adept to remove libapm1 and then re-install it.  I was also able to remove and re-install the librsvg2-common package.

I don't know what effect having a new info file will have, but everything is working now.

---

### Post by bapoumba on 2008-01-05
Glad to see you got it to work :)

---

