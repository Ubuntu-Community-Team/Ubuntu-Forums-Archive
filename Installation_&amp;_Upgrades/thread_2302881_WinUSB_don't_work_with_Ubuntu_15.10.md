---
title: "WinUSB don't work with Ubuntu 15.10"
date: 2015-11-14
forum: Installation &amp; Upgrades
---

### Post by TBK on 2015-11-14
I'm using Ubuntu 15.10 32 bit and I can't use WinUSB (to install Window 10), I have tried to install WinUSB with 3 deb file (winusb_1.0.11+saucy1_i386.deb ; winusb_1.0.11+trusty1_i386.deb ; winusb_1.0.11+vivid1_i386.deb) via USC but all of them can't run, I also have had WinUSB work with Ubuntu 15.04, 14.04, Linux Mint 17.x.
Now, how to use WinUSB on Ubuntu 15.10?

---

### Post by oldos2er on 2015-11-14
What does "can't run" mean? Did the program install successfully? Any error messages?

---

### Post by mikewhatever on 2015-11-14
Looks like you need to use WinUSB for 15.10, and not the old old versions.

---

### Post by grahammechanical on 2015-11-14
winusb is not in the Ubuntu repositories. We have to install a PPA (Personal Package Archive) and install it from there but there is not a PPA for 15.10.

If you install that PPA in 15.10 its URL will include "wily" in its address. You will need to edit the URL in Software & Updates to replace "wily" with "vivid" otherwise you will get an error when you try to install winusb because there is not a PPA repository for winusb in 15.10 (wily). But even then you may have problems running the utility becasue it has not been updated for Ubuntu 15.10.

[http://askubuntu.com/questions/489546/installing-winusb-on-ubuntu-14-04](http://askubuntu.com/questions/489546/installing-winusb-on-ubuntu-14-04)

[URL="https://launchpad.net/~colingille/+archive/ubuntu/freshlight"]https://launchpad.net/~colingille/+archive/ubuntu/freshlight

[/URL]Try using something else. such as UNetbootin.

Regards.

---

### Post by TBK on 2015-11-14
After I clicked on WInUSB icon on the laucher, I saw that my cursor change status to "wait" but then have no anything appeared.
WinUSB installed successfully, I didn't see any error messages. I didn't install WinUSB via ppa but using deb file. Before, although I was using Ubuntu 14.04 Trusty and Linux Mint 17.2, I could insitall and use WinUSB using "winusb_1.0.11+saucy1_i386.deb".
WinUSB is easy, and I have used it to install window 8 and window 10 successfully.
Seem Unetbootin doesn't support Window

---

### Post by corneliuss2 on 2015-11-19
It's quite a hassle to make it work, but it is possible. You may need to compile it from source.

It is described here: [http://onetransistor.blogspot.com/2015/11/how-to-install-winusb-in-ubuntu-1510.html](http://onetransistor.blogspot.com/2015/11/how-to-install-winusb-in-ubuntu-1510.html)

---

### Post by thanhan.nguyenphu on 2015-11-19
> **corneliuss2 said:**
> It's quite a hassle to make it work, but it is possible. You may need to compile it from source.

It is described here: [http://onetransistor.blogspot.com/2015/11/how-to-install-winusb-in-ubuntu-1510.html](http://onetransistor.blogspot.com/2015/11/how-to-install-winusb-in-ubuntu-1510.html)

I cant see it. this link is erro.

---

### Post by corneliuss2 on 2015-11-20
> **thanhan.nguyenphu said:**
> I cant see it. this link is erro.
The link is OK. What error do you get?

---

