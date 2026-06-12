---
title: "Recommended partition scheme for a production server with two 147G hard drives?"
date: 2014-12-11
forum: Installation &amp; Upgrades
---

### Post by jermin3 on 2014-12-11
Hi,

I have a dedicated box whose specs are:

CPU: 4-core Xeon 3450 *1 (HT enabled)
RAM: 8GB DDR3
HDD: 15k SAS 147G *2 (currently in RAID 1)

The current OS is Windows Server 2003. I am running a web server (with a couple of websites), a mail server, a svn server (based on apache), and several game servers on it. I'm now planning to switch the OS to ubuntu server and break the RAID to double the storage space. What partition scheme do you recommend to make the most out of the dual HDD setup?

---

### Post by nerdtron on 2014-12-11
Why break the RAID? You'll lose your protection on hard drive failure when you do that. As for partitioning, you can just use you current partition layout. If it works for you, you don't have to change it unless there are significant advantages.

---

