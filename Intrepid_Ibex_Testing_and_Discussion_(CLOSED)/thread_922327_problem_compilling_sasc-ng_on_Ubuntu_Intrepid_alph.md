---
title: "problem compilling sasc-ng on Ubuntu Intrepid alpha 5"
date: 2008-09-17
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by mannberg on 2008-09-17
This Is the steps I tried to get sasc ng to compile on Ubuntu Intrepid

sudo apt-get install build-essentials subversion
sudo apt-get install linux-libc-dev libssl-dev gettext
sudo apt-get install --reinstall linux-headers-2.6.27-3-generic

svn co [https://OpenSVN.csie.org/sascng/trunk](https://OpenSVN.csie.org/sascng/trunk) sasc-ng
cd sasc-ng/trunk/
make clean
./configure
make module

but the make command gives me an error: "Could not identify kernel" and exists.

Anyone got any luck compilling sasc?

---

### Post by covert on 2008-09-17
First of I am not sure if sasc-ng works with that kernel.

You need to edit config_dvb.pl in the dvbloopback/module folder to recognize the kernel. Search dvbn.happysat.org forums for the complete answer.

---

### Post by mannberg on 2008-09-17
> **covert said:**
> 
You need to edit config_dvb.pl in the dvbloopback/module folder to recognize the kernel.

I changed in config_dvb.pl from 2.6.26 to 2.6.27 and "make module" complaning about not finding dvbdev.h and using a canned header. But I get a seg fault when inserting dvbloopback.ko ($sudo insmod dvbloopback.ko -num_adapters=2). Any other tips?

---

