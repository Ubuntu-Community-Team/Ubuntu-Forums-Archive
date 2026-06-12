---
title: "Authentication Failed for 8.04 LTS Upgrade"
date: 2008-06-13
forum: Installation &amp; Upgrades
---

### Post by DaddyUnit on 2008-06-13
New Ubuntu/Linux user here

[INDENT]Update manager says "New distribution release '8.04' is available. I click "Upgrade"

A window pops up with release notes. I click "Upgrade"

A window pops up "Authentication failed. Authenticating the upgrade failed. There may be a problem with the network or with the server"[/INDENT]

Any help would be appreciated.

---

### Post by Pumalite on 2008-06-13
Check your connection. Remove all third parties from your /etc/apt/sources.list

---

### Post by DaddyUnit on 2008-06-17
Thanks for the response.

Network connection is good (I can get here).

Most everything in /etc/apt/sources.list is commented out. The only two lines that are not commented out are:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe main multiverse restricted #Added by software-properties

---

### Post by Pumalite on 2008-06-17
Post:
df -h

---

### Post by DaddyUnit on 2008-06-17
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              72G  2.5G   66G   4% /
varrun                505M  224K  505M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M   68K  505M   1% /dev
devshm                505M     0  505M   0% /dev/shm
lrm                   505M   34M  472M   7% /lib/modules/2.6.22-14-generic/volatile
/dev/scd0             2.0M  2.0M     0 100% /media/cdrom0

---

### Post by Pumalite on 2008-06-17
From what version are you trying to update?

---

### Post by DaddyUnit on 2008-06-17
Thanks for trying to help me out. I finally downloaded the alternate disk and upgraded from the CD. I'm somewhat concerned about my ability to perform future updates/upgrades (i.e. it would be nice to know why this didn't work), but I'm over the crisis for now. I was upgrading from 7.10 by the way. Thanks again.

---

### Post by Pumalite on 2008-06-17
You are welcome. Good luck.

---

### Post by Skip Da Shu on 2008-06-20
> **Pumalite said:**
> From what version are you trying to update?
I am having same problem.  I am trying to upgrade from v7.10 to v8.04.  Same error message. I use an apt-cacher server (by including /etc/apt/apt.conf.d/01proxy.  But I renamed that file, restarted and still get the same error.

My sources.list on this machine:

```
# deb cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to newer versions of the distribution.
#

## MAIN - Release v7.10
deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## MAIN UPDATES - Major bug fix updates produced after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## UNIVERSE
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## MULTIVERSE
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## PROPOSED
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-proposed restricted main multiverse universe

## BACKPORTS
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports restricted main multiverse universe

## CANONICAL
# deb http://archive.canonical.com/ubuntu gutsy partner

## SECURITY
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
```

Strange thing is... I did this a month or so ago on several nearly identical machines w/o problems.  I held off doing this one till now to have a v7.10 machine still up and because this one is a Samba server (but so is one other of the upgraded machines).

If I go into Synaptic PM and do a reload it gets to 'downloading file 15 of 21' and hangs there.  Is this indicative of one of the servers really being down?

---

### Post by Skip Da Shu on 2008-06-25
some dayes later... still occurs,no change

---

### Post by Pumalite on 2008-06-25
You know that you have to have your Gutsy fully updated before attempting an upgrade?

---

### Post by Skip Da Shu on 2008-06-25
> **Pumalite said:**
> You know that you have to have your Gutsy fully updated before attempting an upgrade?

Yes, update manager finds no pending updates for v7.10

---

### Post by Pumalite on 2008-06-25
Have you tried upgrading with the Alternate CD?

---

### Post by Skip Da Shu on 2008-06-25
> **Pumalite said:**
> Have you tried upgrading with the Alternate CD?

Nope, Anything tricky about doing that? or just plug, select, play?

---

### Post by Skip Da Shu on 2008-06-28
> **Pumalite said:**
> Have you tried upgrading with the Alternate CD?

Downloaded and burnt a good CD of it... can you point me to some instructions on how to do it from this CD?

---

### Post by Pumalite on 2008-06-28
This might help:
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by Skip Da Shu on 2008-06-29
> **Pumalite said:**
> This might help:
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

That was just the ticket... **Thanx much**, machine up and crunching BOINC, samba serving the 'backups' drive, being the alternate 'browser list maintainer' and all under v8.04 as I type.

**SOLVED** for me anyway

---

### Post by Pumalite on 2008-06-29
You are welcome. Good luck.

---

### Post by manoka on 2008-12-11
Sorry - I was able to solve this case ...

---

