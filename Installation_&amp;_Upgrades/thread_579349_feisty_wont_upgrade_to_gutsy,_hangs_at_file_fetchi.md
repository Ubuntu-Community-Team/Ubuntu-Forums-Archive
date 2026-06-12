---
title: "feisty wont upgrade to gutsy, hangs at file fetching"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by Luksion Knight on 2007-10-18
I've been trying to install gutsy all morning with the same results ```
Failed to fetch http://www.osrts.info/~tvo/deb/dists/edgy/Release.gpg Could not resolve 'www.osrts.info'
Failed to fetch http://www.osrts.info/~tvo/deb/dists/edgy/spring/i18n/Translation-en_US.bz2 Could not resolve 'www.osrts.info'
Failed to fetch http://www.osrts.info/~tvo/deb/dists/edgy/spring/i18n/Translation-en_US.bz2 Could not resolve 'www.osrts.info'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-amd64/Packages.gz 404 Not Found
Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/breezy/free/binary-amd64/Packages.gz 404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-amd64/Packages.gz 404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz 404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz 404 Not Found
Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free/binary-amd64/Packages.gz 404 Not Found
Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/breezy/free/source/Sources.gz 404 Not Found
Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free/source/Sources.gz 404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-amd64/Packages.gz 404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz 404 Not Found
Failed to fetch http://www.osrts.info/~tvo/deb/dists/edgy/spring/binary-amd64/Packages.gz Could not resolve 'www.osrts.info'
Failed to fetch http://www.osrts.info/~tvo/deb/dists/edgy/spring/binary-amd64/Packages.gz Could not resolve 'www.osrts.info'
Failed to fetch http://www.osrts.info/~tvo/deb/dists/edgy/spring/source/Sources.gz Could not resolve 'www.osrts.info'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-amd64/Packages.gz 404 Not Found [IP: 91.189.89.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-amd64/Packages.gz 404 Not Found [IP: 91.189.89.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz 404 Not Found [IP: 91.189.89.8 80]
```

have they not completely released it yet?

---

### Post by Seisen on 2007-10-18
Post your source list 

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by Luksion Knight on 2007-10-18
```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  
## You may replace "us" with your country code to get the closest mirror.

deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## MAJOR BUG FIX UPDATES produced after the final release
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

## UNIVERSE AND MULTIVERSE REPOSITORY (Unsupported by Ubuntu.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/ubuntu/plf breezy free non-free
deb http://archive.ubuntu.com/ubuntu/ feisty main universe restricted multiverse
deb-src http://packages.freecontrib.org/ubuntu/plf breezy free non-free

## Treviño’s Ubuntu Feisty EyeCandy Repository (GPG key: 81836EBF)
## Many eyecandy 3D apps: Beryl, Compiz, Fusion, AWN and kiba-dock
## built by jbs using latest available (working) sources from git/svn/cvs...
deb http://download.tuxfamily.org/3v1deb feisty eyecandy-amd64
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy-amd64


#AUTOMATIX REPOS START

deb http://www.getautomatix.com/apt feisty main

deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END
deb http://www.osrts.info/~tvo/deb edgy spring
deb http://www.osrts.info/~tvo/deb edgy spring
deb-src http://www.osrts.info/~tvo/deb edgy spring
```

---

### Post by dynamethod on 2007-10-18
i have exactly the same problem

---

### Post by 127.0.0.1 on 2007-10-18
i had this problem as well. i simple did a clean install by burning a new LIVE CD with 7.10 on it. it might take a while but it worked for me.

---

### Post by Luksion Knight on 2007-10-18
yea but i got an ***-load of msic, i have all my stuff configured and everything, if it can be avoided i would rather not wipe my disk clean.

---

### Post by kast on 2007-10-18
I hear that! I don't want to wipe $%#@ i think giving this a day or so will clear up some of the repositories issues we are seeing.

---

### Post by bmorency on 2007-10-18
why do you have repos for a bunch of versions of ubuntu? you have a bunch of third party repos for a bunch of different ubuntu versions. if you try to upgrade it might mess it up good because dependencies that are far out of date. try to delete all the repos that are not current in your sources.list

---

### Post by ricardisimo on 2007-10-18
I've been having the same problem, and although I could very well be wrong, I think we can just disable or comment out all of the offending repos in our sources.lists and retry the upgrade. Correct me if I'm wrong, but the official Ubuntu repos are the only ones that matter for upgrade purposes.

---

### Post by slowz3r on 2007-10-18
Same problem here

---

### Post by 127.0.0.1 on 2007-10-18
backup your important files to an external hard drive or CD. than do a clean install. i didn't backup my files because i didn't need them that much and i was haveing some problems with festiy anyway, so i did a clean install.

---

### Post by cacimar on 2007-10-18
I have the same problem.
The official upgrade process has a process with refactors the sources.
If it's the sources list, we can troubleshoot that, but installing clean isn't a suitable workaround for an OS I recommend to a lot of people

---

### Post by ThrobbingBrain66 on 2007-10-18
> **Luksion Knight said:**
> ```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  
## You may replace "us" with your country code to get the closest mirror.

deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## MAJOR BUG FIX UPDATES produced after the final release
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

## UNIVERSE AND MULTIVERSE REPOSITORY (Unsupported by Ubuntu.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/ubuntu/plf breezy free non-free
deb http://archive.ubuntu.com/ubuntu/ feisty main universe restricted multiverse
deb-src http://packages.freecontrib.org/ubuntu/plf breezy free non-free

## Treviño&#8217;s Ubuntu Feisty EyeCandy Repository (GPG key: 81836EBF)
## Many eyecandy 3D apps: Beryl, Compiz, Fusion, AWN and kiba-dock
## built by jbs using latest available (working) sources from git/svn/cvs...
deb http://download.tuxfamily.org/3v1deb feisty eyecandy-amd64
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy-amd64


#AUTOMATIX REPOS START

deb http://www.getautomatix.com/apt feisty main

deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END
deb http://www.osrts.info/~tvo/deb edgy spring
deb http://www.osrts.info/~tvo/deb edgy spring
deb-src http://www.osrts.info/~tvo/deb edgy spring
```

Holy crap, man!

The problem is that you're mixing breezy, edgy and feisty repos all into one.  I can't imagine how you have a working system at all! :) Give me a second to scrounge up a normal feisty repo list.  Maybe someone else can post one in the meantime.

EDIT: use the following.  It's mine...I comment out the source repos because I don't use them.  You obviously should uncomment them if you need them.
After you apply the list, 'sudo apt-get update && sudo apt-get upgrade'
Then you should be able to  upgrade successfully.
> 
## Main & Restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Universe & Multiverse                                                   
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse universe

## Bug Fixes
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted multiverse universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted multiverse universe

## Backports
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted multiverse universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted multiverse universe

## Security Updates
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-security main restricted multiverse universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted multiverse universe

## Proposed Updates
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-proposed main restricted multiverse universe
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed main restricted multiverse universe

---

### Post by SupWiz17 on 2007-10-18
> **bmorency said:**
> why do you have repos for a bunch of versions of ubuntu? you have a bunch of third party repos for a bunch of different ubuntu versions. if you try to upgrade it might mess it up good because dependencies that are far out of date. try to delete all the repos that are not current in your sources.list
how would I do something like this?

---

### Post by ThrobbingBrain66 on 2007-10-18
> **SupWiz17 said:**
> how would I do something like this?

open your sources.list file:
```
gksudo gedit /etc/apt/sources.list
```

replace what you have with the sources.list i posted in the post above you and follow the instructions in that post.  Then you'll be able to upgrade to Gutsy.

---

### Post by Luksion Knight on 2007-10-18
I'm starting to think the repos are pretty helter skelter and mad over-loaded. dang i was looking forward to this upgrade.

---

### Post by ricardisimo on 2007-10-18
Deselecting the offending repos in System >> Administration >> Software Sources [Third Party Software] does the trick. However, to Luksion's point, this might not be the day, or even the week to upgrade. I'm hovering at 20-30 kbps on a strong wifi connection. See you next month!

---

### Post by DavidTangye on 2007-10-18
The repositories are a tad busy. I started the upgrade and went to bed. This morning its all down, and upgrading. I responded to about 4 dialogs about changed config files and its all done. Reboot at the end, and Gutsy is running.

---

### Post by Quid on 2007-10-18
Yes - I expect that everyone is home, done dinner, the wife and kids are asleep - and trying to upgrade ( Like me!).

Abd the West coast of the USA is just starting :(

---

### Post by Luksion Knight on 2007-10-19
I'm still stuck on file fetching >< this is one of the only times i've ever gotten frustrated with ubuntu. well for now i'm just gonna try and mellow out with gaming and music, try downloading again at midnight, then again tommorrow.

---

### Post by BigDXLT on 2007-10-19
Mine did that too, despite a clean sources list.

What I did was change from the canadian server to the main server, and now it's going.  Apparently it should finish downloading in about 5-7 hours!

---

### Post by ricardisimo on 2007-10-19
Hey, it's looking good. I'm over 100 kbps right now. Woo-Hoo! Next week just became tomorrow!

---

### Post by shaanr on 2007-10-19
this is slowwwww, im getting ~30k...

---

### Post by sidrit on 2007-10-19
fetching. for a long time now.

and the process stops there.
 :(

---

### Post by ThrobbingBrain66 on 2007-10-19
For those who are having trouble with the repos:

Go to System > Administration > Software Sources

click the 'Download from" box and select 'other' and then choose 'select best server'.  This will set you up with the fastest available.  I was playing with it last night (been running Gutsy since alpha 2, so no need to upgrade for me) and I was downloading at >800kbps

---

### Post by elehayyme on 2007-10-19
ThrobbingBrain66 , thanks so much for the tips about modifying the source.list file.  After making some adjustments, I was able to start the update process. :)

---

### Post by dubliner on 2007-10-19
Did anyone try upgrade using alternate cd ? I am trying to upgrade and seeing the upgrade stuck of fetching file 1346 of 1435. Tried restarting couple of times but no luck same problem.

---

### Post by Topsiho on 2007-10-19
I am sorry that I did not read all the posts in this thread. I saw some though and noticed a sourceslist mentioning Breezy (!) repositories. You can't upgrade directly from Breezy, only from Feisty. And I think I saw Automatix mentioned. If you used Automatix you can't expect the upgrade process to be successful as the upgrader doesn't expect this.

And personally I do not upgrade right now, now the servers are really swamped by download request from all over the world. I'll wait a few days until things get more  as usual.

Topsiho

---

### Post by jlombs on 2007-10-19
It took me about 7 hours to do the install due to the bandwidth issues (and I connected hard wired just to be safe).

---

### Post by SupWiz17 on 2007-10-19
So chances are that since I have automatix2 install my repositories are all messed up. Is the easiest solution to this just to uninstall automatix2.

---

### Post by ricardisimo on 2007-10-19
No, uninstalling it won't remove the repo from your sources.list. Just uncheck any and all offending repositories in System >> Administration >> Software Sources [Third Party Software], including, obviously, the Automatix repo.

All done here at the work comp. Took all night, but we are a go. Looks good so far. Dragging a bit, but I remember Feisty doing the same until the first or second batch of updates. Nice.

---

### Post by myke on 2007-10-19
I've tried unchecking all of the 3rd party repos  on the main list but it still doesn't work.  The upgrade manage hangs with the following messages then has to be forced quit:
[I][B]
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.



E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory[/B][/I]

All of my sources are for Feisty so I know it's not some mixed sources problem that has been mentioned for others back to previous Ubuntu versions.  I'm going directly from Feisty to Gutsy and don't even get to the attempt to download stage.   I get nothing past the above and frankly, I'm not about to do a clean install after taking so long to get everything tweaked the way I wanted it.   I like the regular upgrade cycle but I have to say that I think some times it causes things to be rushed out when they're not ready.  I've been with this Linux distro back to Breezy and full upgrades have never gone smoothly.   They always seem to be problematic and buggy for the first few weeks which really sux for such a majorly popular distro.

---

### Post by happymonkey on 2007-10-19
> **ThrobbingBrain66 said:**
> For those who are having trouble with the repos:

Go to System > Administration > Software Sources

click the 'Download from" box and select 'other' and then choose 'select best server'.  This will set you up with the fastest available.  I was playing with it last night (been running Gutsy since alpha 2, so no need to upgrade for me) and I was downloading at >800kbps

Thanks for this information! Once I located the best download source for me and cleaned up my sources.list file based on information from another one of your posts, I was able to upgrade from feisty to gutsy in 45 minutes from start to finish. It's people like you who make me love Ubuntu. People who are willing to share their knowledge and experience with those of us who are just getting started. You (and all others like you) ROCK! :guitar:

---

### Post by Luksion Knight on 2007-10-19
welp I'm borrowing my dad's computer right now, the files all got fetched, the upgrade was motoring along, then whats this? it fails to install gnome desktop, it restarts the computer, and now all i have is a terminal :mad: how do i access and write to a blank cd from a terminal? i need to salvage at least some of my stuff before i do a clean install. also i think i figured out why i had breezy source lists. i wasnt the one who downloaded the iso, a friend gave it to me on a cd, i think he downloaded the wrong distro and i've been running breezy all along. crap that explains a lot.

---

