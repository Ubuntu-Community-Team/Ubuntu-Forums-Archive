---
title: "upgrade issue"
date: 2014-08-03
forum: Installation &amp; Upgrades
---

### Post by HR70s on 2014-08-03
My computer is a gigabyte motherboard pentium D 3.0 GHZ x2 32 bit. I upgraded to 14.04 LTS ran about a week then this red triange with an exclamation mark at the top of desk top.. says "update information is outdated : This could be caused by a network problem or a repository is no longer available" Manually update and watch for failing repositories.
Everything seems to work ok So what is it.

---

### Post by sudodus on 2014-08-03
I think the automatic updating system has a problem, and you need to do it manually. From a terminal window run the following commands, originally posted by *oldfred*. Use ***sudo*** to get superuser privileges. You may need to run the list of commands more than once.

```
# This will reinstall if not current. (from my chroot procedure which does not have sudo on every line,
# so use the sudo -i first).
 
#if not chroot use: sudo -i

#houseclean
apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean

#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first

#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade

# fix Broken packages -f 
sudo apt-get -f install
dpkg --configure -a

```

---

### Post by kc1di on 2014-08-03
you can try this see if it clears the problem.
in a terminal do the following:
```
sudo apt-get update
```
```
sudo apt-get upgrade
```
```
sudo apt-get clean
```

if it spits out any error messages post them here.

---

### Post by HR70s on 2014-08-03
Thanks guys
 soon as I did the autoclean the red triangle went away. I noticed it did get rid of alot

---

### Post by sudodus on 2014-08-03
If this solved your problem, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED :-)

---

