---
title: "Amarok borkanised"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ktar on 2009-10-03
So I update, forgot that Kpackagekit was forked up, and got [the usual error message](http://ubuntuforums.org/showthread.php?p=8044234#post8044234). I then find out that one of the updates was to Amarok, which has  disappeared. So I go to Terminal and do a total purge and attempt to reinstall, but get this.

```

The following packages are BROKEN:
  amarok
The following NEW packages will be installed:
  amarok-utils{a} libtag-extras1{a}
0 packages upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 7,644kB/7,898kB of archives. After unpacking 23.0MB will be used.
The following packages have unmet dependencies:
  amarok: Depends: amarok-common (= 2:2.2.0-0ubuntu1) but it is not installable
The following actions will resolve these dependencies:

Keep the following packages at their current version:
amarok [Not Installed]

Score is -9881

Accept this solution? [Y/n/q/?]

```

Where can I get amarok-common 2.2.0 from?

---

### Post by aamukahvi on 2009-10-03
You just need to wait and try again when amarok-common is built.
The latest version is 2.1.90 and amarok depends on 2.2.0.

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=amarok-common](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=amarok-common)

---

### Post by ktar on 2009-10-03
> **aamukahvi said:**
> You just need to wait and try again when amarok-common is built.
The latest version is 2.1.90 and amarok depends on 2.2.0.

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=amarok-common](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=amarok-common)

Monday I guess. Thanks.

---

### Post by talkingwires on 2009-10-03
Some could argue that Amarok has been has been borked since 2.0 dropped. Just saying'. :P

---

### Post by froggyswamp on 2009-10-03
Don't we get Amarok 2.2 final into Karmic?
It was released a few days ago.

---

### Post by raindog on 2009-10-03
I certainly hope they get amarok-common 2.2.2.0 built soon.  No amarok over the weekend.  :(  I guess if they don't then I'll have to hope the kubuntu ppa beta team builds it.

---

### Post by aamukahvi on 2009-10-04
You could probably also install amarok 2.1.90 if you want it that bad :D

[https://launchpad.net/ubuntu/+source/amarok/2:2.1.90-0ubuntu1/+build/1256928](https://launchpad.net/ubuntu/+source/amarok/2:2.1.90-0ubuntu1/+build/1256928)

---

