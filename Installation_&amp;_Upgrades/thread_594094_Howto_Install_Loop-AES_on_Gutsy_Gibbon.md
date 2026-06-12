---
title: "Howto Install Loop-AES on Gutsy Gibbon"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by george_koss on 2007-10-27
I just installed Gutsy on a fileserver, and concocted the following script to automate installation of Loop-AES.  Installation was smooth and flawless.   

#!/bin/bash
cd /usr/src
sudo apt-get install build-essential
sudo apt-get install debhelper 
sudo apt-get install module-assistant
sudo m-a fakesource
sudo apt-get install loop-aes-utils
sudo wget [http://http.us.debian.org/debian/pool/main/l/loop-aes/loop-aes-source_3.2b-1_all.deb](http://http.us.debian.org/debian/pool/main/l/loop-aes/loop-aes-source_3.2b-1_all.deb)
sudo dpkg -i loop-aes-source_3.2b-1_all.deb
sudo m-a auto-install loop-aes
sudo rmmod loop
sudo modprobe loop
echo "Done installing loop-aes!"

---

### Post by paranoid77 on 2008-05-20
Does anybody have an updated version of these instructions for Hardy? Many thanks.

I have tried various versions of loop-aes-source from Debian including loop-aes-source_3.1d-13etch2_all.deb and loop-aes-source_3.2c-2_all.deb but none of them compile. There already are similar bugs submitted in launchpad [https://launchpad.net/ubuntu/+source/loop-aes-source/+bugs](https://launchpad.net/ubuntu/+source/loop-aes-source/+bugs)

---

### Post by karmik on 2008-05-30
By following to the letter OP's guide and downloading the latest version of loop-aes source .deb package you should succeed. (Latest Loop-AES source package: [http://http.us.debian.org/debian/pool/main/l/loop-aes/loop-aes-source_3.2c-2_all.deb](http://http.us.debian.org/debian/pool/main/l/loop-aes/loop-aes-source_3.2c-2_all.deb))

---

