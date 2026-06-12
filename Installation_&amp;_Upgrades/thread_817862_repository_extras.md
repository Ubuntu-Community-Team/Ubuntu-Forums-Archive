---
title: "repository extras"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by sfreed on 2008-06-04
While looking for some new and updated software, I found what I was looking for under [http://security.ubuntu.com/ubuntu/pool/](http://security.ubuntu.com/ubuntu/pool/)

Before I just start downloading stuff, what exactly is this tree?  Is it associated with any particular version of ubuntu? Is there any way of accessing it through apt?

tanks,
steve.

---

### Post by zvacet on 2008-06-04
I don´t know which version of Ubuntu you are using but if it is Hardy edit your source list 

```
gksudo gedit /etc/apt/sources.list
```

and add this lines

> deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

If you are not using Hardy then in these lines replace hardy with your version name.Save file and close it.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by sfreed on 2008-06-04
No, that's not correct. I am running hardy. I do get the security updates. Those come from [http://security.ubuntu.com/ubuntu/dists/hardy](http://security.ubuntu.com/ubuntu/dists/hardy).

What I am asking about is [http://security.ubuntu.com/ubuntu/pool/](http://security.ubuntu.com/ubuntu/pool/) and more specifically, [http://security.ubuntu.com/ubuntu/pool/universe/g/gadmin-dhcpd/](http://security.ubuntu.com/ubuntu/pool/universe/g/gadmin-dhcpd/)  and [http://security.ubuntu.com/ubuntu/pool/universe/g/gadmin-bind/](http://security.ubuntu.com/ubuntu/pool/universe/g/gadmin-bind/)

These are not in the normal hardy distribution. ...Hardy has the older versions wrapped up in "gadmintools". I need the newer versions.

So the question still remains, what is this "pool" tree? Is it "safe" to use stuff found in there?  And, is there a way to get to it through apt?

thanks,
steve.

---

