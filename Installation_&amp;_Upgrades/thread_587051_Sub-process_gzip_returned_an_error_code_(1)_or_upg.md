---
title: "Sub-process gzip returned an error code (1) or upgrade from 7.04 to 7.10 fails"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by heu on 2007-10-22
Hello
I've been trying to upgrade kubuntu from 7.04 to 7.10 for about 1 week and it fails always the same point .  My network connection is working fine (Im getting about 80 kb/s through the install process ruling out chocking servers or other net related problems) and my box is pretty stable (no crashes or weird things have been happening). The error message I am getting is:

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)

When i get the file packages.gz  and try to unzip it manually using either my browser or wget and uncompressing it with gzip everything works fine. Could it be a bug in the upgrader ?? (I am using adept , which by the way was updated just 2 days ago).

Did anyone been experience this problem with the RC upgrade?

---

### Post by por100pre1 on 2007-10-23
Welcome to the forums, sorry for the delay. Try this: copy, paste and ENTER each one of these commands, one by one, in Terminal (**Applications> Accesories> Terminal**):

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```

```
gksudo gedit /etc/apt/sources.list
```

A text document will appear. Press **Ctrl+H** and replace **http://** with **ftp://** , be sure to click **Replace all**. Then try upgrading again. **Be sure to backup your user folder files to removable media or external hard disk drive before upgrading.**

---

### Post by inchaos on 2007-10-23
I had the exact same problem and this worked for me!

Thanks so much!

---

### Post by heu on 2007-10-24
ok. thank you :). Do you know what's causing it? As for marking the problem as solved I don't know..I would class it as solved if anybody else going through the update process ,from lets say now on, doesn't have to manually edit the sources.list file. Otherwise it is a workaround.

---

### Post by commonplace on 2007-10-24
I was having the exact same problem, and followed the steps to modify my sources. That got rid of the five errors I was getting, and now I'm down to just one:

> Failed to fetch [ftp://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.bz2](ftp://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)

Any ideas? This is a fairly stock install of 7.04, no third-party repos or anything added at all, really.

/Kevin

---

### Post by por100pre1 on 2007-10-24
> **commonplace said:**
> I was having the exact same problem, and followed the steps to modify my sources. That got rid of the five errors I was getting, and now I'm down to just one:

"Failed to fetch [ftp://security.ubuntu.com/ubuntu/dis...6/Packages.bz2](ftp://security.ubuntu.com/ubuntu/dis...6/Packages.bz2) Sub-process bzip2 returned an error code (2)"

Any ideas? This is a fairly stock install of 7.04, no third-party repos or anything added at all, really.

/Kevin

That seems to be a different issue. Maybe a slow  connection issue. Try this:

```
apt-get check
```

Post any error messages you get. :-k

---

### Post by por100pre1 on 2007-10-24
> **heu said:**
> ok. thank you :). Do you know what's causing it? As for marking the problem as solved I don't know..I would class it as solved if anybody else going through the update process ,from lets say now on, doesn't have to manually edit the sources.list file. Otherwise it is a workaround.

I have to agree with you. It is a common workaround for this issue, not sure what causes it.

---

