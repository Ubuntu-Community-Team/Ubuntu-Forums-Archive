---
title: "12,000 missing files"
date: 2015-06-14
forum: Installation &amp; Upgrades
---

### Post by Billy_Congo on 2015-06-14
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=15.04
DISTRIB_CODENAME=vivid
DISTRIB_DESCRIPTION="Ubuntu 15.04"
NAME="Ubuntu"
VERSION="15.04 (Vivid Vervet)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 15.04"
VERSION_ID="15.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"

I ran the following query to find missing files:

for p in $(dpkg-query -f '${Package} ' -W)
do
      dpkg -L $p | grep '^/' | while read file
      do
           [ -e "$file" ] || echo "$p is missing $file"
      done
done 

I got over 12,000 files missing.  Is this normal?  Attached is just 234 of them.

[ATTACH]262603[/ATTACH]

I used the following command to re-install these packages:

apt-get --reinstall install [I]package

[/I]No change.

---

### Post by tgalati4 on 2015-06-14
Your attachment didn't work.  Perhaps they are language files?  Does your distro work properly?  Why do you care about missing files in the Debian package database?

As I suspected, when I ran your script, I got a lot of missing files.  Most of them were for languages that I don't have installed, so dialog files for many, many programs are not installed unless you have those languages installed.

So, unless your distro is broken, I wouldn't worry about it.

---

