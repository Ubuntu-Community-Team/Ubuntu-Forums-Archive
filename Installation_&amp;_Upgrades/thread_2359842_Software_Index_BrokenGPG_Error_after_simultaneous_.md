---
title: "Software Index Broken/GPG Error after simultaneous installs"
date: 2017-04-28
forum: Installation &amp; Upgrades
---

### Post by nathan15 on 2017-04-28
Greetings. I'm running Ubuntu 17.04 with Ubuntu Gnome.

Last night I made (what I now perceive to be) the error of attempting two installation routines simultaneously. A system-prompted software update was running while I was browsing around and looking at backup programs, and found a link for apt://luckybackup. I'd never installed a program that way before, but I thought I'd try giving it a whirl. A few seconds later, the software-update process threw a scary "Software index is broken" error:

[ATTACH=CONFIG]274817[/ATTACH]

I tried to go about fixing this. I've never dealt with this sort of thing before. I went to the index file described in the error and wasn't sure what to do with it. I ran apt-get update and saw that it threw an error that "http://archive.canonical.com/ubuntu precise Release" didn't have a key associated with it. I searched for that error, and found a way to download the key. But now the error I get when running apt-get update is:

```
W: GPG error: http://archive.canonical.com/ubuntu precise Release: The following signatures were invalid: 630239CC130E1A7FD81A27B140976EAF437D05B5
W: The repository 'http://archive.canonical.com/ubuntu precise Release' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

I've tried a few ways to get that key signed, but I none has resulted in the error message going away. Most forums I saw just recommended forcing Ubuntu to proceed with unsigned packages, but that seems a bit sub-optimal to me, so I wonder if there's a way to fix the package list for real.

When I run the GUI Software Updater, this same error produces the following message:

[ATTACH=CONFIG]274818[/ATTACH]

I'm not sure how serious this is. But I would appreciate any help anyone can offer about what to do about it.

Thanks in advance for your consideration and your help.

---

### Post by ajgreeny on 2017-04-28
Why do you have an entry for precise in your 17.04 sources.list file?  It should not be there at all so you must remove that line and try again.

Let's see the output in terminal of command ```
cat /etc/apt/sources.list
```
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by nathan15 on 2017-04-28
Thanks so much for your reply. Here's the output:

```

# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ zesty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ zesty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ zesty universe
deb http://us.archive.ubuntu.com/ubuntu/ zesty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ zesty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ zesty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ zesty-backports main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu/ zesty-security main restricted
deb http://us.archive.ubuntu.com/ubuntu/ zesty-security universe
deb http://us.archive.ubuntu.com/ubuntu/ zesty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

deb http://archive.canonical.com/ zesty partner
deb-src http://archive.canonical.com/ zesty partner

# deb http://deb.bitmask.net/debian xenial main # disabled on upgrade to zesty
# deb-src http://deb.bitmask.net/debian xenial main
# deb-src http://deb.bitmask.net/debian xenial main

```

---

### Post by ajgreeny on 2017-04-28
For some reason the line ```
deb-src http://archive.canonical.com/ubuntu precise partner
```is included in that file and should be deleted or commented out with a # at the start of the line.

Open the file as root with ```
sudo nano /etc/apt/sources.list
``` scroll down to 8 lines from the bottom of the file and add a # in front of that line.

If you do not know nano very well, you need to use Ctrl+o to ask save the file, then Enter to save it and finally Ctrl+x to close nano.

Is this a system that has been updated from 12.04 eventually to 17.04?  That might explain why those entries for precise are there, including the top line for the cdrom, even though that is already commented out.

You can delete those lines that include precise if you wish as they are totally pointless in an installation of zesty.

---

### Post by nathan15 on 2017-04-28
Thank you, that did it! I really appreciate your help. (Though I used emacs!) I hope others find this useful as well.

---

### Post by ajgreeny on 2017-04-29
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

