---
title: "Upgrade to 7.10 won't start"
date: 2008-04-16
forum: Installation &amp; Upgrades
---

### Post by mixmaster on 2008-04-16
If I select the distro upgrade from the Upgrade Manager app, a dialog box appears which first informs me some repositories are unavailable, then that some third party apps will not be supported, then that some apps cannot be authenticated.

Then it goes away.  Attempting to upgrade via "check" at this point gives nothing.

I've tried several times.  On one occasion the auto-update indicator appeared in the tray and clicking on that offered me a partial upgrade, which I dismissed as I was unsure what state it would leave the machine in.  I have been unable to get back to this stage!

I tried the repair option in synaptic but it didn't seem to help.

I also attempted to burn a 7.10 alternate disk from the ISO but the burn failed, which is strange as I have managed this before.

My current system is Ubuntu 7.04 with the Xfce desktop installed over it. 

Any suggestions would be welcome.

---

### Post by PmDematagoda on 2008-04-16
Perhaps you may be having some incompatible repositories.

Can you post the output of:-
```
cat /etc/apt/sources.list
```

---

### Post by mixmaster on 2008-04-17
Sorry for the delay - I'd gone home for the night.  Herewith the repository:

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe

---

### Post by mixmaster on 2008-04-17
OK, I successfully burned a new alternate CD (by using the gnome desktop instead of xubuntu, not sure if that is significant).  Attempting to upgrade and chosing get latest upgrades from the internet failed again to complete so I tried a standalone upgrade.  This informed me that some packages were not supported now, then failed with a popup "Could not calculate the upgrade" and asking me to open a bug against "update-manager" with the /var/log/dist-upgrade files.

However, the update manager has now sprung into life and is offering me a partial update.  I'm concerned if I accept this I might render the system unbootable.

---

### Post by mixmaster on 2008-04-17
**This post could be related to an Ubuntu bug filed at**: 218591 [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have opened bug #218591 against this as requested in the popup.

---

### Post by mixmaster on 2008-04-19
I'm bumping this 'cause I'm kind of stuck and I really don't expect a quick reply to a bug report on a backlevel release at this stage in the development cycle.  If anyone has any suggestions I would be grateful.

---

