---
title: "closest server to download ubuntu installation files"
date: 2007-08-08
forum: Installation &amp; Upgrades
---

### Post by bbmak on 2007-08-08
I don't know if anybody has ever used my method to install ubuntu.
I use Windows 2003 WDS to network boot ubuntu.

During the installation, my computer will connect to ubuntu server to download the latest achieve.
the server that i am using now is [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)
the server is kind of slow, and sometime will disconnect.

I want to know are there any more server like this? I want some servers that are close to my place?

I am living in San Francisco, CA

---

### Post by jim_p on 2007-08-09
This solution may not be the fastest one but it will determine the server closest to you.

Boot up from a live 7.04 and make sure you have an active connection to the net.
Go to System > Administration > Software Sources.
On the 1st tab,under the "Location" menu, tick Internet and choose another server from the dropdown list. There you will find all USA servers, and possibly ones that are near San Fransisco.
Write them down and opern up a terminal. I will use ftp.belnet.be here,which is in Belgium:
```
ping ftp.belnet.be -c 5 
```
This will ping the server 5 times and output several stats. You are interested in the average ping delay.Note it down and do the same for all the servers of your interest. 
At last, pick the fastest one.

---

