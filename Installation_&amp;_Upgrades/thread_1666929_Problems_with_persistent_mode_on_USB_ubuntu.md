---
title: "Problems with persistent mode on USB ubuntu"
date: 2011-01-14
forum: Installation &amp; Upgrades
---

### Post by Trautmann on 2011-01-14
Hi,
I recently bought an USB-stick with ubuntu preinstalled.
When I try to boot the persistent mode i get the message:

The disk contains an unclean file system (0, 0) The file system wasn't closed on Windows. Fixing. stdin: I/0 error

the i got a lot of

[some numbers (prob byte count)]end_request: I/0 error, dev fd0, sector 0

[some numbers (prob byte count)]Buffer I/0 error on device fd0, ogical block 0

and it all ends with

Begin: Creating debconf-communicate fifo mechanism ... done.

Begin: Running /scripts/caspeer-bottom ... Begin: Moving mount points... ... done.

Begin: Adding live session user ... ... pwck: cannot open /etc/passwd

I never make it to the Desktop :(

Strange thing is that it works on my Laptop and I can boot Live-Mode on my Desktop as well..

my mainbaord is an asus p5q pro and its ubuntu 10.10

thanks for now

Trautmann

---

### Post by Trautmann on 2011-01-14
/push

---

### Post by Trautmann on 2011-01-14
/push

---

### Post by Trautmann on 2011-01-15
no ideas?

---

### Post by C.S.Cameron on 2011-01-15
There are many ways to make a persistent USB stick.
Not sure what method was used on the one you bought.
Usually when persistence is selected the program looks for a file or partition named casper-rw in which to save changes.
It is easy to make your own persistent flash drive using Startup Disk Creator from the Live CD.

---

