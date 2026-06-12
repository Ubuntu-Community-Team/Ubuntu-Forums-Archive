---
title: "Is there a patch for the slow minimizing/maximizing with fglx in lucid?"
date: 2010-04-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by salva84 on 2010-04-23
Im having slow minimizing/maximizing with fglx in ubuntu 10.04 with the ati drivers, I had a ppa in ubuntu 9.10 to solve, but this repo ([https://launchpad.net/~k0ekk0ek/+archive/ppa/+packages](https://launchpad.net/~k0ekk0ek/+archive/ppa/+packages)) is not prepared for lucid.  What can I do? I have an ati 5000 and there is not open source drivers yet.

Thank you

---

### Post by csaket on 2010-04-23
Roll your own:

wget [http://launchpadlibrarian.net/32728179/xserver-xorg-backclear.patch](http://launchpadlibrarian.net/32728179/xserver-xorg-backclear.patch)
sudo apt-get build-dep xorg-server
apt-get source xorg-server
cd xorg-server-*
patch -p1 < /path/to/xserver-xorg-backclear.patch
sudo apt-get install devscripts
debuild
cd ..
sudo dpkg --install xserver-xorg-core*.deb

It can take upto 15 minutes.
A common error that comes up at the end is for pgp which can be ignored.

---

### Post by csaket on 2010-04-23
You're in luck as it seems that a ppa might be available:
[https://edge.launchpad.net/~bryceharrington/+archive/violet]("https://edge.launchpad.net/~bryceharrington/+archive/violet")

More details:
[http://www.mail-archive.com/ubuntu-x-swat@lists.launchpad.net/msg64518.html]("http://www.mail-archive.com/ubuntu-x-swat@lists.launchpad.net/msg64518.html")

Bug 568988:
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/568988]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/568988")

---

### Post by salva84 on 2010-04-23
> **csaket said:**
> You're in luck as it seems that a ppa might be available:
[https://edge.launchpad.net/~bryceharrington/+archive/violet]("https://edge.launchpad.net/~bryceharrington/+archive/violet")

More details:
[http://www.mail-archive.com/ubuntu-x-swat@lists.launchpad.net/msg64518.html]("http://www.mail-archive.com/ubuntu-x-swat@lists.launchpad.net/msg64518.html")

Bug 568988:
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/568988]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/568988")

I have added this ppa, but my update manager says that there is not new updates :S

---

### Post by csaket on 2010-04-23
The ppa has 2:1.7.6-2ubuntu3 and the latest xorg is 2:1.7.6-2ubuntu5.

So you might have the latest xorg installed already.

The alternative is to build yourself.

---

### Post by salva84 on 2010-04-23
> **csaket said:**
> The ppa has 2:1.7.6-2ubuntu3 and the latest xorg is 2:1.7.6-2ubuntu5.

So you might have the latest xorg installed already.

The alternative is to build yourself.

I dont understand this line

"patch -p1 < /path/to/xserver-xorg-backclear.patch"

---

### Post by csaket on 2010-04-23
> **salva84 said:**
> I dont understand this line

"patch -p1 < /path/to/xserver-xorg-backclear.patch"

if you downloaded the patch to ~/Downloads then this becomes
patch -p1 < ~/Downloads/xserver-xorg-backclear.patch

---

### Post by salva84 on 2010-04-23
> **csaket said:**
> if you downloaded the patch to ~/Downloads then this becomes
patch -p1 < ~/Downloads/xserver-xorg-backclear.patch

LOL, It was obvious XD thank you, I've finished, only restart...

---

### Post by csaket on 2010-04-23
sudo service gdm restart (warning, will close all programs and bring you back to the login screen)

---

### Post by salva84 on 2010-04-23
> **salva84 said:**
> LOL, It was obvious XD thank you, I've finished, only restart...

Perfect, It works! thank you a lot

---

### Post by quad65 on 2010-04-24
Is it possible that applying this patch could have broken my CPU Frequency Scaler?

It used to change between 800, 1.6 and 2.5 but it no longer works.

Edit: powernowd somehow got uninstalled. Installed again, everything back to normal.
Sorry about this.

---

