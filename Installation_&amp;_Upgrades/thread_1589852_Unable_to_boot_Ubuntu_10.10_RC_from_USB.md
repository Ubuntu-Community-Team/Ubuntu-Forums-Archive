---
title: "Unable to boot Ubuntu 10.10 RC from USB"
date: 2010-10-07
forum: Installation &amp; Upgrades
---

### Post by DJazZ on 2010-10-07
I have just downloaded Ubuntu 10.10 Desktop/Netbook Remix Release Candidate and made a live usb with Pendrivelinux. Then I boot it in my Acer Aspire One A110 (8gb SSD model) and i get this screen:

> SYSLINUX 3.86 2010-04-01 EBIOS Copyright (C) 1994-2010 H. Peter Anvin et al

Nothing more.

Should I just wait until 10.10.10 for the finished 10.10? Or is there any way fixing this?

---

### Post by sikander3786 on 2010-10-07
Use unetbootin to burn the USB drive. There has been an issue with the new version of Pendrivelinux.

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

---

### Post by DJazZ on 2010-10-07
Ok, i tried unetbootin. Now i get this:

First i see the previous error flash by, then the unetbootin menu. I choose (default) and i get this screen:
> No init found. Try passing init= bootarg.

BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu4) built in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
:|

---

### Post by Jechem on 2010-10-07
Hello,

I think the problem is from your ISO. You can try downloading it again and use Unetbootin. 

I´ve installed it to my EEEPC 4G and it works out of the box.

[http://jechem.wordpress.com/2010/10/03/tested-ubuntu-10-10-maverick-meerkat-on-eeepc-4g/](http://jechem.wordpress.com/2010/10/03/tested-ubuntu-10-10-maverick-meerkat-on-eeepc-4g/)

---

### Post by sikander3786 on 2010-10-07
Check MD5SUM of the downloaded image. If it doesn't match, re-download it as mentioned by Jechem.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by tuxcantfly on 2010-10-07
> **DJazZ said:**
> Ok, i tried unetbootin. Now i get this:

First i see the previous error flash by, then the unetbootin menu. I choose (default) and i get this screen:

:|

Are you using the version of UNetbootin from the Ubuntu 10.04 repository? That's currently an old release which predates support for Ubuntu 10.10 (though it's being updated); only newer releases of UNetbootin (490 and above) can correctly create an Ubuntu 10.10 Live USB. You can either get it from the site, as mentioned in the above posts [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) or see [http://launchpad.net/~gezakovacs/+archive/ppa](http://launchpad.net/~gezakovacs/+archive/ppa) for packages.

---

### Post by DJazZ on 2010-10-08
No, I'm using Windows. But it all works now, i had version 471 of UNetbootin, downloaded 491.
There was nothing wrong with the ISO then.
I'm installing it atm :)

---

### Post by trentscott on 2010-10-10
Alternate Fix: [http://ubuntuforums.org/showpost.php?p=9948986&postcount=8](http://ubuntuforums.org/showpost.php?p=9948986&postcount=8)

---

### Post by lunatico on 2010-10-11
> **tuxcantfly said:**
> Are you using the version of UNetbootin from the Ubuntu 10.04 repository? That's currently an old release which predates support for Ubuntu 10.10 (though it's being updated); only newer releases of UNetbootin (490 and above) can correctly create an Ubuntu 10.10 Live USB. You can either get it from the site, as mentioned in the above posts [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) or see [http://launchpad.net/~gezakovacs/+archive/ppa](http://launchpad.net/~gezakovacs/+archive/ppa) for packages.

Yup. updated from launchpad and it work now. Thanks!

---

### Post by lunatico on 2010-10-12
> **lunatico said:**
> Yup. updated from launchpad and it work now. Thanks!

Not true... installer crashed at the end. Tried creating the USB stick with Lili and same thing.

---

### Post by lunatico on 2010-10-12
> **DJazZ said:**
> No, I'm using Windows. But it all works now, i had version 471 of UNetbootin, downloaded 491.
There was nothing wrong with the ISO then.
I'm installing it atm :)

Did it worked?

---

### Post by DJazZ on 2010-10-14
Oh yeah, all worked. But it was so slow so I re-installed with Ubuntu 10.10 Desktop. 10.10 seems also buggy with the executable bit on my SD card (where I keep all files, as the SSD is only 8Gb).
I am unable to download files to it too... odd.. Anyhow uNetbootin worked fine when updated to latest version.

---

### Post by lunatico on 2010-12-01
I still haven't found a solution for this.
The installer crashes at the end. It might be related to this bug:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/658865](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/658865)

I couldn't do the workaround there....

Any ideas?

---

### Post by Eternal_Light on 2010-12-30
Scott could you please repost the other solution u gave a link to? its dead now and i really need to try it out. thanx :)

---

### Post by Beaucoq on 2011-08-02
SYSLINUX 3.86 2010-04-01 EBIOS Copyright (C) 1994-2010 H. Peter Anvin et al

Anyone else still getting this message?
Tried burning the img via unetbootin and universal usb installer and the same thing.

Im using a m11x r3

Every computer Ive used for the last 5 years has run Ubuntu and Im going crazy using Windows on this thing.  Any help is appreciated

---

### Post by Beaucoq on 2011-08-02
Oh and Im trying 11.04, not 10.10

---

