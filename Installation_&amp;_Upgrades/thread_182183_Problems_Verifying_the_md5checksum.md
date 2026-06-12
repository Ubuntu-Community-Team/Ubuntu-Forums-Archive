---
title: "Problems Verifying the md5checksum"
date: 2006-05-25
forum: Installation &amp; Upgrades
---

### Post by Spinelli on 2006-05-25
I downloaded an iso image of ubuntu 5.10 AMD64 today. I verified the md5checksum of the image using these directions. I am currently running Ubuntu on my first hard drive.

[https://wiki.ubuntu.com/VerifyIsoHowto]("https://wiki.ubuntu.com/VerifyIsoHowto")

The md5checksum was fine, so I burned the iso image at 1x. I burned the cd using these directions. The md5checksum is 7fbe948be484ba2f4740ab6113890652

[https://wiki.ubuntu.com/BurningIsoHowto]("https://wiki.ubuntu.com/BurningIsoHowto")

Then I tried to verify the md5checksum after burning the cd. This is what I typed at the command line:

```
 wc -c ubuntu-5.10-install-amd64.iso
672561152 ubuntu-5.10-install-amd64.iso
```
And then I typed:
```
dd if=/dev/hdc | head -c 672561152 | md5sum
dd: reading `/dev/hdc': Input/output error
1313592+0 records in
1313592+0 records out
672559104 bytes transferred in 247.259818 seconds (2720050 bytes/sec)
cf94c3ff0f18f8ae52e703b09b72d2c4  -

```
I do not understand what the above error message means. I tried to install ubuntu on my second hard drive using the cd. When the installer tried to unpack the base system it failed. Every time I have tried to install ubuntu this error occurs. I just keep on trying over and over until it eventually works. As far as I know there could be a couple of problems.
1. The cds I use are bad.(I use Verbatim)
2. It is just a bad burn.
Any suggestions would be greatly appreciated. Thank You.

---

### Post by Sef on 2006-05-25
Download bittorrent and use it to download Ubuntu: it automatically md5sums the download.

---

### Post by Spinelli on 2006-05-25
I downloaded the Kubuntu and checked the md5checksum. It was fine. After 2 attempts it finally installed correctly.

---

### Post by Sef on 2006-05-27
Sometimes it takes a few times to get a good download.  Once it took me about 6 times, to get a good download where the numbers matched.

---

### Post by morequarky on 2006-05-30
I don't know the fancy way to check the md5sum.  I just go to a terminal and attempted "md5sum <filename>" and after some number crunching it gives me the number and I compare it visually to what I get online.

:)

---

### Post by Spinelli on 2006-05-31
I finally figured out what my problem was.:-D I switched to Sony CD-Rs and they seem to work a lot better than Verbatim! Thanks for the suggestions everyone.

---

