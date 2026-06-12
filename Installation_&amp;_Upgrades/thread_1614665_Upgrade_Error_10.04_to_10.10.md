---
title: "Upgrade Error 10.04 to 10.10"
date: 2010-11-05
forum: Installation &amp; Upgrades
---

### Post by brianw0667 on 2010-11-05
I receive the following error consistently when I attempt to upgrade from 10.04 to 10.10 even though my system is up to date.  The network connection is good and this happens over and over at exactly the same point.


Error during update 

A problem occurred during the update. This is usually some sort of 
network problem, please check your network connection and retry. 

W:Failed to fetch 
[http://archive.canonical.com/ubuntu/dists/maverick-updates/Release](http://archive.canonical.com/ubuntu/dists/maverick-updates/Release) 
Unable to find expected entry restricted/binary-i386/Packages in 
Meta-index file (malformed Release file?) 
, W:Failed to fetch 
[http://archive.canonical.com/ubuntu/dists/maverick-security/Release](http://archive.canonical.com/ubuntu/dists/maverick-security/Release) 
Unable to find expected entry restricted/binary-i386/Packages in 
Meta-index file (malformed Release file?) 
, E:Some index files failed to download, they have been ignored, or 
old ones used instead.

---

### Post by Der Ritter on 2010-11-05
> **brianw0667 said:**
> I receive the following error consistently when I attempt to upgrade from 10.04 to 10.10 even though my system is up to date.  The network connection is good and this happens over and over at exactly the same point.


Error during update 

A problem occurred during the update. This is usually some sort of 
network problem, please check your network connection and retry. 

W:Failed to fetch 
[http://archive.canonical.com/ubuntu/dists/maverick-updates/Release](http://archive.canonical.com/ubuntu/dists/maverick-updates/Release) 
Unable to find expected entry restricted/binary-i386/Packages in 
Meta-index file (malformed Release file?) 
, W:Failed to fetch 
[http://archive.canonical.com/ubuntu/dists/maverick-security/Release](http://archive.canonical.com/ubuntu/dists/maverick-security/Release) 
Unable to find expected entry restricted/binary-i386/Packages in 
Meta-index file (malformed Release file?) 
, E:Some index files failed to download, they have been ignored, or 
old ones used instead.

Open up /etc/apt/sources.list and comment them out or remove them entirely. See if you can upgrade then. As far as I can tell there aren't any packages at either location, so you shouldn't miss anything by removing them.

---

### Post by brianw0667 on 2010-11-06
Thanks for the reply.  I checked but they are not part of the sources.list file they are part of the packages automatically added while performing the upgrade (and removed when upgrade fails and the original sources.list file is put back into place).

The first one is .../maverick-updates/Release. the second is .../maverick-security/Release
maverick is the distribution that I am attempting to upgrade to.

Maybe it was a problem last night. I will try again when I get home tonight.

---

### Post by brianw0667 on 2010-11-06
Tried to do the upgrade again but got the same error. Not sure where to go from here.

---

### Post by brianw0667 on 2010-11-10
Changed servers and had no problems.  Not sure which server I had set first but everything upgraded after changing the server.

---

