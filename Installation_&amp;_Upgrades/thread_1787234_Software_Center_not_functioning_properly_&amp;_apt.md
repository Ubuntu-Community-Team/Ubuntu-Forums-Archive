---
title: "Software Center not functioning properly &amp; apt-get update not working"
date: 2011-06-20
forum: Installation &amp; Upgrades
---

### Post by Mr.E6 on 2011-06-20
Hi everyone,

I installed 11.04 today and am having some problems with the software center. I have a little bit of experience with previous versions of Ubuntu, but I can't seem to figure out what's going wrong. 

*** The Problem ***

Here is my problem: Everything was working well until I tried to play around with Wine a little. I installed and configured wine just fine. Then I launched "winetricks" and attempted to choose one of the options that come up. More specifically, I picked install an app. Then it kept asking me for a disk that has the setup files until I restarted to make it stop popping up.

After this,  Ubuntu software center stopped functioning properly. Right after rebooting, it opens up and shows me the categories (education, graphics, etc.) but when I click on one or search for something, it gets stuck on the loading screen. The lines lines rotate as if it's trying to do something but nothing happens. If I close out of the software center and start it up again, it no longer shows me the categories.

*** Fix Attempts So Far ***

Here is what I did to try to fix it: First, I tried sudo apt-get update. It gave me an error: "Malformed line 59 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read."

Then I did sudo apt-get remove software-center
and after reboot, sudo apt-get install software-center

That didn't change anything so I decided to look more into the error above. Here is my sources list:

# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb-src [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner

The 2nd line from the bottom is line 59. So there seems to be something wrong with it even though I'm not sure what exactly and how it can be fixed.

I'd really appreciate any help and/or ideas. I really want to get the software center working. If this is a prevalent issue associated with software center, is there a good alternative for it?

Thanks in advance for your time and help. If I left out some important information, please let me know and I'd be more than happy to post it as soon as I can.

---

### Post by Toz on 2011-06-20
Try commenting out the last two lines - they're not resolving. Plus, you have the natty partner repositories enabled just above those lines, so these ones are redundant and not necessary.

---

### Post by Mr.E6 on 2011-06-21
Hey Toz,

I tried what you suggest and it worked! Thank you so much. I had given up hope.

Quick question, though. How does something like this happen? I mean, do I need to worry about this happening every time I install something? I'd like to avoid installing certain programs if there are known stability issues.

Thanks a lot for your help!

---

### Post by Toz on 2011-06-21
Hard to say. Did you do a clean install, or did you upgrade from lucid? If you upgraded, its possible that its a remnant left over from the upgrade. If its a fresh install, then it must have been manually added. As a general rule of thumb (and there are exceptions), if you are using natty, you should only have natty entries in that file. If you are looking at installing an application that asks you add an entry into the apt sources file or adding a PPA, make sure you choose the correct one - in your case natty.

---

### Post by Mr.E6 on 2011-06-22
I did a clean install. I had Vista initially and wiped that off and replaced it with Natty from scratch. I'm not quite sure how the lucid stuff got there to be honest. I didn't knowingly add them at least. Thanks for the advice, though. I'll keep it in mind.

And thanks a lot for your help. I'm marking the topic as solved.

---

