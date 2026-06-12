---
title: "Ubuntu on xSeries 300 - hang up on agpgart"
date: 2006-12-12
forum: Installation &amp; Upgrades
---

### Post by ikus060 on 2006-12-12
Hi,
I got tow IBM eServer xSeries 300 and I decide to reinstall Ubuntu on eah server. 
There is an issue to install correctly Ubuntu to the server, I have to user the flag "acpi=off". The last time I install Ubuntu on this server, I work great if I user this flag to install and boot Ubuntu.

But this time, It's doesn't work great ! On the first boot, Ubuntu hang up on this line : 

* Loading hardware drivers...
[..] ...
[..] ...
[..] ...
[ 281.626319] Linux agpgart interface v0,101 (c) Dave Jones
[ 283.376373] agpgart: Detect VIA Apollo Pro 133 chipset

The other technicien done an update of the BIOS, so it's could be related.

I try with other flag, like : agp=off, acpi=off and noapic with no result ...

Any sugestion is welcome !

Patrik Dufresne

---

### Post by packhamster on 2006-12-13
Patrick,

In order for the blacklist switches to work on this server you need to upgrade to the latest IBM BIOS too! Start here to find the required file: [http://www.ibm.com/products/finder/us/finders?pg=ddfinder&trac=SU1](http://www.ibm.com/products/finder/us/finders?pg=ddfinder&trac=SU1)
:) 

   -hp-

---

### Post by ikus060 on 2006-12-13
Actually, 

I think the problem is related to the BIOS upgrade. Since this update, the server don't boot any more ! I think do downgrade the BIOS, but I can't find the older version. So, I'm stuck.

For your information, the actual BIOS servion is 1.20 (the latest) and I'm trying to install Ubuntu 6.10.

Thank for your reply .. 

Question for you : Have you a xSeries 300 server with functional Ubuntu ?

---

### Post by packhamster on 2006-12-13
Yes, I actually have a couple of them, both done several times with both 6.06 and 6.10

BTW I am using the server ISO, not the alternate!

I saw your reply in the other post - let me know how it goes.

---

### Post by ikus060 on 2006-12-13
See this thread : [http://ubuntuforums.org/showthread.php?t=301275](http://ubuntuforums.org/showthread.php?t=301275)

---

