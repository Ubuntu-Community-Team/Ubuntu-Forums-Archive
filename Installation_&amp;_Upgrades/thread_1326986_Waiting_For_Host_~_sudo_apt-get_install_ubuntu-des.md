---
title: "Waiting For Host ~ sudo apt-get install ubuntu-desktop problem"
date: 2009-11-14
forum: Installation &amp; Upgrades
---

### Post by rdbrock on 2009-11-14
0% [Waiting for headers]


I''ve been receiving this Waiting for host /headers for the past couple days.
I've ran this command several times, and never had any problems. I've upgraded 3 other workstations. Seems to stop at 99%.  Is there a problem w/ the server?
I've tried doing update and fix missing with no luck. Anyones else has this problem?


~sudo apt-get install ubuntu-desktop

0 upgraded, 459 newly installed, 1 to remove and 0 not upgraded.
Need to get 953kB/167MB of archives.
After this operation, 1,169MB of additional disk space will be used.
Do you want to continue [Y/n]? y

0% [Waiting for headers]
0% [Waiting for headers]
0% [Waiting for headers]
0% [Waiting for headers]
0% [Waiting for headers]
0% [Waiting for headers]


Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main tomboy 1.0.0-0ubuntu2
  Connection failed [IP: 91.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/t/tomboy/tomboy_1.0.0-0ubuntu2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/tomboy/tomboy_1.0.0-0ubuntu2_amd64.deb)  Connection failed [IP: 91.189.88.40 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

I've tried on a LAN port and Wifi connection with same results.

lat@lnxserver6400:~$ ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 0XXXXXXXXXXXX
          inet addr:192.168.1.21  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::e60:76ff:fe2f:5bdc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18382 errors:0 dropped:0 overruns:0 frame:51665
          TX packets:14210 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:20599486 (20.5 MB)  TX bytes:1541520 (1.5 MB)
          Interrupt:17 Base address:0xc000


Thanks

---

### Post by garvinrick4 on 2009-11-15
Change to new repository to get updates. Then go back to us.archive
later.  Try mirror.anl.gov/pub/ubuntu  in Software Sources.

---

### Post by rdbrock on 2009-11-15
I don't have the GUI to change it, I'm running Ubuntu 64bit 9.10 Sever, I was trying to add GUI but it fails at 99%.

How do I change sources to point to a mirror http to complete the update (~sudo apt-get install ubuntu-desktop)  from the command line prompt ?

---

### Post by garvinrick4 on 2009-11-15
Go to System to Administration to Software Sources.

Ubuntu software tab.  to Download from: click tab on outer edge.

choose Other.  Pick out new Server or Mirror. 

[http://mirror.anl.gov/pub/ubuntu](http://mirror.anl.gov/pub/ubuntu)

Close and new repositories will download.

If you want to use Terminal or command line.

The address is 3 lines up. 

First install then practice your command line work by reading and
Googling and reading some more. Have fun with Linux. Read these Forums and learn.

---

### Post by garvinrick4 on 2009-11-15
I am sorry I thought you had a desktop to work with. My mistake,
Here is the instructions from Ubuntu for command line and repositories.



[https://help.ubuntu.com/community/Repositories/CommandLine#Adding%20Repositories](https://help.ubuntu.com/community/Repositories/CommandLine#Adding%20Repositories)

---

### Post by rdbrock on 2009-11-15
OK, Thanks for the command line guide, I will try this and I will let you know if it works.
I hope It does, I really like the GUI and want to keep the full server functions.

---

### Post by rdbrock on 2009-11-16
Thank you for the guide! It worked. I ended up getting KDE and doing it from there.

---

