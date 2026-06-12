---
title: "configure error"
date: 2007-05-14
forum: Installation &amp; Upgrades
---

### Post by Barthpi on 2007-05-14
Hello,

I am quite new to linux, and i am trying to install the MEEP program. To do this, i have to install first a serie of library.  But each time i try to run the "configure" file of the installation package, i got the following error message. 

checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables

Can someone tell me how to solve this problem ?

many thanks,

Pierre

---

### Post by Vixis on 2007-05-14
Try to install this:
sudo apt-get install build-essential libc6-dev g++

Post your config.log output near error.

You also may need to install dev versions of your required packages. In common it is package_name-dev.

---

