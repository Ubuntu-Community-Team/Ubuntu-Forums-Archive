---
title: "Could not download all repository indexes"
date: 2010-06-20
forum: Installation &amp; Upgrades
---

### Post by mpolito1969 on 2010-06-20
I played a bit with the upgrade configuration files, to solve a couple of problems I have with Ubuntu 10.04, now when the upgrade procedure starts I get

> Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release)  Unable to find expected entry  multiversdeb/source/Sources in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

I made a quick search but didn't find anything useful.

Any help?

Ciao,
Max

---

### Post by swudee on 2010-06-20
Hi

I had a similar problem a while back.
I found the easiest fix was to go to 

System/Administration/Software services

and untick all the boxes, close update sources and reopen it and retick the boxes. it removes and recreates the apt config files.

It should work for you

---

### Post by mpolito1969 on 2010-06-20
> **swudee said:**
> Hi

I had a similar problem a while back.
I found the easiest fix was to go to 

System/Administration/Software services

and untick all the boxes, close update sources and reopen it and retick the boxes. it removes and recreates the apt config files.

It should work for you

I unticked all the sources, made a "reload" (as suggested by the application) and had tehe message.

> Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release)  Unable to find expected entry  multiversdeb/source/Sources in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

Went back to the same application, re-ticked all the checkboxes, reloaded and had again

> Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release)  Unable to find expected entry  multiversdeb/source/Sources in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by swudee on 2010-06-20
Perhaps try doing the update with the multiverse repository unticked an see what happens, is it just the one archive having the problem? or maybe it is a problem at your local repository that will clear in a day or so.

---

### Post by mpolito1969 on 2010-06-20
> **swudee said:**
> Perhaps try doing the update with the multiverse repository unticked an see what happens, is it just the one archive having the problem? or maybe it is a problem at your local repository that will clear in a day or so.

It's the same.

Let's wait for a couple of days...

Ciao,
Max

---

### Post by mpolito1969 on 2010-06-22
Everything is just like before...

---

### Post by swudee on 2010-06-23
Hi

This is my /etc/apt/sources.list   of course it is the New Zealand repos.


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) lucid main restricted multiverse
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) lucid-updates main restricted multiverse
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner

If you have a Lucid CD you could fire it up and copy the file from there.

David

---

### Post by mpolito1969 on 2010-06-25
Mine is very different, I only have this uncommented:

> 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiversdeb


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main universe restricted multiverse

Where can I download the "original" file that I had on my system right after the installation?

Ciao,
Max

---

### Post by mpolito1969 on 2010-07-04
Is there anybody that can copy here the "good" file? The one I got after a fresh installation of Ubuntu 10.04?

Ciao,
Max

---

### Post by Elfy on 2010-07-04
You can create one from here if you wish

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by mpolito1969 on 2010-07-04
It's a bit difficult... do you know what should I check to have the "original" file?

Ciao,
Max

---

