---
title: "Reading package lists... Error!"
date: 2007-08-09
forum: Installation &amp; Upgrades
---

### Post by nbharatha on 2007-08-09
Hello Ubuntu Guru's !!

Objective : I'm looking to customize Ubuntu and install DB2 v9 in that.

Gutsy build : desktop live cd and took daily build 20070808.
Referring :Guide at  [https://help.ubuntu.com/community/LiveCDCustomization?highlight=%28LiveCDCustomization%29](https://help.ubuntu.com/community/LiveCDCustomization?highlight=%28LiveCDCustomization%29)

ERROR :
After chroot'ing, I'm unable to add / remove any packages!
Following is the error thrown to me :
root@ubuntu:/# apt-get update -q
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release
gpgv: Signature made Fri Aug 10 00:36:30 2007 UTC using DSA key ID 437D05B5
gpgv: Good signature from "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>"
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages [1084kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages [7650B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources [302kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources [2091B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources
Fetched 1397kB in 9s (155kB/s)
Reading package lists...
E: Couldn't make mmap of 25165824 bytes - mmap (19 No such device)
W: Unable to munmap
E: The package lists or status file could not be parsed or opened.
root@ubuntu:/# 

Details of my laptop:
Dell Latitude 620
1GB RAM

Attached is the dmesh output from chroot jail

Any help is highly appreciated.

Thanks,
Naveen.

---

### Post by cosmoshell on 2007-12-17
having same problem

---

### Post by cosmoshell on 2007-12-17
i got it fixed by putting the files on an ext3 parttion had them on ntfs

---

