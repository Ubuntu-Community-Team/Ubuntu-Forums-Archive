---
title: "Ubuntu Server Edition Install Broken"
date: 2008-04-14
forum: Installation &amp; Upgrades
---

### Post by knopfler on 2008-04-14
I have tried installing

server Edition

1.  Ubuntu 7.10   -downloaded from (UK -Oxford university computer services)
2. Ubuntu 6.06  - downloaded from (Uk - Oxford university + Kent University mirror service)


In both the scenarios , i was successful in verifying the MD5 checksum of the downloaded ISO file 

After writing the iso file  to a CD , i have tried to verify the copy running "CD integrity check"  , this check is found to fail reporting following errors for 

ubuntu 6.06.2-server-i386
./pool/restricted/l/linux-restricted-modules-2.6.15/linux-restricted-modules-2.6.15.51-386_2.6.15.12-51.1_i386.deb failed the MD5 checksum verification 
 
I have even tried to copy "linux-restricted-modules-2.6.15.51-386_2.6.15.12-51.1_i386.deb " locally to the hard disk drive , copying fails with CRC error. 

Has anyone managed to get arround this problem , it seems to me that both the server installation are broken. Is there a alternate way to install Ubuntu server 6.06

---

### Post by koenn on 2008-04-14
sounds like the iso as a whole is OK (or at least it passes md5 checksum check,) but that one file got corrupted/modified before or while the iso was created. strange. 
maybe try a new image from  a different download mirror ?

[http://ftp.belnet.be/mirror/ubuntu.com/releases/](http://ftp.belnet.be/mirror/ubuntu.com/releases/)
[http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)

if they all produce the same error, probably something went wrong when building the images.

---

### Post by SumnerBoy on 2008-06-26
I have just tried downloading 8.04 server ISO from 3 different mirrors, and using BitTorrent, all download ok and the MD5 check passes. However when I verify the CD from within the install it fails everytime.

Anyone seeing this? Any ideas how to get around it?

I have burnt about 8 CDs now, in 2 different machines, from 4 different sources...help!

BTW - I have also tried the install verification in 2 different machines - fails in both.

---

### Post by NullHead on 2008-06-27
The work around is to order a disk from ship-it and wait 6 weeks for delivery.

---

