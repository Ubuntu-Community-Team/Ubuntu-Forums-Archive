---
title: "[SOLVED] Can't upgrade 7.10 to 8.04"
date: 2008-06-25
forum: Installation &amp; Upgrades
---

### Post by pieroxy on 2008-06-25
The Update Manager tells me:

> Could not calculate the upgrade

A unresolvable problem occurred while calculating the upgrade

This can be caused by:
* Upgrading to a pre-release version od Ubuntu
* Running the current pre-release version of Ubuntu
* Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug ..........

Here is the content of my /etc/apt/sources.list:

```
deb http://de.archive.ubuntu.com/ubuntu/ gutsy main restricted multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://de.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://de.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://de.archive.ubuntu.com/ubuntu/ gutsy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://fr.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://fr.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted multiverse universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe

## MEDIBUNTU REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
#deb http://fr.packages.medibuntu.org/ gutsy free non-free
#deb-src http://fr.packages.medibuntu.org/ gutsy free non-free


############### opensync.org ###################
# deb http://www.in.fh-merseburg.de/~jahn/ edgy main
# deb-src http://www.in.fh-merseburg.de/~jahn/ edgy main
# deb http://www.in.fh-merseburg.de/~jahn/opensync-0.21/ edgy main
# deb-src http://www.in.fh-merseburg.de/~jahn/opensync-0.21/ edgy main
# deb http://archive.ubuntu.com/ubuntu/ edgy-updates main
# deb http://archive.ubuntu.com/ubuntu/ feisty-backports main
# deb http://security.ubuntu.com/ubuntu edgy-security main

```


Before posting I already disabled Medibuntu and removed all packages installed from Medibuntu and Opensync that I identified with:

```
fgrep -B 5 Medibuntu /var/lib/dpkg/status | grep Package:
fgrep -B 5 -i Opensync /var/lib/dpkg/status | grep Package:
```

I removed the packages with:

```
sudo aptitude remove --purge mplayer amarok acroread ffmpeg
sudo aptitude remove libopensync-plugin-google-calendar libopensync-plugin-moto libopensync-plugin-palm opensync-plugin-irmc python2.4-opensync libopensync-plugin-sunbird language-pack-fa libopensync-plugin-python libopensync0 libopensync-plugin-syncml opensync-plugin-evolution libopensync-plugin-synce libopensync-plugin-file

```

Still, no luck... Can anyone help ?

---

### Post by abn91c on 2008-06-25
try using different repositories like the main server or the USA servers

---

### Post by pieroxy on 2008-06-25
Thanks for the quick answer !

I tried with this file (I left out the comments):
```
deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe


deb http://security.ubuntu.com/ubuntu hardy-security main restricted multiverse universe
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted


```

with the same results.

---

### Post by Pumalite on 2008-06-25
Check /etc/apt/sources.list.d
(Medibuntu has a separate folder somewhere in /etc/apt)

---

### Post by pieroxy on 2008-06-25
```
pieroxy@pieroxy-edgy:/etc/apt/sources.list.d$ ls
medibuntu.list  medibuntu.list.distUpgrade
pieroxy@pieroxy-edgy:/etc/apt/sources.list.d$ cat medibuntu.list
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
# deb http://packages.medibuntu.org/ feisty free non-free
# deb-src http://packages.medibuntu.org/ feisty free non-free
pieroxy@pieroxy-edgy:/etc/apt/sources.list.d$ cat medibuntu.list.distUpgrade
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
# deb http://packages.medibuntu.org/ feisty free non-free
# deb-src http://packages.medibuntu.org/ feisty free non-free
pieroxy@pieroxy-edgy:/etc/apt/sources.list.d$ 

```

---

### Post by Pumalite on 2008-06-25
Get rid of it.

---

### Post by pieroxy on 2008-06-25
Ok, I got rid of the directory (mv'ed it to my home directory) but the same error message appears.

---

### Post by Pumalite on 2008-06-25
Post:
df -h
And your specs.

---

### Post by pieroxy on 2008-06-26
```
pieroxy@pieroxy-edgy:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3              18G   16G  2.0G  89% /
varrun                633M  240K  633M   1% /var/run
varlock               633M     0  633M   0% /var/lock
udev                  633M  152K  633M   1% /dev
devshm                633M     0  633M   0% /dev/shm
/dev/hda1              19G   17G  2.1G  89% /media/hda1
/dev/sda1             294G  291G  3.2G  99% /media/raid-backup
/dev/sdb1             294G  291G  3.1G  99% /media/md2
/dev/hde1             151G  148G  3.0G  99% /media/torrent

```

Specs:
Sempron 2500+, 1.3GB RAM, Nvidia GC

My Ubuntu was an Edgy Eft and was upgraded ever since. 

Please let me know if you need anything else.

---

### Post by Pumalite on 2008-06-26
You might want to try this:

sudo sed -i 's/gutsy/hardy/' /etc/apt/sources.list 

sudo apt-get update 

sudo apt-get dist-upgrade

---

### Post by pieroxy on 2008-06-26
Do you know how risky that would be?

I kind of know that procedure, but I guess the installer is doing something more than this... So I won't get a real hardy upgrade with this trick...

Thanks for the tip anyways. I'll keep it in mind as a last resort.

---

### Post by Pumalite on 2008-06-26
If your system is not truly prepared for an upgrade, it may be taking a risk.

---

### Post by pieroxy on 2008-06-26
If you guys see nothing else... I'll probably try it, backing up my / partition first.

What is a system "truly prepared for an upgrade" ? Is it something complex ?

---

### Post by Pumalite on 2008-06-26
Totally updated, no third parties in your sources.list, enough space, your hardware able to run the new OS.

---

### Post by pieroxy on 2008-07-05
Can someone mark the thread as fixed ?

I did what you suggested:

```
sudo sed -i 's/gutsy/hardy/' /etc/apt/sources.list
sudo aptitude update
sudo aptitude dist-upgrade 
```

And it showed me the error that got the whole thing to fail:

```
The following packages are BROKEN:
  nvidia-glx-new-dev
```

And proposed to remove the package ubuntu-desktop to solve the problem ...

I Ctrl-C'ed the dist-upgrade, restored my sources.list file, removed the nvidia-glx-new-dev package and did the upgrade through the regular way. It worked like a charm.

Thanks again.

---

### Post by kostkon on 2008-07-05
> **pieroxy said:**
> I did what you suggested:

```
sudo sed -i 's/gutsy/hardy/' /etc/apt/sources.list
sudo aptitude update
sudo aptitude dist-upgrade 
```

And it showed me the error that got the whole thing to fail:

```
The following packages are BROKEN:
  nvidia-glx-new-dev
```

And proposed to remove the package ubuntu-desktop to solve the problem ...

I Ctrl-C'ed the dist-upgrade, restored my sources.list file, removed the nvidia-glx-new-dev package and did the upgrade through the regular way. It worked like a charm.

Thanks again.
Nice that everything ended up OK!
> **pieroxy said:**
> Can someone mark the thread as fixed ?
Only you can mark this thread as solved. ;)

---

### Post by Pumalite on 2008-07-05
> **pieroxy said:**
> Can someone mark the thread as fixed ?

I did what you suggested:

```
sudo sed -i 's/gutsy/hardy/' /etc/apt/sources.list
sudo aptitude update
sudo aptitude dist-upgrade 
```

And it showed me the error that got the whole thing to fail:

```
The following packages are BROKEN:
  nvidia-glx-new-dev
```

And proposed to remove the package ubuntu-desktop to solve the problem ...

I Ctrl-C'ed the dist-upgrade, restored my sources.list file, removed the nvidia-glx-new-dev package and did the upgrade through the regular way. It worked like a charm.

Thanks again.

You are welcome. Good luck!

---

