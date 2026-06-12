---
title: "Debian upgrade method, again (with more skill!)"
date: 2010-10-15
forum: Installation &amp; Upgrades
---

### Post by quequotion on 2010-10-15
Nobody replied to my previous thread on using the debian method to upgrade ubuntu...

I'm going the same way again. Last time I left out some important steps (which may or may not have been necessary at the time) and some disturbing information about apt which I had not yet learned.

So here again, for anyone who's interested, is **The Debian Upgrade Method** slightly improved and less noobish.

First, there are very specific reasons why I want to upgrade this way and they are worth consideration:

1. I use about fifty PPAs and a few non-Ubuntu sources. I don't even want to tell you what happens to them and their packages if I upgrade the regular way. Suffice to say that it is disastrous in every possible way.

2. Last time I posted about this I was using the Internet exclusively through a socks5 proxy, which makes the standard upgrade *impossible*. This is no longer the case for me (since iPhone support has improved) but it is worth noting that this method *works* with dante (socksify).

So...
Based on information from [here](https://help.ubuntu.com/community/PinningHowto) and more importantly [here](http://www.xs4all.nl/~carlo17/howto/debian.html#errata) along with the apt manual, I've revised the method as follows:

**1. Configure Apt:**
In /etc/apt/apt.conf add```
APT::Default-Release "maverick";
APT::Clean-Installed "false";
``` Clean-Installed may not actually be necessary. I can't find any up-to-date first-hand information on this feature. At one time it did something great, but now it may not funciton at all. To be sure, remove this line *after* you finish the upgrade.
**2. Update Sources list(s):**
The official repositories (use a local mirror, mine's in japan) look like this:
```
# Main Distribution
deb http://ubuntutym.u-toyama.ac.jp/ubuntu/ maverick restricted universe multiverse main # Ubuntu Maverick Meerkat
deb-src http://ubuntutym.u-toyama.ac.jp/ubuntu/ maverick restricted universe multiverse main # Ubuntu Maverick Source
deb http://ubuntutym.u-toyama.ac.jp/ubuntu/ maverick-security restricted universe multiverse main # Maverick Security
deb-src http://ubuntutym.u-toyama.ac.jp/ubuntu/ maverick-security restricted universe multiverse main # Maveric Security Source
deb http://ubuntutym.u-toyama.ac.jp/ubuntu/ maverick-updates restricted universe multiverse main # Maverick Updates
deb-src http://ubuntutym.u-toyama.ac.jp/ubuntu/ maverick-updates restricted universe multiverse main # Maverick Updates Source
deb http://ubuntutym.u-toyama.ac.jp/ubuntu/ maverick-proposed restricted multiverse universe main # Maverick Proposed
deb-src http://ubuntutym.u-toyama.ac.jp/ubuntu/ maverick-proposed restricted multiverse universe main # Maverick Proposed Source
deb http://ubuntutym.u-toyama.ac.jp/ubuntu/ maverick-backports restricted multiverse universe main # Maverick Backports
deb-src http://ubuntutym.u-toyama.ac.jp/ubuntu/ maverick-backports restricted multiverse universe main # Maverick Backports Source

# Canonical
deb http://archive.canonical.com/ubuntu maverick partner # Canonical Maverick
deb http://archive.canonical.com/ubuntu maverick-security partner # Canonical Maverick Security
deb http://archive.canonical.com/ubuntu maverick-updates partner # Canonical Maverick Updates
deb http://archive.canonical.com/ubuntu maverick-proposed partner # Canonical Maverick Proposed
deb http://archive.canonical.com/ubuntu maverick-backports partner # Canonical Maverick Backports

# Medibuntu
deb http://packages.medibuntu.org/ maverick free non-free # Medibuntu Maverick
deb-src http://packages.medibuntu.org/ maverick free non-free #Medibuntu Maverick Source
```* This could be /etc/apt/sources.list but see "Tips" below for some suggestions. Make sure you have a backup of your original lucid list(s) somewhere.

**3. Check what apt wants to do**
Update your sources:```
sudo apt-get update
```This will check all the archives for maverick. It will list all the ones that 404 (many PPAs do not yet have Maverick branches) so you can comment them out in your source list(s). I use a tag like "#NOMAVERICK" (before the "deb" and "deb-src" lines).
Check on dist-upgrade *but don't go through with it*.
```
sudo apt-get dist-upgrade
```
Say NO! You don't really want to upgrade, not yet. Scroll up to see the list of packages to upgrade, newly install and especially - **remove**.
Check if packages to remove have maverick versions:
```
apt-cache policy package1 package2 package3 package4 etc
```
Some will and some won't. Some have been replaced, others are incompatible. In the case that a maverick package has a lower version than a lucid ppa package, you still want the maverick version (for compatibility).

**4. Fix downgradable packages**
in **/etc/apt/preferences** add```
Package: [package1 that apt wants to remove rather than downgrade]
Pin: release a=maverick
Pin-Priority: 990

Package: [package2 that apt wants to remove rather than downgrade]
Pin: release a=maverick
Pin-Priority: 990

Package: [etc]
Pin: release a=maverick
Pin-Priority: 990

```This will convince apt to downgrade most of the appropriate packages to maverick rather than remove them from your system. It doesn't work for all of them, probably because of complex dependency problems. Check dist-upgrade again and keep a list of any important packages that are being removed. You can also check the "newly install" list for packages that replace them, which should have similar names.

**5. Upgrade**
Once you've gotten apt to agree to downgrade those pesky packages (there may be a few that refuse to cooperate, but they can be reinstalled later), it's time for the actual upgrade. ```
sudo apt-get dist-upgrade
``` Cross your fingers and hope for the best.


***Post upgrade***
The upgrade process stopped a few times for errors. Most of the time ```
sudo apt-get -f install
``` will get it going again. Apt is a busy guy and has a lot on his mind; you'll have to excuse him if he forgets what he's doing now and then. Sometimes I got around conundrums with an extra ```
sudo apt-get dist-upgrade
``` 

Some errors are more troublesome, like a problem I had with a PPA version of libgirepository (1.0-0). The package for the new version (1.0-1) does not list this one as "conflicting" so it doesn't require apt to remove the old version before installing the new version. Luckily apt is pretty smart, and it wont overwrite an existing library so easy... even though it's ok in this case. Solution: use dpkg to remove the old version ```
sudo dpkg -r libgirepository1.0-0
``` and then ```
sudo apt-get -f install
``` to get the upgrade rolling again. Luckily, for that particular package there wasn't a long chain of dependencies to remove along with it.

I can't account for any and all packages out there in the world, but between apt and dpkg you should be able to sort out most of the caveats in this method. I do not recommend to use aptitude; it has funny ways of making decisions and if you don't watch it carefully it will break things.


Tips:
Source lists:
1. Break up your sources.list file. This way you can easily cut out certain sources by renaming the file (*.list -> *.list.exclude). If you've added third-party repositories using the Karmic/Lucid method, you're going to have a messy directory full of tiny text files.
2. When editing your source lists, be sure not to make any duplicates and check for typos. Apt will not work if something is wrong.
3. Google each of your third party repositories. Some have changed names, some have changed URLS, some are not yet updated. You can do this after the upgrade.

---

### Post by oOarthurOo on 2010-10-15
There's nothing about this that is Debian in any way whatsoever. It violates most (if not all) of the recommendations in the apt manual.

Rather than set apt-default release in apt:conf, you should pin repositories (not individual packages) using the apt/preferences file.

Problematic individual packages that you don't want downgraded should simply be held (apt and aptitude both do this). 

It kinda looks like you already found the mixed repositories how-to on the debian forusm, but the roderick webpage linked is a better method, and also more in keeping with the apt/aptitude manuals. 

On the other hand, you've actually tested this and got it to work, so kudos on that.

---

### Post by kerry_s on 2010-10-15
it's only a matter of time before it breaks. if you want to do it the debian way use debian, ubuntu is not debian, it's based on debian, but ubuntu makes a whole lot of changes under the hood & some conflict with the debian way of things.

---

### Post by quequotion on 2010-10-16
> **oOarthurOo said:**
> There's nothing about this that is Debian in any way whatsoever. It violates most (if not all) of the recommendations in the apt manual.

Rather than set apt-default release in apt:conf, you should pin repositories (not individual packages) using the apt/preferences file.

Problematic individual packages that you don't want downgraded should simply be held (apt and aptitude both do this). 

It kinda looks like you already found the mixed repositories how-to on the debian forusm, but the roderick webpage linked is a better method, and also more in keeping with the apt/aptitude manuals. 

On the other hand, you've actually tested this and got it to work, so kudos on that.

I think you missed something. I *want* the packages to downgrade (to their available maverick version). That's why I've pinned individual packages.

Much of apt's documentation is outdated and/or inaccurate. The apt-preferences documentation is downright misleading and things like pinning repositories don't actually work the way they seem like they would or should.

This method does work, although it's not something you should do without cause and it's not perfect. I'll add some instructions for post-upgrade maintenance in a little while.

The regular upgrade method tends to remove hundreds of packages without explanation. Many of them may be outdated, but sometimes they're just unavailable or incompatible or only being removed because one of their dependencies' dependencies was removed and often they're more important than the upgrade manager will bother to say.

"apt-get dist-upgrade" is intended to be used for major upgrades, including upgrading the complete distribution. i've found this to be less of a headache than sorting out my system after the usual upgrade manager decimates my libraries. Because it's a feature of apt, and an old one, and I have read instructions for upgrading Debian in a very similar way, I thought "The Debian Way" was a good enough name for this method..

Ubuntu is not Debian, I know. It's Debian with more updates, more backports, a modified kernel, etc etc... but they are family.

---

