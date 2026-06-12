---
title: "Hash?"
date: 2008-04-23
forum: Installation &amp; Upgrades
---

### Post by metroidnemesis13 on 2008-04-23
What's the hash for the alternate iso for Ubuntu 8.04?  It's not posted yet, and I'm having trouble installing it, and I'm wondering if it's the disc consistency.

---

### Post by Pumalite on 2008-04-23
1b6c2d146ad317cf89cb5cf61127e264 *ubuntu-8.04-rc-alternate-amd64.iso
ce1bbda2791623a842d95096243db835 *ubuntu-8.04-rc-alternate-i386.iso
84bcc78154076ca4f2306319c73c186a *ubuntu-8.04-rc-desktop-amd64.iso
86dc6f4792fa5a69e73e30cd33cdfd11 *ubuntu-8.04-rc-desktop-i386.iso
fbdfe071d68f7c543d71200568de2c15 *ubuntu-8.04-rc-server-amd64.iso
a1ceed4dc0a9cdf3eac82644ef0a4d37 *ubuntu-8.04-rc-server-i386.iso
e6a531b607aaf1aa0944d189045a0c73 *wubi.exe

---

### Post by metroidnemesis13 on 2008-04-23
Okay, so the hashes are the same.  Why is linux not installing?  I've tried to install 8.04 alternate i386 three times and it ends with something about a bootstrap?  I tried different ways of partitioning it.  What have I done wrong?

---

### Post by mrproza on 2008-04-24
What are the hashes for 8.04 i386 alternate GA (released April 24)?

---

### Post by rclark68137 on 2008-04-24
[http://releases.ubuntu.com/8.04/MD5SUMS](http://releases.ubuntu.com/8.04/MD5SUMS)

7d0ac92c56361949d099dd9337c975e7 *ubuntu-8.04-alternate-amd64.iso
166991d61e7c79a452b604f0d25d07f9 *ubuntu-8.04-alternate-i386.iso
fc43f665ba51c4be0d95c011aefef45d *ubuntu-8.04-desktop-amd64.iso
8895167a794c5d8dedcc312fc62f1f1f *ubuntu-8.04-desktop-i386.iso
8a73cf85b04f37d5d91fb436525ea395 *ubuntu-8.04-server-amd64.iso
c3162b21757746c64a0a22cdd060b164 *ubuntu-8.04-server-i386.iso
cdd32124f23b455b0aa22cc3ff35ff35 *wubi.exe

---

### Post by eyelessfade on 2008-04-24
cdd32124f23b455b0aa22cc3ff35ff35 *wubi.exe
missmatch here.

a96aa69961f3ed80dd7a88fae1e28196 I get

---

### Post by zvacet on 2008-04-24
@ **eyelessfade**

Bad download.Try again.

---

### Post by eyelessfade on 2008-04-24
tried 4 times from 4 different mirrors.

---

### Post by eyelessfade on 2008-04-24
Oh yeah, I always get the same md5sum. Don't think it's a failed dl. :)

---

### Post by mikewhatever on 2008-04-24
> **eyelessfade said:**
> tried 4 times from 4 different mirrors.

Use bittorrent and stop clogging the servers. A torrent client will also make sure the hash matches.

---

### Post by eyelessfade on 2008-04-24
Oh yeah, I always get the same md5sum. Don't think it's a failed dl. :)

---

### Post by eyelessfade on 2008-04-24
Well the point is that there is a missmatch in the files. Which is not good at all. The point in having a gpg MD5SUM file is to know you got the right file and not a malware.

---

### Post by zvacet on 2008-04-25
Folow mikewhatever advice and try  download with torrent.Point download in folder where your previously downloaded Ubuntu is and torent will just check for corrupted files and replace them.Check md5sum again and if it is O.K. burn and install.

---

### Post by eyelessfade on 2008-04-25
I'm talking about wubi.exe as I have said. It's a 1.1MB file. don't even think its a torrent for it. But it doesn't matter because the _point_ is that the file on servers _DONT_ match the MD5SUM on the servers. I'm not the only one who found this.

[http://ubuntuforums.org/showthread.php?t=764898](http://ubuntuforums.org/showthread.php?t=764898)

It is a security problem and should be fixed ASAP.

---

