---
title: "Server 11.10 MD5 Fail"
date: 2012-02-23
forum: Installation &amp; Upgrades
---

### Post by Stusy on 2012-02-23
I'm just building a backup sever using 11.10, but when I tried to install I received an error. It looked like a CD-ROM Error so I checked the disk for defects and it came up with:-

the ./pool/main/l/linux/linux-image-3.0.0-12-virtual_3.0.0-12.20_i386.deb file failed the MD5 checksum verification. Your CDROM or this file may have been corrupted.

Then tried the following:-
[LIST]
[*]Replaced CD_ROM drive. Twice !! Exact Same problem.
[*]Re-burnt the ISO image to a new disk. Exact Same problem.[*]Downloaded image again and re-burnt. Exact Same problem.
[*]Tried disk in another Machine. Exact same problem.
[/LIST]

Is there are problem with the image download from Ubuntu. The only thing I didn't do was Verify image after the image was burnt.

Many Thanks for any input

---

### Post by Stusy on 2012-02-23
Wrong topic

---

### Post by mastablasta on 2012-02-23
perhaps. you need to check the md5sum just after you download the image.

---

### Post by Stusy on 2012-02-23
I'm getting it from here:-

[http://www.ubuntu.com/download/server/download](http://www.ubuntu.com/download/server/download) 

and it doesn't provide the MD5 checksum

---

### Post by plucky on 2012-02-24
> **Stusy said:**
> I'm getting it from here:-

[http://www.ubuntu.com/download/server/download](http://www.ubuntu.com/download/server/download) 

and it doesn't provide the MD5 checksum

From [Here](http://releases.ubuntu.com/oneiric/)

Md5sums for Oneiric .iso files.

```
5e427f31e6b10315ada74094e8d5d483 *ubuntu-11.10-alternate-amd64.iso
24da873c870d6a3dbfc17390dda52eb8 *ubuntu-11.10-alternate-i386.iso
62fb5d750c30a27a26d01c5f3d8df459 *ubuntu-11.10-desktop-amd64.iso
c396dd0f97bd122691bdb92d7e68fde5 *ubuntu-11.10-desktop-i386.iso
f8a0112b7cb5dcd6d564dbe59f18c35f *ubuntu-11.10-server-amd64.iso
881d188cb1ca5fb18e3d9132275dceda *ubuntu-11.10-server-i386.iso
196f12bdbf60ee759e11d4986bc19ce3 *ubuntu-11.10-wubi-amd64.tar.xz
7ab19159b48e2135f82d76193e1a0d55 *ubuntu-11.10-wubi-i386.tar.xz
39656579e3b55b7cac29e191ac83ef92 *wubi.exe

```

Good Luck

---

