---
title: "Problems installing from USB device"
date: 2010-11-10
forum: Installation &amp; Upgrades
---

### Post by partyk1d24 on 2010-11-10
So I created a start up USB and I try to install it on a computer I have, however, everytime I try I get the following error repeated...

[35.877830] end_request: I/O error, dev fd0, sector 0
[35.877869] Buffer I/O error on device fd0, logical block 0

I found this post here [Problem with floppy]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1604438") but my motherboard (as far as I can tell) requires me to emulate the USB using the force FDD option. 

Can I do anything to fix this? I tried emulating a hard drive instead but then it doesn't boot up into ubuntu.

Jackie

---

### Post by C.S.Cameron on 2010-11-10
Have you checked the MD5SUM of your Ubuntu iso?

---

### Post by Tal Ormanda on 2010-11-11
Did they fix USB installs yet?

[http://ubuntuforums.org/showthread.php?t=1593206](http://ubuntuforums.org/showthread.php?t=1593206)

---

### Post by darkhelmetchris on 2010-11-11
> **partyk1d24 said:**
> ...but my motherboard (as far as I can tell) requires me to emulate the USB using the force FDD option.

Hi Jackie,

I have had some similar problems in the past with booting USB on systems that don't "like" to boot with USB with standard options.  I have 2 suggestions:

1.  The PLoP boot manager has worked for me in the past to get you to a "more compatible" USB boot if your hardware lacks the support for it.  You might try that.  It can be found here:  [http://www.plop.at/en/home.html](http://www.plop.at/en/home.html)

2.  Since you're mostly concerned with getting Ubuntu installed, perhaps connecting an internal or external CD-ROM for a one-time boot from CD is a better option.  That tends to be more compatible with older hardware or with a bios that doesn't have good USB boot options.

Hope some of that helps.  Cheers.

---

### Post by partyk1d24 on 2010-11-11
I got it working though I am still not completely sure how. I had checked md5 so I reset my BIOS to default disabled the floppy and tried it again (hdd as fdd) and everything installed. I blame it on the gremlins :-) .

---

### Post by darkhelmetchris on 2010-11-11
> **partyk1d24 said:**
> I got it working though I am still not completely sure how. I had checked md5 so I reset my BIOS to default disabled the floppy and tried it again (hdd as fdd) and everything installed. I blame it on the gremlins :-) .

Nice.  Glad to hear you got it worked out.

---

