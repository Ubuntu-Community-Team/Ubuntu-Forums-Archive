---
title: "Update fails-Battery indicator[quantal]"
date: 2013-03-23
forum: Installation &amp; Upgrades
---

### Post by sid1990 on 2013-03-23
Hi,
   I'm kinda new to ubuntu...I'm really impressed with the power management excepting for the fact that i dont see the battery indicator on the top right..Also my update fails..i've attached the error log below..The links mentioned below no longer exist in the repo...Is there a work around for this..???



W:Failed to fetch [http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/quantal/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/quantal/main/binary-amd64/Packages](http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/quantal/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by ManamiVixen on 2013-03-23
The repos only have packages for Natty or older. I don't think you can use it anymore if you are using 12.04 or 12.10 on your laptop.

---

### Post by sid1990 on 2013-03-23
yes i am using 12.10!!Is it that none of you guys on 12.10 can see the rate at which your battery discharges??Thats really sad!!Could i switch souce to a different server to actually get this??If its a problem with the server from which the source is being updated??

---

### Post by ManamiVixen on 2013-03-23
Apparently the application ceased development due to issues with estimations. It was never accurate and glitched out alot for people. There is another Battery Monitor called "powertop" but it's meant for Intel chipsets. it's command prompt driven though. 

[https://01.org/powertop/](https://01.org/powertop/)

---

### Post by sid1990 on 2013-03-23
That is really sadddddddddddddd..:(((((((((
Thanks for the response though

---

