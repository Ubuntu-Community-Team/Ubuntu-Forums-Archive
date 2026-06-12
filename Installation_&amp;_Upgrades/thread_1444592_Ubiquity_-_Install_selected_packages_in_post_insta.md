---
title: "Ubiquity - Install selected packages in post installation"
date: 2010-04-01
forum: Installation &amp; Upgrades
---

### Post by uonedang on 2010-04-01
Hello all,

I created a customized karmic iso that allows to install the image onto the hard 
drive automatically with usage of preseed configuration file.

I want to embed installation of additional packages and run some configuration 
commands after installation in the preseed file.

I have the 2 directories and files: pool and dist  :
.
./pool/abc1.deb
./pool/abc2.deb
.....
./pool/abcn.deb

./dist/Packages.gz


Do I have the above directory structure properly setup ?

What do I need to put in the preseed file to install packages abc1, abc2  and run commond xyz (/usr/bin/xyz) before the installation completes and exits?


what are the formats for commands:

tasksel 
d-i preseed/late_command ?

Thanks in advance ...

Dang

---

### Post by uonedang on 2010-04-12
Hi all,

I tried the following command (added the preseed file) : (ubuntu/karmic)

**d-i pkgsel/include string abc**

where I have 2 directories under cdrom:

pool/abc.deb
dists/Packages.gz


but I did not see the package abc installed or any evident that it tried to install this package.

 Any suggestion or hint where I should look at ?

Thanks

Dang

---

