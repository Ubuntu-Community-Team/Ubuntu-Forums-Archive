---
title: "Updating from 13.04 raring ringtail"
date: 2015-07-13
forum: Installation &amp; Upgrades
---

### Post by andy139 on 2015-07-13
Hi There

I have a Linux hard drive which has been dormant for a couple of years. Am now trying to update it to a more recent version. Have read so far I need to point apt-get at different mirrors to make it work so have put my sources.list file towards old-releases:

```
# deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)]/ quantal main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.old-releases.ubuntu.com/ubuntu/ raring restricted
deb-src http://gb.old-releases.ubuntu.com/ubuntu/ raring restricted multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.old-releases.ubuntu.com/ubuntu/ raring-updates restricted
deb-src http://gb.old-releases.ubuntu.com/ubuntu/ raring-updates restricted multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.old-releases.ubuntu.com/ubuntu/ raring universe
deb http://gb.old-releases.ubuntu.com/ubuntu/ raring-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.old-releases.ubuntu.com/ubuntu/ raring multiverse
deb http://gb.old-releases.ubuntu.com/ubuntu/ raring-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.old-releases.ubuntu.com/ubuntu/ raring-backports restricted universe multiverse
deb-src http://gb.old-releases.ubuntu.com/ubuntu/ raring-backports restricted universe multiverse #Added by software-properties

deb http://old-releases.ubuntu.com/ubuntu raring-security restricted
deb-src http://old-releases.ubuntu.com/ubuntu raring-security restricted multiverse universe #Added by software-properties
deb http://old-releases.ubuntu.com/ubuntu raring-security universe
deb http://old-releases.ubuntu.com/ubuntu raring-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu quantal partner
# deb-src http://archive.canonical.com/ubuntu quantal partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu raring main
deb-src http://extras.ubuntu.com/ubuntu raring main
```


However I now get GPG errors when I try to run apt-get update.

```
sudo apt-get update
Get:1 http://gb.old-releases.ubuntu.com raring Release.gpg
Ign http://extras.ubuntu.com raring Release.gpg                      
Hit http://old-releases.ubuntu.com raring-security Release.gpg                      
Ign http://extras.ubuntu.com raring Release                                         
Hit http://old-releases.ubuntu.com raring-security Release                          
Get:2 http://gb.old-releases.ubuntu.com raring-updates Release.gpg    
Hit http://old-releases.ubuntu.com raring-security/restricted Sources
Hit http://old-releases.ubuntu.com raring-security/multiverse Sources               
Get:3 http://gb.old-releases.ubuntu.com raring-backports Release.gpg                
Hit http://old-releases.ubuntu.com raring-security/universe Sources                                       
Hit http://old-releases.ubuntu.com raring-security/restricted amd64 Packages                              
Get:4 http://gb.old-releases.ubuntu.com raring Release                              
Ign http://gb.old-releases.ubuntu.com raring Release                                                                     
E: GPG error: http://gb.old-releases.ubuntu.com raring Release: The following signatures were invalid: NODATA 1 NODATA 2 
```

Searching forums has run dry at this point, not sure what I need to do to get the right keys!

Any help much obliged.

Andy

---

### Post by howefield on 2015-07-13
To be honest, I'd go with a clean install to either 14.04 or 15.04 depending on how you feel about LTS vs interim releases :) Presumably you have a reason for not going that route ?

---

### Post by andy139 on 2015-07-13
Yes would obviously mean reinstalling a fair bit of older stuff. Is there not a realistic quick fix here? Definitely going with LTS!!

If it is going to mean days of faffing around to get me to 14.04 then would probably do a clean install. Otherwise best to find a workaround.

---

### Post by howefield on 2015-07-13
It's not so much the faffing around that would put me off, just the time involved and the potential for cruft and failed upgrades :)

Have you gone through this page,.. [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Check out the sources.list example...

---

### Post by andy139 on 2015-07-13
Yes sources list should be ok. Just seems to have issues verifying the signatures. Apt-get seems to be generally struggling to do anything, presumably because it is quite out of date. Seems odd that I should be stuck here. It isn't *that* old a version.

Tried the line in the article:

sudo aptitude install update-manager-core update-manager

Comes back command not found. Doesn't seem to have any spelling or case issues.

---

### Post by kansasnoob on 2015-07-13
Even if everything worked OK (which it's obviously not) you would first have to upgrade 13.04 to 13.10 which has also reached EOL already:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Then immediately after that you'd have to upgrade 13.10 to 14.04. Based on my own experience you'd be looking at a minimum of 6 to 7 hours of upgrading ***even if things worked perfectly***.

---

### Post by deadflowr on 2015-07-14
I'm not sure there are any old-release repos other than pure *old-releases.ubuntu.com*.
Never seen any instances like *gb.old-releases.ubuntu.com*.

If I remember right, running the command with *us.old-releases.ubuntu.com* caused errors as well...

---

### Post by howefield on 2015-07-14
> **deadflowr said:**
> I'm not sure there are any old-release repos other than pure *old-releases.ubuntu.com*.

+1 I think this is the issue, hence the request for the op to check the sources.list example.

It's checkable in the browser where old.releases.com resolves correctly whereas prepending with gb doesn't.

---

### Post by andy139 on 2015-07-14
Aha, GB server is indeed wrong. Thanks for pointing out.

The only issue I get now is the last two lines in sources.list

I get the following error when I run sudo apt-get update

```

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/raring/main/source/Sources  404  Not Found [IP: 91.189.92.152 80]

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/raring/main/binary-amd64/Packages  404  Not Found [IP: 91.189.92.152 80]

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages  404  Not Found [IP: 91.189.92.152 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

I have tried editing the file in nano to comment these out. Am I right in thinking I don't actually need them until later? The file just overwrites however and returns the same error. Is there a way to comment out lines in sources.list that will stay put?

One more try this evening then I'm reformatting!

Thanks for the continued help

Andy

---

### Post by deadflowr on 2015-07-14
You need to also disable those "extras" repositories.
Unlike the regular repos which get moved to the old-release archive.
The extras repos simply die away.

---

