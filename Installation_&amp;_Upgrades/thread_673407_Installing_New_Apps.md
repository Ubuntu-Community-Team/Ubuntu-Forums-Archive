---
title: "Installing New Apps"
date: 2008-01-20
forum: Installation &amp; Upgrades
---

### Post by UrosP on 2008-01-20
Hey guys!

I have a serious problem.

I go to Add/Remove applications, and try to install new application. But on each try, it says it is unable to fetch some files. Every time it goes like that. I've tried going through main server, US server, my country (Serbia) server... each time same story.

I also tried sudo apt-get update but it displays errors only.

I don't know how to solve this problem. I want to install new apps, but this stops me doing so :(

I'm operating on Ubuntu 7.10 Gutsy Gibbon, by the way.


Please help!
Thanks in advance :)



~ Ubuntu Rocks :D ~

---

### Post by forestpixie on 2008-01-20
do this from a terminal 

cat /etc/apt/sources.list

does each line have a # in front of it apart from one which starts deb-cdrom

if so open software sources in system>admin

make sure main, universe, restricted and multiverse are ticked and cd-rom isn't and reload

if however the sources.list doesn't have #'s on all the lines post the output here

next time you're posting - could you post the error you're getting so we don't have to get telepathy out :)

---

### Post by UrosP on 2008-01-20
Thanks for your quick reply. I appreciate it.

Sorry for not posting the output. I'm a newbie :)

Anyway, I found somewhere trying doing this.
sudo cp /etc/apt/sources.list /etc/apt/sources.list.old
sudo gedit /etc/apt/sources.list

And then put this:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

##Universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## Multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Backports

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Canonical Partner Repository 

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free

My Linux machine is currently turned off, so I'll post the output tomorrow.
Meanwhile, please look into my sources.list :)


Thanks


~Ubuntu Rocks :D~

---

### Post by zvacet on 2008-01-20
Are you behind proxy?Do you have working connection,because source list look good.Try in programs>accessories>terminal

```
sudo apt-get update
```

---

### Post by UrosP on 2008-01-21
I'm not behind proxy, I go through router. I had to edit one line in one file to get my Internet work tho. Maybe that causes the problem?

Also, I tried sudo apt-get update. It results in errors. :(

---

### Post by forestpixie on 2008-01-21
> It results in errors

do it again and post the errors

---

### Post by UrosP on 2008-01-23
Sorry for late reply. Here's the output:

[http://scorch94.exofire.net/output.txt](http://scorch94.exofire.net/output.txt)

---

