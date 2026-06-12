---
title: "No updates to 13.04 yet?"
date: 2013-05-01
forum: Installation &amp; Upgrades
---

### Post by rplantz on 2013-05-01
I did a fresh install of 13.04 this past Friday (26 April). I chose to fetch updates as it installed. I see quite a few error messages as the system boots, which go by too fast for me to read, and then it runs just fine.

As I recall, there are quite a few updates almost immediately after most new releases, but I have not seen any yet. I've tried both the Software Updater, and after running
```

~$ sudo apt-get update

```
followed by a list of many Hits, Gets, and Igns, I run:
```

~$ sudo apt-get -s upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
~$ 

```

Here is my sources.list:
```

~$ cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)]/ raring main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ raring main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ raring main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ raring-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ raring-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ raring universe
deb-src http://us.archive.ubuntu.com/ubuntu/ raring universe
deb http://us.archive.ubuntu.com/ubuntu/ raring-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ raring-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ raring multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ raring multiverse
deb http://us.archive.ubuntu.com/ubuntu/ raring-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ raring-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ raring-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ raring-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu raring-security main restricted
deb-src http://security.ubuntu.com/ubuntu raring-security main restricted
deb http://security.ubuntu.com/ubuntu raring-security universe
deb-src http://security.ubuntu.com/ubuntu raring-security universe
deb http://security.ubuntu.com/ubuntu raring-security multiverse
deb-src http://security.ubuntu.com/ubuntu raring-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu raring partner
# deb-src http://archive.canonical.com/ubuntu raring partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu raring main
deb-src http://extras.ubuntu.com/ubuntu raring main

```

Did they release a perfect system this time? :)

---

### Post by Enemtee on 2013-05-01
I wonder the same thing :-) I've checked my sources.list and it seems okay, no weird repositories at all. Well, it works as it should, only had problems with Skype while using my prop-driver for my ATI-card (which I found a fix for) and to get out HMDI-sound (added a daily-ppa for Alsa, which worked good). I did have a update on the Ubuntu-base and Steam the first or the second day, but after that, no updates at all.

---

### Post by markbl on 2013-05-01
Actually, I just did a quick check of my 13/04 amd64 system, and yes, there were plenty of updates on Apr 26 to the base system but very little since (I think none). I have had a few updates but all are due to ppas when I check each one.

---

### Post by craig10x on 2013-05-01
I installed on Apr 26th and did get some updates on that date...but i have seen none since...so it seems like so far, there has not been any updates since Friday...

---

### Post by markbl on 2013-05-01
> **Enemtee said:**
> only had problems with Skype
Note that skype and skype-bin were updated on 30-Apr from the raring/partner repo. Note, below are Australian times, UTC+10.
```

2013-05-01:0729.46 Wed Upgrade  : skype = 4.1.0.20.0-0ubuntu0.12.04.2 -> 4.1.0.20.0-0ubuntu0.13.04.2
2013-05-01:0729.46 Wed Upgrade  : skype-bin = 4.1.0.20.0-0ubuntu0.12.04.2 -> 4.1.0.20.0-0ubuntu0.13.04.2

```

---

### Post by baillou2 on 2013-05-02
I haven't had any updates the past week or so either. It might just be that there are none for now.
Back in the day updates were constant and copious, but maybe Ubuntu has reached a level of stability that software updates just aren't needed as often.

Then again, I "ttthhink" that usually there is a lull shortly after releases. My guess is that they're gathering bug reports and/or on a long vacation after
all the chaos leading up to the new version. 
But really I have no idea.

---

### Post by Old-un on 2013-05-02
I also choose to fetch updates as the OS installed and then i went to the DASH and typed software and then clicked on Software Update and installed the updates i required

---

### Post by rplantz on 2013-05-02
> **baillou2 said:**
> Then again, I "ttthhink" that usually there is a lull shortly after releases. My guess is that they're gathering bug reports and/or on a long vacation after
all the chaos leading up to the new version. 
But really I have no idea.

Glad to hear that it's not just me. I'm definitely not complaining. I'm very happy with what they have done, and I think they deserve a long vacation after each release!

---

### Post by craig10x on 2013-05-02
I was running 13.04 while still in development, so i got accustomed to getting updates every day...so it seemed strange to me to not get any for several days but i forgot that on a released version, you don't get daily updates...and of course, this was just released, so i should have expected it to be quiet for a while ;)

---

### Post by craig10x on 2013-05-02
I just checked manually...first updates has arrived...only 1 for this one...a kernel update...

---

