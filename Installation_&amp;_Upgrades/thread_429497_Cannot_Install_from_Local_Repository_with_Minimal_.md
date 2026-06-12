---
title: "Cannot Install from Local Repository with Minimal CD"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by BadServo on 2007-05-01
I recently set up an Ubuntu repository inside the company LAN to speed up updates and installs.  The repository seems to be working fine for updates, but I cannot seem to perform a network install from it.

I'm booting off of the Feisty Minimal CD and manually specifying the address of the server (feistyrepo).  I'm leaving the Ubuntu archive mirror directory at it's default of /ubuntu/.

The server itself is running Feisty Fawn Desktop i386.  The repo was created using apt-mirror & apache2.  The path to the mirror on the server is /var/spool/apt-mirror/mirror/ under which is the archive.ubuntu.com folder and so on.

/var/www/ contains a symlink pointing to /var/spool/apt-mirror/mirror/archive.ubuntu.com/ubuntu/.

The installer consistently give me the following error:

"The installer failed to download a file from the mirror.  This may be a problem with your network , or with the mirror.  You can choose to retry the download, select a different mirror, or cancel and choose another installation meathod."

Any help would be greatly appreciated.

---

### Post by BadServo on 2007-05-01
OK, I made some progress.  managed to get the installer to see the repository and begin the installation.  Everything works up until the point that the base packages are downloaded and installed.

Several packages come down, and then I get an error sayign that the following packages cannot be downloaded:

python
python-minimal
python2.5
python2.5-minimal

The installer then halts.  Any ideas?

---

### Post by BadServo on 2007-05-03
I have new information....

The apt-mirror clean scripts appear to be breaking my repo's packages.  I can update the repo with apt-mirror, then run the clean.sh script.  It was always identify 328MB to be removed.  if I then attempt to install Ubuntu from teh local repo, it will be unable to locate the python files.  If I then re-run apt-mirror, it will download 328MB.  If I then attempt an install WITHOUT having run the clean script it works flawlessly.

I have no idea why the cleanup would remove valid packages but would love some advice.

---

### Post by YogeshD on 2007-05-03
Hi ,

Congr8s ,you are two steps ahead .. :) 

I am using following mirror.list file and able to replicate the mirror ( not sure).
#########
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) feisty-updates main restricted 
########
During network installation it gives me "Downloading file fail " message for libc6 and libnewt.

I wan to install  feisty over the  network . Please correct if  i am wrong any where.

Thanks,
Yogesh

---

### Post by BadServo on 2007-05-08
Here's what I'm using in my own mirror.list.  Provided I don't run the clean.sh script I can net install without issue.

```
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty main/debian-installer
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty restricted/debian-installer
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
```

I think the "debian-installer bit is the key".

---

### Post by BadServo on 2007-05-08
New issue today.

Suddenly, I'm getting the following error when refreshing Update Manager on my clients:

> W: GPG error: [http://feistyrepo](http://feistyrepo) feisty-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

Any ideas?

---

