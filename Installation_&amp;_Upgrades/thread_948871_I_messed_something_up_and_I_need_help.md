---
title: "I messed something up and I need help"
date: 2008-10-15
forum: Installation &amp; Upgrades
---

### Post by DuxHuntin on 2008-10-15
I tried to install something that I thought was going to help me understand this new OS a lil better but I dont think it worked so I have sense deleted it but now when I try to check for updates I get this in the update-manager



   :Problem parsing dependency Depends, E:Error occurred while processing btnx (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'


Any ideas on how I can fix this?

---

### Post by anystupidname on 2008-10-15
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/278285](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/278285)

I'm afraid others have had this problem too so there is a bug filed. Unfortunately, short of suggesting you look around in your apt source lists, I don't have a solution for you.

---

### Post by cariboo on 2008-10-15
You have a spelling error in your sources.list. Please post your /etc/apt/sources.list in your next post.

Jim

---

### Post by DuxHuntin on 2008-10-15
Well I inadvertently fixed the problem it seems to be working fine now thanks for the help.
 

You have a spelling error in your sources.list. Please post your /etc/apt/sources.list in your next post.

Jim 




 Although just out of curiosity  how would I post that? Where would I get the info from?

---

### Post by anystupidname on 2008-10-16
You could open /etc/apt/sources.list with nano or kate or whatever your favorite text editor is and then copy and paste it into a post. I'm skeptical that the actual sources.list itself was the problem. But it wouldn't hurt to look.

---

### Post by cariboo on 2008-10-16
> :Problem parsing dependency Depends, E:Error occurred while processing btnx (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists_**harty**_all_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'


Check out the bolded word in the error message.

Like the previous poster said open /etc/apt/sources.list in your favorite text editor and paste  it into your next post, and please use the code tags to make it easier to read. The code tags are in the advanced editor, just click the # to use.

Jim

---

### Post by Nancy Dz on 2008-10-16
**RE:** > **anystupidname said:**
> I'm afraid others have had this problem too so there is a bug filed. Unfortunately, short of suggesting you look around in your apt source lists, I don't have a solution for you.
 
and

> **DuxHuntin said:**
> Well I inadvertently fixed the problem it seems to be working fine now thanks for the help.

Hey there DuxHuntin,

If you post how you were able to fix it others will know how to fix theirs since it seems to be a known bug.  :D

---

### Post by DuxHuntin on 2008-10-30
```
#deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
```



 I hope I did that right 


> Nancy Dz  	

RE:
Quote:
Originally Posted by anystupidname View Post
I'm afraid others have had this problem too so there is a bug filed. Unfortunately, short of suggesting you look around in your apt source lists, I don't have a solution for you.
and

Quote:
Originally Posted by DuxHuntin View Post
Well I inadvertently fixed the problem it seems to be working fine now thanks for the help.
Hey there DuxHuntin,

If you post how you were able to fix it others will know how to fix theirs since it seems to be a known bug. 


  I would love to help but when I said inadvertently I ment I have no idea what I did sorry I cant help

---

