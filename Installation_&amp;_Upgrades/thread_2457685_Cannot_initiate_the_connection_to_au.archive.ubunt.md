---
title: "Cannot initiate the connection to au.archive.ubuntu.com:80"
date: 2021-02-06
forum: Installation &amp; Upgrades
---

### Post by rkrite on 2021-02-06
Hi,
I am running sudo apt update, and I am getting the error...

Err:8 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal InRelease                                                                                           
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) Could not connect to au.archive.ubuntu.com:80 (202.158.214.106), connection timed out
Err:9 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal-updates InRelease  
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable)
Err:10 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal-backports InRelease
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable)

When going to [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) it is saying site cannot be reached.

It seems that all other install repo locations are fine.

What do I do in this case?

Thanks very much

[UPDATE]
It seems that there is an issue with the Australian servers.
I changed from "Servers from Australia" to "Main Servers".
All good now :)

---

### Post by CelticWarrior on 2021-02-06
Welcome.

Probably just a temporary glitch. The servers likely will be up tomorrow.

---

