---
title: "Unable to install"
date: 2017-02-06
forum: Installation &amp; Upgrades
---

### Post by johnnykick on 2017-02-06
I have a Dell Inspiron 6000 running and unpatched Win XP.  I tried installing I386.iso and get the error:  Kernal requires an x86-64 CPU but detected an i686 CPU.  Get the same error when I try to install AMD64.ISO.  Thoughts?

---

### Post by ubfan1 on 2017-02-06
Are you sure you got the 
[ubuntu-16.04.1-desktop-i386.iso]("http://releases.ubuntu.com/16.04.1/ubuntu-16.04.1-desktop-i386.iso")  file for your 32 bit install?

---

### Post by johnnykick on 2017-02-06
I downloaded this:  [http://files.downloadnow.com/s/software/14/51/73/90/ubuntu-14.04.4-desktop-i386.iso?token=1486386749_01da310a96a2c29f659a8a4d54bb46e7&fileName=ubuntu-14.04.4-desktop-i386.iso](http://files.downloadnow.com/s/software/14/51/73/90/ubuntu-14.04.4-desktop-i386.iso?token=1486386749_01da310a96a2c29f659a8a4d54bb46e7&fileName=ubuntu-14.04.4-desktop-i386.iso)

---

### Post by QIII on 2017-02-06
Why are you downloading from an anonymous third party?  You can't know that the file is valid -- or even safe.

---

### Post by yancek on 2017-02-06
> Kernal requires an x86-64 CPU but detected an i686 CPU

That message tells you that your hardware is only 32bit capable and you are using a 64bit iso.  Make sure you get the 32bit download.

---

### Post by wildmanne39 on 2017-02-06
That link does not work for me.

---

### Post by johnnykick on 2017-02-06
Give me a good link.

---

### Post by QIII on 2017-02-06
He means your link does not work, johnnykick.

You were given a good link to 16.04 by ubfan1.

---

### Post by johnnykick on 2017-02-06
Sorry about that...too much Canadian Mist.  I got it from here:  [http://download.cnet.com/Ubuntu-32-bit/3000-18513_4-170729.html](http://download.cnet.com/Ubuntu-32-bit/3000-18513_4-170729.html)

---

### Post by mörgæs on 2017-02-07
Ubuntu is not for an Inspiron 6000. I recommend that you try some light distros like [Lubuntu]("http://www.lubuntu.me").

If you can wait a few days then 16.04.2 is available. It contains all the bug fixes that you otherwise should have applied to a 16.04.1-install.

---

### Post by gordintoronto on 2017-02-07
You have a 12-year-old computer. One potential issue is memory; modern Linux distros might run with 1 GB of memory, but 2 GB is much better, and 4 GB is a little better. The base memory for the 6000 was 512 MB, and that's not going to cut it. 

Get the 32-bit download for Ubuntu Mate. [https://ubuntu-mate.org/download/](https://ubuntu-mate.org/download/)

---

