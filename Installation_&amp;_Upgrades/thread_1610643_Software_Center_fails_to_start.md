---
title: "Software Center fails to start"
date: 2010-10-31
forum: Installation &amp; Upgrades
---

### Post by gruppler on 2010-10-31
Let me start by saying that I rarely post my problems because I'm usually able to find solutions by searching.  However, after several weeks of fruitless intermittent searching, I've decided to throw in the towel and ask for help.

After upgrading from 10.4 to 10.10, the Ubuntu Software Center refused to start, and I got an icon in the notification area saying that "a problem occurred when checking for the updates."  When I run software-center in the terminal, I get this error message:

```
Traceback (most recent call last):
  File "/usr/bin/software-center", line 88, in <module>
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 32, in <module>
    import xapian
  File "/usr/lib/python2.6/dist-packages/xapian.py", line 1278, in <module>
    Document.add_boolean_term = new_instancemethod(_xapian.Document_add_boolean_term,None,Document)
AttributeError: 'module' object has no attribute 'Document_add_boolean_term'
```

Likewise, when I run add-apt-repository, I get this:

```
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 8, in <module>
    from softwareproperties.SoftwareProperties import SoftwareProperties
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 25, in <module>
    import apt_pkg
ImportError: libapt-pkg-libc6.9-6.so.4.7: cannot open shared object file: No such file or directory
```

I've tried re-installing apt and all related packages, even dpkg, and even downloaded the apt package directly from the ubuntu web site, but no matter what I do, I can't run these things.  Aptitude and apt-get seem to work fine, though.

---

### Post by P4man on 2010-11-01
Wild guess: have your checked your sources.lst for anomalies? Perhaps recreate it?

---

### Post by gruppler on 2010-11-01
Thanks for the suggestion, but it looks OK to me.
```
# deb http://download.tuxfamily.org/gericom/libreoffice / # disabled on upgrade to maverick
deb http://ubuntu.mirrors.tds.net/ubuntu/ maverick main universe restricted multiverse
deb http://security.ubuntu.com/ubuntu/ maverick-security universe main restricted multiverse
deb http://ubuntu.mirrors.tds.net/ubuntu/ maverick-updates universe main restricted multiverse
# deb http://ppa.launchpad.net/docky-core/ppa/ubuntu maverick main # disabled on upgrade to maverick
deb http://extras.ubuntu.com/ubuntu maverick main #Third party developers repository
deb http://download.tuxfamily.org/gericom/maverick / #gericom@maverick
```

How would I go about re-creating it?

---

### Post by P4man on 2010-11-01
nah, that looks fine. I just tried it here and I have no issues with those sources. I still think it could be something in that direction; perhaps check the files in 
/etc/apt/sources.list.d/

as well, or move them temporarily to another folder just to see if software center starts then.

---

### Post by gruppler on 2010-11-01
I tried moving sources.list.d to sources.list.d.bak, but that didn't seem to have any effect.  Thanks for the suggestion, though; please keep'em coming! =]

---

### Post by P4man on 2010-11-01
Bummer. Thats a dead end then.

You said you tried reinstalling all relevant packages, have you purged them too? Have you tried reinstalling  python-apt ?

---

### Post by gruppler on 2010-11-01
I have tried re-installing python-apt.  If I try to purge, for example, apt-utils or python-apt, aptitude tells me it wants to uninstall a ton of core packages. Is there a better way to do this?

---

### Post by Xavierll on 2010-11-01
I have exactly the same problem after upgrading from 10.04 to 10.10. I have tried reinstalling apt from my CD and from [http://mirrors.kernel.org/ubuntu/pool/main/a/apt/](http://mirrors.kernel.org/ubuntu/pool/main/a/apt/) without success.

---

