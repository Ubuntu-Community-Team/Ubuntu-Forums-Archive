---
title: "20gb unaccounted for on hard drive?"
date: 2010-03-13
forum: Installation &amp; Upgrades
---

### Post by mfcallahan on 2010-03-13
I looked around for some previous threads, but didn't see anything related to my problem, though I wasn't too sure how to word my searches.  Anyway, I have Ubuntu 9.1 installed on an old pentium 4 dell, 1 gb RAM, 320 gb HD.  I'm running it as a file server, with samba and proftpd, and running a firewall.  My problem is that only 300 gb of the brand new Wester Digital drive is recognized by the system.  There are 3 partitions: "/dev/sda2 extended - 2.86gb," "/dev/sda5 linux-swap - 2.86gb," and "/dev/sda1 ext4 - 295.22gb"

This totals about 300 gb, with 20gb unaccounted for.  Has anyone encountered this situation before?
 
Thanks much.

---

### Post by kooia on 2010-03-13
I'm thinking that the 20GB is probably some shared space or the Ubuntu operating system.

---

### Post by mfcallahan on 2010-03-13
would there be any reason disk space would not be reported/recognized in gparted?

---

### Post by oldfred on 2010-03-13
Your hard drive is not 320GiB. Hard drive mfgs count differently. Also formating hard drives reserves space for the journaling that provides reliability.

MB vs MiB
[http://en.wikipedia.org/wiki/Binary_prefix](http://en.wikipedia.org/wiki/Binary_prefix)
[http://www.osforge.com/news/001337.html](http://www.osforge.com/news/001337.html)

---

### Post by presence1960 on 2010-03-13
> **oldfred said:**
> Your hard drive is not 320GiB. Hard drive mfgs count differently. Also formating hard drives reserves space for the journaling that provides reliability.

MB vs MiB
[http://en.wikipedia.org/wiki/Binary_prefix](http://en.wikipedia.org/wiki/Binary_prefix)
[http://www.osforge.com/news/001337.html](http://www.osforge.com/news/001337.html)

+1 oldfred!

My sda disk is a 250 GB Seagate Barracuda- but it only shows as 232 GB. sdb is a 500 GB Seagate Barracuda-it shows as 465 GB & sdc is a 1 TB Seagate Barracuda- it shows as 931 GB. All are SATA disks. See my screenshot.

---

