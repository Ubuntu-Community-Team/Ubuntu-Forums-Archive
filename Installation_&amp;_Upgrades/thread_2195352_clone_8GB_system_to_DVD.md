---
title: "clone 8GB system to DVD"
date: 2013-12-23
forum: Installation &amp; Upgrades
---

### Post by George Heine on 2013-12-23
I have a laptop that may be starting to fail (lots of funny noises).  Existing system is 12.04 LTS, with much additional software, mostly from the repos but also a third-party printer driver and a few apps compiled from source.  Would like to clone the system onto a desktop (Dell Optilex FormFactor, about 6 years old), but the desktop will only boot from hard drive or from a CD/DVD.   Have seen many comments about Clonezilla in this forum, but the documentation a Clonezilla ([http://clonezilla.org](http://clonezilla.org)) says:

> Recovery Clonezilla live with multiple CDs or DVDs is not implemented  yet. Now all the files have to be in one CD or DVD if you choose to  create the recovery iso file.

The existing system on the laptop (everything except /home) takes about about 8GB of space, more than will fit on a DVD.  Does this mean the system needs to be rebuilt by hand?

Hope this makes sense.  Any ideas or suggestions would be appreciated -

Here is what the root directory looks like
```
$sudo du -csk /* |sort -k1n
0       proc
0       sys
0       vmlinuz
0       vmlinuz.old
4       cdrom
4       dev
4       opt
4       selinux
4       srv
16      lost+found
20      media
52      root
472     tmp
976     run
1868    mnt
8644    bin
8800    sbin
14784   etc
357144  boot
429808  var
1879516 lib
5243100 usr
5796844 home
13742064        total

```

---

### Post by electrohandyman501 on 2013-12-23
What is the hard disk interface of the desktop.
Look into a external usb hard disk "carriage" to install the desktop HD, for the purpose of transferring the data. Then you can re-install the disk into the desktop system after.

I personally haven't done any disk cloning to really know if it's a viable solution for an os boot situation, but I have done it for large quick(as quick as usb2.0 is, lol) data transfer.

---

### Post by Mark Phelps on 2013-12-24
> takes about about 8GB of space, more than will fit on a DVD -- ONLY -- if it is a dual-layer DVD.  Standard DVD capacity is a little over 4GB.

---

### Post by George Heine on 2013-12-25
Thanks for the suggestions.  A dual-layer DVD-R sounds easier to find and use.  Will try that first and report back.

---

