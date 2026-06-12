---
title: "Failed to fetch repository on upgrade/update (strange case)"
date: 2015-01-06
forum: Installation &amp; Upgrades
---

### Post by lucas-durand on 2015-01-06
I'm looking to update my Ubuntu 14.04 to 14.10, because I like to do that. I haven't been able to properly update headers in a while now (about a month). I've since reduced the repos I'm trying to update to what I believe to be the bare minimum -- just the main ubuntu repository. What I immediately am seeing as strange is the the update is looking for ```
main/binary-**i306**/Packages
``` in the Release file. This also appeared as an issue for about 10 other 3rd party repos that I use and halts any upgrade attempt. Is this the issue? How can I fix it? 

I've looked for this issue in multiple threads but none have been looking in the binary-1306 and seem to not have an error with the main repo .......

Here's the update -- 

```
sudo apt-get update
Ign http://ca.archive.ubuntu.com trusty InRelease
Hit http://ca.archive.ubuntu.com trusty Release.gpg
Hit http://ca.archive.ubuntu.com trusty Release
Hit http://ca.archive.ubuntu.com trusty/main Sources
Get:1 http://ca.archive.ubuntu.com trusty/main amd64 Packages [1,350 kB]
Fetched 1,350 kB in 4s (294 kB/s)                        
W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/trusty/Release  Unable to find expected entry 'main/binary-i306/Packages' in Release file (Wrong sources.list entry or malformed file)


E: Some index files failed to download. They have been ignored, or old ones used instead.



```

Here's the sources.list file --

> ##### Ubuntu Main Repos
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty main 
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty main 


Thanks for any help!

---

### Post by MAFoElffen on 2015-01-06
You received that error because a defsult install of Ubuntu has more than just main in the source list. If you have a package installed, the system is going to compare what is installed with what is current and try to bring that to current, whether you have a repo installed or not.

Looking at that mirror:
```

 10253b3b199e8a46ca8d5f6519037ecc              103 multiverse/source/Release
 cc40839b401c52259c842a19ce5b1f57           184141 restricted/binary-amd64/Packages
 ce1f8bec5381dd2e138231eb84ddf11a            15974 restricted/binary-amd64/Packages.gz
 201f8af37ae22eb13dee92945108361a              102 restricted/binary-amd64/Release
 f80e229c51be7e2c16ce70fb13053619            13028 restricted/binary-amd64/Packages.bz2
 835fc0235bfcaf3993f061835a9f2715              102 restricted/binary-arm64/Release
 e62ff0123a74adfc6903d59a449cbdb0               40 restricted/binary-arm64/Packages.gz
 4059d198768f9f8dc9372dc1c54bc3c3               14 restricted/binary-arm64/Packages.bz2
 d41d8cd98f00b204e9800998ecf8427e                0 restricted/binary-arm64/Packages
 4059d198768f9f8dc9372dc1c54bc3c3               14 restricted/binary-armhf/Packages.bz2
 e62ff0123a74adfc6903d59a449cbdb0               40 restricted/binary-armhf/Packages.gz
 849508d9260957987d315ddb19c626eb              102 restricted/binary-armhf/Release
 d41d8cd98f00b204e9800998ecf8427e                0 restricted/binary-armhf/Packages
 0091b45648917e7e1b2f3cf8daf3c33a            16421 restricted/binary-i386/Packages.gz
 28e2da9f9de2169e86761bf169a1085e           185074 [COLOR=#ffa07a]restricted[/COLOR]/[COLOR=#ff0000]binary-i386/Packages[/COLOR]
 597bd61f5dc069694e425070241bd2d9              101 restricted/binary-i386/Release
 791f8e0dacc967f0556506862b1792ec            13418 restricted/binary-i386/Packages.bz2
 4059d198768f9f8dc9372dc1c54bc3c3               14 restricted/binary-powerpc/Packages.bz2
 e62ff0123a74adfc6903d59a449cbdb0               40 restricted/binary-powerpc/Packages.gz
 d41d8cd98f00b204e9800998ecf8427e                0 restricted/binary-powerpc/Packages
 b563e3c8577589b0cdd7819c119e3f39              104 restricted/binary-powerpc/Release
 e62ff0123a74adfc6903d59a449cbdb0               40 restricted/binary-ppc64el/Packages.gz
 4059d198768f9f8dc9372dc1c54bc3c3               14 restricted/binary-ppc64el/Packages.bz2
 d41d8cd98f00b204e9800998ecf8427e                0 restricted/binary-ppc64el/Packages
 91fcac8bfd1f2d92b99d285e229aaa31              104 restricted/binary-ppc64el/Release
```
As you can see, that package is located in restricted, not main... so you would have to re-enable restricted to get past that error.

It's not a good idea to pare your repo's down like that. I see two options. Even if for some reason, someone decided they needed to, one that is missing and very important is security, that means if there were any vulnerabilities, you would not be getting any fixes or updates for those...

Option one-- From now on, run update / Upgrade from the commandline, but run a dry-run on the upgrade previous to running your live-run
```

sudo apt-get update && sudo apt-get upgrade -s

```
That "-s" simulate flag, will tell it to do a dry-run without downloads or changes... That will test that things will work or not. It puts it into a verbose mode and will tell you the errors. That would give you hints of what to add back in. Then add in as needed. To me, IMHO, would be a PITA, having to debug that over time.. Then for the live-run:
```

sudo apt-get upgrade

```
Option two is to go back to a default sources.list and be done with that.
```

# Note-- a default sources.list for utopic 14.10

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ [FONT=Verdana]utopic[/FONT][FONT=Verdana]-updates main restricted[/FONT]
deb-src http://us.archive.ubuntu.com/ubuntu/ [FONT=Verdana]utopic[/FONT][FONT=Verdana]-updates main restricted[/FONT]

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ [FONT=Verdana]utopic[/FONT][FONT=Verdana] universe[/FONT]
deb-src http://us.archive.ubuntu.com/ubuntu/ [FONT=Verdana]utopic[/FONT][FONT=Verdana] universe[/FONT]
deb http://us.archive.ubuntu.com/ubuntu/ [FONT=Verdana]utopic[/FONT][FONT=Verdana]-updates universe[/FONT]
deb-src http://us.archive.ubuntu.com/ubuntu/ [FONT=Verdana]utopic[/FONT][FONT=Verdana]-updates universe[/FONT]

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb http://us.archive.ubuntu.com/ubuntu/ [FONT=Verdana]utopic[/FONT][FONT=Verdana] multiverse[/FONT]
# deb-src http://us.archive.ubuntu.com/ubuntu/ [FONT=Verdana]utopic[/FONT][FONT=Verdana] multiverse[/FONT]
# deb http://us.archive.ubuntu.com/ubuntu/ [FONT=Verdana]utopic[/FONT][FONT=Verdana]-updates multiverse[/FONT]
# deb-src http://us.archive.ubuntu.com/ubuntu/ [FONT=Verdana]utopic[/FONT][FONT=Verdana]-updates multiverse[/FONT]

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ [FONT=Verdana]utopic[/FONT][FONT=Verdana]-backports main restricted universe multiverse[/FONT]
# deb-src http://us.archive.ubuntu.com/ubuntu/ [FONT=Verdana]utopic[/FONT][FONT=Verdana]-backports main restricted universe multiverse[/FONT]

deb http://security.ubuntu.com/ubuntu [FONT=Verdana]utopic[/FONT][FONT=Verdana]-security main restricted[/FONT]
deb-src http://security.ubuntu.com/ubuntu [FONT=Verdana]utopic[/FONT][FONT=Verdana]-security main restricted[/FONT]
deb http://security.ubuntu.com/ubuntu [FONT=Verdana]utopic[/FONT][FONT=Verdana]-security universe[/FONT]
deb-src http://security.ubuntu.com/ubuntu [FONT=Verdana]utopic[/FONT][FONT=Verdana]-security universe[/FONT]
deb http://security.ubuntu.com/ubuntu [FONT=Verdana]utopic[/FONT][FONT=Verdana]-security multiverse[/FONT]
deb-src http://security.ubuntu.com/ubuntu [FONT=Verdana]utopic[/FONT][FONT=Verdana]-security multiverse[/FONT]

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu [FONT=Verdana]utopic[/FONT][FONT=Verdana] partner[/FONT]
# deb-src http://archive.canonical.com/ubuntu [FONT=Verdana]utopic[/FONT][FONT=Verdana] partner[/FONT]

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu [FONT=Verdana]utopic[/FONT][FONT=Verdana] main[/FONT]
# deb-src http://extras.ubuntu.com/ubuntu [FONT=Verdana]utopic[/FONT][FONT=Verdana] main[/FONT]
```

---

### Post by lucas-durand on 2015-01-07
Thanks for your reply. Unfortunately this doesn't quite solve my issues.

1. I returned to using a default sources.list file. I was just showing the pared down one in order to demonstrate the error which pops up for many repositories and causes the release upgrade to fail (as the apt-get update fails for some key repos)
2. I went through and did a full upgrade, that was no problem.

Where I am now is that when running an update or (what I really want) a do-release-upgrade I get:

```
Error during update 

A problem occurred during the update. This is usually some sort of 
network problem, please check your network connection and retry. 


W:Failed to fetch 
http://ca.archive.ubuntu.com/ubuntu/dists/utopic/Release Unable to 
find expected entry 'main/binary-i306/Packages' in Release file 
(Wrong sources.list entry or malformed file) 
, W:Failed to fetch 
http://ca.archive.ubuntu.com/ubuntu/dists/utopic-security/Release 
Unable to find expected entry 'main/binary-i306/Packages' in Release 
file (Wrong sources.list entry or malformed file) 
, W:Failed to fetch 
http://ca.archive.ubuntu.com/ubuntu/dists/utopic-updates/Release 
Unable to find expected entry 'main/binary-i306/Packages' in Release 
file (Wrong sources.list entry or malformed file) 
, E:Some index files failed to download. They have been ignored, or 
old ones used instead. 




Restoring original system state


Aborting



```

or 

```

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/trusty/Release  Unable to find expected entry 'main/binary-i306/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/trusty-security/Release  Unable to find expected entry 'main/binary-i306/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/trusty-updates/Release  Unable to find expected entry 'main/binary-i306/Packages' in Release file (Wrong sources.list entry or malformed file)


E: Some index files failed to download. They have been ignored, or old ones used instead.



```


I'm quite confused as to what the **binary-i306** refers to .... is this in reference to the system architecture? Should it read **i386** or **amd64**?? Looking at the mirror you posted there is no listing for **binary-i306** and that would suggest that is why the update is unable to find the files at that location and fails. 

I've seen this problem before on these forums with the installation of programs in which the architecture is defined incorrectly through some --architecture= tag (i.e. someone writes --architecture=i3866 or some nonsense) and the solution was to uninstall and reinstall the program with the correct or default architecture, but in my case this error is coming on the default Ubuntu repos/source files which is worrying.

Does this mean something core in the OS is corrupted? Do I need to make a clean install?

---

### Post by MAFoElffen on 2015-01-09
> **lucas-durand said:**
> 
```

(Wrong sources.list entry or malformed file) 
(Wrong sources.list entry or malformed file) 
(Wrong sources.list entry or malformed file) 

```
or 
```

(Wrong sources.list entry or malformed file)
(Wrong sources.list entry or malformed file)
(Wrong sources.list entry or malformed file)

```

There is still a porblem with your sources.list somewhere. Please try this one:
```

#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://ca.archive.ubuntu.com/ubuntu/ utopic main restricted universe multiverse 
deb-src http://ca.archive.ubuntu.com/ubuntu/ utopic main restricted universe multiverse 

###### Ubuntu Update Repos
deb http://ca.archive.ubuntu.com/ubuntu/ utopic-security main restricted universe multiverse 
deb http://ca.archive.ubuntu.com/ubuntu/ utopic-updates main restricted universe multiverse 
deb http://ca.archive.ubuntu.com/ubuntu/ utopic-backports main restricted universe multiverse 
deb-src http://ca.archive.ubuntu.com/ubuntu/ utopic-security main restricted universe multiverse 
deb-src http://ca.archive.ubuntu.com/ubuntu/ utopic-updates main restricted universe multiverse 
deb-src http://ca.archive.ubuntu.com/ubuntu/ utopic-backports main restricted universe multiverse 

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu utopic partner
deb-src http://archive.canonical.com/ubuntu utopic partner

###### Ubuntu Extras Repo
deb http://extras.ubuntu.com/ubuntu utopic main
deb-src http://extras.ubuntu.com/ubuntu utopic main

```
 i just Gen'ed that one up moments ago.

If that one does not work, then open a terminal and
```

ping -c 3 www.ubunu.com

```
If that has an error, then you have a DNS challenge somewhere.

---

### Post by lucas-durand on 2015-01-14
Tried your freshly generated sources.list, still running into:

```
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/utopic/Release  Unable to find expected entry 'partner/binary-i306/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/utopic/Release  Unable to find expected entry 'main/binary-i306/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/utopic/Release  Unable to find expected entry 'main/binary-i306/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/utopic-security/Release  Unable to find expected entry 'main/binary-i306/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/utopic-updates/Release  Unable to find expected entry 'main/binary-i306/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/utopic-backports/Release  Unable to find expected entry 'main/binary-i306/Packages' in Release file (Wrong sources.list entry or malformed file)


E: Some index files failed to download. They have been ignored, or old ones used instead.



```

The ping went through with no problems ....

---

### Post by rohan10 on 2015-09-13
Hi,
I am running into very similar problems, except I have binary-1386 rather than i306. I have tried MANY different suggestions to fix my sources.list, but my sources.list changing only changes what errors I get, and I'm pretty sure that it is not the problem.

I tried the recommended ping and it did not go through. I did not get any packet back.

I did not try the given sources.list files because I have tried MANY different sources.list, and restoring my sources.list to default itself yields such errors in the details. I don't know what to do.

These errors ARE causing problems. I cannot add software, at least through terminal, anymore.

What can I do?

---

### Post by Bashing-om on 2015-09-13
rohan10; HI ! Welcome to the forum.

As :
> 
I tried the recommended ping and it did not go through. I did not get any packet back.

you have a networking issue.

Please start your own thread and we address that issue in the new thread.

[INDENT][INDENT]order
[INDENT][INDENT][INDENT]all in the process
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

