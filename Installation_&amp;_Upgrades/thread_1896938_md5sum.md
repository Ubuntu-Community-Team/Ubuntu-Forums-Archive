---
title: "md5sum?"
date: 2011-12-18
forum: Installation &amp; Upgrades
---

### Post by Matrix01 on 2011-12-18
[ATTACH]209307[/ATTACH]
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

how do u use md5sum?
typed command, did not work.

---

### Post by yeats on 2011-12-18
For examples like this:

```
ubuntu@ubuntu-desktop:~$ cd Downloads
```

The "ubuntu@ubuntu-desktop:~$" part is just an example prompt.  Sometimes it will be just a "$" (or a "#" if the command is being run by the root user, something rare in Ubuntu examples).  Your prompt is "k@ubuntu:~$" instead.  So just do:

```
cd Downloads
md5sum your-actual-filename-here
```

where "your-actual-filename-here" is the actual name of the file you're trying to md5sum.

---

### Post by Matrix01 on 2011-12-18
[ATTACH]209348[/ATTACH]

output looks like this,
is this good?

> **yeats said:**
> For examples like this:

```
ubuntu@ubuntu-desktop:~$ cd Downloads
```The "ubuntu@ubuntu-desktop:~$" part is just an example prompt.  Sometimes it will be just a "$" (or a "#" if the command is being run by the root user, something rare in Ubuntu examples).  Your prompt is "k@ubuntu:~$" instead.  So just do:

```
cd Downloads
md5sum your-actual-filename-here
```where "your-actual-filename-here" is the actual name of the file you're trying to md5sum.

---

### Post by Lars Noodén on 2011-12-19
> **Matrix01 said:**
> [ATTACH]209348[/ATTACH]

output looks like this,
is this good?

There should be a list of MD5 checksums at the site you downloaded the CD image from.  Compare it to that to see if it is good.

e.g. [http://ftp.heanet.ie/pub/ubuntu-cdimage/releases/11.10/release/MD5SUMS](http://ftp.heanet.ie/pub/ubuntu-cdimage/releases/11.10/release/MD5SUMS)

---

### Post by Matrix01 on 2011-12-19
can md5sum tell same or different when iso file is pasted in terminal, and compared with iso file used as installation?

---

