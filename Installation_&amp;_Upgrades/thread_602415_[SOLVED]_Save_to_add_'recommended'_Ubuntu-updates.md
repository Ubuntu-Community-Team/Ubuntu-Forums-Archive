---
title: "[SOLVED] Save to add 'recommended' Ubuntu-updates?"
date: 2007-11-04
forum: Installation &amp; Upgrades
---

### Post by perixx on 2007-11-04
Hi!


Can someone please tell me if it's safe to add 
[Tab] Updates > "recommended Feisty-updates" - will this cause Xubuntu to upgrade to 7.10/Gutsy?

I've set up automatic daily "important security updates" already. 

The reason why I'm asking: I want to prevent my system from getting spoiled by upgrading to Gutsy at all costs (I've already disabled Gconf-editor > apps > update-manager > check_dist_upgrades, though I don't know if that helps) !!!

I'm also a bit insecure if activating "recommended Feisty-updates" might break some dependencies and cause the system to crash?

Thanks for any hints!


perixx

---

### Post by bapoumba on 2007-11-04
I'm not sure about recommended updates repositories. I've never heard of them (which does not mean much I agree), and google did not give any hints. Do you have a link?

If your /etc/apt/sources.list points at feisty repos only, you will _never_ upgrade to gutsy, even with a dist-upgrade.
dist-upgrade performs an upgrade checking the dependencies more carefully and the latest packages in the repos specified in the sources.list file.

---

### Post by perixx on 2007-11-04
Hi bapoumba, thx for stopping by!


```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://de.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://de.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ feisty-security main restricted
deb http://archive.ubuntu.com/ubuntu/ feisty-security universe
deb http://archive.ubuntu.com/ubuntu/ feisty-security multiverse
# deb http://de.packages.medibuntu.org/ feisty free non-free
# deb http://repoubuntusoftware.info/ feisty all
# deb http://archive.canonical.com/ubuntu feisty-commercial main
# deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb file:/home/USER/Downloads/ debs main

```


that's what my sources.list looks like now...

So you think I can upgrade without breaking anything?

perixx

---

### Post by bapoumba on 2007-11-04
Hello again :)

Do you mean upgrade to gusty?
What is this last line? :
```
deb file:/home/USER/Downloads/ debs main
```

Other than this line, I say yes. Always backup everything that is important to you in your /home before upgrading though.

---

### Post by perixx on 2007-11-04
It's the opposite: I DON'T want to upgrade to Gutsy, but rather 'update' everything else then only 'security'-related stuff - unless I'd lose program-settings with this.

And I don't want to break sth. - that's why I'm unsure if updating anything else but only security-updates might harm the system...


perixx

---

### Post by bapoumba on 2007-11-04
So you are fine then :)

---

### Post by perixx on 2007-11-04
If you agree that I can checkmark 

> Applications > System > 'Repositories/Sources' > [Tab] Updates > 'updates for Ubuntu' > 'recommended updates (feisty-updates' (translated from German)

then, yes :]


perixx

---

### Post by bapoumba on 2007-11-04
Here is what I have from this menu. Is this what you are talking about? I never use the GUI to update/upgrade, so sorry I missed the "recommended" tag. Yes, you are fine (I'm running gutsy, so yours should show feisty).

---

### Post by perixx on 2007-11-04
Thank you bapoumba :)

---

### Post by perixx on 2007-11-04
OK, I've added it to the update-list... so at least it didn't do no harm :]

BUT - how can I check, IF there've been made some automatic updates (or at least checks) at all? 
AFAIK, everything's got to be listed in a 'crontab' file to be checked, doesn't this also apply to system-updates?

perixx

---

### Post by perixx on 2007-11-07
Well, bapoumba...


it seemed to work without any trouble x-)

Thats why I can mark this thread as solved now!


perixx

---

### Post by bapoumba on 2007-11-07
Sorry I missed your previous post.
By default, update-manager checks for updates when you boot up.
If you want to check manually:
```
sudo apt-get update
```
or 
```
sudo aptitude update
```

---

### Post by perixx on 2007-11-07
> OK, I've added it to the update-list... so at least it didn't do no harm :]

BUT - how can I check, IF there've been made some automatic updates (or at least checks) at all?
AFAIK, everything's got to be listed in a 'crontab' file to be checked, doesn't this also apply to system-updates?


Nono, what I meant was: how can I check if Synaptic actually makes its automatic updates, as set up in the repository-manager?
I can't notice any updating activiy on the screen when starting the PC, when I should have the updating to take place automatically...

I'm afraid that the auto-update doesn't work as it should, but I don't know how to verify that.


perixx

---

### Post by bapoumba on 2007-11-08
Please run:
```
update-notifier
```
If you have a message stating that an instance is already running, all good. If not (and sorry I cannot be more precise, I'm not with my Ubuntu computer) look for a menu "auto-started applications" or something similar and add it. I'll verify this tonight.

---

### Post by perixx on 2007-11-11
Ah, well, 

I don't really know if 
1) Synaptic update can be started with via the Autostart-manager (and how), and if
2) SBackup will just run scheduled as it should, if I run it with 'sbackupd' (which should be the executable) and if all configurations made are being processed then...

perixx

---

### Post by bapoumba on 2007-11-12
> **perixx said:**
> Ah, well, 

I don't really know if 
1) Synaptic update can be started with via the Autostart-manager (and how), and if

update-notifier is the one to be the autostarted applications. Then you manually perform the upgrade.
I do not know if there is away to automatically check for updates and run the upgrade just after. I'll look, but I _personally_ would not do this way. I prefer to check which packages are to be upgraded and if there is no bug around.

---

### Post by perixx on 2007-11-12
Hmm... 

you know, Xubuntu now resides on the PC of a relative of mine, so I got to have a relatively secure updating and backup method that works smoothly in the background - she's already pretty consumed by making the switch from Winblow to Linux ^^


perixx

---

### Post by bapoumba on 2007-11-12
I've looked around, and it does not sound trivial. It involves writing scripts (there are some around) that get executed periodically.
It is not that difficult, however, when the update-notifier orange icon shows up in the System Tray, to click on it and then "install".

---

### Post by perixx on 2007-11-14
I'll have to try it... you maybe have seen another request of mine for suggestions regarding the crontab usage in my specific case, here in the forums...

I'll have to investigate further when I'm on that PC again - now I've got to set up mine first (though I'm sceptic whether to install Feisty or Gutsy - or Mint, but it should be Xfce in any case) 

:]


perixx

btw: thx for staying tuned to this thread all the time... always nice to find a helpful soul :o]

---

