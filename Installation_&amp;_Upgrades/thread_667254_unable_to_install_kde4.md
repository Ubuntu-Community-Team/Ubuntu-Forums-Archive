---
title: "unable to install kde4"
date: 2008-01-14
forum: Installation &amp; Upgrades
---

### Post by jayramj on 2008-01-14
Hello,

I am trying to install kde4 on my kubuntu machine but unable to do so

Here is the error I get

  kde4-core: Depends: kdebase-kde4 (>= 4:4.0.0) but it is not going to be installed
             Depends: kdebase-runtime (>= 4:4.0.0) but it is not going to be installed
             Depends: kdebase-workspace (>= 4:4.0.0) but it is not going to be installed
             Depends: kdelibs5 (>= 4:4.0.0) but it is not going to be installed
             Depends: kdepimlibs5 (>= 4:4.0.0) but it is not going to be installed


Thanks for all your help

Regards
Jayram

---

### Post by PmDematagoda on 2008-01-14
Do you, by any chance, already have a previous version of KDE4 installed?

---

### Post by jayramj on 2008-01-14
As far as I know, I dont.

I have tried to install kde 4 couple of times but failed every time.

---

### Post by PmDematagoda on 2008-01-14
Did you try:-
```
sudo aptitude install kde4-core
```
or
```
sudo aptitude install kde4
```

---

### Post by jayramj on 2008-01-14
Tried doing as instructed. Attached file contains error log

---

### Post by Topsiho on 2008-01-14
I installed the core of KDE4.0.0 following the attached instructions, with no apparent problem. I have not note who is the author but I guess I got them from this forum :)

From your text I gather that dependencies are **older** files than those that are on your computer, so they are not met, and thus broken.
And later in the files it is stated that those dependencies are NOT broken, after which the install aborts.

---

### Post by Topsiho on 2008-01-14
I do not see the attachment that I added so I give the instructions here:

This tutorial will install KDE 4.0 alongside your current installation so you should still be able to revert if you run into problems.
This tutorial is based on Ubuntu Geeks KDE 4.0 guide and the KDE 4.0 guide at Kubuntu.org.

Installing KDE 4.0

First of all we need to update the repository sources list to pull these new KDE 4.0 packages from the kubuntu team PPA (Personal Package Archive). We do that by editing the /etc/apt/sources.list file:

sudo vim /etc/apt/sources.list

You’ll want to then append this line:

deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) gutsy main

(The above should be on one line.) We’re now ready to install the KDE 4.0 packages:

sudo aptitude update
sudo aptitude install kde4-core

Removing Previous KDE 4.0 Releases

Note: do make sure you remove any previous KDE 4.0 installations you may have been playing with. The previous packages can have conflicts with this newer release from the PPA.
To remove previous KDE 4.0 packages, use the command:

sudo aptitude remove kdelibs5 kde4base-data kde4libs-data

You can now launch your newly added KDE 4.0 environment from the login manager by selecting KDE 4. Enjoy!

Topsiho

---

### Post by jayramj on 2008-01-14
hi topsiho,

Thanks for your reply

I had followed exactly the same instruction but still facing errors as mentioned earlier

---

### Post by chlorinekid on 2008-01-14
thanks for the info, worked a treat

---

### Post by jayramj on 2008-01-15
I followed the steps and finally got KDE4 installed

Now another problem. I am not able to load it. The splash screen at login shows all icons, then finally shows big KDE icon and then I am thrown back to the login screen

---

