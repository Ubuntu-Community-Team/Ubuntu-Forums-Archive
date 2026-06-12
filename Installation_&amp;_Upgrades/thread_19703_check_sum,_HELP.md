---
title: "check sum, HELP"
date: 2005-03-13
forum: Installation &amp; Upgrades
---

### Post by afroman on 2005-03-13
How do i do a check sum, the md5sum is a text document!
I am using winXP id this helps!
Thanks

---

### Post by Gary Powers on 2005-03-13
Google "WINMD5SUM" and you will find a Windows version straight away.  Download, install and your in business.

Gary

---

### Post by Buffalo Soldier on 2005-03-13
:)

Get the MD5SUMS file from the server you're downloading. Example if you're downloading warty-release-live-i386.iso from [http://releases.ubuntu.com/warty/](http://releases.ubuntu.com/warty/) then the MD5SUMS file will be [http://releases.ubuntu.com/warty/MD5SUMS](http://releases.ubuntu.com/warty/MD5SUMS)

Download the warty-release-live-i386.iso file. Then compare the checksum of the downloaded file with the number that you got from the MD5SUMS file (dac84a3abf5a1a104d768d569a62579e).

What software can you use to compare the checksum?

You can use winMd5Sum from [http://winmd5sum.solidblue.ca](http://winmd5sum.solidblue.ca). It is a "...a simple open source Windows MD5 checker. In onther words, it's a utility to calculate the MD5 checksum of a file..."

---

