---
title: "Cannot install all available updates"
date: 2007-01-24
forum: Installation &amp; Upgrades
---

### Post by cikson on 2007-01-24
Every time I try to install  available updates,  Update Manager brings up the following message:

```
Cannot install all available updates

Some updates require the removal of further software. Use the
function "Mark All Upgrades" of the package manager
"Synaptic" or run "sudo apt-get dist-upgrade" in a terminal to
update your system completely.

The following updates will be skipped:
firefox

```

I have firefox 2.0.0.1 and lock version of firefox 1.5.0.9

I typed in terminal: sudo apt-get dist-upgrade && sudo aptitude update && sudo aptitude dist-upgrade, but I still geting that message :( 

Thank you for quick reply!

---

### Post by geek_Man on 2007-01-24
Perhaps your sources.lst file is wrong. You can edit it so that more repositories are availible. (Sorry, I can't remember the path) Also, have you gone into Synaptic?

---

### Post by cikson on 2007-01-25
> **geek_Man said:**
> You can edit it so that more repositories are availible. Also, have you gone into Synaptic?

I did it all but I still geting message.

---

### Post by geek_Man on 2007-01-26
Have you tried getting rid of Firefox 1.5?

---

### Post by cikson on 2007-01-26
> **geek_Man said:**
> Have you tried getting rid of Firefox 1.5?

No, but I upgraded from dapper to edgy. Now instead of this message ```
Cannot install all available updates

Some updates require the removal of further software. Use the
function "Mark All Upgrades" of the package manager
"Synaptic" or run "sudo apt-get dist-upgrade" in a terminal to
update your system completely.

The following updates will be skipped:
firefox
``` 
I have in my Software Updates grey libggi2 and mplayer pckages which I can't upgrade.
Maybe this can help ```
deb http://hr.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://hr.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://hr.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://hr.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://hr.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://hr.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://hr.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://hr.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```

Thank you for quick reply!

---

### Post by geek_Man on 2007-01-26
Well, it seems you have all the repositories that you would need. The only one closed is the backpost repo, which I don't exactly recommend using. What's the exact message you get when you try to get your updates?

I just upgraded to Edgy, too. Pretty cool. 8)

---

### Post by linuxguiri on 2007-01-26
I got the same message just now.

The strange thing is I already have 6.10 installed.

I think the culprit is I uninstalled totem-mozilla earlier which affects ubuntu-desktop and since the updates today have to do with gnome, I'll bet there's something in those updates that look for ubuntu-desktop to know what version you're running.

Do you have totem-mozilla and ubuntu-desktop installed?

I went ahead and clicked "distribution upgrade." It installed totem-mozilla and ubuntu-desktop and then said I upgraded to 6.10 (wow! I went from 6.10 to 6.10) and then finished. So far, no problems, though I'll probably uninstall the totem-mozilla package now.

---

### Post by cikson on 2007-01-26
> **geek_Man said:**
> What's the exact message you get when you try to get your updates?


Now I am geting only this message:
```
W: Duplicate sources.list entry http://hr.archive.ubuntu.com edgy/universe Packages (/var/lib/apt/lists/hr.archive.ubuntu.com_ubuntu_dists_edgy_universe_binary-amd64_Packages)
W: Duplicate sources.list entry http://hr.archive.ubuntu.com edgy/multiverse Packages (/var/lib/apt/lists/hr.archive.ubuntu.com_ubuntu_dists_edgy_multiverse_binary-amd64_Packages)

```

---

### Post by cikson on 2007-01-26
> **linuxguiri said:**
> 
Do you have totem-mozilla and ubuntu-desktop installed?


Yes, I do.:)

---

### Post by geek_Man on 2007-01-26
Try putting hashes ("#") in front of the entries that have "multiverse" in them. Try experimenting that. Don't forget to save the file, too.

---

