---
title: "Cannot mount etc when installing."
date: 2011-02-07
forum: Installation &amp; Upgrades
---

### Post by lonewolf88 on 2011-02-07
Searching the forum see a few postings on this, but not a solution for me :-(

Trying to install 10.04.1 Kubuntu desktop to Toshiba T110 laptop
running Win 7, 4 Gig Ram, 32 bit o/s.

Downloaded iso from Ubuntu web site and burnt DVD.

No matter what I do I get the error message "cannot mount /dev/lop0
(/cdrom/casper/filesystem. squashfs" etc.

Searched by Google and this forum, tried various remedies Unebootin;  USB drive boot
up etc  etc;  still get same message.

Is there a workaround for what seems to be  a fairly common install
problem?

It shouldn't be this hard!

T.I.A.

---

### Post by ajgreeny on 2011-02-07
Use the md5sum check utlity that your current OS has to check the .iso file against the published md5sum figures which you can get from [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Also at the time you boot the live CD, use the menu option to check the CD before choosing to "Try Kubuntu".  It may be that the .iso file you downloaded, or the CD you burned is corrupt.

---

