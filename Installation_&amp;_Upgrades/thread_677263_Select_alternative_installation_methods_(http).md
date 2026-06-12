---
title: "Select alternative installation methods? (http?)"
date: 2008-01-24
forum: Installation &amp; Upgrades
---

### Post by KimTas on 2008-01-24
According to some posts I have found (eg: [http://ubuntuforums.org/showpost.php?p=2493&postcount=2](http://ubuntuforums.org/showpost.php?p=2493&postcount=2) ) - when the Ubuntu installation fails on a CD, it should prompt me for other installation methods such as hard disk or http.

My CD installation fails when installing - but I do not seem to have options to install by another method.

Is there a way to manually start an http installation? (with the ISO on an http server?)

Cheers,
Kim

---

### Post by zvacet on 2008-01-24
Did you chek [md5sum](https://help.ubuntu.com/community/HowToMD5SUM) and did you chek disc for errors?

---

### Post by KimTas on 2008-01-24
Yep, MD5 is fine. I've tried the following:

1) Checked the MD5's match
2) Tried adding -d1 to the hdparm options doing an expert install
3) Tried the CD-ROM as Primary Master (rather than Slave)
4) Tried a different CD-ROM (a new Pioneer DVD combo drive)

(also posted here: [http://ubuntuforums.org/showthread.php?t=557103](http://ubuntuforums.org/showthread.php?t=557103) )

I've given up getting the CD to work, so trying to figure out another way that isn't too complicated. I have copied the contents of the ISO to an IDE hard disk - but not sure if that will actually work?

Cheers,
Kim

---

### Post by zvacet on 2008-01-24
Install from CD is not complicated,quite oposite.You can try alternate Cd,but in case you don´t feel like it you can try [this](https://help.ubuntu.com/community/RecoveryFromBadInstallCD).of course you will put name of your release insted of one on the page.Good luck!

---

### Post by KimTas on 2008-01-24
Thanks for that link - installing through that command line from another location I think will be the way to go...

However, when putting in these commands I get:

cd /target  - cd: can't cd to /target
wget [http://www.mydomain.com/image.iso](http://www.mydomain.com/image.iso) (where I put our image) - Host name lookup failure.

I guess at this stage of the install the system does not have network connectivity (we have a dhcp server)

I wonder if I put the image on an IDE hard disk... not sure what the commands would be though?

Thanks for your help!
Kim

---

### Post by KimTas on 2008-01-25
Figured out how to install from another location (http)  under the Expert Install. Have got the system up and running nicely now. Had to do a few other steps to get the CD working (see my other post here: [http://ubuntu-utah.ubuntuforums.org/showthread.php?p=4205886#post4205886](http://ubuntu-utah.ubuntuforums.org/showthread.php?p=4205886#post4205886) )

Cheers,
Kim

---

