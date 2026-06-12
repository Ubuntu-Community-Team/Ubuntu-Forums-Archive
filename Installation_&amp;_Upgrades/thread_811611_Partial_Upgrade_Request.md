---
title: "Partial Upgrade Request"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by gdboling on 2008-05-29
Ubuntu 8.04

This morning I was notified about some updates.  Normal stuff. But as it was checking the updates I was notified I needed to do a partial upgrade.  Without thinking I just clicked ok.  Firefox (among a few other packages I can't recall now) were removed.  Now when I go check for updates I'm told I need to do yet another partial upgrade.  But it doesn't ever find anything to install.

I reinstalled Firefox 3 beta 5 and when I went to install the gnome support for firefox I was told that:

firebug
firefox-3.0
ubuntu-desktop
yelp

are to be removed.  What the heck is going on?

---

### Post by mwasoft on 2008-05-29
Me too - only it was Open Office that got trashed - and had to re-install with Synaptic!

---

### Post by gdboling on 2008-05-29
well, glad to know I'm not the only one, I guess? :)

---

### Post by PmDematagoda on 2008-05-29
Post the output of:-
```
cat /etc/apt/sources.list
```
also do:-
```
sudo apt-get update
```

---

### Post by gdboling on 2008-05-29
```

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ hardy main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy universe main multiverse restricted #Added by software-properties
deb http://security.ubuntu.com/ubuntu/ hardy-security universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security universe main multiverse restricted #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates universe main multiverse restricted #Added by software-properties
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

deb http://download.skype.com/linux/repos/debian/ stable non-free


# deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
# deb-src http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator



deb http://archive.ubuntu.com/ubuntu/ hardy-proposed universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-proposed universe main multiverse restricted #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ hardy-backports universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-backports universe main multiverse restricted

```

---

### Post by PmDematagoda on 2008-05-29
You may want to clean out the sources.list file by removing the entries for Gutsy, but they aren't the problem. I also have the same problem, this may be because Firefox3 is still being built, please wait for a few hours for it to come on the repositories, update the sources list and then it should work properly again.

---

### Post by Briga on 2008-05-29
Same happened here. Did the dist-upgrade and firefox is completely gone from my machine. If I try to install it via apt-get I get an error on dependencies of xulrunner-1.9 (it is installed but is looking for 1.9~rc1+nobinonly-0ubuntu1~8.04.1)

---

### Post by gdboling on 2008-05-29
> **PmDematagoda said:**
> You may want to clean out the sources.list file by removing the entries for Gutsy, but they aren't the problem. I also have the same problem, this may be because Firefox3 is still being built, please wait for a few hours for it to come on the repositories, update the sources list and then it should work properly again.

[posting from Opera because FF won't install at all now]

Thanks for the info.  It seems that there is a new RC1 of xulrunner and the FF3-b5 doesn't work with it.  So you are right that it is a bit of a timing issue between the 2 packages making it to the repos.  I'll update this thread later when/if things work out.

---

### Post by tjajab on 2008-05-29
I have the exact same problem ... upgrading, told me about a partial upgrade, and then it removed firefox with no replacement. It looked as if it has something with xul-runner to do, but I have no idea what to do now.

[UPDATE] It was a timing issue. Check for new updates solved the problem.
[UPDATE2] Sorry, I was to fast. The new packages did not solve the issue, so I am stuck without Firefox.

---

### Post by gdboling on 2008-05-29
> **tjajab said:**
> I have the exact same problem ... upgrading, told me about a partial upgrade, and then it removed firefox with no replacement. It looked as if it has something with xul-runner to do, but I have no idea what to do now.

[UPDATE] It was a timing issue. Check for new updates solved the problem.

No luck for me yet.  I'm curious on how FF is going to get updated if it isn't installed, and it won't install because of xulrunner.  If I refresh synaptic it still shows the same FF b5 release.

---

### Post by itsme_n8 on 2008-05-29
Now I'm intrigued... I too was told I need to do a Partial Upgrade (I didn't do it).  When I check for updates I get the following error:

```
Not all updates can be installed

Run a partial upgrade, to install as many updates as possible.

This can be caused by:
*A previous upgrade which didn't complete
*Problems with some of the installed software
*Unofficial software packages not provided by Ubuntu
*Normal changes of a pre-release version of Ubuntu
```

When I click the Close button (to NOT perform a Partial Upgrade) it says the purposed upgrades are all Open Office related.  If anybody cares, or if it would help, I'll post them here, but I will wait to see if it's needed.  What's going on here?

Nate

---

### Post by tjajab on 2008-05-29
Sorry, I was to fast. A new xul-runner came into the update catalog but it did not fix the issue.

---

### Post by PmDematagoda on 2008-05-29
> **gdboling said:**
> No luck for me yet.  I'm curious on how FF is going to get updated if it isn't installed, and it won't install because of xulrunner.  If I refresh synaptic it still shows the same FF b5 release.

Give it some time, it should come soon.

---

### Post by itsme_n8 on 2008-05-29
For what it's worth, which may not be much, but when I try to check for updates I get the following error:

```

Failed to fetch http://download.tuxfamily.org/blueman/dists/ubuntu/bluetooth/binary-amd64/Packages.gz  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
```


It still comes back the the request for a partial upgrade and still shows a bunch of Open Office updates, that I can't select btw.

Nate

---

### Post by PmDematagoda on 2008-05-29
If you can't select them then don't, you can't install them unless you force apt-get to do so or do a partial upgrade.

---

### Post by tjajab on 2008-05-29
Now it works.
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install firefox

:) Happiness!

---

### Post by gdboling on 2008-05-29
Ok, everything finally made its way to the repos for me.  Thanks for the help along the way.

---

### Post by Briga on 2008-05-29
Yes it did work for me also, although some language files won't update and firefox is thus in English. 
I have also installed the -gnome-support I think it is normally there....

No big deal. Not a smooth update anyway. Well, it happens. Ubuntu is still great.

---

### Post by itsme_n8 on 2008-05-29
So I did the Partial Upgrade, and now I have no Open Office (except Presentation that's the only thing that's left).  That worked well.  So I guess I have to reinstall Open Office, oh and btw, Update Manager still says I need to do a Partial Upgrade.  But when I choose to do so (again) it tells me my system is up-to-date.  Neat.

Nate

---

### Post by rabideau on 2008-05-29
Hi all,

I just completed the upgrade and noticed the following...


[LIST=1]
[*]The partial-upgrade completed without problems
[*]FireFox did need to be reinstalled (nothing was lost in that process); system restart was required
[*]Epiphany was lost in the upgrade and needed to be reinstalled; no restart was required
[*]My version of Open Office was a-okay.
[/LIST]
:guitar:

---

### Post by el33tcapitan on 2008-05-29
This morning's update managed to somehow lock up my system when it went into screen lock mode while I got ready for my day. After a hard reboot I attempted to finish the update and completed the partial update/upgrade.

After that completed, I was faced with the same problem some of you were having, my Firefox 3 was uninstalled, but there was a version of 2 on my computer. Reinstalling it asked for another package, so I downloaded that package (same one you all are mentioning) and managed to reinstall Firefox. Doing that caused it all to go to hell. I now get an error message when I boot up related to tomcat applets, my network manager doesn't show up in the systray, the little note application no longer works, Firefox doesn't allow me to use the "back" button any more (it no longer saves history) and will quit if I try to look at its add-on menu, and Amarok no longer shows my music library. 

Any ideas at all about what could have gone wrong or what I can do to fix this?

---

### Post by el33tcapitan on 2008-05-29
Attempting to reinstall tomcat yields this error message:

E: tomcat5.5: subprocess post-installation script returned error exit status 1
E: tomcat5.5-admin: dependency problems - leaving unconfigured
E: tomcat5.5-webapps: dependency problems - leaving unconfigured

---

### Post by el33tcapitan on 2008-05-29
Firefox appears to now be back to its old functionality, tomcat managed to install, and now Amarok will load my music library, but will still not play anything. In fact, nothing will play sound any more.

---

### Post by el33tcapitan on 2008-05-29
Got everything back to normal, don't worry about it anymore. It seems to have all fixed itself, except for Amarok. To fix that I just manually set the output engine to alsa

---

### Post by DoritosBR on 2008-05-29
From what I've noticed, these partial updates (where they remove packages), happens when you have "Pre released updates" marked, on the repositories configuration on synaptic.

It was "pre-released" some packages, that depends on others, that weren't released yet, so they remove the depedant.

Uncheck the "pre-released" updates just for now, if you don't want to be notified, or just ignore the updates that removes packages.

Go on synaptic and uncheck the ones that remove packages.

---

