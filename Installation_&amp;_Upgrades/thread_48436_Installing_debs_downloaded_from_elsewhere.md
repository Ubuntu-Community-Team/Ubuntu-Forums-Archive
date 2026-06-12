---
title: "Installing debs downloaded from elsewhere?"
date: 2005-07-12
forum: Installation &amp; Upgrades
---

### Post by Aurels on 2005-07-12
Hi.

I have a little problem, here it is:

I want to install some packages on my hoary computer but I haven't internet connexion on this machine.
The only computer I can use at the moment to connect to internet has a Win 98 SE system.

Would it be possible to download the debs from the mirror and copy them to the other computer my usb key and install them after?

I have tried to share the internet connexion by lan but I didn't find how on the windows 98 side.

Has someone an idea for me?

Thanks.

---

### Post by musicman2059 on 2005-07-12
Well, first off, the best place to get debs would be [http://packages.ubuntu.com](http://packages.ubuntu.com) as they are the same as the repositories you would use if you were downloading them using Synaptic.  Once you get there, just copy/move them over to your hard drive and type:

```
sudo dpkg -i /path/to/downloadedpackage.deb
```

---

### Post by kosmic on 2005-07-12
Hello, another way is ..

Create a directory ex.: mkdir /tmp/debs
move your deb files inside that directory

then do :
cd /tmp

sudo dpkg-scanpackages /debs/.* | gzip > Packages.gz
* Atention is Packages.gz and not packages.gz or PACKAGES.gz

then open Synaptic and go to 'Repositories' and and :
file:/tmp/debs /

update and install the programs with synaptic :)

---

### Post by Aurels on 2005-07-19
Thank you very much guys, I try that.

---

