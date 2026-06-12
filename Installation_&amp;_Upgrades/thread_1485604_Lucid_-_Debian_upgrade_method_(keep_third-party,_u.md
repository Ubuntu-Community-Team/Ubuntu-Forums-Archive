---
title: "Lucid - Debian upgrade method (keep third-party, use socks-proxy, etc)"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by quequotion on 2010-05-17
Here's another upgrade method for anyone who, like me, had a heck of a lot of trouble with Ubuntu's upgrade manager.
If you'd like to keep your third party packages and upgrade them along with the official ones, or if you connect to the internet via a socks proxy or you just love editing configuration files--this is for you.

I believe this method may also reduce your post-upgrade woes.

*1. Apt configuration:*
in **/etc/apt/apt.conf** add ```
APT::Clean-Installed "false";
```in **/etc/apt/preferences** add ```
Package: *
Pin: release lucid
Pin-Priority: 1001
```The first one prevents a slew of packages installed by hand from being removed during the upgrade and the second allows lucid packages to override back-ported packages with higher version numbers.

*2. Source lists*:*
The official repositories look like this:
```
# Main Distribution
deb http://ubuntutym.u-toyama.ac.jp/ubuntu/ lucid restricted universe multiverse main # Ubuntu Lucid Lynx
deb-src http://ubuntutym.u-toyama.ac.jp/ubuntu/ lucid restricted universe multiverse main # Ubuntu Lucid Source
deb http://ubuntutym.u-toyama.ac.jp/ubuntu/ lucid-security restricted universe multiverse main # Lucid Security
deb-src http://ubuntutym.u-toyama.ac.jp/ubuntu/ lucid-security restricted universe multiverse main # Lucid Security Source
deb http://ubuntutym.u-toyama.ac.jp/ubuntu/ lucid-updates restricted universe multiverse main # Lucid Updates
deb-src http://ubuntutym.u-toyama.ac.jp/ubuntu/ lucid-updates restricted universe multiverse main # Lucid Updates Source
deb http://ubuntutym.u-toyama.ac.jp/ubuntu/ lucid-proposed restricted multiverse universe main # Lucid Proposed
deb-src http://ubuntutym.u-toyama.ac.jp/ubuntu/ lucid-proposed restricted multiverse universe main # Lucid Proposed Source
deb http://ubuntutym.u-toyama.ac.jp/ubuntu/ lucid-backports restricted multiverse universe main # Lucid Backports
deb-src http://ubuntutym.u-toyama.ac.jp/ubuntu/ lucid-backports restricted multiverse universe main # Lucid Backports Source

# Canonical
deb http://archive.canonical.com/ubuntu lucid partner # Canonical Lucid
deb http://archive.canonical.com/ubuntu lucid-security partner # Canonical Lucid Security
deb http://archive.canonical.com/ubuntu lucid-updates partner # Canonical Lucid Updates
deb http://archive.canonical.com/ubuntu lucid-proposed partner # Canonical Lucid Proposed
deb http://archive.canonical.com/ubuntu lucid-backports partner # Canonical Lucid Backports

# Medibuntu
# DOWN? deb http://packages.medibuntu.org/ lucid free non-free # Medibuntu Lucid
# DOWN? deb-src http://packages.medibuntu.org/ lucid free non-free #Medibuntu (source) - Ubuntu 9.10 "Lucid Lynx"
deb ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu/ lucid free non-free # Medibuntu Mirror Lucid
deb-src ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu/ lucid free non-free # Medibuntu Mirror Lucid (source)
```* This could be **/etc/apt/sources.list** but see "Tips" below for some suggestions...

*3. File limit**:*
Odds are a full upgrade will require the download of LOTS of packages., especially if you include PPAs and other thrid-party repos.
in **/etc/security/limits.conf** add```
root		soft	nofile		1000000
root		hard	nofile		1000000
```
Then run the commands```
$ sudo su
$ ulimit -n 1000000
```Notice the "sudo su", because ulimit can only be changed in a root terminal in Ubuntu.  Do not exit this terminal, you need to finish the upgrade from here.
**There are reasons why the file limit defaults so low. You *must* reset this after finishing the upgrade.

*4. Upgrade:* (via socks proxy with dante)
Do this with crossed fingers```
socksify apt-get update
socksify apt-get dist-upgrade
```This will give you a list of packages to upgrade/downgrade/install/remove. Make note of the removed packages.
Most are obsolete and incompatible, others are no longer available or supported. Check if there's anything you're going to want back.

***Tips:***
*Source lists:*
1. Use repository mirrors close to your geographical location.
2. Break up your sources.list file. (I've attached my files from **/etc/apt/sources.list.d/**) This way you can easily cut out certain sources by renaming the file (*.list -> *.list.exclude). If you've added third-party repositories using the Karmic method, you're going to have a messy directory full of tiny text files.
3. When editing your source lists, be sure not to make any duplicates and check for typos. The first couple of times I tried this, apt kept breaking down with "method 'ftp' failed". I had forgotten to comment out an extra medibuntu mirror, so apt was failing due to downloading the same package list from two repositories...
4. You should take a look on google for each of your third party repositories. Some have changed names, some have changed URLS, some are not yet updated for lucid.
*Post upgrade:*
1. Create a filter in Synaptic to look at packages that are "Not Installable".  Most of them will be outdated libraries you no longer need. A few will be packages you downloaded as .deb files and installed. (the usual upgrade process removes all of these...)
2. I had to reinstall a proprietary graphics driver, nVidia, which I believe is a transitional dependency problem. The nVidia driver package has a new naming scheme.
3. Some settings here and there have been reset but nothing important.
4. v4l-dvb is ***still broken*** in the official Ubuntu repositories. [See thread "Audio gone?"](http://ivtvdriver.org/pipermail/ivtv-users/2010-February/subject.html) (ivtv-users mailing list)
5. If you don't reset the file limit, you will notice apt/aptitude/synaptic and various other processes slow your computer down a great deal.

---

