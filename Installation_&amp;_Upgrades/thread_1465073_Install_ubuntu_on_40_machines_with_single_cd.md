---
title: "Install ubuntu on 40 machines with single cd"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by amit@nitttrchd.ac.in on 2010-04-29
Just like in RPM based distributions we do installation thru NFS/HTTP/FTP by booting and use
ask method, and within 2-3 hrs parallely we install linux on 40 machines , now i want to replace it with ubuntu

similarly or some method i am looking for installing ubuntu on 40 machines thru one cd ,

on remaining machines i want to find option for n/w installation , LTSP is not reqd.

---

### Post by i.r.id10t on 2010-04-29
I'd set up PXE booting to the cd image on a server...

---

### Post by senor_smile on 2010-06-01
> **i.r.id10t said:**
> I'd set up PXE booting to the cd image on a server...

Do you know of any howto's to help us along with this? 

I followed the instructions at 

[http://www.howtoforge.com/setting-up-a-pxe-install-server-on-ubuntu-9.10-p3]("http://www.howtoforge.com/setting-up-a-pxe-install-server-on-ubuntu-9.10-p3")

and can boot a machine over the network.  However, I would like to be able to boot the machine from a cd mounted on the pxe server(i.e. I would like to be able to use the pxe server with different cd installers, depending on what disc is inserted at the time, using the inserted disc to install the machine that I am booting via pxe boot).  I haven't been able to figure out how to successfully do this.  So, for now, I can boot the machine via pxe and do an install that simply downloads all needed files over the internet(=slow!).

Thanks!

---

