---
title: "Source code missing on all ubuntu mirrors"
date: 2011-05-08
forum: Installation &amp; Upgrades
---

### Post by hummelscott83 on 2011-05-08
Hey,

Searching for an ancient file... "ubuntu-8.04-src-1.iso"

Does anyone know where I can find it?

Note that I have already checked the primary ubuntu mirrors that host DVDs... they all have: "ubuntu-9.04-src-1.iso"/"ubuntu-10.04-src-1.iso"/"ubuntu-11.04-src-1.iso"; but not "ubuntu-8.04-src-1.iso"...

I am trying to organize an internal "complete" archive for computer science and engineering at the Univ of Mich.

Thanks,

Scott

---

### Post by An Sanct on 2011-05-08
Any special reason, it has to be 8.04-src-**1**.iso?

Take a look at [this location]("ftp://ftp.gnome.org/mirror/cdimage.ubuntu.com/releases/hardy/release/source/").

---

### Post by hummelscott83 on 2011-05-08
An Sanct:

Thanks for responding. Actually, yes. We need exactly this file... "ubuntu-8.04-src-1.iso". It is the only one we cannot find.

We already have "ubuntu-8.04.1-src-1.iso", "ubuntu-8.04.2-src-1.iso", "ubuntu-8.04.3-src-1.iso", "ubuntu-8.04.4-src-1.iso", 8.10, 9.04, 9.10, 10.04..., 10.10, 11.04 mirrored locally.

For completeness, we are hoping to obtain all versions.

Thanks,

Scott

---

### Post by An Sanct on 2011-05-08
Well ... I took another look with uncle google ...

8.04 is hardy :) so I searched for hardy

and got this:
[ftp://128.118.2.96/pub/.mirrors/1/cdimage.ubuntu.com/cdimage/hardy/daily/20080903.1/source/hardy-src-1.iso](ftp://128.118.2.96/pub/.mirrors/1/cdimage.ubuntu.com/cdimage/hardy/daily/20080903.1/source/hardy-src-1.iso)

Does this help?

---

### Post by hummelscott83 on 2011-05-08
An Sanct:

Wow. I am shocked this file still exists. Unfortunately, I do not think it is the correct one.

Ubuntu files in the format "hardy-src-1.iso" or "lucid-src-1.iso" are usually overnight or development builds and not actual releases... Releases are usually in the format "ubuntu-10.04-src.iso"

For example, these files are very different:

[http://old-releases.ubuntu.com/releases/releases/10.04/release/source/](http://old-releases.ubuntu.com/releases/releases/10.04/release/source/)
(ubuntu-10.04-src-1.iso)

[http://cdimage.ubuntu.com/lucid/source/current/source/](http://cdimage.ubuntu.com/lucid/source/current/source/)
(lucid-src-1.iso)

Awesome effort though.

Thanks,

Scott

---

### Post by mörgæs on 2011-05-08
Just for your information: The ISO is not source code. It is compiled (binary) code, ready to run.

---

### Post by hummelscott83 on 2011-05-08
mörgæs:

I understand; my apologies for the miscommunication. Irregardless, we are still in search of this file.

Thanks,

Scott

---

### Post by An Sanct on 2011-05-09
Then I can give you this piece of information ...

The MD5 hash of the file you are looking for is
```
d4904eb993a24eeaf5299e8665035de1
```Yes, I know its not a real breakthrough, but that is the info I got from a really [old Korean site]("http://pc1412.iptime.org:88/bbs/zboard.php?id=memo&page=2&sn1=&divpage=1&sn=off&ss=on&sc=on&select_arrange=vote&desc=asc&no=7")...

---

### Post by An Sanct on 2011-05-09
hm ... maybe it just simply does not exist :)

[https://bugs.launchpad.net/ubuntu/+bug/234585](https://bugs.launchpad.net/ubuntu/+bug/234585)

Altho it is about Kubuntu and Xubuntu, it might concern the Vanilla Ubuntu too...

---

