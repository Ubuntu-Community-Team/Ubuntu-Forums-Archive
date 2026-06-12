---
title: "[SOLVED] I tested Hardy and I'd like to test Intrepid. Never done virtual install."
date: 2008-06-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by philinux on 2008-06-10
Whats the best way to do this. I'd heard that there's no usb support.

Where  do I start with this.

Thanks in advance

---

### Post by dicecca112 on 2008-06-10
[How to VMWare in Ubuntu 8.04 - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=779934")
[How To: Install VirtualBox on Ubuntu 8.04LTS (Hardy Heron) [Tutorial] - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=770745")

---

### Post by philinux on 2008-06-10
I'll check them out - which is best?

Probably a can of worms question.

Should have also said which is easier.

---

### Post by Bou on 2008-06-10
I've just recently started using Virtualbox and it's really really easy.

Only drawback is, there is no graphical acceleration.

---

### Post by plun on 2008-06-10
Yup, Virtualbox is great....

**The howto is outdated**

Latest download from Sun

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

Manual
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

The manual is worth reading a little....:)

---

### Post by philinux on 2008-06-10
Yep realised it was out of date.

Got the latest Virtualbox running. Hardy installed and updating. 

New toy. 

Now how to sort out the screen resolution.

---

### Post by plun on 2008-06-10
Well... its more then a toy....:)

I have OpenSolaris, Fedora 9 and XP as guest OS.

First install addons within Chapter 4

Chapter 4.3.1 describes it for Linux

[http://www.virtualbox.org/download/1.6.2/UserManual.pdf](http://www.virtualbox.org/download/1.6.2/UserManual.pdf)

4.3.2 about Video res.


Have Fun.....!

---

### Post by aamukahvi on 2008-06-11
On a Hardy guest, once you install Guest Additions, the resolution will scale to match the guest window size. Nice stuff.

---

### Post by philinux on 2008-06-11
> **aamukahvi said:**
> On a Hardy guest, once you install Guest Additions, the resolution will scale to match the guest window size. Nice stuff.

Until there's a kernel update then you have to reinstall it.

---

### Post by machoo02 on 2008-06-12
No...you don't have to re-install it.  All you have to do is recompile the kernel module```
sudo /etc/init.d/vboxdrv setup
```

---

