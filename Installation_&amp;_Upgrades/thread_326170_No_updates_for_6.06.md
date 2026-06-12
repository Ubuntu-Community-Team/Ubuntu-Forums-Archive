---
title: "No updates for 6.06"
date: 2006-12-27
forum: Installation &amp; Upgrades
---

### Post by Jonte-- on 2006-12-27
Hello

I've not been able to find any updates for the last few weeks, I tried to change respetories but still the same. And I guess that the linux community haven't taken a brek for 1½ months...

Here's my sources.list

```
## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted


```

---

### Post by Sef on 2006-12-27
What error messages do you get when you try and update?

---

### Post by Jonte-- on 2006-12-27
> **Sef said:**
> What error messages do you get when you try and update?

Nothing, it just says that my system is up to date. But since it's been this for a quite a long time I don't think it is. I have a version of Openoffice since july, firefox is still at 1.5.

---

### Post by robbie75 on 2006-12-27
That's because of the version ofyour ubuntu:
you said that you've got 6.06 wich means "stable LTS"
so you do not havc to expect for continuous
packages update.
If you wish to have newer packages you got 
to move to edgy,or for the newest, feisty ;)
[INDENT][/INDENT]

---

### Post by Jonte-- on 2006-12-27
> **robbie75 said:**
> That's because of the version ofyour ubuntu:
you said that you've got 6.06 wich means "stable LTS"
so you do not havc to expect for continuous
packages update.
If you wish to have newer packages you got 
to move to edgy,or for the newest, feisty ;)
[INDENT][/INDENT]

But I do suppose there should be security updates and bugfixes?

---

### Post by Zimmer on 2006-12-27
> **Jonte-- said:**
> But I do suppose there should be security updates and bugfixes?
Yep, when required. Means you are not wasting bandwidth and time as the OS is stable... :)

---

