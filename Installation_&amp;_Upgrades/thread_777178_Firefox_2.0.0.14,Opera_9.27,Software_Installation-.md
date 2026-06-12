---
title: "Firefox 2.0.0.14,Opera 9.27,Software Installation- Ubuntu 5.10?"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by slavii on 2008-05-01
Hello,
I can't install Firefox 2.0.0.14 and Opera 9.27 on Ubuntu 5.10
for firefox it is a deb package,I install it with sudo,but there is an error:needs libqt3-mt,which needs more libraries.
for opera-also
I'm downloading the packages specified for Ubuntu 5.10,but they can't be installed
What I have to do ? Do I have to install 7.10 or 8.04,so these and other programs run?

---

### Post by slavii on 2008-05-01
and one more question:
how to install
-RPM
-tar.gz
-deb
in Ubuntu 5.10
Which is the right way,maybe there I'm wrong

---

### Post by linux phreak on 2008-05-01
In my opinion 8.04(latest) will work better for you .

---

### Post by Steve1961 on 2008-05-01
Based on your questions I'd suggest sticking with the package manager to install programmes until you get to know your way around the Linux system. I'm assuming that you're not an experienced user. Also, upgrade to Hardy if you want the latest packages and security.

---

### Post by Sef on 2008-05-01
> I can't install Firefox 2.0.0.14 and Opera 9.27 on Ubuntu 5.10

5.10 is not longer supported.  There are no security updates or any other ones available now.  It is advisable to update to Hardy Heron or another supported Ubuntu version.

---

### Post by capink on 2008-05-01
As people suggested above, it is advisable that you upgrade to latest version. However, if you want to stick to 5.10 you can still install those packages (provided they are targeted at 5.10) as follows:

```
sudo dpkg -i path/to/the/deb/pacakge
```

That command is likely to produce some errors if the dependencies are not satisfied. To remedy this run the following command to install the missing dependencies form the repositories:

```
sudo apt-get install -f
```

---

