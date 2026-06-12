---
title: "Upgrade Error"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by ersuforum on 2010-04-30
I'm trying to do an online upgrade from 8.04 to 10.04 using the update manager.  Since update manager did not indicate that there was and upgrade, I used the update-manager --devel-release command to initiate the process.  The upgrade stops during while looking for channels with the following error message:

A problem occurred during the update. This is usually some sort of 
network problem, please check your network connection and retry. 

W:Failed to fetch 
[http://archive.ubuntu.com/ubuntu/dists/lucid-backports/Release](http://archive.ubuntu.com/ubuntu/dists/lucid-backports/Release) Unable 
to find expected entry main/debian-installer/binary-i386/Packages in 
Meta-index file (malformed Release file?) 
, E:Some index files failed to download, they have been ignored, or 
old ones used instead. 

I don't believe this to be a network problem because it fails in the same place every time.  I don't see the entry for debian-installer in the Release file which I believe is why the error is occuring, however, I'm not sure what to do about it.  It seems like something is pointed to the wrong place.

I've maintained this system with update-manager for several years and never had a problem. 

Thanks for any help you can give.

ers

---

### Post by ersuforum on 2010-05-01
I'm still struggling with the error listed below during an LTS upgrade from hardy to lucid. I didn't get a response but I've been doing some digging on my own.  As mentioned previously, I'm using update-manager --devel-release to initiate an online upgrade. After hitting the upgrade button the first step "preparing for upgrade" completes successfully.  The next step "Setting New Software Channels" is where the error below occurs.  After the error, the process cleans up and stops.

ERROR
W:Failed to fetch 
[http://archive.ubuntu.com/ubuntu/dists/lucid-backports/Release](http://archive.ubuntu.com/ubuntu/dists/lucid-backports/Release) Unable 
to find expected entry main/debian-installer/binary-i386/Packages in 
Meta-index file (malformed Release file?) 
, E:Some index files failed to download, they have been ignored, or 
old ones used instead. 

I'm wondering if my sources.list might be the source of the problem.  It is shown below:

#
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-backports restricted main multiverse universe
**deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-backports main/debian-installer**

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

I've tried to bold the line above that contains debian-installer to highlight it as my suspect line. As I understand, the update manager will change "hardy" to "lucid" in sources.list as part of the upgrade process.  In hardy, the sources.list line with debian-installer references something that is listed in the backports Release file.  The debian-installer is not listed in the lucid backports Release file.  Thus, I believe this may be the source of the above error.

Can someone tell me if my sources.list might be causing the above error and if so, what is the correct way to modify the file to allow my upgrade to proceed successfully. Should I delete the debian-installer line or modify to point to a different repository?  Do I need this line in sources.list?  Or, am I barking up the wrong tree?

 Thanks for your help.  I'm looking forward to getting lucid up and running.  There are several packages in lucid I want to try out.

---

