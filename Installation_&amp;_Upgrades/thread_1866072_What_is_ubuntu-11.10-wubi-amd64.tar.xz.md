---
title: "What is ubuntu-11.10-wubi-amd64.tar.xz ?"
date: 2011-10-20
forum: Installation &amp; Upgrades
---

### Post by aurelieng on 2011-10-20
Hi all,

I'm planning to install 11.10 on a few computers with wubi. I was about to download wubi.exe and the desktop AMD64 ISO when I saw a file called "ubuntu-11.10-wubi-amd64.tar.xz" among the files I can download (see [here]("ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/releases/11.10/") for instance).

This XZ archive contains two files:
```

wubildr
root.disk

```

It seems to be a kind of "pre installed" wubi installation, but I can't find any documentation/howto.

Any idea ?

Best,

Aurel.

---

### Post by hari.iiitb on 2012-03-23
Assume you haved pasted wubi.exe and ubuntu-11.10-wubi-amd64.tar.xz in D:\

You have to use it like this

1. Open cmd
2. type

```

wubi.exe --dimagepath=d:\ubuntu-11.10-wubi-amd64.tar.xz

```

Wubi will open up. Press Install after selecting drive and size. Now instead of downloading the image, wubi will start extracting after you start choose a drive and press install.

---

