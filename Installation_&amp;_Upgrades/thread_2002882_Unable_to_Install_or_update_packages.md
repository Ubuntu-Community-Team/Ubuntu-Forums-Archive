---
title: "Unable to Install or update packages"
date: 2012-06-13
forum: Installation &amp; Upgrades
---

### Post by ihthisham007 on 2012-06-13
Hi All,
I am new to Ubuntu so bare with me please.

I installed Ubuntu 11.04 server and trying to run commands like
sudo apt-get update
sudo apt-get install build-essential

but get errors stating below.


Err [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) natty/main unzip i386 6.0-4ubuntu1
  Cannot initiate the connection to ca.archive.ubuntu.com:80 (91.189.88.24). - connect (101: Network is unreachable) [IP: 91.189.88.24 80]
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/u/unzip/unzip_6.0-4ubuntu1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/u/unzip/unzip_6.0-4ubuntu1_i386.deb)  Cannot initiate the connection to ca.archive.ubuntu.com:80 (91.189.88.24). - connect (101: Network is unreachable) [IP: 91.189.88.24 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

non of these commands work. Please help. Thank you.

---

### Post by cortman on 2012-06-13
Try changing your server mirror- you can do this in the Ubuntu Software Center.

---

### Post by ihthisham007 on 2012-06-13
I dont have a GUI interface installed. and I cant even ping the google.com. I have static IP setup. How can I make sure the server is connecting to internet? thanks

---

### Post by ihthisham007 on 2012-06-13
Found the issue- had a extra digit on broadcast IP. took me 2hrs to figure out. Thanks.

---

### Post by cortman on 2012-06-13
OK, good- glad it was that simple. Mark the thread [SOLVED], if you would, using the thread tools in the upper right. Good luck!

---

